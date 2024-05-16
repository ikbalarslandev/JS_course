---
title: "Strict Mode"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## Dynamic global variable

global variable enviroment içerisinde bulunmayan bir değişkene fonksyon içerisinden değer atamak istersek bu değişken global memory de otomatik olarak oluşturulur.

```
var teacher = "ikbal";

function otherClass(){
  teacher = "Mesut";
  topic = "javascript";
  console.log("Hello!")
}

otherClass();

teacher;            // "Mesut"
topic;              // "javascript"
```

`topic` değişkenine "javascript" değişkenini atadığımızda topic değişkeni global memory de otomatik olarak oluşturulur.

javascript ilk çıktığında yeni başlayan yazılımcıların hatalarını telafi etmek için konan bu özellik dil içerisindeki bug olarak kabul edilebilir

bu durumdan kurtulmak için strict mode kullanabiliriz.

## Strict Mode

dynamic global variable özelliğini kapatmak için kullanılır. kodun başına `"use strict"` yazılarak aktifleştirilir.

```
"use strict"

var teacher = "ikbal";

function otherClass(){
  teacher = "Mesut";
  topic = "javascript";
  console.log("Hello!")
}

otherClass();

teacher;            // "Mesut"
topic;              // "javascript"
```

bu örnekte kod hata verir topic değişkeni hafızada yok çünkü.
