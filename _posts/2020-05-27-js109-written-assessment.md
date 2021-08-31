---
layout: post
title: JS109 Written assessment - Afterword
description: How to properly answer a question in a written assessment
---
I have just passed the written part of the JS109 assessment.

It was a hard experience for me, mainly because English is not my first language. I have never tried explaining
technical details of JavaScript variable scoping rules, object mutation, or using proper programming terminology in a
written form before.

Passing written part is not easy and requires a lot of practice of writing your explanations. In my particular case, it
took 125 hours to prepare for the exam:

![js109-written-assessment-time](/assets/images/js109-written-assessment-time.png)

It is certainly possible to pass the written part faster than I did. All you have to do is to understand the concepts
mentioned in the study guide and practice throughly writing your answers clearly.

There are a lot of great articles from other Launch School students to help with preparation to the exam, tips and tricks to learn and understand the material. In this article I would like to share a template for answering exam questions that worked for me.

## Answer template
**Question example:**
What will line 9 log to the console and why?
```js
/*0*/ let greeting = ["Hello"];
/*1*/
/*2*/ const test = arr => {
/*3*/ arr = ["ByeBye"];
/*4*/ arr.push("World!");
/*5*/ return arr;
/*6*/ }
/*7*/
/*8*/ test(greeting);
/*9*/ console.log(greeting);
```
---

**Answer example:**

On line 9 `console.log` function call prints `["Hello"]` to the console because
1) global variable `greeting` is not reassigned within the body of the function `test`
2) and the object variable `greeting` points to is not mutated within the function `test`.

On line 0 global variable `greeting` is declared and assigned to reference of the array `["Hello"]`.

On line 8 function `test` is invoked with the passed in argument `greeting`. At this stage both global variable
`greeting` and parameter `arr` are referencing the same array.

On line 3 parameter `arr` is reassigned to the new array `["ByeBye"]`. That is, parameter `arr` no longer references the
place in the computer memory where the object `greeting` variable points to.

From now on, we can't mutate the object variable `greeting` points to, because `arr` now references a different object.

---

<div class="box">
  <p style="text-align: center">
  <b>Your answers should be succint, use correct terminology and explain all relevant lines of code.</b>
  </p>
</div>

### Be Succint
The answer should be succint. If you try to explain every line of code in each problem example, you can easily run out
of time and submit late. And if you submit the test late, you'll get a 10% score deduction. This can easily lead to a
`not yet`.

Start by answering the question you were asked:

`What will line 9 log to the console and why?`

```
On line 9 `console.log` function call prints `["Hello"]` to the console because
1) global variable `greeting` is not reassigned within the body of the function `test`
2) and the object variable `greeting` points to is not mutated within the function `test`.
```

### Use correct terminology
Make sure to use the proper terminology. Below are some examples from this template answer:

|Writing|Explanation|
|-------|-----------|
| `console.log` function **call** | - "call" or "invocation" of a function executes statements within the body of a given function definition|
| **prints** `["Hello"]` to the console  | - function `console.log` prints or logs something to the console, not returns the value. The return value of the `console.log` is `undefined`|  
|global variable `greeting` | - make sure to clarify which variable you are referring to and its scope| 
|[variable] is not reassigned | - only variables can be reassigned, not values!|
|the object variable `greeting` points to | - clarify which specific value you are referring to |
| is not mutated within the function `test` | - use "mutated" instead of "changed" or "altered" |

### Explain only relevant lines of code
Once you answered the question, make sure to explain how you come up with your answer. 

Explain in detail all **relevant** lines of code and omit lines that are not related to the question.

This is related to the time restriction of the written assessment. You have to explain the code. Though, by avoiding extra writing that has nothing to do with the score for the assessment, you can save some precious time to answer all questions and review your answers in the end.

That's exactly what you see in the answer example: 

```
On line 3 parameter `arr` is reassigned to the new array `["ByeBye"]`. That is, parameter `arr` no longer references the
place in the computer memory where the object `greeting` variable points to.

From now on, we can't mutate the object variable `greeting` points to, because `arr` now references a different object.
```

## Summary
There are several take-aways from this article:
- it might take a lot of time and some nerves to practice explaing code in writing; however, it is most certainly possible to learn that;
- to pass the exam you need both to fully understand the material and write your answers clearly;
- practice **writing** answers to questions in the quizes in JS101 and JS100 Basics. Do it several times until you feel that your answers are succint, use correct terminology and explain all relevant lines of code.