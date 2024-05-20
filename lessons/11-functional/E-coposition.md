---
title: "Function Composition"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

function composition karmaşık programları pure functionlar ile yapmamızı sağlar.

```
var ender = (ending) => (input) => input + ending;

var adore = ender("rocks");
var anounce = ender(", y'all");
var exclaim = ender("!");

var hypeUp = (x)=> exclaim(announce(adore(x)))

hypeUp("JS"); // JS rocks, y'all!
hypeUp("FP"); // FP rocks, y'all!
```

okunurluğu arttırmak için pipeline fonksyonu kullanılabilinir.

```
function pipeline(...functions){
  if(length(functions) === 0) return input =>input;
  if(length(functions) === 1) return head(functions)(input);
   return function(input){
        return pipeline(...tail(functions))(head(functions)(input));
   }
}
```

## Immutability

özellikle beraber çalışırken verileri değiştirmememiz çok önemli. verileri değiştirmek yerine yeni bir koleksyon oluşturup onun uzerinde işlem yapmalıyız.

veriler değiştiriliyor (tehlikeli)

```
let cities = ["Delhi","Bombay","Banglore"];

cities[1] = "Mumbai";

cities: // "Delhi","Mumbai","Banglore"

```

veriler sabit(olması gereken)

```
const oldCities = ["Delhi","Bombay","Banglore"];

const newCities = oldCities.map(city =>{
 if(city ==="Bombay") return "Mumbai";
 return city;
})

newCities; // "Delhi","Mumbai","Banglore"
```

fakat verileri kopyalamak verimli değil, hafızada fazla alan kaplıyorlar.

bu durumu çözmek için _Immutable Data Structures_ kullanabiliriz.

## Immutable Data Structures

structural sharing kullanılarak değiştirilmeyen verileri tekrar kullanabiliriz.

bunun için kullanabileceğimiz iki farklı kütüphane var:

- immutable.js
- immer

bu kütüphaneler tree kullanarak değişmeyen datayı tekrar kullanmamıza olanak sağlar.
