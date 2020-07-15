# OnLineEnd event

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md)

```pascal
property OnLineEnd: TPJUnicodeTextReadEvent;
```

## Description

This event is triggered whenever the end of a line is encountered in the Unicode text read from the associated pipe. Line ends are determined by the value of the [_EOLMarker_](./TPJUnicodeBMPPipeFilter-EOLMarker.md) property.

The event can also be triggered when the [_Flush_](./TPJUnicodeBMPPipeFilter-Flush.md) method is called or when the object is destroyed. This occurs if there is some text remaining that has not been terminated by an end of line marker.

The event handler is passed the following parameters:

* _Sender_ - Set to the [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md) object that triggered the event.

* _Text_ - An _UnicodeString_ containing the line of text, stripped of the end of line marker.

## Remarks

Note that the _UnicodeString_ type must be defined to use this event. This is a native type on Delphi 2009 or later. For Delphi 2007 and earlier the [_PJPipeFilters_](./PJPipeFilters.md) unit defines _UnicodeString_ as _WideString_.

## Example

In this example all text strings are Unicode.

Suppose we have a [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md) object created on a pipe that contains the following Unicode text:

`Lorem ipsum<EOL>intellegam<EOL>dissentias<EOL>te sea`

The [_EOLMarker_](./TPJUnicodeBMPPipeFilter-EOLMarker.md) property is set to `<EOL>`. We perform three pipe reads and a flush operation before destroying the object. Here's what happens:

* The _ReadPipe_ method is called and reads text [[1]](#footnote-1) `Lorem ip` from the pipe.
  * _OnLineEnd_ is not triggered because the text contains no end of line marker (`<EOL>`).
  * The text is recorded for later use in a "carry forward" buffer.

* _ReadPipe_ is called and reads `sum<EOL>intellegam<EOL>dis` from the pipe.
  * The text is appended to the carried forward text to get `Lorem ipsum<EOL>intellegam<EOL>dis`, which is then processed.
  * _OnLineEnd_ is triggered with parameter `Lorem ipsum`. The following `<EOL>` is discarded.
  * _OnLineEnd_ is triggered again with parameter `intellegam`. The following `<EOL>` is again discarded.
  * The text `dis` is left over and recorded in the carry forward buffer.

* _ReadPipe_ is called and reads `sentias<EOL>te sea` from the pipe.
  * The text is appended to the carried forward text to get `dissentias<EOL>te sea`, which is processed.
  * _OnLineEnd_ is triggered with parameter `dissentias` and the following `<EOL>` is discarded.
  * The remaining text `te sea` is recorded in the carry forward buffer.

* The _Flush_ method is called.
  * _OnLineEnd_ is triggered with carried forward text `te sea` as its parameter.
  * The carry forward buffer is cleared.

* The object is destroyed, which automatically calls _Flush_ once more.
  * Nothing happens because the carry forward buffer is empty.

## Footnotes

### Footnote 1

Of course _ReadPipe_ actually reads binary data from the pipe and converts that data into a Unicode text string.

## Links

* [_TPJUnicodeTextReadEvent_](./TPJUnicodeTextReadEvent.md)
* [_OnText_](./TPJUnicodeBMPPipeFilter-OnText.md) property
