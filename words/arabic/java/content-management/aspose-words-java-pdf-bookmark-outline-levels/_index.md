---
date: '2025-11-27'
description: تعلم كيفية إنشاء العلامات المرجعية، وتوليد ملفات PDF مع العلامات المرجعية،
  وتحويل ملفات Word إلى PDF في جافا باستخدام Aspose.Words. يغطي هذا الدليل العلامات
  المرجعية المتداخلة ومستويات المخطط.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: ar
title: كيفية إنشاء العلامات المرجعية وتعيين مستويات المخطط في ملفات PDF باستخدام Aspose.Words
  Java
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء العلامات المرجعية وتعيين مستويات المخطط في ملفات PDF باستخدام Aspose.Words Java

## المقدمة
إذا واجهت صعوبة في **كيفية إنشاء العلامات المرجعية** التي تظل منظمة عند تحويل مستند Word إلى PDF، فأنت في المكان المناسب. في هذا الدرس سنستعرض العملية الكاملة لإنشاء ملف PDF مع العلامات المرجعية، وتداخلها، وتعيين مستويات المخطط بحيث يكون ملف PDF النهائي سهل التنقل. في النهاية ستتمكن من **تحويل Word إلى PDF باستخدام Java** بأسلوب يحتوي على هيكلية علامات مرجعية نظيفة تعمل في أي عارض PDF.

### ما ستتعلمه
- إعداد Aspose.Words for Java في بيئة التطوير الخاصة بك.  
- **كيفية إنشاء العلامات المرجعية** برمجياً وتداخلها.  
- تكوين مستويات مخطط العلامات المرجعية لإنشاء PDF يحتوي على علامات مرجعية تعكس بنية المستند.  
- حفظ ملف Word كملف PDF مع الحفاظ على هيكلية العلامات المرجعية.

## إجابات سريعة
- **ما هي الفئة الأساسية لإنشاء المستندات؟** `DocumentBuilder`.  
- **أي خيار يتحكم في هيكلية العلامات المرجعية؟** `BookmarksOutlineLevelCollection` داخل `PdfSaveOptions`.  
- **هل يمكنني استخدام Maven أو Gradle؟** نعم – كلاهما موضح أدناه.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تعمل للاختبار؛ يلزم ترخيص دائم للإنتاج.  
- **هل هذا النهج مناسب للمستندات الكبيرة؟** نعم، ولكن يُنصح بأخذ تقنيات تحسين الذاكرة في الاعتبار (مثل إزالة الموارد غير المستخدمة).

### المتطلبات المسبقة
قبل أن تبدأ، تأكد من أن لديك:

- **المكتبات والاعتمادات** – Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **البيئة** – JDK 8 أو أحدث، وIDE مثل IntelliJ IDEA أو Eclipse.  
- **المعرفة الأساسية** – أساسيات برمجة Java ومعرفة بـ Maven أو Gradle.

## إعداد Aspose.Words
لبدء العمل، أدرج الاعتمادات اللازمة في مشروعك. إليك كيفية إضافة Aspose.Words باستخدام Maven أو Gradle:

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
Aspose.Words هي مكتبة تجارية، لكن يمكنك البدء بنسخة تجريبية مجانية:

1. **نسخة تجريبية مجانية** – تحميل من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/).  
2. **ترخيص مؤقت** – تقديم طلب على [صفحة الترخيص المؤقت](https://purchase.aspose.com/temporary-license/) إذا كنت بحاجة إلى مفتاح قصير الأمد.  
3. **ترخيص كامل** – الشراء عبر [بوابة شراء Aspose](https://purchase.aspose.com/buy) للاستخدام في الإنتاج.  

بعد الحصول على ملف الترخيص، حمّله عند بدء تشغيل التطبيق لتفعيل جميع الميزات.

## كيفية إنشاء العلامات المرجعية في ملفات PDF باستخدام Aspose.Words Java
أدناه نقسم التنفيذ إلى خطوات واضحة مرقمة. كل خطوة تتضمن شرحًا قصيرًا يليه كتلة الكود الأصلية (بدون تغيير).

### الخطوة 1: تهيئة مستند DocumentBuilder
نبدأ بنسخة جديدة من كائن `Document` و`DocumentBuilder` يتيح لنا إدراج المحتوى والعلامات المرجعية.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### الخطوة 2: إدراج العلامة المرجعية الأولى (الأصلية)
إنشاء علامة مرجعية من المستوى الأعلى ستحتوي لاحقًا على علامة فرعية.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### الخطوة 3: تداخل علامة مرجعية فرعية داخل الأصلية
الآن نضيف علامة مرجعية ثانية تعيش داخل الأولى، لتوضيح التداخل.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### الخطوة 4: إغلاق العلامة المرجعية الأصلية
إنهاء العلامة المرجعية الخارجية بعد المحتوى المتداخل.

```java
builder.endBookmark("Bookmark 1");
```

### الخطوة 5: إضافة علامة مرجعية ثالثة مستقلة
يمكنك دائمًا إضافة المزيد من العلامات المرجعية التي لا تكون متداخلة.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## تكوين مستويات مخطط العلامات المرجعية
بعد وضع العلامات المرجعية، نخبر Aspose.Words كيف يجب أن تظهر هذه العلامات في مخطط PDF (لوحة التنقل اليسرى).

### الخطوة 6: إعداد PdfSaveOptions
`PdfSaveOptions` يتيح لنا الوصول إلى إعدادات المخطط.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### الخطوة 7: تعيين مستويات الهرمية
كل علامة مرجعية تحصل على مستوى عدد صحيح؛ الأرقام الأقل تعني مستوى أعلى في الهرمية.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### الخطوة 8: حفظ المستند كملف PDF
أخيرًا، تصدير مستند Word إلى PDF مع الحفاظ على مخطط العلامات المرجعية.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## لماذا استخدام هذا النهج لإنشاء PDF مع العلامات المرجعية؟
- **تنقل احترافي** – يمكن للقراء الانتقال مباشرة إلى الأقسام، مما يحسن قابلية الاستخدام للتقارير الكبيرة أو العقود القانونية.  
- **تحكم كامل** – أنت الذي تحدد الهيكلية، وليس عارض PDF.  
- **متعدد المنصات** – يعمل بنفس الطريقة على Windows وLinux وmacOS لأنه مكتوب بالكامل بلغة Java.  

## المشكلات الشائعة والحلول
| العَرَض | السبب المحتمل | الحل |
|---|---|---|
| العلامات المرجعية مفقودة في PDF | `startBookmark` بدون `endBookmark` مطابق | تحقق من أن كل `startBookmark` له `endBookmark` مطابق. |
| الهرمية غير صحيحة | مستويات المخطط تم تعيينها بترتيب غير صحيح | تأكد من أن العلامات المرجعية الأصلية لها أرقام مستويات أقل من العلامات الفرعية. |
| الترخيص غير مفعّل | ملف الترخيص لم يتم تحميله قبل إنشاء المستند | حمّل الترخيص في بداية تشغيل التطبيق (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## التطبيقات العملية
1. **المستندات القانونية** – التنقل السريع بين البنود والملحقات والعروض.  
2. **التقارير المالية** – الانتقال بين أقسام مثل بيان الدخل، والميزانية العمومية، والملاحظات.  
3. **مواد التعلم الإلكتروني** – توفير فهرس محتويات يعكس مخطط PDF.  

## اعتبارات الأداء
- **إدارة الذاكرة** – بالنسبة لملفات Word الكبيرة جداً، يُنصح باستدعاء `doc.cleanup()` قبل الحفظ.  
- **تحسين الموارد** – إزالة الصور أو الأنماط غير المستخدمة للحفاظ على حجم PDF صغير.  

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
ج: أضف الاعتماد Maven أو Gradle كما هو موضح أعلاه، ثم ضع ملف الترخيص في مسار الفئة (classpath) وحمّله أثناء التشغيل.

**س: هل يمكنني إنشاء العلامات المرجعية دون تعيين مستويات المخطط؟**  
ج: نعم، لكن عارض PDF سيعرضها كقائمة مسطحة، مما قد يصعب التنقل في المستندات المعقدة.

**س: هل هناك حد لعمق تداخل العلامات المرجعية؟**  
ج: من الناحية التقنية لا يوجد حد، لكن معظم عارضي PDF يدعمون حتى 9 مستويات بسهولة. حافظ على هيكلية منطقية للقراء.

**س: كيف يتعامل Aspose مع ملفات Word الكبيرة جداً؟**  
ج: المكتبة تقوم ببث المحتوى وتوفر طرقاً مثل `Document.optimizeResources()` لتقليل استهلاك الذاكرة.

**س: هل يمكنني تعديل العلامات المرجعية بعد إنشاء PDF؟**  
ج: بالتأكيد – يمكنك استخدام Aspose.PDF for Java لإضافة أو إزالة أو إعادة تسمية العلامات المرجعية في PDF موجود.

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

**آخر تحديث:** 2025-11-27  
**تم الاختبار مع:** Aspose.Words 25.3 for Java  
**المؤلف:** Aspose