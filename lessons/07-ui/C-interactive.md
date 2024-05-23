---
title: "User Interactivity"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

Web 2 nin iki amacı var:

- kullanıcının etkileşime geçeceği sayfalar oluşturmak.
- kullanıcının verilerine göre verileri değiştirebilme

peki ya kullanıcı websiteyi aktif olarak değiştirmek isterse.

şu konuda anlaşalım C++ object(DOM) direk olarak editlenemez.

## Js dosyasının indirilmesi

html parser html içerisinde bulunan elementleri DOM içerisinde bulunan notlara sırayla dönüştururken eğer
`script src="..."` elementi ile karşılaşırsa parse işlemi durur

- server üzerinden js dosyası indirilir
- kode execute edilir
  daha sonra html parse edilmeye devam eder.

en kısa sürede ekranda birşey yazılmasını istediğimiz için script elementlerini html kodunun en altına yazmak iyi bir fikir. buna alternatif olarak attribute kullanabiliriz.

- async
- defer

async: `<script async src="..."`
javascript kodu indirilir fakat aynı zamanda html parser işlemine devam eder. kod indirildikten sonra script execute edilir bu işlem yapılırken html parser durur. işlem bittikten sonra parse etmeye devam eder.

defer: `<script defer src="..."`
html parse işlemi bittikten sonra javascript indirilir ardından execute edilir.

## peki javascript kullanarak bir kodu ekrana nasıl yazdırabiliriz?

iki şey kullanarak kodu ekrana yazdırabiliriz.

- WebIDL(interface decription language)
- WebCore(DOM ve CSSOM)

webIDL:
javascipt üzerinden dom elementlerine ulaşmak için oluşturulmuş bir dildir. bu sayede javascript tarayıcı ile iletişim kurabilir.

> DOM API WebIDL dilinde yazılmıştır.

index.html

```
<input/>
<div></div>
<script src="script.js"></script>
```

script.js

```
let post = ""
const jsInput = document.querySelector('input');
const jsDiv = document.querySelector('div');

function handleInput(){
   post = jsInput.value
   jsDiv.textContent = post
}

jsInput.oninput = handleInput
```

html parser html dosyasını kullanarak DOM yaratır

ardından querySelector:

- dom içerisinde gizli link ile ulaşır
- elindeki elementin burada bulunup bulunmadığını sorar.
- eğer bulunuyorsa bu node u temsil eden yeni bir javascript objesi yaratılır(gizli link ile DOM Nodeuna bağlı)

---

eğer kullanıcı sayfada herhangi birşeyi değiştirirse Dom değişir , otomatik olarak bu nodu referans alan javascript objesinin içindeki fonksyon callback queue içerisine alınır. fonksyon call stack içerisine gelince otomatik olarak çağırılır.

app.html

```
<input/>
<div></div>
<script src="app.js"></script>
```

app.js

```
let post = ""
const jsInput = document.querySelector("input");
const jsDiv = document.querySelector("div");

jsInput.value = "What's on your mind?";

function handleInput(){
    post = jsInput.value
    jsDiv.textContent = post
}

function handleclick(){
     jsInput.value = ""
}

jsInput.oninput = handleInput
jsInput.onclick = handleclick
```

eğer kullanıcı arayüzde birşey değiştirirse DOM gereksiz bir şekilde tekrar tekrar silinip yeniden oluşturulur. bu performansı olumsuz etkiler.

---

state:
bir değişkenin sahip olduğu değeri temsil eder.

DOM uzerinde bir node değişince bu değere gizli link ile bağlı olan değişkenin state i de değişir.

peki ya javascript uzerinde tüm dom a sahip olsaydık ve isteğimize göre dom u oluşturabilseydik

bu sayede event listenerlar ile dom u takip etmek yerine state leri javascript üzerinden takip etme olanağımız ortaya çıkıyor.

bu sayede elementlerin statelerini javascript uzerinden takip edebiliriz.

peki ya javascript üzerinde dom u temsil eden elementleri bulundursak ve bunları state ile kontrol etsek ve bir algoritma ile sadece değişen kısımların dom üzerinden yeniden oluşturulabilinebileceğini söylesem?

bu sayede DOM sıfırdan silinip tekrar yaratılmak yerine sadece değişen kısımları yeniden oluşturup geriye kalan kısımlar sabit kalabilir.
bu durum performans avantajı oluşturur.

haydi beraber oluşturalım:

ilk olarak ui komponentleri oluşturmamız gerek. DOM elementi oluşturan fonksyonlara UI Component denir.

app.html

```
<script src="app.js"></script>
```

app.js

```
let post = "";
let jsInput , jsDiv;

function dataToView(){
  jsInput = document.createElement("input")
  jsDiv = post == "Will" ? "":document.cretateElement("div")

  jsInput.value = post
  jsDiv.textContent = post
  jsInput.oninput = handleInput
document.body.replaceChildren(jsInput,jsDiv)
}

function handleInput(){
   post = jsInput.value
}

setInterval(dataToView,15)

```

> bu kod içerisinde dataToView fonksyon bir ui component

bu kodun okunabilirliğini arttırmak için _template literal_ kullanabiliriz.

```
let textToDisplay = `Hello, ${name}!`
```

bu sayede kodun okunabilirliği artar

```
let name = "Jo"

const divInfo = ['div','Hi, ${name}!']

function convert(node){
   const elem = document.createElement(node[0])
   elem.textContent = node[1];
   return elem
}

const jsDiv = convert(divInfo)
```

convert fonksyonu sayesinde div info arrayını kullanarak DOM elementi oluşturduk.

sadece arraya bakarak dom elementlerini görebildiğimiz için kodun okunabilinirliği arttı.
