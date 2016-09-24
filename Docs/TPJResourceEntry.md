# TPJResourceEntry #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

This class encapsulates a resource within a resource file.

_TPJResourceEntry_ objects are used to manipulate and interrogate resource entries. Properties are exposed that give access to the resource header information, some of which can be modified by writing to properties. The resource's raw data can be read and manipulated either through the _Data_ property, which provides a _TStream_ interface to the data or via the _DataBytes_**<sup>v1.1</sup>** property that enables the raw data to be read and written to and from a byte array.

This is done mainly via properties which give access to resource header information, allow some header information to be set, and give read/write access to the raw resource data via a _TStream_ or as a an array of bytes**<sup>v1.1</sup>**.

Objects of this class must not be directly instantiated. _[TPJResourceFile](TPJResourceFile.md)_ automatically creates the required objects when loading a resource file. New, empty resource entry instances can be created by using one the overloaded _[AddEntry](TPJResourceFileAddEntry.md)_ methods provided by _[TPJResourceFile](TPJResourceFile.md)_. _TPJResourceEntry_ is actually an abstract class that provides an  interface for manipulating resource entries. The concrete class that implements the resource entry is private. This enforces the rule that all valid resource objects are created and accessed via _[TPJResourceFile](TPJResourceFile.md)_.

Care should be taken not to use a resource entry after the related resource file object has been cleared or destroyed, or a new resource file has been loaded, since all these actions free previous resource entries. It is safe to free a _TPJResourceEntry_ object directly by calling its _Free_ method. Doing so automatically removes the object from the resource file object it belongs to.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[ClearData](TPJResourceEntryClearData.md)_**<sup>v1.1</sup>** | Clears (deletes) the resource entry's raw data. |
| _[IsMatching](TPJResourceEntryIsMatching.md)_ | Overloaded methods to check if the resource entry matches the type, name and language ID of another entry. |
| _[LoadDataFromFile](TPJResourceEntryLoadDataFromFile.md)_**<sup>v1.1</sup>** | Loads the content of a file into the resource entry's raw data. |

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _Characteristics_ | Gets or sets the user specified characteristics of the resource as a _DWORD_. |
| _Data_ | Provides a reference to the _TStream_ object that contains the resource's raw data. The stream can be used to read or write the data. Any padding bytes that follow the resource's data are not included in the stream. The object reference is read only but the stream's contents can be modified. |
| _DataBytes_**<sup>v1.1</sup>** | Provides read-write access to the resource's raw entry as a _TBytes_<sup>†</sup> byte array. Reading the property returns a copy the the resource data. Assigning to the property replaces any existing resource data with a copy of the byte array being assigned and set the !Data stream's position to the start of the stream. |
| _DataSize_ | The size of the resource data in bytes as a _DWORD_ value. This is the same as calling same as calling _Data.Size_. Read only. |
| _DataVersion_ | Gets or sets the predefined data resource version information as a _DWORD_. |
| _HeaderSize_ | The size of the resource header as a _DWORD_. Read only. Note that the header size varies depending on the type and size of the resource type and name. |
| _LanguageID_ | The language used by the resource as a _Word_. A value of 0 is language-neutral. Read only. |
| _MemoryFlags_ | Gets or sets the attribute bitmask that specifies the state of resource as a _Word_. |
| _ResName_ | The name of the resource as a _PChar_. This value is either a pointer to a zero-terminated string or an ordinal value of the type returned from _MakeIntResource_. Read only. |
| _ResType_ | The type of the resource as a _PChar_. This value is either a pointer to a zero-terminated string or an ordinal value of the type returned from _MakeIntResource_. Read only. |
| _Version_ | Gets or sets the user specified version number of the resource data as a _DWORD_. |

**Footnote**

† _TBytes_ is defined in _SysUtils_ on Delphi 2007 and later. For earlier compilers _TBytes_ is defined in the _[PJResFile](ResFileUnit.md)_ unit as `array of byte`.
