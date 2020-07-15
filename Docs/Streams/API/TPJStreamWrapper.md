# TPJStreamWrapper class

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJStreamWrapper_](./PJStreamWrapper.md)

## Description

This class is not normally used on its own. It is designed as a parent for classes that "wrap" a stream.

_TPJStreamWrapper_ simply replicates the facilities in the wrapped stream. Each method simply calls the equivalent method of the wrapped stream.

Sub-classes will add methods to the base class and/or override the base class's handling of the _Read_, _Write_ and _Seek_ methods inherited from _TStream_.

Wrapping a _TStream_ descendant object rather than adding functionality by extending the class means that the functionality provided by the wrapper class can be applied to any _TStream_ descendant.

> Study the _StreamWrapDemo_ demo source code details of how this can be achieved.

### Methods

_TPJStreamWrapper_ inherits all the methods of _TStream_. Only new methods and those of _TStream_ that are overridden are described here.

#### Public

| Method | Description |
|--------|-------------|
| [_Create_](TPJStreamWrapper-Create.md) | Object constructor. Creates a new wrapper object for a given stream. |
| [_Read_](TPJStreamWrapper-Read.md) | _Override_. Reads data from the wrapped stream into a buffer. |
| [_Seek_](TPJStreamWrapper-Seek.md) | _Override_. Updates the current position in the underlying stream. |
| [_Write_](TPJStreamWrapper-Write.md) | _Override_. Writes data from a buffer to the wrapped stream. |

#### Protected

| Method | Description |
|--------|-------------|
| [_SetSize_](TPJStreamWrapper-SetSize.md) | _Override_. Sets the size of the wrapped stream. |

### Properties

The sole property is protected.

| Property | Description |
|----------|-------------|
| [_BaseStream_](TPJStreamWrapper-BaseStream.md) | References the wrapped stream. |

### Events

The class defines no events.

## See Also

* [Classes List](./Classes.md)
* [Programmers' Guide](../API.md)
