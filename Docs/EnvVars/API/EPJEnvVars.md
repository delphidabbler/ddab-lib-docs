# EPJEnvVars exception class

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

```pascal
type
  {$IFDEF Supports_EOSError}
  EPJEnvVars = class(EOSError);
  {$ELSE}
  EPJEnvVars = class(EWin32Error);
  {$ENDIF}
```

***Warning:*** _EPJEnvVars_ *is **deprecated**. It is used only by the [_TPJEnvVars_](./TPJEnvVars.md) component, which is itself deprecated. The exception class is retained for backward compatibility only.*

## Decription

Class of exception raised when errors are detected in the  _PJEnvVars_ unit.

On versions of Delphi that support _EOSError_ _EPJEnvVars_ descends from that, otherwise it descends from _EWin32Error_.
