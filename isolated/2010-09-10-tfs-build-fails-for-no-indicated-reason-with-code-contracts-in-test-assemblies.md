---
title: TFS Build fails for no indicated reason with code contracts in test assemblies
categories : .Net
tags : TFS
date: 2010-09-10 17:02:08 +10:00
---


(MSTest.exe, PID 1868, Thread 1) Exception thrown when enumerating assembly: System.IO.FileLoadException: Could not load file or assembly 'MyProject.Services.Business.UnitTests.Contracts, Version=1.0.449.0, Culture=neutral, PublicKeyToken=0e60eebea588ffe8' or one of its dependencies. Strong name validation failed. (Exception from HRESULT: 0x8013141A)
File name: 'MyProject.Services.Business.UnitTests.Contracts, Version=1.0.449.0, Culture=neutral, PublicKeyToken=0e60eebea588ffe8' ---> System.Security.SecurityException: Strong name validation failed. (Exception from HRESULT: 0x8013141A)

The Zone of the assembly that failed was:
MyComputer
   at System.Reflection.RuntimeAssembly._nLoad(AssemblyName fileName, String codeBase, Evidence assemblySecurity, RuntimeAssembly locationHint, StackCrawlMark& stackMark, Boolean throwOnFileNotFound, Boolean forIntrospection, Boolean suppressSecurityChecks)
   at System.Reflection.RuntimeAssembly.nLoad(AssemblyName fileName, String codeBase, Evidence assemblySecurity, RuntimeAssembly locationHint, StackCrawlMark& stackMark, Boolean throwOnFileNotFound, Boolean forIntrospection, Boolean suppressSecurityChecks)
   at System.Reflection.RuntimeAssembly.InternalLoadAssemblyName(AssemblyName assemblyRef, Evidence assemblySecurity, StackCrawlMark& stackMark, Boolean forIntrospection, Boolean suppressSecurityChecks)
   at System.Reflection.RuntimeAssembly.InternalLoadFrom(String assemblyFile, Evidence securityEvidence, Byte[] hashValue, AssemblyHashAlgorithm hashAlgorithm, Boolean forIntrospection, Boolean suppressSecurityChecks, StackCrawlMark& stackMark)
   at System.Reflection.Assembly.LoadFrom(String assemblyFile)
   at Microsoft.VisualStudio.TestTools.TestTypes.Unit.AssemblyEnumerator.EnumerateAssembly(IWarningHandler warningHandler, String location, ProjectData projectData, ObjectHandle assemblyResolverWrapper)
   at Microsoft.VisualStudio.TestTools.TestTypes.Unit.AssemblyEnumerator.EnumerateAssembly(IWarningHandler warningHandler, String location, ProjectData projectData, ObjectHandle assemblyResolverWrapper)
   at Microsoft.VisualStudio.TestTools.TestTypes.Unit.UnitTestAttributeEnumerator.Read(ITestTypeExtensionClientSidesProvider provider, IWarningHandler warningHandler, String assemblyFileName, ProjectData projectData, TestRunConfiguration testRunConfiguration)
{% endhighlight %}





* *.UnitTests.dll
* *.IntegrationTests.dll
* *.LoadTests.dll



1. the file spec is recursive and so the CodeContracts directory is searched, and
1. the contract assembly will be named *.UnitTests.Contracts.dll



[0]: http://social.msdn.microsoft.com/Forums/en-US/codecontracts/thread/8cfd66b3-007f-45a7-9267-f45579c6401c