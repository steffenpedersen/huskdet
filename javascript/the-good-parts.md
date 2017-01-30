# JavaScript: The Good Parts \(and other stuff\)

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

Når vi laver et nyt object, så kan vi vælge dets prototype. Vi kan tilføje en `create method` til object function. Denne `create method` laver et nyt object, som bruger et gammelt object til dets prototype.

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

Selve prototype link har ingen effekt ved updating. Når vi laver ændringer til et object, så bliver dets prototype ikke rørt:

```js
another_stooge['first-name'] = 'Harry';
another_stooge['middle-name'] = 'Moses';
another_stooge.nickname = 'Moe';
```

Prototype link er kun brugt til at hente. Hvis vi prøver at hente en property value fra et object og hvis object ikke har property name, så prøver JavaScript at få property value fra `prototype object`. Hvis object ikke har property, så går den til dets `prototype` og så videre; indtil at processen når bunden ved `Object.prototype`. Hvis den ønskede property slet ikke eksisterer, så vil resultatet ende med en `undefined value`. Dette hedder _delegation._ Selve prototype relationship er et dynamisk relationship. Hvis vi tilføjer en ny property til en prototype, så vil den property være synlig ved at objects, som er baseret på den prototype \(inheritance\).

```js
stooge.profession = 'actor';
another_stooge.profession // 'actor'
```

### Delete

Selve `delete` operator kan bruges til at fjerne en property fra et object - hvis den har en. Den vil ikke røre objects i `prototype`. Hvis man fjerner en property fra et object, så kan man måske få lov til at se `prototype`.

```js
another_stooge.nickname // 'Moe'
// Remove nickname from another_stooge, revealing
// the nickname of the prototype.

delete another_stooge.nickname;
another_stooge.nickname // 'Curly'
```

### Enumeration/iteration

Selve `for in statement` kan loop over alle property names i et object. Dette vil inkludere alle properties med functions og prototype properties, som vi ikke er interesseret i. Det vil derfor være en god idé at filtrere værdierne, som vi ikke vil have. Vi kan her bruge `hasOwnProperty` method og bruge `typeof` til at ekskludere functions.

```js
var name;
for (name in another_stooge) {
 if (typeof another_stooge[name] !== 'function') {
 document.writeln(name + ': ' + another_stooge[name]);
 }
}
```

Der er her ikke nogen garanti for rækkefølgen af navnene. Hvis vi vil sikre os en bestemt rækkefølge, så kan vi lave et array med navnene og bruge `for statement`.

```js
var i;
var properties = [
 'first-name',
 'middle-name',
 'last-name',
 'profession'
];
for (i = 0; i < properties.length; i += 1) {
 document.writeln(properties[i] + ': ' +
 another_stooge[properties[i]]);
}
```

## Booleans

Ofte vil man gerne bruge en værdi, som kan skelnes mellem to muligheder. Til dette kan man bruge en _Boolean _type, som har to værdier: true og false.

### Truthy

I JavaScript er truthy en værdi i forbindelse med Boolean, som kan oversættes til true. Alle værdier er truthy medmindre de er defineret som falsy \(dvs. medmindre for `false`, `0`, `""`, `null`, `undefined`, og `NaN`\).

Dette er eksempler af truthy værdier i JavaScript \(som vil oversætte til true og eksekvere if block\):

```js
if (true)
if ({})
if ([])
if (42)
if ("foo")
if (new Date())
if (-42)
if (3.14)
if (-3.14)
if (Infinity)
if (-Infinity)
```

### Falsy

I JavaScript er falsy en værdi i forbindelse med Boolean, som kan oversættes til false.

Dette er eksempler af falsy værdier i JavaScript \(som vil oversætte til false og eksekvere if block\):

```js
if (false)
if (null)
if (undefined)
if (0)
if (NaN)
if ('')
if ("")
if (document.all) [1] // browser detection in the past
```

## Functions

En function omslutter et sæt af statements. De bruges til at genbruge kode, gemme information og kompositionen. De bruges til at beskrive  opførelsen af objects.

### Function Objects

Functions i JavaScript er objects. Objects er en samling af name/value, som har et skjult link til et [prototype object](/javascript/the-good-parts.md "Se Objects > Prototype"). 







Functions in JavaScript are objects. Objects are collections of name/value pairs having a hidden link to a prototype object. Objects produced from object literals are linked to Object.prototype. Function objects are linked to Function.prototype \(which is itself linked to Object.prototype\). Every function is also created with two additional hidden properties: the function’s context and the code that implements the function’s behavior. 

Every function object is also created with a prototype property. Its value is an object with a constructor property whose value is the function. This is distinct from the hidden link to Function.prototype. The meaning of this convoluted construction will be revealed in the next chapter. 

Since functions are objects, they can be used like any other value. Functions can be stored in variables, objects, and arrays. Functions can be passed as arguments to functions, and functions can be returned from functions. Also, since functions are objects, functions can have methods. 

The thing that is special about functions is that they can be invoked.





* Booleans

  * **Truthy**

  * **Falsy**

* Objects

  * **Hvad er et object?**

  * **declare**

  * **update**

  * **remove / delete**

  * _iterate_

  * **reference**

  * **prototype**

Functions

* * Hvad er en function?

  * declarations

    * function expression

    * function declaration

  * invocation

  * Prototype



