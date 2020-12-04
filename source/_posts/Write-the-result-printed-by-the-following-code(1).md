---
title: Write the result printed by the following code(1)
date: 2020-12-04 23:02:47
tags:
- variable
categories: 
- console
---

## Question
### Write the result printed by the following code

```js
var result = [];
var a = 3;
var total = 0;
function foo(a) {
  var i = 0;
  for (; i < 3; i++) {
    result[i] = function() {
      total += i * a;
      console.log(total);
    }
  }
}

foo(1);
result[0]();
result[1]();
result[2]();
```
## Answer
<details><summary>CLICK ME</summary>
<p>

```js
result[0](); //3
result[1](); //6
result[2](); //9
```

</p>
</details>

## analyze
First of all, when `foo(1);` is executed, the `foo` function will pass parameter 1 inside, and the for loop will mount three new functions into the `result` array.
Then, we execute the new functions mounted in `result` in turn, we can find that the new function is mainly to obtain `i` and `a` for calculation, there are 3 important points:

1. `i` is temporarily taken from the scope of the current function, and `i` has become 3 after the loop
2. The same with `a`, after the execution of `foo(1);`, the local variable `a=1` has overwritten the global `a=3`
3. When the first `result` function is executed, the global `total` changes, which will affect the subsequent calculations