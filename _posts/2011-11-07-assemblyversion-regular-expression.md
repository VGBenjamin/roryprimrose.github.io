---
title: AssemblyVersion regular expression
categories : .Net
tags : TFS
date: 2011-11-07 11:40:36 +10:00
---


* Major version is required

^
# Major version must exist
(?<VersionPart>\d+)
(
  # Minor only supports numbers
  \.(?<VersionPart>\d+)

  (\.
    (
      # Build can be *
      (?<VersionPart>\*)
      |
      # or a number
      (
        (?<VersionPart>\d+)

        # with optional Revision that may be * or numeric
        (\.(?<VersionPart>\*|\d+))?
      )
    )
  )? # Build.Revision is optional
)?$ # Minor.Build.Revision is optional
{% endhighlight %}


^(?<VersionPart>\d+)(\.(?<VersionPart>\d+)(\.((?<VersionPart>\*)|((?<VersionPart>\d+)(\.(?<VersionPart>\*|\d+))?)))?)?$
{% endhighlight %}

Enjoy.