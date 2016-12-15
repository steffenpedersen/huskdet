# Vanilla JS

**The basics**

![](/assets/Skærmbillede 2016-12-15 kl. 12.08.02.png)

Semicolons separate JavaScript **statements**.

```js
document.write("Hello");
```

JavaScript **variables** are containers for storing data values.

```js
var intVar = 5;
var stringVar = "fish";
var boolianVar = true;
// comment
```

The + **operator** can also be used to add \(concatenate\) strings. You can also use `+`, `-`, `*`, `/`, `%`, `++` \(Increment\), `--` \(Decrement\).

```js
var words = "This is"; 
var morewords = " a sentence"; 
var sentence = words + morewords; 
document.write(sentence);
```

### ![](/assets/Skærmbillede 2016-12-15 kl. 12.27.29.png)

```js
var num1 = 5; 
var total = ++num1; 
document.write(total);
```

### ![](/assets/Skærmbillede 2016-12-15 kl. 12.30.03.png)

**Objects** are variables too. But objects can contain many values.

```js
var alpha = "ABCDEFG"; 
var length = alpha.length; 
document.write(length);
```

### ![](/assets/Skærmbillede 2016-12-15 kl. 12.34.03.png)

JavaScript **methods** are the actions that can be performed on objects.

```js
var alpha = "ABCDEFG"; 
var result = alpha.substring(3, 5); 
document.write(result);
```

### ![](/assets/Skærmbillede 2016-12-15 kl. 12.37.11.png)

JavaScript **arrays** are used to store multiple values in a single variable.

```js
var a = ["cat", "dog", 5, false]; 
document.write(a[1]);
```

### ![](/assets/Skærmbillede 2016-12-15 kl. 12.41.02.png)

A JavaScript **function** is a block of code that performs a particular task.

```js
function hello(who) { 
  document.write("Hello " + who); 
} 
hello("you");
```

### ![](/assets/Skærmbillede 2016-12-15 kl. 12.50.15.png)

**Conditional statements** are used to perform different actions based on different conditions. You can also use else if, `<`, `>=`, `<=`, `==`, `!=`.

```js
var a = 9;
if (a > 10) {
  document.write("The number is greater than 10");
} else {
  document.write("The number is not greater than 10");
}
```

### ![](/assets/Skærmbillede 2016-12-15 kl. 13.01.09.png)

**Loops** can execute a block of code a number of times.

```js
for (statement 1; statement 2; statement 3) { 
  code block to be executed 
}
```

Statement 1 is executed _before_ the loop \(the code block\) starts.

Statement 2 defines the _condition_ for running the loop \(the code block\).

Statement 3 is executed each time _after the loop_ \(the code block\) has been executed.

```js
for (i=0;i<5;i++) {
  document.write("Iteration " + i + "<br>");
}
```

![](/assets/Skærmbillede 2016-12-15 kl. 13.09.40.png)

