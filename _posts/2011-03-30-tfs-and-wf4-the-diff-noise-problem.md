---
title: TFS and WF4: The diff noise problem
categories : .Net
tags : TFS, WF
date: 2011-03-30 16:29:00 +10:00
---

For a long time the most popular post I have on this site is about how to configure Visual Studio to use [WinMerge as the merge/diff tool for TFS][0] rather than using the feature poor out of the box software. Sometimes the nature of the files under development result in version differences that have a lot of noise regardless of the diff/merge tool that you use.

Unfortunately WF is one of the common offenders. I absolutely love WF, but am disappointed that designer state information is persisted with the workflow definition rather than in a user file that is merged in the IDE. The result of this is that the activity xaml file changes if you collapse a composite activity, such as the Sequence activity. The actual workflow definition has not changed, but it is a new version of the file as far as a diff tool and TFS goes.

<!--more-->

For example, I have collapsed lots of activities on one of my workflows. The resulting diff using WinMerge looks like the following:![image][1]

There is a lot of noise here. It is all designer state information rather than actual changes to the workflow definition. There are several culprits in WF4 that cause this noise.

* sap:VirtualizedContainerService.HintSize
* &lt;x:Boolean x:Key="IsExpanded"&gt;
* &lt;x:Boolean x:Key="IsPinned"&gt;

Thankfully WinMerge has a great feature for applying a line filter expression (Tools &ndash;&gt; Filters &ndash;&gt; Linefilters). These can help to reduce a lot of this noise.![image][2]

I have put together three expressions to cover WF4.

* _^.*sap:VirtualizedContainerService\.HintSize="\d+,\d+".*$_ filters sap:VirtualizedContainerService.HintSize when it is defined in an attribute
* _^.*&lt;sap:VirtualizedContainerService.HintSize&gt;\d+,\d+&lt;/sap:VirtualizedContainerService.HintSize&gt;.*$_ filters 
      &lt;sap:VirtualizedContainerService.HintSize when it is defined in an element
* _^.*&lt;x:Boolean x:Key="(IsExpanded|IsPinned)"&gt;.+&lt;/x:Boolean&gt;.*$_ filters &lt;x:Boolean x:Key="IsExpanded"&gt; and &lt;x:Boolean 
      &lt;x:Key="IsPinned"&gt; elements

The above diff of workflow xaml with these filters applied now looks like the following.![image][3]

There are several things to notice about the result of line filters. The overview of differences is now much less noisy. The file differences filtered by line filters are indicated by a light-yellow but do not show up in the diff overview or participate in keyboard navigation. The line filters are not able to filter all of the above WF4 issues as can be seen in the red change above. This is because the xml line is missing on one side rather than being just a change to the line. These changes to the xml still get picked up by the diff tool.

WinMerge stores the line filters in the registry. The easiest way to install them is to import the registry entry below.

[WinMerge Line Filters.reg (978.00 bytes)][4]

[0]: /2007/06/19/using-winmerge-with-tfs/
[1]: /files/image_93.png
[2]: /files/image_94.png
[3]: /files/image_95.png
[4]: /files/2011/3/WinMerge%20Line%20Filters.reg
