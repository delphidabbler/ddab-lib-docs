#summary Description of the TPJWildCardFileFilter.Accept method
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Accept method =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJWildCardFileFilter TPJWildCardFileFilter]_

{{{
function Accept(
  const FilePath: string; const IsFolder: Boolean
): Boolean; override;
}}}

== Description ==

Checks whether a given file or folder passes though the filter.

This method is called by the filter's owning drop files component whenever files are dropped. It is called once for each dropped file or folder and returns true if the file or folder passes through the filter and false if not. _!FilePath_ is the fully qualified path of the file or folder concerned, while _!IsFolder_ indicates whether _!FilePath_ is a file or folder. 

For a file to pass through the filter its file or folder name (not the path) must match the wild card specified in the _[TPJWildCardFileFilterWildCard WildCard]_ property.

This method is used internally by the drop files components. There is no reason to call the method from program code unless to discover whether a file or folder will pass the filter.
