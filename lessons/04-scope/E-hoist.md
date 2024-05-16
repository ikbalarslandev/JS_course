---
title: "Hoisting"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

Javascript Lexical scope ile çalışır yani javascript kodu dönüştürürken ilk olarak scopelar belirlenir ve değişkenler hafızada kaydedilir.daha sonra ikinci kez kontrol ettiğinde kodu çalıştırır.

bu sebeple bir değişkeni oluşturmadan önce kullanabiliriz. bu duruma hoisting denir.

```
student;      //??
teacher;      //??


var student = "you";
var teacher = "Ikbal";
```

_function_ ve _var_ hoist olabilir.

_let_ ve _const_ da hoist olabilir ama daha farklı şekilde. kod çalıştırılırken degişken tanımına gelene kadar, değişkene _uninitialized_ değeri atanır.

`var` ve `let,const` arasındaki fark:

- var ile bir değişken yaratıldığında. scope başladığında değişken _undefinded_ değerini alır.

- let veya const ile bir değişken yaratıldığında değişken _uninitialized_ değerini alır.
