#summary Description of the TPJEnvVars.EnumNames method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !EnumNames method =

|| This is the documentation for the *v2.0* release of the unit. If you are using a *version 3* release please [http://wiki.delphidabbler.com/index.php/Docs/TPJEnvVarsEnumNames see here]. ||

*Project:* [EnvironmentVariablesUnit Environment Variables Unit].

*Unit:* _PJEnvVars_.

*Class:* _[TPJEnvVars TPJEnvVars]_

{{{
type
  TPJEnvVarsEnum = procedure(const VarName: string; Data: Pointer) of object;

procedure EnumNames(Callback: TPJEnvVarsEnum; Data: Pointer);
}}}

== Description ==

_!EnumNames_ enumerates all environment variables in the current environment block. The _Callback_ method is called once for each environment variable and is passed the name of the environment variable and a data value supplied as a parameter to _!EnumNames_. _Data_ is a user defined value and is not processed by _!EnumNames_.

The user must implement _Callback_ as a method.

The values associated with the environment variables can be accessed using the _[TPJEnvVarsValues Values]_ property.
