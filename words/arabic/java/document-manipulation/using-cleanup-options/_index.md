---
date: 2026-01-11
description: تعلم كيفية تنظيف مستند Word باستخدام خيارات التنظيف في Aspose.Words for
  Java، بما في ذلك إزالة الفقرات الفارغة، صفوف الجداول الفارغة، والحقول غير المستخدمة.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: تنظيف مستند Word باستخدام خيارات التنظيف في Aspose.Words (Java)
url: /ar/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تنظيف مستند Word باستخدام خيارات التنظيف في Aspose.Words (Java)

في هذا البرنامج التعليمي ستكتشف كيفية **تنظيف ملفات مستند Word** باستخدام Aspose.Words for Java. سواءً كنت تُنشئ فواتير، عقود، أو تقارير دمج بريدية ضخمة، فإن الفقرات الفارغة غير المرغوب فيها، الحقول غير المستخدمة، أو صفوف الجداول الفارغة يمكن أن تجعل المخرجات النهائية تبدو غير احترافية. سنستعرض كل خيار تنظيف خطوة بخطوة، نُظهر لك الشيفرة الدقيقة التي تحتاجها، ونشرح *لماذا* كل إعداد مهم حتى تتمكن من إنتاج مستندات مصقولة في كل مرة.

## إجابات سريعة
- **ماذا يعني “تنظيف مستند Word”؟** إزالة الفقرات الفارغة، مناطق الدمج غير المستخدمة، صفوف الجداول الفارغة، وغيرها من العناصر الزائدة بعد عملية دمج البريد.  
- **أي خيار تنظيف يزيل الفقرات الفارغة؟** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **كيف يمكنني حذف صفوف الجداول الفارغة؟** استخدم `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **هل يمكنني التخلص من الحقول التي لم تُملأ أبداً؟** نعم – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` أو `REMOVE_EMPTY_FIELDS`.  
- **هل أحتاج إلى ترخيص لتشغيل هذه الأمثلة؟** النسخة التجريبية المجانية تكفي للتقييم؛ الترخيص التجاري مطلوب للاستخدام في الإنتاج.

## ما هو “تنظيف مستند Word” في سياق دمج البريد؟
عند إجراء دمج بريد، يقوم Aspose.Words بإدخال البيانات في حقول ومناطق الدمج. إذا تلقت بعض الحقول قيمة `null` أو سلاسل فارغة، قد ينتهي المستند بوجود فقرات عشوائية، جداول فارغة، أو مناطق نائبة. **خيارات التنظيف** تقوم تلقائيًا بإزالة هذه البقايا، لتترك مستندًا نظيفًا وجاهزًا للطباعة.

## لماذا نستخدم خيارات التنظيف؟
- **مظهر احترافي:** لا خطوط فارغة ولا جداول مهجورة.  
- **حجم ملف أصغر:** إزالة العناصر غير المستخدمة يقلل من وزن المستند.  
- **تبسيط المعالجة اللاحقة:** المستندات النظيفة أسهل في التحويل إلى PDF أو HTML أو صيغ أخرى.  
- **توفير الوقت:** إعداد سطر واحد يحل محل سكريبتات المعالجة اليدوية بعد الدمج.

## المتطلبات المسبقة
- بيئة تطوير Java (JDK 8+).  
- مكتبة Aspose.Words for Java – حمّلها من [هنا](https://releases.aspose.com/words/java/).  
- إلمام أساسي بمفاهيم دمج البريد.

## دليل خطوة بخطوة

### الخطوة 1: كيفية إزالة الفقرات الفارغة (Java)
أولاً، سنوضح كيفية حذف الفقرات التي لا تحتوي على نص مرئي. هذا مفيد بشكل خاص عندما يُنتج حقل دمج قيمة `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**ماذا يحدث هنا؟**  
- `REMOVE_EMPTY_PARAGRAPHS` يطلب من Aspose.Words حذف أي فقرة تصبح فارغة بعد الدمج.  
- تفعيل `cleanupParagraphsWithPunctuationMarks` يزيل أيضًا الفقرات التي تتكون فقط من علامات ترقيم (مثل “?”).

### الخطوة 2: كيفية إزالة المناطق غير المدمجة
إذا لم يكن هناك بيانات مطابقة لمنطقة دمج بريد، يمكنك إهمالها تمامًا.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**لماذا هذا مهم:**  
المناطق غير المستخدمة غالبًا ما تترك أقسامًا فارغة أو عناوين متروكة. علم `REMOVE_UNUSED_REGIONS` ينظفها تلقائيًا.

### الخطوة 3: كيفية إزالة الحقول الفارغة
عندما يتلقى حقل قيمة سلسلة فارغة، قد ترغب في حذف الحقل بالكامل بدلاً من ترك عنصر نائب فارغ.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### الخطوة 4: كيفية إزالة الحقول غير المستخدمة
إذا لم يتم الإشارة إلى بعض الحقول أثناء الدمج، يمكنك إزالتها بالكامل.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### الخطوة 5: كيفية إزالة الحقول المحتواة
أحيانًا يكون حقل دمج داخل فقرة تريد أيضًا إهمالها.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### الخطوة 6: كيفية إزالة صفوف الجداول الفارغة
غالبًا ما تنتهي الجداول بصفوف تحتوي فقط على حقول فارغة. هذا الخيار يزيل تلك الصفوف.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## المشكلات الشائعة & استكشاف الأخطاء
- **الفقرات لم تُحذف:** تأكد من استدعاء `setCleanupParagraphsWithPunctuationMarks(true)` *بعد* ضبط خيار التنظيف.  
- **صفوف الجداول الفارغة لا تزال موجودة:** تحقق من أن خلايا الجدول تحتوي فعليًا على سلاسل فارغة (ليس مسافات).  
- **الحقول غير المستخدمة لا تزال موجودة:** تأكد من أنك تستخدم التعداد الصحيح (`REMOVE_UNUSED_FIELDS`) وأن حقول الدمج لم تُملأ عن طريق الخطأ في مكان آخر.

## الأسئلة المتكررة

**س: ما الفرق بين `REMOVE_EMPTY_FIELDS` و `REMOVE_UNUSED_FIELDS`؟**  
ج: `REMOVE_EMPTY_FIELDS` يحذف الحقول التي تتلقى سلسلة فارغة أو `null` أثناء الدمج، بينما `REMOVE_UNUSED_FIELDS` يزيل الحقول التي لم يتم الإشارة إليها في عملية الدمج مطلقًا.

**س: هل يمكن الجمع بين عدة خيارات تنظيف؟**  
ج: نعم. طريقة `setCleanupOptions` تقبل عملية OR بتية للقيم التعدادية، مما يتيح لك تنظيف الفقرات، الجداول، والمناطق في استدعاء واحد.

**س: هل يؤثر تفعيل `cleanupParagraphsWithPunctuationMarks` على النص العادي؟**  
ج: لا، فهو يزيل فقط الفقرات التي تتكون بالكامل من علامات ترقيم (مثل “?” أو “---”). الجمل العادية تبقى دون تغيير.

**س: هل يمكن تخصيص علامات الترقيم التي تُعتبر؟**  
ج: API الحالي يستخدم مجموعة محددة مسبقًا من علامات الترقيم. لتخصيص السلوك، سيتعين عليك معالجة المستند بعد الدمج يدويًا.

**س: هل تعمل خيارات التنظيف هذه مع تحويل PDF؟**  
ج: بالتأكيد. بمجرد تنظيف مستند Word، يمكنك تحويله إلى PDF أو HTML أو أي صيغة مدعومة أخرى دون نقل العناصر غير المرغوب فيها.

## الخلاصة
الآن لديك مجموعة أدوات كاملة **لتنظيف ملفات مستند Word** أثناء دمج البريد باستخدام Aspose.Words for Java. باختيار `MailMergeCleanupOptions` المناسب، يمكنك حذف الفقرات الفارغة، صفوف الجداول الفارغة، الحقول غير المستخدمة، وأكثر—مما يمنحك مستندًا أنيقًا وجاهزًا للإنتاج في كل مرة.

---

**آخر تحديث:** 2026-01-11  
**تم الاختبار مع:** Aspose.W for Java 24.11  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}