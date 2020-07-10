# OnText event

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md)

```pascal
property OnText: TPJUnicodeTextReadEvent;
```

## Description

This event is triggered whenever Unicode text is read from the associated pipe. The event occurs once for every call to the [_ReadPipe_](./TPJUnicodeBMPPipeFilter-ReadPipe.md) method. Once the data read from the pipe is converted to Unicode text it is not processed further before passing the text to the event handler.

The event handler is passed the following parameters:

* _Sender_ - Set to the [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md) object that triggered the event.

* _Text_ - An _UnicodeString_ containing the text.

## Remarks

In the event that [_ReadPipe_](./TPJUnicodeBMPPipeFilter-ReadPipe.md) reads an empty pipe, or reads just one byte, the text passed to an _OnText_ event handler will be the empty string.

The event handler is never triggered by the [_Flush_](./TPJUnicodeBMPPipeFilter-Flush.md) method.

Note that the _UnicodeString_ type must be defined to use this event. This is a native type on Delphi 2009 or later. For Delphi 2007 and earlier the [_PJPipeFilters_](./PJPipeFilters.md) unit defines _UnicodeString_ as _WideString_.

## Links

* [_TPJUnicodeTextReadEvent_](./TPJUnicodeTextReadEvent.md)
* [_OnLineEnd_](./TPJUnicodeBMPPipeFilter-OnLineEnd.md) property
