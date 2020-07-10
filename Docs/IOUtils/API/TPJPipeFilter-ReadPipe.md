# ReadPipe method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJPipeFilter_](./TPJPipeFilter.md)

```pascal
procedure ReadPipe;
```

## Description

Reads and processes all available data from the pipe being filtered.

## Remarks

Actions resulting from processing the data depend on the implementation of descendant classes.

Implementers of new filter classes should note that the required actions must be implemented in overrides of the abstract [_DoFilter_](./TPJPipeFilter-DoFilter.md) and [_DoFlush_](./TPJPipeFilter-DoFlush.md) methods.
