---
title: ربط المستندات وإضافتها في Aspose.Words لـ Java
linktitle: ربط المستندات وإضافتها
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية ضم المستندات وإضافتها بسهولة باستخدام Aspose.Words for Java. حافظ على التنسيق، وأدر رؤوس الصفحات وتذييلاتها، والمزيد.
weight: 30
url: /ar/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ربط المستندات وإضافتها في Aspose.Words لـ Java


## مقدمة حول ربط المستندات وإضافتها في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية ضم المستندات وإضافتها باستخدام مكتبة Aspose.Words for Java. ستتعلم كيفية دمج مستندات متعددة بسلاسة مع الحفاظ على التنسيق والبنية.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من إعداد Aspose.Words for Java API في مشروع Java الخاص بك.

## خيارات ربط المستندات

### إضافة بسيطة

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### إضافة مع خيارات تنسيق الاستيراد

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### إضافة إلى مستند فارغ

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### إضافة مع تحويل رقم الصفحة

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // تحويل عدد من الحقول
dstDoc.updatePageLayout(); // تحديث تخطيط الصفحة لترقيمها بشكل صحيح
```

## التعامل مع إعدادات الصفحات المختلفة

عند إلحاق المستندات بإعدادات صفحات مختلفة:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// تأكد من أن إعدادات إعداد الصفحة تتطابق مع المستند الوجهة
```

## ربط المستندات بأنماط مختلفة

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## سلوكيات ذكية

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## إدراج المستندات باستخدام DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## الحفاظ على ترقيم المصدر

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## التعامل مع مربعات النص

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## إدارة الرؤوس والتذييلات

### ربط الرؤوس والتذييلات

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### إلغاء ربط الرؤوس والتذييلات

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## خاتمة

يوفر Aspose.Words for Java أدوات مرنة وقوية لضم المستندات وإضافتها، سواء كنت بحاجة إلى الحفاظ على التنسيق أو التعامل مع إعدادات الصفحات المختلفة أو إدارة الرؤوس والتذييلات. جرّب هذه التقنيات لتلبية احتياجات معالجة المستندات الخاصة بك.

## الأسئلة الشائعة

### كيف يمكنني دمج المستندات ذات الأنماط المختلفة بسلاسة؟

 لربط المستندات ذات الأنماط المختلفة، استخدم`ImportFormatMode.USE_DESTINATION_STYLES` عند الإلحاق.

### هل يمكنني الحفاظ على ترقيم الصفحات عند إضافة المستندات؟

 نعم، يمكنك الحفاظ على ترقيم الصفحات باستخدام`convertNumPageFieldsToPageRef` الطريقة وتحديث تخطيط الصفحة.

### ما هو أسلوب السلوك الذكي؟

 يساعد سلوك النمط الذكي في الحفاظ على الأنماط المتسقة عند إضافة المستندات. استخدمه مع`ImportFormatOptions` للحصول على نتائج أفضل.

### كيف يمكنني التعامل مع مربعات النص عند إضافة المستندات؟

تعيين`importFormatOptions.setIgnoreTextBoxes(false)` لتضمين مربعات النص أثناء الإلحاق.

### ماذا لو أردت ربط/إلغاء ربط الرؤوس والتذييلات بين المستندات؟

 يمكنك ربط الرؤوس والتذييلات بـ`linkToPrevious(true)` أو افصلهم عن`linkToPrevious(false)` حسب الحاجة.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
