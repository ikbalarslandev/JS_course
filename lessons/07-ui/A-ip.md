---
title: "Getting IP Address"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

tarayıcının websitesini yüklemesi için server üzerinden html indirmesi gerekir.

server dediğimiz şey internette bulunan bir bilgisayarı temsil eder.

internet üzerinde milyonlarca server var peki hangi server üzerinden veri çekeceğini tarayıcı nereden biliyor.

cevap: domain urli sayesinde.

fakat bir sorun var , `www.website.com` domain urli tarayıcı için birşey ifade etmiyor.

tarayıcı ancak ip adreslerini kullanarak serveri bulabilir.

bu sebeple domain adresini kullanarak ip adresini bulması gerekiyor. bu işleme DNS resolving yani domain çözümleme denir.

çözümleme yapılırken domain parçalara ayrılır.
`www.website.com`

- `www`
- `website`
- `.com`

ilk olarak domain adresi .com ile biten tüm serverlerin ip adresini içerisinde bulunduran serveri buluruz.

daha sonra bu servera `website.com` ip adresini sorarız
bu server sonu `website.com` ile biten tüm serverlarin ip adreslerini bulundurur.

son olarak bu servera `www.website.com` un ip adresini sorarız. bu işlemin sonunda serverimizin ip adresini bulmuş oluruz.

bulduğumuz ip adresi ile TCP bağlantısı yaparız

server ile iletişim kurmaya hazırız.

## Root Name Server

bu server tüm ana serverların ip adreslerini bulundurur

bu servera sonu `.com` ile biten tüm ip adreslerinin bulunduğu serverin ip adresini sorarız.

bu server bize sonu .com ile biten ip adreslerinin tutulduğu serverin ip adresini verir.

## Top Level Name Server

bu server `.com` ile biten tüm serverların ip adreslerini bulundur.

bu servera sonu `website.com` ile biten tüm ip adreslerini içinde bulunduran serverin ip adresini sorarız.

## Authorative name server

bu server sonu `website.com` ile biten tüm serverların ip adreslerini bulundurur.

bu servera `www.website.com` ile biten serverin ip adresini sorarız.

## TCP Connection

şuan serverin ip adresini biliyoruz. tarayıcı ile server arasında bir bağlantı kurmamız gerekiyor bu bağlantıya TCP bağlantısı denir.

bu bağlantı yapıldıktan sonra server ile iletişime geçebiliriz.
