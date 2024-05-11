---
title: "Javascript Engine"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

if you run any javascript source code . It always the engine that runs it for you. It doesn't matter if you run it in the browser or nodeJS or an IoT device.

> V8 is javascript engine for crome

javascript is dynamically typed language so we expect it to be slow. right?

#### but javascript is really fast , How is that possible?

- all modern javascript engines use something called _JIT(Just in time compilation)_
  JIT generate machine code during run time, not _AOT(ahead of time)_

- for optimizing they use two compilers
  - _baseline compiler ( V8 uses Ignition):_ it is regular compiler that generates machine code.
  - _optimizing compiler (V8 uses turbofan):_ saves the type information for "hot" functions

since javascript is dynamically typing language we don't know the types when user enters. so compiler needs to find the types each time.

for optimization we use optimizing compiler which does:

- Re-compile: (if it is hot or used a lot) "hot" functions with type information from previous execution
- De-optimize: since javascript dynamically typed language , when the type changes remove it .

> if we don't change the types optimizing compiler can remember the types for the same functions so code can be faster
