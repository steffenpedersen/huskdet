# JavaScript and the DOM

With the HTML DOM, JavaScript can access and change all the elements of an HTML document.

### The HTML DOM \(Document Object Model\)

When a web page is loaded, the browser creates a **Document Object Model** of the page.

The **HTML DOM** model is constructed as a tree of **Objects**:

![](/assets/pic_htmltree.gif)

**OBJECTS**

I have described what an object is in Vanilla JS. Here I create a variable with an object. I accesses it and change the value. 

```js
var object = {
  name: 'Steffen',
  address: {
    country: 'Denmark'
  }
};

// Access Object Data
var myName = object.name;
var myCountry = object.address.country;

document.write(myName + "<br>");
document.write(myCountry + "<br>");

// Change Object Data
object.address.country = 'Sweden';

var myNewCountry = object.address.country;
document.write(myNewCountry + "<br>");
```

![](/assets/Skærmbillede 2016-12-15 kl. 14.27.52.png)

**DOM FUNCTIONS**

Here I create a heading and throws it on the page.

```js
// Create a heading tag 
var heading = document.createElement('H3');

// Add text to heading
heading.textContent = 'The DOM is the bomb!';

// Add text to body
document.body.appendChild(heading);
```

![](/assets/Skærmbillede 2016-12-15 kl. 14.29.52.png)

**EVENT LISTENERS**

```js
// Create DIV Element
var div = document.createElement('DIV');

// Add height to Element
div.style.height = '500px';
div.style.border = '1px solid #e5e5e5';

// Append Element to DOM
document.body.appendChild(div); 

// Add Event Listener
div.addEventListener('mousemove', function(event) {
  console.log(event);
  var x = event.clientX;
  var y = event.clientY;
  div.textContent = x + ', ' + y;
  div.style.backgroundColor = 'rgb(' + x + ', ' + y + ', 100)';
});
```

![](/assets/dec.-15-2016 14-22-40.gif)

**BETTER CODE**

```js
function theElement(element) {
  var newElement = document.createElement(element);
  newElement.style.height = '500px';
  newElement.style.border = '1px solid #e5e5e5';
  document.body.appendChild(newElement);
  return newElement;
}

function input(inputEvent, DOMElement, callback) { //mousemove, div, asynchronous
  DOMElement.addEventListener(inputEvent, function(event) {
    var x = event.clientX;
    var y = event.clientY;
    callback(DOMElement, x, y);
  });
}

function output(element, x, y) {
  element.textContent = x + ', ' + y;
  element.style.backgroundColor = 'rgb(' + x + ', ' + y + ', 100)';
}

input('click', theElement('DIV'), output);
// Change 'click' to 'mousemove'
```

![](/assets/dec.-15-2016 14-24-25.gif)

```js
document.write("Hello");
```



