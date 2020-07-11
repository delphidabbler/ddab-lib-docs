# [Fractions Unit](../Fractions.md) Overview

This unit contains an encapsulation of a fraction.

A single advanced record type, [TFraction](./API/TFraction.md), is used to encapsulate the fraction. Instances of the record are immutable, i.e. their properties cannot be altered once the instance has been constructed. All methods that manipulate properties create new instances containing the results.

Operator overloading is used extensively to enable normal arithmetic operations to be carried out on fractions.

[DUnit](http://dunit.sourceforge.net/) tests are provided with the source code to help you test the code's accuracy.

Example code is included in the documentation of each method, operator overload or property.

> The current code is beta. The interface is liable to change. If any bugs are noticed, please report them via the [issue tracker](https://sourceforge.net/p/ddablib/tickets/) on SourceForge.

## Links

* [Programmers' Guide](./API.md)
* [Credits](./Credits.md)
