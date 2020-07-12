# BlockSize class method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class function BlockSize: Integer;
```

## Description

Calculates and returns the size, in _characters_, of the environment block in the current process.

The block size is sufficient to store a concatentation of all environment variables where each one is represented in `Name=Value` format, separated by a zero character (i.e. `#0` or `Char(0)`) with the whole block terminated by a pair of zero characters. An example block with three variables is `Foo=Lorem#0Bar=Ipsum#0Raboof=Dolore#0#0`

> **Important**. Because the size of the environment block is returned in _characters_, not bytes, you must multiply the returned value by `SizeOf(Char)` to get the size in bytes.
