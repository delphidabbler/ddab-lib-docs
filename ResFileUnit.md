<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# Resource File Unit #

This unit contains classes that encapsulate Windows 32 bit binary resource files and the resources contained in them. The main functionality is provided by two classes. In addition some helper functions, an exception class and some constants are also provided.

The classes encapsulate the low-level structure of a resource file and its resources. It deals only with raw resource data. The actual format of the raw data depends on the resource type. **This unit does not provide any support for specific resource types or their data formats.**

This wiki is divided into several sections as noted in the following table.

| _[TPJResourceFile](TPJResourceFile.md)_ | Class that encapsulates the contents of a whole resource file and provides methods and properties to search, enumerate and manipulate it. |
|:----------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------|
| _[TPJResourceEntry](TPJResourceEntry.md)_ | Class that encapsulates a single resource within a resource file and provides properties and methods to access its header record and its raw data and to compare it to other resources. |
| _[TPJResourceFileEnumerator](TPJResourceFileEnumerator.md)_**<sup>v1.1</sup>** | Class that implements an enumerator for _[TPJResourceFile](TPJResourceFile.md)_ that enumerates all its resource entries. |
| _[EPJResourceFile](EPJResourceFile.md)_ | Class of exception raised by _[TPJResourceFile](TPJResourceFile.md)_ and _[TPJResourceEntry](TPJResourceEntry.md)_. |
| [Helper Routines](ResFileRoutines.md) | Routines to assist in working with resource identifiers. |
| [Constants](ResFileConsts.md) | Various useful constants. |
| [Examples](ResFileExamples.md) | Several examples of how to use the code of the Resource File Unit. |

**NOTE:** This documentation relates to **v1.0** and later of the Resource File Unit. Any items in this documentation introduced after the release of v1.0 are marked with the version number at which they were first made available, for example: **<sup>v1.1</sup>**

**Links:**

  * Back to [Wiki Home Page](Welcome.md)
  * [Resource File Unit Web Page](http://www.delphidabbler.com/software/resfile).