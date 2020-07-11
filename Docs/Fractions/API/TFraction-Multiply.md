# Multiply operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Multiply(const A, B: TFraction): TFraction;
```

## Description

This operator overload permits two [_TFraction_](./TFraction.md)s to be multiplied together using the `*` operator.

The result of the multiplication is returned as a new [_TFraction_](./TFraction.md) instance, reduced to its lowest terms.

One of the operands may be either an integer or floating point value. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to a [_TFraction_](./TFraction.md) before performing the multiplication.

### Example

```pascal
var
  F1, F2, FRes: TFraction;
begin
  // 3/4 * 2/3 = 6/12 = 1/2
  F1 := TFraction.Create(3, 4);
  F2 := TFraction.Create(2, 3);
  FRes := F1 * F2;
  Assert((FRes.Numerator = 1) and (FRes.Denominator = 2));
  // 2 * 5/6 = 2/1 * 5/6 = 10/6 = 5/3
  F2 := TFraction.Create(5, 6);
  FRes := 2 * F2;
  Assert((FRes.Numerator = 5) and (FRes.Denominator = 3));
  // 5/6 * 2.5 = 5/6 * 5/2 = 25/12
  F1 := TFraction.Create(5, 6);
  FRes := F1 * 2.5;
  Assert((FRes.Numerator = 25) and (FRes.Denominator = 12));
end;
```

## See Also

* [_Add_](./TFraction-Add.md) operator overload
* [_Subtract_](./TFraction-Subtract.md) operator overload
* [_Divide_](./TFraction-Divide.md) operator overload
* [_IntDivide_](./TFraction-IntDivide.md) operator overload
* [_Modulus_](./TFraction-Modulus.md) operator overload
* [_Numerator_](./TFraction-Numerator.md) property
* [_Denominator_](./TFraction-Denominator.md) property
