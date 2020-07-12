# Create constructor

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvVars_](./TPJEnvVars.md)

```pascal
constructor Create(AOwner: TComponent);
```

> ***Warning:*** *[_TPJEnvVars_](./TPJEnvVars.md) has been **deprecated**. The [_TPJEnvironmentVars_](./TPJEnvironmentVars.md) static class should be used instead.*

## Description

Constructs a new [_TPJEnvVars_](./TPJEnvVars.md) component instance.

***Parameter:***

* _AOwner_ -- Reference to the component that owns this component. May be `nil` in which case this component has no owner.

Only one instance of a [_TPJEnvVars_](./TPJEnvVars.md) component is allowed on any form (or to be owned by any component). An attempt to create a second instance with the same owner will cause an _Exception_ to be raised and the duplicate instance will not be created.

Multiple instances **can** be created by passing `nil` as the _AOwner_ parameter.
