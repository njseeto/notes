---
title: "Algorithms: Binary Sort"
date: 2020-02-22T10:13:30+05:30
description: "A better way to search"
tags: [algorithms, binary-sort, big-o]
disqus: false
---

This is part of the Algorithms series that I have decided to write up as a result of reading [Grokking Algorithms](https://www.manning.com/books/grokking-algorithms) book.

#### TL; DR
- Binary search eliminates half the remaining values every time.
- Binary search only works if the list is sorted.
- Algorithm speed isn't measured in seconds but in the **growth** of the number of operations.
- We talk about how quickly the run of the algorithm increases as the size of the input increases.
- Run time of algorithms is expressed in Big O notation.
- Binary search will take log<sub>2</sub>n steps to run in the worst case - That is it runs in logarithmic time ie: **O(log n)**.
- A time of O(n) is known as *linear time*.
- O(log n) is faster than O(n) and gets even faster as the input grows bigger.

<br>

_________

### Binary Search

Imagine you were asked to guess a number between 1 and 100. You could go through each number from 1 to 100 (this is called Simple Search). But it would take a maximum of 100 guesses to get the correct answer.

> <h5>Jessie: Ok I’m thinking of a number between 1 and 100…
<br>
Jo: Is it 1?
<br>
Jessie: No, higher.
<br>
Jo: Is it 2?
<br>
Jessie: Higher…
<br>
Jo: 3?
</h5>

… You get the point.


A quicker way to do this would be to guess the middle number, in this example 50. That way the other person can tell you if you’ve gone too low or too high, eliminating half the numbers. If you guess 25, you’ll again eliminate half - are we seeing a pattern here?

This is binary search in a nutshell.

> You guess the middle number and eliminate half the remaining every time.

With the example of guessing a number between 1 and 100, the maximum guesses you’d have to make using a binary search method is **7**. 

Count them...

100 → 50 → 25 → 13 → 7 → 4 → 2 → 1

Far more efficient than simple search, which has a maximum of 100.

So how do we compare the efficiency between algorithms? 

*Enter Big O notation.*

### Big O Notation

Each algorithm has a run time, which is the time it takes to complete a task.

Big O is based on the maximum number of operations required to complete a task, aka *the worst case scenario*.

The maximum guesses required for a simple search is the same as the size of the input. That is if the input is 100, then the maximum number of guesses will be 100. 

This is known as **linear time**. Or in Big O, **O(n)**

With binary search *the maximum amount of guesses is the logarithm of the input*. 

That is:

> log<sub>2</sub>(8) = 3

> 2<sup>3</sup> = 8

This means an input of 8 will take a maximum of 3 guesses to arrive at the correct answer.

8 → 4 → 2 → 1.

This is known as *logarithmic time*.

That is, **O(log n)** in Big O notation.

Let's compare the running time for simple search vs binary search.

<table>
  <tr>
    <th>Simple Search</th>
    <th>Binary Search</th>
  </tr>
  <tr>
    <td>100 items → 100 guesses</td>
    <td>100 items → 7 guesses</td>
  </tr>
  <tr>
    <td>4,000,000,000 items → 4,000,000,000 guesses</td>
    <td>4,000,000,000 items → 32 guesses</td>
  </tr>
  <tr>
    <td>O(n) - LINEAR TIME</td>
    <td>O(log n) - LOGARITHMIC TIME</td>
  </tr>
</table>

<h5>Note: the O in Big O is literally just an O. It means nothing!</h5>

<br>

### Common Big O Runtimes (From fastest to slowest)
<table>
  <tr>
    <th>Run time</th>
    <th>Example</th>
  </tr>
  <tr>
    <td>O(log n) aka LOG TIME</td>
    <td>Binary Search</td>
  </tr>
  <tr>
    <td>O(n) aka LINEAR TIME</td>
    <td>Simple search</td>
  </tr>
  <tr>
    <td>O(n * log n)</td>
    <td>A fast sorting algorithm, like quick sort</td>
  </tr>
    <tr>
    <td>O(n<sup>2</sup>)</td>
    <td>A slow sorting algorithm, like selection sort</td>
  </tr>
    <tr>
    <td>O(n!)</td>
    <td>A really slow algorithm, like the traveling salesperson<sup>1</sup></td>
  </tr>
</table>

<br>

#### Remember:
- Algorithm speed isn't measured in seconds but in the **growth** of the number of operations.
- We talk about how quickly the run of the algorithm increases as the size of the input increases.
- Run time of algorithms is expressed in Big O notation.
- O(log n) is faster than O(n) and gets even faster as the input grows bigger.

____________

<h6><sup>1</sup>  A salesman has to travel to every single city in an area, visiting each city only once. Additionally, he needs to end up in the same city where he starts his journey from. The problem is finding the most efficient way to do this. The problem gets exponentially more difficult to solve the more cities the salesperson needs to visit.</h6>

<style>
table {
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

box {
  width: 300px;
  border: 2px solid red;
  padding: 8px;
  margin: 10px;
}
</style>