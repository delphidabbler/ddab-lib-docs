# LeftOverByteCount abstract method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJPipeFilter_](./TPJPipeFilter.md)

```pascal
function LeftOverByteCount(const RawData: TBytes): Integer; virtual; abstract;
```

## Description

Returns the number of bytes at end of the given byte array that cannot be processed yet.

The single parameter, _RawData_ is a byte array containing raw unprocessed data that has yet to be filtered. The data formats used by some filters are multi-byte and _RawData_ may be not contain a complete meaningful sequence of bytes at the end of the array. In these cases the meaningless bytes are carried forward until the next pipe read when they are prepended to the next chunk of data read from the pipe.

Implementations must calculate the maximum amount data from the byte array that can be processed and therefore work out how many bytes are to be carried forward. That number must be returned from the function.

## Remarks

The type of the _RawData_ byte array parameter is _TBytes_. In versions of Delphi that do not defined _TBytes_ in _SysUtils_ the [_PJPipeFilters_](./PJPipeFilters.md) unit defines _TBytes_ as `array of Byte`.

## Examples

[_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md) reads Unicode strings comprising characters from the [Basic Multilingual Plane](http://en.wikipedia.org/wiki/Basic_Multilingual_Plane#Basic_Multilingual_Plane), which means that that each character always occupies two bytes.

Therefore if _RawData_ has an odd number of bytes the last byte is meaningless until more data is read and so this last byte needs to be carried forward. In this case `1` is returned from the function. If an even number of bytes is read then all the bytes encode characters and can be processed, so `0` is returned.

Here is the implementation of this method in [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md):

```pascal
function TPJUnicodeBMPPipeFilter.LeftOverByteCount(
  const RawData: TBytes): Integer;
begin
  Result := Length(RawData) mod SizeOf(WideChar);
end;
```

The implementation in [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md) is simpler. Because the class reads [single byte character sets](http://en.wikipedia.org/wiki/SBCS), where every byte represents a different character, it can always process all the bytes in _RawData_. Therefore the implementation of this method in [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md) is simply:

```pascal
function TPJAnsiSBCSPipeFilter.LeftOverByteCount(
  const RawData: TBytes): Integer;
begin
  Result := 0;
end;
```
