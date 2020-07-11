# Equal operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Equal(const A, B: TFraction): Boolean;
```

## Description

This operator overload permits [_TFraction_](./TFraction.md)s to be tested for equality using the `=` operator.

Two fractions are considered equal if they can be simplified to the same fraction. For example `1/2 = 2/4`. Formally, two fractions are equal if their 1st and 2nd cross products are equal.

A [_TFraction_](./TFraction.md) can also be compared to integer and floating point types using the `=` operator. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to [_TFraction_](./TFraction.md) before performing the comparison.

### Example

```pascal
var
  F1, F2, F3, F4: TFraction;
  D: Double;
  I: Integer;
begin
  F1 := TFraction.Create(1, 4);
  F2 := TFraction.Create(1, 4);
  F3 := TFraction.Create(2, 8);
  F4 := TFraction.Create(3, 1);
  D := 0.25;
  I := 3;
  Assert(F1 = F2);
  Assert(F1 = F3);
  Assert(D = F1);
  Assert(F1 = D);
  Assert(I = F4);
  Assert(F4 = I);
end;
```

## See Also

* [_NotEqual_](./TFraction-NotEqual.md) operator overload
* [_LessThan_](./TFraction-LessThan.md) operator overload
* [_LessThanOrEqual_](./TFraction-LessThanOrEqual.md) operator overload
* [_GreaterThan_](./TFraction-GreaterThan.md) operator overload
* [_GreaterThanOrEqual_](./TFraction-GreaterThanOrEqual.md) operator overload
* [_Compare_](./TFraction-Compare.md) class method
* [_CompareTo_](./TFraction-CompareTo.md) method
