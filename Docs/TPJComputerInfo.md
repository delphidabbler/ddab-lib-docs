# TPJComputerInfo #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

This is a static class that provides information about the host computer. The class' functionality is all exposed via its static methods. Because it is static the class does not need to be instantiated before use.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[BiosVendor](TPJComputerInfoBiosVendor.md)_ [v4.0] | Gets the name of the computer's BIOS vendor. |
| _[BootMode](TPJComputerInfoBootMode.md)_ [v3.1] | Determines the operating system mode into which the the computer was booted. |
| _[ComputerName](TPJComputerInfoComputerName.md)_ | Gets the computer's name. |
| _[Is64Bit](TPJComputerInfoIs64Bit.md)_ | Checks if processor is 64 bit. |
| _[IsAdmin](TPJComputerInfoIsAdmin.md)_ [v4.0] | Checks if the current user has administrator privileges. |
| _[IsNetworkPresent](TPJComputerInfoIsNetworkPresent.md)_ [v3.1] | Checks if a network is present. |
| _[IsUACActive](TPJComputerInfoIsUACActive.md)_ [v4.0] | Checks if UAC is active on the computer. |
| _[MACAddress](TPJComputerInfoMACAddress.md)_ | Gets the address of the first network card in the computer. |
| _[Processor](TPJComputerInfoProcessor.md)_ | Gets the kind of processor used in the computer. |
| _[ProcessorCount](TPJComputerInfoProcessorCount.md)_ | Gets the number of processors in the computer. |
| _[ProcessorIdentifier](TPJComputerInfoProcessorIdentifier.md)_ [v4.0] | Gets the identifier of the computer's processor. |
| _[ProcessorName](TPJComputerInfoProcessorName.md)_ [v4.0] | Gets the name of the computer's processor. |
| _[ProcessorSpeedMHz](TPJComputerInfoProcessorSpeedMHz.md)_ [v5.4] | Gets the speed of the computer's processor in MHz. |
| _[SystemManufacturer](TPJComputerInfoSystemManufacturer.md)_ [v4.0] | Gets the name of the computer's manufacturer. |
| _[SystemProductName](TPJComputerInfoSystemProductName.md)_ [v4.0] | Gets the computer's product or model name. |
| _[UserName](TPJComputerInfoUserName.md)_ | Gets the current user name. |

## Properties ##

_TPJComputerInfo_ defines no properties.

## Events ##

_TPJComputerInfo_ defines no events.