#summary Resource File Unit Example 1.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Example #1: Loading a resource file =

In this first example we demonstrate how to create a resource file object and how to load a file into it. The following code fragment shows how this is done.

{{{
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
}}}

First we create a _[TPJResourceFile TPJResourceFile]_ object and then use its _[TPJResourceFileLoadFromFile LoadFromFile]_ method read a file from disk. We then process the file in some way and once we are finished we free the resource file object. That's all there is to it. Note that if the given file does not contain a valid 32 bit resource file an exception will be raised.

We can also read resource data from a stream rather than loading from file by using the _[TPJResourceFileLoadFromStream LoadFromStream]_ method of _[TPJResourceFile TPJResourceFile]_ in place of _[TPJResourceFileLoadFromFile LoadFromFile]_. Here's an example that is functionally the same as the one above, but uses streams.

{{{
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
}}}

Of course, in real life, we would use the code in the first listing, but this suffices as an example of using _[TPJResourceFileLoadFromStream LoadFromStream]_.

*Links:*

  * [ResFileExample2 Next Example]
  * Back to [ResFileExamples List of Examples]
