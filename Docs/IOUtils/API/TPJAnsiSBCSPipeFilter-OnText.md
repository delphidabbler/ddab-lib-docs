# OnText event

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md)

```pascal
property OnText: TPJAnsiTextReadEvent;
```

## Description

This event is triggered whenever ANSI text is read from the associated pipe. The event occurs once for every call to the [_ReadPipe_](./TPJAnsiSBCSPipeFilter-ReadPipe.md) method. Once the data read from the pipe is converted to ANSI text it is not processed further before passing the text to the event handler.

The event handler is passed the following parameters:

* _Sender_ - Set to the [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md) object that triggered the event.

* _Text_ - An _AnsiString_ containing the text.

## Remarks

In the event that [_ReadPipe_](./TPJAnsiSBCSPipeFilter-ReadPipe.md) reads an empty pipe the text passed to an _OnText_ event handler will be the empty string.

The event is never triggered by the [_Flush_](./TPJAnsiSBCSPipeFilter-Flush.md) method.

## Links

* [_TPJAnsiTextReadEvent_](./TPJAnsiTextReadEvent.md)
* [_OnLineEnd_](./TPJAnsiSBCSPipeFilter-OnLineEnd.md) event
