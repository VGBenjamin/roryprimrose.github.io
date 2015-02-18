---
title: Executing build tasks without a build server – In action
categories : .Net, My Software
tags : TFS, WiX
date: 2011-07-06 23:02:00 +10:00
---



[![image][3]][2]
[![image][5]][4]
[![image][7]][6]
1. Executing with verbose logging
[![image][9]][8]

BuildTaskExecutor BinaryOutputVersion|bov
Renames the project output to include the product version of the project output.

BuildTaskExecutor Help|/?
Displays help information about the available tasks

BuildTaskExecutor IncrementAssemblyVersion|iav
Increments version number parts in AssemblyVersionAttribute entries in code files

BuildTaskExecutor SyncWixVersion|swv
Synchronizes the product version in a Wix project to the version of a binary file.

BuildTaskExecutor TfsCheckout|tfsedit
Checks out files from TFS based on a search pattern. The checkout will use default credentials resolved for the identified files.

BuildTaskExecutor WixOutputVersion|wov
Renames the Wix project output to include the wix product version.
{% endhighlight %}


[0]: /2011/07/03/Executing-build-tasks-without-a-build-server-%E2%80%93-Implementation/
[1]: /2011/07/01/Executing-build-tasks-without-a-build-server-%E2%80%93-Design/
[2]: /blogfiles/image%5B8%5D.png
[3]: /blogfiles/image%5B8%5D_thumb.png
[4]: /blogfiles/image%5B11%5D.png
[5]: /blogfiles/image%5B11%5D_thumb.png
[6]: /blogfiles/image%5B14%5D.png
[7]: /blogfiles/image%5B14%5D_thumb.png
[8]: /blogfiles/image%5B17%5D.png
[9]: /blogfiles/image%5B17%5D_thumb.png