# MD5 How-to: How To Get the MD5 Hash of Floating Point Types

[_TPJMD5_](../API/TPJMD5.md) provides no direct means of getting the MD5 hash of floating point types. Instead we need to use the untyped overloads of the [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) and [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) methods.

> Working with untyped data is covered in [How To Get the MD5 Hash of Untyped Data](./HashUntypedData.md)

The general principle is the same as for [ordinal types](./HashOrdinalTypes.md) - you pass the floating point variable as the first parameter to [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) or [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) and the size of the variable as the second parameter.

A single example will suffice. Suppose you have a text file of the text representations of floating point numbers, with just one number per line. The following function gets the MD5 hash of all the (_Double_) numbers in the file. This hash will be different to taking the hash of the text file. It allows files with different representations of the same number (like `0.12` and `.12`) to have the same hash.

> The example in this how-to only uses [_TPJMD5.Process_](../API/TPJMD5-Process.md) because it allows more than one floating point to be added to the hash, but [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) can be used in the unlikely event you want to take the hash of just one variable. For details of the differences see [Understand the Calculate and Process methods](./UseCalculateAndProcess.md).

```pascal
function MD5OfFileOfFloats(const FileName: string): TPJMD5Digest;
var
  F: TextFile;
  Num: Double;
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    AssignFile(F, FileName);
    Reset(F);
    while not EOF(F) do
    begin
      ReadLn(F, Num);
      MD5.Process(Num, SizeOf(Num));
    end;
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

> Although this example uses the _Double_ type, it applies equally to any other floating point type, such as _Extended_.

## See Also

* How-tos:
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
  * [Get the MD5 Hash of Untyped Data](./HashUntypedData.md)
  * [Get the MD5 Hash of Ordinal Types](./HashOrdinalTypes.md)
* Programmers' Guide:
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md)
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)
  * [_TPJMD5.Digest_](../API/TPJMD5-Digest.md)

## Links

* [How-to Guide Contents](../HowTo.md)
