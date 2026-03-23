---
date: '2026-03-23'
description: تعلم كيفية إضافة العلامات المرجعية وتكوين مستويات المخطط عند تحويل مستندات
  Word إلى ملفات PDF باستخدام Aspose.Words for Java. يغطي هذا الدليل تحويل علامات
  PDF في Word ويحسن التنقل.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: كيفية إضافة العلامات المرجعية في ملفات PDF باستخدام Aspose.Words Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة العلامات المرجعية في ملفات PDF باستخدام Aspose.Words Java

## المقدمة
إذا كنت قد واجهت صعوبة في **add bookmarks** التي تجعل ملف PDF سهل التنقل، فأنت في المكان الصحيح. في هذا البرنامج التعليمي سنستعرض **how to add bookmarks** وتعيين مستويات المخطط عند تحويل مستندات Word إلى PDF باستخدام Aspose.Words for Java. في النهاية ستفهم سير العمل الكامل — من إنشاء علامات مرجعية متداخلة في ملف Word إلى تصدير PDF نظيف وقابل للبحث بهكلية علامات مرجعية منطقية.

**ما ستتعلمه**
- إعداد Aspose.Words for Java في مشروعك  
- إنشاء علامات مرجعية متداخلة داخل مستند Word  
- تكوين مستويات مخطط العلامة المرجعية لتجربة تنقل PDF مصقولة  
- حفظ المستند كملف PDF مع الحفاظ على بنية العلامات المرجعية  

### إجابات سريعة
- **ما الفائدة الأساسية من إضافة العلامات المرجعية؟** تتيح للقارئ القفز مباشرة إلى الأقسام، مما يحسن قابلية الاستخدام.  
- **أي مكتبة تتعامل مع علامات PDF في Java؟** Aspose.Words for Java (مع Aspose.PDF الاختياري للمعالجة اللاحقة).  
- **هل أحتاج إلى ترخيص لهذه الميزة؟** الإصدار التجريبي يعمل للتطوير؛ الترخيص التجاري مطلوب للإنتاج.  
- **هل يمكنني التحكم في تسلسل العلامات المرجعية؟** نعم، عن طريق تعيين مستويات المخطط عبر `PdfSaveOptions`.  
- **هل هذا النهج مناسب للمستندات الكبيرة؟** بالطبع — Aspose.Words يبث المحتوى بكفاءة.

## ما هو “كيفية إضافة العلامات المرجعية” في سياق تحويل PDF؟
إضافة العلامات المرجعية تعني إدراج مرساة مسماة في مستند Word يتم نقلها إلى PDF. عند فتح PDF، تظهر هذه العلامات في لوحة التنقل، مما يسمح للمستخدمين بتحديد الفصول أو الأقسام أو أي نقاط مخصصة على الفور.

## لماذا نستخدم Aspose.Words for Java لتحويل علامات Word → PDF؟
يحافظ Aspose.Words على هيكل العلامات المرجعية الدقيق الذي تحدده في Word، على عكس العديد من المحولات المجانية التي تُسطّحها أو تُزيلها. كما يتيح لك تعيين **outline levels**، مما يمنحك تحكمًا دقيقًا في طريقة عرض جدول المحتويات في PDF.

## المتطلبات المسبقة
- **المكتبات**: Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **بيئة التطوير**: JDK 8 أو أحدث، IDE مثل IntelliJ IDEA أو Eclipse.  
- **أداة البناء**: Maven أو Gradle (حسب تفضيلك).  
- **معرفة أساسية بـ Java** وإلمام بـ Maven/Gradle.

### إعداد Aspose.Words
أضف المكتبة إلى مشروعك باستخدام أحد المقاطع أدناه.

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
Aspose.Words تجاري، لكن يمكنك البدء بإصدار تجريبي مجاني:

1. **Free Trial** – حمّل من [Aspose's release page](https://releases.aspose.com/words/java/) لاختبار جميع القدرات.  
2. **Temporary License** – قدّم طلبًا عبر [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) للمشاريع قصيرة الأمد.  
3. **Purchase** – احصل على ترخيص دائم من [Aspose’s purchasing portal](https://purchase.aspose.com/buy).

بعد الحصول على ملف `.lic`، حمّله عند بدء تشغيل التطبيق لتفعيل جميع الميزات.

## دليل خطوة بخطوة

### إنشاء علامات مرجعية متداخلة
**نظرة عامة:** سنبني مستند Word بسيط يحتوي على ثلاث علامات مرجعية، حيث تكون إحدى العلامات داخل أخرى.

#### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
هذا ينشئ مستند Word فارغًا وكائن باني يتيح لنا إدراج النص والعلامات المرجعية.

#### الخطوة 2: إدراج العلامة المرجعية الأولى (الأصلية)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### الخطوة 3: وضع علامة مرجعية ثانية داخل الأولى
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### الخطوة 4: إغلاق العلامة المرجعية الأصلية
```java
builder.endBookmark("Bookmark 1");
```

#### الخطوة 5: إضافة علامة مرجعية ثالثة مستقلة
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

في هذه المرحلة يحتوي مستند Word على هيكل واضح يمكننا لاحقًا ترجمته إلى مستويات مخطط PDF.

### تكوين مستويات مخطط العلامة المرجعية
**نظرة عامة:** مستويات المخطط تخبر عارض PDF بعمق كل علامة في لوحة التنقل.

#### الخطوة 1: إعداد `PdfSaveOptions`
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### الخطوة 2: تعيين مستويات لكل علامة مرجعية
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
المستوى 1 يظهر في المستوى الأعلى، المستوى 2 كطفل، وهكذا.

#### الخطوة 3: حفظ المستند كملف PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
سيعرض PDF الناتج لوحة علامات مرجعية منظمة تعكس الهيكل الذي حددناه.

## المشكلات الشائعة والحلول
| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| اختفاء العلامات المرجعية في PDF | عدم تكوين `PdfSaveOptions` | تأكد من إضافة `outlineLevels` قبل الحفظ. |
| ظهور العلامة المرجعية المتداخلة في المستوى الأعلى | رقم المستوى غير صحيح | تحقق من أن العلامات الفرعية تحصل على مستوى رقمي أعلى. |
| فقدان استدعاء `endBookmark` | عدم توازن استدعاءات البداية/النهاية | راجع كل `startBookmark` وتأكد من وجود `endBookmark` مطابق. |

## التطبيقات العملية
- **العقود القانونية** – القفز سريعًا إلى البنود والفرعيات.  
- **التقارير التقنية** – التنقل بين أقسام كبيرة مثل المنهجية، النتائج، والملاحق.  
- **ملفات PDF للتعليم الإلكتروني** – توفير فهرس قابل للنقر لكل فصل.

## نصائح الأداء
- احذف الأقسام غير المستخدمة قبل الحفظ لتقليل وزن PDF.  
- استخدم البث (`doc.save(OutputStream)`) للملفات الكبيرة جدًا لتقليل استهلاك الذاكرة.

## الخلاصة
الآن تعرف **how to add bookmarks** وتعيين مستويات المخطط عند تحويل مستندات Word إلى PDF باستخدام Aspose.Words for Java. هذه التقنية تحسّن بشكل كبير تنقل PDF، مما يجعل مستنداتك أكثر احترافية وسهولة في الاستخدام.

**الخطوات التالية:** جرّب إضافة أيقونات مخصصة للعلامات عبر كائنات `PdfBookmark`، أو دمج سير العمل هذا في خدمة معالجة دفعات تقوم بتحويل ملفات Word متعددة تلقائيًا.

## قسم الأسئلة المتكررة
1. **كيف أقوم بتثبيت Aspose.Words for Java؟**  
   أضفه كاعتماد عبر Maven أو Gradle، ثم قم بإعداد ملف الترخيص.  
2. **هل يمكنني استخدام العلامات المرجعية بدون مستويات المخطط؟**  
   نعم، لكن مستويات المخطط تعطي هيكلًا أوضح في عارض PDF.  
3. **ما هي حدود التداخل للعلامات المرجعية؟**  
   لا يوجد حد صارم، لكن احرص على أن يكون الهيكل قابلًا للقراءة للمستخدم النهائي.  
4. **كيف يتعامل Aspose مع المستندات الكبيرة؟**  
   يبث المحتوى بكفاءة؛ ومع ذلك، فكر في تحسين الموارد للملفات الضخمة جدًا.  
5. **هل يمكن تعديل العلامات المرجعية بعد حفظ PDF؟**  
   نعم — استخدم Aspose.PDF for Java لتعديل العلامات بعد التحويل.

## الأسئلة المتكررة

**س: هل تعمل هذه الطريقة مع أحدث إصدار من Aspose.Words؟**  
ج: بالتأكيد. API مستويات مخطط العلامة المرجعية ثابت منذ الإصدار 20.  

**س: هل يلزم وجود مكتبة Aspose.PDF منفصلة لعرض العلامات؟**  
ج: لا. العلامات مدمجة في PDF وتظهر في أي عارض PDF قياسي.  

**س: هل يمكنني تغيير عناوين العلامات برمجيًا بعد إنشاء PDF؟**  
ج: نعم، عن طريق تحميل PDF باستخدام Aspose.PDF وتحديث مجموعة `PdfBookmark`.  

**س: هل سيعمل هذا النهج على أنظمة غير Windows؟**  
ج: Aspose.Words for Java مستقل عن المنصة؛ يعمل على أي نظام تشغيل يدعم JDK مدعومًا.  

**س: كيف يمكنني اختبار هيكل العلامات دون فتح PDF؟**  
ج: استخدم `PdfBookmarkCollection` من Aspose.PDF لاستعراض والتحقق من المستويات برمجيًا.

---

**Last Updated:** 2026-03-23  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

## الموارد
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