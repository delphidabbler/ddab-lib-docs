# Example #9: Saving a resource file #

Once you have created or modified a resource file object there comes a time when you need to save it somewhere. To do this we simply use the _[SaveToFile](TPJResourceFileSaveToFile.md)_ or _[SaveToStream](TPJResourceFileSaveToStream.md)_ methods of _[TPJResourceFile](TPJResourceFile.md)_.

The following code shows how to use _[SaveToFile](TPJResourceFileSaveToFile.md)_:

```pascal
var
  ResFile: TPJResourceFile;
begin
  // Assume ResFile references a valid object
  ...
  // Save the file to 'MyResource.res'
  ResFile.SaveToFile('MyResource.res');
end;
```

The next code snippet shows how accomplish the same thing using _[SaveToStream](TPJResourceFileSaveToStream.md)_:

```pascal
var
  ResFile: TPJResourceFile;
  Stream: TStream;
begin
  // Assume ResFile references a valid object
  ...
  Stream := TFileStream.Create('MyResource.res', fmCreate);
  try
    ResFile.SaveToStream(Stream);
  finally
    Stream.Free;
  end;
end;
```

In real life we would just use the code in the first fragment, but this suffices as an example of using _[SaveToStream](TPJResourceFileSaveToStream.md)_.

**Links:**

  * [Next Example](ResFileExample10.md)
  * [Previous Example](ResFileExample8.md)
  * Back to [List of Examples](ResFileExamples.md)