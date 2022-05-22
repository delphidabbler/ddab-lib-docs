# Example #1: Loading a resource file #

In this first example we demonstrate how to create a resource file object and how to load a file into it. The following code fragment shows how this is done.

```pascal
var
  ResFile: TPJResourceFile;
  ...
begin
  ResFile := TPJResourceFile.Create;
  try
    ResFile.LoadFromFile('MyResFile.res');
    ...
    // Do something with resource file object
    ...
  finally
    ResFile.Free;
  end;
end;
```

First we create a _[TPJResourceFile](TPJResourceFile.md)_ object and then use its _[LoadFromFile](TPJResourceFileLoadFromFile.md)_ method read a file from disk. We then process the file in some way and once we are finished we free the resource file object. That's all there is to it. Note that if the given file does not contain a valid 32 bit resource file an exception will be raised.

We can also read resource data from a stream rather than loading from file by using the _[LoadFromStream](TPJResourceFileLoadFromStream.md)_ method of _[TPJResourceFile](TPJResourceFile.md)_ in place of _[LoadFromFile](TPJResourceFileLoadFromFile.md)_. Here's an example that is functionally the same as the one above, but uses streams.

```pascal
var
  ResFile: TPJResourceFile;
  Stream: TStream;
  ...
begin
  ResFile := TPJResourceFile.Create;
  try
    Stream := TFileStream.Create('MyResFile.res', fmOpenRead);
    try
      ResFile.LoadFromStream(Stream);
    finally
      Stream.Free;
    end;
    ...
    // Do something with resource file object
    ...
  finally
    ResFile.Free;
  end;
end;
```

Of course, in real life, we would use the code in the first listing, but this suffices as an example of using _[LoadFromStream](TPJResourceFileLoadFromStream.md)_.

**Links:**

* [Next Example](ResFileExample2.md)
* Back to [List of Examples](ResFileExamples.md)
