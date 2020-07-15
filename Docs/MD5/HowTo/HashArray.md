# MD5 How-to: How To Get the MD5 Hash of an Array

> This how-to assumes you know how and when to use [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) and [_TPJMD5.Process_](../API/TPJMD5-Process.md). For details see [here](./UseCalculateAndProcess.md).

Several different techniques are needed to get an MD5 hash of an array. Which technique to use depends on both the kind of array (static or dynamic) and on the type of the array's elements.

This how-to gives several solutions:

* [TBytes arrays](#tbytes-arrays) -- special case: [_TPJMD5_](../API/TPJMD5.md) has built-in support.
* [Arrays of simple types](#arrays-of-simple-types)
* [Arrays of reference types](#arrays-of-reference-types)
* [Arrays of other types](#arrays-of-other-types)

## TBytes arrays

The simplest case is that of _TBytes_ arrays because [_TPJMD5_](../API/TPJMD5.md) can natively handle getting the hash of a _TBytes_ array.

Here's an example that uses [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#byte-array-versions), because it leads to more concise code than using  [_TPJMD5.Process_](../API/TPJMD5-Process.md#byte-array-versions) would.

```pascal
var
  A: TBytes;
  D: TPJMD5Digest;
begin
  A := TBytes.Create(1,2,3,4,5,6,7,8);
  D := TPJMD5.Calculate(A);
  ShowMessage(D); // D is implicitly cast to a string
end;
```

> Learn about casting [_TPJMD5Digest_](../API/TPJMD5Digest.md) to a string [here](./GetDigestAsString.md).

_TBytes_ is the only array type for which [_TPJMD5_](../API/TPJMD5.md) provides direct support. For all other array types you have to do some more work.

## Arrays of simple types

Arrays of simple types (i.e. ordinal and real types) are quite simple to handle.

Each element contains an actual value (not a reference or pointer) and the elements are always contiguous in memory (regardless of use of the **packed** keyword and the [_$ALIGN_](http://docwiki.embarcadero.com/RADStudio/en/Align_fields_%28Delphi%29) compiler directive [[ref]](http://stackoverflow.com/questions/4583985/are-where-any-difference-between-array-and-packed-array-in-delphi). Therefore we can just get the MD5 of the block of memory occupied by the array. We use the untyped overloads of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) and [_TPJMD5.Process_](../API/TPJMD5-Process.md#untyped-buffer-version) to do this.

Exactly how we proceed depends on if the array is static or dynamic.

### Static arrays

If the array is static (i.e. the size is specified at compile time) code like the following should be used. In this case we are using the untyped overload of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version).

```pascal
const
  A: array[1..5] of Extended = (0.42, 4.2, 42.0, 420.0, 4200.0);
var
  D: TPJMD5Digest;
begin
  D := TPJMD5.Calculate(A[Low(A)], SizeOf(A));
  ShowMessage(D); // D is implicitly cast to a string
end;
```

The block of memory containing the array elements starts at the location of the first array element, which is given by `Low(A)`. This is passed as the first parameter to [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version). The method's second parameter requires the size of memory to be processed: we get this from _SizeOf_ function which returns the total size of the array in bytes.

This example uses the _Extended_ real type, but the array element can be any simple type.

### Dynamic arrays

If the array is dynamic then a slightly different approach is required because we can't use _SizeOf_ to get the size of the array at compile time. Here's the code for dynamic arrays, this time using the ordinal type _Word_:

```pascal
type
  TWordArray = array of Word;
var
  D: TPJMD5Digest;
  A: TWordArray;
begin
  A := TWordArray.Create(5,4,3,2,1);
  D := TPJMD5.Calculate(Pointer(A)^, Length(A) * SizeOf(Word));
  ShowMessage(D); // D is implicitly cast to a string
end;
```

Since dynamic array variables are essentially pointers we get the first parameter of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#untyped-buffer-version) by casting _A_ to a pointer and then dereferencing it. The size of the data required as the second parameter is found by multiplying the length of the array by the size of one element.

This technique also works for the _TArray&lt;T&gt;_ generic array type. To check this delete the type definition in the above code then replace all occurrences of _TWordArray_ with _TArray&lt;Word&gt;_.

## Arrays of reference types

If you have an array of reference types, such as strings, objects, pointers and dynamic array you need to iterate all the elements in the array and add each one to the MD5 hash in turn, using whatever mechanism you would normally use to get the hash of the element's type. This means you can't use [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) because you must be able to add more than one element to the same hash, therefore [_TPJMD5.Process_](../API/TPJMD5-Process.md) must be used.

Here is some boilerplate code:

```pascal
var
  MD5: TPJMD5;
  A: array of TElemType; // could also be TArray<TElemType> or static array
  Elem: TElemType;
begin
  // initialise array here
  MD5 := TPJMD5.Create;
  try
    for Elem in A do
    begin
      // add Elem to MD5 hash here, ultimately calling Process()
    end;
    ShowMessage(MD5.Digest);
  finally
    MD5.Free;
  end;
end;
```

Here is a concrete example using a dynamic array of _AnsiString_ values:

```pascal
var
  MD5: TPJMD5;
  A: TArray<AnsiString>;
  Elem: AnsiString;
begin
  A := TArray<AnsiString>.Create('one', 'two', 'three', 'four', 'five');
  MD5 := TPJMD5.Create;
  try
    for Elem in A do
      MD5.Process(Elem);
    ShowMessage(MD5.Digest);
  finally
    MD5.Free;
  end;
end;
```

And here is a static array example using Unicode strings encoded in UTF-8:

```pascal
const
  A: array[1..5] of UnicodeString = (
    'one', 'two', 'three', 'four', 'five'
  );
var
  MD5: TPJMD5;
  Elem: UnicodeString;
begin
  MD5 := TPJMD5.Create;
  try
    for Elem in A do
      MD5.Process(Elem, TEncoding.UTF8);
    ShowMessage(MD5.Digest);
  finally
    MD5.Free;
  end;
end;
```

> Note that an array of strings with one or more elements containing the empty string will have the same hash as the same array without any empty elements. Therefore you may wish to concatenate the strings using some known delimiter and get the hash of the resulting string. This method will produce a different hash for arrays with empty elements. See [How To Get the MD5 Hash of a String List](./HashStringList.md) for a more detailed discussion of this problem.

If you have an array of objects then use the boilerplate code above and see the [How to Get the MD5 Hash of an Object](./HashObject.md) how-to for details of how to hash each object.

## Arrays of other types

### Records

If you have any array of records use the same boilerplate code presented in [Arrays of reference types](#arrays-of-reference-types) above and get the MD5 hash of each record element using the techniques presented in the [How to Get the MD5 Hash of a Record](./HashRecord.md) how-to.

### Short strings

For an array of Short strings we again iterate the array and use the _ShortString_ overload of [_TPJMD5.Process_](../API/TPJMD5-Process.md#shortstring-version) to get the hash of each string:

```pascal
const
  A: array[1..5] of ShortString = (
    'one', 'two', 'three', 'four', 'five'
  );
var
  MD5: TPJMD5;
  Elem: ShortString;
begin
  MD5 := TPJMD5.Create;
  try
    for Elem in A do
      MD5.Process(Elem);
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
  * [Get the MD5 Hash of Ordinal Types](./HashOrdinalTypes.md)
  * [Get the MD5 Hash of a String](./HashString.md)
  * [Get the MD5 Hash of an Object](./HashObject.md)
  * [Get the MD5 Hash of a Record](./HashRecord.md)
  * [Get a digest string](./GetDigestAsString.md)
* Programmers' Guide:
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md)
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)
  * [_TPJMD5.Digest_](../API/TPJMD5-Digest.md)
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)

## Links

* [How-to Guide Contents](../HowTo.md)
