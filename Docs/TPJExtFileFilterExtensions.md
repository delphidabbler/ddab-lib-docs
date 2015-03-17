# Extensions property #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJExtFileFilter](TPJExtFileFilter.md)_

```pascal
property Extensions: string;
```

## Description ##

Filters out files without specified extensions.

The component can filter files, only accepting the names of files ending with the extensions specified in this property. If _Extensions_ is set to the empty string (the default) then file names are not filtered and all pass through.

Multiple extensions can be stored in the property by separating them with semi-colons. The dot preceeding extensions should be included. If any extensions are specified without the leading dot the character is automatically prepended. A property editor is supplied that enables the extension list to be built using a dialog box. This editor ensures that the extension string is formatted correctly.

Wildcards are not supported (see _[TPJWildCardFileFilter](TPJWildCardFileFilter.md)_ for wildcard support). Only extensions that completely match those specified in the property (ignoring case) pass through the filter.  Whether the filter applies to file names, folder names or both depends on the value of the _[Style](TPJExtFileFilterStyle.md)_ property.

### Example ###

To filter for files with `.htm`, `.html` or `.shtml` extensions set _Extensions_ to `'.htm;.html;.shtml'`.