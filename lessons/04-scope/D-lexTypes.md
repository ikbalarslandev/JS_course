---
title: "Lexical scope types"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

lexical scope iki çeşit scope ile çalışır:

- function scope
- block scope

function scope: sayfanın kendisi ve fonksyon tanımlarından oluşur.

block scope: sayfanın kendisi ve bloklardan oluşur.

## Function Scope

fonksyon tanımlarından oluşur.

`var` kullanarak bir değişken oluşturursak bu değişkeni en yakın fonksyon scopu içerisindeki hafızada oluşturur. eğer yakınlarda fonksyon yok ise global variable enviroment içerisinde oluşturur.

kısaca `var` değişkeni fonksyon içerisinde veya globalde oluşturur.

## Block Scope

fonksyonlar yerine `{}` suslü parantez blokları ile oluşturulur.

IIFE yerine blokları kullanabiliriz.

```
var teacher = "Ikbal";

{
    let teacher = "Suzy";
    console.log(teacher)
}

console.log(teacher);

```

`let` kullanarak bir değişken oluşturursak block scope içerisindeki hafızada oluşturur.

> bu sebeplerden dolayı block scope içerisinde `var` kullanarak değişken oluşturmamalıyız.

> eğer bir değişken fonksyonun scopuna ait ise `var` kullanmalıyız. eğer block scope a ait ise `let` kullanmalıyız.

```
function repeat(fn,n){
  var result;

  for(let i = 0; i < n; i++;){
     result = fn(result , i);
  }

   return result;
}
```

---

bazen block içerisinde var kullanmak mantıklı olabilir.

```
function lookupRecord(searchStr){
   try{
       var id = getRecord(searchStr);
   }
   catch(err){
       var id = -1
   }
   return id;
}
```

veri dönüşümleri için block kullanmalıyız.

```
function formatStr(str){
  {  let prefix , rest;
     prefix = str.slice(0,3);
     rest = str.slice(3);
     str= prefix.toUpperCase() + rest;
  }

   return str;
}
```

### const

aynı let gibi block scope içerisinde değişken yaratmak için kullanılır. let ile farkı const sandece bir defa değer alabilir asla değeri değiştirilemez.

```
var teacher = "Suzy";
teacher = "Ikbal"   // ok

const myTeacher = teacher;
myTeacher = "Suzy"   // TypeError

const teachers = ["Ikbal","Suzy"];
teachers[1]= "Mesut";   //allowed!

```
