# TPJEnvironmentVar record

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

```pascal
type
  TPJEnvironmentVar = record
    Name: string;
    Value: string;
  end;
```

## Description

_TPJEnvironmentVar_ is a simple record that encapsulates the name and value of an environment variable, as follows:

| Field | Description |
|-------|-------------|
| _Name_ | Environment variable name. |
| _Value_ | Environment variable value. |
