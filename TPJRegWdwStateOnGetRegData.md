#summary Description of the TPJRegWdwState.OnGetRegData method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnGetRegData event =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJRegWdwState TPJRegWdwState]_

{{{
type
  TPJWdwStateGetRegData = procedure(
    var RootKey: HKEY; var SubKey: string
  ) of object;

property OnGetRegData: TPJWdwStateGetRegData;
}}}

== Description ==

This event is triggered just before the registry is read when restoring and saving a window. The current values of the _[TPJRegWdwStateRootKey RootKey]_ and _[TPJRegWdwStateSubKey SubKey]_ properties are passed as var parameters of the same name to the event handler, allowing the user to change the values, and hence the location within the registry where the window data is recorded.

Any value assigned to the _!RootKey_ parameter must be a valid _HKEY_ or an exception will be raised. See the _[TPJRegWdwStateRootKey RootKey]_ documentation for a list of valid values.

The purpose of the event is to enable the _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ property to be used without setting the _[TPJRegWdwStateRootKey RootKey]_ and _[TPJRegWdwStateSubKey SubKey]_ properties at design time  - i.e. handling the event allows either or both of the default _[TPJRegWdwStateRootKey RootKey]_  and _[TPJRegWdwStateSubKey SubKey]_ values to be overridden.

=== Alternative Event ===

The _[TPJRegWdwStateOnGetRegDataEx OnGetRegDataEx]_*^v5.6^* event provides an alternative way of to change the registry root- and sub-keys. It is similar to _!OnGetRegData_ except that the root key is specified as one of the value from the _[TPJRegRootKey]_*^v5.6^* enumeration.

*Note:* You should choose which of _!OnGetRegData_ and _[TPJRegWdwStateOnGetRegDataEx OnGetRegDataEx]_*^v5.6^* to handle, but should not handle both events. If you do then _[TPJRegWdwStateOnGetRegDataEx OnGetRegDataEx]_*^v5.6^* will be triggered and _!OnGetRegData_ will be ignored.