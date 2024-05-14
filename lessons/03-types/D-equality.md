---
title: "Equality"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## == vs. ===

`==` coerciona izin verir (farklı veri tiplerine izin verir)
`===` coercionu kabul etmez (veri tipleri aynı olmak zorunda)

#### `==` algoritması:

- veri tipleri aynı ise: `===`
- `null` ve `undefinded` birbirine eşittir.
- eğer referans tip ise: ToPrimitive
- eğer iki farklı ilkel tipi karşılaştırmak istersek ikisini de numbera donuşturup daha sonra karşılaştırır.

#### == Açıkları

```
[] == ![]   //true  What!!

var workshop1Students = [];
var workshop2Students = [];

if(workshop1students == !workshop2Students){
// true whattt!!
}

if(workshop1Students != workshop2Students){
//true what!!
}
```

```
if(workshop1students != workshop2Students)
\\if([] == false)
\\if("" == false)
\\if(0 == false)
\\if(0 === 0)

// true

```

boolean açığı

```
var workshopStudents = [];

if(workshopStudents){
// yep
}

if(workshopStudents == true){
//nope  :
}

if(workshopStudents == false){
// yep  :
}

```

> Açıkları minimuma indirmek için

- `0` ve `""`ve `" "` kullanma
- referans tiplerle kullanma
- `== true` veya `== false` kullanma

peki eşitlikleri nasıl kullanmalıyız.

- Mumkun olan her yerde `==` kullanmalıyız.
- Eğer veri tipleri eşitse `==` , zaten `===` e donusucek.

> Object.is() is acts like quadriple equals.
