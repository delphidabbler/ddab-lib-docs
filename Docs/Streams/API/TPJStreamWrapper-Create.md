# Create constructor

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJStreamWrapper_](./PJStreamWrapper.md)

***Class:*** [_TPJStreamWrapper_](./TPJStreamWrapper.md)

```pascal
constructor Create(const Stream: TStream; const CloseStream: Boolean = False); virtual;
```

## Description

This object constructor creates a new stream wrapper object that wraps a given stream.

***Parameters:***

* _Stream_ -- Stream that is "wrapped" by this object.
* _CloseStream_ -- Determines whether the wrapped stream object is freed when this wrapper object is destroyed. Pass `True` to this parameter to free the wrapped stream on destruction or `False` to leave it unchanged.

## Remarks

Setting the _CloseStream_ parameter to `True`, hence causing the wrapper object to free the wrapped stream on destruction, saves the user from having to remember to free the wrapped stream. It also allows for wrapped streams that are created "on the fly" in this constructor call to be freed without keeping a reference to them.

The wrapped stream can be accessed from descendant classes via the [_BaseStream_](TPJStreamWrapper-BaseStream.md) property.
