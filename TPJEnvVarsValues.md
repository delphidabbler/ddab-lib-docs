<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# Values property #

| This is the documentation for the **v2.0** release of the unit. If you are using a **version 3** release please [see here](http://wiki.delphidabbler.com/index.php/Docs/TPJEnvVarsValues). |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

**Project:** [Environment Variables Unit](EnvironmentVariablesUnit.md).

**Unit:** _PJEnvVars_.

**Class:** _[TPJEnvVars](TPJEnvVars.md)_

```
property Values[Name: string]: string
```

## Description ##

The _Values_ property enables the current process' environment variables to be read and written by name.

To get the value of an environment variable treat the _Values_ property as an array of values indexed by the environment variable name. For example `Value['Foo']` returns the value of an environment variable named `FOO`. If there is no environment variable with the required name then the empty string is returned.

Values of existing environment variables can be set by assigning string values to the property, indexed by the required environment variable name. For example `Values['Foo'] := 'Bar'` sets the environment variable `FOO` to have value `'Bar'`. If no environment variable with the given name exists, a new variable is created and set to the required value. Setting an environment variable to the empty string deletes it.

If an error occurs when setting an environment variable, for example if the environment space is full, a _[EPJEnvVars](EPJEnvVars.md)_ exception is raised.

**NOTE:** Changing an environment variable by setting this property effects only this program's copy of the environment. It has no effect on the system's environment variables.

The names of all current environment variables can be found using the _[EnumNames](TPJEnvVarsEnumNames.md)_ method.