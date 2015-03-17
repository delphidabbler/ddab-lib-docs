# Example #3: Finding a resource #

To find a resource we use either the _[FindEntry](TPJResourceFileFindEntry.md)_ or _[FindEntryIndex](TPJResourceFileFindEntryIndex.md)_ methods of _[TPJResourceFile](TPJResourceFile.md)_. The difference is that _[FindEntry](TPJResourceFileFindEntry.md)_ returns the _[TPJResourceEntry](TPJResourceEntry.md)_ object for the entry (or `nil` if not found) while _[FindEntryIndex](TPJResourceFileFindEntryIndex.md)_ returns the index of the entry in the _[Entries](TPJResourceFileEntries.md)_ property.

Let us assume a resource file is loaded into the _[TPJResourceFile](TPJResourceFile.md)_ variable _ResFile_. We want to find a `RT_HTML` resource named `INDEX_HTML`. The following code checks if such a resource exists and displays its data size in a message box, or a message saying the resource doesn't exist. This first version of the code uses _[FindEntry](TPJResourceFileFindEntry.md)_:

```pascal
// Version using FindEntry
var
  ResFile: TPJResourceFile;
  Entry: TPJResourceEntry;
begin
  ...
  // Assume ResFile contains a loaded resource file
  ...
  Entry := ResFile.FindEntry(RT_HTML, 'INDEX_HTML', $0809);
  if Assigned(Entry) then
    ShowMessageFmt(
      'Data size for INDEX_HTML is %d',
      [Entry.DataSize]
    )
  else
    ShowMessage('Can''t find resource');
  ...
  // Don't forget to free ResFile at some stage.
end;
```

The second version of the code shows how the same result is obtained with _[FindEntryIndex](TPJResourceFileFindEntryIndex.md)_:

```pascal
// Version using FindEntryIdex
var
  ResFile: TPJResourceFile;
  Entry: TPJResourceEntry;
  Idx: Integer;
begin
  ...
  Idx := fResFile.FindEntryIndex(RT_HTML, 'INDEX_HTML');
  if Idx >= 0 then
  begin
    Entry := fResFile.Entries[Idx];
    ShowMessageFmt(
      'Data size for INDEX_HTML is %d', [Entry.DataSize]
    );
  end
  else
    ShowMessage('Can''t find resource');
  ...
end;
```

Note that we have used the "short form" of the _[FindEntry](TPJResourceFileFindEntry.md)_ and _[FindEntryIndex](TPJResourceFileFindEntryIndex.md)_ methods above: they find the first resource with the given type and name, irrespective of language id. The long versions of the methods find a specific resource type, name and language. For example the following code finds a `RT_HTML` resource named `INDEX_HTML` with a language id of `$0809`:

```pascal
// "Full" version of FindEntry
var
  ResFile: TPJResourceFile;
  Entry: TPJResourceEntry;
begin
  ...
  Entry := ResFile.FindEntryIndex(RT_HTML, 'HTMLRES_HTML', $0809);
  if Assigned(Entry) then
    ... etc ...
end;
```

**Links:**

  * [Next Example](ResFileExample4.md)
  * [Previous Example](ResFileExample2.md)
  * Back to [List of Examples](ResFileExamples.md)