# A quick recap of Session 2

Session 2 of the series **JS for newbies** was taken by Abhinav Seelan. The entire session is recorded on YouTube and can be found [here](https://www.youtube.com/watch?v=byB88mL9jEs).

There is also a github repository to follow up with this session. It can be found [here](https://github.com/abinavseelan/js-for-newbies-2/).

If you have not attended this session, I highly suggest you go through it completely. I thank my friend Abhinav for carrying out an excellent webinar 👏, I learnt a lot from that session 🤓.

Let's just run through important concepts of the previous session before we get started. 👀

## Data types in Javascript
Javascript is a *dynamically typed language*. That means variables can hold any value irrespective of the type of the value. 

```javascript
let a = 5;
console.log(typeof a); // number
a = "This is an example";
console.log(typeof a); // string

/* This 
    is 
   cool */
   ```

There are mainly **5** data types of values that can be present in variables.
- `number` (A numeric value like `5` or `5.5`)
- `boolean` (A conditional value like `true` or `false`)
- `string` (A character or string value like `'Hey'`)
- `undefined` (An `undefined` value)
- `object` (An aggregate value of properties and values)

Let us go through each of the data types in a bit more detail.

### number 
A value of type **number** is a numeric value. Let's look at an example.

```javascript
let a = 5;
```
### boolean
A value of type **boolean** stores either a `true` or `false`. There two are a result of conditions in code. 

This helps in deciding which part of the code we want to execute, or how many times we need to execute the same code.

```javascript
let a = (5 == 8);
if(a){
    console.log("5 is equal to 8");
}
else{
    console.log("5 is not equal to 8");
} 
```
### string 
A value of type **string** is either a character or an string of characters. 

```javascript
let myName = "What's my name?";
let myInital = "S";
```
### undefined

A value of type **undefined** is literally undefined. 😆

```javascript
let middleName;
console.log(middleName);
/* Output is undefined because I don't have a middle name */
```
### objects
A value of type **object** is in simple, a **key - value** pair. 

```javascript
let crickter = {
    // key : value
    name: 'Anil Kumble',
    age: 40,
    isBatsman: false,
    isBowler: true,
};
```
Okay, Let's hold it. The subject **object** data type is an ocean. We've not even touched a wave. Let's try to answer some questions below.
- Can the key be a String? 😎
- Can I have an array of objects? 😦
- Can the value be an array? 😨
- Can the value be a function? 😷
- Can the value be an object again? 😱
## Arrays
An array in simple, is a collection of values.  

```javascript
let heroes = ['batman', 'superman', 'flash', 'arrow'];
```
> The values in an array can belong to any data type 😌 

### Iterating an Array
This means, accessing an element in the array through a sequence. Let's use a simple `for` loop to do this.

```javascript
let heroes = ['batman', 'superman', 'flash', 'arrow', 'robin'];

for(let i = 0; i < heroes.length; i++) {
    console.log(heroes[i]);
}
```
### Methods for Arrays
Javascript makes it even simple to **CRUD** elements in an array.

Wait a minute. What's **CRUD**? 🤔😖
- **C**reate :
     
  The `push()` method lets you insert a value to the end of the array.
      
    ```javascript
    heroes.push("hulk");
    ```
- **R**etrieve
  
   You can directly get the value stored in an index.
       
     ```javascript
     console.log(heroes[2]); // ⚡⚡
     ```
    Quick question💡: 
    
    Suppose I now, know the value present in an array. How do I find it's index? 🤤 🤓
- **U**pdate
   
   Now I feel, I need to change a hero from the list. Let's be straight, **arrow** doesn't belong there.
       
     ```javascript
     heroes[3] = "ant man";
  ```
- **D**elete

    Wait, I want to remove **robin** out of the list. `pop()` comes to rescue.
    
   ```javascript
   heroes.pop();
   ```
Wait, there's more. `push()` and `pop()` work only with the end of the array.

I want methods that do the same work with beginning of the array. 😤

**Say no more**

`unshift()` and `shift()` do the same thing as `push()` and `pop()` respectively. Just that they work with the beginning of the array.

```javascript
heroes.unshift("iron man");
// Output : ['iron man', 'batman', 'superman', 'flash', 'ant man']
```
 **iron man** disclosed his identity and **War Machine** is an exact copy of **iron man** plus I don't like him. So I would like to remove him, but the `pop()` method, if used removes **ant-man**. `shift()` comes to the rescue.
 
```javascript
heroes.shift();
// Output : ['batman', 'superman', 'flash', 'ant man']
```
## Functions
A **function** means a block of code, called by a name. A function can be created by using the **function** keyword.

```javascript
function someFunctionName() {
    // some code
}
```
 There are essentially **3** parts of a function :  
- function name: The function name help us reference this function across our program.
- function parameters: These let us provide some data to the function. 
- function body: This houses the logic that we want to execute everytime we call the function.

Let's look at an example function 

```javascript
function add(x, y) {
    return x + y;
}

// Invoke function to find the sum
console.log(add(9, 7));
/* Prints 16 */
```
### Anonymous functions
What does **anonymous** mean? Google says something with an **unknown name** ☝. The same concept applies even here. A **function** which has no name! Wait, how can it be possible? 🙀 How can something not have a name? 👊 Let's check it out. 🖐
```javascript
var x = function (a, b) {
  return a + b;
};
console.log(x(2, 3));
```
Now you may ask, Isn't `x` the name of the function? If it isn't, then what is it? I would tell you, that `x` is just a normal global variable. 🤒

It isn't a compulsion for functions to always have a name. If we need to pass parameters to the functions, pass parameters to the variables which bind them. Here in this case, pass parameters to `x`.  😏

---
Let's get to the interesting part of the discussion 🙄.

Quick question 😶 : How do I share data from one method to another without passing them as parameters? 😮

If your answer is **global variables**. You're right ✌👏. 

Let's take a look at it.

   ```javascript
   var a = 10;
   function addWithA(x, y) {
       return x + y + a;
   }

   // Invoke function to find the sum
   console.log(addWithA(9, 7));
   /* Prints 26 */
   ```

Since you answered the quick question, let's have some more quick questions 😝.

- I have a doubt with the above code. Do you sense a problem too?
- Can I create a global variable inside a function?
- If I change the value in a function, is it going to change the value globally?
- What if there is a variable conflict between global and local?
    
   Let's look at an example which depicts the above question.
     ```javascript 
      let a = 10;
     function addWithA(x, y) {
         let a = 5;
         return x + y + a;
     }
     console.log(addWithA(9, 7));
     /* What's the answer? 🤤 */
     ```
    
- How to make a global variable not accessible by some functions? 

If you want to answer all the above questions, you'll need to know **`scopes`**.