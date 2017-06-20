## Package Manager Console
* The Package Manager Console lets you use NuGet PowerShell commands to find, install, uninstall, and update NuGet packages.
* If you're missing the NuGet Package Manager in Visual Studio 2015, check Tools > Extensions and Updates... and search for the NuGet Package Manager extension. If you're unable to use the extensions installer in Visual Studio, you can download the extension directly from https://dist.nuget.org/index.html.
In Visual Studio 2017, NuGet and the NuGet Package Manager are automatically installed when you select any .NET-related workloads; you can also install it individually by checking the Individual components > Code tools > NuGet package manager option in the Visual Studio 2017 installer.)
* In all cases, you open the Console in Visual Studio through the Tools > NuGet Package Manager > Package Manager Console command.
At the top of the pane you can select the desired package source, manage sources (by clicking the gear icon), and select the default project to which commands will be applied:
Package Manager Console controls
You can override these settings with most commands by using the -Source and -ProjectName options.


# Some nuget packages are missing from this solution. click to restore
https://stackoverflow.com/questions/27895504/how-do-i-enable-nuget-package-restore-in-visual-studio
From the menu - Project-> Manage nuget packages
