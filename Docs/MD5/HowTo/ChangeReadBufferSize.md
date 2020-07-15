# MD5 How-to: How To Change the Read Buffer Size

[_TPJMD5_](../API/TPJMD5.md) uses a buffer when reading data from a stream or a file. By default the buffer has the size specified by the [_TPJMD5.DefReadBufferSize_](../API/TPJMD5-DefReadBufferSize.md) constant. You can change the buffer size by setting the [_TPJMD5.ReadBufferSize_](../API/TPJMD5-ReadBufferSize.md) property.

Here's an example function that gets the MD5 hash of a file using a specified buffer size:

```pascal
function MD5OfFile(const FileName: string;
  const BufSize: Integer): TPJMD5Digest;
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.ReadBufferSize := BufSize;
    MD5.ProcessFile(FileName);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

And here's a similar function that uses one of the _TStream_ overloads of [_TPJMD5.Process_](../API/TPJMD5-Process.md#tstream-versions) to get the MD5 hash of the whole of a stream using a given buffer size:

```pascal
function MD5OfStream(const Stm: TStream;
  const BufSize: Integer): TPJMD5Digest;
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.ReadBufferSize := BufSize;
    Stm.Position := 0;
    MD5.Process(Stm);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```

> Because you need a [_TPJMD5_](../API/TPJMD5.md) instance in order to access the [_TPJMD5.ReadBufferSize_](../API/TPJMD5-ReadBufferSize.md) property you can't change the buffer size when using the [_TPJMD5.CalculateFile_](../API/TPJMD5-CalculateFile.md) class method or the _TStream_ overload of [_TPJMD5.Calculate_](../API/TPJMD5-Calculate.md#tstream-versions).

## See Also

* How-tos:
  * [Understand the Calculate and Process methods](./UseCalculateAndProcess.md)
  * [Get the MD5 Hash of One or More Files](./HashFile.md)
  * [Get the MD5 Hash of a Stream](./HashStream.md)
* Programmers' Guide:
  * [_TPJMD5.Process_](../API/TPJMD5-Process.md)
  * [_TPJMD5.ProcessFile_](../API/TPJMD5-ProcessFile.md)
  * [_TPJMD5.Digest_](../API/TPJMD5-Digest.md)
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)

## Links

* [How-to Guide Contents](../HowTo.md)
