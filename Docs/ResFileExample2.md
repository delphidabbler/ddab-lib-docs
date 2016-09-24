# Example #2: Accessing all resources in a file #

In this example we show how to scan through all the resources in a resource file, listing some information about each one. The following code fragment assumes we have created a resource file object, _ResFile_, and have loaded a resource file into it (see [example #1](ResFileExample1.md)). We also assume that the form contains a memo control named _Memo1_. Here is the code:

```pascal
var
  ResFile: TPJResourceFile;
  ResEntry: TPJResourceEntry;
  EntryIdx: Integer;
begin
  ...
  // Assume ResFile contains a loaded resource file
  ...
  Memo1.Clear;
  for EntryIdx := 0 to Pred(ResFile.EntryCount) do
  begin
    ResEntry := ResFile.Entries[EntryIdx];
    Memo1.Lines.Add(
      Format(
        'Type: "%s"   Name: "%s"   LanguageID: %0.4X',
        [ResIDToStr(ResEntry.ResType), ResIDToStr(ResEntry.ResName),
        ResEntry.LanguageID]
      )
    );
  end;
  ...
  // Don't forget to free ResFile at some stage.
end;
```

This code uses both _[TPJResourceFile](TPJResourceFile.md)_ and _[TPJResourceEntry](TPJResourceEntry.md)_ objects. The resource file's _[EntryCount](TPJResourceFileEntryCount.md)_ property tells us how many resources there are in the file. Each resource is represented by a _[TPJResourceEntry](TPJResourceEntry.md)_ object obtained from the _[Entries](TPJResourceFileEntries.md)_ array property.

We loop through all the valid indexes into _[Entries](TPJResourceFileEntries.md)_ and store a reference to each resource entry in turn. Having got the resource entry object we now access its _ResType_, _ResName_ and _LanguageID_ properties to get the information we want to display.

The details of each entry are formatted by Delphi's _Format_ function and added to _Memo1_. Note that we use the _[ResIDToStr](ResFileRoutines.md#residtostr)_ helper function to get string representations of the resource type and name. We display the language ID as a four digit hex number since its value is a _Word_.

You may have noticed that we have not freed any of the resource entry objects. This is not necessary since they are all freed automatically when the resource files object is freed.

**Alternative Approach<sup>v1.1</sup>**

A second approach to the problem uses the fact that v1.1 of the resource files unit implements an enumerator for _[TPJResourceFile](TPJResourceFile.md)_. This means that we can use a **for..in** loop to enumerate the resources.

Here's the modified code:

```pascal
var
  ResFile: TPJResourceFile;
  ResEntry: TPJResourceEntry;
begin
  ...
  // Assume ResFile contains a loaded resource file
  ...
  Memo1.Clear;
  for ResEntry in ResFile do
  begin
    Memo1.Lines.Add(
      Format(
        'Type: "%s"   Name: "%s"   LanguageID: %0.4X',
        [ResIDToStr(ResEntry.ResType), ResIDToStr(ResEntry.ResName),
        ResEntry.LanguageID]
      )
    );
  end;
  ...
  // Don't forget to free ResFile at some stage.
end;
```

The code above requires Delphi 2005 or later. Users of earlier Delphis _can_ still use the enumerator if desired, like this:

```pascal
var
  ResFile: TPJResourceFile;
  ResEntry: TPJResourceEntry;
  Enum: TPJResourceFileEnumerator;
begin
  ...
  // Assume ResFile contains a loaded resource file
  ...
  Memo1.Clear;
  Enum := ResFile.GetEnumerator;
  try
    while Enum.MoveNext do
    begin
      ResEntry := Enum.Current;
      Memo1.Lines.Add(
        Format(
          'Type: "%s"   Name: "%s"   LanguageID: %0.4X',
          [ResIDToStr(ResEntry.ResType), ResIDToStr(ResEntry.ResName),
          ResEntry.LanguageID]
        )
      );
   end;
  finally
    Enum.Free;
  end;
  ...
  // Don't forget to free ResFile at some stage.
end;
```

**Links:**

  * [Next Example](ResFileExample3.md)
  * [Previous Example](ResFileExample1.md)
  * Back to [List of Examples](ResFileExamples.md)
