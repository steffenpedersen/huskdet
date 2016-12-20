# JavaScript and the DOM 2

**A HEX CLOCK **

```js
function time() {
  var date = new Date();
  var hours = date.getHours();
  var minutes = date.getMinutes();
  var seconds = date.getSeconds();
  var arr = [hours, minutes, seconds].map(function(num) {
    return num < 10 ? '0' + num : String(num);
  });
  hours = arr[0];
  minutes = arr[1];
  seconds = arr[2];

  return hours + minutes + seconds;
}
```

Jeg definerer først en række variabler ud fra `Date` objektet og bruger dets methods. Jeg definerer et array og bruger `map() method`, som kalder en function én gang for hvert element i et array. Hvis et tal er under 10, så skal den sætte et `0`. Det er i strings.

> **Conditional\(ternary\)Operator**
>
> `condition ? expr1 : expr2`
>
> If condition is true, the operator returns the value of expr1; otherwise, it returns the value of expr2.
>
> The map\(\) method calls the provided function once for each element in an array, in order.

```js
function output(time) {
  var color = '#' + time;
  document.body.bgColor = color;
  document.body.textContent = color;
  document.body.style.color = 'white';
  document.body.style.height = '100vh';
}
```

Jeg laver en ny function og kalder den output med `time` som et parameter. Jeg definerer først color som en hex og bruger `document.body` til at angive indhold og styling.

```js
function startClick(callback) {
  document.body.addEventListener('dblclick', function(event) {
    callback();
  });
}

function stopClick(callback, name) {
  document.body.addEventListener('click', function(event) {
    callback(name);
  });
}
```

For at tilføje en smule interaktivitet vil jeg lave et startklik og et stopklik. Dette gør jeg med en `addEventListener` som lytter efter et klik eller et dobbeltklik.

> A callback function is executed after the current effect is 100% finished.
>
> JavaScript statements are executed line by line. However, with effects, the next line of code can be run even though the effect is not finished. This can create errors.
>
> To prevent this, you can create a callback function.

```js
function init() {
  var tick = setInterval(function() { output(time()) }, 1000); // milliseconds
  stopClick(clearInterval, tick);
  startClick(init);
}

init();
```

Her laver jeg en function, som samler det hele og jeg kalder derefter denne function. Jeg bruger `setInterval()` og `clearInterval()` methods.

> The setInterval\(\) method calls a function or evaluates an expression at specified intervals \(in milliseconds\).
>
> The setInterval\(\) method will continue calling the function until clearInterval\(\) is called, or the window is closed.
>
> Tip: 1000 ms = 1 second.

![](/assets/dec.-20-2016 12-13-59.gif)

