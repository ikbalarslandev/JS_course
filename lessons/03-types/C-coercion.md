---
title: "Coercion"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

Javascript içerisinde veri tiplerini birbirine dönüştürmeye _coercion_ denir.

> değişken tiplerini birbirine çevirirken her zaman ilkel tipe çeviririz. asla referans tipe çeviremeyiz.

değişkenlerin veri tiplerini birbirine çevirirken 4 adet fonksyon kullanırız

- ToPrimitive(hint)
- ToString()
- ToNumber()
- ToBoolean()

## ToPrimitive(hint)

Eğer referans tipi ilkel tipe çevirmek istiyorsak bu fonksyonu kullanmalıyız.

bu fonksyonu çağırırken opsyonel olarak hint değeri verebiliriz bu basitçe fonksyonun sonucu olarak hangi tipi istediğimizi gösterir.

> Eğer referans tipi bu fonksyonla çağırdıktan sonra cevap ilkel tip değilse sonucu aynı fonksyonun içerisine yazıp tekrar cağırır. sonuç ilkel tip olana kadar bu döngü devam eder.

hint olarak sadece iki değer verebiliriz. `string` ve `number`

- eğer hint olarak number verirsek:
  ilk olarak `valueOf()` fonksyonu çağırlır. eğer cevap ilkel tipse fonksyon burada sonlanır. değilse sonuç `toString()` içerisine yazılır.

- eğer hint olarak string verirsek:
  ilk olarak `toString()` fonksyonu çağırlır. eğer cevap ilkel tipse fonksyon burada sonlanır. değilse sonuç `valueOf()` içerisine yazılır.

  ## ToString()

  bu fonksyon herhangi bir değeri yazı formuna dönüştürür.

```
null  => "null"
undefined => "undefined"
0 =>  "0"
true => "true"
```

> eğer bu fonksyon içerisine referans tip koyarsak otomatik olarak `ToPrimitive(string)`çağırılır.

- ToString(Array)

```
[] => ""
[1,2,3] => "1,2,3"
[null,undefined]  => ","
[[],[],[]] => "..."
[...] => "..."
```

dizileri yazıya çevirirken `[]` silinir yerine `""` yazılır.

- ToString(Object)

```
{} => "[object Object]"
{a:2} => "[object Object]"
{toString(){return "X";}}  => "X"
```

objeleri yazıya çevirirken`{}` silinir yerine `"[]"` yazılır.

## ToNumber()

numara olmayan bir değişken ile matematiksel işlem yaptığımızda bu fonksyon otomatik olarak çağırılır.

```
"" => 0
"0" => 0
"009" => 9
"3.0"  => 3
"hello" => NaN
false  => 0
true   => 1
null   => 0
undefined  => NaN
```

> eğer bu fonksyon içerisine referans tip koyarsak otomatik olarak `ToPrimitive(number)`çağırılır.

- ToNumber(Array)

```
[""]  => 0
["0"]  => 0
[null] => 0
[undefined] => 0
[1,2,3]  => NaN
[[[[]]]] => 0
```

- ToNumber(Object)

```
{..} => NaN
{valueOf(){return 3;}}  => 3

```

## ToBoolean()

eğer fonksyon içerisine aşşağıdaki değerlerden birini koyarsak sonuç false olur aksi taktirde sonuç true olur.

- ""
- 0
- NaN
- false
- undefined

---

# Boxing

javascript içerisinde ilkel tiplerde propertylere erişimimiz _boxing_ sayesinde sağlanır. bu otomatik coercion olarak bilinir.

```
if(studentName.value.length > 50){
console.log("name too long")
}

```

string , object olmamasına rağmen object gibi davranabildi. bu boxing sayesinde mümkün oldu.

# Coercion Açıkları

her dil içerisinde dilin açıkları bulunur. buna javascrit de dahil. javascriptin coercion açıkları bu şekilde

```
1 < 2 < 3;       //true
(1 < 2) < 3;
(true) < 3;
 1 < 3;         // true



3 > 2 > 1;        // false Hmm...

(3 > 2) > 1;
(true) > 1;
1 > 1          // false

```

burada 1 < 2 < 3 şans eseri doğru çıktı
