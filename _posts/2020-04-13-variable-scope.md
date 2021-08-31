---
layout: post
title: Variable Scope
description: Explaning variables, scope and a variable scope topic.
---

In this article I will try to explain what a variable is, what scope is, and finally what a 'variable scope' is. I will especially try to clarify, how variables interact with function definitions and blocks. I will also suggest reading materials below to understand the topic better.

1. Launch School's Intro to JS book explains what [variable](https://launchschool.com/books/javascript/read/variables#variablescope) is.
2. Eloquent JS book explains what [variable](https://eloquentjavascript.net/02_program_structure.html#h_lnOC+GBEtu) is.
3. Launch School's [Variable Scope explanation in JS101 course](https://launchschool.com/lessons/64655364/assignments/7c0087dd) goes into practical implications of variable scope (this material is only available for subscribed students).
4. Eloquest JS book explains different "locality" of [variable scopes](https://eloquentjavascript.net/03_functions.html#h_XqQR5FlX+8)
5. and, also, here's one more take on variable scope from [javascipt.info](https://javascript.info/closure)

## Definitions of Variable in different places: 

**Variable** in JavaScript means: 
- a contrainer that holds information (source: [Launch School](https://launchschool.com/books/javascript/read/variables#variablescope))
- a "named storage" for data (source: [javascript.info](https://javascript.info/variables))
- a thing to catch and hold values (source: [Eloquest JS book](https://eloquentjavascript.net/02_program_structure.html#h_lnOC+GBEtu))


![octopus](/assets/images/variable-octopus-holding-value.jpg)
<dl>
	<dt>I like a comparison of a variable with an octopus tentacle 🐙 in  <a href="https://eloquentjavascript.net/02_program_structure.html#h_lnOC+GBEtu">Eloquent JavaScript book</a></dt>
	<dd>
		<blockquote>
    You should imagine bindings as tentacles, rather than boxes. They do not contain values; they grasp them—two bindings can refer to the same value. A program can access only the values that it still has a reference to. When you need to remember something, you grow a tentacle to hold on to it or you reattach one of your existing tentacles to it.
		</blockquote>
	</dd>
</dl>


## So, how do you "make" a variable?

![image](/assets/images/variable-scope-1.png)

First things first, you are not making, you are **declaring** a variable. 

A **variable declaration** is a statement that reserves a space in the computer memory for a variable with a particular name and initializes it with a value. 

```javascript
let currentAge = 27;
```

Statement above is a variable declaration. How do we know that? First of all, the line of code starts with the special word _let_. That means that we tell our computer in JavaScript language that we want to store some info for later. Then, we give a name to the info that we want to catch and hold: `currentAge`. At this point we can actually finish the variable declaration by simply putting the semicolon and telling our computer in JavaScript that this is the end of our expression. In that case, we would have written `let currentAge;` and that would initialize it with a value of `undefined`. 

This is exactly why if you try to run the code in Node and hit 'Enter' you would get a return value of 'undefined'. 

And, finally, since we want immediately give our variable a value to store, our variable declaration is followed by `= 27;`. In this chunk of code we assign a variable `currentAge` to the value of number `27`. And, this is why if you try to run the code in Node and hit 'Enter' you would get a return value of '27'.


## Variable scope

The definition of variable seems to be clear now. To understand what's "variable scope" it would be helpful to understand what "scope" is. 

So, **scope** in JavaScript means: 
- the part of the program in which the variable is visible.(source: [https://eloquentjavascript.net/03_functions.html#h_XqQR5FlX+8](https://eloquentjavascript.net/03_functions.html#h_XqQR5FlX+8))
- set of rules for storing variable in some location, and for finding those variable at a later time.(source: [https://github.com/getify/You-Dont-Know-JS/blob/1st-ed/scope%20%26%20closures/ch1.md#chapter-1-what-is-scope](https://github.com/getify/You-Dont-Know-JS/blob/1st-ed/scope%20%26%20closures/ch1.md#chapter-1-what-is-scope))

That means that variable scope determines where that "named storage" for data [variable] can be visible and used in the program. The location where you declare a variable determines its scope. So, this is crucial to understand WHERE a variable is defined.



### Global scope
Variables that are defined outside of a function or block have a scope of the whole program. This is called **global scope**.

Global scope variables are visible and can be accessed from anywhere within a program.

### Local scope
What's hard about understanding the scope is knowing how to access and/or whether you can access a variable that are created for function parameters or declared inside a function. 

Those variables are called local variables, since they can be referenced only in that given function block. 

Every time the function is called, new instances of these variables are created. This provides some isolation between functions — each function call acts in its own little world (its local environment) and can often be understood without knowing a lot about what’s going on in the global environment.(source: [https://eloquentjavascript.net/03_functions.html#h_XqQR5FlX+8](https://eloquentjavascript.net/03_functions.html#h_XqQR5FlX+8))

In JS variables declared with keywords `let` and `const` have **block** scope. A block is a set of JS statements and expressions between a pair of opening and closing curly braces. That means, that variables with  `let` and `const` that are declared inside of a loop ARE NOT visible before and after the loop.

```javascript
let currentAge = 27;   // define variable 'currentAge' and assign it to value of number 27

if (true) {          // true has a truthy value so computer will run the code in the block scope    
  let publicAge = 20;  // define variable 'publicAge' and assign it to value of number 20
  let mentalAge = 30;  // define variable 'mentalAge' and assign it to value of number 30
  console.log(`I wish I were ${(currentAge - publicAge)} years younger. Though, it's good that my mental age is ${mentalAge}.`);  //  → "I wish I were 7 years younger. Though, it's good that my mental age is 30."
}
// 'mentalAge' is not visible here
console.log(`Your mental age is actually ${currentAge - mentalAge}.`);
// → ReferenceError: mentalAge is not defined
```
Each scope can "look out" in the scope around it. So, `currentAge` can be accessed from inside the block scope and used to log `"I wish I were 7 years younger. Though, it's good that my mental age is 30."` string to the console. 

On the other hand, `mentalAge` is defined within the block scope and cannot be accessed from the outter scope. That's why computer tells us that `mentalAge is not defined`.  

There's an exeption to this rule, though. When multiple variables have the same name, JavaScript can ONLY SEE the innermost variable. It's also called variable shadowing.

```javascript
const divideBy2 = function(n) {
  return n / 2;
};

let n = 10;
console.log(divideBy2(100));
// → 50
console.log(n);
// → 10
console.log(divideBy2(n));
// → 5
```

### Nested Scope
And, now, a bit deeper into the topic of scope. Blocks and functions in JavaScript can be created inside other block and functions, which produces multiple degrees of locality. (source: https://eloquentjavascript.net/03_functions.html#i_c/Ms2Ed/N0). 

```javascript
const forFamilyOf = (num = 1) => {
  const ingredient = (amount, unit, name) => {
    let ingredientAmount = amount * num;
    if (ingredientAmount > 1) {
      unit += 's';
    }
    console.log(`${ingredientAmount} ${unit} ${name}`);
  }
  ingredient(1, "cup", "flour");
  ingredient(2, "teaspoon", "baking powder");
  ingredient(2, "tablespoon", "sugar");
  ingredient(1, "egg", "");
  ingredient(2, "tablespoon", "butter");
  ingredient(0.5, "teaspoon", "vanilla extract");
};


pancakesForFamilyOf();
console.log('---------------------');
pancakesForFamilyOf(3);
console.log(ingredient); 


// → 3 cups flour
// → 6 teaspoons baking powder
// → 6 tablespoons sugar
// → 3 eggs 
// → 6 tablespoons butter
// → 1.5 teaspoons vanilla extract
// → ---------------------
// → ReferenceError: ingredient is not defined
```

The code inside `ingredient` function can see the `num` variable from the outer `forFamilyOf` function. But neither `ingredient` function itself, nor its local variables, such as `ingredientAmount`, `unit`, or `name` can be seen in the outer function. Try out for yourself in [Repl.it](https://repl.it/@dmytronayda/variableScope) check file index.js.


## Sources
1. [Launch School JS 101 - Variable Scope](https://launchschool.com/lessons/64655364/assignments/7c0087dd) ** this only available to subscibed students
2. [Eloquent Javascript](https://eloquentjavascript.net/index.html)



****