# [Console Application Runner Classes](../../ConsoleApp.md) Example 13: Customising a console app's environment block. [v3.1]

> This example requires v3.1.0 or later of the Console Application Runner Classes

By default any console app process started by [_TPJConsoleApp_](../API/TPJConsoleApp.md) etc. will inherit a copy of the environment variables of the parent process.

> It is beyond the scope of this example to explain environment blocks and environment varaibles in detail. To learn about them please see the article "[How to access environment variables](https://delphidabbler.com/articles/article-6)".

This can be changed by creating a new _environment block_ and storing a pointer to it in the [_Environment_](../API/TPJCustomConsoleApp-Environment.md) property. An environment block can be either in ANSI format where each character is one byte (the default) or in Unicode format where each character occupies two bytes.

> Prior to v3.1.0 the [_Environment_](../API/TPJCustomConsoleApp-Environment.md) property only supported ANSI environment blocks, but v3.1.0 added the [_UnicodeEnvironment_](../API/TPJCustomConsoleApp-UnicodeEnvironment.md) Boolean property that lets you specify whether the environment block is ANSI (`False`) or Unicode (`True`). For reasons of backward compatibility [_UnicodeEnvironment_](../API/TPJCustomConsoleApp-UnicodeEnvironment.md) defaults to `False`.

This example shows how to pass a custom environment block to a console application using the [_Environment_](../API/TPJCustomConsoleApp-Environment.md) and [_UnicodeEnvironment_](../API/TPJCustomConsoleApp-UnicodeEnvironment.md) properties.

There are two applications in this example:

1. A simple GUI application that lets you define a custom environment block to be passed to a console app that is run using [_TPJConsoleApp_](../API/TPJConsoleApp.md). This app will pass a Unicode environment block when compiled with a Unicode Delphi compiler (i.e. Delphi 2009 and later) or an ANSI environment block if compiled with an earlier, non-Unicode, compiler.
2. A console application that simply writes its environment variables to _stdout_.

## First, some helper code

> The [gist](https://gist.github.com/delphidabbler/81f9e2b48ff6bd1c9736) mentioned here contains all the routines from the article "[How to access environment variables](https://delphidabbler.com/articles/article-6)". If you want to know how they work then please read the article.

Before we get started on the apps themselves we need code to read environment variables and to create the required environment block. Since the purpose of this example is to learn about how to pass an environment block to a console app using [_TPJConsoleApp_](../API/TPJConsoleApp.md) and not to learn about how to create and manipulate environment blocks, we will steal some code from elsewhere to perform these tasks.

All the code you need (and more) can be found in the _gist_ [delphidabbler/UEnvVars.pas](https://gist.github.com/delphidabbler/81f9e2b48ff6bd1c9736). Either copy and paste the content of this gist into a file named `UEnvVars.pas` or download the file itself using the button displayed on the gist's web page.

## On with the GUI app

Start a new Delphi VCL forms application. Drop a _TMemo_, a _TCheckBox_ and a _TButton_ onto the form. The memo control will be used to enter custom environment variables in `Name=Value` format, one per line. The checkbox will be used to determine whether the child process gets a copy of the parent process' environment block along with the environment variables entered in the memo. Clicking the button will execute the console app.

Now add the `UEnvVars.pas` file that you created earlier to the project. We will use the [_CreateEnvBlock_](https://delphidabbler.com/articles/article-6#createenvblock) routine to create an environment block containing the required environment variables.

All the code of the GUI app goes into the button's _OnClick_ event handler, so double click the button in the designer and enter the following code into the resulting event handler:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  EnvBlockSize: Integer;
  EnvBlock: Pointer;
  App: TPJConsoleApp;
begin
  // create the environment block
  EnvBlockSize := CreateEnvBlock(Memo1.Lines, CheckBox1.Checked, nil, 0);
  GetMem(EnvBlock, EnvBlockSize * SizeOf(Char));
  try
    CreateEnvBlock(Memo1.Lines, CheckBox1.Checked, EnvBlock, EnvBlockSize);
    // run the console app
    App := TPJConsoleApp.Create;
    try
      App.CommandLine := 'PrintEnv.exe';
      App.Visible := True;
      App.Environment := EnvBlock;
      {$IFDEF UNICODE}
      App.UnicodeEnvironment := True;
      {$ELSE}
      App.UnicodeEnvironment := False;
      {$ENDIF}
      App.Execute;
    finally
      App.Free;
    end
  finally
    // free the environment block
    FreeMem(EnvBlock);
  end;
end;
```

The first two lines find the size of the environment block and allocate sufficient memory for it. The second call to [_CreateEnvBlock_](https://delphidabbler.com/articles/article-6#createenvblock) is where the environment block gets created. [_CreateEnvBlock_](https://delphidabbler.com/articles/article-6#createenvblock) accepts a string list containing the custom environment variables, so we pass the memo's _Lines_ property to it. The second parameter determines whether a copy of the parent process' environment variables also gets included in the block, so we pass in the checkbox's _Checked_ property.

Next we create a [_TPJConsoleApp_](../API/TPJConsoleApp.md) instance ready to execute `PrintEnv.exe` and store a pointer to the environment block in the [_Environment_](../API/TPJCustomConsoleApp-Environment.md) property. We use conditional compilation to set the [_UnicodeEnvironment_](../API/TPJCustomConsoleApp-UnicodeEnvironment.md) property to `True` when compiled on a Delphi compiler with Unicode support and `False` when compiled without Unicode support. The console app is then executed and the [_TPJConsoleApp_](../API/TPJConsoleApp.md) instance is freed when the app returns.

Lastly we release the memory that holds the environment block: this should not be freed until after the console app has terminated.

## Finally, the console app

All we need now is to write the `PrintEnv.exe` console app that the above code tries to execute.

Start a new Delphi console application project ensuring it places its executable file in the same directory as the GUI app.

Add `UEnvVars.pas`, to the project. We will be using the [_GetAllEnvVars_](https://delphidabbler.com/articles/article-6#getallenvvars) routine to populate a string list with all the app's environment variables. Each item in the list will be displayed in `Name=Value` format.

Now edit the project file to look like this:

```pascal
program PrintEnv;

{$APPTYPE CONSOLE}

uses
  Classes,
  UEnvVars in 'UEnvVars.pas';

{$R *.res}

var
  EnvVars: TStrings;
  I: Integer;
begin
  EnvVars := TStringList.Create;
  try
    GetAllEnvVars(EnvVars);
    for I := 0 to Pred(EnvVars.Count) do
    begin
      WriteLn(EnvVars[I]);
    end;
    WriteLn;
    Write('Press enter to end');
    ReadLn;
  finally
    EnvVars.Free;
  end;
end.
```

Here we create a string list to hold the environment variables then call [_GetAllEnvVars_](https://delphidabbler.com/articles/article-6#getallenvvars) to populate it. Next we write each environment variable in turn to _stdout_ then finally wait for the user to press _Enter_ before terminating the app.

All that remains is to compile both apps then run the GUI program, enter some environment variables, decide whether to include the current environment, then click the button and check that `PrintEnv.exe` displays the expected environment variables.

> Sometimes a service may inject an environment variable into every new process, so you may see some unexpected values in the output of `PrintEnv.exe`. For some NVidia graphics drivers insert a `PATH` environment variable if it is missing and may modify it when present. So, if you something similar it's not a bug in this code!

## Links

* [Previous example](./Example12.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
