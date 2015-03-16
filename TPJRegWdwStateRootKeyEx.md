#summary Description of the TPJRegWdwState.RootKeyEx property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !RootKeyEx property =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJRegWdwState TPJRegWdwState]_

*Introduced:* v5.6

{{{
property RootKeyEx: TPJRegRootKey;
}}}

== Description ==

This property allows the user to specify the registry root key under which the window size, position and state information is recorded. The information is saved in a subkey of this root key determined by the _[TPJRegWdwStateSubKey SubKey]_ property.

_!RootKeyEx_ can take any of the values of the _[TPJRegRootKey]_*^v5.6^* enumeration.

The property defaults to `hkCurrentUser`.

*Note:* The registry root key can also be specified by handling _[TPJRegWdwStateOnGetRegDataEx OnGetRegDataEx]_*^v5.6^* or _[TPJRegWdwStateOnGetRegData OnGetRegData]_ events. If this is done then the value of _!RootKeyEx_ is ignored.

===Alternative Property===

The _[TPJRegWdwStateRootKey RootKey]_ property provides an alternative way of setting the registry root key. Instead of taking a _[TPJRegRootKey]_*^v5.6^* value it takes an _HKEY_. *Note:* This property has been retained for backwards compatibilty reasons. You are recommended to use _!RootKeyEx_ in all new code.

There are two main reason why _!RootKeyEx_ is considered superior to _[TPJRegWdwStateRootKey RootKey]_:

  # It is impossible to specify an invalid root key value when using _!RootKeyEx_ because its value is restricted to those of the _[TPJRegRootKey]_*^v5.6^* enumeration which are all valid. Conversely it is easy to provide an invalid _HKEY_ value to _[TPJRegWdwStateRootKey RootKey]_.
  # _!RootKeyEx_ displays its values in a user-friendly way in Delphi's Object Inspector: the user chooses a value from a drop-down list of values. With _[TPJRegWdwStateRootKey RootKey]_ the user has to type the correct HKEY value into the Object Inspector.

Setting _!RootKeyEx_ changes the value of _[TPJRegWdwStateRootKey RootKey]_ and vice versa.