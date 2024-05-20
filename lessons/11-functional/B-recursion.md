---
title: "Recursion"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

_iteration_ : imperative , looping , statefull

_recursion_ : functional , self-referential , stateless

iteration malesef fonksyonel değil bunun yerine recursion kullanmalıyız.

iteration:

```
funciton sum(numbers){
  let total = 0;
  for (i=0; i<numbers.length; i++;){
     total += numbers[i];
  }
  return total
}

sum([0,1,2,3,4]); // 10
```

recursion:

```
function sum(numbers){
  if(numbers.length === 1){
      // base case
      return numbers[0]
  }else{
      // recursive case
      return numbers[0] + sum(numbers.slice(1))
  }
}


sum([0,1,2,3,4]); //10
```
