# Implicit operator overloads

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator Implicit(const I: Integer): TFraction;
class operator Implicit(const F: TFraction): Extended;
class operator Implicit(const E: Extended): TFraction;
```

## Description

[_TFraction_](./TFraction.md) defines three implicit casts:

* [Integer to TFraction](#integer-to-tfraction)
* [TFraction to Extended](#tfraction-to-extended)
* [Extended to TFraction](#extended-to-tfraction)

### Integer to TFraction

```pascal
class operator Implicit(const I: Integer): TFraction;
```

This cast enables any integer value to be cast as a [_TFraction_](./TFraction.md) that represents a whole number.

The cast works with any signed or unsigned integer type up to 32 bits wide, but not 64 bit integer types.

Both implicit and explicit casting are supported.

The [_TFraction_](./TFraction.md) record created when an integer is cast to it has its [_Numerator_](./TFraction-Numerator.md) property set to the same value as the integer. The [_Denominator_](./TFraction-Denominator.md) property is always set to 1.

A consequence of this cast is that integer values can be assigned, or explicitly cast to a [_TFraction_](./TFraction.md). Integers can also be passed as parameters where a [_TFraction_](./TFraction.md) is expected, including as elements of dynamic arrays of [_TFraction_](./TFraction.md).

#### Integer to TFraction Example

```pascal
var
  F: TFraction;
  I: Integer;
  N, D: Int64;
begin
  I := 42;
  F := I;   // implicit cast of integer variable
  Assert((F.Numerator = 42) and (F.Denominator = 1));
  F := -56; // implicit cast of integer literal
  Assert((F.Numerator = -56) and (F.Denominator = 1));
  N := TFraction(I).Numerator;    // explicit casts
  D := TFraction(I).Denominator;
  Assert((N = I) and (D = 1));
end;
```

#### Integer to TFraction Note

The reverse operation is not defined, so that a [_TFraction_](./TFraction.md) instance can't be cast to an Integer. This is because information would most probably be lost.

To convert a [_TFraction_](./TFraction.md) to an integer use the [_Trunc_](./TFraction-Trunc.md) or [_Round_](./TFraction-Round.md) operators.

### TFraction to Extended

```pascal
class operator Implicit(const F: TFraction): Extended;
```

This cast enables a [_TFraction_](./TFraction.md) instance to be converted to its floating point number representation.

Although defined for the _Extended_ floating point type, the cast works equally well for the _Single_, _Double_ and _Extended_ types.

Both implicit and explicit casting is supported.

A consequence of this cast is that [_TFraction_](./TFraction.md) instances can be passed as parameters to methods whenever a floating point input parameter is expected.

#### TFraction to Extended Example

```pascal
var
  F: TFraction;
  E: Extended;
  D: Double;
begin
  F := TFraction.Create(2, 8);  // 2/8 or 1/4
  E := F;
  Assert(Math.SameValue(E, 0.25));
  D := Double(F); // same effect as D := F;
  Assert(Math.SameValue(D, 0.25));
  Assert(Math.SameValue(F, 0.25)); // F acts as floating point parameter
```

### Extended to TFraction

```pascal
class operator Implicit(const E: Extended): TFraction;
```

This cast enables a floating point value to be cast to a [_TFraction_](./TFraction.md).

Although defined for the _Extended_ floating point type, the cast works equally well for the _Single_, _Double_ and _Extended_ types.

Both implicit and explicit casting is supported.

A consequence of this cast is that, subject to the restrictions below, floating point values can be assigned, or explicitly cast to a [_TFraction_](./TFraction.md). Floats can also be passed as parameters where a [_TFraction_](./TFraction.md) is expected, including as elements of dynamic arrays of [_TFraction_](./TFraction.md).

#### Extended to TFraction Restrictions

1. The absolute value of floating point value being cast must be in the range 1.0E-19 to 1.0E+19, or be 0.
2. Conversions are accurate to 5 decimal places. Any further decimal places are ignored.

#### Extended to TFraction Example

```pascal
var
  E: Extended;
  D: Double;
  F: TFraction;
begin
  E := -4 / 7;
  F := E;             // variable assignment
  Assert((F.Numerator = -4) and (F.Denominator = 7));
  D := 0.75
  F := TFraction(D);  // explicit cast
  Assert((F.Numerator = 3) and (F.Denominator = 4));
  F := 1.07407407;    // floating point literal assignment
  Assert((F.Numerator = 29) and (F.Denominator = 27));
end;
```

## See Also

* [Constructor](./TFraction-Create.md)
