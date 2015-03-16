<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# EnumNames method #

| This is the documentation for the **v2.0** release of the unit. If you are using a **version 3** release please [see here](http://wiki.delphidabbler.com/index.php/Docs/TPJEnvVarsEnumNames). |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

**Project:** [Environment Variables Unit](EnvironmentVariablesUnit.md).

**Unit:** _PJEnvVars_.

**Class:** _[TPJEnvVars](TPJEnvVars.md)_

```
type
  TPJEnvVarsEnum = procedure(const VarName: string; Data: Pointer) of object;

procedure EnumNames(Callback: TPJEnvVarsEnum; Data: Pointer);
```

## Description ##

_EnumNames_ enumerates all environment variables in the current environment block. The _Callback_ method is called once for each environment variable and is passed the name of the environment variable and a data value supplied as a parameter to _EnumNames_. _Data_ is a user defined value and is not processed by _EnumNames_.

The user must implement _Callback_ as a method.

The values associated with the environment variables can be accessed using the _[Values](TPJEnvVarsValues.md)_ property.