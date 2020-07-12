# GetAll class methods

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class function GetAll(const Vars: TStrings): Integer; overload;
class function GetAll: TPJEnvironmentVarArray; overload;
```

## Description

There are two overloads of _GetAll_. Both of them get a list of all environment variables in the current process and return it to the user. The overloads differ in how the environment variables are returned.

### TStrings overload

```pascal
class function GetAll(const Vars: TStrings): Integer; overload;
```

This method returns the environment variables in the given string list in `Name=Value` format and returns the size of the environment block required to store all the variables.

***Parameters***

* _Vars_ -- Reference to a string list object that will receive the environment variables. Any previous contents are discarded. If `nil` is passed to this parameter then no environment variables are fetched.

***Returns***

* The minimum size of an environment block that contains all the environment variables, in _characters_.

When `nil` is be passed to _Vars_ the method returns the size of the block required for the environment variables, even though none are returned. Calling _GetAll_ in this way is the equivalent, but not as clear, as calling the [_BlockSize_](./TPJEnvironmentVars-BlockSize.md) method.

> **Important**. Like [_BlockSize_](./TPJEnvironmentVars-BlockSize.md),  _GetAll_ deals with buffer sizes in _characters_, not bytes.

### TPJEnvironmentVarArray overload

```pascal
class function GetAll: TPJEnvironmentVarArray; overload;
```

This form of the method returns an array of records that give details of each environment variable.

***Returns***

* [_TPJEnvironmentVarArray_](./TPJEnvironmentVarArray.md) dynamic array of [_TPJEnvironmentVar_](./TPJEnvironmentVar.md) records, each of which stores the name and value of an environment variable.
