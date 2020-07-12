# Seek method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJStreamWrapper_](./PJStreamWrapper.md)

***Class:*** [_TPJStreamWrapper_](./TPJStreamWrapper.md)

```pascal
function Seek(Offset: Longint; Origin: Word): Longint; override;
```

_Introduced: v3.1_ [[1]](#footnote-1)

```pascal
function Seek(const Offset: Int64; Origin: TSeekOrigin): Int64; override;
```

## Description

_Seek_ moves the wrapped stream's position a specified number of bytes relative to a given origin.

**[≥v3.1]** There are two overloaded versions of the method: one that takes a 32 bit offset and one that takes a 64 bit offset [[1]](#footnote-1).

***Parameters:***

* _Offset_ -- The number of bytes to move the wrapped stream's position from the origin specified by the _Origin_ parameter.
* _Origin_ -- The origin from which to offset the stream's position. Possible values are:
  * Where _Origin_ has type _Word_:
    * _soFromBeginning_ (=`0`): seek from the start of the stream (_Offset_ should be positive).
    * _soFromCurrent_ (=`1`): seek from the current stream position (use a positive value of _Offset_ to seek forwards and a negative value to seek backwards).
    * _soFromEnd_ (=`2`): seek from the end of the stream (_Offset_ should be negative) [[2]](#footnote-2)
  * Where _Origin_ has type _TSeekOrigin_:
    * _soBeginning_: seek from the start of the stream (_Offset_ should be positive).
    * _soCurrent_: seek from the current stream position (use a positive value of _Offset_ to seek forwards and a negative value to seek backwards).
    * _soEnd_: seek from the end of the stream (_Offset_ should be negative) [[2]](#footnote-2).

***Returns:***

* New position of the wrapped stream.
* **[≥v3.1]** The type of the return value can be either a 32 bit or a 64 bit integer, depending on which of the overloaded versions of the method was called.

## Remarks

This operation may cause an exception if the underlying stream does not support seeking.

The affect of attempting to seek beyond the end of the stream is dependent on the type of the wrapped stream. Attempts to seek before the beginning of the stream result in the stream position being set to the start of the wrapped stream.

**[≥v3.1]** Some wrapped streams may not support 64 bit seek offsets and give unexpected results.

## Footnotes

### Footnote 1

The version of _Seek_ with the 64 bit integer _Offset_ parameter is included in [_TPJStreamWrapper_](./TPJStreamWrapper.md) only if the library is compiled with Delphi 6 or later. This is because the version of _TStream_ shipped with Delphi 5 and earlier did not include this method.

### Footnote 2

Versions of _TStringStream_ compiled from non-Unicode versions of the _Classes_ unit do not handle the _soFromEnd_ / _soEnd_ origin variation of the _Seek_ method correctly - offsets are negated and work in the opposite way expected.

**[v3.0]** [_TPJStreamWrapper_](./TPJStreamWrapper.md) simply passes the seek request through unchanged to the wrapped class. This means that such errors will be replicated in wrapped classes.

**[≥v3.1]** By default [_TPJStreamWrapper_](./TPJStreamWrapper.md) traps requests for seeks with _soFromEnd_ / _soEnd_ origins and processes them so that any errors in handling them in wrapped streams are fixed. This behaviour can be reverted to that in earlier versions by un-defining the _FIX_TSTRINGSTREAM_SEEK_ERROR_ symbol in the [_PJStreamWrapper_](./PJStreamWrapper.md) unit.
