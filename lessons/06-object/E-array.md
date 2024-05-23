---
title: "Arrays"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

Objeleri kullanarak veri koleksiyonlarını saklayabiliriz fakat çoğunlukla bu verinin belirli bir sıralamada olmasını isteriz.ayrıca verileri düzenlemek için çeşitli fonksyonlara ihtiyacımız var . bu fonksyonları teker teker elle yazmak yerine javascript içerisinde bulunan özel Objeler olan Arrayları kullanabiliriz.Arraylar koleksyonları düzenlemek için özel fonksyonlar bulundurur.

## Array oluşturmak

iki sekilde oluşturabiliriz:

```
let arr = new Array();
let arr = [];
```

## index

arraylar objelerden turetilmistir:

```
let obj = {
   name:"ikbal",
   surname:"arslan",
}
```

obje yaratirken "key:value" seklinde elementler olustururuz. arraylarda ise sadece value degerini yazarız. key değeri kacıncı sırada olduguna gore belırlenır.

```
let arr = ["ikbal","arslan"]
```

bu arrayi obje olarak dusunursek :

```
let arr = {
    0:"ikbal",
    1:"arslan",
}
```

arraylarda key yerine index kelimesi kullanılır ve her zaman sıfırdan baslar.

arr[0] = "ikbal" seklinde cagirilir.

> `...` spread operetörü ile array içindeki elementleri açabiliriz.

## methods

> object içerisinde tanımlı olan fonksyonlara method denir.

.push(),.pop(),.shift(),.unshift() methodları bulunur

- .push() = elemanı arrayın sonuna ekler
- .pop() = sondaki elemani array icerisinden cikarip verir
- .shift() = ilk elemanı array içerisinden cikarıp verir
- .unshift() = elemani arrayin basina ekler

.length ile array icerisinde kac eleman oldugunu ogrenebiliriz.
