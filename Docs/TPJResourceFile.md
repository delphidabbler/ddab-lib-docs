# TPJResourceFile #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

This class is used to encapsulate a 32 bit resource file, to find which resources it contains, to add new resources and to delete existing ones.

Create new, empty instances of _TPJResourceFile_ by calling its parameterless _Create_ constructor.

Resource entries accessed or created via this class are _[TPJResourceEntry](TPJResourceEntry.md)_ objects and have methods and properties that can be used to interrogate and update them. These objects are not created directly but are created by loading a resource file or by calling methods of _TPJResourceFile_.

Freeing a _TPJResourceFile_ instance also frees all the associated _[TPJResourceEntry](TPJResourceEntry.md)_ objects, so do not keep references to these objects after the parent _TPJResourceFile_ object has been freed.

When compiled with Delphi 2005 and later all the resource entries in a _TPJResourceFile_ instance can be enumerated within a **for..in** loop.

**Note:** Although we use the term "resource file" in this documentation, the term also relates to binary resource data stored in a stream.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[AddEntry](TPJResourceFileAddEntry.md)_ | Overloaded methods that add a new, empty, resource to the object. |
| _[Clear](TPJResourceFileClear.md)_ | Clears all resource entries from the resource file. |
| _[DeleteEntry](TPJResourceFileDeleteEntry.md)_ | Deletes a given resource entry object from the resource file. |
| _[EntryExists](TPJResourceFileEntryExists.md)_ | Checks if a resource with a given type, name and language ID exists. |
| _[FindEntry](TPJResourceFileFindEntry.md)_ | Finds a resource by type, name and language ID. |
| _[FindEntryIndex](TPJResourceFileFindEntryIndex.md)_ | Finds the index of a resource in the _[Entries](TPJResourceFileEntries.md)_ property by type, name and language ID. |
| _[GetEnumerator](TPJResourceFileGetEnumerator.md)_**<sup>v1.1</sup>** | Returns an object that can enumerate all the resource entries in a resource file. |
| _[IndexOfEntry](TPJResourceFileIndexOfEntry.md)_ | Gets the index of a resource entry in the _[Entries](TPJResourceFileEntries.md)_ property. |
| _[IsValidResourceStream](TPJResourceFileIsValidResourceStream.md)_ | Class function that checks if a stream contains a valid 32 bit resource file. |
| _[LoadFromFile](TPJResourceFileLoadFromFile.md)_ | Loads data from a resource file. |
| _[LoadFromStream](TPJResourceFileLoadFromStream.md)_ | Loads resource data from a stream. |
| _[SaveToFile](TPJResourceFileSaveToFile.md)_ | Saves resource data to a file. |
| _[SaveToStream](TPJResourceFileSaveToStream.md)_ | Saves resource data to a stream. |

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[EntryCount](TPJResourceFileEntryCount.md)_ | Number of resources (entries) in the resource file. |
| _[Entries](TPJResourceFileEntries.md)_ | Indexed access to all resources in the resource file. |