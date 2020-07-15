# Reciprocal method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function Reciprocal: TFraction;
```

## Description

This method returns the reciprocal of the fraction. The fraction must not be zero, i.e. it must have a non-zero numerator.

The reciprocal of fraction `X/Y` is `Y/X`, where `X<>0`.

### Note

Because the reciprocal of any non-zero number `N` is defined as `1/N`, applying _Reciprocal_ to a fraction is the same as dividing the fraction into 1. I.e. if _F_ is any [_TFraction_](./TFraction.md) instance with a non-zero numerator,

```text
F.Reciprocal = 1/F;
```

### Example

```pascal
var
  F, G, H: TFraction;
begin
  F := TFraction.Create(5, 12);
  G := F.Reciprocal;
  H := 1 / F;  // see Note
  Assert(G = H);
  Assert((G.Numerator = F.Denominator) and (G.Denominator = F.Numerator));
end;
```

## See Also

* [_Divide_](./TFraction-Divide.md) operator overload
