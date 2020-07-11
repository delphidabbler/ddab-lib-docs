# LessThanOrEqual operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator LessThanOrEqual(const A, B: TFraction): Boolean;
```

## Description

This operator overload permits two [_TFraction_](./TFraction.md)s to be compared using the `<=` (less than or equal) operator.

One fraction is considered to be less than or equal to a second if the 1st cross product of the two fractions is less than or equal to their 2nd cross product. Here are two examples:

* `3/4` and `7/8`: The 1st cross product is `3 × 8 = 24` and the 2nd cross product is `4 × 7 = 28`. Since `24 < 28`, `3/4` <= `7/8`.
* `6/8` and `3/4`: The 1st cross product is `6 × 4 = 24` and the 2nd cross product is `8 × 3 = 24`. The cross products are equal, so `6/8 <= 3/4`.

A [_TFraction_](./TFraction.md) can also be compared to integer and floating point types using the `<=` operator. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to [_TFraction_](./TFraction.md) before performing the comparison.

### Example

```pascal
var
  F1, F2, F3, F4, F5: TFraction;
  D: Double;
  I: Integer;
begin
  F1 := TFraction.Create(1, 2);
  F2 := TFraction.Create(3, 4);
  F3 := TFraction.Create(6, 8);
  F4 := TFraction.Create(1, 1);
  F5 := TFraction.Create(15, 8);
  D := 0.75;
  I := 1;
  Assert(F1 <= F2);  // 1/2 < 3/4
  Assert(F2 <= F3);  // 3/4 = 6/8
  Assert(F1 <= D);   // 1/2 < 0.75
  Assert(F2 <= D);   // 3/4 = 0.75
  Assert(D <= F3);   // 0.76 = 6/8
  Assert(D <= F5);   // 0.75 < 15/8
  Assert(F1 <= I);   // 1/2 < 1
  Assert(F4 <= I);   // 1/1 = 1
  Assert(I <= F4);   // 1 = 1/1
  Assert(I <= F5);   // 1 < 15/8
end;
```

## See Also

* [_Equal_](./TFraction-Equal.md) operator overload
* [_NotEqual_](./TFraction-NotEqual.md) operator overload
* [_LessThan_](./TFraction-LessThan.md) operator overload
* [_GreaterThan_](./TFraction-GreaterThan.md) operator overload
* [_GreaterThanOrEqual_](./TFraction-GreaterThanOrEqual.md) operator overload
* [_Compare_](./TFraction-Compare.md) class method
* [_CompareTo_](./TFraction-CompareTo.md) method
