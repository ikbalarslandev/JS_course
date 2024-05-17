---
title: "class"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

```
class Workshop {
   constructor(teacher){
      this.teacher = teacher;
   }
   ask(question){
      console.log(this.teacher,question)
   }
}


var deepJS = new workshop("Ikbal");
var reactJS = new workshop("Suzy");

deepJS.ask("Is 'class' a class?");
//Ikbal Is 'class' a class?

reactJS.ask("Is this class OK?");
// Suzy Is this class OK?
```

> extends , super
