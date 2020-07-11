# Numerator property

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
property Numerator: Int64;
```

## Description

This property provides the numerator of a fraction encapsulated by a [_TFraction_](./TFraction.md).

The property can be any 64 bit integer value.

The sign of the numerator is the same as the sign of the fraction.

### Example

```pascal
var
  F: TFraction;
begin
  F := TFraction.Create(2, 3);
  Assert(F.Numerator = 2);   // F = 2/3
  F := -F;
  Assert(F.Numerator = -2);  // F = -2/3
  F := 0.75;
  Assert(F.Numerator = 3);   // F = 3/4
  F := 42;
  Assert(F.Numerator = 42);  // F = 42/1
end;
```

## See Also

* [_Denominator_](./TFraction-Denominator.md) property
* [_WholeNumberPart_](./TFraction-WholeNumberPart.md) property
* [_FractionalPart_](./TFraction-FractionalPart.md) property
