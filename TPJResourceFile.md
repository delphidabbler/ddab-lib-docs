#summary TPJResourceFile class description
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= TPJResourceFile =

*Project:* [ResFileUnit Resource File Unit]

*Unit:* _PJResFile_.

This class is used to encapsulate a 32 bit resource file, to find which resources it contains, to add new resources and to delete existing ones.

Create new, empty instances of _TPJResourceFile_ by calling its parameterless _Create_ constructor.

Resource entries accessed or created via this class are _[TPJResourceEntry TPJResourceEntry]_ objects and have methods and properties that can be used to interrogate and update them. These objects are not created directly but are created by loading a resource file or by calling methods of _TPJResourceFile_.

Freeing a _TPJResourceFile_ instance also frees all the associated _[TPJResourceEntry TPJResourceEntry]_ objects, so do not keep references to these objects after the parent _TPJResourceFile_ object has been freed.

When compiled with Delphi 2005 and later all the resource entries in a _TPJResourceFile_ instance can be enumerated within a *for..in* loop.

*Note:* Although we use the term "resource file" in this documentation, the term also relates to binary resource data stored in a stream.

== Methods ==

|| *Method* || *Description* ||
|| _[TPJResourceFileAddEntry AddEntry]_ || Overloaded methods that add a new, empty, resource to the object. ||
|| _[TPJResourceFileClear Clear]_ || Clears all resource entries from the resource file. ||
|| _[TPJResourceFileDeleteEntry DeleteEntry]_ || Deletes a given resource entry object from the resource file. ||
|| _[TPJResourceFileEntryExists EntryExists]_ || Checks if a resource with a given type, name and language ID exists. ||
|| _[TPJResourceFileFindEntry FindEntry]_ || Finds a resource by type, name and language ID. ||
|| _[TPJResourceFileFindEntryIndex FindEntryIndex]_ || Finds the index of a resource in the _[TPJResourceFileEntries Entries]_ property by type, name and language ID. ||
|| _[TPJResourceFileGetEnumerator GetEnumerator]_*^v1.1^* || Returns an object that can enumerate all the resource entries in a resource file. ||
|| _[TPJResourceFileIndexOfEntry IndexOfEntry]_ || Gets the index of a resource entry in the _[TPJResourceFileEntries Entries]_ property. ||
|| _[TPJResourceFileIsValidResourceStream IsValidResourceStream]_ || Class function that checks if a stream contains a valid 32 bit resource file. ||
|| _[TPJResourceFileLoadFromFile LoadFromFile]_ || Loads data from a resource file. ||
|| _[TPJResourceFileLoadFromStream LoadFromStream]_ || Loads resource data from a stream. ||
|| _[TPJResourceFileSaveToFile SaveToFile]_ || Saves resource data to a file. ||
|| _[TPJResourceFileSaveToStream SaveToStream]_ || Saves resource data to a stream. ||

== Properties ==

|| *Property* || *Description* ||
|| _[TPJResourceFileEntryCount EntryCount]_ || Number of resources (entries) in the resource file. ||
|| _[TPJResourceFileEntries Entries]_ || Indexed access to all resources in the resource file. ||