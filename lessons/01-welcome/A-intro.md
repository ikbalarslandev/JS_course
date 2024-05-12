---
title: "Intro"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## Javascript nedir ?

Javascript anlık olarak işlenen (lightweit interpreted ([JIT "just in time" compiled][jit])) ,birinci sınıf fonksyonları ([first class functions][fcf]) kullanan , prototip temelli ([prototype-based][pb]) , tek seferde tek iş yapabilen ([single-threaded][st]) , [dinamik][dl] bir programlama dilidir.

Javascript ile ilgili bilgi almak için en doğru yol [dökümantasyonu][ecma] okumak veya Mozilla Developer Network yada daha kısaltılmış haliyle [MDN][mdn] websitesi üzerinden arama yapmaktır. Dökümantasyonu okumak daha karmaşık olacağından çoğunlukla mdn yeterli olacaktır.

```
let js = {
    isim: "JavaScript",
    kısaltımı: "JS",
    mükemmelMi: true,
    gerçek_adı: "ECMAScript",
    doğum_tarihi: 1995,
    yaratıcısı: "Brendan Eich"
};
if (js.mükemmelMi) {
    bağır("JS Mükemmel!");
}
```

> Javascripti websitelerinde , serverlarda(nodejs ile) , mobil uygulamalarda , mikro işlemcilerde ve son olarak Nesnelerin Interneti cihazlarinda kullanabilirsiniz.

## Peki Javascripti nereye yazıcaz?

- Tarayıcı üzerinde bulunan konsol
- Bilgisayarınıza indireceğiniz kod yazma programları ([IDE][ide] olarak bilinir)
- online pratik yapma araçları (örnek olarak CodePen , CodeSandbox)
- html dosyasında script etiketi açarak.

[jit]: https://en.wikipedia.org/wiki/Just-in-time_compilation
[fcf]: https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function
[pb]: https://developer.mozilla.org/en-US/docs/Glossary/Prototype-based_programming
[st]: https://developer.mozilla.org/en-US/docs/Glossary/Thread
[dl]: https://developer.mozilla.org/en-US/docs/Glossary/Dynamic_typing
[ecma]: https://262.ecma-international.org/9.0/#Title
[mdn]: https://developer.mozilla.org/en-US/
[ide]: https://developer.mozilla.org/en-US/docs/Glossary/IDE
