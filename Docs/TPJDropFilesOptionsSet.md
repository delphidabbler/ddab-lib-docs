# TPJDropFilesOptions set and TPJDropFilesOption enumeration #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

```pascal
type
  TPJDropFilesOptions = set of TPJDropFilesOption;
  
  TPJDropFilesOption = (dfoIncFiles, dfoIncFolders, dfoRecurseFolders);
```

## Description ##

_TPJDropFilesOptions_ is a set of _TPJDropFilesOption_ values that specify the processing and filtering to be applied to dropped files. _TPJDropFilesOptions_ is the type of the _Options_ property of the various drop files components. Possible values are:

| Option        | Description |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| `dfoIncFiles` | When this option is specified ordinary files are included in the list of dropped files. If the option is not present ordinary files are excluded. |
| `dfoIncFolders` | Including this option causes folders to be included in the list of dropped files. Folders are excluded if the option is not set. |
| `dfoRecurseFolders` | In the absence of this option only the files actually dropped are made available via the _Files_ property (subject to presence of `dfoIncFile` and `dfoIncFolders`). When this option is set all folders in the list of dropped files are scanned and the files and sub-folders they contain are also recorded. This scan continues recursively through all sub-folders. |

It makes no sense to omit both the `dfoIncFiles` and `dfoIncFolders` options since no files will pass the filter.
