#summary Resource File Unit Example 7.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Example #7: Checking if a resource exists =

If you attempt to add a duplicate of an existing resource to a resource file an exception will be raised. To avoid this we may need to check if a resource already exists. This can be done with the _[TPJResourceFileEntryExists EntryExists]_ method of _[TPJResourceFile TPJResourceFile]_ as follows:

{{{
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
}}}

_[TPJResourceFileEntryExists EntryExists]_ can also be used to perform partial checks for entries. It can omit the name and / or the language id when searching for resources. You can take advantage of this behaviour to get some useful information about the resource file. Examples are:

  * Does the file contain any `RCDATA` resources?
  {{{
  if ResFile.EntryExists(RT_RCDATA, nil) then ...
  }}}

  * Does the file contain any `RCDATA` resources named `'FOO'`?
  {{{
  if ResFile.EntryExists(RT_RCDATA, 'FOO') then ...
  }}}

  * Does the file contain any `HTML` resources with language id `$0809`?
  {{{
  if ResFile.EntryExists(RT_HTML, nil, $0809) then ...
  }}}

*Links:*

  * [ResFileExample8 Next Example]
  * [ResFileExample6 Previous Example]
  * Back to [ResFileExamples List of Examples]
