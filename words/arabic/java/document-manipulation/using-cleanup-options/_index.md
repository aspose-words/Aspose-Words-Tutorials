---
"description": "حسّن وضوح مستنداتك باستخدام خيارات التنظيف في Aspose.Words لجافا. تعرّف على كيفية إزالة الفقرات الفارغة والمناطق غير المستخدمة والمزيد."
"linktitle": "استخدام خيارات التنظيف"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استخدام خيارات التنظيف في Aspose.Words لـ Java"
"url": "/ar/java/document-manipulation/using-cleanup-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام خيارات التنظيف في Aspose.Words لـ Java


## مقدمة حول استخدام خيارات التنظيف في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية استخدام خيارات التنظيف في Aspose.Words لجافا لمعالجة المستندات وتنظيفها أثناء عملية دمج البريد. تتيح لك خيارات التنظيف التحكم في جوانب مختلفة من تنظيف المستندات، مثل إزالة الفقرات الفارغة والمناطق غير المستخدمة، وغيرها.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من دمج مكتبة Aspose.Words لجافا في مشروعك. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/java/).

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

في هذا المثال، نُنشئ مستندًا جديدًا، ونُدرج حقول دمج، ونُعيّن خيارات التنظيف لإزالة الفقرات الفارغة. كما نُفعّل إزالة الفقرات التي تحتوي على علامات ترقيم. بعد تنفيذ عملية دمج البريد، يُحفظ المستند مع تطبيق خيارات التنظيف المُحددة.

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

في هذا المثال، نفتح مستندًا موجودًا يحتوي على مناطق دمج، ونضبط خيارات التنظيف لإزالة المناطق غير المستخدمة، ثم ننفذ عملية دمج البريد باستخدام بيانات فارغة. تؤدي هذه العملية تلقائيًا إلى إزالة المناطق غير المستخدمة من المستند.

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

في هذا المثال، نفتح مستندًا يحتوي على حقول دمج، ونضبط خيارات التنظيف لإزالة الحقول الفارغة، ثم ننفذ عملية دمج البريد مع البيانات. بعد الدمج، ستُحذف أي حقول فارغة من المستند.

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

في هذا المثال، نفتح مستندًا يحتوي على حقول دمج، ونضبط خيارات التنظيف لإزالة الحقول غير المستخدمة، ثم ننفذ عملية دمج البريد مع البيانات. بعد الدمج، ستُحذف أي حقول غير مستخدمة من المستند.

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

في هذا المثال، نفتح مستندًا يحتوي على حقول دمج، ونضبط خيارات التنظيف لإزالة الحقول التي تحتوي عليها، ثم ننفذ عملية دمج البريد مع البيانات. بعد الدمج، ستُحذف الحقول نفسها من المستند.

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

في هذا المثال، نفتح مستندًا يحتوي على جدول ودمج الحقول، ونضبط خيارات التنظيف لإزالة صفوف الجدول الفارغة، ثم ننفذ عملية دمج البريد مع البيانات. بعد الدمج، ستُحذف أي صفوف جدول فارغة من المستند.

## خاتمة

في هذا البرنامج التعليمي، تعلمت كيفية استخدام خيارات التنظيف في Aspose.Words لجافا لمعالجة المستندات وتنظيفها أثناء عملية دمج البريد. توفر هذه الخيارات تحكمًا دقيقًا في تنظيف المستندات، مما يتيح لك إنشاء مستندات مصقولة ومخصصة بسهولة.

## الأسئلة الشائعة

### ما هي خيارات التنظيف في Aspose.Words لـ Java؟

خيارات التنظيف في Aspose.Words لجافا هي إعدادات تتيح لك التحكم في جوانب مختلفة من تنظيف المستندات أثناء عملية دمج البريد. تتيح لك هذه الإعدادات إزالة العناصر غير الضرورية، مثل الفقرات الفارغة والمناطق غير المستخدمة، وغيرها، مما يضمن لك الحصول على مستند نهائي منظم وجميل.

### كيف يمكنني إزالة الفقرات الفارغة من مستندي؟

لإزالة الفقرات الفارغة من مستندك باستخدام Aspose.Words for Java، يمكنك تعيين `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` خيار "صحيح". سيؤدي هذا تلقائيًا إلى حذف الفقرات التي لا تحتوي على محتوى، مما ينتج عنه مستند أكثر وضوحًا.

### ما هو الغرض من `REMOVE_UNUSED_REGIONS` خيار التنظيف؟

ال `MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` يُستخدم هذا الخيار لإزالة مناطق من المستند لا تحتوي على بيانات مقابلة أثناء عملية دمج البريد. يساعد هذا الخيار على تنظيم مستندك بالتخلص من العناصر النائبة غير المستخدمة.

### هل يمكنني إزالة صفوف الجدول الفارغة من مستند باستخدام Aspose.Words لـ Java؟

نعم، يمكنك إزالة صفوف الجدول الفارغة من المستند عن طريق تعيين `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` فعّل خيار التنظيف. سيؤدي هذا تلقائيًا إلى حذف أي صفوف جدول لا تحتوي على بيانات، مما يضمن تنظيمًا جيدًا للجدول في مستندك.

### ماذا يحدث عندما أقوم بتعيين `REMOVE_CONTAINING_FIELDS` خيار؟

ضبط `MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` سيؤدي هذا الخيار إلى إزالة حقل الدمج بالكامل، بما في ذلك الفقرة التي يحتويها، من المستند أثناء عملية دمج البريد. هذا مفيد عند الرغبة في حذف حقول الدمج والنص المرتبط بها.

### كيف يمكنني إزالة حقول الدمج غير المستخدمة من مستندي؟

لإزالة حقول الدمج غير المستخدمة من مستند، يمكنك تعيين `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` سيؤدي هذا تلقائيًا إلى حذف حقول الدمج غير المملوءة أثناء دمج البريد، مما ينتج عنه مستند أنظف.

### ما هو الفرق بين `REMOVE_EMPTY_FIELDS` و `REMOVE_UNUSED_FIELDS` خيارات التنظيف؟

ال `REMOVE_EMPTY_FIELDS` يزيل هذا الخيار حقول الدمج التي لا تحتوي على بيانات أو التي تكون فارغة أثناء عملية دمج البريد. من ناحية أخرى، `REMOVE_UNUSED_FIELDS` يزيل هذا الخيار حقول الدمج غير المملوءة بالبيانات أثناء عملية الدمج. يعتمد الاختيار بينهما على ما إذا كنت تريد إزالة الحقول الخالية من المحتوى أو تلك غير المستخدمة في عملية الدمج المحددة.

### كيف يمكنني تفعيل إزالة الفقرات التي تحتوي على علامات الترقيم؟

لتفعيل إزالة الفقرات التي تحتوي على علامات الترقيم، يمكنك ضبط `cleanupParagraphsWithPunctuationMarks` خيار "صحيح" وتحديد علامات الترقيم المراد تنظيفها. يتيح لك هذا إنشاء مستند أكثر دقة بإزالة الفقرات غير الضرورية التي تحتوي فقط على علامات الترقيم.

### هل يمكنني تخصيص خيارات التنظيف في Aspose.Words لـ Java؟

نعم، يمكنك تخصيص خيارات التنظيف وفقًا لاحتياجاتك الخاصة. يمكنك اختيار خيارات التنظيف المُراد تطبيقها وتكوينها وفقًا لمتطلبات تنظيف مستنداتك، مما يضمن أن مستندك النهائي يلبي المعايير المطلوبة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}