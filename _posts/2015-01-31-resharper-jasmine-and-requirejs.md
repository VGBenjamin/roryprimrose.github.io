---
title: ReSharper Jasmine and RequireJS
categories : Development
date: 2015-01-31 09:22:00 +10:00
---


/// <reference path='/../../MyWebsite/Scripts/require.js'/>
/// <reference path='/../../MyWebsite/Scripts/Custom/ResponseParser.js'/>

describe('ResponseParser', function () {

    var target;

    beforeEach(function (done) {
        if (target) {
            done();

            return;
        }

        require(['ResponseParser'], function (parser) {
            target = parser;
            done();
        });
    });

    it('parse - returns empty set when data is null', function () {
        console.log('describe');

        var actual = target.parse(null);

        expect(actual).not.toBeNull();
        expect(actual.length).toBe(0);
    });

});
{% endhighlight %}