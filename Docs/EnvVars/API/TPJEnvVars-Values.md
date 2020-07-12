# Values property

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvVars_](./TPJEnvVars.md)

```pascal
property Values[Name: string]: string;
```

> ***Warning:*** *[_TPJEnvVars_](./TPJEnvVars.md) has been **deprecated**. Use the [_TPJEnvironmentVars.GetValue_](./TPJEnvironmentVars-GetValue.md) and [_TPJEnvironmentVars.SetValue_](./TPJEnvironmentVars-SetValue.md) static methods instead of the _Values_ property.*

## Description

This property enables the current process' environment variables to be read and written by name.

To get the value of an environment variable treat the property as an array of values indexed by the environment variable name. For example `Value['Foo']` returns the value of an environment variable named `FOO`. If there is no environment variable with the required name then the empty string is returned.

Values of existing environment variables can be set by assigning string values to the property, indexed by the required environment variable name. For example `Values['Foo'] := 'Bar'` sets the environment variable `FOO` to have value `'Bar'`. If no environment variable with the given name exists, a new variable is created and set to the required value.

If an error occurs when setting an environment variable, for example if the environment space is full, a [_EPJEnvVars_](./EPJEnvVars.md) exception is raised.

> **Note:** Changing an environment variable by setting this property effects only this program's copy of the environment. It has **no effect** on the system's environment variables. Any changes are lost when the program closes.

The names of all current environment variables can be found using the [_EnumNames_](./TPJEnvVars-EnumNames.md) method.
