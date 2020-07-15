# FractionalPart property

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
property FractionalPart: TFraction;
```

## Description

This property provides the fractional part of a [_TFraction_](./TFraction.md) when viewed as a mixed fraction. The fractional part is always a proper fraction, i.e. its absolute value is less than 1.

For any [_TFraction_](./TFraction.md) it's [_WholeNumberPart_](./TFraction-WholeNumberPart.md) plus its _FractionalPart_ is equal to the original fraction. I.e. for [_TFraction_](./TFraction.md) _F_

```text
F = F.WholeNumberPart + F.FractionalPart;
```

### Example

```pascal
var
  F: TFraction;
begin
  F := TFraction.Create(21, 4);
  Assert((F.FractionalPart.Numerator = 1)      // 21/4 = 5 + 1/4
    and (F.FractionalPart.Denominator = 4));
  F := TFraction.Create(-21, 4);
  Assert((F.FractionalPart.Numerator = -1)     // -21/4 = -5 + -1/4
    and (F.FractionalPart.Denominator = 4));
  F := TFraction.Create(5, 11);
  Assert((F.FractionalPart.Numerator = 5)      // 5/11 = 0 + 5/11
    and (F.FractionalPart.Denominator = 11));
  F := TFraction.Create(60, 6);
  Assert((F.FractionalPart.Numerator = 0)      // 60/6 = 6 + 0/6
    and (F.FractionalPart.Denominator = 6));
  F := -7;
  Assert((F.FractionalPart.Numerator = 0)      // // -7/1 = -7 + 0/1
    and (F.FractionalPart.Denominator = 1));
end;
```

## See Also

* [_Numerator_](./TFraction-Numerator.md) property
* [_Denominator_](./TFraction-Denominator.md) property
* [_WholeNumberPart_](./TFraction-WholeNumberPart.md) property
