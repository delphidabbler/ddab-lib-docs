# MD5 How-to: How To Compare Two Digests

One of the most common tasks when working with MD5 message digests (hashes) is to compare two digests. This is usually done to check if some data or file has changed.

[_TPJMD5Digest_](../API/TPJMD5Digest.md) helps here in that you can directly compare two digests to equality or inequality. For example, if you have two [_TPJMD5Digest_](../API/TPJMD5Digest.md) records, _D1_ and _D2_, you can compare them like this:

```pascal
begin
  ...
  if D1 = D2 then {do something};
  if D1 <> D2 then {do something else};
  ...
end;
```

We are able to do this because [_TPJMD5Digest_](../API/TPJMD5Digest.md) overloads the [_Equal_](../API/TPJMD5Digest-Equal.md) and [_NotEqual_](../API/TPJMD5Digest-NotEqual.md) operators to enable two [_TPJMD5Digest_](../API/TPJMD5Digest.md) records to be compared for equality and inequality.

Another common requirement is to compare a digest with a string representation of the digest. This is often used when downloading files from the Internet. The download site displays the MD5 hash of the file to be downloaded. When you have downloaded the file you get a string representation of its MD5 hash and compare it with the string displayed on the web page. This function provides a way of doing this for a given file and hash string need:

```pascal
function CompareFileHashToMD5String(const FileName: TFileName;
  const MD5Str: string): Boolean;
begin
  Result := SameText(TPJMD5.CalculateFile(FileName), MD5Str);
end;
```

It is easier to see what's happening if we introduce a few local variables:

```pascal
function CompareFileHashToMD5String(const FileName: TFileName;
  const MD5Str: string): Boolean;
var
  S: string;
  D: TPJMD5Digest;
begin
  D := TPJMD5.CalculateFile(FileName);
  S := D;
  Result := SameText(S, MD5Str);
end;
```

> For more information about casting a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record to a string see [How To Get a Digest String](./GetDigestAsString.md).

The function gets the MD5 hash of the file using [_TPJMD5.CalculateFile_](../API/TPJMD5-CalculateFile.md). It then relies on the ability of [_TPJMD5Digest_](../API/TPJMD5Digest.md) to be cast to a string to get the string representation of the file's hash. Finally it compares the has string with the given string, _MD5Hash_ and returns `True` if they are the same and `False` if different. In the shortened version the result from [_TPJMD5.CalculateFile_](../API/TPJMD5-CalculateFile.md) is cast to a string because it is used in a string context (_SameText_ expects a string parameter).

But, we don't need to use _SameText_ at all because [_TPJMD5Digest_](../API/TPJMD5Digest.md) also provides [_Equal_](../API/TPJMD5Digest-Equal.md) and [_NotEqual_](../API/TPJMD5Digest-NotEqual.md) operator overloads that allow strings to be compared directly to [_TPJMD5Digest_](../API/TPJMD5Digest.md) records. Consequently the above function can be reduced to:

```pascal
function CompareFileHashToMD5String(const FileName: TFileName;
  const MD5Str: string): Boolean;
begin
  Result := (TPJMD5.CalculateFile(FileName) = MD5Str);
end;
```

Obviously there's now no need for the function unless you want it for documentary purposes - you can simply in line the comparison.

Finally you can compare a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record with a _TBytes_ array because of yet another overload of the [_Equal_](../API/TPJMD5Digest-Equal.md) and [_NotEqual_](../API/TPJMD5Digest-NotEqual.md) operators. To be equal the _TBytes_ array must have 16 elements and each byte must match the bytes of the [_TPJMD5Digest_](../API/TPJMD5Digest.md) record's _Bytes_ field.

You might do this when checking the content of an HTTP response against an MD5 digest. The MD5 digest arrives in the HTTP header as a Base64 encoded string. Say your decoding code converts this encoding into a byte array, and you have calculated the MD5 hash of the content, which is stored in a stream. Here's a little function that validates the content:

```pascal
function CheckContent(const MD5Bytes: TBytes; const Content: TStream): Boolean;
var
  D: TPJMD5Digest;
begin
  Content.Position := 0;
  D := TPJMD5.Calculate(Content);
  Result := D = MD5Bytes;
end;
```

> To learn more about casting [_TPJMD5Digest_](../API/TPJMD5Digest.md) to _TBytes_ see [How To Get Raw Digest Data](./GetDigestData.md).

This function gets the MD5 hash of the whole stream, using one of _TStream_ overloads of the [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#tstream-versions) method. Note that the stream is positioned at the start to ensure the whole stream is read.

## See Also

* How-tos:
  * [Get a digest string](./GetDigestAsString.md)
  * [Get raw digest data](./GetDigestData.md)
  * [Get the MD5 Hash of One or More Files](./HashFile.md)
  * [Get the MD5 Hash of a Stream](./HashStream.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)

## Links

* [How-To Guide Contents](../HowTo.md)
