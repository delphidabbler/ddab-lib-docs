# PJPipeFilters unit

***Project:*** [I/O Utility Classes](../API.md)

## Description

This unit contains classes that filter or format output from pipes.

## Declarations

* [_TPJPipeFilter_](./TPJPipeFilter.md) abstract class
* [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md) class
* [_TPJUnicodeTextReadEvent_](./TPJUnicodeTextReadEvent.md) method type
* [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md) class
* [_TPJAnsiTextReadEvent_](./TPJAnsiTextReadEvent.md) method type
* _TBytes_ dynamic array type [[1]](#footnote-1)
* _UnicodeString_ type [[2]](#footnote-2)

## Footnotes

### Footnote 1

_TBytes_ is declared as `array of Byte` only if it is not already declared in any used unit.

### Footnote 2

_UnicodeString_ is declared as `WideString` only if it is not already declared. (It is a native type on Delphi 2009 and later).

## Links

* [_Units List_](./Units.md)
