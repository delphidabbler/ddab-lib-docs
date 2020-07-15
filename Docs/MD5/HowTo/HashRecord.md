# MD5 How-to: How To Get the MD5 Hash of a Record

In most cases you get the MD5 hash of a record by creating a new empty hash and adding the value of each field of the record to the hash. How you handle each field depends on its type. If one or more of the fields are also records then the technique is applied recursively.

Because we must add each field in turn to the hash we have to create a [_TPJMD5_](../API/TPJMD5.md) instance and use the [_TPJMD5.Process_](../API/TPJMD5-Process.md) method. We can't use [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md).

> For an explanation of the difference between [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) and [_TPJMD5.Process_](../API/TPJMD5-Process.md) see [here](./UseCalculateAndProcess.md).

For example, if you have a record of type _TFoo_ defined as:

```pascal
type
  TFoo = record
    B: Byte;
    AStr: AnsiString;
    IA: array[1..4] of Integer;
    SA: TArray<string>;
    R: record
      F1: Double;
      F2: Extended;
    end;
  end;
```

then the following function can be used to get its hash:

```pascal
function MD5OfTFoo(const Foo: TFoo): TPJMD5Digest;
var
  MD5: TPJMD5;
  S: string;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.Process(Foo.B, SizeOf(Foo.B));                 // ordinal type
    MD5.Process(Foo.AStr);                             // ANSI string type
    MD5.Process(Foo.IA[Low(Foo.IA)], SizeOf(Foo.IA));  // static array type
    for S in Foo.SA do                                 // dynamic reference array type
      MD5.Process(S, TEncoding.UTF8);
    // add fields of embedded record
    MD5.Process(Foo.R.F1, SizeOf(Foo.R.F1));           // floating point type
    MD5.Process(Foo.R.F2, SizeOf(Foo.R.F2));           // floating point type
    // return required digest
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

First we create our [_TPJMD5_](../API/TPJMD5.md) instance then add each field in turn to the hash using various techniques, each of which is explained in other how-to topics (see the link list below).

## Special Case

In the special case of a **packed** record containing only value fields of simple types we can use the untyped overload of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) to get the MD5 hash of the whole record at once.

Assume you have this record:

```pascal
type
  TBar = packed record
    B: Byte;
    W: Word;
    LW: LongWord;
  end;
```

then the following function will get the MD5 hash of a _TBar_ variable:

```pascal
function MD5OfTBar(const Bar: TBar): TPJMD5Digest;
begin
  Result := TPJMD5.Calculate(Bar, SizeOf(Bar));
end;
```

This works because the call to [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) gets the MD5 hash of all the bytes of _Bar_.

You should not use this technique with unpacked records because there will probably be padding bytes inserted in the record which may not be initialised to known values, which may change between executions. Since all the bytes of the record are processed the values of the padding bytes are included in the hash, giving unexpected results.

Furthermore the technique only works with value fields. Reference fields such as strings, objects and dynamic arrays only store pointers in the record, not the actual values. Therefore the pointers will be hashed, which is not what we want.

## See Also

* How-tos:
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
  * [Get the MD5 Hash of Ordinal Types](./HashOrdinalTypes.md)
  * [Get the MD5 Hash of a String](./HashString.md)
  * [Get the MD5 Hash of an Array](./HashArray.md)
  * [Get the MD5 hash of Floating Point Types](./HashFloatTypes.md)
* Programmers' Guide:
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md)
  * [_TPJMD5.Digest_](../API/TPJMD5-Digest.md)
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)

## Links

* [How-to Guide Contents](../HowTo.md)
