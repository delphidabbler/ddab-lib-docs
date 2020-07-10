# DoFlush abstract method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJPipeFilter_](./TPJPipeFilter.md)

```pascal
procedure DoFlush; virtual; abstract;
```

## Description

Flushes any ***valid*** unprocessed data from any internal buffers.

Not all filters necessarily have any valid buffered data. If this is the case they need only provide a stub, do nothing, implementation of this method.

Those filters that can have such data must take the necessary steps to process it here.

## Example

Both [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md) and [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md) split processed text into lines and report each line via their _OnLineEnd_ events.

Often there will be some text left over after the last end of line that has not been reported. Both classes implement this method to report that remaining text via the _OnLineEnd_ event as if the text was terminated by the normal end-of-line marker.

Here is the code from [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md):

```pascal
procedure TPJUnicodeBMPPipeFilter.DoFlush;
begin
  if fPartialLine <> _ then
  begin
    DoLineEnd(fPartialLine);
    fPartialLine := _;
  end;
end;
```

_fPartialLine_ stores text that is yet to be reported via the _OnLineEnd_ event and _DoLineEnd_ triggers the _OnLineEnd_ event.
