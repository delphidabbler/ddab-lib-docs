# [Environment Variables Unit](../EnvVars.md) Overview

> This page provides an overview of the features of the Environment Variables Unit. If you are looking for information on programming with the classes please see the [Programmers' Guide](./API.md).

The Environment Variables unit provides an interface to the environment variables that are available to a Windows process. The unit contains static class for interogating and modifying environment variables.

The class has methods to:

* Read, write and delete environment variables.
* Query whether an environment variable exists.
* Get the number of environment variables in the environment block along with the size of the block.
* List and enumerate the names, or names and value, of all environment variables in the environment block.
* Create a new environment block suitable for passing to a child process.

There is also an enumerator class the provides an alternative way to enumerate environment variable names.

The unit also contains a component and stand-alone routines that provide some of the functionality of the static class. ***These are all deprecated*** and are provided for backward compatibility reasons only. They should not be used in new code.

> In previous versions the component was registered with the Delphi IDE when this unit was included in a design time package. This is no longer the case. The component is registered only if `PJEnvVarsDsgn.pas` is included a _design_ package and `PJEnvVars.pas` is included in the same _design_ package or a _required_ package.

## Links

* [Programmers' Guide](./API.md) -- Classes, methods, properties etc.
