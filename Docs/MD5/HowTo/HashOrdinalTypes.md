# MD5 How-to: How To Get the MD5 Hash of Ordinal Types

[_TPJMD5_](../API/TPJMD5.md) provides no direct means of getting the MD5 hash of ordinal types. Instead we need to use the untyped overloads of the [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) and [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) methods.

> Working with untyped data is covered in [How To Get the MD5 Hash of Untyped Data](./HashUntypedData.md)

The first example displays the MD5 hash of an _Int64_ data type:

```pascal
var
  D: TPJMD5Digest;
  I: Int64;
begin
  I := -1234567890123456789;
  D := TPJMD5.Calculate(I, SizeOf(I));
  ShowMessage(D);  // relies on implicit cast of TPJMD5Digest to string
end;
```

> The reason why a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record can be passed to _ShowMessage_ where a string argument is expected is explained [here](./GetDigestAsString.md).

We use the untyped overload of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) by passing _Int64_ variable _I_ as the first parameter and the size of _I_ in bytes as the second parameter.

This illustrates the general principle for getting the hash of any ordinal type: pass the ordinal variable as the first parameter to either [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) and [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) and pass the size of the variable as the second parameter.

The following example illustrates how this works with [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) - we get the MD5 hash of a _Word_, an _Integer_, and an enumerated type.

```pascal
type
  TDays = (Mon, Tue, Wed, Thu, Fri, Sat, Sun);
var
  MD5: TPJMD5;
  W: Word;
  I: Integer;
  D: TDays;
begin
  W := 42;
  I := -42;
  D := Thu;
  MD5 := TPJMD5.Create;
  try
    MD5.Process(W, SizeOf(W));
    MD5.Process(I, SizeOf(I));
    MD5.Process(D, SizeOf(D));
    ShowMessage(MD5.Digest);
  finally
    MD5.Free;
  end;
end;
```

## See Also

* How-tos:
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
  * [Get the MD5 Hash of Untyped Data](./HashUntypedData.md)
  * [Get a digest string](./GetDigestAsString.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md)
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)
  * [_TPJMD5.Digest_](../API/TPJMD5-Digest.md)

## Links

* [How-to Guide Contents](../HowTo.md)
