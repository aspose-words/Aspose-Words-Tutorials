---
date: '2026-03-31'
description: تعلم كيفية إنشاء إشارات مرجعية متداخلة في Java وتوليد PDF مع إشارات مرجعية
  باستخدام Aspose.Words. دليل خطوة بخطوة لتصدير Word إلى PDF في Java.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: إنشاء إشارات مرجعية متداخلة في جافا باستخدام Aspose.Words لمستويات PDF
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء إشارات مرجعية متداخلة Java باستخدام Aspose.Words مستويات PDF

## مقدمة
إذا كنت بحاجة إلى **إنشاء إشارات مرجعية متداخلة Java**‑نمط أثناء تحويل مستندات Word إلى PDFs، فأنت في المكان الصحيح. في هذا الدرس سنستعرض كيفية استخدام Aspose.Words for Java لإنشاء PDF يحتوي على إشارات مرجعية منظمة بشكل أنيق بمستويات المخطط. في النهاية ستحصل على PDF بمظهر احترافي يمكن للقراء القفز إلى أي قسم على الفور.

**ما ستتعلمه**
- كيفية إعداد Aspose.Words for Java  
- كيفية إنشاء إشارات مرجعية متداخلة في مستند Word  
- كيفية تكوين مستويات مخطط الإشارة المرجعية لتسلسل هرمي واضح  
- كيفية تصدير المستند كملف PDF مع إشارات مرجعية منظمة  

### إجابات سريعة
- **ما هي الفئة الأساسية لإنشاء المستندات؟** `DocumentBuilder`  
- **ما هي الطريقة التي تضيف مستوى مخطط؟** `outlineLevels.add(bookmarkName, level)`  
- **هل يمكنني استخدام Maven أو Gradle؟** نعم، كلاهما مدعومان (انظر مقتطفات الشيفرة)  
- **هل أحتاج إلى ترخيص لمستويات مخطط PDF؟** الترخيص يفتح جميع الوظائف؛ النسخة التجريبية المجانية تعمل للتقييم  
- **هل هذه الطريقة مناسبة للتقارير الكبيرة؟** نعم، ولكن ضع في اعتبارك نصائح تحسين الذاكرة في قسم الأداء  

## ما هو “إنشاء إشارات مرجعية متداخلة Java”؟
إنشاء إشارات مرجعية متداخلة يعني وضع إشارة مرجعية داخل أخرى، مكونًا تسلسلًا هرميًا من الأب إلى الابن. عندما يُحفظ المستند كملف PDF، تتحول هذه التسلسلات إلى عناصر قابلة للطي في لوحة الإشارات المرجعية في PDF، مما يجعل التنقل بديهيًا للقراء.

## لماذا إنشاء PDF مع إشارات مرجعية؟
إدراج إشارات مرجعية في ملفات PDF يحسن تجربة المستخدم، خاصةً في العقود القانونية، التقارير الطويلة، أو الكتب الإلكترونية. يمكن للقراء القفز فورًا إلى الفصول أو الأقسام أو البنود المحددة دون الحاجة إلى التمرير عبر الصفحات.

## المتطلبات المسبقة
- **المكتبات والاعتمادات**: Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **البيئة**: JDK 8 أو أعلى، IDE مثل IntelliJ IDEA أو Eclipse.  
- **المهارات**: Java أساسي، إلمام بـ Maven أو Gradle.

### إعداد Aspose.Words
قم بتضمين المكتبة في مشروعك باستخدام Maven أو Gradle.

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

#### الحصول على الترخيص
Aspose.Words تجاري، لكن يمكنك البدء بنسخة تجريبية مجانية.

1. **نسخة تجريبية مجانية**: قم بالتنزيل من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاختبار جميع الإمكانيات.  
2. **ترخيص مؤقت**: قدّم طلبًا للحصول على ترخيص مؤقت عبر [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/) إذا لزم الأمر.  
3. **شراء**: للاستخدام المستمر، اشترِ ترخيصًا من [بوابة شراء Aspose](https://purchase.aspose.com/buy).

قم بتهيئة الترخيص في الشيفرة الخاصة بك لفتح جميع الميزات.

## دليل التنفيذ
سنقسم الحل إلى خطوات واضحة مرقمة.

### الخطوة 1: إنشاء مستند وباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
هذا ينشئ مستند Word فارغًا وكائن باني ستستخدمه لإدراج المحتوى والإشارات المرجعية.

### الخطوة 2: إدراج إشارات مرجعية متداخلة
#### الإشارة المرجعية الأساسية
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### إشارة مرجعية متداخلة داخل الأساسية
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### إغلاق الإشارة المرجعية الخارجية
```java
builder.endBookmark("Bookmark 1");
```

#### إشارة مرجعية مستقلة إضافية
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### الخطوة 3: تكوين مستويات مخطط الإشارة المرجعية
#### إعداد خيارات حفظ PDF
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### تعيين مستويات التسلسل الهرمي
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### حفظ كملف PDF مع المخطط المحدد
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### المشكلات الشائعة والحلول
- **الإشارات المرجعية المفقودة** – يجب أن يكون لكل `startBookmark` `endBookmark` مطابق.  
- **المستويات غير الصحيحة** – تحقق مرة أخرى من أرقام المستويات؛ فهي تحدد علاقة الأب‑ابن في PDF.  
- **المستندات الكبيرة** – استخدم `Document.optimizeResources()` قبل الحفظ لتقليل استهلاك الذاكرة.  

## التطبيقات العملية
1. **العقود القانونية** – القفز بسرعة إلى البنود والبنود الفرعية.  
2. **التقارير المالية** – التنقل بين الأقسام والجداول والرسوم البيانية.  
3. **المواد التعليمية** – توفير جدول محتويات قابل للنقر للكتب الإلكترونية.  

## اعتبارات الأداء
- إزالة الأنماط أو الأقسام غير المستخدمة قبل الحفظ.  
- بالنسبة للملفات الكبيرة جدًا، فكر في تدفق مخرجات PDF لتجنب استهلاك عالي للذاكرة.  

## الخلاصة
أنت الآن تعرف كيفية **إنشاء إشارات مرجعية متداخلة Java** وتكوين مستويات المخطط الخاصة بها باستخدام Aspose.Words. هذه التقنية تحول PDF عادي إلى مستند سهل الاستخدام وقابل للتنقل — مثالي للتقارير المهنية والعقود والكتب الإلكترونية.

**الخطوات التالية**: حاول إضافة أيقونات مخصصة للإشارات المرجعية، أو دمج هذه العملية في خدمة معالجة دفعات تقوم بتحويل ملفات Word متعددة في آن واحد.

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
ج: أضف تبعية Maven أو Gradle الموضحة أعلاه، ثم ضع ملف الترخيص في موارد المشروع.

**س: هل يمكنني إنشاء PDF بدون مستويات مخطط؟**  
ج: نعم، لكن PDF سيحتوي على إشارات مرجعية مسطحة، مما يجعل التنقل أصعب.

**س: هل هناك حد لعمق تداخل الإشارات المرجعية؟**  
ج: تقنيًا لا، لكن حافظ على التسلسل الهرمي معقولًا لسهولة القراءة.

**س: هل يتعامل Aspose.Words مع المستندات الكبيرة بكفاءة؟**  
ج: يدير الذاكرة بشكل جيد، خاصةً عند استدعاء `optimizeResources()` قبل الحفظ.

**س: هل يمكنني تعديل الإشارات المرجعية بعد إنشاء PDF؟**  
ج: نعم، يمكنك استخدام Aspose.PDF for Java لتعديل عناوين الإشارات المرجعية أو التسلسل الهرمي بعد الإنشاء.

## الموارد
- [توثيق Aspose.Words](https://reference.aspose.com/words/java/)
- [تحميل أحدث الإصدارات](https://releases.aspose.com/words/java/)
- [شراء ترخيص](https://purchase.aspose.com/buy)
- [نسخة تجريبية مجانية](https://releases.aspose.com/words/java/)
- [طلب ترخيص مؤقت](https://purchase.aspose.com/temporary-license/)
- [منتدى دعم Aspose](https://forum.aspose.com/c/words/10)

---

**آخر تحديث:** 2026-03-31  
**تم الاختبار مع:** Aspose.Words 25.3 for Java  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}