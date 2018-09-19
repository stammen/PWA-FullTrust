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

## Note:

I needed to update the min/max SDK version of the PWA project to 17134. Experiment with lower versions. Using 14393 did not work.

I set the output dir of the Windows Form app to the DesktopExtensions folder of the PWA project. I then added these files to the PWA project. 
This simplified the packaging of the Windows Form app files.

Look at the package.appxmanifest file of the PWA project. 

You will need to add the following to the Package:

```xml
xmlns:desktop="http://schemas.microsoft.com/appx/manifest/desktop/windows10" 
xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities" 
IgnorableNamespaces="uap mp build desktop rescap">
```

To add the Windows Form App add the following to the Application section

```xml
<Extensions>
  <uap:Extension Category="windows.protocol" Executable="DesktopExtensions/WindowsFormsApp1.exe" EntryPoint="Windows.FullTrustApplication">
    <uap:Protocol Name="pwadesktopextension" />
  </uap:Extension>
</Extensions
```

The above XML allows the WindowsFormsApp1.exe to be launched with the pwadesktopextension: protocol

Add the FullTrust Capability to the Capabilites section
```xml
<Capabilities>
  <Capability Name="internetClient" />
  <rescap:Capability Name="runFullTrust" />
</Capabilities>
```

