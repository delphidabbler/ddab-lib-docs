# TPJEnvVarsEnumerator class

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

## Description

Implements an enumerator for the names of all environment variable names in the current process.

> **Note:** This class was originally provided to work with the ***deprecated*** [_TPJEnvVars_](./TPJEnvVars.md) component's [_GetEnumerator_](./TPJEnvVars-GetEnumerator.md) method to enable [_TPJEnvVars_](./TPJEnvVars.md) instances to be enumerated in `for..in` statements when compiled with Delphi 2005 or later. The class can also be used directly from code.
>
> **Important:** Environments variables should not be modified while the enumerator is being used. Any addition or deletion of environment variables will not be reflected in the enumeration. Making such changes can result in obscure bugs.

### Methods

| Method | Description |
|--------|-------------|
| _Create_ | Constructs and initialises a new enumeration object instance. |
| _GetCurrent_ | Returns the name of the current environment variable in the enumeration. Can be used interchangeably with the _Count_ property. |
| _MoveNext_ | Moves to the next name in the enumeration if it exists. Returns `True` if it was possible to move to the next item or `False` if there are no more items in the enumeration. |

### Properties

| Property | Description |
|----------|-------------|
| _Current_ | Records the name of the current environment variable in the enumeration. Can be used interchangeably with the _GetCount_ method. |

## Example

This is an example of using _TPJEnvVarsEnumerator_ directly from code. The code writes the names of every environment variable to the console.

```pascal
var
  Enum: TPJEnvVarsEnumerator;
begin
  Enum := TPJEnvVarsEnumerator.Create;
  try
    while Enum.MoveNext do
      WriteLn(Enum.Current);
  finally
    Enum.Free;
  end;
end;
```
