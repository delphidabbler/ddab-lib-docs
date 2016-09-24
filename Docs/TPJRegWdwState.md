# TPJRegWdwState #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

This non-visual component enables the size, position and state of the form on which it is placed to be saved to and read from the registry.

**NOTE:** It is **strongly** recommended that this component is not used in 32 bit applications compiled with Delphi 5 and earlier that are to be run on 64 bit Windows operating systems. This is because the _TRegistry_ class used by _TPJRegWdwState_ does not support the permissions needed to access the 64 bit registry view.

The _[Save](TPJRegWdwStateSave.md)_ method saves the window information to the registry and the _[Restore](TPJRegWdwStateRestore.md)_ method reads information in and sets the owning form window's size, position and state.

The component's _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property governs whether window sizes, positions and states are automatically restored on opening and saved on closing or whether the user must explicitly call the _[Save](TPJRegWdwStateSave.md)_ and _[Restore](TPJRegWdwStateRestore.md)_ methods.

The _[Options](TPJCustomWdwStateOptions.md)_ property and the _[OnReadWdwState](TPJCustomWdwStateOnReadWdwState.md)_ event can be used to customise how the stored data is interpreted and whether the window's saved state or size should be used or ignored.

Application defined data can be read from and written to the registry by handling the _[OnGettingRegData](TPJRegWdwStateOnGettingRegData.md)_**<sup>v5.1</sup>** and _[OnPuttingRegData](TPJRegWdwStateOnPuttingRegData.md)_**<sup>v5.1</sup>** events that are triggered when the component reads and writes its data.

The root and sub key to be used in the registry are specified using the _[RootKey](TPJRegWdwStateRootKey.md)_ (or _[RootKeyEx](TPJRegWdwStateRootKeyEx.md)_**<sup>v5.6</sup>**) and _[SubKey](TPJRegWdwStateSubKey.md)_ properties respectively. Alternatively the _[OnGetRegData](TPJRegWdwStateOnGetRegData.md)_ (or _[OnGetRegDataEx](TPJRegWdwStateOnGetRegDataEx.md)_**<sup>v5.6</sup>**) event can be handled and used to set the root key and sub key to use.

It is only possible to have one instance of a _TPJRegWdwState_ component on any one form. Neither can a _TPJRegWdwState_ component be dropped onto a form that already contains either a _[TPJWdwState](TPJWdwState.md)_ or a _[TPJUserWdwState](TPJUserWdwState.md)_ component.

_TPJRegWdwState_ exposes the following methods, properties and events, some of which are inherited unchanged from _[TPJCustomWdwState](TPJCustomWdwState.md)_.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[Create](TPJCustomWdwStateCreate.md)_ | Class constructor that permits only one instance of the component to be placed on a form. |
| _[CreateStandAlone](TPJCustomWdwStateCreateStandAlone.md)_ | Class constructor for use when creating components at run time. |
| _[ReadWdwState](TPJRegWdwStateReadWdwState.md)_ | Overridden method that reads a window's size, position and state from the registry. |
| _[Restore](TPJRegWdwStateRestore.md)_ | Restores the size, position and state of a window from the registry. |
| _[Save](TPJRegWdwStateSave.md)_ | Saves the size, position and state of the window to the registry. |
| _[SaveWdwState](TPJRegWdwStateSaveWdwState.md)_ | Overridden method that writes a window's size, position and state to the registry. |

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ | Determines whether the window's size, position and state is automatically restored on creation and stored on destruction. |
| _[IgnoreState](TPJCustomWdwStateIgnoreState.md)_ | Determines whether the window's saved state (maximised, normal or minimised) is applied on restoration. This property is deprecated - use the _[Options](TPJCustomWdwStateOptions.md)_ property instead. |
| _[MinimizeDelay](TPJCustomWdwStateMinimizeDelay.md)_ | Sets the delay between displaying a normalised form on screen and minimising it if required. |
| _[Options](TPJCustomWdwStateOptions.md)_ | Determines how the component interprets the window display data read from storage. |
| _[RootKey](TPJRegWdwStateRootKey.md)_ | Specifies the _HKEY_ value of the registry root key under which the window's size, position and state information is stored. |
| _[RootKeyEx](TPJRegWdwStateRootKeyEx.md)_**<sup>v5.6</sup>** | Similar to _[RootKey](TPJRegWdwStateRootKey.md)_ except that instead of taking an _HKEY_ value it takes a value from the _[TPJRegRootKey](TPJRegRootKey.md)_**<sup>v5.6</sup>** enumeration. |
| _[SubKey](TPJRegWdwStateSubKey.md)_ | Determines the registry sub key under which the window's size, position and state information is stored. |

## Events ##

| **Event** | **Description** |
|:----------|:----------------|
| _[OnAfterWindowRestored](TPJCustomWdwStateOnAfterWindowRestored.md)_**<sup>v5.4</sup>** | Event triggered after window has been restored and its state set. |
| _[OnAfterWindowSized](TPJCustomWdwStateOnAfterWindowSized.md)_**<sup>v5.4</sup>** | Event triggered after the window is sized but before it is physically restored. |
| _[OnGetRegData](TPJRegWdwStateOnGetRegData.md)_ | Event that allows user to change the registry key where window information is stored. The registry root key is specified by it _HKEY_ value. |
| _[OnGetRegDataEx](TPJRegWdwStateOnGetRegDataEx.md)_**<sup>v5.6</sup>** | Similar to _[OnGetRegData](TPJRegWdwStateOnGetRegData.md)_ except that the root key is specified by a value from the _[TPJRegRootKey](TPJRegRootKey.md)_**<sup>v5.6</sup>** enumeration.  |
| _[OnGettingRegData](TPJRegWdwStateOnGettingRegData.md)_**<sup>v5.1</sup>** | Event that allows user to read additional registry data when the component reads window state information. |
| _[OnPuttingRegData](TPJRegWdwStateOnPuttingRegData.md)_**<sup>v5.1</sup>** | Event that allows user to write additional registry data when the component writes window state information. |
| _[OnReadWdwState](TPJCustomWdwStateOnReadWdwState.md)_ | Event that allows user to change the window data read from storage before the window is displayed. _TPJRegWdwState_ publishes this inherited protected event. |
