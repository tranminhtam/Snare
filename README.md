# Snare
The purpose of this App is to provide an easy to use interface to communicate with storage devices.

## Requirements
1. Support command line arguments.
2. Support automated testing.
3. Support testing multiple drives.
4. Support production process on multiple drives.
6. Support software upgrade, and extensions.
7. Support drivers.
8. Support user defined scripts.
9. Support multiple operating systems.

## Decisions and alternatives
**Decisions**

1. Requirements will be broken down into self-containing modules that can be developed, and tested, independently.
2. Each module will be hosted in its own AppDomain to avoid dependency conflicts.
3. Modules will be written in C#, and conform to the ECMA standards to be able to run on the [Mono](http://www.mono-project.com/). Mono is a software platform designed to allow developers to easily create cross platform applications.
4. GUI must be developed independent from modules to ensure cross platform support. For Windows, we will use Prism 5.0 with WPF.
5. Performance critital paths will be written as C++ library to be used by modules.
6. IronPython 2.7.5 will be used to support user defined scripts, because it also runs on Mono.

***Alternatives***

1. Requirements can be broken down into self-containing applications that can be developed, and tested, independently.
2. Since each application runs as a separate process, there are no dependency conflicts.
3. Windows [.NET Core](http://dotnet.github.io/core/about/overview.html) also support cross platform applications.
4. Windows Forms is an alternative to WPF.
5. Performance critital paths can also be written in C.
6. In the future, we might use IronPython 3.

## Concerns
1. Microsoft plans to gradually replace the **.NET Framework** with **.NET Core**.
  1. Updates to .NET libraries might break our code.
  2. .NET Core currently does not support WPF or Windows Forms.
2. We currently don't have any experience writting applications for Mono, or .NET Core.

## Assumptions
1. Manage code (C++/CLI) will be regcogize by Mono, and .NET Core.
2. Critical .NET libraries will be available, and behave as it did in the .NET Framework.
