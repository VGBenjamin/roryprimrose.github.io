---
title: Code Contracts and side by side Azure 1.6 and 1.7 SDK
categories : .Net, Applications
tags : Azure
date: 2012-06-08 22:42:05 +10:00
---



{% highlight text linenos %}
Reading assembly 'Microsoft.WindowsAzure.ServiceRuntime' from 'C:\Program Files\Windows Azure SDK\v1.6\ref\Microsoft.WindowsAzure.ServiceRuntime.dll' resulted in errors.
    Assembly reference not resolved: msshrtmi, Version=1.6.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35.
    Could not resolve type reference: [msshrtmi]Microsoft.WindowsAzure.ServiceRuntime.Internal.InteropRoleUpdates.
    Could not resolve type reference: [msshrtmi]Microsoft.WindowsAzure.ServiceRuntime.Internal.RoleStatus.
{% endhighlight %}

> _To avoid confusion when you install both versions, the public versions of the .NET assemblies have been changed. Assemblies from November 2011 are typically marked with version 1.0 or 1.1. The June 2012 release assemblies are labeled with version 1.7. This change will require you to recompile applications or to use assembly binding redirects to pick up the new June 2012 assemblies. For more information, see [Assembly Binding Redirection][1]._




[0]: /blogfiles/image_141.png
[1]: http://msdn.microsoft.com/en-us/library/2fc472t2(v=vs.90).aspx
[2]: /blogfiles/image_142.png
[3]: /blogfiles/image_143.png