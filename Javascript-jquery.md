# jQuery

jQuery Cheatsheet: http://overapi.com/jquery/

<br>
## The DOM

**= Document Object Model**.
The content from the HTML file transfers slowly into the DOM every time a page is loading.
The DOM is a tree with nodes. E.g. the "html" node is a child of the "document" node; and in case of: ``<h1>Hallo!</h1>``, the "Hallo!"-text-node is a child of the h1-element-node.

<br>
## Selecting/Traversing elements

When working with jQuery, the first thing that need to get done is to SEARCH for the element you want to used. To find h1, you write ``jquery("h1")``, which is the same as ``$("h1")``.

If we want to search for/select the text-element in h1, we write ``$("h1").text();``. That gives back: "Hallo!". To change this text, we can write: ``$("h1").text("Tschüss!");``. Now, "Hallo!" became "Tschüss!".

BUT: We want to make sure that the whole DOM is loaded before we search for elements. That's why we select the whole document-element and wait for the signal if it's ready. Only then we fire up the code:

```javascript
$(document).ready(function() {
    $("h1").text("Tschüss!");
});
```
**Traversing** is very similar, only that it consists out of a selector and a traversal (e.g. ``$("#thatsanid").find("li")``). Traversing takes more code, but is faster.



| Code | Selecting |
| --- | --- |
| ``$(".classyeah")``  | selecting a certain class |
| ``$("#thatsanid")`` | selecting a certain ID |
| ``$("#thatsanid, .classyeah")`` | selecting multiple things |
| ``$("#thatsanid li")`` = ``$("#thatsanid").find("li")``| selecting all list elements in a certain ID |
| ``$("#thatsanid > li")`` = ``$("#thatsanid").children("li")``  | selecting all direct-child list elements in a certain ID (not the subchild list elements!) |
| ``$("#thatsanid li:first")`` = ``$("#thatsanid").first()`` | selecting the first list element in a certain ID |
| ``$("#thatsanid li:last")`` | selecting the last list element in a certain ID |
| ``$("#thatsanid li:even")`` | selecting all even list elements in a certain ID |
| ``$("li").first().next()`` | selecting the 2nd list element
| ``$("li").first().parent()`` | traversing up to get the parent element (e.g. a unordered list)

<br>
## Manipulating the DOM

When you want to manipulate some element in the DOM, you first have to append a new DOM element and then remove the old DOM element you want to manipulate.

E.g. we have a button that says: "Show Price", and we want it to show the price itself when we click on it.
For that, we append the price:

```javascript
$(document).ready(function() {

//creates a node, but doesn't add it to the DOM yet):
var price = $("<p>399.99 Euro</p>");

//appends price var to the ID vacation:
$("#vacation").append(price);
//can be written as the following, too:
price.appendTo($("#vacation"));

//removes the node <button> from the DOM:
$("button").remove();

}
```

| Ways to append | 1:0 |
| -- | -- |
| ``.append(<element>)`` | appends element after all the other elements in a class |
| ``.prepend(<element>)`` | appends element before all the other elements in a class |
| ``.after(<element>)`` | appends element after the whole class |
| ``.before(<element>)`` | appends element before the whole class |
See more here: http://api.jquery.com/category/manipulation/

<br>
## Events

- Mouse Events: http://api.jquery.com/category/events/mouse-events/
- Keyboard Events: http://api.jquery.com/category/events/keyboard-events/
-Event Handler Attachment: http://api.jquery.com/category/events/event-handler-attachment/

```javascript
$("button").on("click",function() {
 ...e.g. appending and removing nodes
}

// $("button")    > WHAT should be acted upon?
// on             > WHAT should happen?
//                > = Event Handler Attachment
// ("click")      > HOW should be acted upon?
//                > = Mouse/Keyboard Event
// function() {}  > What should happen after the interaction?

// other option:
$("#vacation").on("click","button", function() {
 ...e.g. appending and removing nodes
}
// only acts upon buttons in the ID vacation
```

If something has more than one button, ``$(this).closest("someElement")`` finds the button that was clicked on and only changes this button:

```javascript
$("button").on("click",function() {
 var price = $("<p>399.99 Euro</p>");
 $(this).closest("#vacation").append(price);
 $(this).remove();
}

```
<bR>
## Filtering

1. give classes in HTML a certain class-name (e.g. "notForSale" and "Sale"
2. filter all classes: ``$("#vacation").filter(".Sale")``
3. add a class for all filtered events: ``.addClass("highlighted")`` (http://api.jquery.com/category/manipulation/class-attribute/) and do something with it
4. add a ``removeClass("highlighted")`` before the code block, so that it doesn't stay highlighted.

<br>
### Styling

```javascript
$( "#myDiv" ).css( "border", "3px solid red" );
```
