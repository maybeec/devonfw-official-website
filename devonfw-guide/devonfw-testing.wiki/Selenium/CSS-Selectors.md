
**PLEASE HAVE A LOOK on this doc. Maybe it would be worth to reedit it to wiki format:**
[cssSelector.docx](documentation/cssSelector.docx)

***



The css selector is used to select elements from the HTML page.

Selection by element, class or id are the most common selectors.

	<p class='myText' id='123'>

This text element (p) can be  found by using any one of the following selectors:

    The HTML element: "p". Note: in practical use this will be too generic, if a preceding text section is added, the selected element will change.
    The class attribute preceded by ".": ".myText"
    The id attribute preceded by "#": "#123"

Using other attributes
-------
When a class or id attribute is not sufficient to identify the other attributes can be used as well, by using "[attribute=value]":
For example:

	<a href='https://ns.nl/example.html'>

Can be selected by using the entire value: "a\[href='https://ns.nl/example.html'\]". For selecting links starting with, containing, ending with see the list below.

Using sub-elements
-------
The css selectors can be stacked, by appending them:

	<div id='1'><a href='ns.nl'></div>
	<div id='2'><a href='nsinternational.nl'></div>

In the example above, the link element to nsinternational can be obtained by: "#2 a".

When possible avoid
-------
* Using paths of commonly used HTML elements within the containers (HTML: div). This will cause failures when a container is added, a common occurrence during development. E.g.: "div div p". Use class or id instead, if those are not available, request them to be added in the production code.
* Magic order numbers. It is possible to get the second text element in its contained by using selector "p:nth-child(2)". If the items are representing different items, ask the developer to add specific attributes, it is possible to request all items and iterated later, with a selector similar to ".myList li". <Add example>.

List
-------
A good list with CSS Selectors can be found at W3Schools; https://www.w3schools.com/cssref/css_selectors.asp