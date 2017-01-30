# JavaScript: The Good Parts

## Objects

De simple typer i JavaScript er numbers, strings, booleans, null og undefined. Alle andre værdier er objects. Numbers, strings og booleans er object-like, da de har methods, men er immutable\(uforanderlig\). I JavaScript, arrays er objects, functions er objects, regular expressions er objects og objects er objects.

Et object er en container af properties, hvor en property har et navn og en værdi. Et navn på en property kan være en string eller en tom string. En værdi til en property kan være alle værdier i JavaScript pånær undefined.

Objects i JavaScript er class-free. Der er ikke nogen contraint\(begrænsning\) på navnet eller værdien af properties. Objects er brugbare for at indsamle og organisere data. Objects kan indeholde andre objects, så de kan nemt repræsentere et hierarki som et træ. 

JavaScript inkluderer en prototype linkage\(kobling/forbindelse\), som tillader et object at nedarve properties fra et andet object. Når kan eliminere tidsforbrug og hukommelse/plads.

### Object Literals\(konstant\)

En object literal\(\)konstant er et par af curly braces\(tuborgklammer\), som omfavner nul eller flere name/value.

```js
var empty_object = {};

var stooge = {
 "first-name": "Jerome",
 "last-name": "Howard"
};
```

### Update

En værdi i et object kan blive opdateret. Hvis navnet til property allerede eksisterer i object, så kan det erstattes således:

```js
stooge['first-name'] = 'Jerome';
```

Hvis object ikke allerede har navnet til property:

```js
stooge['middle-name'] = 'Lester';
stooge.nickname = 'Curly';
flight.equipment = {
 model: 'Boeing 777'
};
flight.status = 'overdue';
```

### Reference

Objects bliver gentaget som en reference. De må aldrig kopieres.

```js
var x = stooge;
x.nickname = 'Curly';
var nick = stooge.nickname;
 // nick is 'Curly' because x and stooge
 // are references to the same object
var a = {}, b = {}, c = {};
 // a, b, and c each refer to a
 // different empty object
a = b = c = {};
 // a, b, and c all refer to
 // the same empty object
```

### Prototype

Alle objects er linket til et prototype object, hvor den kan nedarve properties. Alle objects som er lavet fra object literals\(konstant\) er linket til `Object.prototype` , som er en standard fra JavaScript.





_When youmake a new object, youcan select the object that should be its prototype. The mechanism that JavaScript provides to do this is messy and complex, but it can be significantly simplified. We will add a create method to the Object function. The create method creates a new object that uses an old object as its prototype. There will be much more about functions in the next chapter._

```js
if (typeof Object.create !== 'function') {
 Object.create = function (o) {
  var F = function () {};
  F.prototype = o;
  return new F();
 };
}
var another_stooge = Object.create(stooge);
```



```js
another_stooge['first-name'] = 'Harry';
another_stooge['middle-name'] = 'Moses';
another_stooge.nickname = 'Moe';
```



```js
stooge.profession = 'actor';
another_stooge.profession // 'actor'
```



## Functions

En function omslutter et sæt af statements. De bruges til at genbruge kode, gemme information og kompositionen. De bruges til at beskrive skrive opførelsen af objects. 

### Function Objects

Functions i JavaScript er objects. Objects er en collection af... 







* Booleans

  * Truthy

  * Falsy

* Objects

  * **Hvad er et object?**

  * **declare**

  * **update**

  * remove / delete

  * iterate

  * **reference**

  * prototype

Functions

* * Hvad er en function?

  * declarations

    * function expression

    * function declaration

  * invocation

  * Prototype

```js
document.write("Hello");
```



