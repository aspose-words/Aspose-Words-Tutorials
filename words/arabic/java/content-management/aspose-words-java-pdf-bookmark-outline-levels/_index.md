---
date: '2026-03-17'
description: تعلم كيفية إضافة العلامات المرجعية، وتعيين مستويات المخطط، وحفظ ملف PDF
  مع العلامات المرجعية باستخدام Aspose.Words للغة Java.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: كيفية إضافة العلامات المرجعية والمستويات في ملفات PDF – Aspose.Words Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

 => "أسئلة وإجابات إضافية"

"Resources" => "الموارد"

"Last Updated:" etc.

Make sure to keep dates and URLs unchanged.

Now produce final content with same shortcodes and placeholders.

Let's craft.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إتقان مستويات مخطط العلامات المرجعية في ملفات PDF باستخدام Aspose.Words Java

## المقدمة
في هذا الدليل، ستتعلم **كيفية إضافة العلامات المرجعية** وتعيين مستويات المخطط عند تحويل مستندات Word إلى PDF باستخدام Aspose.Words for Java. هل تواجه صعوبة في إدارة العلامات المرجعية أثناء التحويل؟ يشرح هذا البرنامج التعليمي كيفية إنشاء علامات مرجعية متداخلة، وتكوين هرميةها، وحفظ ملف PDF سهل التنقل.

**ما ستتعلمه**
- إعداد واستخدام Aspose.Words for Java
- إنشاء علامات مرجعية متداخلة في مستندات Word
- تكوين مستويات مخطط العلامات المرجعية لتحسين التنظيم
- حفظ المستندات كملفات PDF مع علامات مرجعية منظمة

### المتطلبات المسبقة
قبل البدء، تأكد من وجود:
- **المكتبات والاعتمادات**: Aspose.Words for Java (الإصدار 25.3 أو أحدث).
- **إعداد البيئة**: تثبيت JDK على جهازك بالإضافة إلى IDE متوافق مثل IntelliJ IDEA أو Eclipse.
- **المعرفة المسبقة**: فهم أساسي لبرمجة Java وإلمام بأنظمة بناء Maven أو Gradle.

## إجابات سريعة
- **ما هي الطريقة الأساسية لإضافة العلامات المرجعية؟** استخدم طريقتي `DocumentBuilder.startBookmark()` و `endBookmark()`.  
- **هل يمكنني تعيين هرمية للعلامات المرجعية في PDF؟** نعم—قم بتكوين `BookmarksOutlineLevelCollection` عبر `PdfSaveOptions`.  
- **هل أحتاج إلى ترخيص لإنشاء PDF مع علامات مرجعية؟** النسخة التجريبية المجانية تكفي للاختبار؛ الترخيص الدائم مطلوب للإنتاج.  
- **أي كلمة مفتاحية تصف هذه العملية بأفضل شكل؟** *how to add bookmarks* (أساسية).  
- **هل هناك استكشاف أخطاء مدمج للعلامات المرجعية المفقودة؟** نعم—تحقق من توافق بداية/نهاية العلامة المرجعية وتعيينات مستويات المخطط.

## كيفية إضافة العلامات المرجعية في ملفات PDF
إنشاء العلامات المرجعية سهل مع Aspose.Words. سنقسم التنفيذ إلى خطوات واضحة أدناه.

### إعداد Aspose.Words
للبدء، أضف الاعتمادات اللازمة إلى مشروعك.

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
Aspose.Words هو منتج تجاري، لكن يمكنك البدء بنسخة تجريبية مجانية لاستكشاف ميزاته. إليك الخطوات:
1. **نسخة تجريبية مجانية**: حمّلها من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاختبار جميع القدرات.  
2. **ترخيص مؤقت**: قدّم طلبًا للحصول على ترخيص مؤقت عبر [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/) إذا لزم الأمر.  
3. **الشراء**: للاستخدام المستمر، اشترِ ترخيصًا من [بوابة شراء Aspose](https://purchase.aspose.com/buy).

بعد الحصول على ملف الترخيص، قم بتهيئته في مشروعك لفتح جميع ميزات Aspose.Words.

## إنشاء علامات مرجعية متداخلة
**نظرة عامة**: تعلّم كيفية إنشاء علامات مرجعية متداخلة داخل مستند Word باستخدام Aspose.Words for Java.

### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
هذا يجهز بيئة مستند Word حيث يمكنك بدء إدراج المحتوى.

### الخطوة 2: إدراج علامات مرجعية متداخلة
ابدأ بإنشاء علامة مرجعية رئيسية:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

الآن، ضع علامة مرجعية أخرى داخلها:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

أكمل العلامة المرجعية الخارجية:
```java
builder.endBookmark("Bookmark 1");
```

### الخطوة 3: إضافة علامات مرجعية إضافية
استمر في إضافة العلامات المرجعية حسب الحاجة. على سبيل المثال، علامة مرجعية ثالثة منفصلة:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## تكوين مستويات مخطط العلامات المرجعية
**نظرة عامة**: نظّم علامتك المرجعية بتعيين مستويات المخطط لتحسين التنقل في PDF.

### الخطوة 1: إعداد PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
هذا المقتطف يهيئ الخيارات التي ستستخدمها لحفظ المستند كملف PDF مع علامات مرجعية منظمة.

### الخطوة 2: إضافة مستويات المخطط
عيّن المستويات لكل علامة مرجعية، مما سيحدد هرمية العرض:
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### الخطوة 3: حفظ المستند
أخيرًا، احفظ المستند كملف PDF بهذه الإعدادات:
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## نصائح استكشاف الأخطاء وإصلاحها
- **العلامات المرجعية المفقودة**: تأكد من أن كل `startBookmark` له `endBookmark` مطابق.  
- **المستويات غير الصحيحة**: تحقق من الهرمية عبر فحص علاقات الأب‑ابن في الكود.  
- **استكشاف أخطاء علامة PDF**: إذا لم تظهر العلامات المرجعية في PDF المُنشأ، أعد التحقق من تمرير `PdfSaveOptions` بشكل صحيح إلى `doc.save()`.

## تطبيقات عملية
إليك بعض السيناريوهات التي يمكنك فيها تطبيق هذه المعرفة:
1. **الوثائق القانونية** – تنظيم الأقسام والفروع للرجوع السريع.  
2. **التقارير** – استخدام علامات مرجعية متداخلة للتنقل في هياكل بيانات معقدة.  
3. **المواد التعليمية** – هيكلة الفصول، الفروع، والنقاط الرئيسية بفعالية.  

## اعتبارات الأداء
- قلل حجم المستند بإزالة المحتوى غير الضروري قبل الحفظ.  
- إدارة استهلاك الذاكرة بفعالية عند التعامل مع مستندات كبيرة، خاصةً في عمليات **word to pdf bookmarks**.

## الخلاصة
لقد تعلمت الآن **كيفية إضافة العلامات المرجعية** وتكوين مستويات المخطط باستخدام Aspose.Words for Java. هذه المهارة تحسّن بشكل كبير قابلية التنقل في ملفات PDF، مما يجعلها أكثر صداقة للمستخدم واحترافية.

**الخطوات التالية**: جرّب هياكل مستند مختلفة أو دمج هذه الوظيفة في تطبيق أكبر لتلاحظ الفوائد عمليًا.

## قسم الأسئلة المتكررة
1. **كيف أقوم بتثبيت Aspose.Words for Java؟**  
   - أضفه كاعتماد عبر Maven أو Gradle، ثم قم بتهيئة ملف الترخيص.  
2. **هل يمكنني استخدام العلامات المرجعية بدون مستويات المخطط؟**  
   - نعم، لكن استخدام مستويات المخطط يحسّن التنقل في PDF.  
3. **ما هي حدود التداخل للعلامات المرجعية؟**  
   - لا يوجد حد صارم، لكن يُنصح بمراعاة القابلية للقراءة والهيكلة للمستخدمين.  
4. **كيف يتعامل Aspose مع المستندات الكبيرة؟**  
   - يدير الموارد بفعالية، رغم أن تحسين الأداء يُستحسن للملفات الضخمة جدًا.  
5. **هل يمكن تعديل العلامات المرجعية بعد حفظ PDF؟**  
   - نعم، باستخدام Aspose.PDF for Java لتعديل العلامات بعد التحويل.  

**أسئلة وإجابات إضافية**
- **س: هل تعمل هذه الطريقة أيضًا مع علامات Word إلى PDF؟**  
  ج: بالتأكيد – منطق إنشاء العلامات المرجعية نفسه يُطبق عند تحويل Word إلى PDF.  
- **س: كيف يمكنني إنشاء PDF مع علامات مرجعية في سطر واحد من الكود؟**  
  ج: عبر ربط استدعاءات `DocumentBuilder` وتمرير `PdfSaveOptions` المكوَّنة إلى `doc.save()`.

## الموارد
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

---

**آخر تحديث:** 2026-03-17  
**تم الاختبار مع:** Aspose.Words 25.3 for Java  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}