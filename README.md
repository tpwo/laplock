# laplock

This extremely small (~200 lines, ~200KB binary) C++ program allows you to automatically lock your Windows laptop when the lid is closed.

Note that you can achieve the same result by adjusting Windows sign-in options, but then your computer will be locked also if the screen is turned off, and you cannot disable this secondary condition. See [Alternatives](#alternatives) for more details.

`laplock` runs on Windows 10 and probably later versions.

Note this is a fork of an older project which wasn't updated for many years. Original project: <https://github.com/dechamps/laplock>

## Usage

Just run it. At first, nothing will happen; this is normal as laplock runs silently in the background (you can check this using the Windows task manager). laplock will keep running until you log off or kill it. It is recommended to add laplock to your Startup folder; then you can happily forget about it.

Note that laplock listens intelligently for events; meaning, it doesn't consume any CPU *at all* while waiting.

## Compilation

There is only one C++ file and it should compile using any Windows compiler. It was successfully compiled using Build Tools for VS 2022.

Most easily you can compile it by installing *Build Tools for Visual Studio 20XX* and then choosing *Desktop development with C++* in the installer. This installs `cl.exe` which can be run via *Developer Command Prompt for Visual Studio*. The following command compiles a statically linked binary in `Release` folder:

    cl.exe /O2 /EHsc /DNDEBUG /nologo /MT /FeRelease/laplock.exe laplock.cpp

You can use the following command to compile a binary with debug symbols in the `Debug` folder:

    cl.exe /Zi /EHsc /nologo /FeDebug\laplock.exe laplock.cpp

These commands can be also easily run from VS Code, as they were added in `.vscode/tasks.json` file.

Detailed instructions how to install build tools, configure them, and debug C++ programs using cl.exe and VS Code are avaiable in [Microsoft docs](https://code.visualstudio.com/docs/cpp/config-msvc).

## Alternatives

In Windows `Sign-in options` you can set `Require sign-in` option to `Every Time` to lock your computer every time you close the lid *OR* every time the screen is turned off. This option is available here (screenshot taken from [superuser.com](https://superuser.com/a/1580759/1232011)):

![](https://i.stack.imgur.com/Wey3J.png)

In fact, the original version of this program worked exactly the same way, and I forked it to remove the screen turned-off condition. The rationale is described in [this commit message](https://github.com/tpwo/laplock/commit/b44d048b20cab4f254fcb6d03d7a396c488a8201).
