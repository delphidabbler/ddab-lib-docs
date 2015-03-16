<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# DeleteVar method #

| This is the documentation for the **v2.0** release of the unit. If you are using a **version 3** release please [see here](http://wiki.delphidabbler.com/index.php/Docs/TPJEnvVarsDeleteVar). |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

**Project:** [Environment Variables Unit](EnvironmentVariablesUnit.md).

**Unit:** _PJEnvVars_.

**Class:** _[TPJEnvVars](TPJEnvVars.md)_

```
procedure DeleteVar(const Name: string);
```

## Description ##

Deletes the named environment variable. Does nothing if the environment variable does not exist. This is functionally the same as setting `Values[Name] := '';`

A _[EPJEnvVars](EPJEnvVars.md)_ exception is raised if it is not possible to delete the variable.

**NOTE:** This method has no effect on the system environment variables, only on the copy of the environment maintained by this program.