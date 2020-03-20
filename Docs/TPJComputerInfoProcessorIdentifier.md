# ProcessorIdentifier class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJComputerInfo](TPJComputerInfo.md)_

**Introduced:** v4.0

```pascal
class function ProcessorIdentifier: string;
```

## Description ##

Returns the identifier of the computer's processor.

On multi-processor systems the method returns the identifier of the 1st processor.

An example processor identifier is "`Intel64 Family 6 Model 58 Stepping 9`".

**See also**

* _[ProcessorName](TPJComputerInfoProcessorName.md)_
* _[ProcessorSpeedMHz](TPJComputerInfoProcessorSpeedMHz.md)_ 
