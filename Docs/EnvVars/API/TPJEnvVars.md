# TPJEnvVars component

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

> ***Warning:*** *This component is **deprecated*** and is retained for backward compatibility only. New code should use the [_TPJEnvironmentVars_](./TPJEnvironmentVars.md) static class instead.

## Description

_TPJEnvVars_ provides access to the environment variables in the current process' environment block. Environment variables can be read, created, updated or deleted. The names of all available environment variables can also be enumerated.

Only one instance of a _TPJEnvVars_ component can be placed on any form or frame. An attempt to create duplicate instances on a form causes an exception to be raised.

### Methods

| Method | Description |
|--------|-------------|
| [_Create_](./TPJEnvVars-Create.md) | Constructs an instance of the component. |
| [_DeleteVar_](./TPJEnvVars-DeleteVar.md) | Deletes an environment variable. |
| [_EnumNames_](./TPJEnvVars-EnumNames.md) | Enumerates all environment variable names, passing each name to a callback method. |
| [_GetEnumerator_](./TPJEnvVars-GetEnumerator.md) | Creates an enumerator that can be used to enumerate all environment variable names. On Delphi 2005 and later this enumerator enables the component to be used `for..in` loops. |

### Properties

| Property | Description |
|----------|-------------|
| [_Count_](./TPJEnvVars-Count.md) | Returns the number of available environment variables. |
| [_Values_](./TPJEnvVars-Values.md) | Provides read / write access to environment variables. |

### Events

_TPJEnvVars_ exposes no events.
