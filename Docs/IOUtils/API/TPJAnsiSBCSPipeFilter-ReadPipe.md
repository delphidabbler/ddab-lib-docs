# ReadPipe method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md)

```pascal
procedure ReadPipe;
```

## Description

Reads and processes all available data from the pipe being filtered.

A [_OnText_](./TPJAnsiSBCSPipeFilter-OnText.md) event is triggered containing the text read from the pipe.

For each complete line of text read a [_OnLineEnd_](./TPJAnsiSBCSPipeFilter-OnLineEnd.md) event will also be triggered. Any text following the last line end will be held over until the next call to _ReadPipe_ or [_Flush_](./TPJAnsiSBCSPipeFilter-Flush.md).

## Remarks

Lines are divided according the the end of line character(s) specified by the [_EOLMarker_](./TPJAnsiSBCSPipeFilter-EOLMarker.md) property.
