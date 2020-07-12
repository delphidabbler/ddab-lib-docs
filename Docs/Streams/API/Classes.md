# Classes

***Project:*** [Stream Extension Classes](../API.md)

The following classes are provided by the library:

| Class | Unit | Description |
|-------|------|-------------|
| [_TPJStreamWrapper_](./TPJStreamWrapper.md) | [_PJStreamWrapper_](./PJStreamWrapper.md)| This is a base class for descendant classes that "wrap" a _TStream_ class to filter the data or add functionality. The wrapped _TStream_ is used to perform the required reads, writes and seeks. _TStreamWrapper_ simply replicates the facilities in the wrapped stream - it is for descendant classes to add functionality. |
| [_TPJIStreamWrapper_](./TPJIStreamWrapper.md) | [_PJIStreams_](./PJIStreams.md) | Implements the _IStream_ interface for a wrapped _TStream_ object. |
| [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md) | [_PJIStreams_](./PJIStreams.md) | Implements an _IStream_ interface for a wrapped _THandleStream_ object. Acts in a similar way to [_TPJIStreamWrapper_](./TPJIStreamWrapper.md) except that file date stamps can be access. |
| [_TPJFileIStream_](./TPJFileIStream.md) | [_PJIStreams_](./PJIStreams.md) | Implements an _IStream_ interface on a file stream. |
