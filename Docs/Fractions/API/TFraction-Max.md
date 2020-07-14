# Max class methods

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class function Max(const A, B: TFraction): TFraction; overload; static;
class function Max(const FA: array of TFraction): TFraction; overload; static;
```

## Description

These overloaded methods find and return the largest of a series of fractions.

The first overload returns the largest of the two given fractions, _A_ and _B_.

The second method returns the largest fraction in the given array of fractions, _FA_. This array must have at least one element.

### Example

This example uses the array overload of _Max_ along with the associated [_Min_](./TFraction-Min.md) method to find the smallest range that contains all fractions in a given array.

```pascal
type
  TFractionRange = record
    Lo, Hi: TFraction;
  end;

function FindRange(const A: array of TFraction): TFRactionRange;
begin
  Result.Lo := TFraction.Min(A);
  Result.Hi := TFraction.Max(A);
end;
```

## See Also

* [_Min_](./TFraction-Min.md) class method
