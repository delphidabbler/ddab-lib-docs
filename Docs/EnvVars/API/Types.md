# Other Types

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

The _PJEnvVars_ unit contains the following types that are required by the main classes.

|  Type |  Description |
|-------|--------------|
| [_EPJEnvVars_](./EPJEnvVars.md) ***(deprecated)*** | Class of exception raised to report errors that occur when using the [_TPJEnvVars_](./TPJEnvVars.md) component. |
| [_TPJEnvironmentVar_](./TPJEnvironmentVar.md) | Record that encapsulates an environment variable's name and value. |
| [_TPJEnvironmentVarArray_](./TPJEnvironmentVarArray.md) | A dynamic array of [_TPJEnvironmentVar_](./TPJEnvironmentVar.md) records. |
| [_TPJEnvVarsEnum_](./TPJEnvVarsEnum.md) | Type of callback method that is called when enumerating environment variable names in [_TPJEnvironmentVars.EnumNames_](./TPJEnvironmentVars-EnumNames.md) or [_TPJEnvVars.EnumNames_](./TPJEnvVars-EnumNames.md). |
| [_TPJEnvVarsEnumEx_](./TPJEnvVarsEnumEx.md) | Type of callback method (or anonymous method) that is called when enumerating environment variable name / value pairs in [_TPJEnvironmentVars.EnumVars_](./TPJEnvironmentVars-EnumVars.md). |
