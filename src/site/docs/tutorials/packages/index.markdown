---
layout: default
title: "Target 5: Share Code with Packages"
description: "Bundle classes in packages to organize and share code"
has-permalinks: true
tutorial:
  id: packages
---

{% capture whats_the_point %}

* Packages are awesome.
* Packages are cool.
* Share your code in packages, with all your friends at school.

{% endcapture %}

{% capture content %}

Programmers can share code by bundling Dart source files,
and other resources together into packages.
The Dart SDK,
which is part of the Dart download,
provides many built-in packages for use in your Dart programs.
The Dart language and tools
also provide support for using external packages&mdash;those
not included with the Dart SDK.
To use an external package,
your application must itself be a package.

Dart's package manager, _pub_, lets you
create and use external packages
in your Dart programs.
This target shows you how to turn your application
into an _application package_
and then how to import an external package,
namely the web_components package.

<aside class="alert">
The web_components package can be found at
<a href="http://pub.dartlang.org/">pub.dartlang.org</a>,
along with some other interesting and useful packages
written by the Dart team and other Dart programmers.
</aside>

* [About the Dart SDK packages](#dart-sdk)
* [Create a new application with pub support](#new-app-with-pkg)

##About the Dart SDK packages {#dart-sdk}

The Dart SDK contains several build-in packages
that you can use in your Dart programs.
The dart:core library is imported into your Dart program automatically.
Other Dart libraries, like dart:html,
must be explicitly imported with the import directive.

{% highlight dart %}

import 'dart:html';

{% endhighlight %}

You need to import a library into each .dart source file that uses it.
Once imported,
all of the public functions, variables and classes
in the library are available for use that file.
Dart Editor analytics knows about imported libraries and uses
that information to provide warnings, errors, and code completion.

Here's a summary of the more generally useful libraries
included in the Dart SDK:

| Library | Stuff |
|---|---|
| dart:core | Contains standard types like strings, numbers, dates, and some skeletal collection classes. |
| dart:html | Provides classes necessary for web applications. |
| dart:math | Defines mathematical constants and implements some common mathematical functions. |
| dart:collection | Provides implementations for arrays, collections, and maps|
| dart:isolate | Contains interfaces for concurrency and security. |
{: .table}

The libraries in the Dart SDK are built-in
to the Dart system
so they can be easily imported using the special dart: prefix.
External libraries require more preparation to use.

##Create a new application with pub support {#new-app-with-pkg}

Start Dart Editor and bring up the **New Application** window.
Use _helloworldtoday_ for the application name.
Be sure to select **Add pub support**.

![Select **Add pub support** to use packages](images/create-hwtoday.svg)

Click **Finish** and you will see the following directory
in the **Files view** in Dart Editor.

![An application directory created with pub support](images/hwtoday-files.svg)

{% endcapture %}

{% include tutorial.html %}
