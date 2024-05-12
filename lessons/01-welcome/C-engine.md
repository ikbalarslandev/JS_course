---
title: "Javascript Engine"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## Javascript motoru

Eğer bir javascript kodunu çalıştırmak istiyorsanız . Bunu sizin için Javascript motoru yapar. Kodu nerede çalıştırırsanız çalıştırın tarayıcı , nodeJS , mikroişlemci bu değişmeyecektir.

> V8 crome içerisinde bulunan Javascript motorunun adı.

javascript dinamik bir dil bu yüzden yavaş olmasını bekleriz değil mi ?

_Fakat_ Javascript oldukça hızlı , bu nasıl mümkün olabilir ?

- all modern javascript engines use something called _JIT(Just in time compilation)_
  JIT generate machine code during run time, not _AOT(ahead of time)_

  Tüm modern Javascript motorları [JIT][jit] (Just in Time compilation) kullanıyor. JIT kod çalışırken aynı anda makine kodlarını üretir. Bu sayede kod oldukça hızlı çalışır.

  makine kodlarını üretirken daha hızlı çalışmak için iki adet dönüştürücü kullanırlar:

  - _baseline compiler (V8 Ignition kullanır):_ makine diline dönüştürür.
  - _optimizing compiler (V8 turbofan kullanır):_ fazla kullanılan değişkenlerin veri tipi bilgisini hafızada tutar.

Javascript dinamik bir dil olduğundan dolayı, değişkenin veri tipini bilemeyiz. bu sebeple dönüştürücü her defasında veri tipini bulmak zorundadır.

bu durumu hızlandırmak için optimize edici dönüştürücü kullanırız.
optimize edici dönüştürücü iki şey yapar:

- Re-compile: eğer bir değişken sıkça kullanılıyorsa o değişkenin veri tipini hafızaya kaydeder.
- De-optimize: eğer sıkça kullanılan değişkenin veri tipini değiştirirsek. o değişken için hafızada kaydedilen veri tipini hafızadan siler.

> Eğer kodun hızlı çalışmasını istiyorsak değişkenin veri tipini _değiştirmemeliyiz_

[jit]: https://en.wikipedia.org/wiki/Just-in-time_compilation
