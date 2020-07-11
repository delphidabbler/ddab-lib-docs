# NotEqual operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator NotEqual(const A, B: TFraction): Boolean;
```

## Description

This operator overload permits [_TFraction_](./TFraction.md)s to be tested for inequality using the `<>` operator.

Two fractions are considered not equal unless they can be simplified to the same fraction. Formally, two fractions are unequal if their 1st and 2nd cross products are different. Take for example `3/4` and `7/8`. Their 1st cross product is `3 × 8 = 24` and their 2nd cross product is `4 × 7 = 28`. Since `24 <> 28`, the fractions are not equal.

A [_TFraction_](./TFraction.md) can also be compared to integer and floating point types using the `<>` operator. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to [_TFraction_](./TFraction.md) before performing the comparison.

### Example

```pascal
var
  F1, F2: TFraction;
  D: Double;
  I: Integer;
begin
  F1 := TFraction.Create(3, 4);
  F2 := TFraction.Create(3, 8);
  D := 0.25;
  I := 3;
  Assert(F1 <> F2);
  Assert(F2 <> F1);
  Assert(D <> F2);
  Assert(F1 <> D);
  Assert(I <> F2);
  Assert(F1 <> I);
end;
```

## See Also

* [_Equal_](./TFraction-Equal.md) operator overload
* [_LessThan_](./TFraction-LessThan.md) operator overload
* [_LessThanOrEqual_](./TFraction-LessThanOrEqual.md) operator overload
* [_GreaterThan_](./TFraction-GreaterThan.md) operator overload
* [_GreaterThanOrEqual_](./TFraction-GreaterThanOrEqual.md) operator overload
* [_Compare_](./TFraction-Compare.md) class method
* [_CompareTo_](./TFraction-CompareTo.md) method
