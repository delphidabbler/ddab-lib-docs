# Simplify methods

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function Simplify(const CommonFactor: Int64): TFraction; overload;
function Simplify: TFraction; overload;
```

## Description

These overloaded methods are used to simplify or reduce the fraction instance to which they relate. The result is returned as a new [_TFraction_](./TFraction.md) instance.

If _CommonFactor_ is specified it the fraction is reduced by the value of this parameter. _CommonFactor_ must be non zero and be a valid common factor of the fraction. Reducing by a negative common factor has the same effect as the equivalent positive value.

You can check if a value is a valid common factor using the [_HasCommonFactor_](./TFraction-HasCommonFactor.md) method.

When _CommonFactor_ is omitted then the fraction is reduced to its lowest terms. In this case the common factor is the greatest common divisor of the numerator and denominator.

The original fraction and its simplification are equivalent.

### Example

```pascal
var
  F, G: TFraction;
begin
  F := TFraction.Create(24, 32);
  G := F.Simplify(2);
  Assert((G.Numerator = 12) and (G.Denominator = 16));
  Assert(F = G);  // fraction and simplification are equivalent

  F := TFraction.Create(-24, 32);
  G := F.Simplify(-2);
  Assert((G.Numerator = -12) and (G.Denominator = 16));
  Assert(F = G);

  F := TFraction.Create(12, 15);
  G := F.Simplify; // GCD = 3
  Assert((G.Numerator = 4) and (G.Denominator = 5));
  Assert(F = G);

  F := TFraction.Create(11, 12);
  G := F.Simplify; // already in lowest terms (GCD = 1)
  Assert((G.Numerator = 11) and (G.Denominator = 12));
  Assert(F = G);
end;
```

## See Also

* [_Convert_](./TFraction-Convert.md) method
* [_HasCommonFactor_](./TFraction-HasCommonFactor.md) method
