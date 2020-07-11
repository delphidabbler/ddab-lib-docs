# Power class method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class function Power(const F: TFraction; Exponent: ShortInt): TFraction; static;
```

## Description

Returns the given fraction _F_ raised to the power of integer _Exponent_.

_Exponent_ can be positive, zero or negative. When _Exponent_ is negative the reciprocal of _F_ is raised to the power of the absolute value of _Exponent_. This is because, for any number `n`, `n^-x = 1/(N^x)`.

If _F_ is zero, _Exponent_ must be non-negative.

The resulting fraction is simplified.

### Examples

Here's a simple function that squares the given fraction.

```pascal
function Square(const F: TFraction): TFraction;
begin
  Result := TFraction.Power(F, 2);
end;
```

And here is some code that write out all the integer powers of 1/2 from -32 to +32:

```pascal
var
  F, G: TFraction;
  N: ShortInt;
begin
  F := TFraction.Create(1, 2);  // 1/2
  for N := -32 to 32 do
  begin
    G := TFraction.Power(F, N);
    WriteLn(
      Format(
        '1/2^%d = %d/%d', [N, G.Numerator, G.Denominator]
      )
    );
  end;
end;
```

## See Also

* [_Multiply_](./TFraction-Multiply.md) operator overload
* [_Reciprocal_](./TFraction-Reciprocal.md) method
