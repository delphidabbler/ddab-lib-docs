#summary TPJComputerInfo class description
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= TPJComputerInfo =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

This is a static class that provides information about the host computer. The class' functionality is all exposed via its static methods. Because it is static the class does not need to be instantiated before use.

== Methods ==

|| *Method* || *Description* ||
|| _[TPJComputerInfoBiosVendor BiosVendor]_ [v4.0] || Gets the name of the computer's BIOS vendor. ||
|| _[TPJComputerInfoBootMode BootMode]_ [v3.1] || Determines the operating system mode into which the the computer was booted. ||
|| _[TPJComputerInfoComputerName ComputerName]_ || Gets the computer's name. ||
|| _[TPJComputerInfoIs64Bit Is64Bit]_ || Checks if processor is 64 bit. ||
|| _[TPJComputerInfoIsAdmin IsAdmin]_ [v4.0] || Checks if the current user has administrator privileges. ||
|| _[TPJComputerInfoIsNetworkPresent IsNetworkPresent]_ [v3.1] || Checks if a network is present. ||
|| _[TPJComputerInfoIsUACActive IsUACActive]_ [v4.0] || Checks if UAC is active on the computer. ||
|| _[TPJComputerInfoMACAddress MACAddress]_ || Gets the address of the first network card in the computer. ||
|| _[TPJComputerInfoProcessor Processor]_ || Gets the kind of processor used in the computer. ||
|| _[TPJComputerInfoProcessorCount ProcessorCount]_ || Gets the number of processors in the computer. ||
|| _[TPJComputerInfoProcessorIdentifier ProcessorIdentifier]_ [v4.0] || Gets the identifier of the computer's processor. ||
|| _[TPJComputerInfoProcessorName ProcessorName]_ [v4.0] || Gets the name of the computer's processor. ||
|| _[TPJComputerInfoSystemManufacturer SystemManufacturer]_ [v4.0] || Gets the name of the computer's manufacturer. ||
|| _[TPJComputerInfoSystemProductName SystemProductName]_ [v4.0] || Gets the computer's product or model name. || 
|| _[TPJComputerInfoUserName UserName]_ || Gets the current user name. ||

== Properties ==

_TPJComputerInfo_ defines no properties.

== Events ==

_TPJComputerInfo_ defines no events.