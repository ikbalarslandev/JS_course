---
title: "Functions"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

fonksyonlar bir işlem yapılırken kullanılır ve tekrar tekrar kullanılabilinir.

fonksyonlar objecten türetilmiştir.

fonksyon tanımı yaparken üç şey kullanılır:

- function kelimesi
- ()
- {}

```
function showMessage(){
    alert("Hello everyone!")
}
```

> fonksyon tanimina isim vermek zorunda değiliz.

fonksyonların kendi lexical scopları bulunur.

return ile fonksyon sonlandirilir.

## parameter ve argument

```
function showMessage(a){
return    console.log(a)
}

showMessage("araba")
```

burada `a` parameter `"araba"` argument
