# TPJCustomWdwState #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

This is the abstract base class for the _[TPJWdwState](TPJWdwState.md)_, _[TPJRegWdwState](TPJRegWdwState.md)_ and _[TPJUserWdwState](TPJUserWdwState.md)_ components. It provides the common functionality and properties of the derived components. _[TPJWdwState](TPJWdwState.md)_, _[TPJRegWdwState](TPJRegWdwState.md)_ and _[TPJUserWdwState](TPJUserWdwState.md)_ simply add the methods and / or events used to store and read window state information along with any properties and events relevant to the desired storage.

_TPJCustomWdwState_ can be used as a base class for further window state components that use other forms of storage. To derive a new component you must override the protected abstract methods _[ReadWdwState](TPJCustomWdwStateReadWdwState.md)_ and _[SaveWdwState](TPJCustomWdwStateSaveWdwState.md)_ to read and save window size, position and state information via the desired storage medium.

Instances of _TPJCustomWdwState_ must not be constructed directly.

_TPJCustomWdwState_ exposes the following methods, properties and events in addition to those inherited from _TComponent_.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[Create](TPJCustomWdwStateCreate.md)_ | Class constructor that permits only one instance of the component to be placed on a form. |
| _[CreateStandAlone](TPJCustomWdwStateCreateStandAlone.md)_ | Class constructor for use when creating components at run time. |
| _[ReadWdwState](TPJCustomWdwStateReadWdwState.md)_ | Protected abstract method called to read a window's size, position and state from storage. Derived classes must override. |
| _[Restore](TPJCustomWdwStateRestore.md)_ | Restores the size, position and state of a window. |
| _[Save](TPJCustomWdwStateSave.md)_ | Saves the size, position and state of the window. |
| _[SaveWdwState](TPJCustomWdwStateSaveWdwState.md)_ | Protected abstract method called to write a window's size, position and state to storage. Derived classes must override. |

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ | Determines whether the window's size, position and state is automatically restored on creation and stored on destruction. |
| _[IgnoreState](TPJCustomWdwStateIgnoreState.md)_ | Determines whether the window's saved state (maximised, normal or minimised) is applied on restoration. This property is deprecated - use the _[Options](TPJCustomWdwStateOptions.md)_ property instead. |
| _[MinimizeDelay](TPJCustomWdwStateMinimizeDelay.md)_ | Sets the delay between displaying a normalised form on screen and minimising it if required. |
| _[Options](TPJCustomWdwStateOptions.md)_ | Determines how the component interprets the window display data read from storage. |

## Events ##

### Protected ###

| **Event** | **Description** |
|:----------|:----------------|
| _[OnReadWdwState](TPJCustomWdwStateOnReadWdwState.md)_ | Event that allows user to change the window data read from storage before the window is displayed. |

### Published ###

| **Event** | **Description**|
|:----------|:---------------|
| _[OnAfterWindowRestored](TPJCustomWdwStateOnAfterWindowRestored.md)_ **<sup>v5.4</sup>** | Event triggered after window has been restored and its state set. |
| _[OnAfterWindowSized](TPJCustomWdwStateOnAfterWindowSized.md)_ **<sup>v5.4</sup>** | Event triggered after the window is sized but before it is physically restored. |
