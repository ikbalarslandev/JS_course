---
title: "Currying"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

birden fazla parametre alan fonksyonları closure yardımıyla tek parametre alan fonksyonlara bölmemizi sağlar.

```
function greet(greeting,name){
   return `${greeting},${name}`
}

function curryGreet(greeting){
   return function (name){
       return `${greeting},${name}`
   }
}


const greetTur = curryGreet("Merhaba");
greetTur("Ikbal");  // Merhaba Ikbal

const greetEng = curryGreet("Hello");
greetEng("Ikbal");  // Hello Ikbal
greetEng("Mesut");  // Hello Mesut

```
