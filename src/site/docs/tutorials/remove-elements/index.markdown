---
layout: default
title: "Target 4: Remove an Element from the DOM"
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

In this short target,
you will modify the todo app
to allow the user to delete items from the list.
When the user hovers the mouse over an item,
it changes its appearance.
When the user clicks the item,
the Dart program removes the item from the DOM.

* [Copy and run the new todo app](#copy-app)
* [Removing an element from the DOM tree](#remove-elem)

##Copy and run the new todo app {#copy-app}

Use the following links to
copy the HTML, Dart, and CSS code
into a new web app in Dart Editor.
Name the app todo and make sure the filenames
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
For example, the diagram shows the app after
_dance_, _sing_, _walk the dog_, and _laugh_ have all been entered.

![todo app with a several items in the list](images/todo-with-items.png)

Hover the mouse over one of the items in the list.
Its appearances changes.
The text is now red and the font is slightly larger.

![todo app with hovering mouse](images/todo-with-hover.png)

Click the red item
and it disappears from the list.

##Removing an element from the DOM tree {#remove-elem}


[xx: talk about the event argument to the handler,
talk about not removing an item from the list,
but from Element,
perhaps even talk about why we don't have to do boundary checking,
talk about why seemingly useless interim assignment to a var]

The todo app needs to
listen for click events
and respond to those events by removing an item in the list.

![Dart code for removing an item](images/remove-dart-code.png)

In the Dart file,
register an event handler on each new item
when it is added to the list.
Within the function that handles the event,
remove the item.

To signal to the user that something irreversible is about to happen,
the todo app displays the list item
in red in a larger font when the mouse hovers over it.
This change is made in the CSS file.

{% highlight dart %}
#to-do-list li {
  padding:5px 0px 5px 5px;
  border-bottom: 1px dotted #ccc;
}
{% endhighlight %}





{% endcapture %}

{% include tutorial.html %}
