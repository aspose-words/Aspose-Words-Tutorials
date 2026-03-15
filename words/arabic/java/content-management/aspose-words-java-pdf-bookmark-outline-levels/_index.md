---
date: '2026-03-15'
description: تعلم كيفية إضافة إشارات مرجعية إلى ملفات PDF وتعيين مستويات المخطط باستخدام
  Aspose.Words for Java، مما يعزز تنقل PDF وقابليته للقراءة.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: إضافة إشارات مرجعية ومستويات مخطط PDF باستخدام Aspose.Words Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

" unchanged.

Make sure to keep markdown formatting.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة إشارات PDF ومستويات المخطط التفصيلي باستخدام Aspose.Words Java

## المقدمة
في هذا البرنامج التعليمي ستتعلم **كيفية إضافة إشارات PDF** وتكوين مستويات المخطط التفصيلي الخاصة بها باستخدام **Aspose.Words for Java**. تجعل الإشارات المنظمة بشكل جيد ملفات PDF الكبيرة سهلة التنقل، سواء كنت تتعامل مع عقود قانونية، تقارير مفصلة، أو مواد التعلم الإلكتروني.

**ما ستتعلمه**
- إعداد واستخدام **Aspose.Words for Java**
- **إنشاء إشارات متداخلة** في مستند Word
- **كيفية تعيين مستويات المخطط التفصيلي للإشارة** للحصول على هيكلية نظيفة
- **حفظ المستند كملف PDF** مع شجرة إشارات منظمة

دعنا نتأكد من أن لديك كل ما تحتاجه قبل أن نبدأ.

### المتطلبات المسبقة
قبل أن تبدأ، تأكد من وجود:
- **المكتبات والاعتمادات**: Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **إعداد البيئة**: تثبيت JDK وبيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- **المتطلبات المعرفية**: مهارات برمجة Java الأساسية ومعرفة بـ Maven أو Gradle.

## إجابات سريعة
- **ما هو الهدف الأساسي؟** إضافة إشارات PDF وتحديد مستويات المخطط التفصيلي.  
- **ما المكتبة المطلوبة؟** Aspose.Words for Java (v25.3+).  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للاختبار؛ يلزم ترخيص تجاري للإنتاج.  
- **هل يمكنني إنشاء PDF مع إشارات في خطوة واحدة؟** نعم—قم بتكوين `PdfSaveOptions` واستدعِ `doc.save`.  
- **هل يدعم التداخل؟** بالتأكيد، يمكنك إنشاء مستويات غير محدودة من الإشارات المتداخلة.

## إعداد Aspose.Words
للبدء، أدرج الاعتمادات اللازمة في مشروعك. إليك كيفية القيام بذلك باستخدام Maven و Gradle:

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### الحصول على الترخيص
Aspose.Words هو منتج تجاري، لكن يمكنك البدء بنسخة تجريبية مجانية لاستكشاف ميزاته.

1. **نسخة تجريبية مجانية**: قم بالتنزيل من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاختبار جميع الإمكانيات.  
2. **ترخيص مؤقت**: قدّم طلبًا للحصول على ترخيص مؤقت عبر [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/) إذا كنت بحاجة إلى وقت تقييم ممتد.  
3. **شراء**: للاستخدام المستمر، اشترِ ترخيصًا من [بوابة الشراء الخاصة بـ Aspose](https://purchase.aspose.com/buy).

بعد حصولك على ملف الترخيص، قم بتهيئته في مشروعك لفتح جميع الميزات.

## دليل التنفيذ
سنستعرض التنفيذ خطوة بخطوة، مقسمين كل جزء إلى قطع صغيرة.

### إنشاء إشارات متداخلة
**نظرة عامة**: تعلم كيفية **إنشاء إشارات متداخلة** داخل مستند Word باستخدام Aspose.Words for Java.

#### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
هذا ينشئ مستند Word جديدًا وكائن باني يسمح لك بإدراج المحتوى والإشارات.

#### الخطوة 2: إدراج إشارات متداخلة
ابدأ بإنشاء إشارة رئيسية:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
الآن، أدرج إشارة أخرى داخلها:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
أكمل الإشارة الخارجية:
```java
builder.endBookmark("Bookmark 1");
```

#### الخطوة 3: إضافة إشارات إضافية
يمكنك الاستمرار في إضافة إشارات حسب الحاجة. على سبيل المثال، إشارة ثالثة منفصلة:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### تكوين مستويات المخطط التفصيلي للإشارات
**نظرة عامة**: نظم إشاراتك بتعيين مستويات المخطط التفصيلي لها، والتي تحدد الهرمية التي ستظهر في عارضات PDF.

#### الخطوة 1: إعداد PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
سيتم تطبيق هذه الخيارات عند **حفظ المستند كملف PDF**.

#### الخطوة 2: إضافة مستويات المخطط التفصيلي
عيّن مستويات لكل إشارة؛ الأرقام الأقل تظهر أعلى في شجرة المخطط التفصيلي:
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### الخطوة 3: حفظ المستند
أخيرًا، أنشئ ملف PDF مع شجرة الإشارات المكوّنة:
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### نصائح استكشاف الأخطاء وإصلاحها
- **الإشارات المفقودة**: تأكد من أن كل `startBookmark` له `endBookmark` مطابق.  
- **المستويات غير الصحيحة**: راجع مرة أخرى ترتيب إضافة مستويات المخطط التفصيلي؛ الهرمية تتبع المستوى الرقمي الذي تعينه.  
- **المستندات الكبيرة**: استخدم `doc.removeUnusedResources()` قبل الحفظ لتقليل حجم PDF.

## تطبيقات عملية
إليك بعض السيناريوهات الواقعية حيث يبرز **إضافة إشارات PDF**:

1. **المستندات القانونية** – الانتقال سريعًا إلى البنود أو الملاحق أو المرفقات.  
2. **التقارير المالية** – التنقل بين الأقسام والجداول والرسوم البيانية.  
3. **مواد التعلم الإلكتروني** – توفير جدول محتويات قابل للنقر للقراء.  

## اعتبارات الأداء
- **إدارة الذاكرة**: عند معالجة ملفات Word الكبيرة جدًا، استدعِ `System.gc()` بعد الحفظ لتحرير الذاكرة.  
- **حجم المستند**: احذف الصور غير الضرورية أو النص المخفي قبل إنشاء الإشارات للحفاظ على خفة PDF النهائي.

## الخلاصة
أنت الآن تمتلك طريقة كاملة وجاهزة للإنتاج **لإضافة إشارات PDF**، وتكوين مستويات المخطط التفصيلي لها، و**إنشاء PDF مع إشارات** باستخدام Aspose.Words for Java. هذا النهج يحسن بشكل كبير قابلية استخدام PDF ويمنح المستخدمين النهائيين تجربة تنقل احترافية.

**الخطوات التالية**: جرّب دمج هذه التقنية مع Aspose.PDF for Java لتعديل الإشارات بعد إنشاء PDF، أو دمجها في خدمة معالجة دفعات تضيف جدول محتويات تلقائيًا إلى كل تقرير تقوم بإنشائه.

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
ج: أضف اعتماد Maven أو Gradle كما هو موضح أعلاه، ثم ضع ملف الترخيص في مجلد الموارد بالمشروع وقم بتهيئته عند بدء التشغيل.

**س: هل يمكنني استخدام الإشارات بدون مستويات المخطط التفصيلي؟**  
ج: نعم، لكن بدون مستويات المخطط التفصيلي سيعرض عارض PDF جميع الإشارات في نفس الهرمية، مما يجعل التنقل أصعب.

**س: ما هي حدود تداخل الإشارات؟**  
ج: تقنيًا لا يوجد حد ثابت، لكن حافظ على الهرمية معقولة (3‑5 مستويات) للحصول على قابلية قراءة مثالية.

**س: كيف يتعامل Aspose مع المستندات الكبيرة؟**  
ج: يقوم ببث المحتوى ويوفر طرقًا مثل `Document.optimizeResources()` للحفاظ على انخفاض استهلاك الذاكرة.

**س: هل يمكنني تعديل الإشارات بعد حفظ PDF؟**  
ج: بالتأكيد—استخدم Aspose.PDF for Java لتعديل، إعادة ترتيب، أو حذف الإشارات بعد الإنشاء.

## الموارد
- [توثيق Aspose.Words](https://reference.aspose.com/words/java/)
- [تحميل أحدث الإصدارات](https://releases.aspose.com/words/java/)
- [شراء ترخيص](https://purchase.aspose.com/buy)
- [نسخة تجريبية مجانية](https://releases.aspose.com/words/java/)
- [طلب ترخيص مؤقت](https://purchase.aspose.com/temporary-license/)
- [منتدى دعم Aspose](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-03-15  
**Tested With:** Aspose.Words for Java 25.3  
**Author:** Aspose