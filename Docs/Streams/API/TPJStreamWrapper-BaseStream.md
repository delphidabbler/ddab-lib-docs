# BaseStream property

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJStreamWrapper_](./PJStreamWrapper.md)

***Class:*** [_TPJStreamWrapper_](./TPJStreamWrapper.md)

```pascal
property BaseStream: TStream read fBaseStream;
```

## Description

This protected property references the wrapped stream. It is provided for use by sub-classes that need to call methods on the wrapped stream.
