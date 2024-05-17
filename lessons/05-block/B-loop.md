---
title: "Loops"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

Döngü aynı kod parçacığının birden fazla defa çalıştırılmasına denir.

# while

```
let i = 0;
while (i < 3) { // önce 0, sonra 1, sonra 2
  alert( i );
  i++;
}
```

koşul doğru iken(while), döngü gövdesinde bulunan kod çalıştırılır.

Örneğin, aşağıdaki kod i < 3 iken çalışır.

## do while

do..while döngüsü kullanarak koşul kontrolünü sonda yapmak mümkündür.Bu şekilde döngü yazımı çok nadir olarak kullanılır. Kullanılmasının en önemli amacı en azından bir defa ne olursa olsun gövdenin çalıştırılma istenmesidir.

```
let i = 0;
do {
  alert( i );
  i++;
} while (i < 3);
```

# for

for döngüsü en fazla kullanılan döngüdür.

```
for (let i = 0; i < 3; i++) { // shows 0, then 1, then 2
  alert(i);
}
```

# donguyu kirma

Normalde döngüler koşul yanlış olduğunda biter.

Fakat bazı durumlarda bu döngü kırılabilir ( break ).

Örneğin, kullanıcıdan bir dizi sayı girmesini istediniz eğer boş bir değer girerse döngüyü kırabilirsiniz.

```
let toplam = 0;

while (true) {

  let deger = +prompt("Bir sayı giriniz", '');

  if (!deger) break; // (*)

  toplam += deger;

}
alert( 'Toplam: ' + toplam );
```

# bir sonrakine gecme

continue, break in daha hafif versiyonudur. Döngüyü tamamen kırmaz da zorla bir sonraki tekerrüre geçer(tabi koşul sağlanıyorsa)

O anda tekrar eden değer ile işimiz bitti ve bir sonraki tekrar geçmek istendiğinde continue kullanılır.

```
for (let i = 0; i < 10; i++) {

  // Eğer 2'ye bölünebiliyorsa bir sonraki adıma atlar.
  if (i % 2 == 0) continue;

  alert(i); // ekranda 1, 3, 5, 7, 9 değerleri gösterilir.
}
```
