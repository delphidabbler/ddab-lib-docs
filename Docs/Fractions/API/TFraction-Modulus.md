# Modulus operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Modulus(const A, B: TFraction): TFraction;
```

## Description

This operator overload permits the `mod` operator to be applied to [_TFraction_](./TFraction.md) operands. It calculates the remainder after dividing _A_ by _B_.

The result of the operation is returned as a new [_TFraction_](./TFraction.md) instance, reduced to its lowest terms.

One of the operands may be either an integer or floating point value. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to a [_TFraction_](./TFraction.md) before performing the modulus operation.

The second operand must not be zero. In the case of a [_TFraction_](./TFraction.md) this means the [_Numerator_](./TFraction-Numerator.md) must not be zero.

### Example

```pascal
var
  F1, F2, FRes: TFraction;
begin
  // 7/8 mod 1/3 = 7/8 - 2 * 1/3 = 7/8 - 2/3 = 21/24-16/24 = 5/24
  F1 := TFraction.Create(7, 8);
  F2 := TFraction.Create(1, 3);
  FRes := F1 mod F2;
  Assert(FRes.Numerator = 5) and (FRes.Denominator = 24));

  // 4/3 mod 2/3 = 4/3 - 2 * 2/3 = 4/3 - 4/3 = 0
  F1 := TFraction.Create(4, 3);
  F2 := TFraction.Create(2, 3);
  FRes := F1 mod F2;
  Assert(FRes.Numerator = 0) and (FRes.Denominator = 1));

  // 32/5 mod 3 = 32/5 - 2 * 3 = 32/5 - 6/1 = 32/5 - 30/5 = 2/5
  F1 := TFraction.Create(32, 5);
  FRes := F1 mod 3;
  Assert(FRes.Numerator = 2) and (FRes.Denominator = 5));

  // 5 mod 2/3 = 5 - 7 * 2/3 = 5/1 - 14/3 = 15/3 - 14/3 = 1/3
  F2 := TFraction.Create(2, 3);
  FRes := 5 mod F2;
  Assert(FRes.Numerator = 1) and (FRes.Denominator = 3));

  // 10 7/8 mod 3.75 = 87/8 mod 15/4 = 87/8 mod 30/8 = 87/8 - 60/8 = 27/8
  F1 := TFraction.Create(87, 8);
  FRes := F1 mod 3.75;
  Assert(FRes.Numerator = 27) and (FRes.Denominator = 8));
end;
```

## See Also

* [_Add_](./TFraction-Add.md) operator overload
* [_Subtract_](./TFraction-Subtract.md) operator overload
* [_Multiply_](./TFraction-Multiply.md) operator overload
* [_Divide_](./TFraction-Divide.md) operator overload
* [_IntDivide_](./TFraction-IntDivide.md) operator overload
* [_Numerator_](./TFraction-Numerator.md) property
* [_Denominator_](./TFraction-Denominator.md) property
