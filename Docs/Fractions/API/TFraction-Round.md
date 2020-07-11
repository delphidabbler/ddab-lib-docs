# Round operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Round(const F: TFraction): Int64;
```

## Description

The operator overload enables the `Round` "operator" or compiler function to operate on a [_TFraction_](./TFraction.md). The operator rounds the fraction to the nearest whole number value.

### Example

```pascal
var
  F: TFraction;
begin
  F := TFraction.Create(17, 3);
  Assert(Trunc(F) = 6);
  F := TFraction.Create(-17, 3);
  Assert(Trunc(F) = -6);
  F := TFraction.Create(-58, 7);
  Assert(Trunc(F) = -8);
  F := TFraction.Create(3, 1);
  Assert(Trunc(F) = 3);
  F := TFraction.Create(-3, 1);
  Assert(Trunc(F) = -3);
  F := TFraction.Create(0, 1);
  Assert(Trunc(F) = 0);
end;
```

## See Also

* [_Trunc_](./TFraction-Trunc.md) operator
