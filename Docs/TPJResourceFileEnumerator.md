# TPJResourceFileEnumerator #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Introduced:** v1.1

This class implements an enumerator for _[TPJResourceFile](TPJResourceFile.md)_ objects. It enumerates all the resources entries of the associated _[TPJResourceFile](TPJResourceFile.md)_ instance.

The main purpose of this class is to be used in conjunction with _[TPJResourceFile](TPJResourceFile.md)_'s _[GetEnumerator](TPJResourceFileGetEnumerator.md)_**<sup>v1.1</sup>** method to enable _[TPJResourceFile](TPJResourceFile.md)_ instances to be enumerated in a **for..in** statement. In this case the class is instantiated and used behind the scenes by the compiler.

Therefore in compilers that support the **for..in** statement (i.e. Delphi 2005 and later) there is rarely a need to use this class directly.

Users of earlier compilers can use the class directly from code. If this is done then the class must be instantiated via a call to _[TPJResourceFile](TPJResourceFile.md).[GetEnumerator](TPJResourceFileGetEnumerator.md)_**<sup>v1.1</sup>** - the constructor must not be called directly. See the _[TPJResourceFile](TPJResourceFile.md).[GetEnumerator](TPJResourceFileGetEnumerator.md)_**<sup>v1.1</sup>** documentation for an example of how to use _TPJResourceFileEnumerator_.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _Create_ | Constructor. This method should not be called directly. It is called internally by _[TPJResourceFile](TPJResourceFile.md).[GetEnumerator](TPJResourceFileGetEnumerator.md)_**<sup>1.1</sup>** to create a new enumerator instance. |
| _MoveNext_ | Moves the enumerator to the next item if one exists. Returns True if such an item exists or False if the enumeration has ended. In a new enumeration _MoveNext_ must be called to move to the first item. |
| _GetCurrent_ | Returns the current item in the enumeration. It is an error to call this method before _MoveNext_ has been called or if _MoveNext_ returns False. |

## Property ##

| **Property** | **Description** |
|:-------------|:----------------|
| _Current_ | Read only. Returns the current item in the enumeration. It is an error to read this property before _MoveNext_ has been called or if _MoveNext_ returns False. |