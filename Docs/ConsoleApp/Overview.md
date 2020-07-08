# [Console Application Runner Classes](../ConsoleApp.md) Overview

> This page provides an overview of the features of the Console Application Runner Classes. If you are looking for information on programming with the classes please see the [Programmers' Guide](./API.md).

The Console Application Runner classes are intended to simplify working with child console application processes.

Here's a short list of tasks that the classes simplify:

* Running a console application from a program and waiting for it to finish.
* Running a console application in the background and getting notified when it finishes.
* Redirecting a console application's standard input / output from and to files or pipes.
* Capturing the output of a console application and displaying it in a GUI.
* Configuring the appearance and visibility of a console process.
* Terminating errant applications.

[_TPJConsoleApp_](./API/TPJConsoleApp.md) is the main class responsible for console applications. It enables standard input, standard output and standard error to be redirected to and from files or pipes. It can also time-slice the running of the console application to allow the calling application to continue processing and to enable redirected piped output to be processed.

Various other properties of the console application can also be configured, including:

* Whether the application's process and thread handles can be inherited.
* Whether the application is visible or is displayed in a new console window.
* The console window's title, colour, size and position.
* The environment block passed to the application.
* The application's maximum execution time. The process can be forcibly terminated if it times-out.
* The application's priority.

Information about the running process can be read and a console application's exit code is made available.

If a console application fails to execute information about the error is provided.

[_TPJConsoleApp_](./API/TPJConsoleApp.md) descends from [_TPJCustomConsoleApp_](./API/TPJCustomConsoleApp.md), which provides all the functionality of the derived class, except that all properties are protected. [_TPJCustomConsoleApp_](./API/TPJCustomConsoleApp.md) should be used if you need to create subclasses. Subclasses should make the required properties public.

## Links

* [Programmers' Guide](./API.md)
* [Examples](./Examples.md)
* [Appendices](./Appendices.md)
