---
title: TFS Build Remote Database Deployment Pain
tags : TFS
date: 2012-11-02 13:43:00 +10:00
---






winrm set winrm/config/winrs `@`{MaxMemoryPerShellMB =`"512`"`}

restart-service winrm
{% endhighlight %}
