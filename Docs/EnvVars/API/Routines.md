# Helper Routines

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

> ***Warning:*** All the routines described here are ***deprecated***. Each routine has analogue in the [_TPJEnvironmentVars_](./TPJEnvironmentVars.md) static class that should be used in preference.

_PJEnvVars_ contains several functions and procedures to assist in interogating and manipulating environment variables. They are:

* [_CreateEnvBlock_](#createenvblock)
* [_DeleteEnvVar_](#deleteenvvar)
* [_EnvBlockSize_](#envblocksize)
* [_ExpandEnvVars_](#expandenvvars)
* [_GetAllEnvVarNames_](#getallenvvarnames)
* [_GetAllEnvVars_](#getallenvvars)
* [_GetEnvVarValue_](#getenvvarvalue)
* [_SetEnvVarValue_](#setenvvarvalue)

## CreateEnvBlock

> ***Deprecated*** -- use [_TPJEnvironmentVars.CreateBlock_](./TPJEnvironmentVars-CreateBlock.md) instead.

```pascal
function CreateEnvBlock(const NewEnv: TStrings;
  const IncludeCurrent: Boolean; const Buffer: Pointer;
  const BufSize: Integer): Integer;
```

Creates a new environment block that can be used to pass to another process.

Pass a string list in _NewEnv_ containing any environment variables that are to be included in the new block. Set _IncludeCurrent_ to `True` to include the current environment in the new block. _Buffer_ should point to a block of memory of sufficient size to contain the new block and _BufSize_ should be the size of this buffer.

The routine returns the buffer size in _characters_. If the supplied buffer is too small or is `nil` then no data is created and the return value is the required buffer size.

Normal usage is to call _CreateEnvBlock_ with _Buffer_ set to `nil` to get the required buffer size, then to create the memory block of that size and finally to call _CreateEnvBlock_ again with _Buffer_ pointing to the newly created memory block and _BufSize_ set to the size returned from the previous call to _CreateEnvBlock_.

## DeleteEnvVar

> ***Deprecated*** -- use [_TPJEnvironmentVars.Delete_](./TPJEnvironmentVars-Delete.md) instead.

```pascal
function DeleteEnvVar(const VarName: string): Integer;
```

Deletes the environment variable with the given name.

Returns a Windows error code on failure or `0` on success.

## EnvBlockSize

> ***Deprecated*** -- use [_TPJEnvironmentVars.BlockSize_](./TPJEnvironmentVars-BlockSize.md) instead.

```pascal
function EnvBlockSize: Integer;
```

This function returns the size of the current environment block in _characters_.

> **Important**. Because the size of the environment block is returned in _characters_, not bytes, you must multiply the returned value by `SizeOf(Char)` to get the size in bytes.

## ExpandEnvVars

> ***Deprecated*** -- use [_TPJEnvironmentVars.Expand_](./TPJEnvironmentVars-Expand.md) instead.

```pascal
function ExpandEnvVars(const Str: string): string;
```

Replaces any environment variables embedded in the given string with their values and returns the modified string.

## GetAllEnvVarNames

> ***Deprecated*** -- use [_TPJEnvironmentVars.GetAllNames_](./TPJEnvironmentVars-GetAllNames.md) instead.

```pascal
procedure GetAllEnvVarNames(const Names: TStrings); overload;
function GetAllEnvVarNames: TStringDynArray; overload;
```

Both overloaded versions of this routine fetch a list of the current environment variable names. Any blank names are excluded from the list.

The first version of the routine stores the environment variable names in the given string list. Any existing contents of the string list are discarded.

The second version creates and returns a dynamic string array containing the environment variable names.

## GetAllEnvVars

> ***Deprecated*** -- use [_TPJEnvironmentVars.GetAll_](./TPJEnvironmentVars-GetAll.md) instead.

```pascal
function GetAllEnvVars(const Vars: TStrings): Integer;
```

Copies all the environment variables available to the current process in to the given string list. Each item placed in the string list represents one environment variable in the form `NAME=VALUE`. Any previous contents of the string list are lost.

The size of the environment block, in characters, is returned.

## GetEnvVarValue

> ***Deprecated*** -- use [_TPJEnvironmentVars.GetValue_](./TPJEnvironmentVars-GetValue.md) instead.

```pascal
function GetEnvVarValue(const VarName: string): string;
```

Returns the value of environment variable with the given name.

## SetEnvVarValue

> ***Deprecated*** -- use [_TPJEnvironmentVars.SetValue_](./TPJEnvironmentVars-SetValue.md) instead.

```pascal
function SetEnvVarValue(const VarName, VarValue: string): Integer;
```

Sets the value of a given environment variable.

Returns a Windows error code on failure or `0` on success.
