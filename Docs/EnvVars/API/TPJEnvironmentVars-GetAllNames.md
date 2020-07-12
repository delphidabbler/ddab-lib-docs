# GetAllNames class methods

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class procedure GetAllNames(const Names: TStrings); overload;
class function GetAllNames: TStringDynArray; overload;
```

## Description

There are two overloads of _GetAllNames_. Both of them get a list of the names of all environment variables in the current process and return it to the user. The overloads differ in how the names are returned.

### TStrings overload

```pascal
class procedure GetAllNames(const Names: TStrings); overload;
```

This method returns the environment variable names in the given string list.

***Parameters:***

* _Names_ -- Reference to a string list object that will receive the environment variable names. Any previous contents are discarded. _Names_ must not be `nil`.

### TStringDynArray overload

```pascal
class function GetAllNames: TStringDynArray; overload;
```

This form of the method returns an array of environment variable names.

***Returns:***

* A _TStringDynArray_ dynamic array of strings containing the environment variable names.

> _TStringDynArray_ is defined as `array of string` in Delphi 6 and later. As a convenience to Delphi 5 and earlier users, _PJEnvVars_ defines _TStringDynArray_ when compiled with those compilers.
