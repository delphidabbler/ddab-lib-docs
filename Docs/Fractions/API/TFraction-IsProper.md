# IsProper method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function IsProper: Boolean;
```

## Description

The _IsProper_ method checks if a [_TFraction_](./TFraction.md) instance is a proper fraction and returns True if so or False if not.

A proper fraction is one whose absolute value is less than 1, i.e. the absolute value of its numerator is less than its denominator.

### Example

```pascal
var
  F: TFraction;
begin
  F := TFraction.Create(-2, 3);
  Assert(F.IsProper);
  F := TFraction.Create(3, 4);
  Assert(F.IsProper);
  F := TFraction.Create(7, 4);
  Assert(not F.IsProper);
end;
```

### Note

Another test for a proper fraction is to check whether its [_WholeNumberPart_](./TFraction-WholeNumberPart.md) property is 0. If the property is 0 then the fraction is proper, otherwise it is not.

## See Also

* [_WholeNumberPart_](./TFraction-WholeNumberPart.md) property.
* [_IsWholeNumber_](./TFraction-IsWholeNumber.md) method.
