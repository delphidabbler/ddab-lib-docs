# Process methods

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
procedure Process(const X: TBytes; const StartIdx, Count: Cardinal);
  overload;
procedure Process(const X: TBytes; const Count: Cardinal); overload;
procedure Process(const X: TBytes); overload;
procedure Process(const Buf; const Count: Cardinal); overload;
procedure Process(const S: RawByteString); overload;
procedure Process(const S: ShortString); overload;
procedure Process(const S: WideString); overload;
procedure Process(const S: UnicodeString; const Encoding: TEncoding); overload;
procedure Process(const S: UnicodeString); overload;
procedure Process(const Stream: TStream; const Count: Int64); overload;
procedure Process(const Stream: TStream); overload;
```

## Description

There a several different overloaded versions of the _Process_ method. Each method adds the data passed to it via its parameters to the current MD5 hash.

The advantages of these methods over the similar [_Calculate_](./TPJMD5-Calculate.md) methods are:

1. _Process_ methods can be called more than once: for example they can be called in a loop adding data to the hash on each occasion.
2. The methods enable data of different types to be added to the same hash.
3. In the case of the _TStream_ variant, the size of the buffer to use to read the stream can be changed from the default before calling the method.

The disadvantage of _Process_ is that an instance of [_TPJMD5_](./TPJMD5.md) must be created before the method can be used.

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
procedure Process(const X: TBytes; const StartIdx, Count: Cardinal);
  overload;
procedure Process(const X: TBytes; const Count: Cardinal); overload;
procedure Process(const X: TBytes); overload;
```

These methods add bytes from a _TBytes_ array to the current hash.

1. The first version adds _Count_ bytes to the hash, starting from index _StartIdx_ in byte array _X_. If there are less than _Count_ bytes in the array counting from _StartIdx_ then an [_EPJMD5_](./EPJMD5.md) exception is raised. If _StartIdx_ is beyond the end of the array or if _Count_ is zero no data is processed.
2. The second version adds _Count_ bytes from the beginning of byte array _X_ to the hash. _X_ must have at least _Count_ elements otherwise an [_EPJMD5_](./EPJMD5.md) exception is raised. If _Count_ is zero then no data is processed.
3. The last version adds all the content of byte array _X_ to the hash. If the array is empty then no data is processed.

#### Byte array example

Suppose you have read a file into a byte array and want its MD5 hash. However, to save processing time, if the array is longer that 32Kb you just take the hash of the first and last 16Kb of data from the array. Here's a function to do that:

```pascal
function MD5OfArray(const A: TBytes): TPJMD5Digest;
var
  MD5: TPJMD5;
const
  ChunkSize = 16 * 1024;
  MaxSize = 2 * ChunkSize;
begin
  MD5 := TPJMD5.Create;
  try
    if Length(A) > MaxSize then
    begin
      MD5.Process(A, ChunkSize); // 1st 16Kb
      MD5.Process(A, Length(A) - ChunkSize, ChunkSize);  // last 16Kb
    end
    else
      MD5.Process(A); // array <= 32Kb, process it all
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

--------------------------------------------

### Untyped buffer version

```pascal
procedure Process(const Buf; const Count: Cardinal); overload;
```

This method adds _Count_ bytes from untyped buffer _Buf_ to the current hash. _Buf_ must contain at least _Count_ bytes.

#### Untyped buffer example

Suppose you have two variables, _Foo_ of type _Byte_ and _Bar_ of type _Int64_ and you need the MD5 checksum of both of them. Here's the code to do it:

```pascal
var
  Foo: Byte;
  Bar: Int64;
  MD5: TPJMD5;
begin
  Foo := 42;
  Bar := -56;
  MD5 := TPJMD5.Create;
  try
    MD5.Process(Foo, SizeOf(Foo));
    MD5.Process(Bar, SizeOf(Bar));
    MD5.Finalize; // optional
    ShowMessage(MD5.Digest); // implicitly casts Digest to string
  finally
    MD5.Free;
  end;
end;
```

--------------------------------------------

### ANSI string version

```pascal
procedure Process(const S: RawByteString); overload;
```

Adds the ordinal value of all the characters from an ANSI string _S_ to the current hash. _S_ can have any code page.

--------------------------------------------

### ShortString version

```pascal
procedure Process(const S: ShortString); overload;
```

Adds the ordinal value of all the characters from the _ShortString_ _S_ to the current hash.

--------------------------------------------

### WideString version

```pascal
procedure Process(const S: WideString); overload;
```

Adds the ordinal value of all the _WideChar_ characters from the _WideString_ parameter _S_ to the current hash.

--------------------------------------------

### Unicode string versions

```pascal
procedure Process(const S: UnicodeString; const Encoding: TEncoding); overload;
procedure Process(const S: UnicodeString); overload;
```

Each of these methods adds data from a Unicode string _S_ to the current hash. Before adding to the hash the string is converted to a sequence of bytes. The first version uses the encoding passed in the _Encoding_ parameter to perform the conversion, while the second version uses the _TEncoding.Default_ encoding.

#### Unicode string examples

Suppose you have two text files that have the same text but may have different amounts of white space or different kinds of line endings. You want the MD5 hash to depend only on the words and not the white space.

One solution is to read all the words from a file into a string list, ignoring intervening white space and then build the MD5 hash from the words. Assuming the words are in a string list you can get the MD5 hash as follows using the following function:

```pascal
function MD5OfStrings(const Words: TStrings): TPJMD5Digest;
var
  MD5: TPJMD5;
  Word: string;
begin
  MD5 := TPJMD5.Create;
  try
    for Word in Words do
      MD5.Process(Word);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

This code uses the system default encoding of the words in the string, which could mean that different hashes are returned on systems running on different locales. To get round this, use UTF8 (or Unicode) for the encoding. Here's an example using UTF8:

```pascal
function MD5OfStrings(const Words: TStrings): TPJMD5Digest;
var
  MD5: TPJMD5;
  Word: string;
begin
  MD5 := TPJMD5.Create;
  try
    for Word in Words do
      MD5.Process(Word, TEncoding.UTF8);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

--------------------------------------------

### TStream versions

```pascal
procedure Process(const Stream: TStream; const Count: Int64); overload;
procedure Process(const Stream: TStream); overload;
```

Each of these methods adds bytes from the stream _Stream_ to the current hash. The stream is read from the current position. To read the from the start of the stream set its _Position_ property to `0`. Both methods modify the stream's _Position_ property.

The first version reads _Count_ bytes from the stream if possible. If _Count_ is greater than number of bytes available then an [_EPJMD5_](./EPJMD5.md) exception is raised. The second version reads to the end of the stream, processing `Stream.Size - Stream.Position` bytes.

The stream is read into an internal buffer before adding the data to the hash. The buffer's size is given by the [_ReadBufferSize_](./TPJMD5-ReadBufferSize.md) property and can be changed by assigning a new value to the property.

#### TStream example

Suppose you have a file containing multiple streams or "storages" and you have opened a _TStream_ onto each storage in the file. You want to get a MD5 hash of all of them. However some can be very large so to save processing time you only take the hash of the first 32Kb of each stream.

The following function will do the job: it is passed an array of _TStream_ objects and returns the MD5 digest:

```pascal
function GetStreamHashes(const Streams: array of TStream): TPJMD5Digest;
var
  MD5: TPJMD5;
  Stream: TStream;
const
  MaxSize = Int64(32 * 1024);
begin
  MD5 := TPJMD5.Create;
  try
    for Stream in Streams do
    begin
      Stream.Position := 0;
      if Stream.Size > MaxSize then
        MD5.Process(Stream, MaxSize) // process first 32Kb of stream
      else
        MD5.Process(Stream); // stream <= 32Kb - process it all
    end;
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```
