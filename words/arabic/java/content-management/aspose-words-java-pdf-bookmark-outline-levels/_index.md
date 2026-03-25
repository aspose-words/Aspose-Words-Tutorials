---
date: '2026-03-25'
description: تعلم كيفية إنشاء العلامات المرجعية وتوليد ملف PDF مع العلامات المرجعية
  باستخدام Aspose.Words for Java. يغطي هذا الدليل خطوة بخطوة التداخل ومستويات المخطط
  وتصدير PDF.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: كيفية إنشاء إشارات مرجعية في ملفات PDF باستخدام Aspose.Words للـ Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إتقان مستويات مخطط العلامات المرجعية في ملفات PDF باستخدام Aspose.Words للـ Java

## المقدمة
إذا كنت بحاجة إلى **how to create bookmarks** التي تجعل ملفات PDF الخاصة بك سهلة التنقل، فأنت في المكان الصحيح. في هذا الدرس سنستعرض إعداد Aspose.Words للـ Java، إنشاء علامات مرجعية متداخلة، تعيين مستويات المخطط، وأخيرًا **generating PDF with bookmarks** التي تبدو احترافية وسهلة الاستخدام. في النهاية ستحصل على نمط قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Java.

**ما ستتعلمه**
- تثبيت وترخيص Aspose.Words للـ Java  
- إنشاء علامات مرجعية متداخلة في مستند Word  
- تهيئة مستويات مخطط العلامات المرجعية للتنقل الهرمي  
- حفظ المستند كملف PDF مع علامات مرجعية منظمة بشكل صحيح  

### إجابات سريعة
- **ما هي الفئة الأساسية لبناء المستندات؟** `DocumentBuilder`  
- **هل يمكنني تداخل العلامات المرجعية؟** نعم، ببساطة ابدأ علامة مرجعية جديدة قبل إنهاء العلامة الأصلية.  
- **كيف يمكنني تعيين مستويات المخطط؟** استخدم `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()`.  
- **هل أحتاج إلى ترخيص لتصدير PDF؟** النسخة التجريبية تعمل، لكن الترخيص يزيل حدود التقييم.  
- **ما هي العبارة المفتاحية التي يستهدفها هذا الدرس؟** *how to create bookmarks*  

## ما هو “how to create bookmarks” في Aspose.Words؟
العلامات المرجعية هي مواقع مسماة داخل مستند Word تصبح إدخالات قابلة للنقر في لوحة مخطط PDF. تسمح للقراء بالانتقال مباشرة إلى الأقسام أو الجداول أو الأشكال دون الحاجة للتمرير.

## لماذا إنشاء PDF مع علامات مرجعية؟
إدراج العلامات المرجعية أثناء إنشاء PDF يوفر عليك خطوة ما بعد المعالجة، يحسن إمكانية الوصول، ويمنح المستندات القانونية أو التقنية بنية نظيفة وقابلة للبحث.

## المتطلبات المسبقة
- **المكتبات والاعتمادات**: Aspose.Words للـ Java (الإصدار 25.3 أو أحدث).  
- **البيئة**: JDK 8 أو أحدث، IntelliJ IDEA/Eclipse، وMaven أو Gradle.  
- **المعرفة**: أساسيات Java، ملفات بناء Maven/Gradle، ومعرفة بمفاهيم PDF.  

## إعداد Aspose.Words
للبدء، أدرج الاعتمادات اللازمة في مشروعك. إليك كيفية القيام بذلك باستخدام Maven وGradle:

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
Aspose.Words هو منتج تجاري، لكن يمكنك البدء بنسخة تجريبية مجانية لاستكشاف ميزاته. اتبع الخطوات التالية:

1. **نسخة تجريبية مجانية**: قم بتنزيلها من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاختبار جميع الإمكانيات.  
2. **ترخيص مؤقت**: قدم طلبًا للحصول على ترخيص مؤقت عبر [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/) إذا لزم الأمر.  
3. **شراء**: للاستخدام المستمر، اشترِ ترخيصًا من [بوابة الشراء لـ Aspose](https://purchase.aspose.com/buy).

بمجرد حصولك على ملف الترخيص، قم بتهيئته في مشروعك لفتح جميع ميزات Aspose.Words.

## دليل التنفيذ
سنقسم التنفيذ إلى جزأين منطقيين: إنشاء علامات مرجعية متداخلة وتكوين مستويات المخطط الخاصة بها.

### كيفية إنشاء علامات مرجعية في مستند Word
**نظرة عامة** – يوضح هذا القسم الشيفرة الدقيقة التي تحتاجها **how to create bookmarks** والتي يمكن لاحقًا تصديرها كهرمية PDF.

#### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
كائن `Document` يمثل ملف Word، بينما يتيح لك `DocumentBuilder` إدراج النصوص والصور والعلامات المرجعية.

#### الخطوة 2: إدراج علامات مرجعية متداخلة
ابدأ بعلامة مرجعية أساسية:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
الآن أدخل علامة مرجعية أخرى داخل الأولى:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
أغلق العلامة المرجعية الخارجية:
```java
builder.endBookmark("Bookmark 1");
```

#### الخطوة 3: إضافة علامات مرجعية مستقلة إضافية
يمكنك الاستمرار في إضافة ما تحتاجه. على سبيل المثال، علامة مرجعية ثالثة منفصلة:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### كيفية إنشاء PDF مع علامات مرجعية ومستويات مخطط
**نظرة عامة** – بعد وجود العلامات المرجعية في مستند Word، نقوم بتكوين هرمية المخطط قبل حفظه كملف PDF.

#### الخطوة 1: إعداد PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
هذه الخيارات تخبر Aspose.Words كيفية تحويل علامات مرجعية Word إلى إدخالات مخطط PDF.

#### الخطوة 2: تعيين مستويات المخطط
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
العدد الصحيح يحدد العمق – `1` هو المستوى الأعلى، `2` هو مستوى فرعي، وهكذا.

#### الخطوة 3: حفظ المستند كملف PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
سيعرض PDF الناتج لوحة علامات مرجعية مرتبة تعكس الهرمية التي حددتها.

### نصائح استكشاف الأخطاء وإصلاحها
- **العلامات المرجعية المفقودة** – تحقق مرة أخرى من أن كل `startBookmark` له `endBookmark` مطابق.  
- **المستويات غير الصحيحة** – تأكد من أن أرقام المستويات تتطابق مع علاقة الأب‑ابن المقصودة.  
- **مشكلات الترخيص** – إذا رأيت علامات مائية للتقييم، تأكد من تحميل ملف الترخيص بشكل صحيح قبل أي عملية على المستند.

## تطبيقات عملية
إليك سيناريوهات شائعة حيث تكون **how to create bookmarks** و**generate PDF with bookmarks** ذات قيمة خاصة:

1. **العقود القانونية** – الانتقال سريعًا إلى البنود أو التعريفات أو الملاحق.  
2. **التقارير المالية** – التنقل بين الأقسام والجداول والرسوم البيانية دون التمرير.  
3. **مواد التعلم الإلكتروني** – توفير جدول محتويات قابل للنقر للفصول والفصول الفرعية.  

## اعتبارات الأداء
- **حجم المستند** – إزالة الأنماط أو الصور غير المستخدمة قبل الحفظ للحفاظ على خفة PDF.  
- **إدارة الذاكرة** – للملفات الكبيرة جدًا، فكر في استدعاء `doc.updatePageLayout()` بعد التعديلات الكبيرة لتحرير الموارد.

## الخلاصة
الآن لديك طريقة كاملة وجاهزة للإنتاج لـ **how to create bookmarks**، تعيين مستويات المخطط، و**generate PDF with bookmarks** باستخدام Aspose.Words للـ Java. دمج هذا النمط في خطوط معالجة المستندات الخاصة بك لتقديم ملفات PDF مصقولة وسهلة التنقل في كل مرة.

**الخطوات التالية**: جرّب إضافة أيقونات مخصصة للعلامات المرجعية، أو دمج هذا النهج مع Aspose.PDF للمهام ما بعد المعالجة مثل إضافة التوقيعات الرقمية.

## قسم الأسئلة الشائعة
1. **كيف أقوم بتثبيت Aspose.Words للـ Java؟**  
   - أضفه كاعتماد عبر Maven أو Gradle، ثم قم بإعداد ملف الترخيص الخاص بك.  
2. **هل يمكنني استخدام العلامات المرجعية بدون مستويات مخطط؟**  
   - نعم، لكن استخدام مستويات المخطط يحسن التنقل في ملفات PDF.  
3. **ما هي حدود تداخل العلامات المرجعية؟**  
   - لا يوجد حد صارم، لكن حافظ على منطقية الهرمية للمستخدمين النهائيين.  
4. **كيف يتعامل Aspose مع المستندات الكبيرة؟**  
   - يدير الموارد بكفاءة، رغم أنه يُنصح بالتحسين للملفات الكبيرة جدًا.  
5. **هل يمكنني تعديل العلامات المرجعية بعد حفظ PDF؟**  
   - نعم، يمكنك استخدام Aspose.PDF للـ Java لتعديل العلامات المرجعية بعد التحويل.  

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

**آخر تحديث:** 2026-03-25  
**تم الاختبار مع:** Aspose.Words 25.3 للـ Java  
**المؤلف:** Aspose