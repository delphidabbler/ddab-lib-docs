# [Clipboard Viewer Component](../CBView.md)  Overview

> This page provides an overview of the features of the Clipboard Viewer Component. If you are looking for information on programming with the component please see the [Programmers' Guide](./API.md).

This project provides a single non-visual component that notifies the user when the content of the Windows clipboard changes. This is done by triggering an event.

On versions of Windows that support it the newer clipboard format listener API is used to monitor the clipboard. On older versions of Windows the older, and less reliable, clipboard viewer API is used instead.

> Thanks to _Mason Wheeler_ for providing the more reliable clipboard listener code.

## Links

* [Programmers' Guide](./API.md) -- Classes, methods, properties etc.
* [Example](./Example.md)
