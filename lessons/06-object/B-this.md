---
title: "this"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

`this` fonksyonun execution contextini referans eder.başka bir deyişle çalıştırılan fonksyonu temsil eder.

this fonksyon her çağırıldığında yeniden çağırılır bu sayede tekrar tekrar kullanılabilinir.

içerisinde this bulunan fonksyonu çalıştırmak için 4 yol var:

- .call()
- .bind() veya .apply()
- new
- default: global scope

```
function ask(question){
    console.log(this.teacher,question);
}

var workshop1 = {
   teacher:"Ikbal",
   ask:ask,
}

var workshop2 = {
   teacher:"Suzy",
   ask:ask,
}

workshop1.ask("How do I share a method?");
//Ikbal How do I share a method?

workshop2.ask("How do I share a method?")
//Suzy How do I share a method?
```

## new keyword

new keyword this için boş bir obje oluşturup fonksyonu çağırır.

```
function ask(question){
     console.log(this.teacher,question);
}

var newEmptyObject = new ask("'new' keywordu ne işe yarıyor.")
// undefined 'new' keywordu ne işe yarıyor.
```

sırasıyla new keyword bunları yapar:

- sıfırdan boş bir object oluşturur.
- yeni oluşturulan object diğer objecte link verir.
- fonksyonu bu boş obje ile çalıştırır.

> arrow functions doesn't have this and this will connect the closest functional scope.
