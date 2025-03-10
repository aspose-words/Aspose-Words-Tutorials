---
title: استخدام خيارات التنظيف في Aspose.Words لـ Java
linktitle: استخدام خيارات التنظيف
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تحسين وضوح المستند باستخدام خيارات التنظيف في Aspose.Words لـ Java. تعرف على كيفية إزالة الفقرات الفارغة والمناطق غير المستخدمة والمزيد.
weight: 10
url: /ar/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدام خيارات التنظيف في Aspose.Words لـ Java


## مقدمة حول استخدام خيارات التنظيف في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية استخدام خيارات التنظيف في Aspose.Words for Java لمعالجة المستندات وتنظيفها أثناء عملية دمج البريد. تتيح لك خيارات التنظيف التحكم في جوانب مختلفة من تنظيف المستندات، مثل إزالة الفقرات الفارغة والمناطق غير المستخدمة والمزيد.

## المتطلبات الأساسية

 قبل أن نبدأ، تأكد من دمج مكتبة Aspose.Words for Java في مشروعك. يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/java/).

## الخطوة 1: إزالة الفقرات الفارغة

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج حقول الدمج
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// تعيين خيارات التنظيف
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// تمكين فقرات التنظيف باستخدام علامات الترقيم
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// تنفيذ دمج البريد
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// حفظ المستند
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

في هذا المثال، نقوم بإنشاء مستند جديد وإدراج حقول دمج وتعيين خيارات التنظيف لإزالة الفقرات الفارغة. بالإضافة إلى ذلك، نقوم بتمكين إزالة الفقرات التي تحتوي على علامات ترقيم. بعد تنفيذ عملية دمج البريد، يتم حفظ المستند مع تطبيق عملية التنظيف المحددة.

## الخطوة 2: إزالة المناطق غير المدمجة

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// تعيين خيارات التنظيف لإزالة المناطق غير المستخدمة
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// تنفيذ دمج البريد مع المناطق
doc.getMailMerge().executeWithRegions(data);

// حفظ المستند
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

في هذا المثال، نفتح مستندًا موجودًا يحتوي على مناطق دمج، ونضبط خيارات التنظيف لإزالة المناطق غير المستخدمة، ثم ننفذ عملية دمج البريد باستخدام بيانات فارغة. تعمل هذه العملية تلقائيًا على إزالة المناطق غير المستخدمة من المستند.

## الخطوة 3: إزالة الحقول الفارغة

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// تعيين خيارات التنظيف لإزالة الحقول الفارغة
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// تنفيذ دمج البريد
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// حفظ المستند
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

في هذا المثال، نفتح مستندًا يحتوي على حقول دمج، ونضبط خيارات التنظيف لإزالة الحقول الفارغة، وننفذ عملية دمج البريد بالبيانات. بعد الدمج، سيتم إزالة أي حقول فارغة من المستند.

## الخطوة 4: إزالة الحقول غير المستخدمة

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// تعيين خيارات التنظيف لإزالة الحقول غير المستخدمة
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// تنفيذ دمج البريد
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// حفظ المستند
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

في هذا المثال، نفتح مستندًا يحتوي على حقول دمج، ونضبط خيارات التنظيف لإزالة الحقول غير المستخدمة، وننفذ عملية دمج البريد بالبيانات. بعد الدمج، سيتم إزالة أي حقول غير مستخدمة من المستند.

## الخطوة 5: إزالة الحقول المتضمنة

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// تعيين خيارات التنظيف لإزالة الحقول المتضمنة
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// تنفيذ دمج البريد
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// حفظ المستند
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

في هذا المثال، نفتح مستندًا يحتوي على حقول دمج، ونضبط خيارات التنظيف لإزالة الحقول التي تحتوي على البيانات، وننفذ عملية دمج البريد بالبيانات. بعد الدمج، سيتم إزالة الحقول نفسها من المستند.

## الخطوة 6: إزالة صفوف الجدول الفارغة

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// تعيين خيارات التنظيف لإزالة صفوف الجدول الفارغة
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// تنفيذ دمج البريد
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// حفظ المستند
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

في هذا المثال، نفتح مستندًا يحتوي على جدول وحقول دمج، ونضبط خيارات التنظيف لإزالة صفوف الجدول الفارغة، وننفذ عملية دمج البريد بالبيانات. بعد الدمج، سيتم إزالة أي صفوف جدول فارغة من المستند.

## خاتمة

في هذا البرنامج التعليمي، تعلمت كيفية استخدام خيارات التنظيف في Aspose.Words for Java لمعالجة المستندات وتنظيفها أثناء عملية دمج البريد. توفر هذه الخيارات تحكمًا دقيقًا في تنظيف المستندات، مما يسمح لك بإنشاء مستندات مصقولة ومخصصة بسهولة.

## الأسئلة الشائعة

### ما هي خيارات التنظيف في Aspose.Words لـ Java؟

خيارات التنظيف في Aspose.Words for Java هي إعدادات تسمح لك بالتحكم في جوانب مختلفة من تنظيف المستند أثناء عملية دمج البريد. فهي تمكنك من إزالة العناصر غير الضرورية مثل الفقرات الفارغة والمناطق غير المستخدمة والمزيد، مما يضمن أن المستند النهائي الخاص بك منظم ومصقول بشكل جيد.

### كيف يمكنني إزالة الفقرات الفارغة من مستندي؟

 لإزالة الفقرات الفارغة من مستندك باستخدام Aspose.Words for Java، يمكنك ضبط`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` خيار "صحيح". سيؤدي هذا تلقائيًا إلى إزالة الفقرات التي لا تحتوي على محتوى، مما يؤدي إلى الحصول على مستند أنظف.

###  ما هو الغرض من ذلك؟`REMOVE_UNUSED_REGIONS` cleanup option?

 ال`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` يُستخدم هذا الخيار لإزالة المناطق في المستند التي لا تحتوي على بيانات مقابلة أثناء عملية دمج البريد. ويساعد هذا الخيار في الحفاظ على ترتيب مستندك من خلال التخلص من العناصر النائبة غير المستخدمة.

### هل يمكنني إزالة صفوف الجدول الفارغة من مستند باستخدام Aspose.Words لـ Java؟

 نعم، يمكنك إزالة صفوف الجدول الفارغة من المستند عن طريق ضبط`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`قم بضبط خيار التنظيف على true. سيؤدي هذا تلقائيًا إلى حذف أي صفوف جدول لا تحتوي على بيانات، مما يضمن وجود جدول منظم جيدًا في مستندك.

###  ماذا يحدث عندما أقوم بتعيين`REMOVE_CONTAINING_FIELDS` option?

 ضبط`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` سيؤدي الخيار إلى إزالة حقل الدمج بالكامل، بما في ذلك الفقرة التي يحتوي عليها، من المستند أثناء عملية دمج البريد. وهذا مفيد عندما تريد إزالة حقول الدمج والنص المرتبط بها.

### كيف يمكنني إزالة حقول الدمج غير المستخدمة من مستندي؟

 لإزالة حقول الدمج غير المستخدمة من مستند، يمكنك ضبط`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` خيار "صحيح". سيؤدي هذا تلقائيًا إلى التخلص من حقول الدمج التي لم يتم ملؤها أثناء دمج البريد، مما يؤدي إلى الحصول على مستند أنظف.

###  ما هو الفرق بين`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 ال`REMOVE_EMPTY_FIELDS` يزيل الخيار حقول الدمج التي لا تحتوي على بيانات أو التي تكون فارغة أثناء عملية دمج البريد. من ناحية أخرى،`REMOVE_UNUSED_FIELDS`يزيل الخيار حقول الدمج التي لا تحتوي على بيانات أثناء الدمج. يعتمد الاختيار بينهما على ما إذا كنت تريد إزالة الحقول التي لا تحتوي على محتوى أو تلك التي لا يتم استخدامها في عملية الدمج المحددة.

### كيف يمكنني تفعيل إزالة الفقرات التي تحتوي على علامات الترقيم؟

 لتمكين إزالة الفقرات التي تحتوي على علامات الترقيم، يمكنك ضبط`cleanupParagraphsWithPunctuationMarks` خيار "صحيح" وتحديد علامات الترقيم التي يجب مراعاتها للتنظيف. يتيح لك هذا إنشاء مستند أكثر دقة من خلال إزالة الفقرات غير الضرورية التي تحتوي على علامات الترقيم فقط.

### هل يمكنني تخصيص خيارات التنظيف في Aspose.Words لـ Java؟

نعم، يمكنك تخصيص خيارات التنظيف وفقًا لاحتياجاتك المحددة. يمكنك اختيار خيارات التنظيف التي تريد تطبيقها وتكوينها وفقًا لمتطلبات تنظيف المستندات، مما يضمن أن المستند النهائي يلبي المعايير المطلوبة.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
