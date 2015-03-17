# Example #7: Checking if a resource exists #

If you attempt to add a duplicate of an existing resource to a resource file an exception will be raised. To avoid this we may need to check if a resource already exists. This can be done with the _[EntryExists](TPJResourceFileEntryExists.md)_ method of _[TPJResourceFile](TPJResourceFile.md)_ as follows:

```pascal
var
  ResFile: TPJResourceFile;
  Entry: TPJResourceEntry;
begin
  ...
  // Assume ResFile references a valid object
  ...
  if not ResFile.EntryExists(RT_RCDATA, 'FORTYTWO', $0809) then
    Entry := ResFile.AddEntry(RT_RCDATA, 'FORTYTWO', $0809);
  ...
end;
```

_[EntryExists](TPJResourceFileEntryExists.md)_ can also be used to perform partial checks for entries. It can omit the name and / or the language id when searching for resources. You can take advantage of this behaviour to get some useful information about the resource file. Examples are:

  * Does the file contain any `RCDATA` resources?
```pascal
  if ResFile.EntryExists(RT_RCDATA, nil) then ...
```

  * Does the file contain any `RCDATA` resources named `'FOO'`?
```pascal
  if ResFile.EntryExists(RT_RCDATA, 'FOO') then ...
```

  * Does the file contain any `HTML` resources with language id `$0809`?
```pascal
  if ResFile.EntryExists(RT_HTML, nil, $0809) then ...
```

**Links:**

  * [Next Example](ResFileExample8.md)
  * [Previous Example](ResFileExample6.md)
  * Back to [List of Examples](ResFileExamples.md)