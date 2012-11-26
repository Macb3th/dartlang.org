---
layout: default
title: "Target 5: Install Shared Packages"
description: "Packages are bundles of source code, tools, and resources that help you to organize and share code"
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

Programmers can share code by bundling Dart code, libraries,
tools, and other resources together into packages.
Dart's package manager, _pub_, helps you to
create, use, share, and manage packages
(including versioning and dependencies).

To use a package,
your application must itself be a package.
So this target will first show you how to create an application package,
and then how to use an external package&mdash;in our example,
the Dart web_components package, which can be found at
<a href="http://pub.dartlang.org/">pub.dartlang.org</a>.
That webside includes many other interesting and useful packages
written by the Dart team and other Dart programmers.

* [Create a new application package](#new-app-with-pkg)
* [... Or, put an existing application into a package](#old-app-in-pkg)
* [Name the package dependences](#name-dependencies)
* [Install the package dependences](#install-dependencies)
* [Use the package](#use-package)

##Create a new application package {#new-app-with-pkg}

Start Dart Editor and bring up the **New Application** window.
Use _helloworldtoday_ for the application name.
Select **Add pub support** to make Dart Editor
generate basic package support.

![Select **Add pub support** to use packages](images/create-hwtoday.png)

Click **Finish**.
Dart Editor creates a new application directory
with boilerplate files.
The application files with the basename helloworldtoday
should be familiar; they implement the clickme application.
New is the file pubspec.yaml,
which contains the package specification.

Double click pubspec.yaml to view its contents.

![Dart Editor with pubspec.yaml file](images/hwtoday-files.png)

Each package must have one pubspec.yaml file
written in the YAML language.
At minimum, the pubspec provides a name for the package.
It also can provide a description and identify packages on
which this package is dependent.

![The default pubspec.yaml file specifies name and description](images/pubspec.png)

Any application with a valid pubspec.yaml file is a package
and can therefore use external packages.

##...Or put an existing application into a package {#old-app-in-pkg}

If you already have an application
and want it to use an external package,
simply create a pubspec.yaml file in the application's top-level directory.
Your pubspec.yaml file must have a line specifying the package name.

![The smallest possible pubspec.yaml](images/minimalpubspec.png)

When you first create the empty pubspec.yaml file in Dart Editor,
you will get an error message,
because the package manager runs automatically and
is trying to resolve the package specification file,
which has nothing in it.
Ignore the message,
add the required name field,
and save the pubspec.yaml file.

##Name the package dependences {#name-dependencies}

To use an external package from 
<a href="http://pub.dartlang.org/">pub.dartlang.org</a>,
you just need to set a dependency on the package.
Dart's package manager automatically checks that
website when resolving package dependencies.
The helloworldtoday sample will use the web_components package,
so modify the pubspec.yaml file
to set a dependency on the web_components package:

![A pubspec with dependency on web_components package](images/pubspec-webcomponents.png)

##Install the package dependences {#install-dependencies}

In Dart Editor, save pubspec.yaml with **File->Save**.
When you save the file,
Dart Editor automatically runs the package manager to install
the packages specified in the dependencies list.
You can also select **Pub Install** from the **Tools** menu in Dart Editor.

![Pub Install finds and installs required packages](images/run-pub-install.png)

Pub install creates a directory called packages,
locates the packages on which your package depends,
and installs them.
In addition, pub install
recursively installs the packages on which those depend.
So by getting web_components,
your application package also gets the unittest, js, and other packages.

The package manager also creates a file called pubspec.lock,
which lists the specific versions of the packages that were installed.
This helps to provide a stable development environment.
You can specify version dependencies and update them as necessary.

##Use the package {#use-package}

Now that the required packages are installed,
you can use the resources contained in the packages
in your application.

To use Dart code from an external packages,
use the import directive.
For example,
to use classes and functions from the web_components package,
you could write the following:

{% highlight dart %}
import 'package:web_components/web_components.dart'
{% endhighlight %}

The next target shows you how to use some of the features
from the web_components package.

<div class="row">
  <div class="span3">
  <a href="/docs/tutorials/remove-elements/"><i class="icon-chevron-left"> </i> Remove Elements</a>
  </div>
  <div class="span3">
<a href="http://code.google.com/p/dart/issues/entry?template=Tutorial%20feedback"
 target="_blank">
<i class="icon-comment"> </i>
Send feedback
</a>
  </div>
  <div class="span3">
  <a href="/docs/tutorials/web-components" class="pull-right">Web Components <i class="icon-chevron-right"> </i> </a>
  </div>
</div>

{% endcapture %}

{% include tutorial.html %}
