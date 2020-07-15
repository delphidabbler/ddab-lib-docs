# Version Information Routines

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

These functions are provided mainly for users of Delphi 2005 and earlier who don't have the extended functionality of [_TPJVersionNumber_](./TPJVersionNumber.md). The functions seek to replicate that functionality.

## VerNumToStr

***Introduced:*** v3.3

```pascal
function VerNumToStr(const Ver: TPJVersionNumber): string;
```

### VerNumToStr description

Converts the given [_TPJVersionNumber_](TPJVersionNumber.md) record into a dotted quad string and returns it.

### VerNumToStr example

If the following code is executed the string variable S will have the value `'2.5.8.3'`.

```pascal
var
  S: string;
  VN: TPJVersionNumber;
begin
  VN.V1 := 2;
  VN.V2 := 5;
  VN.V3 := 8;
  VN.V4 := 3;
  S := VerNumToStr(VN);
  // ...
end;
```

### VerNumToStr remarks

Users of Delphi 2006 and later can simply assign a [_TPJVersionNumber_](TPJVersionNumber.md) record to a string to get exactly the same effect. There is never any need to call _VerNumToStr_.

## CompareVerNums

***Introduced:*** v3.3

```pascal
function CompareVerNums(const Ver1, Ver2: TPJVersionNumber): Integer;
```

### CompareVerNums description

Compares two TPJVersionNumber records. Return values are:

* `0` if `Ver1` and `Ver2` are the same
* `<0` if `Ver1` is less than `Ver2`
* `>0` if `Ver1` is greater than `Ver2`

### CompareVerNums remarks

Users of Delphi 2006 should rarely, if ever, need to use this function. Two version number records can be directly compared using the normal `=`, `<>`, `<`, `<=`, `>` and `>=` operators.
