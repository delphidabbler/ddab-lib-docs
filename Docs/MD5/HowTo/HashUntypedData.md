# MD5 How-to: How To Get the MD5 Hash of Untyped Data

[_TPJMD5_](../API/TPJMD5.md) provides an overload of both the [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) and [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) methods that can be used to calculate the MD5 hash of untyped data.

The methods both take a reference to the untyped data item as the first parameter and the length of the data as the second parameter.

For example, if you have a pointer _P_ to some data that is 100 bytes long you would get its MD5 hash like this:

```pascal
var
  D: TPJMD5Digest;
  P: Pointer;
begin
  // set P to point to some 100 bytes of data
  // ...
  D := TPJMD5.Calculate(P^, 100);
  // ...
  // do something with D
end;
```

This example is admittedly rather contrived, but it is not uncommon to have pointers to data you for which you want the MD5 hash. The main thing to note is that you must deference the pointer before call the method.

> See the "How to get the MD5 hash of" topics for [ordinal types](./HashOrdinalTypes.md), [floats](./HashFloatTypes.md), [arrays](./HashArray.md) and [records](./HashRecord.md).

The main use for the Untyped overload of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) and [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) is in getting the MD5 hash of ordinal values, floating point values, packed records and arrays of both these items. This is covered in more detail in other how-to pages, so a simple example will suffice here.

Suppose you have an array of Extended values. You can use [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) to get a MD5 hash of each item in the array, one element at a time, like this:

```pascal
var
  AE: TArray<Extended>;
  E: Extended;
  MD5: TPJMD5;
begin
  AE := TArray<Extended>.Create(0.42, 4.2, 42.0, 420.0, 4200.0);
  MD5 := TPJMD5.Create;
  try
    for E in AE do
      MD5.Process(E, SizeOf(E));
    ShowMessage(MD5.Digest);  // uses of implicit cast of Digest to string
  finally
    MD5.Free;
  end;
end;
```

> The reason why a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record can be passed to _ShowMessage_ where a string argument is expected is explained [here](./GetDigestAsString.md).

Here we create an arbitrary array of _Extended_ values (using Delphi's _TArray&lt;T&gt;_ generic array type) and then iterate the array adding each _Extended_ element in turn to the MD5 hash. Finally we access the hash via the [_TPJMD5.Digest_](../API/TPJMD5-Digest.md) property, using the untyped overload of [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) and display it in a message box. Notice how an array element is passed as the method's first parameter and the size of the element is passed as the second. This adds all the bytes of the array element to the hash.

## See Also

* How-tos:
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
  * [Get the MD5 Hash of Ordinal Types](./HashOrdinalTypes.md)
  * [Get the MD5 Hash of Floating Point Types](./HashFloatTypes.md)
  * [Get the MD5 Hash of an Array](./HashArray.md)
  * [Get the MD5 Hash of a Record](./HashRecord.md)
  * [Get a digest string](./GetDigestAsString.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md)
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)
  * [_TPJMD5.Digest_](../API/TPJMD5-Digest.md)

## Links

* [How-to Guide Contents](../HowTo.md)
