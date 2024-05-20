---
title: "Fonksyonel Programlama Nedir?"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

dört çeşit programlama stili bulunur:

- Imperative: sırası ile kodun yazılmasıyla olur ilk önce bunu yap daha sonra bunu yap gibi.
- Declarative: kodun sonucu olarak ne istediğimizi söyleriz fakat kodun nasıl çalışacağını belirtmeyiz.
- Object Orianted : kodlar statüleri ve kopyalanarak miras yolu ile olur.
- functional: herşey pure functionlar ile yapılır.

fonksyonel programlama bir kod yazma stilidir , bazı diller bu stil kod yazmayı destekler:

- Haskell
- F#
- Elm
- Javascript

## Neden Fonksyonel Programlama?

pure fonksyonlar kullanılarak yapılır. yani aynı argumetleri verdigimizde sonucun aynı olduğu için kod daha öngörülebilinir ayrıca test edilmesi de kolaylaşır bu sebeple kod daha güvenli olur.

fonksyonel programlamada herşey fonksyonlarla yapılır.

```
pipe(
 getPlayerName,
 getFirstName,
 properCase,
 addUserLabel,
 createUserTemplate
)([{name: 'will sentance', score: 3}]);
```

## Pure Function

bu fonksyonları aynı argüment ile çağırdığımızda sonuç her zaman aynı olur.dışarı ile iletişim kurmaz.

pure olmayan fonksyon:

```
let name = "Alonzo";

function greet(){
    console.log(`Hello, ${name}`)
}

greet(); // Hello, Alonzo!

name = "Alan";
greet();//Hello , Alan!

```

pure fonksyon:

```
funciton greet(name){
    return `Hello,${name}`
}

greet("Alonzo"); // Hello, Alonzo!

greet("Alan"); // hello, Alan!
```

## Side Effect

fonksyon içerisinde dışarı ile iletişime geçilmesine side effect denir.

side effect pure fonksyonlarda bulunmaz.
