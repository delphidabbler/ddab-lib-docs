#summary Resource File Unit documentation.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Resource File Unit =

This unit contains classes that encapsulate Windows 32 bit binary resource files and the resources contained in them. The main functionality is provided by two classes. In addition some helper functions, an exception class and some constants are also provided.

The classes encapsulate the low-level structure of a resource file and its resources. It deals only with raw resource data. The actual format of the raw data depends on the resource type. *This unit does not provide any support for specific resource types or their data formats.*

This wiki is divided into several sections as noted in the following table.

|| _[TPJResourceFile]_ || Class that encapsulates the contents of a whole resource file and provides methods and properties to search, enumerate and manipulate it. ||
|| _[TPJResourceEntry]_ || Class that encapsulates a single resource within a resource file and provides properties and methods to access its header record and its raw data and to compare it to other resources. ||
|| _[TPJResourceFileEnumerator]_*^v1.1^* || Class that implements an enumerator for _[TPJResourceFile]_ that enumerates all its resource entries. ||
|| _[EPJResourceFile]_ || Class of exception raised by _[TPJResourceFile]_ and _[TPJResourceEntry]_. ||
|| [ResFileRoutines Helper Routines] || Routines to assist in working with resource identifiers. ||
|| [ResFileConsts Constants] || Various useful constants. ||
|| [ResFileExamples Examples] || Several examples of how to use the code of the Resource File Unit. ||

*NOTE:* This documentation relates to *v1.0* and later of the Resource File Unit. Any items in this documentation introduced after the release of v1.0 are marked with the version number at which they were first made available, for example: *^v1.1^*

*Links:*

  * Back to [Welcome Wiki Home Page]
  * [http://www.delphidabbler.com/software/resfile Resource File Unit Web Page].