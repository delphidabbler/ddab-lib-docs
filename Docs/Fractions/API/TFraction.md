# TFraction record

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Introduced:*** v0.1

## Description

_TFraction_ is an advanced "record with methods" encapsulates a vulgar fraction and defines various mathematical operations on it.

The record is immutable, i.e. its properties are read-only and are never modified by any operations on the record. Any methods that manipulate a fraction always return a new record instance containing the result of the manipulation.

### Creating a TFraction instance

A variable of type _TFraction_ can be instantiated by passing the numerator and denominator to the record's [constructor](./TFraction-Create.md). The fraction is normalised by the constructor, so that the denominator is always positive and the numerator takes the sign.

Furthermore a _TFraction_ variable can be instantiated by assigning a variable of a valid type to it. Supported types are:

* Another _TFraction_. Properties are simply copied.
* Any integer type. This creates a fractions with numerator equal to the integer and denominator 1.
* A _Single_, _Double_ or _Extended_ floating point type. The floating point value is converted to a fraction to an accuracy of 5 decimal places. The floating point value must be 0 or have an absolute value in the range 1.0e-19 to 1.0e+19.

### Properties

The following read-only properties are exposed.

| Property | Description |
|----------|-------------|
| [_Numerator_](./TFraction-Numerator.md) | The fraction's numerator. |
| [_Denominator_](./TFraction-Denominator.md) | The fraction's denominator. |
| [_WholeNumberPart_](./TFraction-WholeNumberPart.md) | The whole number part of the fraction when considered as a mixed fraction. |
| [_FractionalPart_](./TFraction-FractionalPart.md) | The fractional part of the fraction when considered as a mixed fraction. |

### Operator overloads

The operators are overloaded by the record

| Operator | Description |
|----------|-------------|
| [_Implicit_](./TFraction-Implicit.md) | Enables a _TFraction_ record to be cast / assigned from integer and floating point types and to floating point types (not integers). |
| [_Equal_](./TFraction-Equal.md) | Enables two _TFraction_ records to be compared for equality using the `=` operator. |
| [_NotEqual_](./TFraction-NotEqual.md) | Enables two _TFraction_ records to be compared for inequality using the `<>` operator. |
| [_LessThan_](./TFraction-LessThan.md) | Enables two _TFraction_ records to be compared using the less-than (`<`) operator.  |
| [_LessThanOrEqual_](./TFraction-LessThanOrEqual.md) | Enables two _TFraction_ records to be compared using the less-than-or-equal (`<=`) operator.  |
| [_GreaterThan_](./TFraction-GreaterThan.md) | Enables two _TFraction_ records to be compared using the greater-than (`>`) operator.  |
| [_GreaterThanOrEqual_](./TFraction-GreaterThanOrEqual.md) | Enables two _TFraction_ records to be compared using the greater-than-or-equal (`>=`) operator.  |
| [_Negative_](./TFraction-Negative.md) | Enables the unary minus operator to be used to negate a _TFraction_ record.  |
| [_Positive_](./TFraction-Positive.md) | Enables the unary plus operator to be applied to a _TFraction_ record.  |
| [_Add_](./TFraction-Add.md) | Enables the addition operator (`+`) to be used to add two _TFraction_ records. |
| [_Subtract_](./TFraction-Subtract.md) | Enables the subtraction operator (`-`) to be used to subtract two _TFraction_ records. |
| [_Multiply_](./TFraction-Multiply.md) | Enables the multiplication operator (`*`) to be used to multiple two _TFraction_ records.  |
| [_Divide_](./TFraction-Divide.md) | Enables the division operator (`/`) to be used to divide to _TFraction_ records.  |
| [_IntDivide_](./TFraction-IntDivide.md) | Enables the integer division operator (`div`) to be used to divide two integers giving an integer result. |
| [_Modulus_](./TFraction-Modulus.md) | Enables the modulus operator (`mod`) to be used to get the fractional remainder after dividing one _TFraction_ record by another.  |
| [_Round_](./TFraction-Round.md) | Enables the `Round` operator to round a _TFraction_ record to the nearest whole number value.  |
| [_Trunc_](./TFraction-Trunc.md) | Enables the `Trunc` operator to truncate a _TFraction_ record to the nearest whole number in the direction of zero. |

### Methods

_TFraction_ defines several methods. Some are static class methods that operate on fractions passed as parameters while others are instance methods that operate on the current record. There is also a single constructor.

#### Constructor

| Method | Description |
|--------|-------------|
| [_Create_](./TFraction-Create.md) | Constructs a _TFraction_ instance from a given numerator and denominator.  |

#### Instance Methods

| Method | Description |
|--------|-------------|
| [_CompareTo_](./TFraction-CompareTo.md) | Compares the fraction to another and returns a value indicating which fraction is greatest or if they are equal. |
| [_Convert_](./TFraction-Convert.md) | Converts the fraction into an equivalent one in which the numerator and denominator are a given integer multiple of their original values. |
| [_HasCommonFactor_](./TFraction-HasCommonFactor.md) | Checks if a given integer is a common factor of the fraction. |
| [_IsProper_](./TFraction-IsProper.md) | Checks if the fraction is a proper fraction. |
| [_IsWholeNumber_](./TFraction-IsWholeNumber.md) | Checks if the fraction represents a whole number. |
| [_Reciprocal_](./TFraction-Reciprocal.md) | Returns the reciprocal of the fraction. |
| [_RoundToMultiple_](./TFraction-RoundToMultiple.md) | Rounds the fraction to the nearest whole number multiple of another fraction. |
| [_Sign_](./TFraction-Sign.md) | Returns a value representing the sign of the fraction.  |
| [_Simplify_](./TFraction-Simplify.md) | Two overloaded methods that reduce the fraction either to its common terms or by a given common factor. |
| [_TruncateToMultiple_](./TFraction-TruncateToMultiple.md) | Truncates the fraction to a whole number multiple of another fraction. |

#### Class Methods

| Method | Description |
|--------|-------------|
| [_Abs_](./TFraction-Abs.md) | Returns the absolute value of a given fraction. |
| [_Compare_](./TFraction-Compare.md) | Compares two fractions and returns a value indicating which of the two is greater or if they equal. |
| [_LCD_](./TFraction-LCD.md) | Computes the least common denominator of two fractions. |
| [_Max_](./TFraction-Max.md) | Overloaded methods that find the largest of two or more fractions. |
| [_Min_](./TFraction-Min.md) | Overloaded methods that find the smallest of two or more fractions. |
| [_Power_](./TFraction-Power.md) | Computes an integer power of a fraction. |
