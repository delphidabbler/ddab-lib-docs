# MD5 How-to: How To Get the MD5 Hash of a Stream

There are two overloads of the [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#tstream-versions) and [_TPJMD5.Process_](../API/TPJMD5-Process.md#tstream-versions) methods that can be used to create MD5 hashes of streams. One version takes a single _TStream_ parameter and gets the hash of the data in the stream after the current position while the other version hashes a given number of bytes from the current stream position.

> Code examples in this how-to all use  [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#tstream-versions) because it lends itself to more concise code, but [_TPJMD5.Process_](../API/TPJMD5-Process.md#tstream-versions) can be used for the same purpose. For details of the differences see [Understand the Calculate and Process methods](./UseCalculateAndProcess.md).

The most common requirement is to take the MD5 hash of a whole stream. This is done like this:

```pascal
function GetMD5OfWholeStream(const Stm: TStream): TPJMD5Digest;
begin
  Stm.Position := 0;
  Result := TPJMD5.Calculate(Stm);
end;
```

The main point to note is that we ensure the stream position is at the start so that [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#tstream-versions) processes the whole stream.

It is much less likely that you will need to process parts of a stream, but it can be done. There are three main cases:

1. Process N bytes at the start of a stream
2. Process N bytes at the end of a stream
3. Process N bytes from a given offset in the stream

Assume you have a stream of length greater that 1Kb, then the following code fragments get the MD5 of the first, last and middle 1Kb of data:

```pascal
const
  OneKb: Int64 = 1024;
var
  DFirst, DMiddle, DLast: TPJMD5Digest;
  Stm: TStream;
begin
  // ...
  // create Stm and ensure it contains at least 1Kb of data
  // ...
  Assert(Stm.Size >= OneKb);

  // get MD5 of 1st 1Kb of data
  Stm.Seek(0, soFromBeginning);
  DFirst := TPJMD5.Calculate(Stm, OneKb);

  // get MD5 of last 1Kb of data
  Stm.Seek(OneKb, soFromEnd);
  DLast := TPJMD5.Calculate(Stm);  // reads to end

  // get MD5 of middle 1Kb of data
  Stm.Seek((Stm.Size - OneKb) div 2, soFromBeginning);
  DMiddle := TPJMD5.Calculate(Stm, OneKb);

  // ...
  // do something with digests
  // ...
end;
```

## See Also

* How-tos:
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md)
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)

## Links

* [How-to Guide Contents](../HowTo.md)
