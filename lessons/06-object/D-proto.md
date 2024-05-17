---
title: "Prototypes"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

her javscript sayfası Object tir ve bu object içerisinde prototype propertysi bulunur.
Object.prototype

herhangi bir obje yarattığımızda aynı anda prototype objesini de beraberinde yaratırız. prototypelar birbirine lin```
var workshop = {
setTeacher(teacher){
this.teacher = teacher;
},
ask(question){
console.log(this.teacher,question);
}
};

var AnotherWorkshop = Object.assign(
Object.create(workshop),
{
sepeakUp(msg){
this.ask(msg.toUpperCase());
}
}
);

var JSRecentParts = Object.create (AnotherWorkshop);
JSRecentParts.setTeacher("Ikbal");
JSRecentParts.speakUp("But isn't this cleaner?");
// Ikbal But isn't this cleaner?

```k ile bağlıdır.

```

function workshop(teacher){
this.teacher = teacher;
}

workshop.prototype.ask = function(question){
console.log(this.teacher,question);
}

var deepJS = new workshop("Ikbal");
var reactJS = new workshop("Suzy");

deepJS.ask("Is 'prototype' a class")
// Ikbal Is 'prototype' a class

reactJS.ask("Isn't 'prototype' ugly?");
// Suzy Isn't 'prototype' ugly?

```

constructor ile objeye prototype ile objenin prototipine ulaşabiliriz.

```

function workshop(teacher){
this.teacher = teacher;
}

workshop.prototype.ask = function(question){
console.log(this.teach`
var workshop = {
  setTeacher(teacher){
     this.teacher = teacher;
  },
  ask(question){
     console.log(this.teacher,question);
  }
};`
var workshop = {
setTeacher(teacher){
this.teacher = teacher;
},
ask(question){
console.log(this.teacher,question);
}
};

var AnotherWorkshop = Object.assign(
Object.create(workshop),
{
sepeakUp(msg){
this.ask(msg.toUpperCase());
}
}
);

var JSRecentParts = Object.create (AnotherWorkshop);
JSRecentParts.setTeacher("Ikbal");
JSRecentParts.speakUp("But isn't this cleaner?");
// Ikbal But isn't this cleaner?

````

var AnotherWorkshop = Object.assign(
   Object.create(workshop),
   {
       sepeakUp(msg){
           this.ask(msg.toUpperCase());
       }
   }
);


var JSRecentParts = Object.create (AnotherWorkshop);
JSRecentParts.setTeacher("Ikbal");
JSRecentParts.speakUp("But isn't this cleaner?");
// Ikbal But isn't this cleaner?
```er,question);
};

var deepJS = new workshop("Ikbal");

deepJS.constructor === workshop; // true

deepJS.__proto__ == workshop.prototype; // true  where it is linked
Object.getPrototypeOf(deepJS) === workshop.prototype; //true

````

> arrow functionslarda prototype bulunmaz bu sebeple new keywordünü kullanamazlar.

## Prototypal Inheritence

birbirinin kopyası oluşturulmak yerine link verme ile olur.

````
function workshop(teacher){
   this.teacher = teacher;
}

workshop.prototype.ask = function(question){
    console.log(this.teacher,question);
};

function AnotherWorkshop(teacher){
    workshop.call(this,teacher)
}
AnotherWorkshop.prototype = Object.create(workshop.prototype);  // magic here
AnotherWorkshop.prototype.speakUp = function(msg){
   this.ask(msg.toUpperCase());
}

var JSRecentParts = new AnotherWorkshop("Ikbal");

JSRecentParts.speakUp("Is this actually inheritance?");
// Ikbal Is this actually ```
var workshop = {
  setTeacher(teacher){
     this.teacher = teacher;
  },
  ask(question){```
var workshop = {
  setTeacher(teacher){
     this.teacher = teacher;
  },
  ask(question){
     console.log(this.teacher,question);
  }
};

var AnotherWorkshop = Object.assign(
   Object.create(workshop),
   {
       sepeakUp(msg){
           this.ask(msg.toUpperCase());
       }
   }
);


var JSRecentParts = Object.create (AnotherWorkshop);
JSRecentParts.setTeacher("Ikbal");
JSRecentParts.speakUp("But isn't this cleaner?");
// Ikbal But isn't this cleaner?
````

     console.log(this.teacher,question);

}
};

var AnotherWorkshop = Object.assign(
Object.create(workshop),
{
sepeakUp(msg){
this.ask(msg.toUpperCase());
}
}
);

var JSRecentParts = Object.create (AnotherWorkshop);
JSRecentParts.setTeacher("Ikbal");
JSRecentParts.speakUp("But isn't this cleaner?");
// Ikbal But isn't this cleaner?

```inheritence?


```

> Object.create() boş bir obje oluşturup prototype link verir.

daha kısa yol olarak

```
var workshop = {
  setTeacher(teacher){
     this.teacher = teacher;
  },
  ask(question){
     console.log(this.teacher,question);
  }
};

var AnotherWorkshop = Object.assign(
   Object.create(workshop),
   {
       sepeakUp(msg){
           this.ask(msg.toUpperCase());
       }
   }
);


var JSRecentParts = Object.create (AnotherWorkshop);
JSRecentParts.setTeacher("Ikbal");
JSRecentParts.speakUp("But isn't this cleaner?");
// Ikbal But isn't this cleaner?
```
