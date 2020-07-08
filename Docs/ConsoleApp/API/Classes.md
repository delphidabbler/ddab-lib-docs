# Classes

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

The following classes are provided by the project:

| Class | Description |
|-------|-------------|
| [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md) | Base class for [_TPJConsoleApp_](./TPJConsoleApp.md). Provides all functionality but declares all properties protected. Use this class if creating sub-classes that do not want to make all properties public or need to execute custom code within the class rather than handling events. |
| [_TPJConsoleApp_](./TPJConsoleApp.md) | Main console application class. Makes all properties inherited from [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md) public. Use instances of this class when working with console processes. |
