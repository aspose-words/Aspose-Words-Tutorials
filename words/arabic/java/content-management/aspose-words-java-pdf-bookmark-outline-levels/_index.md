---
date: '2026-04-11'
description: تعلم كيفية حفظ PDF مع العلامات المرجعية ومستويات المخطط في جافا باستخدام
  Aspose.Words. يتضمن نصائح التحويل، عينات الشيفرة، وحلول المشكلات.
keywords:
- save pdf with bookmarks
- convert word pdf java
- aspose words java pdf
title: حفظ PDF مع العلامات المرجعية باستخدام Aspose.Words Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# حفظ PDF مع العلامات المرجعية باستخدام Aspose.Words Java

## مقدمة
إذا كنت بحاجة إلى **حفظ PDF مع العلامات المرجعية** التي تعكس هيكلًا واضحًا، فأنت في المكان المناسب. في هذا البرنامج التعليمي سنستعرض عملية تحويل مستند Word إلى PDF مع تكوين مستويات مخطط العلامات المرجعية، بحيث يكون PDF الناتج سهل التنقل للقراء والمراجعين.  

**ما ستتعلمه**
- كيفية إعداد Aspose.Words لـ Java  
- كيفية إنشاء علامات مرجعية متداخلة في مستند Word  
- كيفية تعيين مستويات المخطط بحيث تظهر علامات PDF المرجعية في شجرة منطقية  
- كيفية **حفظ PDF مع العلامات المرجعية** باستخدام أحدث API لـ Aspose.Words  

### إجابات سريعة
- **هل يمكنني إضافة علامات مرجعية عند تحويل Word إلى PDF؟** نعم، يتيح لك Aspose.Words تعريفها قبل الحفظ.  
- **هل أحتاج إلى ترخيص لاستخدام الميزة؟** النسخة التجريبية المجانية تكفي للتقييم؛ الترخيص يفتح جميع الوظائف.  
- **ما نسخة Java المطلوبة؟** Java 8 أو أعلى.  
- **هل تكوين مستوى المخطط اختياري؟** هو اختياري لكن يُنصح به بشدة لتحسين التنقل.  
- **هل سيحافظ PDF على هيكل العلامات المرجعية؟** بالتأكيد – المستويات التي تحددها تصبح شجرة العلامات المرجعية في PDF.  

### المتطلبات المسبقة
قبل أن نبدأ، تأكد من أن لديك:

- **المكتبات والاعتمادات**: Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **البيئة**: JDK 8+ وIDE مثل IntelliJ IDEA أو Eclipse.  
- **المعرفة الأساسية**: الإلمام بـ Java، Maven أو Gradle، ومفهوم العلامات المرجعية في Word.  

## كيفية حفظ PDF مع العلامات المرجعية ومستويات المخطط

### إعداد Aspose.Words
أضف مكتبة Aspose.Words إلى مشروعك باستخدام Maven أو Gradle.

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

#### الحصول على الترخيص
Aspose.Words هو منتج تجاري، ولكن يمكنك البدء بنسخة تجريبية مجانية.

1. **نسخة تجريبية مجانية** – قم بتنزيلها من [Aspose's release page](https://releases.aspose.com/words/java/) لاختبار جميع القدرات.  
2. **ترخيص مؤقت** – قدّم طلبًا عبر [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) للتقييم قصير المدة.  
3. **شراء** – احصل على ترخيص دائم من [Aspose purchasing portal](https://purchase.aspose.com/buy).  

بعد حصولك على ملف `.lic`، قم بتحميله عند بدء تشغيل التطبيق لفتح جميع الميزات.

### إنشاء علامات مرجعية متداخلة (الخطوة 1)
أولاً، أنشئ مستند Word وأدرج علامات مرجعية تعكس الهيكل الذي تريده.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

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

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### تكوين مستويات مخطط العلامات المرجعية (الخطوة 2)
الآن أخبر Aspose.Words كيف يجب أن تظهر تلك العلامات المرجعية في لوحة العلامات المرجعية للـ PDF.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

عند فتح الـ PDF المُولد، ستلاحظ شجرة علامات مرجعية ذات ثلاثة مستويات تعكس الهيكل الذي حددته في مستند Word.

## لماذا تستخدم Aspose.Words لتحويل Word إلى PDF في Java؟
- **دقة عالية**: يتم الحفاظ على التخطيط، الخطوط، والعناصر المعقدة.  
- **تحكم برمجي**: يمكنك إضافة أو تعديل العلامات المرجعية، مستويات المخطط، والعديد من ميزات PDF مباشرةً من Java.  
- **الأداء**: يتعامل مع المستندات الكبيرة بكفاءة، خاصةً عند اتباع نصائح الأداء أدناه.

## التطبيقات العملية
1. **العقود القانونية** – التنقل السريع بين البنود والفقرة الفرعية.  
2. **التقارير السنوية** – توفير جدول محتويات قابل للنقر للقراء.  
3. **وحدات التعلم الإلكتروني** – تنظيم الفصول، الأقسام، والاختبارات في PDF واحد.

## اعتبارات الأداء
- إزالة الأنماط غير المستخدمة أو الأقسام المخفية قبل الحفظ للحفاظ على خفة الـ PDF.  
- استخدم `doc.optimizeResources()` للمستندات الكبيرة جدًا لتقليل استهلاك الذاكرة.

## المشكلات الشائعة والحلول
- **العلامات المرجعية المفقودة** – تحقق من أن كل `startBookmark` لديه `endBookmark` مطابق.  
- **الهيكل غير الصحيح** – تأكد من أن أرقام مستويات المخطط تعكس علاقة الأب‑ابن (الرقم الأقل = المستوى الأعلى).  
- **الترخيص غير مفعّل** – حمّل ملف الترخيص قبل أي استدعاء لواجهة Aspose.Words API؛ وإلا ستحصل على علامة مائية تجريبية.

## الأسئلة الشائعة

**س: كيف أقوم بتثبيت Aspose.Words لـ Java؟**  
ج: أضف تبعية Maven أو Gradle الموضحة أعلاه، ثم حمّل ملف الترخيص أثناء التشغيل.

**س: هل يمكنني إنشاء علامات مرجعية دون تحديد مستويات المخطط؟**  
ج: نعم، لكن الـ PDF سيظهر قائمة مسطحة من العلامات المرجعية، مما يصعب التنقل.

**س: هل هناك حد لعمق تداخل العلامات المرجعية؟**  
ج: من الناحية التقنية لا، لكن حافظ على قابلية القراءة للهيكل—عادةً ثلاثة إلى أربعة مستويات هي المثالية.

**س: هل يتعامل Aspose.Words بفعالية مع ملفات Word الكبيرة؟**  
ج: يقوم ببث المحتوى وتوفير طرق تحسين؛ ومع ذلك، قد تحتاج إلى تقسيم المستندات الضخمة جدًا.

**س: هل يمكن تعديل العلامات المرجعية بعد حفظ الـ PDF؟**  
ج: نعم، يمكنك استخدام Aspose.PDF لـ Java لتعديل العلامات المرجعية بعد التحويل.

## الموارد
- [توثيق Aspose.Words](https://reference.aspose.com/words/java/)  
- [تحميل أحدث الإصدارات](https://releases.aspose.com/words/java/)  
- [شراء ترخيص](https://purchase.aspose.com/buy)  
- [نسخة تجريبية مجانية](https://releases.aspose.com/words/java/)  
- [طلب ترخيص مؤقت](https://purchase.aspose.com/temporary-license/)  
- [منتدى دعم Aspose](https://forum.aspose.com/c/words/10)

---

**آخر تحديث:** 2026-04-11  
**تم الاختبار مع:** Aspose.Words 25.3 for Java  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}