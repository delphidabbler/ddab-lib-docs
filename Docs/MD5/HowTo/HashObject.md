# MD5 How-to: How To Get the MD5 Hash of an Object

To get the MD5 hash of an object you must use all the data that uniquely identifies the object. This usually means accessing the object's fields and adding each one to the hash, in a similar way as that for [records](./HashRecord.md). You will usually do this by reading public or published properties.

For example, if you have a class, _TFoo_:

```pascal
type
  TFoo = class(TObject)
  private
    fField1: Integer;
    fField2: string;
  public
    // methods and constructor here
    property Prop1: Integer read fField1;
    property Prop2: string read fField2;
  end;
```

then the following function can be used to get the required hash:

```pascal
function MD5OfTFoo(const Foo: TFoo): TPJMD5Digest;
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.Process(Foo.Prop1, SizeOf(Foo.Prop1));  // ordinal type
    MD5.Process(Foo.Prop2, TEncoding.UTF8);     // string type
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

> Because we're adding more than one field to the hash we can't use [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md). For an explanation see [here](./UseCalculateAndProcess.md).

First we create our [_TPJMD5_](../API/TPJMD5.md) instance then add each field in turn to the hash using various overloads of the [_TPJMD5.Process_](../API/TPJMD5-Process.md) method.  The technique used to add each field to the hash depends on the type of the field. Different techniques are explained in other how-to topics.

Another approach is to modify or subclass the object to provide a MD5 hash method that returns the hash. This has the advantage of being able to reach any fields that aren't publicly available. For example we can add a _MD5Hash_ method to _TFoo_ as follows:

```pascal
type
  TFoo = class(TObject)
  private
    fField1: Integer;
    fField2: string;
  public
    // methods and constructor here
    property Prop1: Integer read fField1;
    property Prop2: string read fField2;
    function MD5Hash: TPJMD5Digest;
  end;

...

function TFoo.MD5Hash: TPJMD5Digest;
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.Process(fField1, SizeOf(fField1));
    MD5.Process(fField2, TEncoding.UTF8);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

In this code we can access the fields directly rather than via properties.

## See Also

* How-tos:
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
  * [Get the MD5 Hash of a Record](./HashRecord.md)
  * [Get the MD5 Hash of Ordinal Types](./HashOrdinalTypes.md)
  * [Get the MD5 Hash of a String](./HashString.md)
* Programmers' Guide:
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md)
  * [_TPJMD5.Digest_](../API/TPJMD5-Digest.md)
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)

## Links

* [How-to Guide Contents](../HowTo.md)
