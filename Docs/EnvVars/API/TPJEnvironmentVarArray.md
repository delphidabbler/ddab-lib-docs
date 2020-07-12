# TPJEnvironmentVarArray array type

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

```pascal
type
  TPJEnvironmentVarArray = array of TPJEnvironmentVar;
```

## Description

_TPJEnvironmentVarArray_ is a dymanic array of [_TPJEnvironmentVar_](./TPJEnvironmentVar.md) records.

It is used as the return type of one of the overloaded [_TPJEnvironmentVars.GetAll_](./TPJEnvironmentVars-GetAll.md) methods.
