---
title: Not all browsers are made equal - The JavaScript console
categories : .Net
tags : JavaScript
date: 2014-10-09 09:17:00 +10:00
---


(function () {
    if (!window.console) {
        window.console = {};
    }

    var outputFunctions = ["log", "trace", "info", "debug", "warn", "error"];
    var defaultFunction = function () { };

    // Find the first available default function
    for (var searchIndex = 0; searchIndex < outputFunctions.length; searchIndex++) {
        if (window.console[outputFunctions[searchIndex]]) {
            defaultFunction = window.console[outputFunctions[searchIndex]];

            break;
        }
    }

    // union of Chrome, FF, IE, and Safari console methods
    var m = [
      "log", "trace", "info", "debug", "warn", "error", "dir", "group",
      "groupCollapsed", "groupEnd", "table", "time", "timeEnd", "profile", "profileEnd",
      "dirxml", "assert", "count", "markTimeline", "timeStamp", "clear"
    ];
    // define undefined methods as noops to prevent errors
    for (var i = 0; i < m.length; i++) {
        if (!window.console[m[i]]) {
            window.console[m[i]] = defaultFunction;
        }
    }
})();

{% endhighlight %}

[0]: http://stackoverflow.com/a/13817235