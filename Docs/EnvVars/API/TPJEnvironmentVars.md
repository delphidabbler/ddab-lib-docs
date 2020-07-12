# TPJEnvironmentVars class

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

## Description

This is a _static class_ that provides methods for interogating, manipulating and modifying the environment variables available to the current process.

**Warning:** This class must never be constructed: all its methods are class methods. No standard methods, properties or events are defined. Attempting to construct it will raise an _ENoConstructException_ exception.

### Class Methods

| Method | Description |
|--------|-------------|
| [_BlockSize_](./TPJEnvironmentVars-BlockSize.md) | Returns the size of the current environment block. |
| [_Count_](./TPJEnvironmentVars-Count.md) | Returns the number of available environment variables. |
| _Create_ | This constructor must never be called. If it is called it will raise an _ENoConstructException_ exception. |
| [_CreateBlock_](./TPJEnvironmentVars-CreateBlock.md) | Creates a new custom environment block. |
| [_Delete_](./TPJEnvironmentVars-Delete.md) | Deletes an environment variable. |
| [_EnumNames_](./TPJEnvironmentVars-EnumNames.md) | Enumerates the names of all available environment variables. |
| [_EnumVars_](./TPJEnvironmentVars-EnumVars.md) | Enumerates all available environment variables. |
| [_Exists_](./TPJEnvironmentVars-Exists.md) | Checks if a given environment variable exists. |
| [_Expand_](./TPJEnvironmentVars-Expand.md) | Expands a string containing environment variables by replacing each environment variable name with its value. |
| [_GetAll_](./TPJEnvironmentVars-GetAll.md) | Overloaded methods that get a list of all available environment variables. |
| [_GetAllNames_](./TPJEnvironmentVars-GetAllNames.md) | Overloaded methods that get a list of the names of all available environment variables. |
| [_GetValue_](./TPJEnvironmentVars-GetValue.md) | Returns the value of an environment variable. |
| [_SetValue_](./TPJEnvironmentVars-SetValue.md) | Sets the value of an environment variable. |
