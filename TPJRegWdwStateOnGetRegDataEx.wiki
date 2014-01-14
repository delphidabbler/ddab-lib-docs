#summary Description of the TPJRegWdwState.OnGetRegDataEx method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnGetRegDataEx event =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJRegWdwState TPJRegWdwState]_

*Introduced:* v5.6

{{{
type
  TPJWdwStateGetRegDataEx = procedure(
    var RootKeyEx: TPJRegRootKey; var SubKey: string
  ) of object;

property OnGetRegDataEx: TPJWdwStateGetRegDataEx;
}}}

== Description ==

This event is triggered just before the registry is read when restoring and saving a window. The current values of the _[TPJRegWdwStateRootKeyEx RootKeyEx]_*^5.6^* and _[TPJRegWdwStateSubKey SubKey]_ properties are passed as var parameters of the same name to the event handler, allowing the user to change the values, and hence the location within the registry where the window data is recorded.

The _!RootKeyEx_ parameter can be set to any of the values from the _[TPJRegRootKey]_*^v5.5^* enumeration.

The purpose of the event is to enable the _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ property to be used without setting the _[TPJRegWdwStateRootKeyEx RootKeyEx]_*^5.6^* and _[TPJRegWdwStateSubKey SubKey]_ properties at design time  - i.e. handling the event allows either or both of the default _[TPJRegWdwStateRootKeyEx RootKeyEx]_*^5.6^* and _[TPJRegWdwStateSubKey SubKey]_ values to be overridden.

=== Alternative Event ===

The _[TPJRegWdwStateOnGetRegData OnGetRegData]_ event provides an alternative way of to change the registry root- and sub-keys. It is similar to _!OnGetRegDataEx_ except that the root key is specified as a valid _HKEY_ value.

*Note:* You are recommended to use _!OnGetRegDataEx_ in preference to _[TPJRegWdwStateOnGetRegData OnGetRegData]_. If you choose to handle _[TPJRegWdwStateOnGetRegData OnGetRegData]_ do not also handle _!OnGetRegDataEx_ because doing so prevents _[TPJRegWdwStateOnGetRegData OnGetRegData]_ from being fired.