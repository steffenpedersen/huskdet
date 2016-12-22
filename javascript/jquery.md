# jQuery Basics

**Hide/Show**

```js
$('div.box1').click(function(){
  $(this).hide(800).delay(300).show(500);
});
```

![](/assets/dec.-22-2016 14-31-55.gif)

**Fade**

```js
$('div.box3').click(function(){
  $(this).fadeOut(800).show(500);
});
```

![](/assets/dec.-22-2016 14-34-53.gif)

**Slide**

```js
$('div.box2').click(function(){
  $(this).slideUp(800).slideDown(500);
});
```

![](/assets/dec.-22-2016 14-37-37.gif)

**Animate**

```js
$('div.box4').click(function(){
  $(this).animate({'bottom': '-50px'}, 300);
});
```

![](/assets/dec.-22-2016 14-40-16.gif)

**stop\(\)**

```js
$('p.stop').click(function(){
  $('div.box4').stop();
});
```

![](/assets/dec.-22-2016 14-52-02.gif)

**Callback**

A callback function is executed after the current effect is 100% finished.

```js
$("button").click(function(){
    $(this).fadeOut("slow", function(){
        alert("The paragraph is now hidden");
    });
});
```

![](/assets/dec.-22-2016 15-01-55.gif)

**Filtering**

```js
// INDEX FILTERS
$('p:eq(4)').css('border', '4px solid grey');

// RELATIONSHIP FILTERS
$('#box:empty').css('border', '4px solid grey');

$('.box1').children().css('border', '4px solid lightgrey');

// ATTRIBUTE FILTERS
$('a[href$=".io"]').css('border', '4px solid grey');
```

-

