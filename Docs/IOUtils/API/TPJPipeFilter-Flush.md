# Flush method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJPipeFilter_](./TPJPipeFilter.md)

```pascal
procedure Flush;
```

## Description

Flushes any unprocessed data.

## Remarks

_Flush_ is called automatically when the filter object is destroyed.

Actions resulting from calling this method depend on the implementation of descendant classes.

Implementers of new filter classes should note that the required actions must be implemented in the override of the abstract [_DoFlush_](./TPJPipeFilter-DoFlush.md) method.

Implementations should ensure that multiple calls to _Flush_ between pipe reads have the same effect as calling the method once. For example, assuming that F is and instance of a [_TPJPipeFilter_](./TPJPipeFilter.md) concrete descendant class, this code:

```pascal
...
F.ReadPipe;
F.Flush;
F.Flush;
F.ReadPipe;
F.Flush;
F.Free; // calls.F.Flush;
...
```

should act the same as

```pascal
...
F.ReadPipe;
F.Flush;
F.ReadPipe;
F.Free;  // calls F.Flush;
...
```

In some cases this method may legitimately do nothing.
