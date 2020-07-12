# [Environment Variables Unit](../EnvVars.md) Programmers Guide

## Introduction

This section of the _Environment Variables Unit_ documentation focusses on describing the usage of unit's code.

> **This documentation refers to v3.0 or later of the unit only.**
>
> Earlier versions are no longer supported and no documentation is available.

The project is made up of two units:

| Unit | Description |
|------|-------------|
| _PJEnvVars_ | The all the run time code. This includes a static class for manipulating environment vaiables, an environment variable enumerator, various supporting types and a ***deprecated*** component and related routines. See [Contents](#contents) below for details. |
| _PJEnvVarsDsgn_ | ***Deprecated*** Registers the [_TPJEnvVars_](./API/TPJEnvVars.md) component  with the Delphi IDE. No further documentation for this unit is available. |

## Contents

This guide is divided into the following sections:

* [_TPJEnvironmentVars_](./API/TPJEnvironmentVars.md) -- static class for reading and manipulating environment variables.
* [_TPJEnvVars_](./API/TPJEnvVars.md) -- ***deprecated*** component for eading and manipulating environment variables.
* [_TPJEnvVarsEnumerator_](./API/TPJEnvVarsEnumerator.md) -- enumerates all the environment variable names in the current process.
* [Other Types](./API/Types.md) -- other types used by [_TPJEnvironmentVars_](./API/TPJEnvironmentVars.md) and [_TPJEnvVars_](./API/TPJEnvVars.md).
* [Helper Routines](./API/Routines.md) -- ***deprecated*** various environment variable manipulation routines.

## Conventions

Identifiers in plain text appear like this: _Identifier_

Identifiers in links appear like this: [_Identifier_](#conventions)

Values and in-line code appear like this:

* `42`
* `'text'`
* `True`
* `X := 42;`

Declarations and source code examples appear syntax highlighted like this:

```pascal
procedure Foo(const Bar: string);
```

## Links

* [Overview](./Overview.md)
