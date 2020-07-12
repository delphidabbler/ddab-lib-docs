# Write method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJStreamWrapper_](./PJStreamWrapper.md)

***Class:*** [_TPJStreamWrapper_](./TPJStreamWrapper.md)

```pascal
function Write(const Buffer; Count: Longint): Longint; override;
```

## Description

This method overrides and implements an abstract method of _TStream_.

_Write_ attempts to write a specified number of bytes of data from a buffer into the wrapped stream.

***Parameters:***

* _Buffer_ -- Untyped variable containing the data to be written to the stream. The data passed to this parameter must have size of a least _Count_ bytes.
* _Count_ -- Number of bytes to be written from _Buffer_ into the wrapped stream.

***Returns:***

* Number of bytes actually written.

## Remarks

If the method's return value is less than _Count_ then not all the data could be written to the wrapped stream.

Data is written to the wrapped stream from its current position. The stream's position is incremented by the number of bytes written.

An exception may be raised if the wrapped stream does not support write access.
