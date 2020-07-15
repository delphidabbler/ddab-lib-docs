# Environment property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property Environment: Pointer;
```

## Description

_Environment_ references the environment block to be used by the console application or is **nil** if the child process is to inherit the parent process' environment block.

If the property is not **nil** then the memory it points to must not be freed until the console application has finished executing.

The default value is **nil**.

## Remarks

To give a console application its own environment block you must:

* Allocate memory for the environment block.
* Set up the environment block containing the required environment variables.
* Set the _Environment_ property to point to the environment block.
* Execute the console application.
* Free the environment block.

> See [this article](https://delphidabbler.com/articles/article-6) and its demo code for information on setting up environment blocks.

**[Up to v3.0.1]** The environment variables contained in the block must be encoded as a sequnece of _AnsiChar_ characters regardless of whether a Unicode or ANDI Delphi compiler is used.

**[From v3.1]** The environment variables contained in the block must be stored as a sequence of _WideChar_ characters if the [_UnicodeEnvironment_](./TPJCustomConsoleApp-UnicodeEnvironment.md) property is _True_ or as a sequence of _AnsiChar_ characters otherwise. ***Important:*** The memory allocated for the block must allow for the size of characters used.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
