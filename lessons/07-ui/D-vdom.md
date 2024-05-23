---
title: "Virtual DOM"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

önceki derste kodun okunabilinirliğini arttırmak için convert fonksyonunu oluşturduk bu sayede sadece array üzerinden DOM elementlerimizi görebildik.

bu arraya Virtual DOM yani sanal dom denir.

kullanıcı websitesinde bir değişiklik yaptığında tüm dom silinip güncel hali tekrar oluşturulur. DOM u oluşturmak oldukça enerji tüketen bir işlem bu sebeple performans düşmesine sebep oluyor.

Virtual dom sayesinde kullanıcının değişikliklerine göre sadece değişen kısımları yeniden oluşturup aynı olan kısımları sabit olarak bırakma avantajımız ortaya çıkıyor.

> visual Domu effektif olarak kullanmak için Diffing ve Reconciliation algoritmasını kullanmak gerekir.

Virtual Domu oluşturalım:
app.html

```
<script src="app.js"></script>
```

app.js

```
let name = ""; let jsInput; let jsDiv; let vDOM;

function createVDOM(){
   return [ ['input',name,handle],['div',`Hello, ${name}!`]]
}

function handle (){
  name = jsInput.value
}

function updateDOM(){
  vDOM = createVDOM()
  jsInput = convert(vDOM[0])
  jsDiv = convert(vDOM[1])
  document.body.replaceChildren(jsInput,jsDiv)
}

function convert(node){
  const elem = document.createElement(node[0])
  elem.textContent = node[1]
  elem.value = node[1]
  elem.oninput = node[2]
  return elem
}

setInterval(updateDOM,15)
```

iç içe geçmiş arraylar kullanılarak veya react functional components kullanılarak yapılabilinir.

kullanıcıdan gelen datayı işlemek için adım adım:

- kullanıcı datasını Javascript e gönderme
- data ile VDOM u güncelleriz
- son olarak VDOM u kullanarak DOM u yaratırız.

---

## Composition & Functional Components

javascript kodu VDOM u temsil ediyor ve bu arrayı `map()` kullanarak genelleştirebiliriz .

tekrar kullanılabilen fonksyonları ve data yı kullanarak Virtual DOM u yaratabiliriz.

```
function createVDOM(){
   return [ ['input',name,handle],['div',`Hello, ${name}!`]]
}
```

şuan array içerisinde iki adet array bulunuyor fakat daha fazla olabilirdi bu sebeple kodu her array ile çalışabilicek hale getirmemiz lazım.

bunu başarabilmek için iki şeye ihtiyacımız var:

- `vDOM.map()`
- array elementlerini bağımsız birer elemente dönüştürmek için `...` spread operatörü.

bu sayede yeni element oluşturmak için ekstra kod yazmamıza gerek kalmayacak.

```
let name = ""; let vDOM; let elems;

function createVDOM(){
   return [ ['input',name,handle],['div',`Hello, ${name}!`]], ['div',"great job"]
}

function handle (e){
  name = e.target.value
}

function updateDOM(){
  vDOM = createVDOM()
  elems = vDOM.map(convert)
  document.body.replaceChildren(...elems)
}

function convert(node){
  const elem = document.createElement(node[0])
  elem.textContent = node[1]
  elem.value = node[1]
  elem.oninput = node[2]
  return elem
}

setInterval(updateDOM,15)
```

DOM API fonksyonları callback queue atarken çalıştırıp içerisine argümentleri yerleştirir

```
function handle (e){
  name = e.target.value;
}
```

bu sayede ekstra kod yazmadan kullanıcı verilerini istediğimiz kadar VDOM elementi yaratabiliriz.

```
let posts = ["Ginger","Gez","Ursay","Fen"]
let vDOM;  let elems;

function Post(msg){ return ["div",msg]}

function createVDOM(){
    return [["input",name,handle],
             ...posts.map(post)]
}

function handle(e){
     posts.push(e.target.value)
}

function updateDOM(){
    vDOM = createVDOM();
    elems = vDOM.map(convert)
    document.body.replaceChildren(...elems)
}

function convert(node){
     const elem = document.createElement(node[0])
     elem.textContent = node[1]
     elem.value = node[1]
     elem.oninput = node[2]
     return elem
}


setInterval(updateDOM,15)
```

---

## Performance Improvements

şuanda VDOM her değiştiğinde tüm dom tekrardan silinip yaratılıyor . bu durum performansı düşürüyor.

- veri değiştiğinde auto-update yapabilmek için state hooklarını kullanmalıyız.
- sadece bazı elementlerin sıfırdan yaratılması gerekiyor eski ve yeni vDOM u kıyaslayarak(diffing algorithm)

setInterval ile 15ms de bir update etmek yerine kullanıcı değiştirdikçe update veriyoruz.

app.js

```
let name = ""; let vDOM; let elems;

function updateName(value){
   name = value;
   updateDOM();
}

function createvDOM(){
    return [["input",name,handle],
    ["div",`Hello, ${name}!`] ,
    ["div","Great job!"]]
}

function handle(e){updateName(e.target.value)}

function updateDOM(){
     vDOM = createvDOM()
     elems = vDOM.map(convert);
     document.body.replaceChildren(...elems)
}


function convert(node){
     const elem = document.createElement(node[0])
     elem.textContent = node[1]
     elem.value = node[1]
     elem.oninput = node[2]
     return elem
}

updateDOM()

```

bu kodu herhangi bir data ile kullanılabilicek hale getirelim

app.js

```
const data = {name: ""}; let vDOM; let elems;

function updateData(label,value){
   data[label] = value;
   updateDOM();
}

function createvDOM(){
    return [["input",name,handle],
           ["div",`Hello, ${name}!`] ,
           ["div","Great job!"]]
}

function handle(e){updateData('name',e.target.value)}

function updateDOM(){
     vDOM = createvDOM()
     elems = vDOM.map(convert);
     document.body.replaceChildren(...elems)
}


function convert(node){
     const elem = document.createElement(node[0])
     elem.textContent = node[1]
     elem.value = node[1]
     elem.oninput = node[2]
     return elem
}

updateDOM()

```

herhangi bir data ile kullanılabilicek hale getirerek

`updateData` fonksyonu ile içerisine koyduğumuz dataya kanca atıyor (state hook) bu sebeple bu fonksyona hook denir.

---

Diffing Algoritm

VDOM şimdiki haliyle oldukça kullanışsız eski ve yeni VDOM u karşılaştırarak sadece değişen elementlerin tekrardan yaratılması diffing algoritm sayesinde sağlıyoruz.

```
let name = ""

function createVDOM(){
    return [["input",name,handle],
           ["div",`Hello, ${name}!`],
           ["div","Great job!"]]
}

function handle (e){name = e.target.value}

function findDiff(prev,current){
  for(let i = 0; i < current.length; i++){
     if(JSON.stringify(prev[i]) !== JSON.stringify(current[i])){
        // change the actual dom element
     }
  }
}

conzt vDOM1 = createVDOM()
name = "will"
const vDOM2 = createVDOM()

findDiff(vDOM1,vDOM2)

```

## VDOM İçin Final Kodu

> DOM üzerinde sadece değişen elementlerin yeniden yaratılmasına _DOM Reconciliation_ denir.

app.js

```
let name = ''; let vDOM = createVDOM();
let prevVDOM; let elems

function createVDOM(){
   return [["input",name,handle],
          ["div",`Hello, ${name}!`],
          ["div","Great job!"]]
}
function handle(e){name = e.target.value}

function updateDOM(){
   if(elems == undefined){
       elems = vDOM.map(convert)
       document.body.append(...elems)
   }else{
      prevVDOM = [...vDOM]
      vDOM = createVDOM()
      findDiff(prevVDOM,vDOM)
   }
}


function convert(node){
     const elem = document.createElement(node[0])
     elem.textContent = node[1]
     elem.value = node[1]
     elem.oninput = node[2]
     return elem
}


function findDiff(prev,current){
  for(let i = 0; i < current.length; i++){
     if(JSON.stringify(prev[i]) !== JSON.stringify(current[i])){
       elems[i].textContent = current[i][1]
       elems[i].value = current[i][1]
     }
  }
}

setInterval(updateDOM,15)
```
