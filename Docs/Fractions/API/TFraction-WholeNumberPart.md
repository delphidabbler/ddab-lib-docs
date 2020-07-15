# WholeNumberPart property

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
property WholeNumberPart: Int64;
```

## Description

This property provides the whole number part of a [_TFraction_](./TFraction.md) when considered as a mixed fraction.

For any [_TFraction_](./TFraction.md) it's _WholeNumberPart_ plus its [_FractionalPart_](./TFraction-FractionalPart.md) is equal to the original fraction. I.e. for [_TFraction_](./TFraction.md) _F_

```text
F = F.WholeNumberPart + F.FractionalPart;
```

### Example

```pascal
var
  F: TFraction;
begin
  F := TFraction.Create(21, 4);
  Assert(F.WholeNumberPart = 5);  // 21/4 = 5 + 1/4
  F := TFraction.Create(-21, 4);
  Assert(F.WholeNumberPart = -5); // -21/4 = -5 - 1/4
  F := TFraction.Create(5, 11);
  Assert(F.WholeNumberPart = 0);  // 5/11 = 0 + 5/11
  F := TFraction.Create(60, 6);
  Assert(F.WholeNumberPart = 10); // 60/6 = 6 + 0/6
  F := -7;
  Assert(F.WholeNumberPart = -7); // -7/1 = -7 + 0/1
end;
```

## See Also

* [_Numerator_](./TFraction-Numerator.md) property
* [_Denominator_](./TFraction-Denominator.md) property
* [_FractionalPart_](./TFraction-FractionalPart.md) property
