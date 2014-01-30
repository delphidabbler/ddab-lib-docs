#summary Description of the TPJEnvVars.GetEnumerator method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !GetEnumerator method =

|| This is the documentation for the *v2.0* release of the unit. If you are using a *version 3* release please [http://wiki.delphidabbler.com/index.php/Docs/TPJEnvVarsGetEnumerator see here]. ||

*Project:* [EnvironmentVariablesUnit Environment Variables Unit].

*Unit:* _PJEnvVars_.

*Class:* _[TPJEnvVars TPJEnvVars]_

{{{
function GetEnumerator: TPJEnvVarsEnumerator;
}}}

== Description ==

_!GetEnumerator_ creates an enumerator of type _[TPJEnvVarsEnumerator TPJEnvVarsEnumerator]_ that can be used to enumerate the names of all environment variables in the current environment block. This can be used as an alternative to the _[TPJEnvVarsEnumNames EnumNames]_ method.

By providing this method _[TPJEnvVars TPJEnvVars]_ supports the <strong>for..in</strong> Delphi language construct that was introduced in Delphi 2005. Environment variable names can be enumerated as follows:

{{{
var
  Name: string;
begin
  for Name in PJEnvVars1 do
  begin
    // do something with Name here
  end;
end;
}}}

In the above code _PJEnvVars1_ is assumed to be a _[TPJEnvVars TPJEnvVars]_ component instance. The compiler calls _!GetEnumerator_ and manipulates the enumerator internally.

Compilers before Delphi 2005 can still use the enumerator by calling
_!GetEnumerator_ explicitly to get an [TPJEnvVarsEnumerator enumerator object] instance. The enumerator can then be manipulated as required. For example:

{{{
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
}}}

Again, _PJEnvVars1_ is a _[TPJEnvVars TPJEnvVars]_ component instance.

*Warning:* If you call _!GetEnumerator_ explicitly you must free the enumerator when you have finished using it.

*See also*

  * _[TPJEnvVarsEnumerator TPJEnvVarsEnumerator documentation]_
