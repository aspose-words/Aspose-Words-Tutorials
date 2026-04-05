---
date: '2026-04-05'
description: تعلم كيفية حفظ ملفات PDF مع العلامات المرجعية باستخدام Aspose.Words للغة
  Java. أنشئ علامات مرجعية متداخلة، حدّد مستويات المخطط، وأنشئ ملفات PDF احترافية.
keywords:
- save pdf with bookmarks
- Aspose.Words Java bookmarks
- PDF bookmark outline levels
title: حفظ PDF مع العلامات المرجعية باستخدام Aspose.Words للـ Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# حفظ PDF مع العلامات المرجعية باستخدام Aspose.Words for Java

## مقدمة
هل تواجه صعوبة في إدارة العلامات المرجعية عند تحويل مستندات Word إلى PDFs؟ في هذا البرنامج التعليمي ستتعلم كيفية **حفظ PDF مع العلامات المرجعية** باستخدام Aspose.Words for Java، وتنظيمها بفعالية لتوفير تنقل مهني.

**ما ستتعلمه**
- إعداد Aspose.Words for Java
- إنشاء علامات مرجعية متداخلة في مستند Word
- تكوين مستويات مخطط العلامات المرجعية لتنقل PDF أوضح
- حفظ المستند كملف PDF **يحفظ PDF مع العلامات المرجعية** بشكل صحيح

### المتطلبات المسبقة
قبل البدء، تأكد من أنك تمتلك:
- **المكتبات والاعتمادات**: Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **إعداد البيئة**: JDK مثبت على جهازك وIDE مثل IntelliJ IDEA أو Eclipse.  
- **المتطلبات المعرفية**: مهارات برمجة Java الأساسية ومعرفة بـ Maven أو Gradle.

## إجابات سريعة
- **ماذا يعني “حفظ PDF مع العلامات المرجعية”?**  
  يعني إنشاء PDF حيث يعكس جزء العلامات المرجعية الهيكل المنطقي للمستند.  
- **ما المنتج Aspose المطلوب؟**  
  Aspose.Words for Java (ميزات تحويل PDF مدمجة).  
- **هل أحتاج إلى ترخيص للتطوير؟**  
  نسخة تجريبية مجانية تكفي للاختبار؛ ترخيص دائم مطلوب للإنتاج.  
- **هل يمكنني تعيين مستويات هرمية للعلامات المرجعية؟**  
  نعم – استخدم `BookmarksOutlineLevelCollection` لتحديد علاقات الأب‑ابن.  
- **هل هذا النهج متوافق مع المستندات الكبيرة؟**  
  بالتأكيد؛ Aspose.Words يبث البيانات بكفاءة، لكن يُنصح بتحسين الموارد للملفات الضخمة جدًا.

## ما هو “حفظ PDF مع العلامات المرجعية”؟
عند تحويل مستند Word إلى PDF، يمكن إنشاء علامات مرجعية تعكس العناوين، الأقسام، أو أي علامات مخصصة. تظهر هذه العلامات في جزء التنقل الخاص بـ PDF، مما يسمح للقراء بالقفز مباشرة إلى أجزاء محددة من المستند.

## لماذا نستخدم مستويات مخطط العلامات المرجعية؟
تعيين مستويات المخطط يخلق هيكلًا واضحًا (فصول، فصول فرعية، إلخ). هذا يحسن تجربة المستخدم، خاصة في العقود القانونية، التقارير التقنية، أو الكتب الإلكترونية حيث يكون التنقل السريع ضروريًا.

## إعداد Aspose.Words
أضف المكتبة إلى مشروعك باستخدام Maven أو Gradle.

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
Aspose.Words تجاري، لكن يمكنك البدء بنسخة تجريبية مجانية.

1. **نسخة تجريبية مجانية** – قم بالتنزيل من [Aspose's release page](https://releases.aspose.com/words/java/) لاختبار جميع الإمكانات.  
2. **ترخيص مؤقت** – قدّم طلبًا على [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) إذا كنت تحتاج إلى مفتاح قصير الأمد.  
3. **شراء** – احصل على ترخيص دائم من [Aspose’s purchasing portal](https://purchase.aspose.com/buy).

قم بتهيئة الترخيص في الكود الخاص بك (غير موضح هنا) قبل حفظ ملفات PDF لفتح جميع الميزات.

## كيفية إنشاء علامات مرجعية متداخلة
### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
هذا ينشئ مستند Word جديد يمكنك ملؤه بالمحتوى والعلامات المرجعية.

### الخطوة 2: إدراج العلامة المرجعية الأساسية
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### الخطوة 3: إضافة علامة مرجعية متداخلة
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### الخطوة 4: إغلاق العلامة المرجعية الأساسية
```java
builder.endBookmark("Bookmark 1");
```

### الخطوة 5: إضافة علامات مرجعية مستقلة إضافية (اختياري)
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## كيفية تكوين مستويات مخطط العلامات المرجعية
### الخطوة 1: إعداد خيارات حفظ PDF
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### الخطوة 2: تعيين المستويات الهرمية
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
القيمة الرقمية تحدد العمق في شجرة العلامات المرجعية لملف PDF.

### الخطوة 3: حفظ المستند كملف PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
PDF الناتج يحتوي على جزء علامات مرجعية منظم بالكامل، مما يلبي متطلب **حفظ PDF مع العلامات المرجعية**.

## نصائح استكشاف الأخطاء وإصلاحها
- **العلامات المرجعية المفقودة** – تحقق من أن كل `startBookmark` له `endBookmark` مطابق.  
- **الهيكل غير الصحيح** – راجع أرقام المستويات التي تعينها؛ الرقم الأقل يعني مستوى أعلى في الشجرة.  
- **ملفات كبيرة** – استدعِ `doc.optimizeResources()` قبل الحفظ لتقليل استهلاك الذاكرة.

## تطبيقات عملية
1. **العقود القانونية** – القفز بسرعة إلى البنود، الملاحق، والملحقات.  
2. **التقارير التقنية** – التنقل بين الأقسام، الفروع، وجداول البيانات.  
3. **مواد التعلم الإلكتروني** – توفير جدول محتويات قابل للنقر داخل PDF للقراء.

## اعتبارات الأداء
- إزالة الأنماط أو الصور غير المستخدمة قبل التحويل للحفاظ على خفة PDF.  
- عند معالجة مستندات ضخمة، فكر في بث الإخراج باستخدام `PdfSaveOptions.setSaveFormat(SaveFormat.Pdf)` ومراقبة استهلاك الذاكرة.

## الخلاصة
أنت الآن تعرف كيفية **حفظ PDF مع العلامات المرجعية** والتحكم في مستويات المخطط الخاصة بها باستخدام Aspose.Words for Java. تجعل هذه التقنية ملفات PDF الخاصة بك أسهل بكثير في الاستكشاف، سواء كانت مذكرات قانونية، كتيبات تقنية، أو أدلة إرشادية.

### الخطوات التالية
- تجربة أسماء علامات مرجعية ديناميكية بناءً على عناوين المستند.  
- دمج هذا النهج مع Aspose.PDF لتعديل العلامات بعد التحويل إذا لزم الأمر.  
- استكشاف ميزات PDF أخرى مثل الروابط التشعبية، التعليقات التوضيحية، والأمان.

## الأسئلة المتكررة
**س: كيف أُثبت Aspose.Words for Java؟**  
ج: أضف تبعية Maven أو Gradle الموضحة أعلاه، ثم ضع ملف الترخيص في مجلد الموارد الخاص بالمشروع.

**س: هل يمكنني إنشاء علامات مرجعية دون تعيين مستويات المخطط؟**  
ج: نعم، لكن بدون مستويات المخطط سيظهر جزء العلامات مسطحًا، مما يجعل التنقل العميق أصعب.

**س: هل هناك حد لعدد مستويات العلامات المرجعية التي يمكنني إنشاؤها؟**  
ج: تقنيًا لا، لكن من أجل القابلية للقراءة احفظ الهيكل بعمق معقول (عادة 3‑5 مستويات).

**س: كيف يتعامل Aspose مع ملفات Word الكبيرة جدًا؟**  
ج: يبث المحتوى ويقدم `optimizeResources()` للحفاظ على انخفاض استهلاك الذاكرة أثناء التحويل.

**س: هل يمكنني تعديل العلامات المرجعية بعد حفظ PDF؟**  
ج: نعم – استخدم Aspose.PDF for Java لتعديل أو إضافة علامات مرجعية في PDF موجود.

## الموارد
- [توثيق Aspose.Words](https://reference.aspose.com/words/java/)
- [تحميل أحدث الإصدارات](https://releases.aspose.com/words/java/)
- [شراء ترخيص](https://purchase.aspose.com/buy)
- [نسخة تجريبية مجانية](https://releases.aspose.com/words/java/)
- [تطبيق ترخيص مؤقت](https://purchase.aspose.com/temporary-license/)
- [منتدى دعم Aspose](https://forum.aspose.com/c/words/10)

---

**آخر تحديث:** 2026-04-05  
**تم الاختبار مع:** Aspose.Words 25.3 for Java  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}