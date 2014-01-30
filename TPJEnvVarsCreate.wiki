#summary Description of the TPJEnvVars.Create method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Create method =

|| This is the documentation for the *v2.0* release of the unit. If you are using a *version 3* release please [http://wiki.delphidabbler.com/index.php/Docs/TPJEnvVarsCreate see here]. ||

*Project:* [EnvironmentVariablesUnit Environment Variables Unit].

*Unit:* _PJEnvVars_.

*Class:* _[TPJEnvVars TPJEnvVars]_

{{{
constructor Create(AOwner: TComponent);
}}}

== Description ==

_Create_ constructs a new instance of the component. Only one instance of a _[TPJEnvVars TPJEnvVars]_ component is allowed on any form (or to be owned by any component). An attempt to create a second instance will cause an _Exception_ to be raised and the duplicate instance will not be created.

Multiple instances can be created by passing nil as the owner.
