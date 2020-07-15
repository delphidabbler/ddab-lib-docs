# Calculate methods

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
class function Calculate(const X: TBytes; const StartIdx, Count: Cardinal):
  TPJMD5Digest; overload;
class function Calculate(const X: TBytes; const Count: Cardinal):
  TPJMD5Digest; overload;
class function Calculate(const X: TBytes): TPJMD5Digest; overload;
class function Calculate(const Buf; const Count: Cardinal): TPJMD5Digest;
  overload;
class function Calculate(const S: RawByteString): TPJMD5Digest; overload;
class function Calculate(const S: ShortString): TPJMD5Digest; overload;
class function Calculate(const S: WideString): TPJMD5Digest; overload;
class function Calculate(const S: UnicodeString;
  const Encoding: TEncoding): TPJMD5Digest; overload;
class function Calculate(const S: UnicodeString): TPJMD5Digest; overload;
class function Calculate(const Stream: TStream;
  const Count: Int64): TPJMD5Digest; overload;
class function Calculate(const Stream: TStream): TPJMD5Digest; overload;
```

## Description

There a several different overloaded versions of the _Calculate_ method, all of which are class methods that return a [_TPJMD5Digest_](./TPJMD5Digest.md) record containing the digest of some specified data.

The methods provide a useful shortcut when all you need to do is create an MD5 hash of a single data item such as a stream, a string or a byte array. You can do this with just one call to _Calculate_ - there is no need to create a [_TPJMD5_](./TPJMD5.md) instance.

The disadvantages are:

* Only one "resource" can be processed.
* The size of the read buffer used when processing streams and files cannot be changed from the default.

Similar groups of methods are described below:

* [Byte array versions](#byte-array-versions)
* [Untyped buffer version](#untyped-buffer-version)
* [ANSI string version](#ansi-string-version)
* [ShortString version](#shortstring-version)
* [WideString version](#widestring-version)
* [Unicode string versions](#unicode-string-versions)
* [TStream versions](#tstream-versions)

--------------------------------------------

### Byte array versions

```pascal
class function Calculate(const X: TBytes; const StartIdx, Count: Cardinal):
  TPJMD5Digest; overload;
class function Calculate(const X: TBytes; const Count: Cardinal):
  TPJMD5Digest; overload;
class function Calculate(const X: TBytes): TPJMD5Digest; overload;
```

These methods generate a MD5 digest from a _TBytes_ array.

1. The first version processes _Count_ bytes starting from index _StartIdx_ in byte array _X_. If there are less than _Count_ bytes in the array counting from _StartIdx_ then an [_EPJMD5_](./EPJMD5.md) exception is raised. If _StartIdx_ is beyond the end of the array or if _Count_ is zero no data is processed.
2. The second version processes _Count_ bytes from the beginning of byte array _X_. _X_ must have at least _Count_ elements otherwise an [_EPJMD5_](./EPJMD5.md) exception is raised. If _Count_ is zero then no data is processed.
3. The last version processes the whole of byte array _X_. If the array is empty then no data is processed.

#### Examples

Create an MD5 digest of an eight element array of bytes:

```pascal
var
  Digest: TPJMD5Digest;
  A: TBytes;
begin
  A := TBytes.Create(1,2,3,4,5,6,7,8);
  Digest := TPJMD5.Calculate(A);  // MD5 of 1,2,3,4,5,6,7,8
  ...
end;
```

Create an MD5 digest of the middle four bytes of an eight element array of bytes:

```pascal
var
  Digest: TPJMD5Digest;
  A: TBytes;
begin
  A := TBytes.Create(1,2,3,4,5,6,7,8);
  Digest := TPJMD5.Calculate(A, 2, 4);  // MD5 of 3,4,5,6
  ...
end;
```

--------------------------------------------

### Untyped buffer version

```pascal
class function Calculate(const Buf; const Count: Cardinal): TPJMD5Digest;
  overload;
```

Calculates a digest from _Count_ bytes read from untyped buffer _Buf_. _Buf_ must contain at least _Count_ bytes.

#### Untyped example

Assume you have an array of long word values for which you want the MD5 hash. Here's a function that gets it for you:

```pascal
function MD5OfLongWordArray(const A: array of LongWord): TPJMD5Digest;
begin
  Result := TPJMD5.Calculate(A[0], SizeOf(LongWord) * Length(A));
end;
```

--------------------------------------------

### ANSI string version

```pascal
class function Calculate(const S: RawByteString): TPJMD5Digest; overload;
```

Calculates a digest from the ordinal values of the characters of an ANSI string _S_. _S_ can have any code page.

#### ANSI string example

Create an MD5 digest of an AnsiString containing the text `Hello World`:

```pascal
var
  Digest: TPJMD5Digest;
  S: AnsiString;
begin
  S := 'Hello World';
  Digest := TPJMD5.Calculate(S);
  ...
end;
```

--------------------------------------------

### ShortString version

```pascal
class function Calculate(const S: ShortString): TPJMD5Digest; overload;
```

Calculates a digest from the ordinal values of the characters of a short string _S_.

--------------------------------------------

### WideString version

```pascal
class function Calculate(const S: WideString): TPJMD5Digest; overload;
```

Calculates a digest from the ordinal values of the _WideChar_ characters of the _WideString_ parameter, _S_.

--------------------------------------------

### Unicode string versions

```pascal
class function Calculate(const S: UnicodeString;
  const Encoding: TEncoding): TPJMD5Digest; overload;
class function Calculate(const S: UnicodeString): TPJMD5Digest; overload;
```

Each of these methods creates a digest of a Unicode string _S_. Before processing the string it is converted to a sequence of bytes. The first version uses the encoding passed in the _Encoding_ parameter to perform the conversion while the second version uses the _TEncoding.Default_ encoding.

--------------------------------------------

### TStream versions

```pascal
class function Calculate(const Stream: TStream;
  const Count: Int64): TPJMD5Digest; overload;
class function Calculate(const Stream: TStream): TPJMD5Digest; overload;
```

This pair of methods calculate a digest from the bytes read from stream _Stream_. Bytes are always read from the current position in _Stream_. Both methods modify the stream's _Position_ property.

The first version reads _Count_ bytes from the stream. If _Count_ is greater than number of bytes available then an [_EPJMD5_](./EPJMD5.md) exception is raised. The second version reads to the end of the stream, processing `Stream.Size - Stream.Position` bytes.

The stream is read in chunks. The size of a chunk is given by the [_TPJMD5.DefReadBufferSize_](./TPJMD5-DefReadBufferSize.md) constant. This buffer size cannot be changed. If you need to change the buffer size you must create a [_TPJMD5_](./TPJMD5.md) instance, set the buffer size using the [_ReadBufferSize_](./TPJMD5-ReadBufferSize.md) property, then use the appropriate [_Process_](./TPJMD5-Process.md) method.

#### TStream example

Create an MD5 digest of a _TStream_ referenced by _Stm_. We write the ASCII characters `Hello World` to the stream and then get the MD5 of various parts of the stream.

```pascal
var
  Digest1, Digest2, Digest3: TPJMD5Digest;
  Stm: TStringStream;
begin
  Stm := TStringStream.Create('Hello World', TEncoding.ASCII);
  try
    // get digest of ASCII chars 'Hello World'
    Stm.Position := 0;
    Digest1 := TPJMD5.Calculate(Stm);
    ...
    // get digest of ASCII chars 'llo'
    Stm.Position := 2;
    Digest2 := TPJMD5.Calculate(Stm, Int64(3));
    ...
    // get digest of ASCII chars 'World'
    Stm.Position := 6;
    Digest3 := TPJMD5.Calculate(Stm);
    ...
  finally
    Stm.Free;
  end;
end;
```
