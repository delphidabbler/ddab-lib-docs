# [Stream Extension Classes](../Streams.md) Overview

This project provides a library of classes that can be used to extend the functionality of Delphi's _TStream_ classes.

The classes provided are:

* A _TStream_ derived class which can wrap another _TStream_. This is useful as a base class for filters to wrap round existing stream classes.

* A set of classes that wrap existing streams and provide an _IStream_ interface to them -- like Delphi's previously undocumented _TStreamAdapter_ class. Also included are classes that provides a _IStream_ interface to any file or any handle stream.

## Links

* [Programmers' Guide](./API.md)
