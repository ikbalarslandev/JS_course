---
title: "Module Pattern"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## Module Pattern

Module pattern sayesinde tüm kodları bir sayfaya yazmak yerine küçük sayfalar oluşturup tek bir sayfaya import edebiliriz bu sayede kodun okunabilirliüi artar.

> modüller verileri kapsuller. verilerin statüsü closure sayesinde takip edilebilir.

```
function workshopModule(teacher){
   var publicAPI = {ask,};
   return publicAPI;

   function ask(question){
      console.log(teacher,question);
   }
}

var workshop = workshopModule("Ikbal");

workshop.ask("It's a module right?")

```

teacher private olduğu için ulaşılamaz yani kapsullenmiştir.

## ES6 Modules

sayfanın uzantısını .mjs (module javascript) kullanarak bu özelliği aktifleştirebiliriz.

`export` ve `import` keywordları kullanılarak moduller kullanılır.

default olarak module içerisindeki herşey private yani dışarıdan erişilemez şekilde kapsüllenmiştir. dışarıdan erişim olmasını istediğimiz değişkenlerin başına `export` keywordu yazılır.

modüller sayfa tabanlı çalışır yani bir sayfada birden fazla modül yazılamaz.

kodu çalıştırdığımızda tüm moduller birleştirilerek tek bir javascript sayfası oluşturlur. javascript motoru bu tek sayfayı okur.

modüller singletlon dur yani ne kadar import yaparsak yapalım her zaman aynı modulu referans gösterir.

```
// workshop.mjs
var teacher = "Ikbal";

export default function ask(question){
     console.log(teacher,question)
}

```

---

```
import ask from "workshop.mjs";

ask("It's a default import, right?");
// Ikbal its a default import, right?
```

veya

```
import * as workshop from "workshop.mjs";

workshop.ask("It's a namespace import, right?")
```

şeklinde moduller import edilip kullanılabilir.
