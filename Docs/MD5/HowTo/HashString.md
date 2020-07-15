# MD5 How-to: How To Get the MD5 Hash of a String

[_TPJMD5_](../API/TPJMD5.md) can calculate the MD5 hash of three of Delphi's string types:

* [Unicode](#unicode-strings) strings
* [Wide](#wide-strings) strings
* [Ansi](#ansi-strings) strings
* [Short](#short-strings) strings

There are overloads of the [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) and [_TPJMD5.Process_](../API/TPJMD5-Process.md) methods that can be used to create MD5 hashes of each string type.

> Code examples in this how-to all use [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) because it lends itself to more concise code, but [_TPJMD5.Process_](../API/TPJMD5-Process.md) can be used for the same purpose. For details of the differences see [Understand the Calculate and Process methods](./UseCalculateAndProcess.md).

## Unicode strings

There are two overloads of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#unicode-string-versions) that deal with Unicode strings, one that takes a single Unicode string parameter and another that takes an additional _TEncoding_ parameter.

The single parameter versions of the methods always converts the given string to its default ANSI encoding before calculating the hash. The two parameter versions apply the specified encoding to the string before calculating the hash.

To see this in action, create a new Delphi VCL forms application and drop five _TEdit_ controls on the form. Implement the _FormCreate_ event handler as follows:

```pascal
procedure TForm1.FormCreate(Sender: TObject);
var
  D: TPJMD5Digest;
const
  S = 'Iñtërnâtiônàlizætiøn';
begin
  D := TPJMD5.Calculate(S);
  Edit1.Text := D;
  D := TPJMD5.Calculate(S, TEncoding.Default);
  Edit2.Text := D;
  D := TPJMD5.Calculate(S, TEncoding.UTF8);
  Edit3.Text := D;
  D := TPJMD5.Calculate(S, TEncoding.Unicode);
  Edit4.Text := D;
  D := TPJMD5.Calculate(S, TEncoding.ASCII);
  Edit5.Text := D;
end;
```

> The reason why a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record can be assigned to the edit controls' _Text_ property is explained in [How to Get a digest string](./GetDigestAsString.md).

This code places a string representation of the 5 MD5 hashes in the edit controls. On my UK English system I get:

1. `580e27689cf5accd2f6ea979f9f3b11c` - default ANSI encoding (single parameter version of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#unicode-string-versions))
2. `580e27689cf5accd2f6ea979f9f3b11c` - explicit default ANSI encoding
3. `e5e628206e73b1ae69b37fc69762a1e1` - explicit UTF-8 encoding
4. `0e52e06ecd5bd0c61eeb52c19263946a` - explicit Unicode (little endian) encoding (UTF-16LE)
5. `70b4903abcb62ace84264ad0443ae759` - explicit ASCII encoding

Your mileage may vary in that the first two hashes will depend on your locale and hence which ANSI code page is used for the default encoding.

## Wide strings

[_TPJMD5_](../API/TPJMD5.md) provides one overload of the [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#widestring-version) method that processes _WideString_ strings. Wide strings are encoded in UTF-16 little endian (LE) format with each character occupying two bytes.

We'll exercise [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#widestring-version) by creating a new Delphi VCL forms application that contains a single edit control and the following _FormCreate_ event handler:

```pascal
procedure TForm1.FormCreate(Sender: TObject);
var
  D: TPJMD5Digest;
const
  S: WideString = 'Iñtërnâtiônàlizætiøn';

begin
  D := TPJMD5.Calculate(S);
  Edit1.Text := D;
end;
```

Running this code gives me the result:

* `0e52e06ecd5bd0c61eeb52c19263946a`

which is the same as result 4 in the [Unicode strings](#unicode-strings) section. This is as expected because UTF-16LE is used as the encoding in both cases.

## Ansi strings

There's just one overload of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#ansi-string-version) that handles Ansi strings. It takes a single RawByteString parameter, meaning it doesn't care what the code page of the Ansi string is.

We'll demonstrate this by getting the MD5 hash of two Ansi strings, one with the default code page and one UTF8 string.

Create a new Delphi VCL forms application and this time drop two edit controls on the form. Create a _FormCreate_ event handler as follows:

```pascal
procedure TForm1.FormCreate(Sender: TObject);
var
  D: TPJMD5Digest;
type
  ASCIIString = type AnsiString(20127);
const
  SANSI: AnsiString = 'Iñtërnâtiônàlizætiøn';
  SUTF8: UTF8String = 'Iñtërnâtiônàlizætiøn';
  SASCII: ASCIIString = 'Iñtërnâtiônàlizætiøn';
begin
  D := TPJMD5.Calculate(SANSI);
  Edit1.Text := D;
  D := TPJMD5.Calculate(SUTF8);
  Edit2.Text := D;
  D := TPJMD5.Calculate(SASCII);
  Edit3.Text := D;
end;
```

When I run this program on my UK English system I get:

1. `580e27689cf5accd2f6ea979f9f3b11c` - default code page
2. `e5e628206e73b1ae69b37fc69762a1e1` - UTF8
3. `70b4903abcb62ace84264ad0443ae759` - ASCII

Compare these with results 1 (or 2) and 3 for the [Unicode string](#unicode-strings) results and you will see they are the same, as you would expect.

## Short strings

As with Ansi strings there is just one overload of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#shortstring-version) that handles _ShortString_ strings. These strings always use the default Ansi code page.

Create a similar VCL forms application as before with just the one edit control this time. The _FormCreate_ method is now:

```pascal
procedure TForm1.FormCreate(Sender: TObject);
var
  D: TPJMD5Digest;
const
  S: ShortString = 'Iñtërnâtiônàlizætiøn';
begin
  D := TPJMD5.Calculate(S);
  Edit1.Text := D;
end;
```

Running the program on the expected UK English system gives the result:

* `580e27689cf5accd2f6ea979f9f3b11c`

As you will by now expect this is the same as the results in the previous sections for the default Ansi code page.

## See Also

* How-tos:
  * [Get a digest string](./GetDigestAsString.md)
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md)
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)

## Links

* [How-to Guide Contents](../HowTo.md)
