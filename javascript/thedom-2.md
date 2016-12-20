# JavaScript and the DOM 2

### what is a callback function?

### what is a map\(\) method?

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



```js
function output(time) {
  var color = '#' + time;
  document.body.bgColor = color;
  document.body.textContent = color;
  document.body.style.color = 'white';
  document.body.style.height = '100vh';
}
```

...

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

...

```js
function init() {
  var tick = setInterval(function() { output(time()) }, 1000); // milliseconds
  stopClick(clearInterval, tick);
  startClick(init);
}

init();
```

...

![](/assets/dec.-20-2016 12-13-59.gif)

