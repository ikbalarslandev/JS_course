---
title: "Equality"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## == vs. ===

`==` allows coercion (types different will work)
`===` disallows coercion ( types has to be same)

#### `==` algorithm:

- if the types are same : `===`
- if `null` or `undefinded`:equal
- if non-primitives: ToPrimitive
- if two different primitives converts them to number then compare.

#### Corner cases of ==

```
[] == ![]   //true  What!!

var workshop1Students = [];
var workshop2Students = [];

if(workshop1students == !workshop2Students){
// true whattt!!
}

if(workshop1Students != workshop2Students){
//true what!!
}
```

```
if(workshop1students != workshop2Students){
\\if([] == false){
\\if("" == false){
\\if(0 == false){
\\if(0 === 0){

// true

```

boolean corner case

```
var workshopStudents = [];

if(workshopStudents){
// yep
}

if(workshopStudents == true){
//nope  :(
}

if(workshopStudents == false){
// yep  :(
}


```

> for Avoiding corner cases

- `==` with 0 or ""(or even " ")
- `==` with non-primitives
- `== true` or `== false`

what should you use for equality.

- You should always prefer double equals everytime.
- when the types are same double equals will convert to triple equals anyway.

Summary:
if you know the types use `==` if not use `===`

> Object.is() is acts like quadriple equals.
