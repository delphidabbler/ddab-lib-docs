<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# GetEnumerator method #

| This is the documentation for the **v2.0** release of the unit. If you are using a **version 3** release please [see here](http://wiki.delphidabbler.com/index.php/Docs/TPJEnvVarsGetEnumerator). |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

**Project:** [Environment Variables Unit](EnvironmentVariablesUnit.md).

**Unit:** _PJEnvVars_.

**Class:** _[TPJEnvVars](TPJEnvVars.md)_

```
function GetEnumerator: TPJEnvVarsEnumerator;
```

## Description ##

_GetEnumerator_ creates an enumerator of type _[TPJEnvVarsEnumerator](TPJEnvVarsEnumerator.md)_ that can be used to enumerate the names of all environment variables in the current environment block. This can be used as an alternative to the _[EnumNames](TPJEnvVarsEnumNames.md)_ method.

By providing this method _[TPJEnvVars](TPJEnvVars.md)_ supports the <strong>for..in</strong> Delphi language construct that was introduced in Delphi 2005. Environment variable names can be enumerated as follows:

```
var
  Name: string;
begin
  for Name in PJEnvVars1 do
  begin
    // do something with Name here
  end;
end;
```

In the above code _PJEnvVars1_ is assumed to be a _[TPJEnvVars](TPJEnvVars.md)_ component instance. The compiler calls _GetEnumerator_ and manipulates the enumerator internally.

Compilers before Delphi 2005 can still use the enumerator by calling
_GetEnumerator_ explicitly to get an [enumerator object](TPJEnvVarsEnumerator.md) instance. The enumerator can then be manipulated as required. For example:

```
var
  Name: string;
  Enum: TPJEnvVarsEnumerator;
begin
  Enum := PJEnvVars1.GetEnumerator;
  try
    while Enum.MoveNext do
    begin
      Name := Enum.Current;
      // do something with Name here
    end;
  finally
    Enum.Free;
  end;
end;
```

Again, _PJEnvVars1_ is a _[TPJEnvVars](TPJEnvVars.md)_ component instance.

**Warning:** If you call _GetEnumerator_ explicitly you must free the enumerator when you have finished using it.

**See also**

  * _[TPJEnvVarsEnumerator documentation](TPJEnvVarsEnumerator.md)_