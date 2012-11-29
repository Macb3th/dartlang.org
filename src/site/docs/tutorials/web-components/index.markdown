---
layout: default
title: "Start Using Web Components"
description: "Use one-way data binding"
has-permalinks: true
tutorial:
  id: web-components
---

{% capture whats_the_point %}

* Put dynamic information using one-way data binding

{% endcapture %}

{% capture content %}

{% comment %}
Of particular interest is the web_components package,
which contains the resources for creating encapsulated,
reusable views&mdash;a powerful tool for building larger web applications.
{% endcomment %}

1. Start with example from previous target
2. create build.dart file
3. run build.dart
    what do you get?
4. copy stuff into helloworldtoday.dart
5. et voila, run the bloody thing.

##Use web_components one-way data binding {#use-one-way}

Let's use one-way data binding from the web_components package to
check that the packages are set up correctly.

You can ignore or delete helloworldtoday.dart.
The Dart code will be embedded directly in the HTML file.

Edit helloworldtoday.html, delete the boilerplate code,
and copy this code in full:

{% highlight html %}
<!DOCTYPE html>
<!--
Copyright (c) 2012, the Dart project authors.  Please see the AUTHORS file
for details. All rights reserved. Use of this source code is governed by a
BSD-style license that can be found in the LICENSE file.
-->
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <link rel="stylesheet"
  href="http://twitter.github.com/bootstrap/assets/css/bootstrap.css">
</head>
<body>
  <div class="well">Hello {{dataValue}}!</div>
  <script type="application/dart">
    String dataValue;
    main() {
      var today = new Date.now();
      dataValue = 'world ${today.year}-${today.month}-${today.day}';
    }
  </script>
</body>
</html>
{% endhighlight %}

<div class="row">
  <div class="span3">
  <a href="/docs/tutorials/packages/"><i class="icon-chevron-left"> </i> Install Shared Packages</a>
  </div>
  <div class="span3">
<a href="http://code.google.com/p/dart/issues/entry?template=Tutorial%20feedback"
 target="_blank">
<i class="icon-comment"> </i>
Send feedback
</a>
  </div>
  <div class="span3">
  <a href="/docs/tutorials/" class="pull-right">Home <i class="icon-chevron-right"> </i> </a>
  </div>
</div>

{% endcapture %}

{% include tutorial.html %}
