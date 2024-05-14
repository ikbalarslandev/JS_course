---
title: "Coercion"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

In Javascript we name type conversion as _coercion_

for converting types we use abstract operations.

## ToPrimitive(hint)

if we have something not primitive and want to convert it to primitive we always call that funciton in the background.

it does takes an optional type hint. In another way it asks if it is not a primitive tell me which type you want as result.

> when we call the function and the result is not primitive then it will call the same function with result until it get a primitive result or an error.

as a hint we can only use two thing `string` and `number`:

- if we give number as hint :
  it will call `valueOf()` function first and it will check the result. if it gives primitive then we are done. if not it will pass result as argument to `toString()` if we try both of these and the result still not primitive then it will return an error.

- if we give string as hint:
  then we will change the order first we will call `toString` then we will call `valueOf()`

  ## ToString()

  it takes any value and gives us representation of that value in string form.

```
null  => "null"
undefined => "undefined"
0 =>  "0"
true => "true"
```

> if we put a referance type in ToString it will call `ToPrimitive(hint)` automatically.

- ToString(Array)

```
[] => ""
[1,2,3] => "1,2,3"
[null,undefined]  => ","
[[],[],[]] => "..."
[...] => "..."
```

when we convert arrays to string it removes `[]` and puts `""` instead.

- ToString(Object)

```
{} => "[object Object]"
{a:2} => "[object Object]"
{toString(){return "X";}}  => "X"
```

when we convert objects to string it removes `{}` and it puts `"[]"`

## ToNumber()

when we need to do something numeric and we don't have a number we are gonna invoke toNumber() operation

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

> if we put a referance type in ToNumber it will call `ToPrimitive(hint)` automatically.

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

if the value is on that list it will return false if not it will return true.

- ""
- 0
- NaN
- false
- undefined

# Boxing

in javascript we can access properties from primitive values. it is happens because of _boxing_ it is a form of implicit coercion.

```
if(studentName.value.length > 50){
console.log("name too long")
}

```

string is not an object but it can behave like an object.because of boxing.

# Corner Cases

every language has type conversion corner cases.

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

in this case 1 < 2 < 3 returned true by chance.
