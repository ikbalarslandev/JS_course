---
title: "Module Pattern"
description: "Brian Holt introduces you to himself, the Complete Intro to React version 6, and what you can expect to learn"
---

## Module Pattern

Module pattern sayesinde tüm kodları bir sayfaya yazmak yerine küçük sayfalar oluşturup tek bir sayfaya import edebiliriz bu sayede kodun okunabilirliüi artar.

> modüller verileri kapsuller. verilerin statüsü closure sayesinde takip edilebilir.

```
function workshopModule(teacher){
   var publicAPI = {ask,};
   return publicAPI;

   function ask(question){
      console.log(teacher,question);
   }
}

var workshop = workshopModule("Ikbal");

workshop.ask("It's a module right?")

```

teacher private olduğu için ulaşılamaz yani kapsullenmiştir.

## ES6 Modules

sayfanın uzantısını .mjs (module javascript) kullanarak bu özelliği aktifleştirebiliriz.

`export` ve `import` keywordları kullanılarak moduller kullanılır.

default olarak module içerisindeki herşey private yani dışarıdan erişilemez şekilde kapsüllenmiştir. dışarıdan erişim olmasını istediğimiz değişkenlerin başına `export` keywordu yazılır.

modüller sayfa tabanlı çalışır yani bir sayfada birden fazla modül yazılamaz.

kodu çalıştırdığımızda tüm moduller birleştirilerek tek bir javascript sayfası oluşturlur. javascript motoru bu tek sayfayı okur.

modüller singletlon dur yani ne kadar import yaparsak yapalım her zaman aynı modulu referans gösterir.

```
// workshop.mjs
var teacher = "Ikbal";

export default function ask(question){
     console.log(teacher,question)
}

```

---

```
import ask from "workshop.mjs";

ask("It's a default import, right?");
// Ikbal its a default import, right?
```

veya

```
import * as workshop from "workshop.mjs";

workshop.ask("It's a namespace import, right?")
```

şeklinde moduller import edilip kullanılabilir.

## Örnek module pattern export kullanarak

> export default olunca fonksyonun kendisi import edilir , object içerisinde import edilmez.

export dediğimizde bir object içerisinde methodlar import edilir.

```

function defineWorkshop() {
	var currentEnrollment = [];
	var studentRecords = [];

	var publicAPI = {
		addStudent,
		enrollStudent,
		printCurrentEnrollment,
		enrollPaidStudents,
		remindUnpaidStudents,
	};
	return publicAPI;


	// ********************************

	function addStudent(id,name,paid) {
		studentRecords.push({ id, name, paid, });
	}

	function enrollStudent(id) {
		if (!currentEnrollment.includes(id)) {
			currentEnrollment.push(id);
		}
	}

	function printCurrentEnrollment() {
		printRecords(currentEnrollment);
	}

	function enrollPaidStudents() {
		currentEnrollment = paidStudentsToEnroll();
		printCurrentEnrollment();
	}

	function remindUnpaidStudents() {
		remindUnpaid(currentEnrollment);
	}

	function getStudentFromId(studentId) {
		return studentRecords.find(matchId);

		// *************************

		function matchId(record) {
			return (record.id == studentId);
		}
	}

	function printRecords(recordIds) {
		var records = recordIds.map(getStudentFromId);

		records.sort(sortByNameAsc);

		records.forEach(printRecord);
	}

	function sortByNameAsc(record1,record2){
		if (record1.name < record2.name) return -1;
		else if (record1.name > record2.name) return 1;
		else return 0;
	}

	function printRecord(record) {
		console.log(`${record.name} (${record.id}): ${record.paid ? "Paid" : "Not Paid"}`);
	}

	function paidStudentsToEnroll() {
		var recordsToEnroll = studentRecords.filter(needToEnroll);

		var idsToEnroll = recordsToEnroll.map(getStudentId);

		return [ ...currentEnrollment, ...idsToEnroll ];
	}

	function needToEnroll(record) {
		return (record.paid && !currentEnrollment.includes(record.id));
	}

	function getStudentId(record) {
		return record.id;
	}

	function remindUnpaid(recordIds) {
		var unpaidIds = recordIds.filter(notYetPaid);

		printRecords(unpaidIds);
	}

	function notYetPaid(studentId) {
		var record = getStudentFromId(studentId);
		return !record.paid;
	}
}

```
