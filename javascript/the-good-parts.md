# JavaScript: The Good Parts \(and other stuff\)

## Methods

Når en function er udført på en property af et object, så kaldes det for en method. Når en method bliver kaldt, så er den bundet til dette object. Dette kan blive gjort gennem dot notation. Vi kan på denne måde få værdier fra object eller ændre object.

```js
// Create myObject. It has a value and an increment
// method. The increment method takes an optional
// parameter. If the argument is not a number, then 1
// is used as the default.
var myObject = {
 value: 0,
 increment: function (inc) {
 this.value += typeof inc === 'number' ? inc : 1;
 }
};
myObject.increment( );
document.writeln(myObject.value); // 1
myObject.increment(2);
document.writeln(myObject.value); // 3
```

A method can use this to access the object so that it can retrieve values from the object or modify the object. The binding of this to the object happens at invocation time. This very late binding makes functions that use this highly reusable. Methods that get their object context from this are called public methods.

## Objects

De simple typer i JavaScript er numbers, strings, booleans, null og undefined. Alle andre værdier er objects. Numbers, strings og booleans er object-like, da de har methods, men er immutable\(uforanderlig\). I JavaScript, arrays er objects, functions er objects, regular expressions er objects og objects er objects.

Et object er en container af properties, hvor en property har et navn og en værdi. Et navn på en property kan være en string eller en tom string. En værdi til en property kan være alle værdier i JavaScript pånær undefined.

Objects i JavaScript er class-free. Der er ikke nogen contraint\(begrænsning\) på navnet eller værdien af properties. Objects er brugbare for at indsamle og organisere data. Objects kan indeholde andre objects, så de kan nemt repræsentere et hierarki som et træ.

JavaScript inkluderer en prototype linkage\(kobling/forbindelse\), som tillader et object at nedarve properties fra et andet object. Når kan eliminere tidsforbrug og hukommelse/plads.

### Object Literals \(konstant\)

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

### Prototype: Eksempel 1

Her laver vi en function, som log'er `this.sound`. Vi laver object animal med property talk med funktionen talk. Object cat og dog har property sound med værdi "meow" og "woof". Vi bruger `Object.setPrototypeOf()` til at nedarve object animal. Ved object angryDog nedarver vi fra object dog. Ved `animal.talk` tilføjer ved tekst til property `talk`.

`animal` er derfor prototype til `cat` og `dog` - `animal` og `dog` er prototype til `angryDog`

```js
function talk() {
  console.log(this.sound);
}
let animal = {
  talk: talk
}
let cat = {
  sound: "meow"
}
let dog = {
  sound: "woof"
}
let angryDog = {
  howl: function() {
    console.log(this.sound.toUpperCase());
  }
}
animal.talk = function() {
  console.log("I am a little " + this.sound);
}
Object.setPrototypeOf(cat, animal);
cat.talk()
Object.setPrototypeOf(dog, animal);
dog.talk()
Object.setPrototypeOf(angryDog, dog);
angryDog.howl()
```

![](/assets/import.png)

### Prototype: Eksempel 2.1

Vi laver et object med const, da vi ikke skal ændre den senere. Derefter laver vi en init method, som tager en type. Vi tilføjer denne type til en property. Vi laver en eat method, som log'er tekst og this.type.

Med Object.create kan vi lave nye objects af food.

```js
const food = {
  init: function (type) {
    this.type = type
  },
  eat: function() {
    console.log("you ate the " + this.type);
  }
}

const waffle = Object.create(food)
waffle.init("waffle")
waffle.eat()

const carrot = Object.create(food)
carrot.init("carrot")
carrot.eat()
```

![](/assets/import1.png)

### Prototype: Eksempel 2.2

`waffle` og `carrot` har `food` som sin prototype. `Object.create` laver et nyt object og tilføjer `food` som prototype. `waffle` og `carrot` vil kun falde tilbage til `food`, hvis den mangler sin property. Hvis den har sin property, så vil den selvfølgelig bruge den.

I dette tilfælde vil den ikke falde tilbage på `food.type`. Det vil den dog gøre, hvis vi udkommenterer `waffle.init()`.

```js
const food = {
  init: function (type) {
    this.type = type
  },
  eat: function() {
    console.log("you ate the " + this.type);
  }
}

const waffle = Object.create(food)
waffle.init("waffle")
waffle.eat()
food.type = "fuyfiuhiuhjojphoihohog"
waffle.eat()
```

![](/assets/import2.png)

```js
//waffle.init("waffle")
//waffle.eat()
```

![](/assets/import3.png)

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

Ofte vil man gerne bruge en værdi, som kan skelnes mellem to muligheder. Til dette kan man bruge en \_Boolean \_type, som har to værdier: true og false.

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

Functions i JavaScript er objects. Objects er en samling af name/value, som har et skjult link til et [prototype object](/javascript/the-good-parts.md "Se Objects > Prototype"). Function objects er linket til Function.prototype, som selv er linket til Object.prototype. Alle functions har to skjulte properties, som er function's context og koden, som implementerer funktionens adfærd.

Alle function objects er lavet med en prototype property. [JavaScript: The Good Parts s. 26](http://bdcampbell.net/javascript/book/javascript_the_good_parts.pdf)

...

Det specielle med functions er at de kan kaldes.

### Function Literal \(konstant\)

Function objects er defineret med function literals:

Function objects are created with function literals:

```js
// Create a variable called add and store a function
// in it that adds two numbers.
var add = function (a, b) {
 return a + b;
};
```

En function literal har fire dele.

Den **første del** er ordet function. Den valgfrie **anden del** er funktionens navn. Funktionens navn kan bruges til fremover at kalde den. Navnet kan også bruges af debuggers og developments tools til at identificere funktionen. Hvis en function ikke har fået et navn er den _anonym_.

Den **tredje del** er funktionens parametre omgivet af parenteser, som tager et sæt af nul eller flere parametre. Disse navne vil blive defineret som variabler i funktionen. Til forskel fra almindelige variabler bliver de _initialiseret_, når funktionen bliver kaldt.

 Den **fjerde del** er et sæt af statements omgivet af curly braces\(tuborgklammer\). Disse statements er kroppen til funktionen, som bliver udført, når funktionen bliver kaldt.

En function literal kan være alle steder, hvor en _expression_ kan være. Functions kan blive defineret inde i andre functions. En inner function vil derfor have adgang til begge funktioners parametre og variabler. 

> An expression is any valid unit of code that resolves to a value.







