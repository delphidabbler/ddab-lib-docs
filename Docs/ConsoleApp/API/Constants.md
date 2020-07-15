# Constants

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

The following constants are declared in the library.

* [_cOneSecInMS_](#conesecinms)
* [_cOneMinInMS_](#conemininms)
* [_cDefTimeSlice_](#cdeftimeslice)
* [_cDefMaxExecTime_](#cdefmaxexectime)
* [_cAppErrorMask_](#capperrormask)
* [_cAppErrorTimeOut_](#capperrortimeout)
* [_cAppErrorTerminated_](#capperrorterminated)

## cOneSecInMS

```pascal
const cOneSecInMS = 1000;
```

Number of milliseconds in a second. This can be a useful value when setting properties such as [_TPJCustomConsoleApp.MaxExecTime_](./TPJCustomConsoleApp-MaxExecTime.md) and [_TPJCustomConsoleApp.TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md).

## cOneMinInMS

```pascal
const cOneMinInMS = 60 * cOneSecInMS;
```

Number of milliseconds in a minute. This can be useful when setting the [_TPJCustomConsoleApp.MaxExecTime_](./TPJCustomConsoleApp-MaxExecTime.md) property.

## cDefTimeSlice

***Introduced:*** v1.0

```pascal
cDefTimeSlice = 50;
```

Default value of the [_TPJCustomConsoleApp.TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md) property.

There should rarely be a need to use this value directly.

## cDefMaxExecTime

```pascal
const cDefMaxExecTime = cOneMinInMS;
```

Default value of the [_TPJCustomConsoleApp.MaxExecTime_](./TPJCustomConsoleApp-MaxExecTime.md) property.

There should rarely be a need to use this value directly.

## cAppErrorMask

```pascal
const cAppErrorMask = 1 shl 29;
```

Mask that is ORd with application error codes. This sets bit 29 in accordance with Windows requirements. Application error codes are tested for by ANDing them with this constant.

The [_IsApplicationError_](./Routines.md#isapplicationerror) routine is provided to perform this test so there should be no need to use _cAppErrorMask_ directly.

## cAppErrorTimeOut

```pascal
const cAppErrorTimeOut = 1 or cAppErrorMask;
```

Error code used to report that an application has timed out. c.f. the [_TPJCustomConsoleApp.ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) property.

## cAppErrorTerminated

```pascal
const cAppErrorTerminated = 2 or cAppErrorMask;
```

Error code used to report that an application has been terminated. c.f. the [_TPJCustomConsoleApp.ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) property and [_TPJCustomConsoleApp.Terminate_](./TPJCustomConsoleApp-Terminate.md) method.
