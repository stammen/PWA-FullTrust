# Example of PWA UWP App with FullTrust Desktop Extension

This sample demonstrates how a PWA UWP application can include a Win32 Desktop Extension that runs with Full Trust

The App does the following:

* Packages a Windows 10 PWA UWP application with a Win32 Desktop Extension



## Requirements

* Visual Studio 2017 with Windows Universal App Development package installed
* Windows SDK version 17134 (installed with Visual Studio 2017) 

## Running the Sample

* Open projects\PWA\Store packages\windows10\App.sln with Visual Studio 2017

* Select the Debug/Any CPU configuration. 

* Set the App project as the StartUp project

* Press F5 to build and run the solution. 

* The PWA UWP app should run and display the Microsoft web site

To run the Win32 Forms App

* Open a Command Prompt console

* enter 

```console
start pwadesktopextension:
``` 

The Win32 Forms App should run


