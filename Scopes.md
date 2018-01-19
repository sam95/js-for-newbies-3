## Scopes in Javascript
What is a scope?

Scope simply means visibility. Let's take a closer look at the image below. 
![Floors](https://lh3.googleusercontent.com/DGTv5Nxex7EQWaT59Mr7EbYyZl_RO2M1woT7Y8P-fUGi85CksKOVVJbqkpwkO-SvgFQ_9xSOeotHBcgbDDHk2vLgzdrGhqeAPi3CuSkZCGb5APLP1zWtfiwjYOF0s8Ws9_RGtZLPcZ8-S-J5CW_mzmpIRrYVfngH-XWC9uWhXAMlNOgWo9kD16QvnbHijTOzYXC23Mj_AynlmXiJ0TyHupg_aDdTolhgkyn95edPQkgje48jDF3F4b6gkHoxTNoZPFxtKy_7aT94ja0Uv184BSDSfhGsOd1QYQQ8fn6KeGay9pIh6TsXd9t7tQMGiXgaypEQadg75acgyY8LmF5eI1q_ure6e0veA_r6UYHzFnlJ-3DnsBuoOUyERAsNOc8xnlUVMkxZ_M7a18_u9OZtILi7kVVJdmMKOO8B4lzwtthSzkrodcYhvBTC4vytpz2ZWxf2Yp7pZx2MKFJRoyxi19dwmGScaU_lNvgv8WfPGdnZ8XKqZEQ1KpYwDXsHmUb0kznFE4JkD1BkE2BkcZrpXv858Ehdq1X2m8NAdG3WueTuvj9UgnUOSzKdnv7_LdZydRyxxb_XfKgBoW3aJN9xwjIfb-YOR-T0DtpeLE1Rsjo4MzoDa7Mi_tK1yuFeX7G6P6EGbwTO0C_2Wd4WvjBTFiGIrKYtmjA=w1516-h1136-no)
There are 3 people in the above image, person 3 can see both person 2 and person 1, person 2 can see only person 1. And person 1 can see no one!

Now, person 1 is called the **global scope**. It is visible by every function under it. There is also something called as **local scope**. If a function is created, it creates a scope of it's own (just like person 2). It will not be accessible globally or by any other function. 

Let's take a look at an example.

```javascript
let a = 20;

function anExample(){
  console.log("I am local "+ a);
  a += 10;
  console.log("I am local too "+ a);
}

anExample();
console.log("I am global "+ a);
```
In the above example, the function `anExample()` can access the variable `a` since the scope of `a` is global. The function `anExample()` can even change the value of the variable and it would affect the entire scope below. 😧

Suppose we now create another variable in `anExample()`, how are scopes applicable? Let's try it out.

```javascript
let a = 20;

function anExample(){
  let b = 30;
  console.log("I am local "+ (a+b));
}

anExample();
console.log("I am global "+ (a+b));
```
Now, can anyone guess the output? 😲

Let's take a closer look at the image below.
![Execution style by JS](https://lh3.googleusercontent.com/5MyYObEM_Yd9K_oue6QpP-R-u7Xx1BEe7Pu9VjFI6xSPcr5vlapSi0an8IRAdVUcSUPgoGhB-lAGdqA79utyypdMpI8_yAwSC2QCgwHBRBRPs5EZkGfesl27JR3eLQGqZvf6bXomI2CIZse01yQAaJVUqpxVaSuy3Ev1L90g0N_Ajgu7IinSHp7rgEFKXtScbkG2dQqCuh0c5wq1gB_JHl19QUCFBa1TZf56cIqleKWIVSudggqX2dzHA8TM2TEHM2VocGALECq617QlyNMlO5kESY2aBLPpiGiKRib311wgqiwUp2sdGB6K4IkFJZqXRS0BS_7nQXhIShJhNt8T37auHS8lYVqSIwDMLMdYf7W4-n0CFFpANcvcs2YcBtGnM_DWGfIA26hcFTQWcz23yoRvLUTgtJzK-Cdp9jRDw7nZDclKm3cIDLPCBxhfzA5_ttz8qAe9HngT_0nQZRFPxSKBPBk5ozP5nIU3PQGjTozaQ8XxQARE2--BCNnp4VRAu6R-uZuQDnPo6dGrZoCelpeCchI41EY9uFmB5KRB0DZOPWdIsQ0a6vB8xdetR9I6lN0-xaAFGuug0_DEoRJZ78AiDF7qM2s38D3d1w=w1632-h1224-no)
The blue boundary depicts the **global scope**. The red boundary depicts the **local scope** created by `anExample()`. And the green arrows are compilation constructs by the JS compiler.

When the function ends, the **local scope** which was created by the respective function is automatically destroyed, therefore all variables that were created in the function no longer exist. 😮

>Tip 💡 : Garbage Collector manages variables and each variable's context.

 ### Conflicts are love 💌
 Since we've now learnt about scopes. Ever wondered what would happen if both **global scope** and the **local scope** have the same variable? 

Let's try it out.
```javascript
let a = 10;

function anExample(){
  let a = 20;
  console.log(a);
}

anExample();
```
Always, if there is a conflict between the **local scope** and the **global scope**, **local** always wins! 👌

If there is a fight between **superman** and **shaktiman**, wouldn't you support **shaktiman**? For real? 🤥

### Creation of global in local 😵
So how can I create a **global** variable inside a **local scope** (function)?

Okay this is risky. You should may be never do this again while programming.

```javascript
function anExample(){
  a = 20;
  console.log("Local rocks too "+ a);
}

anExample();
console.log(a);
```
So did you guess the magical keyword to do that? 🙃

### War with var
Do you remember that I had used the `var` keyword in one of the recap codes before?

But why have we been using the `let` keyword the whole time? What is the difference between `var` and `let`?

Well actually, they're pretty much the same. Let's take a look at some examples.
```javascript
var a = 10; //globally scoped
let b = 20; //globally scoped
```
In the above scenario, both variables are defined globally. So their scope would be **global** throught.
```javascript
function anExample(){
	var a = 10; // locally scoped
	let b = 20; // locally scoped
}
// neither a nor b can be accessed
```
Okay, so where's the difference? 😤😡

In a **local scope**, `let` is block specific whereas `var` is not.
```javascript
function anExample(){
	let a = 10;
	for(let i=0;i<5;i++){ // scoped within the for block
		console.log(i);
	}
	console.log(i); // 😷 throws an error, `i` is undefined in this context 
}
```
Let's try the same thing out with `var`
```javascript
function anExample(){
	let a = 10;
	for(var i=0;i<5;i++){ //scoped within the enclosing function
		console.log(i);
	}
	console.log(i); // 😎🤓
}
```
In the above examples, `for` loop is a block. When the scope of a block is over, variables declared with `let` are destroyed but variables declared with `var` are not.

There's another difference between the two. In ***strict*** mode, `var` variables are treated as re-assignment. Let's get more clarity on this.

```javascript
'use strict';
let me = 'foo';
let me = 'bar';
/* This is an error */
```
But if we try to do the same thing with `var` the JS complier just assumes it to be a re-assignment of data.
```javascript
'use strict';
var me = 'foo';
var me = 'bar';
/* No error is awesome! */
```
In simple words, variables declared with `var` remain until the scope is destroyed.

> Food for thought 💡 : Try to print a `var` variable even before declaring it
### Where are global variables stored? 😐
Global variables are attached to the `window` object. What's `window` now? 

`window` is the main Javascript root object, it is the root object of your `DOM` (**Document Object Model**).
 
Whenever a web page is loaded, the browser constructs a `DOM` of every page. 

With the help of this `DOM`, javascript is able to create dynamic **HTML**.

### Global variables are cool but Security is an issue 😔
Just think for a moment, is it not a problem if every function can access a global variable? How do I restrict access for global variables? Okay, now it's time to jump to the next topic **`closures`**
