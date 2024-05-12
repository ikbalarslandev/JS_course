---
title: "Memory Management"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

Javascript motoru verileri hafızata tutmak için iki adet alan kullanır:

- stack
- heap

> Javascript sadece stack ile iletişime geçebilir.

Veri tipleri ikiye ayrılır:

- ilkel tipler: direk olarak stack içerisinde tutulur.

  - String,Number,Boolean,Undefined,Symbol,BigInt

- referans tipler: heap içerisinde tutulur stack içerisinde bulunan referanslarla iletişime geçer.

  - Array , Function , Object

  ![memory image](./images/memory.png)

## Garbage Collector

Düşük seviyeli programlama dillerinde manuel olarak hafızayı temizlemeniz gerekir.

- C , C++

Yüksek seviyeli dillerde ise kullanılmayan veriler otomatik olarak silinir. bu işleme garbage collection (Çöp toplama) denir.

- Javascript , Python , C#
