---
title: Executing build tasks without a build server – Example scenario
categories : .Net
tags : Extensibility, TFS, WiX
date: 2011-07-07 00:14:06 +10:00
---

* Check out from TFS as required
* Sync updated product version into wix project
* Check out from TFS as required
* Rename wix output to include the product version
* Neovolve.Switch.Extensibility
* Neovolve.Switch.Skinning
* Neovolve.Switch
* Neovolve.Switch.Deployment
* Unit test projects

{% highlight text linenos %}
If Not '$(ConfigurationName)' == 'Release' GOTO End

CD "$(SolutionDir)"
CALL bte tfsedit /pattern:"$(SolutionDir)Solution Items\ProductInfo.cs" /i
CALL bte iav /pattern:"$(SolutionDir)Solution Items\ProductInfo.cs" /b

GOTO End

:End
{% endhighlight %}





<?xml version="1.0"
      encoding="UTF-8" ?>
<?include Definitions.wxi ?>

<Wix xmlns="http://schemas.microsoft.com/wix/2006/wi"
     xmlns:netfx="http://schemas.microsoft.com/wix/NetFxExtension">
  <Product Id="*"
           Name="$(var.PRODUCTNAME)"
           Language="1033"
           Version="$(var.ProductVersion)"
           Manufacturer="$(var.COMPANYNAME)"
           UpgradeCode="0FD2155F-5676-448F-864A-482BE0C26E97">
{% endhighlight %}


{% highlight text linenos %}
CD "$(SolutionDir)"
CALL bte tfsedit /pattern:"$(ProjectDir)Definitions.wxi" /i
CALL bte swv /pattern:"$(ProjectPath)" /source:"$(SolutionDir)Neovolve.Switch\$(OutDir)Switch.exe" /M /m /b /r
{% endhighlight %}





1. Changing the project during compilation will cause Visual Studio to want to reload the project. This is not really a problem but is a bad user experience as reload project dialogs will get in the way.
1. The next time the project compiles, the task will have to deal with having a prior version number in the output name that it will need to parse out and replace. Easily achievable with a regular expression, but messy.



{% highlight text linenos %}
CD "$(SolutionDir)"
CALL bte wov /pattern:"$(ProjectPath)"
{% endhighlight %}




{% highlight text linenos %}
------ Rebuild All started: Project: Neovolve.Switch.Extensibility, Configuration: Release Any CPU ------
  BuildTaskExecutor - Neovolve Build Task Executor 1.0.0.29135
  
  Executing task 'TfsCheckout'.
  Using 'C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\tf.exe' to check out files.
  Searching for matching files under 'D:\Codeplex\Neovolve.Switch\Solution Items\'.
  Checking out file 'D:\Codeplex\Neovolve.Switch\Solution Items\ProductInfo.cs'.
  Solution Items:
  ProductInfo.cs
  
  BuildTaskExecutor - Neovolve Build Task Executor 1.0.0.29135
  
  Executing task 'IncrementAssemblyVersion'.
  Searching for matching files under 'D:\Codeplex\Neovolve.Switch\Solution Items\'.
  Updating file 'D:\Codeplex\Neovolve.Switch\Solution Items\ProductInfo.cs' from version '2.0.2.0' to '2.0.3.0'.
  elapsed time: 134.0076ms
  elapsed time: 239.0136ms
  
  Microsoft (R) .NET Framework Strong Name Utility  Version 3.5.30729.1
  Copyright (c) Microsoft Corporation.  All rights reserved.
  
  Assembly 'obj\Release\Neovolve.Switch.Extensibility.dll' successfully re-signed
  Neovolve.Switch.Extensibility -> D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Extensibility\bin\Release\Neovolve.Switch.Extensibility.dll
------ Rebuild All started: Project: Neovolve.Switch.Skinning, Configuration: Release Any CPU ------

  Microsoft (R) .NET Framework Strong Name Utility  Version 3.5.30729.1
  Copyright (c) Microsoft Corporation.  All rights reserved.
  
  Assembly 'obj\Release\Neovolve.Switch.Skinning.dll' successfully re-signed
  Neovolve.Switch.Skinning -> D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Skinning\bin\Release\Neovolve.Switch.Skinning.dll
------ Rebuild All started: Project: Neovolve.Switch.Extensibility.UnitTests, Configuration: Release Any CPU ------
  
  Microsoft (R) .NET Framework Strong Name Utility  Version 3.5.30729.1
  Copyright (c) Microsoft Corporation.  All rights reserved.
  
  Assembly 'obj\Release\Neovolve.Switch.Extensibility.UnitTests.dll' successfully re-signed
  Neovolve.Switch.Extensibility.UnitTests -> D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Extensibility.UnitTests\bin\Release\Neovolve.Switch.Extensibility.UnitTests.dll
------ Rebuild All started: Project: Neovolve.Switch, Configuration: Release x86 ------
  
  Microsoft (R) .NET Framework Strong Name Utility  Version 3.5.30729.1
  Copyright (c) Microsoft Corporation.  All rights reserved.
  
  Assembly 'obj\x86\Release\Switch.exe' successfully re-signed
  Neovolve.Switch -> D:\Codeplex\Neovolve.Switch\Neovolve.Switch\bin\Release\Switch.exe
------ Rebuild All started: Project: Neovolve.Switch.UnitTests, Configuration: Release Any CPU ------
  Neovolve.Switch.UnitTests -> D:\Codeplex\Neovolve.Switch\Neovolve.Switch.UnitTests\bin\Release\Neovolve.Switch.UnitTests.dll
------ Rebuild All started: Project: Neovolve.Switch.Deployment, Configuration: Release x86 ------
        CD "D:\Codeplex\Neovolve.Switch\"
CALL bte tfsedit /pattern:"D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\Definitions.wxi" /i
CALL bte swv /pattern:"D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\Neovolve.Switch.Deployment.wixproj" /source:"D:\Codeplex\Neovolve.Switch\Neovolve.Switch\bin\Release\Switch.exe" /M /m /b /r
        BuildTaskExecutor - Neovolve Build Task Executor 1.0.0.29135
        Executing task 'TfsCheckout'.
        Using 'C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\tf.exe' to check out files.
        Searching for matching files under 'D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\'.
        Checking out file 'D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\Definitions.wxi'.
        Neovolve.Switch.Deployment:
        Definitions.wxi
        BuildTaskExecutor - Neovolve Build Task Executor 1.0.0.29135
        Executing task 'SyncWixVersion'.
        Searching for matching files under 'D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\'.
        Updating wix project 'D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\Neovolve.Switch.Deployment.wixproj' from version '2.0.2.0' to '2.0.3.0'.

        CD "D:\Codeplex\Neovolve.Switch\"
CALL bte wov /pattern:"D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\Neovolve.Switch.Deployment.wixproj"
        BuildTaskExecutor - Neovolve Build Task Executor 1.0.0.29135
        Executing task 'WixOutputVersion'.
        Searching for matching files under 'D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\'.
        Moving 'D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\bin\Release\Neovolve Switch.msi' to 'D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\bin\Release\Neovolve Switch 2.0.3.0.msi'.
        Moving 'D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\bin\Release\Neovolve Switch.wixpdb' to 'D:\Codeplex\Neovolve.Switch\Neovolve.Switch.Deployment\bin\Release\Neovolve Switch 2.0.3.0.wixpdb'.
========== Rebuild All: 6 succeeded, 0 failed, 0 skipped ==========

Build Summary
-------------
00:13.492 - Success - Release Any CPU - Neovolve.Switch.Extensibility\Neovolve.Switch.Extensibility.csproj
00:12.825 - Success - Release x86 - Neovolve.Switch\Neovolve.Switch.csproj
00:12.793 - Success - Release x86 - Neovolve.Switch.Deployment\Neovolve.Switch.Deployment.wixproj
00:07.458 - Success - Release Any CPU - Neovolve.Switch.Skinning\Neovolve.Switch.Skinning.csproj
00:07.067 - Success - Release Any CPU - Neovolve.Switch.Extensibility.UnitTests\Neovolve.Switch.Extensibility.UnitTests.csproj
00:01.879 - Success - Release Any CPU - Neovolve.Switch.UnitTests\Neovolve.Switch.UnitTests.csproj

Total build time: 00:55.555

========== Rebuild All: 6 succeeded or up-to-date, 0 failed, 0 skipped ==========
{% endhighlight %}


* Checked out ProductInfo.cs from TFS
* Identified the existing version as 2.0.2.0
* Incremented version to 2.0.3.0
* Synchronised the Wix project to 2.0.3.0
* Moved the Wix project output to the same filename with the addition of the version number.
      
      

{% highlight text linenos %}
@ECHO OFF
References\Neovolve\BuildTaskExecutor\BuildTaskExecutor.exe %*

If errorlevel 1 GOTO BuildTaskFailed
GOTO BuildTaskSuccessful

:BuildTaskFailed
exit 1
:BuildTaskSuccessful
{% endhighlight %}

      

[0]: /2011/07/01/Executing-build-tasks-without-a-build-server-%E2%80%93-Design/
[1]: /2011/07/03/Executing-build-tasks-without-a-build-server-%E2%80%93-Implementation/
[2]: /2011/07/06/Executing-build-tasks-without-a-build-server-%E2%80%93-In-action/
[3]: http://switch.codeplex.com/
[4]: /blogfiles/image_110.png
[5]: /blogfiles/image_111.png
[6]: /blogfiles/image_112.png
[7]: /blogfiles/image_113.png
[8]: /blogfiles/image_114.png