# Negative operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Negative(const F: TFraction): TFraction;
```

## Description

This operator overload enables the unary negative (negation) operator `-` to be applied to a [_TFraction_](./TFraction.md).

The operator returns a copy of the fraction with its sign changed.

### Example

```pascal
var
  F, FNeg: TFraction;
begin
  F := TFraction.Create(3, 4);
  FNeg := -F;
  Assert((FNeg.Numerator = -3) and (FNeg.Denominator = 4));
  F := TFraction.Create(-3, 4);
  FNeg := -F;
  Assert((FNeg.Numerator = 3) and (FNeg.Denominator = 4));
  F := TFraction.Create(0, 1);
  FNeg := -F;
  Assert((FNeg.Numerator = 0) and (FNeg.Denominator = 1));
end;
```

## See Also

* [_Positive_](./TFraction-Positive.md) operator overload.
