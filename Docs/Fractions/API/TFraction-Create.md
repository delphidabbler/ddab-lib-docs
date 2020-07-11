# Create constructor

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
constructor Create(const Numerator, Denominator: Int64);
```

## Description

This constructor creates a [_TFraction_](./TFraction.md) with the given numerator and denominator.

The _Numerator_ and _Denominator_ parameters are "normalised" before being assigned to the fraction's [_Numerator_](./TFraction-Numerator.md) and [_Denominator_](./TFraction-Denominator.md) properties.

"Normalisation" ensures that _Numerator_ always takes the sign of the fraction and _Denominator_ is always a positive integer. This means that if a negative value is passed to _Denominator_ then the signs of both _Numerator_ and _Denominator_ are reversed. It follows that if both _Numerator_ and _Denominator_ and negative then both are made positive.

It is an error if _Denominator_ is zero.

Fractions are not simplified in the constructor.

Because [_TFraction_](./TFraction.md) is an invariant record to only way to set the [_Numerator_](./TFraction-Numerator.md) and [_Denominator_](./TFraction-Denominator.md) properties is via the construction process. They retain the same value through the life of the record instance.

### Implicit construction

Due to the magic of the [_Implicit_](./TFraction-Implicit.md) operator overload, a [_TFraction_](./TFraction.md) instance can be created simply by assigning a floating point or integer value to a [_TFraction_](./TFraction.md) variable, for example:

```pascal
var
  F, G: TFraction;
begin
  F := 42;    // integer assignment
  G := 3/4;   // floating point assignment (3/4 = 0.75)
end;
```

In the case of integer assignment the [_Implicit_](./TFraction-Implicit.md) operator overload calls _Create_ internally, passing the integer value in the _Numerator_ parameter and 1 to thr _Denominator_ parameter.

For floating point assignments, [_Implicit_](./TFraction-Implicit.md) calculates the numerator and denominator of the best fractional approximation to the floating point value, within five decimal places. _Create_ is again called internally and the calculated values are passed to _Numerator_ and _Denominator_ parameters.

It is tempting to use the floating point assignment to enable fraction to assign values expressed using the divide operator to avoid calling _Create_ explicitly, as in.

```pascal
G := 3/4;
```

instead of

```pascal
G := TFraction.Create(3, 4);
```

Be aware though that `3/4` is actually converted to a floating point value before being converted to a [_TFraction_](./TFraction.md). This is not only quite a slow operation but it is potentially inaccurate, especially for fractions with large numerators and denominators because rounding errors can occur.

### Note

The [_WholeNumberPart_](./TFraction-WholeNumberPart.md) and [_FractionalPart_](./TFraction-FractionalPart.md) properties are not set explicitly: they are calculated from the [_Numerator_](./TFraction-Numerator.md) and [_Denominator_](./TFraction-Denominator.md) properties.

### Example

```pascal
var
  F1, F2, F3, F4, F5: TFraction;
begin
  F1 := TFraction.Create(3, 8);
  F2 := TFraction.Create(-3, 8);
  F3 := TFraction.Create(3, -8);
  F4 := TFraction.Create(-3, -8);
  F4 := TFraction.Create(0 -8);
  Assert((F1.Numerator = 3) and (F1.Denominator = 8));
  Assert((F2.Numerator = -3) and (F2.Denominator = 8));
  Assert((F3.Numerator = -3) and (F3.Denominator = 8));
  Assert((F4.Numerator = 3) and (F4.Denominator = 8));
  Assert((F4.Numerator = 0) and (F4.Denominator = 8));
end;
```

## See Also

* [_Implicit_](./TFraction-Implicit.md) operator overload
