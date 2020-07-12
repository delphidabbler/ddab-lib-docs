# TPJFileIStream class

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

## Description

_TPJFileIStream_ provides an _IStream_ interface to a file. It's constructor is like that of _TFileStream_ except that the constructor returns an object of type _TPJFileIStream_ which can be cast to _IStream_.

The [_Stat_](TPJFileIStream-Stat.md) method of _TPJFileIStream_, like that of [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), provides file date / time stamp information. Additionally, the _pwcsName_ element of the _TStatStg_ structure returns the name of the open file rather than a name based on the class name.

### Methods

| Method | Description |
|--------|-------------|
| [_Clone_](TPJIStreamWrapper-Clone.md) | Method of _IStream_. Creates a new _IStream_ object that accesses the same physical stream. ***Not supported in this implementation***. |
| [_Commit_](TPJIStreamWrapper-Commit.md) | Method of _IStream_. Commits pending changes. |
| [_CopyTo_](TPJIStreamWrapper-CopyTo.md) | Method of _IStream_. Copies data from the file stream into another stream. |
| [_Create_](TPJFileIStream-Create.md) | Object constructor. Creates a stream onto a given file that supports the _IStream_ interface. |
| [_LockRegion_](TPJIStreamWrapper-LockRegion.md) | Method of _IStream_. Restricts access to a specified range of bytes in the file stream. ***Not supported in this implementation***. |
| [_Read_](TPJIStreamWrapper-Read.md) | Method of _IStream_. Reads data from the file stream. |
| [_Revert_](TPJIStreamWrapper-Revert.md) | Method of _IStream_. Discards un-committed changes in a transacted stream. |
| [_Seek_](TPJIStreamWrapper-Seek.md) | Method of _IStream_. Changes the seek pointer to a new location. |
| [_SetSize_](TPJIStreamWrapper-SetSize.md) | Method of _IStream_. Changes the size of the file stream. |
| [_Stat_](TPJFileIStream-Stat.md) | Method of _IStream_. Retrieves the _TStatStg_ structure that provides information about the file associated with the stream. |
| [_UnlockRegion_](TPJIStreamWrapper-UnlockRegion.md) | Method of _IStream_. Removes access restrictions from a range of bytes in the stream. ***Not supported in this implementation***. |
| [_Write_](TPJIStreamWrapper-Write.md) | Method of _IStream_. Writes data to the file stream. |

> **Note:**
>
> **[v3.0]** Note that the methods of _IStream_ have protected visibility in _TPJFileIStream_ and cannot be accessed from an object instance referenced by a variable of type _TPJFileIStream_. The methods can only be accessed via the object's _IStream_ interface.
>
> **[≥v3.1]** Methods of _IStream_ have public visibility.

### Properties

_TPJFileIStream_ exposes no properties.

### Events

_TPJFileIStream_ exposes no events.

## See Also

* [Classes List](./Classes.md)
* [Programmers' Guide](../API.md)
