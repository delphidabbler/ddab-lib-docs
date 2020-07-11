# Abs class method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class function Abs(const F: TFraction): TFraction; static;
```

## Description

Returns the absolute value of the given fraction _F_.

The returned fraction is not simplified.

### Example

```pascal
var
  F, G: TFraction;
begin
  F := TFraction.Create(3, 4);
  G := TFraction.Abs(F);
  Assert(G = +F);
  F := TFraction.Create(-7, 8);
  G := TFraction.Abs(F);
  Assert(G = -F);
end;
```

## See Also

* [_Sign_](./TFraction-Sign.md) method
* [_Positive_](./TFraction-Positive.md) operator overload
* [_Negative_](./TFraction-Negative.md) operator overload
