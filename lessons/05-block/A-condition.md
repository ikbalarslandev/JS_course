---
title: "Conditions"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

bir olayın olup olmaması bir şarta bağlıysa bu tür durumlarda condition kullanırız.

## if / else

if koşulu oluşturmak için:

- if keywordü
- ()
- {}

() parantez içerisindeki değer boolean alır dogruysa {} içine girer , değilse else {} içine girer.

```
let year = 2000

if (year === 2000){
    console.log("heey")
}

if(year === 2003){
    console.log("hehehe")
}else{
    console.log("Aaaaaa")
}
```

## ternary if

? ve : kullanılarak if else kısa sekilde yazılabilir.

```
if(year === 2003){
    console.log("hehehe")
}else{
    console.log("Aaaaaa")
}
```

ternary if hali

```
year === 2003 ? console.log("hehehe") : console.log("Aaaaaa")
```

## Switch / case

````switch(x) {
  case 'value1':  // if (x === 'value1')
    ...
    [break]

  case 'value2':  // if (x === 'value2')
    ...
    [break]

  default:
    ...
    [break]
}```
````
