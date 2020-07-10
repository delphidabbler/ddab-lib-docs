# Create constructor

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Classes:*** [_TPJPipeFilter_](./TPJPipeFilter.md), [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md), [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md)

```pascal
constructor Create(const APipe: TPJPipe; const AOwnsPipe: Boolean = False);
```

## Description

This constructor creates an instance of the filter object to operate on a specified pipe.

Parameters:

* _APipe_ - Pipe on which the filters are to act. The pipe will be exposed via the read only [_Pipe_](./TPJPipeFilter-Pipe.md) property.

* _AOwnsPipe_ - Flag that indicates whether the filter object owns the pipe. If true then the pipe object will be freed when the filter object is destroyed.

## Remarks

The filter object will read the pipe whenever the filter's [_ReadPipe_](./TPJPipeFilter-ReadPipe.md) method is called.

Setting _AOwnsPipe_ to true means that pipes can be created on the fly in the filter's constructor and they will be freed automatically at the appropriate time. For example the two following code fragments are functionally the same:

```pascal
var
  Filter: TPJUnicodeBMPPipeFilter;
  Pipe: TPJPipe;
begin
  Pipe := TPJPipe.Create;
  try
    Filter := TPJUnicodeBMPPipeFilter.Create(Pipe, False);
    try
      // do something with Filter and Pipe
    finally
      Filter.Free;
    end;
  finally
    Pipe.Free;
  end;
end;
```

```pascal
var
  Filter: TPJUnicodeBMPPipeFilter;
begin
  Filter := TPJUnicodeBMPPipeFilter.Create(TPJPipe.Create, True);
  try
    // do something with Filter and Filter.Pipe
  finally
    Filter.Free;
  end;
end;
```

In the second listing, if we need to access the pipe object we must use the filter's [_Pipe_](./TPJPipeFilter-Pipe.md) property.
