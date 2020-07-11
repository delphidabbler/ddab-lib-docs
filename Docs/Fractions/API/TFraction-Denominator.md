# TFraction Denominator property

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
property Denominator: Int64;
```

## Description

This property provides the denominator of a fraction encapsulated by a [_TFraction_](./TFraction.md).

The property is always strictly positive in the range `1..High(Int64)`.

### Example

```pascal
var
  F: TFraction;
begin
  F := TFraction.Create(2, 3);
  Assert(F.Denominator = 3);  // F = 2/3
  F := -F;
  Assert(F.Denominator = -3); // F = -2/3
  F := 0.75;
  Assert(F.Denominator = 4);  // F = 3/4
  F := 42;
  Assert(F.Denominator = 1);  // F = 42/1
end;
```

## See Also

* [_Numerator_](./TFraction-Numerator.md) property
* [_WholeNumberPart_](./TFraction-WholeNumberPart.md) property
* [_FractionalPart_](./TFraction-FractionalPart.md) property
