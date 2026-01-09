---
date: 2026-01-09
description: تعلم كيفية دمج المستندات باستخدام Aspose.Words للغة Java مع الحفاظ على
  التنسيق وربط رؤوس وتذييلات الصفحات والمزيد.
linktitle: Joining and Appending Documents
second_title: Aspose.Words Java Document Processing API
title: كيفية دمج المستندات باستخدام Aspose.Words للـ Java
url: /ar/java/document-manipulation/joining-and-appending-documents/
weight: 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية دمج المستندات باستخدام Aspose.Words for Java

يمكن أن يكون دمج ملفات Word برمجيًا مصدر صداع—خاصة عندما تحتاج إلى الحفاظ على الأنماط، أرقام الصفحات، والرؤوس/التذييلات دون تغيير. في هذا الدرس ستكتشف **كيفية دمج المستندات** باستخدام مكتبة Aspose.Words for Java، خطوة بخطوة. سنغطي الإلحاقات البسيطة، خيارات الاستيراد المتقدمة، التعامل مع إعدادات صفحات مختلفة، والحيل التي تحتاجها **للحفاظ على تنسيق الدمج** عبر مجموعة متنوعة من السيناريوهات الواقعية.

## إجابات سريعة
- **ما هي أسهل طريقة لدمج مستندات Word؟** استخدم `Document.appendDocument` مع `ImportFormatMode.KEEP_SOURCE_FORMATTING`.  
- **هل يمكنني الحفاظ على الأنماط الأصلية لكل ملف مصدر؟** نعم—حدد `ImportFormatMode.USE_DESTINATION_STYLES` أو فعّل Smart Style Behavior.  
- **كيف أحافظ على صحة أرقام الصفحات بعد الدمج؟** حوّل حقول `NUMPAGES` إلى مراجع صفحات واستدعِ `updatePageLayout()`.  
- **هل تبقى الرؤوس والتذييلات مرتبطة تلقائيًا؟** يمكنك ربطها أو فك ربطها باستخدام `linkToPrevious(true/false)`.  
- **ماذا أحتاج قبل البدء؟** إضافة Aspose.Words for Java إلى مشروعك وتوافر ملفات `.docx` المصدرية.

## مقدمة حول دمج وإلحاق المستندات في Aspose.Words for Java

في هذا الدرس، سنستكشف كيفية دمج وإلحاق المستندات باستخدام مكتبة Aspose.Words for Java. ستتعلم كيف تدمج عدة مستندات بسلاسة مع الحفاظ على التنسيق والبنية.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من إعداد Aspose.Words for Java API في مشروع Java الخاص بك.

## خيارات دمج المستندات

### إلحاق بسيط

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### إلحاق مع خيارات استيراد التنسيق

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### إلحاق إلى مستند فارغ

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### إلحاق مع تحويل أرقام الصفحات

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convert NUMPAGES fields
dstDoc.updatePageLayout(); // Update page layout for correct numbering
```

## التعامل مع إعدادات صفحات مختلفة

عند إلحاق مستندات ذات إعدادات صفحات مختلفة:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ensure page setup settings match the destination document
```

## دمج مستندات بأنماط مختلفة

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## سلوك الأنماط الذكي

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

## التعامل مع صناديق النص

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

### فك ربط الرؤوس والتذييلات

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## لماذا هذا مهم لمشاريع “merge word documents java”

عندما تحتاج إلى **دمج مستندات Word بأسلوب Java**، يكون الحفاظ على مظهر كل ملف أمرًا حيويًا للعمليات القانونية، النشر، أو إعداد التقارير. باستخدام التقنيات أعلاه تضمن أن:

* تبقى الأنماط من كل مصدر سليمة (أو موحدة، حسب اختيارك).  
* أرقام الصفحات وفواصل الأقسام تتصرف بشكل متوقع.  
* يمكن ربط الرؤوس والتذييلات أو إبقاؤها مستقلة بسطر واحد من الشيفرة.  

## الأخطاء الشائعة والنصائح

| المشكلة | السبب | طريقة الحل |
|-------|----------------|------------|
| فقدان الترقيم بعد الدمج | حقول `NUMPAGES` لا تزال تشير إلى الأقسام الأصلية | استدعِ `convertNumPageFieldsToPageRef` ثم `updatePageLayout()` |
| تعارض الأنماط | استخدام `KEEP_SOURCE_FORMATTING` مع أنماط متضاربة | بدّل إلى `USE_DESTINATION_STYLES` أو فعّل Smart Style Behavior |
| ظهور صفحات فارغة | قيم `SectionStart` مختلفة | حدّد `SectionStart.CONTINUOUS` على الأقسام المصدرية قبل الإلحاق |

## الأسئلة المتكررة

**س: كيف يمكنني دمج مستندات بأنماط مختلفة بسلاسة؟**  
ج: استخدم `ImportFormatMode.USE_DESTINATION_STYLES` عند الإلحاق، أو فعّل `SmartStyleBehavior` للحصول على دمج أذكى.

**س: هل يمكنني الحفاظ على ترقيم الصفحات عند إلحاق المستندات؟**  
ج: نعم، حوّل حقول `NUMPAGES` إلى مراجع صفحات باستخدام `convertNumPageFieldsToPageRef` ثم استدعِ `updatePageLayout()`.

**س: ما هو سلوك الأنماط الذكي؟**  
ج: يقوم تلقائيًا بربط الأنماط المصدرية بالأنماط الوجهة عندما يكون ذلك ممكنًا، مما يساعد على الحفاظ على مظهر موحد عبر المحتوى المدمج.

**س: كيف أتعامل مع صناديق النص عند إلحاق المستندات؟**  
ج: حدّد `importFormatOptions.setIgnoreTextBoxes(false)` حتى تُحافظ على صناديق النص أثناء الدمج.

**س: ماذا أفعل إذا أردت ربط أو فك ربط الرؤوس والتذييلات بين المستندات؟**  
ج: استخدم `linkToPrevious(true)` للربط، أو `linkToPrevious(false)` للفصل قبل استدعاء `appendDocument`.

## الخلاصة

توفر Aspose.Words for Java أدوات مرنة وقوية لـ **كيفية دمج المستندات**، سواء كنت تحتاج إلى الحفاظ على التنسيق الدقيق، التعامل مع إعدادات صفحات متنوعة، أو التحكم في ربط/فصل الرؤوس والتذييلات. جرّب مقتطفات الشيفرة أعلاه لتناسب سير عمل معالجة المستندات الخاص بك، وستتمكن من **دمج مستندات Word بأسلوب Java** بثقة.

---

**آخر تحديث:** 2026-01-09  
**تم الاختبار مع:** Aspose.Words for Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}