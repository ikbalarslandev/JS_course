---
title: "Memory Management"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

Javascript engine has two different places to store memory.

- stack
- heap

> javascript only can comunicate with stack memory.

Data Types:

- Primitive types: primitive types stored directly in the stack
  - String,Number,Boolean,Null,Undefined,Symbol,BigInt
- Referance types: Stored in the heap and accesed by reference from Stack
  - Arrays , Functions , Objects

---

For low level languages you should free up memory manually

- C , C++

For Higher level languages memory frees automatically when they are not used anymore. this process called _garbage collection_

- Javascript , Python , C#
