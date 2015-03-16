#summary TPJRegRootKey enumerated type description
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= TPJRegRootKey type =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_.

*Introduced:* v5.6

{{{
type
  TPJRegRootKey = (
    hkClassesRoot, hkCurrentUser, hkLocalMachine,
    hkUsers, hkPerformanceData, hkCurrentConfig, hkDynData
  );
}}}

== Description ==

This enumerated type has an entry for each supported type of registry root key.

Each value represents a value defined by one of the _HKEY_xxx_ constants as follows:

|| *TPJRegRootKey value* || *HKEY constant* ||
|| `hkClassesRoot` || `HKEY_CLASSES_ROOT` ||
|| `hkCurrentUser` || `HKEY_CURRENT_USER` ||
|| `hkLocalMachine` || `HKEY_LOCAL_MACHINE` ||
|| `hkUsers` || `HKEY_USERS` ||
|| `hkPerformanceData` || `HKEY_PERFORMANCE_DATA` ||
|| `hkCurrentConfig` || `HKEY_CURRENT_CONFIG` ||
|| `hkDynData` || `HKEY_DYN_DATA` ||

_TPJRegRootKey_ is used as the type for the _[TPJRegWdwState].[TPJRegWdwStateRootKeyEx RootKeyEx]_*^v5.6^* property and the _!RootKeyEx_ parameter of the _[TPJRegWdwState].[TPJRegWdwStateOnGetRegDataEx OnGetRegDataEx]_*^v5.6^* event.