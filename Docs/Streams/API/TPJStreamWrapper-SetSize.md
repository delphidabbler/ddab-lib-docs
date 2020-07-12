# SetSize method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJStreamWrapper_](./PJStreamWrapper.md)

***Class:*** [_TPJStreamWrapper_](./TPJStreamWrapper.md)

```pascal
procedure SetSize(NewSize: Longint); override;
```

_Introduced: v3.1:_ [[1]](#footnote-1)

```pascal
procedure SetSize(const NewSize: Int64); override;
```

## Description

This protected method overrides the do-nothing method of _TStream_ and attempts to set the size of the wrapped stream.

**[≥v3.1]** There are two overloaded versions of the method: one that takes a 32 bit size and one that takes a 64 bit size [[1]](#footnote-1).

If the size of the wrapped stream cannot be changed then _SetSize_ has no effect.

***Parameters:***

* _NewSize_ -- Request new size of the wrapped stream.

## Footnotes

### Footnote 1

The version of _SetSize_ with the 64 bit integer parameter is included in [_TPJStreamWrapper_](./TPJStreamWrapper.md) only if the library is compiled with Delphi 6 or later. This is because the version of _TStream_ shipped with Delphi 5 and earlier did not include this method.
