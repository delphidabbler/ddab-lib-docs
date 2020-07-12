# TPJHandleIStreamWrapper class

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

## Description

This class wraps a stream of type _THandleStream_ or its sub-classes (such as _TFileStream_) and provides an _IStream_ interface to the stream.

_TPJHandleIStreamWrapper_ descends from, and acts the same as, [_TPJIStreamWrapper_](./TPJIStreamWrapper.md) with the exception that the _TStatStg_ structure returned by the [_Stat_](./TPJHandleIStreamWrapper-Stat.md) method also returns information about file creation, modification and access dates where available.

### Methods

| Method | Description |
|--------|-------------|
| [_Clone_](TPJIStreamWrapper-Clone.md) | Method of _IStream_. Creates a new _IStream_ object that accesses the same physical stream. ***Not supported in this implementation***. |
| [_Commit_](TPJIStreamWrapper-Commit.md) | Method of _IStream_. Commits pending changes. |
| [_CopyTo_](TPJIStreamWrapper-CopyTo.md) | Method of _IStream_. Copies data from the wrapped stream into another stream. |
| [_Create_](TPJHandleIStreamWrapper-Create.md) | Object constructor. Creates a new wrapper object for a given _THandleStream_ instance. |
| [_LockRegion_](TPJIStreamWrapper-LockRegion.md) | Method of _IStream_. Restricts access to a specified range of bytes in the stream. ***Not supported in this implementation***. |
| [_Read_](TPJIStreamWrapper-Read.md) | Method of _IStream_. Reads data from the wrapped stream. |
| [_Revert_](TPJIStreamWrapper-Revert.md) | Method of _IStream_. Discards un-committed changes in a transacted stream. |
| [_Seek_](TPJIStreamWrapper-Seek.md) | Method of _IStream_. Changes the seek pointer to a new location. |
| [_SetSize_](TPJIStreamWrapper-SetSize.md) | Method of _IStream_. Changes the size of the stream. |
| [_Stat_](TPJHandleIStreamWrapper-Stat.md) | Method of _IStream_. Retrieves the _TStatStg_ structure that provides information about the wrapped stream. |
| [_UnlockRegion_](TPJIStreamWrapper-UnlockRegion.md) | Method of _IStream_. Removes access restrictions from a range of bytes in the stream. ***Not supported in this implementation***. |
| [_Write_](TPJIStreamWrapper-Write.md) | Method of _IStream_. Writes data to the wrapped stream. |

> **Note:**
>
>**[v3.0]** Methods of _IStream_ have protected visibility in _TPJHandleIStreamWrapper_ and cannot be accessed from an object instance referenced by a variable of type _TPJHandleIStreamWrapper_. The methods can only be accessed via the object's _IStream_ interface.
>
> **[≥v3.1]** Methods of _IStream_ have public visibility.

### Properties

_TPJHandleIStreamWrapper_ exposes no properties.

### Events

_TPJHandleIStreamWrapper_ exposes no events.

## See Also

* [Classes List](./Classes.md)
* [Programmers' Guide](../API.md)
