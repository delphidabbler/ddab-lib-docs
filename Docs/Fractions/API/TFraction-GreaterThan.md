# GreaterThan operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator GreaterThan(const A, B: TFraction): Boolean;
```

## Description

This operator overload permits two [_TFraction_](./TFraction.md)s to be compared using the `>` (greater than) operator.

One fraction is considered to be greater than a second if the 1st cross product of the two fractions is greater than the 2nd cross product. Take for example `7/8` and `3/4`. Their 1st cross product is `7 × 4 = 28` and their 2nd cross product is `8 × 3 = 24`. Since `28 > 24`, `7/8` is greater than `3/4`.

A [_TFraction_](./TFraction.md) can also be compared to integer and floating point types using the `>` operator. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to [_TFraction_](./TFraction.md) before performing the comparison.

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
  Assert(F2 > F1);
  Assert(F3 > F2);
  Assert(F3 > F1);
  Assert(D > F1);
  Assert(F2 > D);
  Assert(F3 > D);
  Assert(I > F1);
  Assert(I > F2);
  Assert(F3 > I);
end;
```

## See Also

* [_Equal_](./TFraction-Equal.md) operator overload
* [_NotEqual_](./TFraction-NotEqual.md) operator overload
* [_LessThan_](./TFraction-LessThan.md) operator overload
* [_LessThanOrEqual_](./TFraction-LessThanOrEqual.md) operator overload
* [_GreaterThanOrEqual_](./TFraction-GreaterThanOrEqual.md) operator overload
* [_Compare_](./TFraction-Compare.md) class method
* [_CompareTo_](./TFraction-CompareTo.md) method
