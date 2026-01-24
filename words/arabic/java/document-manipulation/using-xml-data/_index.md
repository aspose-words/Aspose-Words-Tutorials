---
date: 2026-01-24
description: تعلم كيفية دمج بيانات XML مع Aspose.Words for Java، وأتمتة إنشاء المستندات
  باستخدام Java، واستخدام صيغة Mustache للمستندات الديناميكية.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: كيفية دمج XML في Aspose.Words للـ Java
url: /ar/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية دمج XML في Aspose.Words للـ Java

في هذا الدليل الشامل ستكتشف **كيفية دمج XML** باستخدام Aspose.Words للـ Java. سنستعرض سيناريوهات دمج البريد الأساسية والمتداخلة، ونظهر لك كيفية **استخدام صيغة Mustache**، ونشرح كيفية **أتمتة إنشاء المستندات** في مشاريع Java. في النهاية ستتمكن من إنشاء مستندات Word مخصصة مباشرةً من مصادر XML ببضع أسطر من الشيفرة.

## إجابات سريعة
- **ما هي الفئة الأساسية لدمج البريد؟** `Document` وخاصية `MailMerge` الخاصة بها.  
- **هل يمكنني دمج جداول XML المتداخلة؟** نعم – استخدم `executeWithRegions` للبيانات الهرمية.  
- **هل تدعم صيغة Mustache؟** فعّلها باستخدام `setUseNonMergeFields(true)`.  
- **هل أحتاج إلى ترخيص للإنتاج؟** يلزم الحصول على ترخيص تجاري لـ Aspose.Words.  
- **ما نسخة Java المتوافقة؟** Java 8+ وما بعدها مدعومة بالكامل.

## ما هو دمج البريد XML في Aspose.Words؟
يتيح دمج البريد XML ربط مجموعات البيانات المستندة إلى XML بالمواضع النائبة في قالب Word. يقوم المحرك باستبدال كل موضع نائبي بقيمة العقدة XML المقابلة، مما ينتج مستندًا نهائيًا دون تحرير يدوي.

## لماذا تستخدم Aspose.Words لإنشاء المستندات المستندة إلى XML؟
- **أتمتة إنشاء المستندات في مشاريع Java** دون أي تبعيات على Microsoft Office.  
- **دعم الهياكل المعقدة** – جداول متداخلة، أقسام متكررة، ومحتوى شرطي.  
- **صيغة Mustache** توفر لك مواضع نائبة مرنة غير حقل دمج لتقنيات القوالب المتقدمة.  
- **متعدد المنصات** – يعمل على Windows وLinux وmacOS.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

- [Aspose.Words for Java](https://products.aspose.com/words/java/) مثبت (أحدث إصدار).  
- ملفات XML نموذجية للعملاء والطلبات والبائعين (يستخدم الدرس `Mail merge data - Customers.xml` و`Orders.xml` و`Vendors.xml`).  
- مستندات قالب Word التي تحتوي على حقول دمج (مثل `Registration complete.docx` و`Invoice.docx` و`Vendor.docx`).  

## كيفية دمج XML – دمج بريد أساسي

يقوم دمج البريد الأساسي بسحب جدول XML واحد إلى قالب Word. اتبع الخطوات التالية:

1. حمّل ملف XML في كائن `DataSet`.  
2. افتح مستند Word الوجهة.  
3. نفّذ الدمج باستخدام اسم الجدول.  
4. احفظ المستند المدموج.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**نصيحة احترافية:** حافظ على هيكل XML مسطح للدمجات البسيطة – يجب أن يرتبط كل جدول مباشرةً بمجموعة من حقول الدمج.

## كيفية دمج XML – دمج بريد متداخل

عندما يحتوي XML الخاص بك على علاقات أب‑ابن (مثل الطلبات مع بنودها)، تحتاج إلى دمج متداخل. تقوم طريقة `executeWithRegions` بمعالجة كل منطقة بشكل متكرر.

1. حمّل XML الهرمي في كائن `DataSet`.  
2. عطل تقليم الفراغات إذا كنت تحتاج إلى تنسيق دقيق.  
3. استدعِ `executeWithRegions` لمعالجة جميع الجداول المتداخلة.  
4. احفظ النتيجة.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**مشكلة شائعة:** نسيان ضبط `setTrimWhitespaces(false)` قد يسبب مسافات غير مرغوب فيها في المستند النهائي، خاصةً للحقول المالية أو الرقمية.

## كيفية استخدام صيغة Mustache مع DataSet

تتيح صيغة Mustache لك تضمين مواضع نائبة غير حقل دمج (مثل `{{CustomerName}}`) داخل القالب الخاص بك. فعّلها وشغّل دمجًا قائمًا على المناطق.

1. حمّل XML البائع.  
2. فعّل دعم Mustache باستخدام `setUseNonMergeFields(true)`.  
3. نفّذ الدمج باستخدام المناطق.  
4. احفظ الناتج.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**لماذا تستخدم Mustache؟** توفر طريقة نظيفة وغير مرتبطة بلغة معينة للإشارة إلى البيانات، مما يجعل القوالب أسهل للقراءة والصيانة، خاصةً عند **إنشاء مستندات** المدفوعة بـ XML.

## المشكلات الشائعة والحلول

| المشكلة | الحل |
|-------|----------|
| عقد XML لا تتطابق مع حقول الدمج | تحقق من أن أسماء عناصر XML تتطابق تمامًا مع أسماء حقول الدمج (حساسة لحالة الأحرف). |
| ظهور فراغات حول القيم المدمجة | استخدم `doc.getMailMerge().setTrimWhitespaces(false)` للحفاظ على الفراغات الأصلية. |
| تُهمل الجداول المتداخلة | تأكد من تعريف منطقة جدول الأب في القالب (مثال: `{{#Orders}} … {{/Orders}}`). |
| لم يتم استبدال مواضع Mustache | استدعِ `setUseNonMergeFields(true)` قبل تنفيذ الدمج. |

## الأسئلة الشائعة

### كيف يمكنني إعداد بيانات XML للدمج؟

تأكد من أن XML الخاص يحتوي كل عنصر `<TableName>` على صفوف (`<Row>`) وأعمدة تتطابق مع حقول الدمج في قالب Word الخاص بك.

### هل يمكنني تخصيص سلوك التقليم لقيم دمج البريد؟

نعم. استخدم `doc.getMailMerge().setTrimWhitespaces(false)` للحفاظ على المسافات البادئة/اللاحقة كما تظهر في XML.

### ما هي صيغة Mustache ومتى يجب استخدامها؟

تسمح صيغة Mustache (`{{FieldName}}`) بمواضع نائبة مرنة لا تقتصر على حقول الدمج التقليدية. فعّلها باستخدام `setUseNonMergeFields(true)` عندما تحتاج إلى قالب أنظف أو تريد فصل منطق البيانات عن أكواد حقول Word.

### كيف يمكنني أتمتة إنشاء المستندات في مشاريع Java باستخدام هذه الطريقة؟

ادمج مقتطفات الشيفرة أعلاه في طبقة الخدمة الخاصة بك، اقرأ XML من قواعد البيانات أو APIs، واستدعِ روتين الدمج كلما احتجت إلى مستند جديد (مثل إنشاء  
**تم الاختبار مع:** Aspose.Words للـ Java (أحدث إصدار)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}