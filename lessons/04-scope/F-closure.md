---
title: "Closure"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## Factory function

fabrika fonksyonları olarak bilinir. bu fonksyonlar çalıştırıldığında object yaratırlar.
(fonksyonlar objelerden türetilmiştir.)

```
function userCreator(name, score) {
const newUser = {};
newUser.name = name;
newUser.score = score;
newUser.increment = function() {
newUser.score++;
  };
return newUser;
};

const user1 = userCreator("Will", 3);

const user2 = userCreator("Tim", 5);
user1.increment()
```

## Closure

Bir fonksyonun çalıştırıldıktan sonra lexical scopeunu _hatırlamasına_ closure denir. fonksyon çalıştırıldıktan sonra garbage collector variable enviromenti silmez.

bu durum factory functionlar sayesinde mümkün olur.

```
function createFunc(){
   let i = 0;

   function inner(){
     let element = i;
     i = i + 1;
     return element
   }
   return inner
}

const returnNextElement  = createFunc()

returnNextElement()   // 0
returnNextElement()   // 1
returnNextElement()   // 2
returnNextElement()   // 3
returnNextElement()   // 4

```

`returnNextElement()` fonksyonu her çağırıldığında bir sonraki rakamı verir. yani daha önceki hafızasını hatırlar.
