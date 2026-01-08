---
date: 2025-12-24
description: تعلم كيفية حفظ المستند كملف PDF باستخدام Aspose.Words للغة Java، مع تغطية
  تحويل Word إلى PDF في Java، تصدير بنية المستند إلى PDF، وخيارات PDF المتقدمة في
  Aspose.Words.
linktitle: Saving Documents as PDF
second_title: Aspose.Words Java Document Processing API
title: كيفية حفظ المستند بصيغة PDF باستخدام Aspose.Words للـ Java
url: /ar/java/document-loading-and-saving/saving-documents-as-pdf/
weight: 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ المستند كملف PDF باستخدام Aspose.Words للـ Java

في هذا الدرس الشامل ستكتشف **كيفية حفظ المستند كملف PDF** باستخدام مكتبة Aspose.Words للـ Java القوية. سواءً كنت تبني محرك تقارير، نظام فواتير آلي، أو تحتاج ببساطة إلى أرشفة ملفات Word بصيغة PDF، فإن هذا الدليل يرشّحك خلال كل خطوة—من التحويل الأساسي إلى ضبط مخرجات PDF بدقة باستخدام الخيارات المتقدمة.

## إجابات سريعة
- **هل يمكن لـ Aspose.Words تحويل Word إلى PDF في Java؟** نعم، بسطر واحد من الشيفرة يمكنك تحويل ملف .docx إلى PDF.  
- **هل أحتاج إلى ترخيص للاستخدام في الإنتاج؟** الترخيص التجاري مطلوب للعمليات غير التجريبية.  
- **ما إصدارات Java المدعومة؟** Java 8 وما فوق مدعومة بالكامل.  
- **هل يمكن تضمين الخطوط في PDF؟** بالتأكيد—قم بتعيين `setEmbedFullFonts(true)` في `PdfSaveOptions`.  
- **هل جودة الصورة قابلة للتعديل؟** نعم، استخدم `setImageCompression` و `setInterpolateImages` للتحكم في الحجم والوضوح.

## ما هو “حفظ المستند كملف PDF”؟
حفظ المستند كملف PDF يعني تصدير التخطيط البصري، الخطوط، والمحتوى لملف Word إلى صيغة Portable Document Format، وهو نوع ملف يُعرض عالميًا ويحافظ على التنسيق عبر الأنظمة.

## لماذا تحويل Word إلى PDF باستخدام Aspose.Words للـ Java؟
- **دقة عالية:** المخرجات تعكس تخطيط Word الأصلي، بما في ذلك الجداول، رؤوس وتذييلات الصفحات، والرسومات المعقدة.  
- **لا حاجة إلى Microsoft Office:** يعمل على أي خادم أو بيئة سحابية.  
- **تخصيص غني:** تحكم في الخطوط، ضغط الصور، بنية المستند، والبيانات الوصفية عبر `PdfSaveOptions`.  
- **الأداء:** مُحسّن للدفعات الكبيرة والسيناريوهات متعددة الخيوط.

## المتطلبات المسبقة
- تثبيت Java Development Kit (JDK).  
- مكتبة Aspose.Words للـ Java (قم بتحميلها من الموقع الرسمي).  

يمكنك الحصول على المكتبة من المصدر التالي:

- تحميل Aspose.Words للـ Java: [here](https://releases.aspose.com/words/java/)

## تحويل مستند إلى PDF

لتحويل مستند Word إلى PDF، يمكنك استخدام المقتطف البرمجي التالي:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

استبدل `"input.docx"` بمسار ملف Word الخاص بك و `"output.pdf"` بمسار ملف PDF الناتج المطلوب.

## التحكم في خيارات حفظ PDF

يمكنك التحكم في خيارات حفظ PDF المتنوعة باستخدام الفئة `PdfSaveOptions`. على سبيل المثال، يمكنك تعيين عنوان العرض لمستند PDF كما يلي:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## تضمين الخطوط في PDF

لتضمين الخطوط في ملف PDF المُنشأ، استخدم الشيفرة التالية:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## تخصيص خصائص المستند

يمكنك تخصيص خصائص المستند في ملف PDF المُنتج. على سبيل المثال:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## تصدير بنية المستند

لتصدير بنية المستند، عيّن الخيار `exportDocumentStructure` إلى `true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## ضغط الصور

يمكنك التحكم في ضغط الصور باستخدام الشيفرة التالية:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## تحديث خاصية “آخر طباعة”

لتحديث خاصية “Last Printed” في PDF، استخدم:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## عرض تأثيرات DML ثلاثية الأبعاد

للتصيير المتقدم لتأثيرات DML ثلاثية الأبعاد، عيّن وضع العرض:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## تحسين جودة الصور (Interpolation)

يمكنك تمكين تحسين الصور لرفع جودة الصورة:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## حالات الاستخدام الشائعة والنصائح

- **تحويل دفعي:** كرّر العملية على مجلد يحتوي على ملفات `.docx` واستخدم نفس `PdfSaveOptions` للحصول على مخرجات متسقة.  
- **الأرشفة القانونية:** فعّل `setExportDocumentStructure(true)` لإنشاء ملفات PDF مُوسومة تلبي معايير الوصول.  
- **نصيحة الأداء:** أعد استخدام كائن `PdfSaveOptions` واحد عند معالجة العديد من المستندات لتقليل عبء إنشاء الكائنات.  
- **استكشاف الأخطاء:** إذا ظهرت خطوط مفقودة، تأكد من أن ملفات الخطوط المطلوبة متاحة للـ JVM وأن `setEmbedFullFonts(true)` مفعّلة.

## الخلاصة

توفر Aspose.Words للـ Java إمكانيات شاملة لتحويل مستندات Word إلى صيغة PDF مع مرونة وخيارات تخصيص واسعة. يمكنك التحكم في جوانب مختلفة من مخرجات PDF، بما في ذلك الخطوط، خصائص المستند، ضغط الصور، وأكثر، مما يجعلها حلاً قويًا لسيناريوهات **حفظ المستند كملف PDF**.

## الأسئلة المتكررة

### كيف يمكنني تحويل مستند Word إلى PDF باستخدام Aspose.Words للـ Java؟

لتحويل مستند Word إلى PDF، استخدم الشيفرة التالية:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

استبدل `"input.docx"` بمسار ملف Word الخاص بك و `"output.pdf"` بمسار ملف PDF المطلوب.

### هل يمكنني تضمين الخطوط في PDF الذي تُنشئه Aspose.Words للـ Java؟

نعم، يمكنك تضمين الخطوط في PDF عن طريق تعيين خيار `setEmbedFullFonts` إلى `true` في `PdfSaveOptions`. إليك مثالًا:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### كيف يمكنني تخصيص خصائص المستند في PDF المُنتج؟

يمكنك تخصيص خصائص المستند في PDF باستخدام خيار `setCustomPropertiesExport` في `PdfSaveOptions`. على سبيل المثال:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### ما هو هدف ضغط الصور في Aspose.Words للـ Java؟

ضغط الصور يتيح لك التحكم في جودة وحجم الصور في PDF المُنشأ. يمكنك تعيين وضع ضغط الصورة باستخدام `setImageCompression` في `PdfSaveOptions`.

### كيف يمكنني تحديث خاصية “Last Printed” في PDF؟

يمكنك تحديث خاصية “Last Printed” في PDF عن طريق تعيين `setUpdateLastPrintedProperty` إلى `true` في `PdfSaveOptions`. سيظهر تاريخ الطباعة الأخير في بيانات تعريف PDF.

### كيف يمكنني تحسين جودة الصورة عند التحويل إلى PDF؟

لتحسين جودة الصورة، فعّل تحسين الصور عن طريق تعيين `setInterpolateImages` إلى `true` في `PdfSaveOptions`. سيؤدي ذلك إلى صور أكثر سلاسة وجودة أعلى في PDF.

---

**آخر تحديث:** 2025-12-24  
**تم الاختبار مع:** Aspose.Words للـ Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}