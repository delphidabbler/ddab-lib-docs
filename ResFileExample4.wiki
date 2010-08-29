#summary Resource File Unit Example 4.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Example #4: Listing specific resources from a file =

We can use the _[TPJResourceEntryIsMatching IsMatching]_ method of _[TPJResourceEntry TPJResourceEntry]_ to check if a specific resource matches some given criteria. _[TPJResourceEntryIsMatching IsMatching]_ can match just a resource type, a resource type and name or it can uniquely identify a resource in a file by matching its type, name and language id.

Like _[TPJResourceFileFindEntry TPJResourceFile.FindEntry]_, the language id parameter is optional. The resource name parameter can be nil if we don't want to specify the resource name in the match.

Using _[TPJResourceEntryIsMatching IsMatching]_, we can list all the `RT_HTML` resources from a resource file in a _TMemo_ control with this code:

{{{
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
}}}

To list just the different language versions of the `RT_HTML` resource named `'INDEX_HTML'` we simply change the _[TPJResourceEntryIsMatching IsMatching]_ method call in the for loop to:

{{{
Entry.IsMatching(RT_HTML, 'INDEX_HTML')
}}}

Finally, to list all the `RT_HTML` resources with language id `$0809`, regardless of name, we can pass `nil` as the _!ResName_ parameter and specify the language id as the final parameter. With these changes the _[TPJResourceEntryIsMatching IsMatching]_ method call becomes:

{{{
Entry.IsMatching(RT_HTML, nil, $0809)
}}}

*Links:*

  * [ResFileExample5 Next Example]
  * [ResFileExample3 Previous Example]
  * Back to [ResFileExamples List of Examples]
