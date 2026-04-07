---
date: '2026-04-07'
description: تعلم كيفية إنشاء إشارات مرجعية متداخلة في ملفات PDF، وإنشاء PDF مع إشارات
  مرجعية، وحفظ إشارات مرجعية PDF من Word باستخدام Aspose.Words للغة Java.
keywords:
- create nested pdf bookmarks
- generate pdf with bookmarks
- save word pdf bookmarks
title: إنشاء إشارات مرجعية متداخلة في PDF باستخدام Java و Aspose.Words
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء إشارات PDF متداخلة في Java باستخدام Aspose.Words

## مقدمة
في هذا الدرس، ستتعلم كيفية **إنشاء إشارات PDF متداخلة** باستخدام Aspose.Words for Java، مما يتيح لك توليد ملفات PDF مع إشارات وحفظ إشارات Word PDF بهيكل مخطط نظيف. سنستعرض إعداد المكتبة، بناء الإشارات المتداخلة، تعيين مستويات المخطط، وتصدير ملف PDF النهائي.

**ما ستتعلمه**
- تثبيت وترخيص Aspose.Words for Java
- بناء إشارات متداخلة داخل مستند Word
- تكوين مستويات مخطط الإشارة للتنقل الهيكلي
- حفظ المستند كملف PDF يحافظ على تسلسل الإشارات

### المتطلبات المسبقة
قبل أن تبدأ، تأكد من أن لديك:
- **المكتبات والاعتمادات**: Aspose.Words for Java (25.3 أو أحدث)  
- **البيئة**: JDK 8+ وIDE مثل IntelliJ IDEA أو Eclipse  
- **المهارات الأساسية**: الإلمام بـ Java، Maven أو Gradle، ومفهوم إشارات PDF  

## إجابات سريعة
- **ماذا يعني “إنشاء إشارات PDF متداخلة”?**  
  يعني بناء هيكلية من الإشارات حيث توضع الإشارات الفرعية داخل الإشارات الأم، مثل الفصول والفصول الفرعية في كتاب.  
- **أي منتج من Aspose يتعامل مع تحويل PDF؟**  
  يقوم Aspose.Words for Java بتحويل Word إلى PDF مع الحفاظ على مستويات مخطط الإشارة.  
- **هل أحتاج إلى ترخيص للتطوير؟**  
  يمكنك البدء بتجربة مجانية؛ يتوفر ترخيص مؤقت للاختبار قصير المدى.  
- **هل يمكنني تعيين مستويات مخطط مخصصة؟**  
  نعم – تسمح لك `BookmarksOutlineLevelCollection` بتعيين أي مستوى عدد صحيح لكل إشارة.  
- **هل هذا النهج متوافق مع المستندات الكبيرة؟**  
  بالتأكيد. تقوم Aspose.Words ببث البيانات بكفاءة، لكن يجب إزالة المحتوى غير المستخدم للحفاظ على حجم الملف مثاليًا.

## ما هو “إنشاء إشارات PDF متداخلة”؟
إشارات PDF المتداخلة هي بنية شجرية تظهر في لوحات التنقل في عارضات PDF. تسمح للقراء بالقفز مباشرة إلى الأقسام، الفروع، أو الفقرات المحددة، مما يحسن من قابلية استخدام المستند—خاصةً للعقود القانونية، التقارير التقنية، أو الكتب الإلكترونية.

## لماذا نستخدم Aspose.Words لمستويات مخطط الإشارة؟
يوفر Aspose.Words واجهة برمجة تطبيقات سلسة لتحديد الإشارات أثناء بناء المستند، ثم يطابق هذه الإشارات تلقائيًا مع مدخلات مخطط PDF. هذا يلغي الحاجة إلى معالجة يدوية بعد الإنشاء ويضمن أن تنقل PDF يعكس الهيكل الأصلي في Word.

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
Aspose.Words مكتبة تجارية، لكن يمكنك تقييمها مجانًا.

1. **تجربة مجانية** – قم بتنزيلها من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاستكشاف جميع الميزات.  
2. **ترخيص مؤقت** – قدم طلبًا على [صفحة الترخيص المؤقت من Aspose](https://purchase.aspose.com/temporary-license/) للمشاريع قصيرة الأجل.  
3. **شراء** – احصل على ترخيص كامل من [بوابة شراء Aspose](https://purchase.aspose.com/buy).

بعد استلامك لملف `.lic`، قم بتحميله عند بدء تشغيل التطبيق لفتح جميع الإمكانيات.

## دليل التنفيذ
سنقسم التنفيذ إلى جزأين منطقيين: إنشاء إشارات متداخلة وتكوين مستويات مخططها.

### إنشاء إشارات متداخلة
**نظرة عامة** – يوضح هذا القسم كيفية تضمين إشارات هرمية مباشرة في مستند Word.

#### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
يوفر لك `DocumentBuilder` طريقة مريحة لإدراج النصوص، الجداول، والإشارات.

#### الخطوة 2: إدراج إشارات أساسية ومتداخلة
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
الآن أضف إشارة فرعية داخل الإشارة الأولى:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
إغلاق الإشارة الخارجية:
```java
builder.endBookmark("Bookmark 1");
```

#### الخطوة 3: إضافة إشارة مستوى أعلى منفصلة
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```
يمكنك تكرار هذه الخطوات لبناء هيكلية عميقة حسب الحاجة.

### تكوين مستويات مخطط الإشارة
**نظرة عامة** – بعد وجود الإشارات، حدد مستويات المخطط بحيث يعرضها عارضو PDF بشكل صحيح.

#### الخطوة 1: إعداد PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
`PdfSaveOptions` يتحكم في كيفية تحويل مستند Word إلى PDF.

#### الخطوة 2: تعيين مستويات لكل إشارة
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
المستوى 1 يظهر كإدخال مستوى أعلى، المستوى 2 كفرعي، وهكذا.

#### الخطوة 3: حفظ المستند كملف PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
سيعرض ملف PDF الناتج لوحة إشارات ثلاثية المستويات تعكس الهيكلية التي حددتها.

### نصائح حل المشكلات
- **الإشارات المفقودة** – تحقق من أن كل `startBookmark` له `endBookmark` مطابق.  
- **الهيكلية غير الصحيحة** – راجع أرقام مستويات المخطط؛ يجب أن يكون للفرع مستوى أعلى من المستوى الأب.  
- **أخطاء الترخيص** – تأكد من تحميل ملف الترخيص قبل استدعاء أي واجهات Aspose؛ وإلا سترى علامات مائية للتقييم.

## تطبيقات عملية
1. **العقود القانونية** – الانتقال السريع إلى البنود، الفقرات الفرعية، والملحقات.  
2. **التقارير التقنية** – تصفح المواصفات الكبيرة باستخدام إشارات على مستوى الفصول.  
3. **مواد التعلم الإلكتروني** – توفير وصول فوري للمتعلمين إلى الدروس والاختبارات.

## اعتبارات الأداء
- **حجم المستند** – أزل الأنماط غير المستخدمة أو الأقسام المخفية قبل الحفظ للحفاظ على خفة PDF.  
- **إدارة الذاكرة** – للملفات الكبيرة جدًا، فكر في بث المستند أو استخدام `Document.optimizeResources()`.

## الخلاصة
الآن لديك طريقة كاملة وجاهزة للإنتاج **لإنشاء إشارات PDF متداخلة**، **إنشاء PDF مع إشارات**، و**حفظ إشارات Word PDF** باستخدام Aspose.Words for Java. دمج هذا النمط في خطوط تقاريرك أو أنابيب توليد المستندات لتقديم ملفات PDF مصقولة وقابلة للتنقل.

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
**ج:** أضف تبعية Maven أو Gradle الموضحة أعلاه، ثم حمّل ملف الترخيص أثناء التشغيل.

**س: هل يمكنني استخدام الإشارات دون تعيين مستويات المخطط؟**  
**ج:** نعم، لكن تنقل PDF سيكون مسطحًا، مما يصعب على القراء فهم هيكل المستند.

**س: هل هناك حد لعمق تداخل الإشارات؟**  
**ج:** تقنيًا لا، لكن احرص على أن تكون الهيكلية معقولة (3‑5 مستويات) للحفاظ على قابلية القراءة في معظم عارضات PDF.

**س: كيف يتعامل Aspose.Words مع المستندات الكبيرة جدًا؟**  
**ج:** يبث المحتوى ويقدم `optimizeResources()` لتقليل استهلاك الذاكرة، رغم أنه يجب عليك اختبار ذلك مع أحجام ملفاتك الخاصة.

**س: هل يمكنني تعديل الإشارات بعد إنشاء PDF؟**  
**ج:** بالتأكيد—استخدم Aspose.PDF for Java لتعديل عناوين الإشارات أو وجهاتها أو مستويات المخطط بعد الإنشاء.

## الموارد
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

---

**Last Updated:** 2026-04-07  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}