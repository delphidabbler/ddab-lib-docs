#summary Resource File Unit Example 8.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Example #8: Deleting resources =

We can delete all resources from a resource file simply by calling the _[TPJResourceFileClear Clear]_ method of _[TPJResourceFile TPJResourceFile]_. In addition to deleting the resources _[TPJResourceFileClear Clear]_ also frees all the _[TPJResourceEntry TPJResourceEntry]_ instances.

{{{
var
  ResFile: TPJResourceFile;
begin
  ...
  // Assume ResFile is a valid resource file object
  ...
  // Delete all resources and free them
  ResFile.Clear;
  ...
end;
}}}

A single resource can be removed from the resource file using the _[TPJResourceFileDeleteEntry TPJResourceFile.DeleteEntry]_ method. This checks if the resource file contains the resource and removes it from the file if so. However, the resource entry object *is not freed*. While this behaviour may be useful at times, it is not recommended for geral use. The preferred method is simply to free the resource entry instance. Freeing a _[TPJResourceEntry TPJResourceEntry]_ object automatically removes it from the resource file.

So, to remove a single resource, _!ResEntry_, from the resource file use the following code:

{{{
var
  Entry: TPJResourceEntry;
begin
  ...
  // Assume ResEntry references a valid object
  ...
  // Delete the object from its resource file and free it
  Entry.Free;
  ...
end;
}}}

*Links:*

  * [ResFileExample9 Next Example]
  * [ResFileExample7 Previous Example]
  * Back to [ResFileExamples List of Examples]
