# CreateBlock class method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class function CreateBlock(const NewEnv: TStrings;
  const IncludeCurrent: Boolean; const Buffer: Pointer;
  const BufSize: Integer): Integer;
```

## Description

Creates a new custom environment block in a form suitable for passing to another process.

***Parameters:***

* _NewEnv_ -- List of environment variables in `Name=Value` format to be included in the new environment block. If `nil` then no new environment variables are included.
* _IncludeCurrent_ -- Indicates whether the environment variables of the current process are to be included in the new environment block.
* _Buffer_ -- Pointer to a memory block that will receive the new environment block, or `nil`. When provided _Buffer_ must be large enough to accomodate the environment block. If `nil` to environment block will be created.
* _BufSize_ -- The number of _characters_ that can be stored in the memory pointed to by _Buffer_. If _Buffer_ is `nil` then set _BufSize_ to `0`.

***Returns:***

* The size of the environment block in _characters_. If _Buffer_ is `nil` this value is the required buffer size.

The format of the environment block created with this method is a concatentation of the environment variables where each one is represented in `Name=Value` format, separated by a zero character (i.e. `#0` or `Char(0)`) with the whole block terminated by a pair of zero characters. An example block with three variables is `Foo=Lorem#0Bar=Ipsum#0Raboof=Dolore#0#0`

> **Important**. Because _CreateBlock_ deals with buffer sizes in _characters_, not bytes, you must multiply the returned value by `SizeOf(Char)` when allocating suitable buffers with _GetMem_. Alternatively, use a routine such as _StrAlloc_ that automatically takes account of the character size.

The usual way to use _CreateBlock_ is to call it once with a `nil` buffer to get the required buffer size in characters, allocate the buffer and then call _CreateBlock_ again, this time passing the actual buffer and its size, for example:

```pascal
var
  EnvBlock: Pointer;
  BlockSize: Integer;
  NewEnv: TStringList;
begin
  // Create and populate NewEnv
  // ...
  // Create the environment block: include NewEnv and process' own block
  BlockSize := TPJEnvironmentVars.CreateBlock(NewEnv, True, nil, 0);
  // BlockSize is in Characters, not bytes: so needs converting to bytes
  GetMem(EnvBlock, BlockSize * SizeOf(Char));
  try
    CreateEnvBlock(NewEnv, True, EnvBlock, BlockSize);
    // Execute a program with environment block
    // ...
  finally
    FreeMem(EnvBlock);
  end;
end;
```
