---
title: "Function Types"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

fonksyonlar yaratılmalarına göre ikiye ayrılır:

- Function declerations: direk olarak fonksyon tanımlama
- Function expressions: fonksyonun bir değişkene atanması.

```

// function declaration
function otherClass(){
  teacher = "Mesut";
  topic = "javascript";
  console.log("Hello!")
}


// function expression
var hello = function other(){
  teacher = "Mesut";
  topic = "javascript";
  console.log("Hello!")
}


```

## IIFE Pattern (Immediately Invoked Function Expression)

yaratıldığı anda çağırılan fonksyonlara denir.

```
var teacher = "Ikbal"

function anotherTeacher(){
  var teacher = "Suzy";
  console.log(teacher);
}

(anotherTeacher)();

console.log(teacher)

```

```
var teacher = "Ikbal"

(function anotherTeacher(){
  var teacher = "Suzy";
  console.log(teacher);
})();

console.log(teacher)
```

```
var teacher = "Ikbal"

(function (teacher){
  console.log(teacher);
})("Suzy");

console.log(teacher)


```
