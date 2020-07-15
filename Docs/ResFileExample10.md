# Example #10: Creating a resource file for use with Internet Explorer #

All the previous examples in this documentation are rather contrived examples that seek to focus on one or more related aspects of the functionality in the _PJResFile_ unit. This example is the first of three examples that aim to present useful code that uses several of the methods covered by other examples.

We will create a routine that takes a list of HTML and related files and creates a resource file which has a unique `RT_HTML` resource for each file. The resource contains the contents of the related file.

Such resources can be used for display in Internet Explorer, using the `res://` protocol. See the article ["How to create and use HTML resource files"](https://delphidabbler.com/articles/article-10) for more information on this subject.

Here is the code of the routine:

```pascal
procedure BuildHTMLResFile(const Files: TStrings; const ResFileName: string);
var
  ResFile: TPJResourceFile; // res file object
  Entry: TPJResourceEntry;  // a resource entry
  ResName: string;          // a resource name
  SrcFileName: string;      // a source file name
  SrcStm: TFileStream;      // source file stream
  FileIdx: Integer;         // loops thru Files
const
  LanguageID: Word = $0809; // UK English
begin
  ResFile := TPJResourceFile.Create;
  try
    // Loop through all source files
    for FileIdx := 0 to Pred(Files.Count) do
    begin
      // Record name of current file 0 should be fully specified
      SrcFileName := Files[FileIdx];
      // Construct resource name from source file name, without path. If the
      // resource name already exists repeatedly prepend underscores until a
      // unique name is found
      ResName := ExtractFileName(SrcFileName);
      while ResFile.EntryExists(RT_HTML, PChar(ResName), LanguageID) do
        ResName := '_' + ResName;
      // Create new resource for current file - this will be unique
      Entry := ResFile.AddEntry(RT_HTML, PChar(ResName), LanguageID);
      // Copy source file into resource data
      SrcStm := TFileStream.Create(SrcFileName, fmOpenRead);
      try
        Entry.Data.CopyFrom(SrcStm, 0);
        Entry.Data.Position := 0;
      finally
        SrcStm.Free;
      end;
    end;
    // Save resource file
    ResFile.SaveToFile(ResFileName);
  finally
    ResFile.Free; // this also frees resource entry objects
  end;
end;
```

The _Files_ parameter of the routine is a string list containing the (fully specified) names of files that are to be included in the resource file. The _ResFileName_ parameter receives the name of the output file which will be a valid 32 bit resource file.

The comments in the code should explain what is happening.

**Alternative Approach<sup>v1.1</sup>**

The above code can be simplified when using v1.1 of the Resource File Unit because of its new _[LoadDataFromFile](TPJResourceEntryLoadDataFromFile.md)_ method. Using this method we can replace all the stream processing code between the `// Copy source file into resource data` comment and the end of the loop with a single line of code:

```pascal
      ...
      // 5: Copy source file into resource data
      SrcStm := TFileStream.Create(SrcFileName, fmOpenRead);
      Entry.LoadDataFromFile(SrcFileName, False);
    end;
    ...
```

**Links:**

  * [Next Example](ResFileExample11.md)
  * [Previous Example](ResFileExample9.md)
  * Back to [List of Examples](ResFileExamples.md)