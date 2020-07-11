# Subtract operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Subtract(const A, B: TFraction): TFraction;
```

## Description

This operator overload permits one [_TFraction_](./TFraction.md) to be subtracted from another using the `-` operator.

The result of the subtraction is returned as a new [_TFraction_](./TFraction.md) instance, reduced to its lowest terms.

One of the operands may be either an integer or floating point value. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to a [_TFraction_](./TFraction.md) before performing the subtraction.

### Example

```pascal
var
  F1, F2, FRes: TFraction;
begin
  F1 := TFraction.Create(2, 3);
  F2 := TFraction.Create(5, 6);
  FRes := F1 - F2;  // 2/3 - 5/6 = 4/6 - 5/6 = -1/6
  Assert((FRes.Numerator = -1) and (FRes.Denominator = 6));
  F2 := TFraction.Create(-5, 6);
  FRes := 1 - F2;   // 1 - -5/6 = 6/6 - -5/6 = 11/6
  Assert((FRes.Numerator = 11) and (FRes.Denominator = 6));
  F1 := TFraction.Create(3, 4);
  FRes := F1 - 0.25;  // 3/4 - 0.25 = 3/4 - 1/4 = 2/4 = 1/2
  Assert((FRes.Numerator = 1) and (FRes.Denominator = 2));
end;
```

## See Also

* [_Add_](./TFraction-Add.md) operator overload
* [_Multiply_](./TFraction-Multiply.md) operator overload
* [_Divide_](./TFraction-Divide.md) operator overload
* [_IntDivide_](./TFraction-IntDivide.md) operator overload
* [_Modulus_](./TFraction-Modulus.md) operator overload
* [_Numerator_](./TFraction-Numerator.md) property
* [_Denominator_](./TFraction-Denominator.md) property
