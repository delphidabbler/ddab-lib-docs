<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# Environment Variables Routines #

| This is the documentation for the **v2.0** release of the unit. If you are using a **version 3** release please [see here](http://wiki.delphidabbler.com/index.php/Docs/PJEnvVarsRoutines). |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

**Project:** [Environment Variables Unit](EnvironmentVariablesUnit.md).

**Unit:** _PJEnvVars_.

The following public routines are defined in _PJEnvVars_:

  * [GetEnvVarValue](#GetEnvVarValue.md)
  * [SetEnvVarValue](#SetEnvVarValue.md)
  * [DeleteEnvVar](#DeleteEnvVar.md)
  * [GetAllEnvVars](#GetAllEnvVars.md)
  * [ExpandEnvVars](#ExpandEnvVars.md)
  * [CreateEnvBlock](#CreateEnvBlock.md)
  * [GetAllEnvVarNames](#GetAllEnvVarNames.md)
  * [EnvBlockSize](#EnvBlockSize.md)

## GetEnvVarValue ##

```
function GetEnvVarValue(const VarName: string): string;
```

Returns the value of the environment variable named by _VarName_. The empty string is returned if the named variable does not exist.

## SetEnvVarValue ##

```
function SetEnvVarValue(const VarName, VarValue: string): Integer;
```

Sets the environment variable named by _VarName_ to _VarValue_. If there is no usch environment variable it is created. If _VarValue_ is the empty string then the environment variable is deleted.

Returns 0 on success or a Windows error code on error. The most likely cause of error is that the environment block is full and there is no room for the new value or to create a new variable. A description of any error can be found by passing the error code to _SysUtils.SysErrorMessage_.

**NOTE:** This routine does not update the system's environment variables, only the copy of the environment maintained by this program.

## DeleteEnvVar ##

```
function DeleteEnvVar(const VarName: string): Integer;
```

Deletes the environment variable specified by _VarName_. If the variable does not exist _DeleteEnvVar_ does nothing.

If _DeleteEnvVar_ completes successfuly then 0 is returned. If an error occurs then a non-zero Windows error code is returned. A description of any error can be found by passing the error code to _SysUtils.SysErrorMessage_.

**NOTE:** This routine has no effect on the system's environment variables, only the copy of the environment maintained by this program.

## GetAllEnvVars ##

```
function GetAllEnvVars(const Vars: TStrings): Integer;
```

Copies all the environment variables available to the current process in to the given string list. Each item placed in the string list represents one environment variable in the form `NAME=VALUE`. Any previous contents of the string list are lost.

The size of the environment block in _characters_ is returned.

It is permitted to pass nil as the parameter to _GetAllEnvVars_. If this is done then details of the environment variables are not provided, but the size of the environment block is returned. Therefore this function can also be used to determine the size of the environment block.

**WARNING:** The size of the environment block is returned in characters, not bytes. Therefore, you should multiply the required buffer size by SizeOf(Char) to determine the number of bytes required.

## ExpandEnvVars ##

```
function ExpandEnvVars(const Str: string): string;
```

_ExpandEnvVars_ replaces any environment variables embedded in string _Str_ with their values and returns the modified string.

Environment variables should be delimited by `%` characters thus: `%ENVVAR%`. If any environment variables are not recognised their names are left unmodified. The case of the environment variable name is not significant: i.e. `%ENVVAR%` is the same as `%envvar%`.

## CreateEnvBlock ##

```
function CreateEnvBlock(const NewEnv: TStrings;
  const IncludeCurrent: Boolean; const Buffer: Pointer;
  const BufSize: Integer): Integer;
```

_CreateEnvBlock_ creates a new environment block that can be used to pass to another process.

The new environment block is stored in the memory pointed to by _Buffer_, which is taken to be at least _BufSize_ characters in size. The actual size of the environment block is returned by _CreateEnvBlock_. If the buffer provided is nil or is too small then no block is created and the return value is the required buffer size in characters.

The _NewEnv_ and _IncludeCurrent_ parameters determine what is included in the new environment block. If the _NewEnv_ string list is not nil then it must contain a list of environment variables in the form `NAME=VALUE`. The new environment block will contain these values. If _IncludeCurrent_ is true then the new environment block will also include a copy of the current process' environment block.

The usual way to use _CreateEnvBlock_ is to call it once with a nil buffer to get the required buffer size in characters, allocate the buffer and then call _CreateEnvBlock_ again, this time passing the actual buffer and its size, for example:

```
var
  EnvBlock: Pointer;
  BlockSize: Integer;
  NewEnv: TStringList;
begin
  // Create and populate NewEnv
  // ...
  // Create the environment block: include NewEnv and process' own block
  BlockSize := CreateEnvBlock(NewEnv, True, nil, 0);
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

**WARNING:** _CreateEnvBlock_ deals with buffer sizes in characters, not bytes, which is not the same thing on Unicode Delphis. When allocating buffers in bytes (e.g. with _GetMem_) you must multiply the required size returned from _CreateEnvBlock_ by SizeOf(Char). Alternatively, use a routine such as _StrAlloc_ that automatically takes account of the character size.

The format of the environment block stored in _Buffer_ is a #0 character separated list of environment variables in `NAME=VALUE` form, terminated by two #0 characters.

## GetAllEnvVarNames ##

```
procedure GetAllEnvVarNames(const Names: TStrings); overload;
function GetAllEnvVarNames: TStringDynArray; overload;
```

Both overloaded versions of this routine fetch a list of the current environment variable names. Any blank names are excluded from the list.

The first version of the routine stores the environment variable names in the _Names_ string list. Any existing contents of the string list are discarded.

The second version creates and returns a dynamic string array containing the environment variable names. _TStringDynArray_ is defined in the _Types_ unit. If the version of Delphi being used does not have the _Types_ unit then _TStringDynArray_ is defined in _PJEnvVars_.

## EnvBlockSize ##

```
function EnvBlockSize: Integer;
```

This function returns the size of the current environment block in _characters_. To get the size in bytes multiply the returned value by `SizeOf(Char)`.