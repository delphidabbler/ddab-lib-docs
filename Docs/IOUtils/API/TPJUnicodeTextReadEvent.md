# TPJUnicodeTextReadEvent method type

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

```pascal
type
  TPJUnicodeTextReadEvent = procedure(Sender: TObject;
    const Text: UnicodeString) of object;
```

## Description

This is an event handler type. It is the type of text read events triggered by pipe filter classes that read Unicode strings from pipes.

The parameters are:

* _Sender_ - Reference to the pipe filter object that triggered the event.

* _Text_ - Unicode text for which the event was triggered.

## Remarks

This event handler type is used for the [_OnText_](./TPJUnicodeBMPPipeFilter-OnText.md) and [_OnLineEnd_](./TPJUnicodeBMPPipeFilter-OnLineEnd.md) events of [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md).

Note that the _UnicodeString_ type must be defined to use event handlers of this type. On Delphi 2009 _UnicodeString_ is a native type while the [_PJPipeFilters_](./PJPipeFilters.md) unit defines _UnicodeString_ as _WideString_ on Delphi 2007 and earlier.

## Links

* [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md)
* [_TPJAnsiTextReadEvent_](./TPJAnsiTextReadEvent.md)
* [Type Definitions List](./Types.md)
