# MD5 How-to: How To Get Started

This is the "hello world" how-to where you'll learn just enough to generate your first MD5 digest.

We'll get the MD5 digest of the contents of the string `Hello world`. Here's the code:

```pascal
var
  Digest: TPJMD5Digest;
begin
  Digest := TPJMD5.Calculate('Hello world');
  ShowMessage(Digest);
end;
```

This code gets the MD5 hash of "Hello World" and displays its text representation in a message box.

The [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) method creates the MD5 hash (or digest) and stores it in the _Digest_ variable, which is a record of type [_TPJMD5Digest_](../API/TPJMD5Digest.md).

There are several overloaded versions of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) and the one used here is one of the Unicode string overloads. This one converts the string to its default ANSI encoding then takes the hash of that.

[_TPJMD5Digest_](../API/TPJMD5Digest.md) is also a little magical in that it automatically generates the string representation of itself when assigned to a string or when it is used in a string context. Since _ShowMessage_ takes a string parameter _Digest_ converts itself into its string representation, which is displayed in the dialog box.

## See Also

* How-tos:
  * [Get a digest string](./GetDigestAsString.md)
  * [Get raw digest data](./GetDigestData.md)
  * [Compare two digests](./CompareDigests.md)
  * [Get the MD5 hash of a string](./HashString.md)
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#unicode-string-versions
) (Unicode overloads)

## Links

* [How-to Guide Contents](../HowTo.md)
