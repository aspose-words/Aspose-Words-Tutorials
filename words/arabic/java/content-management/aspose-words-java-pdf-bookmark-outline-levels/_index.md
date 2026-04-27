---
date: '2026-04-27'
description: تعلم كيفية تعيين العلامات المرجعية وحفظ ملف PDF مع العلامات المرجعية
  باستخدام Aspose.Words للغة Java. حسّن قابلية القراءة والتنقل مع هذا الدليل الشامل.
keywords:
- how to set bookmarks
- save pdf with bookmarks
- create nested bookmarks
- generate pdf with bookmarks
- convert word pdf bookmarks
title: كيفية تعيين العلامات المرجعية في ملفات PDF باستخدام Aspose.Words Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين العلامات المرجعية في ملفات PDF باستخدام Aspose.Words Java

## المقدمة
إذا كنت تواجه صعوبة في إدارة **كيفية تعيين العلامات المرجعية** عند تحويل مستندات Word إلى ملفات PDF، فأنت في المكان المناسب. في هذا الدرس سنستعرض العملية بالكامل باستخدام Aspose.Words for Java، بدءًا من إنشاء علامات مرجعية متداخلة إلى ضبط مستويات المخطط لها بحيث يكون ملف PDF النهائي نظيفًا، احترافيًا، وسهل التنقل.

**ما ستتعلمه**
- إعداد Aspose.Words for Java في مشروعك  
- **إنشاء علامات مرجعية متداخلة** داخل مستند Word  
- **ضبط مستويات مخطط العلامات المرجعية** للحصول على مخطط PDF منظم  
- **حفظ PDF مع علامات مرجعية** تعكس التسلسل الهرمي الذي حددته  

### إجابات سريعة
- **ما هو الصنف الأساسي لإنشاء المستندات؟** `DocumentBuilder`  
- **ما هو الخيار الذي يتحكم في تسلسل العلامات المرجعية؟** `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()`  
- **هل يمكنني استخدام Maven أو Gradle؟** نعم، كلاهما مدعومان (انظر مقتطفات الشيفرة)  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية تعمل للتقييم؛ الترخيص الدائم مطلوب للإنتاج  
- **هل سيحتفظ PDF بالعلامات المرجعية المتداخلة؟** بالتأكيد، عندما يتم ضبط مستويات المخطط بشكل صحيح  

## ما هو “كيفية تعيين العلامات المرجعية” في ملف PDF؟
تعني تعيين العلامات المرجعية تعريف مدخلات قابلة للنقر في لوحة التنقل الخاصة بملف PDF والتي تقفز إلى أقسام محددة من المستند. عندما تكون العلامات المرجعية متداخلة ومُعينة بمستويات المخطط، تظهر كشجرة قابلة للطي، مما يجعل استكشاف المستندات الكبيرة أسهل بكثير.

## لماذا تستخدم Aspose.Words لمستويات مخطط العلامات المرجعية؟
يوفر لك Aspose.Words تحكمًا برمجيًا كاملاً في تحويل Word إلى PDF، بما في ذلك القدرة على **إنشاء PDF مع علامات مرجعية** تعكس بنية مستندك. هذا يلغي الحاجة إلى المعالجة اليدوية بعد التحويل ويضمن تجربة مستخدم متسقة عبر جميع ملفات PDF المُنشأة.

## المتطلبات المسبقة
- **المكتبات والاعتمادات**: Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **البيئة**: JDK 8 أو أحدث، بيئة تطوير مثل IntelliJ IDEA أو Eclipse.  
- **المعرفة**: أساسيات Java، إلمام بـ Maven أو Gradle.

## إعداد Aspose.Words
Add the required library to your build system.

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
Aspose.Words هو منتج تجاري، لكن يمكنك البدء بنسخة تجريبية مجانية.

1. **نسخة تجريبية مجانية**: قم بالتنزيل من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاختبار جميع الإمكانيات.  
2. **ترخيص مؤقت**: قدّم طلبًا للحصول على ترخيص مؤقت عبر [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/) إذا لزم الأمر.  
3. **الشراء**: للاستخدام المستمر، اشترِ ترخيصًا من [بوابة شراء Aspose](https://purchase.aspose.com/buy).

قم بتهيئة ملف الترخيص في الشيفرة الخاصة بك لفتح جميع الميزات.

## دليل التنفيذ
فيما يلي دليل خطوة بخطوة يغطي **إنشاء علامات مرجعية متداخلة**، ضبط مستويات المخطط لها، وأخيرًا **حفظ PDF مع علامات مرجعية**.

### إنشاء علامات مرجعية متداخلة
**نظرة عامة**: إنشاء مستند Word وإدراج علامات مرجعية تعكس تسلسلًا هرميًا.

#### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
هذا ينشئ مستندًا جديدًا جاهزًا لإدراج المحتوى.

#### الخطوة 2: إدراج علامات مرجعية متداخلة
ابدأ بعلامة مرجعية أساسية، ثم ضع علامة ثانية داخلها.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

```java
builder.endBookmark("Bookmark 1");
```

#### الخطوة 3: إضافة علامات مرجعية إضافية
يمكنك الاستمرار في إضافة علامات مرجعية مستقلة حسب الحاجة.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### ضبط مستويات مخطط العلامات المرجعية
**نظرة عامة**: تعيين مستويات المخطط بحيث تعكس لوحة علامات المرجعية في PDF التسلسل الهرمي المقصود.

#### الخطوة 1: إعداد PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
ستُستخدم هذه الخيارات عند حفظ المستند كملف PDF.

#### الخطوة 2: إضافة مستويات المخطط
ربط كل اسم علامة مرجعية بمستوى مخطط (1 = المستوى الأعلى، 2 = فرعي، إلخ).

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### الخطوة 3: حفظ المستند
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
يحتوي ملف PDF الناتج الآن على شجرة علامات مرجعية منظمة.

## المشكلات الشائعة والحلول
- **العلامات المرجعية المفقودة** – تحقق من أن كل `startBookmark` له `endBookmark` مطابق.  
- **التسلسل الهرمي غير الصحيح** – افحص أرقام مستويات المخطط؛ يجب أن يكون للفرع رقم أعلى من الأب.  
- **المستندات الكبيرة** – استدعِ `doc.removeUnusedResources()` قبل الحفظ لتقليل حجم الملف.

## التطبيقات العملية
1. **العقود القانونية** – القفز بسرعة إلى البنود والبنود الفرعية.  
2. **التقارير السنوية** – التنقل بين الأقسام والجداول والرسوم البيانية بسهولة.  
3. **مواد التعلم الإلكتروني** – توفير فهرس قابل للنقر للطلاب.

## اعتبارات الأداء
- إزالة العقد غير الضرورية قبل التحويل للحفاظ على خفة ملف PDF.  
- بالنسبة للملفات الكبيرة جدًا، فكر في تدفق المستند لتجنب استهلاك عالي للذاكرة.

## الخلاصة
أنت الآن تعرف **كيفية تعيين العلامات المرجعية**، وضبط مستويات المخطط لها، و**حفظ PDF مع علامات مرجعية** باستخدام Aspose.Words for Java. هذه التقنية تحسن بشكل كبير تنقل PDF وتمنح مستنداتك لمسة احترافية.

**الخطوات التالية**: جرّب إضافة أيقونات مخصصة للعلامات المرجعية أو دمج هذه العملية في خدمة معالجة دفعات.

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
ج: أضف تبعية Maven أو Gradle الموضحة أعلاه، ثم ضع ملف الترخيص في مجلد الموارد الخاص بالمشروع.

**س: هل يمكنني إنشاء علامات مرجعية بدون مستويات مخطط؟**  
ج: نعم، ولكن بدون مستويات المخطط ستظهر جميع العلامات المرجعية في لوحة التنقل في PDF على نفس المستوى، مما يجعل تصفح المستندات الكبيرة أصعب.

**س: هل هناك حد لعمق تداخل العلامات المرجعية؟**  
ج: تقنيًا لا، لكن احرص على أن يكون التسلسل الهرمي مقروءًا للمستخدمين النهائيين—عادةً ما تكون 3‑4 مستويات كافية.

**س: كيف يتعامل Aspose مع ملفات Word الكبيرة جدًا؟**  
ج: يقوم بتدفق المحتوى ويقدم طرقًا مثل `Document.optimizeResources()` للحفاظ على انخفاض استهلاك الذاكرة.

**س: هل يمكنني تعديل العلامات المرجعية بعد توليد PDF؟**  
ج: نعم، يمكنك استخدام Aspose.PDF for Java لتعديل عناوين العلامات المرجعية أو وجهاتها أو التسلسل الهرمي بعد التحويل.

---

**Last Updated:** 2026-04-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

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