---
title: "Basics"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

çeşitli verilerin bir arada bulunduğu kompleks kolleksyonlara object denir.

object içerisinde bulunan veriler değişken isimleri içerisinde tutulur.
{
"key:value",
}

```
 let user = {
   name:"John",
   age:30
 }
```

## Object oluşturmak

object oluşturmak için iki yol var:

- Object constructor
- Object literal

object constructor:

```
let user = new Object(); // "object constructor" syntax
```

object literal:

```
let user = {}; // "object literal" syntax
```

## Dot Notation

Object içerisinde bulunan key değerlerine ulaşmak için nokta kullanılır.

```
let user = {
    name: "Ikbal",
    surname:"Arslan",
    age:45
}
```

name değerine ulaşmak için _user.name_ şeklinde nokta kullanılır.

user.[name] seklinde de çağırılabilinir.

## delete operator

delete operator kullanarak object içerisindeki key değerini silebiliriz.

```
delete user.age;
```

## Object içerisine key ekleme

```
let user = {
    name: "Ikbal",
    surname:"Arslan",
    age:45
}

user.color = "blue";
```

bu şekilde yeni key ekleyebiliriz.

> Object içerisinde key olarak tanımladığımız fonksyonlara method denir.
