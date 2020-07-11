# LessThan operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator LessThan(const A, B: TFraction): Boolean;
```

## Description

This operator overload permits two [_TFraction_](./TFraction.md)s to be compared using the `<` (less than) operator.

One fraction is considered to be less than a second if the 1st cross product of the two fractions is less than the 2nd cross product. Take for example `3/4` and `7/8`. Their 1st cross product is `3 × 8 = 24` and their 2nd cross product is `4 × 7 = 28`. Since `24 < 28`, `3/4` is less than `7/8`.

A [_TFraction_](./TFraction.md) can also be compared to integer and floating point types using the `<` operator. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to [_TFraction_](./TFraction.md) before performing the comparison.

### Example

```pascal
var
  F1, F2, F3: TFraction;
  D: Double;
  I: Integer;
begin
  F1 := TFraction.Create(1, 2);
  F2 := TFraction.Create(3, 4);
  F3 := TFraction.Create(5, 4);
  D := 0.6;
  I := 1;
  Assert(F1 < F2);
  Assert(F2 < F3);
  Assert(F1 < F3);
  Assert(F1 < D);
  Assert(D < F2);
  Assert(D < F3);
  Assert(F1 < I);
  Assert(F2 < I);
  Assert(I < F3);
end;
```

## See Also

* [_Equal_](./TFraction-Equal.md) operator overload
* [_NotEqual_](./TFraction-NotEqual.md) operator overload
* [_LessThanOrEqual_](./TFraction-LessThanOrEqual.md) operator overload
* [_GreaterThan_](./TFraction-GreaterThan.md) operator overload
* [_GreaterThanOrEqual_](./TFraction-GreaterThanOrEqual.md) operator overload
* [_Compare_](./TFraction-Compare.md) class method
* [_CompareTo_](./TFraction-CompareTo.md) method
