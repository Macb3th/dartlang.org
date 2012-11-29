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

Now that you're are able to create and run a Dart application
and have a basic understanding of DOM programming,
you are ready to leverage code written by other programmers.
Many interesting and useful packages of reusable Dart code
are available at the
<a href="http://pub.dartlang.org/">pub.dartlang.org</a>
repository.

This target shows you how to use Dart's package manager
to install one of the packages in the repository,
the vector_math package.
You can follow these same steps to install any package hosted at
<a href="http://pub.dartlang.org/">pub.dartlang.org</a>;
just change the package name when you get to that step.
This target also describes some of the resources you can expect to find
in a well-built package.

* [Create a new application within a package](#new-app-with-pkg)
* [... Or, put an existing application into a package](#old-app-in-pkg)
* [Name the package dependences](#name-dependencies)
* [Install the package dependences](#install-dependencies)
* [What did you get (and not get)?](#about-packages)
* [Import libraries from a package](#use-package)

##Create a new application within a package {#new-app-with-pkg}

To use an external package,
your application must itself be a package.
You can create an application and its package together
from the New Application window in Dart Editor.

Start Dart Editor and bring up the **New Application** window.
Use vector_victor for the application name.
Select **Add pub support** to make Dart Editor
generate basic package support.
Click **Finish**.

![Select **Add pub support** to use packages](images/create-victor.png)

Dart Editor creates a new directory with boilerplate files.
Notice that the directory contains a new kind of file:
the `pubspec.yaml` file.
Double click pubspec.yaml to view its contents.

![Dart Editor with pubspec.yaml file](images/victor-files.png)

It is this file that makes the vector_victor directory a package.
This file contains the package specification written in YAML.
At minimum, the pubspec provides a name for the package.
It also can provide a description and identify packages on
which this package is dependent.

![The default pubspec.yaml file specifies name and description](images/pubspec.png)

Any application with a valid pubspec.yaml file in its top-level directory
is a package and can therefore use external packages.

An application package contains everything required
by an application to run.
The code is not intended to be reused by other programmers.
A library package contains code, libraries,
tools, and resources intended to be shared and reused by others.
To use a library package,
an application must be in an application package.

##...Or put an existing application into a package {#old-app-in-pkg}

If you already have an application
and want it to use an external package,
simply create a pubspec.yaml file in the application's top-level directory.
Your pubspec.yaml file must at least specify the package name.

![The smallest possible pubspec.yaml](images/minimalpubspec.png)

<aside class="alert">
<strong>Tip:</strong> If you are using
Dart Editor to create the pubspec.yaml file,
you might get an error message
when you first create the empty pubspec.yaml file.
This is because the package manager runs automatically and
is trying to resolve the package specification file,
which at first has nothing in it.
Ignore the message,
add the required name field,
and save the pubspec.yaml file.
</aside>

##Name the package dependences {#name-dependencies}

To use an external library package,
include it in a list of _dependencies_ in the pubspec.yaml file.
Each item in the dependencies list
specifies the name, and sometimes the version,
of a package that your application uses.

To make vector_victor dependent on
the vector_math package,
modify the pubspec.yaml file as shown below.
Be sure to remove the hash marks (#) so that
the dependencies list is not commented out.

![A pubspec with dependency on the vector_math package](images/pubspec-vectormath.png)

`any` means that this application can use
any version of the vector_math package.
You could instead specify a particular version of the package
and for a real application you should likely do so.

<a href="http://pub.dartlang.org/">pub.dartlang.org</a>
is the primary public repository for Dart packages.
Dart's package manager automatically checks that
website when resolving package dependencies.
So to use one of the libraries from that site,
you can specify it by its simple name,
as we have done here.

##Install the package dependences {#install-dependencies}

In Dart Editor, save pubspec.yaml with **File->Save**.
When you save the file,
Dart Editor automatically runs the package manager,
which recursively installs the Dart libraries
from the packages in the dependencies list.
You can also select **Pub Install** from the **Tools** menu in Dart Editor.

Pub install puts the installed libraries in a directory called packages
under the application's top-level directory.
Click the wee arrow to expand the packages directory.
There you will find the vector_math directory,
which contains the Dart libraries from the vector_math package.

![Pub Install finds and installs required packages](images/run-pub-install.png)

In addition,
you will notice the unittest directory;
unittest is another package in the repository.
vector_math depends on unittest
(unittest is listed in vector_math's dependencies list)
so package manager installed it as well.
Pub install works recursively and installs
all of the required packages
of your application and its dependencies.

The package manager also created a file called pubspec.lock,
which identifies the specific versions of the packages that were installed.
This helps to provide a stable development environment.
Later you can modify the version constraints and use `pub update`
to update to new versions as needed.

##What did you get (and not get)? {#about-packages}

Besides the Dart libraries,
the vector_math package has other resources that might be useful to you
that do not get installed into your application directory.

Let's take a step back for a moment to look at what
you got and where it came from.
Use your browser and go to
the github repository for the
<a href="https://github.com/johnmccutchan/DartVectorMath" target="_blank">
vector_math
</a>
package.
You will see a lot of files and directories there.
Only one of which, `lib`, was installed when you ran pub install.

<div>
  <hr>
  <div class="row">
    <div class="span2">
    <img src="images/libraries-folder.png"
         alt="Dart libraries directory"/>
    </div>
    <div class="span7">
      <em>Dart libraries</em>:
      The lib directory contains one or more Dart libraries,
      which can be imported into your Dart programs.
      <em>It is this directory that gets installed when you install a package.</em>
    </div>
  </div>
  <hr>
  <div class="row">
    <div class="span2">
    <img src="images/housekeeping-files.png"
         alt="Housekeeping files"/>
    </div>
    <div class="span7">
      <em>Housekeeping files</em>:
      When using an package written by someone else,
      the readme file is a good place to start.
      It should contain important information about the package,
      such as its intent, contents, samples, and instructions.
      The license file provides copyright and rules of use information.
      These files can be found at the package repository.
      They are not installed when you install a package.
    </div>
  </div>
  <hr>
  <div class="row">
    <div class="span2">
    <img src="images/other-folders.png"
         alt="Document, scripts, tests, and other resources"/>
    </div>
    <div class="span7">
      <em>Other resources</em>:
      Along with Dart libraries,
      a package might also contain other resources 
      such as example code, tests, scripts, and documentation.
      If a package contains these resources,
      they should be in the directories named as shown.
    </div>
  </div>
  <hr>
</div>

A set of
<a href="http://pub.dartlang.org/doc/package-layout.html">conventions</a>
govern the contents and organization of a package.
By following these conventions,
programmers make it easier for one another to learn
and quickly put to use the contents of a package.
Like other well-built packages,
the vector_math package includes resources organized and named
according to convention.

##Import libraries from a package {#use-package}

Open the vector_math directory by clicking the little arrow.

![Finally, the vector_math library files](images/the-vectormath-library.png)

The directory contains two Dart files,
each of which defines a different library.
Like the SDK libraries,
use the import directive to use code from an installed library.
Recall the following line of code that imports the dart HTML library:

{% highlight dart %}
import 'dart:html';
{% endhighlight %}

The Dart SDK libraries are built-in and
are identified with the special dart: prefix.
For libraries installed by the package manager,
use the `package:` prefix.

![Import a library installed from an external package](images/import-directive.png)

Note that you specify the filename not the library name.

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
  <a href="/docs/tutorials/web-components/" class="pull-right">Web Components <i class="icon-chevron-right"> </i> </a>
  </div>
</div>

{% endcapture %}

{% include tutorial.html %}
