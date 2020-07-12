# Expand class method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class function Expand(const Str: string): string;
```

## Description

Expands a string containing environment variables by replacing each environment variable name with its value.

***Parameters:***

* _Str_ -- A string containing zero or more environment variables names that are to be expanded. Each environment variable name must be enclosed in `%` characters, for example `%ENVVAR%`.

***Returns***

* The string with enviroment variable names relaced with their values.

If an environment variable does not exist then its name and enclosing `%` characters are left unmodified in the result string. The case of the environment variable name is not significant, i.e. `%ENVVAR%` is the same as `%envvar%`.

## Example

The following code shows how _Expand_ handles strings with zero, one and two valid environment variables along with how an undefined environment variable is handled.

```pascal
begin
  WriteLn(./TPJEnvironmentVars.Expand('No variables')); // no variables
  TPJEnvironmentVars.SetValue('FOO', 'Lorem');   // defines FOO
  WriteLn(./TPJEnvironmentVars.Expand('One good variable: %FOO%'));
  TPJEnvironmentVars.SetValue('BAR', 'Ipsum');   // defines BAR
  WriteLn(./TPJEnvironmentVars.Expand('Two good variables: %FOO% & %BAR%'));
  TPJEnvironmentVars.Delete('FOO');              // FOO no longer defined
  WriteLn(./TPJEnvironmentVars.Expand('Good and bad variables: %FOO% & %BAR%'));
end;
```

When this code is run it writes the following:

```pascal
No variables
One good variable: Lorem
Two good variables: Lorem & Ipsum
Good and bad variables: %FOO% & Ipsum
```
