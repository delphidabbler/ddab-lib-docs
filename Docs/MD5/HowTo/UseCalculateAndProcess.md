# MD5 How-to: Understand the Calculate and Process methods

[_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) and [_TPJMD5.Process_](../API/TPJMD5-Process.md) are methods of [_TPJMD5_](../API/TPJMD5.md) within similar purposes but some significant differences.

Both methods are used in creating MD5 hashes. Both have numerous overloaded versions.

## Process

[_TPJMD5.Process_](../API/TPJMD5-Process.md) is used to add one or more items of data to a [_TPJMD5_](../API/TPJMD5.md) instance. When all the data has been added the resulting hash (or digest) is read using the instance's [_TPJMD5.Digest_](../API/TPJMD5-Digest.md) property.

Here's an example where we add data from a byte array and an ANSI string to the same MD5 hash, using the _AnsiString_ and one of the _TBytes_ overloads of [_TPJMD5.Process_](../API/TPJMD5-Process.md):

```pascal
function Foo(const S: AnsiString; const B: TBytes): TPJMD5Digest;
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.Process(S);
    MD5.Process(B);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

You can mix and match any data in a single hash. However it is much more common to get the hash of just a single data item, for example of the contents of a _TBytes_ array, like this:

```pascal
function Bar(const B: TBytes): TPJMD5Digest;
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.Process(B);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

Because this is so common an idiom a short-cut would be great. And that's where [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) comes in.

## Calculate

[_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) is set of overloaded class function gets the MD5 hash of a single data item without the need to construct a [_TPJMD5_](../API/TPJMD5.md) instance. For every overload of [_TPJMD5.Process_](../API/TPJMD5-Process.md) there is a matching [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) overload.

Effectively all call to [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) is equivalent to this code:

```pascal
function TPJMD5.Calculate(param-list): TPJMD5Digest; overload;
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.Process(param-list);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

For example, we can now re-implement the _Bar_ function from above using a _TBytes_ overload of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#byte-array-version) like this:

```pascal
function Bar(const B: TBytes): TPJMD5Digest;
begin
  Result := TPJMD5.Calculate(B);
end;
```

Of course you wouldn't bother implementing _Bar_ now, you would just make the direct call to [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#byte-array-version).

## See Also

* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md)
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)

## Links

* [How-to Guide Contents](../HowTo.md)
