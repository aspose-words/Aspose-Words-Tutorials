---
date: '2025-12-10'
description: تعلم كيفية إنشاء إشارات مرجعية متداخلة وحفظ إشارات مرجعية PDF في Word
  باستخدام Aspose.Words للغة Java، وتنظيم تنقل PDF بفعالية.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: إنشاء إشارات مرجعية متداخلة في PDF باستخدام Aspose.Words Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء إشارات مرجعية متداخلة في PDF باستخدام Aspose.Words Java

## المقدمة
إذا كنت بحاجة إلى **إنشاء إشارات مرجعية متداخلة** في ملف PDF تم إنشاؤه من مستند Word، فقد وصلت إلى المكان الصحيح. في هذا الدليل سنستعرض العملية بالكامل باستخدام Aspose.Words for Java، بدءًا من إعداد المكتبة إلى تكوين مستويات مخطط الإشارة المرجعية وأخيرًا **حفظ إشارات مرجعية PDF من Word** بحيث يكون ملف PDF النهائي سهل التنقل.

**ما ستتعلمه**
- كيفية إعداد Aspose.Words for Java
- كيفية **إنشاء إشارات مرجعية متداخلة** داخل مستند Word
- كيفية تعيين مستويات المخطط لتسهيل التنقل في PDF
- كيفية **حفظ إشارات مرجعية PDF من Word** باستخدام PdfSaveOptions

## إجابات سريعة
- **ما هو الهدف الأساسي؟** إنشاء إشارات مرجعية متداخلة وحفظ إشارات مرجعية PDF من Word في ملف PDF واحد.  
- **ما المكتبة المطلوبة؟** Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للاختبار؛ يلزم ترخيص تجاري للإنتاج.  
- **هل يمكن التحكم في مستويات المخطط؟** نعم، باستخدام `PdfSaveOptions` و `BookmarksOutlineLevelCollection`.  
- **هل هذا مناسب للمستندات الكبيرة؟** نعم، مع إدارة الذاكرة بشكل صحيح وتحسين الموارد.

## ما هو “إنشاء إشارات مرجعية متداخلة”؟
إنشاء إشارات مرجعية متداخلة يعني وضع إشارة مرجعية داخل أخرى، مكوّنةً هيكلًا هرميًا يعكس الأقسام المنطقية في مستندك. ينعكس هذا الهرم في لوحة تنقل PDF، مما يسمح للقراء بالقفز مباشرة إلى الفصول أو الفروع المحددة.

## لماذا استخدام Aspose.Words for Java لحفظ إشارات مرجعية PDF من Word؟
توفر Aspose.Words واجهة برمجة تطبيقات عالية المستوى تُجرد من تعقيدات معالجة PDF منخفضة المستوى، مما يتيح لك التركيز على هيكل المحتوى بدلاً من تفاصيل تنسيق الملف. كما أنها تحافظ على جميع ميزات Word (الأنماط، الصور، الجداول) مع إعطائك تحكمًا كاملاً في هيكلية الإشارات المرجعية.

## المتطلبات المسبقة
- **المكتبات**: Aspose.Words for Java (الإصدار 25.3+).  
- **بيئة التطوير**: JDK 8 أو أحدث، IDE مثل IntelliJ IDEA أو Eclipse.  
- **أداة البناء**: Maven أو Gradle (حسب تفضيلك).  
- **المعرفة الأساسية**: برمجة Java، أساسيات Maven/Gradle.

## إعداد Aspose.Words
أضف المكتبة إلى مشروعك باستخدام أحد المقاطع التالية.

**Maven**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### الحصول على الترخيص
1. **نسخة تجريبية مجانية** – قم بالتحميل من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاختبار جميع الإمكانيات.  
2. **ترخيص مؤقت** – قدِّم طلبًا على [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/) إذا كنت بحاجة إلى مفتاح قصير الأمد.  
3. **شراء** – احصل على ترخيص دائم من [بوابة شراء Aspose](https://purchase.aspose.com/buy).

بعد حصولك على ملف `.lic`، قم بتحميله عند بدء تشغيل التطبيق لتفعيل جميع الميزات.

## دليل التنفيذ
فيما يلي شرح خطوة بخطوة. كل كتلة شفرة تبقى كما هي للحفاظ على الوظيفة.

### كيفية إنشاء إشارات مرجعية متداخلة في مستند Word
#### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
هذا ينشئ مستند Word فارغًا وكائن Builder لإدراج المحتوى.

#### الخطوة 2: إدراج الإشارة المرجعية الأولى (الأصلية)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### الخطوة 3: إدراج إشارة مرجعية ثانية داخل الأولى
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### الخطوة 4: إغلاق الإشارة المرجعية الخارجية
```java
builder.endBookmark("Bookmark 1");
```

#### الخطوة 5: إضافة إشارة مرجعية ثالثة منفصلة
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### كيفية حفظ إشارات مرجعية PDF من Word وتعيين مستويات المخطط
#### الخطوة 1: تكوين PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### الخطوة 2: تعيين مستويات المخطط لكل إشارة مرجعية
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### الخطوة 3: حفظ المستند كملف PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## المشكلات الشائعة والحلول
- **الإشارات المرجعية المفقودة** – تأكد من أن كل `startBookmark` له `endBookmark` مطابق.  
- **الهيكل غير الصحيح** – تأكد من أن أرقام مستويات المخطط تعكس علاقة الأصل‑الابن المطلوبة (الأرقام الأقل = المستوى الأعلى).  
- **حجم الملف كبير** – احذف الأنماط أو الصور غير المستخدمة قبل الحفظ، أو استدعِ `doc.optimizeResources()` إذا لزم الأمر.

## التطبيقات العملية
| السيناريو | فائدة الإشارات المرجعية المتداخلة |
|----------|----------------------------|
| العقود القانونية | قفزة سريعة إلى البنود والفقرة الفرعية |
| التقارير التقنية | التنقل بين الأقسام المعقدة والملحقات |
| مواد التعلم الإلكتروني | الوصول المباشر إلى الفصول، الدروس، والاختبارات |

## اعتبارات الأداء
- **استخدام الذاكرة** – عالج المستندات الكبيرة على دفعات أو استخدم `DocumentBuilder.insertDocument` لدمج أجزاء أصغر.  
- **حجم الملف** – ضغط الصور وإزالة المحتوى المخفي قبل تحويل PDF.

## الخلاصة
أنت الآن تعرف كيفية **إنشاء إشارات مرجعية متداخلة**، تكوين مستويات المخطط الخاصة بها، و**حفظ إشارات مرجعية PDF من Word** باستخدام Aspose.Words for Java. هذه التقنية تحسن بشكل كبير تنقل PDF، مما يجعل مستنداتك أكثر احترافية وسهولة في الاستخدام.

**الخطوات التالية**: جرّب هياكل إشارات مرجعية أعمق، دمج هذه المنطق في خطوط معالجة الدُفعات، أو دمجه مع Aspose.PDF لتعديل الإشارات بعد الإنشاء.

## الأسئلة المتكررة
**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
ج: أضف تبعية Maven أو Gradle المذكورة أعلاه، ثم حمّل ملف الترخيص عند تشغيل البرنامج.

**س: هل يمكنني استخدام الإشارات المرجعية دون تعيين مستويات المخطط؟**  
ج: نعم، لكن بدون مستويات المخطط سيظهر شريط التنقل في PDF جميع الإشارات في نفس المستوى الهرمي، مما قد يربك القارئ.

**س: هل هناك حد لعمق تداخل الإشارات المرجعية؟**  
ج: تقنيًا لا، لكن من منظور الاستخدام يُفضَّل الحفاظ على عمق معقول (3‑4 مستويات) حتى يتمكن المستخدمون من استعراض القائمة بسهولة.

**س: كيف يتعامل Aspose مع المستندات الكبيرة جدًا؟**  
ج: المكتبة تقوم ببث المحتوى وتوفر `optimizeResources()` لتقليل استهلاك الذاكرة؛ ومع ذلك، يُنصح بمراقبة مساحة الذاكرة في JVM للملفات التي تتجاوز مئات الصفحات.

**س: هل يمكن تعديل الإشارات المرجعية بعد إنشاء PDF؟**  
ج: نعم، يمكنك استخدام Aspose.PDF for Java لتعديل أو إضافة أو إزالة الإشارات المرجعية في PDF موجود.

---

**Last Updated:** 2025-12-10  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

**الموارد**
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}