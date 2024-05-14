---
title: "Abstract Operations"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## typeof operator

when we assign any value to a variable, we are not asking what is the type of the variable we are asking what is the type of value which is currently set to variable.

all the 6 primitive types are:

```
var v;
typeof v;                         //"undefined"
v = "1";
typeof v;                         //"string"
v = 1;
typeof v;                         // "number"
v = true;
typeof v;                         // "boolean"
v = 42n;
typeof v;                         // "bigInt"
v = Symbol();
typeof v;                         // "symbol"
```

> the result of the typeof operator always is a string , it guarantees that it always return a string.

> if you want to unset a primitive type value you will set `undefined` but if you want to unset an referance type you will set `null` because of that type of null is object.

## Kinds of Emptyness

### undefined vs. undeclared vs. uninitialized

undeclared: it means never been created in any scope that we have access to.

undefined: it means there is definitly a variable and at the moment it has no value.

uninitialized: when a variable in TDZ(temporal dead zone) we didn't read the variable yet.

## NaN & isNaN(not a number)

NaN is a type what we get if we try to do math operation with not a number it will return not a number.

NaN is the only value which is not equal to itself.

so for checking if something is nan we can't use `something === NaN` because even if it is equal to NaN it wont be equal to itself .

so for checking nan we should use `isNaN()` to check nan.

as defalult NaN will convert argument to a number then check the NaN.

we can use `Number.isNaN()` instead so it won't convert the argument . it will directly check if it is nan or not.

> typeof NaN is number . it is just invalid number. type of invalid number definetly is a number.

```
var myAge = 38;                           // 38
var myNextAge = 39;                       // 39
var catsAge = "hello";                    // NaN

catsAge - "my son's age";                 // NaN

myCatsAge === myCatsAge;                  // false

isNaN(myAge);                             //false
isNaN(catsAge);                           //true
isNaN("my son's age");                    //true  OOPS!

Number.isNaN(catsAge);                    //true
Number.isNaN("my son's age");             //false

```
