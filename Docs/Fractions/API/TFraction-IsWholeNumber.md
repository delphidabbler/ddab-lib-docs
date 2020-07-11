# IsWholeNumber method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function IsWholeNumber: Boolean;
```

## Description

The _IsWholeNumber_ method checks if a [_TFraction_](./TFraction.md) instance represent a whole number and returns True if so or False if not.

When a fraction is a whole number its numerator is an exact integer multiple of its denominator.

### Example

```pascal
var
  F: TFraction;
begin
  F := TFraction.Create(-2, 2);  // F = -2/2 = -1 - 0/2 = -1
  Assert(F.IsWholeNumber);
  F := TFraction.Create(12, 4);  // F = 12/4 = 3 + 0/4 = 3
  Assert(F.IsWholeNumber);
  F := TFraction.Create(7, 4);   // F = 7/4 = 1 + 3/4
  Assert(not F.IsWholeNumber);
  F := 42;
  Assert(F.IsWholeNumber);       // F = 42/1 = 42 + 0/1 = 42
  F := 0;
  Assert(F.IsWholeNumber);       // F = 0/1 = 0 + 0/1 = 0
end;
```

### Note

Another test for a whole number fraction is to check whether its [_FractionalPart_](./TFraction-FractionalPart.md) property is equal to 0. If this property is zero then the fraction is a whole number.

## See Also

* [_FractionalPart_](./TFraction-FractionalPart.md) property.
* [_IsProper_](./TFraction-IsProper.md) method.
