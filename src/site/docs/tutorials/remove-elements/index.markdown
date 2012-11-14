---
layout: default
title: "Target 4: Remove Elements from the DOM"
description: "Remove a child element from the DOM"
has-permalinks: true
tutorial:
  id: remove-elements
---

{% capture whats_the_point %}

* Use the remove() function in the Element class.
* Learn some CSS.

{% endcapture %}

{% capture content %}

This target focuses on a modified version of the todo app
that allows the users to delete items from the list.
When the user hovers the mouse over an item,
the item changes its appearance.
When the user clicks the item,
the Dart program removes the item from the list
(by removing it from the DOM).
Also, the program has a **Delete All** button
for removing all items from the list.

* [Copy and run the new todo app](#copy-app)
* [Changing the appearance during mouse hover](#css-hover)
* [Removing elements from the DOM tree](#remove-elem)

##Copy and run the new todo app {#copy-app}

Use the following links to
copy the HTML, Dart, and CSS code
into a new web app in Dart Editor.
Name the app todo-with-delete and make sure the filenames
are the same as those listed here.

<ul>
  <li>
<a href="http://raw.github.com/dart-lang/dart-tutorials-samples/master/web/target04/todo/todo-with-delete.dart"
   target="_blank">todo-with-delete.dart</a>
 </li>
  <li>
<a href="http://raw.github.com/dart-lang/dart-tutorials-samples/master/web/target04/todo/todo-with-delete.html"
   target="_blank">todo-with-delete.html</a>
 </li>
  <li>
<a href="http://raw.github.com/dart-lang/dart-tutorials-samples/master/web/target04/todo/todo-with-delete.css"
   target="_blank">todo-with-delete.css</a>
 </li>
 </ul>

Then run the app.
Enter a few items into the input field.
The following diagram shows the app after
_dance_, _sing_, _walk the dog_, and _laugh_ have all been entered.

![Entering items into the todo app](images/enter-items.png)

Hover the mouse over one of the items in the list.
Its appearances changes;
the text is now red and the font is slightly larger.
Also, the cursor changes to a pointer or a hand shape.
These visual clues signal to the user that something irreversible
will happen when they click on it.

Click the red item
and it disappears from the list.
The event handling and the DOM manipulation is controlled on the Dart side.

![Hover over an item then click to delete it](images/remove-an-item.png)

Use the **Delete All** button in the lower right corner of the app
to remove all of the items in the list at once.

![Click the Delete All button to remove all the todo items](images/remove-all.png)

The remaining sections describe
key aspects of the code 
added to the todo app for this target.
Specifically, it looks at
the Dart code that removes elements from the DOM
and one key rule in the CSS code.
You should familiarize yourself with the HTML code
that creates the **Delete All** button
and the CSS code that styles it.

##Changing the appearance during mouse hover {#css-hover}

As you saw, an item in the list turns red and gets bigger
when the user hovers the mouse over it.
The mouse cursor also changes shape.
These visual clues are an important part of the user interface
in this example because they are the only indication to the user
that something will happen when the item is clicked.

This behavior is coded in the todo app's CSS file with this rule:

{% highlight dart %}
#to-do-list li:hover {
  color: red;
  font-size: 18px;
  cursor:pointer;
}
{% endhighlight %}

We've used this CSS trick
instead of providing a familiar user interface,
such as a button with an 'X' on it,
to keep the code simpler.

##Removing elements from the DOM tree {#remove-elem}

The user clicks an item in the todo list to delete it.
The Dart code implements this behavior in two steps:

* it registers an event handler to respond to mouse clicks
* when called, the event handler removes the item from the list

This is all achieved with one line of code in the Dart side.
As you saw in the previous target,
for each new to do item typed in by the user,
the addToDoItem() function creates a new LIElement and adds it to the DOM.

Now,
the code also adds a function for handling mouse
clicks to the new element.
On a mouse click, the element removes itself from the DOM.

![Registering an event handler to delete an item](images/addToDoItem-with-delete.png)

Instead of using a function in the List class
to remove the element as you might expect,
this code uses the remove() function declared in Element.
Doing so makes the code shorter and more concise
because the element knows its location in the DOM 
and because the remove() function already implements the desired behavior;
it locates the element in the parent's list of children and removes it,
doing any error and boundary checks that are necessary.

When the element removes itself from the DOM,
the browser re-renders the page and the item in the todo list is gone.

###Removing all the items from the todo list

When the user clicks the **Delete All** button,
all elements are removed from the list.
Here's how.

<ol>
<li markdown="1">
The HTML code creates a button with the ID delete-all.
(The CSS styles it.)

{% highlight dart %}
<button id="delete-all" type="button" float:right> Delete All </button>
{% endhighlight %}

</li>

<li markdown="1">
The Dart code gets the button element from the DOM
and adds a mouse click handler to the button
that removes all of the child elements from the UListElement.
clear() is a function defined in the List class.
Here's all of the Dart code related to the **Delete All** button.

{% highlight dart %}
import 'dart:html';
...
ButtonElement deleteAll;

void main() {}
...
  deleteAll = query('#delete-all');
  deleteAll.on.click.add((e) => toDoList.elements.clear());
}
...
{% endhighlight %}

</li>
</ol>

<div class="row">
  <div class="span3">
  <a href="/docs/tutorials/add-elements/"><i class="icon-chevron-left"> </i> Add an Element to the DOM</a>
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
