---
title: "Execution Context"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

Execution Context basitçe kodun çalışmasını ifade eder. kodun çalışması için iki şeye ihtiyacımız var:

- Thread of Execution
- Hafıza

iki çeşit execution context bulunur:

- Execution Context: bir fonksyonun çalışması
- Global Execution Context : Tüm sayfanın çalışması

## Execution context nasıl çalışır:

```
const  num= 3
function mutliplyby2( inputNumber ){
    const result=inputNumber*2;
    return result
}


const output= multiplyby2(num)
```

Sırasıyla bunlar yapılır:

##### global execution context

- `num` parametresine `3` argumenti atanır ve hafızaya kaydedilir
- `multiplyBy2` parametresine fonksyon tanımı atanır ve hafızaya kaydedilir.
- `output` parametresi yazilir ve birşey atanmaz.
- `multiplyBy2(num)` için execution context oluşturulur.

##### execution context

- call stack içerisinde en üste `multiplyBy2(num)` değeri gelir.
- num değeri global memoryden alınır `multiplyBy2(3)`
- local memory de result parametresine (2x3=6) 6 argumenti yazilir `result=6`
- daha sonra result değeri fonksyonun değeri olarak döndürülür.
- fonksyonun değeri `output` parametresine argument olarak yazılır.
- `multiplyBy2(num)` callstack den silinir.
- garbage collector local memory siler.
