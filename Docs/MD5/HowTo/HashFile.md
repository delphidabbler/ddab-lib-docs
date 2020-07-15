# MD5 How-to: How To Get the MD5 Hash of One or More Files

## Get the hash of a single file

It is very easy to get the hash of a single file because [_TPJMD5_](../API/TPJMD5.md) defines the [_TPJMD5.CalculateFile_](../API/TPJMD5-CalculateFile.md) class method just for that purpose.

To see how to do this start a new Delphi VCL forms application and drop a _TOpenDialog_ and a _TButton_ control on the form. Give the button the following _OnClick_ event handler:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  D: TPJMD5Digest;
begin
  if OpenDialog1.Execute then
  begin
    D := TPJMD5.CalculateFile(OpenDialog1.FileName);
    Label1.Caption := D;
  end;
end;
```

> The reason why a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record can be assigned to the label's _Caption_ property in the above code is explained [here](./GetDigestAsString.md).

Run the program and click the button to display the file open dialog box. Select a file and open it. The MD5 hash of the file appears in the label. There may be a delay for large files.

## Get the hash of multiple files

You may occasionally need to get a single MD5 hash of a group of files. An example might be all the files in a directory.

The [_TPJMD5.CalculateFile_](../API/TPJMD5-CalculateFile.md) class method can't be used because it takes only a single file as a parameter and provides no means to add more files to the resulting hash.

This is a little more complex than getting the MD5 of a single file because we need to add the contents of each file to the same hash. Whenever we need to add more than once data item to a MD5 hash we must create a [_TPJMD5_](../API/TPJMD5.md) instance, repeatedly add data to the hash and then read the resulting hash from the [_TPJMD5.Digest_](../API/TPJMD5-Digest.md) property.

> [_TPJMD5.ProcessFile_](../API/TPJMD5-ProcessFile.md) buffers file reads. The buffer size can be modified. See [Change the read buffer size](./ChangeReadBufferSize.md) for more information.

Here is a function that takes a list of file names to be hashed and returns the required hash as a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record. The file names are passed to the function in a string list. [_TPJMD5.ProcessFile_](../API/TPJMD5-ProcessFile.md) is called repeatedly to add the contents of each file to the hash.

```pascal
function GetMD5OfFiles(const Files: TStrings): TPJMD5Digest;
var
  MD5: TPJMD5;
  FileName: string;
begin
  MD5 := TPJMD5.Create;
  try
    for FileName in Files do
      MD5.ProcessFile(FileName);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

That just leaves the problem of getting the list of files. For the sake of brevity we will just select one or more files from a file open dialog box. Return to the program that demonstrate getting the hash of a single file. Add the _GetMD5OfFiles_ function and change the button's _OnClick_ event handler to:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  D: TPJMD5Digest;
begin
  OpenDialog1.Options := OpenDialog1.Options + [ofAllowMultiSelect];
  if OpenDialog1.Execute then
  begin
    D := GetMD5OfFiles(OpenDialog1.Files);
    Label1.Caption := D;
  end;
end;
```

Run the program, click the button and select more than one file from the file open dialog box. Open the files and the MD5 of all the files will be displayed in the label. (This may take some time to appear if there are a lot of files or if they are large.)

## See Also

* How-tos:
  * [Get a digest string](./GetDigestAsString.md)
  * [Change the read buffer size](./ChangeReadBufferSize.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)
  * [_TPJMD5.CalculateFile_](../API/TPJMD5-CalculateFile.md)
  * [_TPJMD5.ProcessFile_](../API/TPJMD5-ProcessFile.md)

## Links

* [How-to Guide Contents](../HowTo.md)
