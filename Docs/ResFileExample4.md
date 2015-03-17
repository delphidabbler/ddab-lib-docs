# Example #4: Listing specific resources from a file #

We can use the _[IsMatching](TPJResourceEntryIsMatching.md)_ method of _[TPJResourceEntry](TPJResourceEntry.md)_ to check if a specific resource matches some given criteria. _[IsMatching](TPJResourceEntryIsMatching.md)_ can match just a resource type, a resource type and name or it can uniquely identify a resource in a file by matching its type, name and language id.

Like _[TPJResourceFile.FindEntry](TPJResourceFileFindEntry.md)_, the language id parameter is optional. The resource name parameter can be nil if we don't want to specify the resource name in the match.

Using _[IsMatching](TPJResourceEntryIsMatching.md)_, we can list all the `RT_HTML` resources from a resource file in a _TMemo_ control with this code:

```pascal
var
  ResFile: TPJResourceFile;
  Entry: TPJResourceEntry;
  Idx: Integer;
begin
  ...
  // Assume ResFile contains a loaded resource file
  ...
  for Idx := 0 to Pred(ResFile.EntryCount) do
  begin
    Entry := ResFile.Entries[Idx];
    if Entry.IsMatching(RT_HTML, nil) then
      Memo1.Lines.Add(
        Format('%s', [ResIDToStr(Entry.ResName)])
      );
  end;
  ...
end;
```

To list just the different language versions of the `RT_HTML` resource named `'INDEX_HTML'` we simply change the _[IsMatching](TPJResourceEntryIsMatching.md)_ method call in the for loop to:

```pascal
Entry.IsMatching(RT_HTML, 'INDEX_HTML')
```

Finally, to list all the `RT_HTML` resources with language id `$0809`, regardless of name, we can pass `nil` as the _ResName_ parameter and specify the language id as the final parameter. With these changes the _[IsMatching](TPJResourceEntryIsMatching.md)_ method call becomes:

```pascal
Entry.IsMatching(RT_HTML, nil, $0809)
```

**Links:**

  * [Next Example](ResFileExample5.md)
  * [Previous Example](ResFileExample3.md)
  * Back to [List of Examples](ResFileExamples.md)