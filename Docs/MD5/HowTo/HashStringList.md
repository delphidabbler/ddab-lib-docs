# MD5 How-to: How To Get the MD5 Hash of a String List

> This how-to involves getting the MD5 hash of Unicode strings which is explained [here](./HashString.md)
>
> It also assumes you understand the difference between the [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md) and [_TPJMD5.Process_](../API/TPJMD5-Process.md) methods which is explained [here](./UseCalculateAndProcess.md).

There are two possible ways to create a hash of a _TStringList_ object:

1. Convert the string list to text and take the hash of the result.
2. Take each string from the list and add one at a time to the hash.

Each of these approaches will give a different hash, so you need to decide on one approach and stick to it if you want have repeatable results.

To see the differences, start a new Delphi VCL forms application and drop two edit controls on the form. Create the following _FormCreate_ event handler:

```pascal
procedure TForm1.FormCreate(Sender: TObject);
var
  D: TPJMD5Digest;
  MD5: TPJMD5;
  Strings: TStrings;
  S: string;
begin
  Strings := TStringList.Create;
  Strings.Add('The');
  Strings.Add('cat');
  Strings.Add('sat');
  Strings.Add('on');
  Strings.Add('the');
  Strings.Add('mat');

  // 1st approach
  Strings.LineBreak := #13#10;
  D := TPJMD5.Calculate(Strings.Text, TEncoding.UTF8);
  Edit1.Text := D;

  // 2nd approach
  MD5 := TPJMD5.Create;
  try
    for S in Strings do
      MD5.Process(S, TEncoding.UTF8);
    Edit2.Text := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

> The reason why a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record can be assigned to the string _Text_ property of the edit controls in the above code is explained in the [How to Get a digest string](./GetDigestAsString.md) how-to.

Running this program displays the following values in the edit controls:

1. `c8b029b7698b23a5962e7cc21a75653a` (MD5 of _Strings.Text_)
2. `780c94281a0b1e10395098c690a91d26` (MD5 of each string in _Strings_)

The first approach converts the string list to text, with each line separated by the string stored in the _TStrings.LineBreak_ property. It then uses one of the Unicode overloads of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#unicode-string-versions) to get the required digest. The resulting hash includes the line break characters.

The second approach adds each string from the string list in turn to the same hash. It uses one of the [_TPJMD5.Process_](../API/TPJMD5-Process.md#unicode-string-versions) Unicode overloaded methods to do this.

There are advantages and disadvantages of each approach:

* The second approach gives the same MD5 hash if you insert empty lines into the string list.  This is because an empty string added to a hash makes no difference to it. (Try adding one or more `Strings.Add('xxx');` statements to the above code to check this). The first approach gives a different hash because of the extra line breaks included in the string (providing that the _TStrings.LineBreak_ property is not the empty string).

* With the first approach changing the _TStrings.LineBreak_ property will change the hash for the same string list. Therefore you must be careful to ensure that the line break is always the same. (Try changing the line `Strings.LineBreak := #13#10;` to `Strings.LineBreak := #10;`in the above code to confirm this).

* The first approach introduces additional data into the mix (the line breaks) meaning that the hash doesn't only relate to the list contents.

You must decide which of the approaches to use. If empty lines are not significant I would opt for the second approach as being more "pure". However if empty lines are significant I would use the first approach.

## See Also

* How-tos:
  * [Get a digest string](./GetDigestAsString.md)
  * [Get the MD5 hash of a string](./HashString.md)
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)
  * [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#unicode-string-versions) -- Unicode overloads
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md#unicode-string-versions) -- Unicode overloads

## Links

* [How-to Guide Contents](../HowTo.md)
