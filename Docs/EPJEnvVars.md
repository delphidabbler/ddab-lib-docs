<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# EPJEnvVars #

| This is the documentation for the **v2.0** release of the unit. If you are using a **version 3** release please [see here](http://wiki.delphidabbler.com/index.php/Docs/EPJEnvVars). |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

**Project:** [Environment Variables Unit](EnvironmentVariablesUnit.md).

**Unit:** _PJEnvVars_

Exceptions of this class are raised by the _[TPJEnvVars](TPJEnvVars.md)_ component when an error occurs while attempting to modify environment variables.

The Windows error code associated with the error is stored in the public _ErrorCode_ property, while the Windows error message is recorded in the _Message_ property.

_EPJEnvVars_ inherits from _EOSError_ (or _EWin32Error_ on Delphi 5 and earlier) and adds no further properties or methods.