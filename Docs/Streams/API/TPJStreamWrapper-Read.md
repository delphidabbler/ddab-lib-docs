# Read method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJStreamWrapper_](./PJStreamWrapper.md)

***Class:*** [_TPJStreamWrapper_](./TPJStreamWrapper.md)

```pascal
function Read(var Buffer; Count: Longint): Longint; override;
```

## Description

This method overrides and implements an abstract method of _TStream_.

_Read_ attempts to read a specified number of bytes from the stream into a buffer.

***Parameters:***

* _Buffer_ -- Untyped buffer that receives the data read from the wrapped stream. This variable passed to this parameter must have a size of at least _Count_ bytes.
* _Count_ -- The number of bytes to be read from the stream. If the stream does not contain sufficient data to fulfil the request just the available number of bytes are read.

***Returns:***

* Number of bytes actually read.

## Remarks

If the requested number of bytes are available in the wrapped stream then _Buffer_ receives _Count_ bytes and the method's return value is equal to _Count_. If there is insufficient data remaining in the wrapped stream to fulfil the request then any remaining bytes are read from the stream into _Buffer_ and the return value will be less than _Count_. If the stream is at the end when the request is made then no data is copied into _Buffer_ and zero is returned.

Note that the wrapped stream is read from the current position and the position is incremented by the number of bytes read.

An exception may be raised if the wrapped stream does not support read access.
