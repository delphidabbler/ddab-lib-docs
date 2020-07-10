# OnLineEnd event

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md)

```pascal
property OnLineEnd: TPJAnsiTextReadEvent;
```

## Description

This event is triggered whenever an end of a line is encountered in the ANSI text read from the associated pipe. Line ends are determined by the value of the [_EOLMarker_](./TPJAnsiSBCSPipeFilter-EOLMarker.md) property.

The event can also be triggered when the [_Flush_](./TPJAnsiSBCSPipeFilter-Flush.md) method is called or when the object is destroyed. This occurs if there is some text remaining that has not been terminated by the end of line marker.

The event handler is passed the following parameters:

* _Sender_ - Set to the [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md) object that triggered the event.

* _Text_ - An _AnsiString_ containing the line of text, stripped of the end of line marker.

## Example

Suppose we have a [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md) object created on a pipe that contains the following ANSI text:

> `Lorem ipsum<EOL>intellegam<EOL>dissentias<EOL>te sea`

The [_EOLMarker_](./TPJAnsiSBCSPipeFilter-EOLMarker.md) property is set to "`<EOL>`". We perform three pipe reads and a flush operation before destroying the object. Here's what happens:

* The _ReadPipe_ method is called and reads text "`Lorem ip`" from the pipe.
  * _OnLineEnd_ is not triggered because the text contains no end of line marker ("`<EOL>`").
  * The text is recorded for later use in a "carry forward" buffer.

* _ReadPipe_ is called and reads "`sum<EOL>intellegam<EOL>dis`" from the pipe.
  * The text is appended to the carried forward text to get "`Lorem ipsum<EOL>intellegam<EOL>dis`", which is then processed.
  * _OnLineEnd_ is triggered with parameter "`Lorem ipsum`". The following "`<EOL>`" is discarded.
  * _OnLineEnd_ is triggered again with parameter "`intellegam`". The following "`<EOL>`" is again discarded.
  * The text "`dis`" is left over and recorded in the carry forward buffer.

* _ReadPipe_ is called and reads "`sentias<EOL>te sea`" from the pipe.
  * The text is appended to the carried forward text to get "`dissentias<EOL>te sea`", which is processed.
  * _OnLineEnd_ is triggered with parameter "`dissentias`" and the following "`<EOL>`" is discarded.
  * The remaining text "`te sea`" is recorded in the carry forward buffer.

* The _Flush_ method is called.
  * _OnLineEnd_ is triggered with carried forward text "`te sea`" as its parameter.
  * The carry forward buffer is cleared.

* The object is destroyed, which automatically calls _Flush_ once more.
  * Nothing happens because the carry forward buffer is empty.

## Links

* [_TPJAnsiTextReadEvent_](./TPJAnsiTextReadEvent.md)
* [_OnText_](./TPJAnsiSBCSPipeFilter-OnText.md) event
