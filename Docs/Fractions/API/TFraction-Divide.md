# Divide operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Divide(const A, B: TFraction): TFraction;
```

## Description

This operator overload permits one [_TFraction_](./TFraction.md) to be divided by another using the `/` operator.

The result of the division is returned as a new [_TFraction_](./TFraction.md) instance, reduced to its lowest terms.

One of the operands may be either an integer or floating point value. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to a [_TFraction_](./TFraction.md) before performing the division.

The second operand must not be zero. In the case of a [_TFraction_](./TFraction.md) this means the [_Numerator_](./TFraction-Numerator.md) must not be zero.

### Example

```pascal
var
  F1, F2, FRes: TFraction;
begin
  // 2/3 / 5/6 = 2/3 * 6/5 = 12/15 = 4/5
  F1 := TFraction.Create(2, 3);
  F2 := TFraction.Create(5, 6);
  FRes := F1 / F2;
  Assert((FRes.Numerator = 4) and (FRes.Denominator = 5));
  // 5/8 / 3 = 5/8 * 1/3 = 5/24
  F1 := TFraction.Create(5, 8);
  FRes := F1 / 3;
  Assert((FRes.Numerator = 5) and (FRes.Denominator = 24));
  // 2.5 / 3/4 = 5/2 / 3/4 = 5/2 * 4/3 = 20/6 = 10/3
  Assert((FRes.Numerator = 10) and (FRes.Denominator = 3));
end;
```

## See Also

* [_Add_](./TFraction-Add.md) operator overload
* [_Subtract_](./TFraction-Subtract.md) operator overload
* [_Multiply_](./TFraction-Multiply.md) operator overload
* [_IntDivide_](./TFraction-IntDivide.md) operator overload
* [_Modulus_](./TFraction-Modulus.md) operator overload
* [_Numerator_](./TFraction-Numerator.md) property
* [_Denominator_](./TFraction-Denominator.md) property
