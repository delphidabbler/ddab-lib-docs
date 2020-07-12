# Create constructor

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Class:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md)

```pascal
constructor Create(const Stream: TStream; const CloseStream: Boolean = False);
```

## Description

Object constructor. Creates a new wrapper (or adapter) object for a given _TStream_ that supports the _IStream_ interface. Calls to methods of _IStream_ are mapped onto calls on the wrapped stream.

***Parameters:***

* _Stream_ -- Stream that is "wrapped" by this object.
* _CloseStream_ -- Determines whether the wrapped stream object is freed when this wrapper object is destroyed. Pass `True` to this parameter to free the wrapped stream on destruction or `False` to leave it unchanged.

## Remarks

Setting the _CloseStream_ parameter to `True`, hence causing the wrapper object to free the wrapped stream on destruction, saves the user from having to remember to free the wrapped stream. It also allows for wrapped streams to be created "on the fly" in the constructor call to be freed without keeping a reference to them.
