#summary Resource File Unit Example 9.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Example #9: Saving a resource file =

Once you have created or modified a resource file object there comes a time when you need to save it somewhere. To do this we simply use the _[TPJResourceFileSaveToFile SaveToFile]_ or _[TPJResourceFileSaveToStream SaveToStream]_ methods of _[TPJResourceFile TPJResourceFile]_.

The following code shows how to use _[TPJResourceFileSaveToFile SaveToFile]_:

{{{
var
  ResFile: TPJResourceFile;
begin
  // Assume ResFile references a valid object
  ...
  // Save the file to 'MyResource.res'
  ResFile.SaveToFile('MyResource.res');
end;
}}}

The next code snippet shows how accomplish the same thing using _[TPJResourceFileSaveToStream SaveToStream]_:

{{{
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
}}}

In real life we would just use the code in the first fragment, but this suffices as an example of using _[TPJResourceFileSaveToStream SaveToStream]_.

*Links:*

  * [ResFileExample10 Next Example]
  * [ResFileExample8 Previous Example]
  * Back to [ResFileExamples List of Examples]
