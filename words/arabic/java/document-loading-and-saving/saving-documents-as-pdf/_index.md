---
"description": "تعرّف على كيفية حفظ مستندات Word بصيغة PDF باستخدام Aspose.Words لجافا. خصّص الخطوط والخصائص وجودة الصورة. دليل شامل لتحويل ملفات PDF."
"linktitle": "حفظ المستندات بتنسيق PDF"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "حفظ المستندات بتنسيق PDF في Aspose.Words لـ Java"
"url": "/ar/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستندات بتنسيق PDF في Aspose.Words لـ Java


## مقدمة لحفظ المستندات بتنسيق PDF في Aspose.Words لـ Java

في هذا الدليل التفصيلي، سنستكشف كيفية حفظ المستندات بتنسيق PDF باستخدام Aspose.Words لجافا. سنغطي جوانب مختلفة من تحويل PDF، ونقدم أمثلة برمجية لتسهيل العملية.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية لديك:

- تم تثبيت Java Development Kit (JDK) على نظامك.
- مكتبة Aspose.Words لجافا. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/java/).

## تحويل مستند إلى PDF

لتحويل مستند Word إلى PDF، يمكنك استخدام مقتطف التعليمات البرمجية التالي:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

يستبدل `"input.docx"` مع المسار إلى مستند Word الخاص بك و `"output.pdf"` مع مسار ملف PDF الناتج المطلوب.

## التحكم في خيارات حفظ ملف PDF

يمكنك التحكم في خيارات حفظ ملفات PDF المختلفة باستخدام `PdfSaveOptions` على سبيل المثال، يمكنك تعيين عنوان عرض مستند PDF كما يلي:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## تضمين الخطوط في PDF

لتضمين الخطوط في ملف PDF المُنشأ، استخدم الكود التالي:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## تخصيص خصائص المستند

يمكنك تخصيص خصائص المستند في ملف PDF المُنشأ. على سبيل المثال:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## تصدير هيكل المستند

لتصدير هيكل المستند، قم بتعيين `exportDocumentStructure` خيار ل `true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## ضغط الصور

يمكنك التحكم في ضغط الصورة باستخدام الكود التالي:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## تحديث آخر خاصية مطبوعة

لتحديث خاصية "آخر طباعة" في ملف PDF، استخدم:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## تقديم تأثيرات DML ثلاثية الأبعاد

للحصول على عرض متقدم لتأثيرات DML 3D، اضبط وضع العرض:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## استيفاء الصور

يمكنك تمكين استيفاء الصورة لتحسين جودة الصورة:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## خاتمة

يوفر Aspose.Words for Java إمكانيات شاملة لتحويل مستندات Word إلى صيغة PDF مع مرونة وخيارات تخصيص متعددة. يمكنك التحكم في جوانب مختلفة من إخراج PDF، بما في ذلك الخطوط وخصائص المستند وضغط الصور وغيرها.

## الأسئلة الشائعة

### كيف أقوم بتحويل مستند Word إلى PDF باستخدام Aspose.Words for Java؟

لتحويل مستند Word إلى PDF، استخدم الكود التالي:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

يستبدل `"input.docx"` مع المسار إلى مستند Word الخاص بك و `"output.pdf"` مع مسار ملف PDF الناتج المطلوب.

### هل يمكنني تضمين الخطوط في ملف PDF الذي تم إنشاؤه بواسطة Aspose.Words لـ Java؟

نعم، يمكنك تضمين الخطوط في ملف PDF عن طريق ضبط `setEmbedFullFonts` خيار ل `true` في `PdfSaveOptions`. وإليك مثال:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### كيف يمكنني تخصيص خصائص المستند في ملف PDF الناتج؟

يمكنك تخصيص خصائص المستند في ملف PDF باستخدام `setCustomPropertiesExport` الخيار في `PdfSaveOptions`. على سبيل المثال:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### ما هو الغرض من ضغط الصور في Aspose.Words لـ Java؟

يتيح لك ضغط الصور التحكم في جودة وحجم الصور في ملف PDF المُنشأ. يمكنك ضبط وضع ضغط الصور باستخدام `setImageCompression` في `PdfSaveOptions`.

### كيف أقوم بتحديث خاصية "آخر طباعة" في ملف PDF؟

يمكنك تحديث خاصية "آخر طباعة" في ملف PDF عن طريق تعيين `setUpdateLastPrintedProperty` ل `true` في `PdfSaveOptions`سيعكس هذا تاريخ آخر طباعة في بيانات PDF التعريفية.

### كيف يمكنني تحسين جودة الصورة عند تحويلها إلى PDF؟

لتحسين جودة الصورة، قم بتمكين استيفاء الصورة عن طريق الإعداد `setInterpolateImages` ل `true` في `PdfSaveOptions`سيؤدي هذا إلى الحصول على صور أكثر سلاسة وأعلى جودة في ملف PDF.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}