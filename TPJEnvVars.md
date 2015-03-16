<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# TPJEnvVars #

| This is the documentation for the **v2.0** release of the unit. If you are using a **version 3** release please [see here](http://wiki.delphidabbler.com/index.php/Docs/TPJEnvVars). |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

**Project:** [Environment Variables Unit](EnvironmentVariablesUnit.md).

**Unit:** _PJEnvVars_.

This component provides access to the environment variables in the current process' environment block. Environment variables can be read, created, updated or deleted. The names of all available environment variables can also be enumerated.

Only one instance of a _TPJEnvVars_ component can be placed on any form. An attempt to place further instances on a form causes an exception to be raised.

## Methods ##

_TPJEnvVars_ defines the following methods in addition to those inherited from
_TComponent_.

| **Method** | **Description** |
|:-----------|:----------------|
| _[Create](TPJEnvVarsCreate.md)_ | Object constructor. Permits only one instance to be placed on any form. |
| _[DeleteVar](TPJEnvVarsDeleteVar.md)_ | Deletes an environment variable. |
| _[EnumNames](TPJEnvVarsEnumNames.md)_ | _This is a redundant method provided for backward compatibility reasons only._ It enumerates all environment variable names, passing each name to a callback method. _[GetEnumerator](TPJEnvVarsGetEnumerator.md)_ or <strong>for..in</strong> loops, where supported, should be used in preference. |
| _[GetEnumerator](TPJEnvVarsGetEnumerator.md)_ | Creates an [enumerator](TPJEnvVarsEnumerator.md) that can be used to enumerate all environment variable names. On Delphi 2005 and later this enumerator enables the <strong>for..in</strong> construct to be used with the component. |


## Properties ##

_TPJEnvVars_ defines the following properties in addition to those inherited from _TComponent_.

| **Property** | **Description** |
|:-------------|:----------------|
| _[Count](TPJEnvVarsCount.md)_ | Returns the number of environment variables. |
| _[Values](TPJEnvVarsValues.md)_ | Provides read / write access to environment variables. |

## Events ##

_TPJEnvVars_ defines no events.