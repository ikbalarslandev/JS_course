---
title: "Display Content"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

ilk olarak tarayıcı domain urle bakıp hangi serverden(bilgisayar) veri isteyeceğini belirler. domain urli sayesinde serverin ip adresine ulaşır.

daha sonra ip adresine get request yapıp yanlızca html dosyası tarayıcıya indirir.

html dökümanı parse edilir yani dönüştürülür.

> DOM + Rendering = Web Core

## DOM

dönüştürme başlamadan önce tarayıcı üzerinde bir adet C++ object oluşturulur.

html parser kullanarak html elementleri tarayıcıda bulunan object içerisine node olarak yaratılır. bu nodelar iç içe yaratıldığından bu object e tree diyebiliriz.

bu object içerisinde bulunan node lar sayfanın(document) içerisinde bulunan elementleri simgeliyor yani modelliyor diyebiliriz.

bu sebeple oluşturulan bu C++ objesine Document Object Model kısaca DOM diyebiliriz.

## CSSOM

html parse edilirken eğer `<link rel="stylesheet" href="mystyle.css">` elementi bulunursa eğer.

başka bir C++ objecti oluşturulur.bu object içerisinde css içerisindeki elementler nodelara dönüştürülerek tree olarak kaydedilir

## Render Tree

tarayıcı DOM ve CSSOM kulllanarak _sadece ekranda görünen_ elementleri belirler ve bunlardan Render Tree yaratılır.

> Render tree sadece ekranda görünen elementleri içerir.

## Layout

render tree kullanılarak layout oluşturulur. yani her elementin pozisyonu ve ne kadar yer kaplayacağı hesaplanır.

> birden fazla layer varsa tüm layerlar için layout oluşturulur.

## Paint

layout ile belirlenen pozisyonlara elementler css ile beraber yazdırılır.

> birden fazla layer varsa tüm layerlar için paint yapılır.

## Composite

paint aşamasında eğer birden fazla layer varsa bunları birleştirip tek bir layer oluşturur.

bu tek layer bilgisayardaki grafik kartına gönderilir. grafik kartı ekranı yazdırır.
