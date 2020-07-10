# TPJAnsiTextReadEvent method type

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

```pascal
type
  TPJAnsiTextReadEvent = procedure(Sender: TObject;
    const Text: AnsiString) of object;
```

## Description

This is an event handler type. It is the type of text read events triggered by pipe filter classes that read ANSI strings from pipes.

The parameters are:

* _Sender_ - Reference to the pipe filter object that triggered the event.

* _Text_ - ANSI text for which the event was triggered.

## Remarks

This event handler type is used for the [_OnText_](./TPJAnsiSBCSPipeFilter-OnText.md) and [_OnLineEnd_](./TPJAnsiSBCSPipeFilter-OnLineEnd.md) events of [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md).

## Links

* [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md)
* [_TPJUnicodeTextReadEvent_](./TPJUnicodeTextReadEvent.md)
* [Type Definitions List](./Types.md)
