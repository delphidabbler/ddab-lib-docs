# Add operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Add(const A, B: TFraction): TFraction;
```

## Description

This operator overload permits two [_TFraction_](./TFraction.md)s to be added together using the `+` operator.

The result of the addition is returned as a new [_TFraction_](./TFraction.md) instance, reduced to its lowest terms.

One of the operands may be either an integer or floating point value. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to a [_TFraction_](./TFraction.md) before performing the addition.

### Example

```pascal
var
  A, B, C, Res: TFraction;
begin
  A := TFraction.Create(2, 3);
  B := TFraction.Create(5, 6);
  C := TFraction.Create(4, 6);
  Res := A + B;  // 2/3 + 5/6 = 4/6 + 5/6 = 9/6 = 3/2
  Assert((Res.Numerator = 3) and (Res.Denominator = 2));
  Res := 2 + B;  // 2 + 5/6 = 12/6 + 5/6 = 17/6
  Assert((Res.Numerator = 17) and (Res.Denominator = 6));
  Res := 1.5 + C; // 1.5 + 4/6 = 3/2 + 4/6 = 9/6 + 4/6 = 13/6
  Assert((Res.Numerator = 13) and (Res.Denominator = 6));
end;
```

## See Also

* [_Subtract_](./TFraction-Subtract.md) operator overload
* [_Multiply_](./TFraction-Multiply.md) operator overload
* [_Divide_](./TFraction-Divide.md) operator overload
* [_IntDivide_](./TFraction-IntDivide.md) operator overload
* [_Modulus_](./TFraction-Modulus.md) operator overload
* [_Numerator_](./TFraction-Numerator.md) property
* [_Denominator_](./TFraction-Denominator.md) property
