# Example #8: Deleting resources #

We can delete all resources from a resource file simply by calling the _[Clear](TPJResourceFileClear.md)_ method of _[TPJResourceFile](TPJResourceFile.md)_. In addition to deleting the resources _[Clear](TPJResourceFileClear.md)_ also frees all the _[TPJResourceEntry](TPJResourceEntry.md)_ instances.

```pascal
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
```

A single resource can be removed from the resource file using the _[TPJResourceFile.DeleteEntry](TPJResourceFileDeleteEntry.md)_ method. This checks if the resource file contains the resource and removes it from the file if so. However, the resource entry object **is not freed**. While this behaviour may be useful at times, it is not recommended for geral use. The preferred method is simply to free the resource entry instance. Freeing a _[TPJResourceEntry](TPJResourceEntry.md)_ object automatically removes it from the resource file.

So, to remove a single resource, _ResEntry_, from the resource file use the following code:

```pascal
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
```

**Links:**

  * [Next Example](ResFileExample9.md)
  * [Previous Example](ResFileExample7.md)
  * Back to [List of Examples](ResFileExamples.md)