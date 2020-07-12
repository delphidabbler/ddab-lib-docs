# PJStreamWrapper Unit

***Project:*** [Stream Extension Classes](../API.md)

## Description

This unit defines [_TPJStreamWrapper_](./TPJStreamWrapper.md) which is a base class for descendants that "wrap" _TStream_ instances to provide a filter or to add functionality.

The wrapped _TStream_ instance is used to do physical i/o. [_TPJStreamWrapper_](./TPJStreamWrapper.md) simply replicates the facilities in the wrapped stream. It is for descendant classes to add functionality.

## Declarations

* [_TPJStreamWrapper_](./TPJStreamWrapper.md) class

## [v3.1] Optional Conditionally Defined Symbol

There is an error in _TStringStream_'s _Seek_ implementation that occurs only in non-Unicode versions of the _Classes_ unit. Calls to _Seek_ using the _soFromEnd_ origin incorrectly handle offsets: positive offsets move back from the end of the stream. This behaviour is the opposite of all other stream classes which require a negative offset to move back from the end of the stream. Note that Unicode implementations of _TStringStream_ do not have this error.

By default [_TPJStreamWrapper_](./TPJStreamWrapper.md) fixes this problem and all wrapped streams behave correctly and in the same way.

If you prefer this bug to be replicated in wrapped _TStringStream_ classes, or if this change in behaviour from earlier versions of [_TPJStreamWrapper_](./TPJStreamWrapper.md) may break existing code, you can revert to the earlier behaviour by commenting out the _FIX_TSTRINGSTREAM_SEEK_ERROR_ defined symbol in the unit source code.

## Links

* [Units List](./Units.md)
