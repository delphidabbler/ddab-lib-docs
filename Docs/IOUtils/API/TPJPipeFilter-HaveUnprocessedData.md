# HaveUnprocessedData method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Classes:*** [_TPJPipeFilter_](./TPJPipeFilter.md), [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md), [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md)

```pascal
function HaveUnprocessedData: Boolean;
```

## Description

This method checks if the filter object contains any unprocessed binary data and returns `True` if so and `False` if not.

The method provides information about whether the last read operation on the pipe left any partial data over for processing on the next read.

## Remarks

The main purpose of this method is after the last pipe read to check whether any data is left unprocessed. This indicates that the data read from the pipe has invalid data in it. It may have been truncated or corrupted. The caller can then decide whether to ignore or report the error.

Calling the method between reads will give information about whether the last read was all processed (method returns `False`) or whether some data is being carried forward (returns `True`).

## Example

A data stream of odd length cannot contain valid Unicode text because the size of a Unicode character is at least two. If such a stream is being read by a filter object that understands Unicode then there will be one byte left over after the last read operation causing _HaveUnprocessedData_ to return `True`.
