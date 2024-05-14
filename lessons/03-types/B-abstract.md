---
title: "Abstract Operations"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## typeof

`typeof` fonksyonunu kullanarak değişken içerisinde bulunan değerin tipini string olarak yazdırabiliriz.

6 ilkel tipini typeof ile yazdıralım.

```
var v;
typeof v;                         //"undefined"
v = "1";
typeof v;                         //"string"
v = 1;
typeof v;                         // "number"
v = true;
typeof v;                         // "boolean"
v = 42n;
typeof v;                         // "bigInt"
v = Symbol();
typeof v;                         // "symbol"
```

> `typeof` sonucu her zaman `string` olarak verir.

> Eğer ilkel bir tipi silmek isterseniz yerine `undefined` yazmalısınız. eğer referans tipi silmek isterseniz yerine `null` yazmalısınız.

## Boş Değer Varyasyonları

_undeclared_: bu değişken erişimimiz olan hiçbir yerde hiçbir zaman oluşturulmadı.

_undefined_: bu değişken kesinlikle bir değere sahip fakat şimdilik değeri yok.

_uninitialized_: bu değişken TDZ(temporal dead zone) içerisinde yani, henüz treat of execution bu değişkeni okumadı.

## NaN & isNaN(not a number)

Eğer sayı olmayan bir değişken ile matemetik operasyonu yaparsak sonuç `NaN` olur.

> NaN kendine eşit olmayan tek değerdir.

NaN kendine eşit değil bu sebeple`something === NaN` kullanarak eşitliği ölçemeyiz. Bu sebeple NaN olup olmadığını kontrol etmek için `isNaN()` kullanırız.

Otomatik olarak `isNaN()` içerisindeki değeri sayıya çevirir daha sonra NaN olup olmadığını kontrol eder.

Eğer değeri sayıya çevirmesini istemiyorsak onun yerine `Number.isNaN()` kullanabilirsiniz. bu fonksyon değişkeni direkt olarak kontrol eder.

> typeof NaN cevabı Number olarak gelir.

```
var myAge = 38;                           // 38
var myNextAge = 39;                       // 39
var catsAge = "hello";                    // "hello"

catsAge - "my son's age";                 // NaN

myCatsAge === myCatsAge;                  // false

isNaN(myAge);                             //false
isNaN(catsAge);                           //true
isNaN("my son's age");                    //true  OOPS!

Number.isNaN(catsAge);                    //true
Number.isNaN("my son's age");             //false

```
