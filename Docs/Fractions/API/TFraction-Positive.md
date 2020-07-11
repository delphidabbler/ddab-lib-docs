# Positive operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Positive(const F: TFraction): TFraction;
```

## Description

This operator overload enables the unary positive (plus) operator `+` to be applied to a [_TFraction_](./TFraction.md).

The operator is a no-op. It returns an exact copy of the fraction.

### Example

```pascal
var
  F, FPos: TFraction;
begin
  F := TFraction.Create(3, 4);
  FPos := +F;
  Assert(
    (FPos.Numerator = F.Numerator)
    and (FPos.Denominator = F.Denominator));
end;
```

## See Also

* [_Negative_](./TFraction-Negative.md) operator overload
