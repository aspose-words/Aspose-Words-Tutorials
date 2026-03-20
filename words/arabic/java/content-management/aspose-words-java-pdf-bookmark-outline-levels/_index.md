---
date: '2026-03-20'
description: تعلم كيفية إنشاء إشارات مرجعية متداخلة وتوليد PDF مع إشارات مرجعية باستخدام
  Aspose.Words for Java، مما يحسن القراءة والتنقل.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: إنشاء إشارات مرجعية متداخلة في ملفات PDF باستخدام Aspose.Words Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء إشارات مرجعية متداخلة في ملفات PDF باستخدام Aspose.Words Java

## المقدمة
إذا واجهت صعوبة في تنظيم إشارات PDF المرجعية بعد تحويل مستند Word، فأنت لست وحدك. في هذا الدرس ستقوم **بإنشاء إشارات مرجعية متداخلة** وتتعلم كيفية **إنشاء PDF مع إشارات مرجعية** تكون سهلة التنقل. سنستعرض إعداد Aspose.Words، بناء هيكلية الإشارات، تعيين مستويات المخطط، وأخيرًا تصدير PDF نظيف.

**ما ستتعلمه**
- كيفية إعداد Aspose.Words لـ Java
- كيفية **إنشاء إشارات مرجعية متداخلة** داخل مستند Word
- كيفية تكوين مستويات مخطط الإشارة لتسهيل التنقل في PDF
- كيفية **إنشاء PDF مع إشارات مرجعية** تعكس الهيكلية التي حددتها

### إجابات سريعة
- **ما هو الصنف الأساسي لإنشاء المستندات؟** `DocumentBuilder`
- **أي طريقة تضيف إشارة مرجعية؟** `startBookmark(String name)`
- **كيف تحدد مستوى المخطط لإشارة مرجعية؟** `outlineLevels.add(name, level)`
- **هل أحتاج إلى ترخيص للإنتاج؟** نعم، الترخيص المدفوع يفتح جميع الميزات.
- **هل يمكنني استخدام ذلك مع Maven أو Gradle؟** بالتأكيد – كلاهما مدعومان.

### المتطلبات المسبقة
قبل أن نبدأ، تأكد من وجود:
- **Aspose.Words for Java** (الإصدار 25.3 أو أحدث).  
- JDK مثبت وبيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- معرفة أساسية بـ Java وإلمام بـ Maven أو Gradle.

## ما معنى “إنشاء إشارات مرجعية متداخلة”؟
إنشاء إشارات مرجعية متداخلة يعني وضع إشارة داخل أخرى، مكوّنةً هيكلية أب‑ابن. عندما يُحفظ المستند كملف PDF، تظهر هذه العلاقات كعناصر قابلة للطي في لوحة الإشارات المرجعية للـ PDF، مما يجعل استكشاف المستندات الكبيرة أسهل كثيرًا.

## لماذا نستخدم مستويات المخطط عند إنشاء PDF مع إشارات مرجعية؟
مستويات المخطط تحدد الهرمية البصرية للإشارات في عارض الـ PDF. إشارة مستوى 1 تظهر كعنصر أعلى المستوى، مستوى 2 كابن، وهكذا. مستويات المخطط الصحيحة تحول قائمة مسطحة من الإشارات إلى جدول محتويات منظم، وهو أمر قيم خاصةً في العقود القانونية، التقارير التقنية، والكتب الإلكترونية.

## إعداد Aspose.Words
أضف المكتبة إلى مشروعك باستخدام Maven أو Gradle.

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
Aspose.Words هو منتج تجاري، لكن يمكنك البدء بنسخة تجريبية مجانية.

1. **نسخة تجريبية مجانية** – حمّلها من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاختبار جميع الإمكانات.  
2. **ترخيص مؤقت** – قدّم طلبًا عبر [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/) للتقييم قصير الأمد.  
3. **شراء** – احصل على ترخيص دائم من [بوابة الشراء الخاصة بـ Aspose](https://purchase.aspose.com/buy).

بعد حصولك على ملف `.lic`، حمّله في الكود لتفعيل جميع الميزات.

## دليل التنفيذ
فيما يلي شرح خطوة بخطوة لإنشاء مستند، إضافة إشارات مرجعية متداخلة، تعيين مستويات المخطط، وحفظ النتيجة كملف PDF.

### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
هذا ينشئ مستند Word فارغًا وكائن باني ستستخدمه لإدراج النص والإشارات المرجعية.

### الخطوة 2: إنشاء الإشارة المرجعية الأولى (الأصل)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
استدعاء `startBookmark` يفتح إشارة جديدة باسم **Bookmark 1**. أي محتوى تكتبه بعد هذا الاستدعاء سيُضمّن ضمن هذه الإشارة حتى تقوم بإغلاقها.

### الخطوة 3: تضمين إشارة مرجعية ثانية داخل الأولى
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
نظرًا لأن هذه الإشارة تبدأ **بعد** الأولى وتُغلق **قبل** الأولى، فإنها تصبح ابنًا لـ **Bookmark 1**.

### الخطوة 4: إغلاق الإشارة المرجعية الأصلية
```java
builder.endBookmark("Bookmark 1");
```
الآن تبدو الهيكلية كالتالي:

- Bookmark 1 (المستوى 1)  
  - Bookmark 2 (المستوى 2)

### الخطوة 5: إضافة إشارة مرجعية ثالثة مستقلة
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```
هذه الإشارة تقع في المستوى الأعلى، منفصلة عن الإشارتين السابقتين.

### الخطوة 6: تكوين مستويات المخطط لتصدير PDF
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
كائن `PdfSaveOptions` يتيح لك التحكم في كيفية ظهور الإشارات في ملف PDF النهائي.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 1);
```
هنا نُعيّن المستوى 1 للإشارات العليا والمستوى 2 للإشارة المتداخلة.

### الخطوة 7: حفظ المستند كملف PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
سيظهر ملف PDF الناتج لوحة إشارات مرجعية قابلة للطي تعكس الهيكلية التي عرّفتها.

## المشكلات الشائعة والحلول
- **الإشارات المفقودة** – يجب أن يكون لكل `startBookmark` ما يقابله `endBookmark`. إغفال أحدهما سيؤدي إلى تجاهل الإشارة في PDF.  
- **مستويات المخطط غير صحيحة** – تحقق من الأسماء التي تمررها إلى `outlineLevels.add`. أي خطأ إملائي يعني عدم تطبيق المستوى.  
- **المستندات الكبيرة** – للملفات الضخمة جدًا، استدعِ `doc.removeMacros()` أو احذف الأنماط غير المستخدمة قبل الحفظ لتقليل حجم PDF.

## تطبيقات عملية
1. **العقود القانونية** – الانتقال السريع بين البنود والفقرة الفرعية.  
2. **التقارير التقنية** – تصفح الأقسام والجداول والرسوم دون الحاجة للتمرير.  
3. **المواد التعليمية** – توفير جدول محتويات قابل للنقر للطلاب.

## نصائح الأداء
- احذف الموارد غير المستخدمة (الصور، الأنماط) قبل الحفظ.  
- استخدم واجهات الـ streaming إذا كنت تتعامل مع ملفات PDF أكبر من 100 ميغابايت لتقليل استهلاك الذاكرة.

## الخلاصة
أصبحت الآن قادرًا على **إنشاء إشارات مرجعية متداخلة**، تعيين مستويات المخطط، و**إنشاء PDF مع إشارات مرجعية** تكون عملية وسهلة الاستخدام. جرّب هيكليات أعمق أو دمج هذه المنطق في خط أنابيب توليد المستندات الخاص بك لمزيد من الأتمتة.

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words لـ Java؟**  
ج: أضف تبعية Maven أو Gradle الموضحة أعلاه، ثم حمّل ملف الترخيص في وقت التشغيل.

**س: هل يمكنني استخدام الإشارات دون تعيين مستويات المخطط؟**  
ج: نعم، لكن PDF سيظهر قائمة مسطحة قد تكون صعبة التنقل في المستندات المعقدة.

**س: هل هناك حد لعمق التداخل في الإشارات؟**  
ج: تقنيًا لا يوجد حد، لكن يُنصح بالحفاظ على هيكلية معقولة (3‑4 مستويات) لضمان قابلية القراءة.

**س: كيف يتعامل Aspose مع المستندات الضخمة؟**  
ج: يقوم بتدفق المحتوى ويقدم أدوات لإدارة الذاكرة؛ ومع ذلك، لا يزال من الأفضل حذف العناصر غير المستخدمة.

**س: هل يمكن تعديل الإشارات بعد إنشاء PDF؟**  
ج: بالتأكيد – استخدم Aspose.PDF لـ Java لتعديل عناوين الإشارات، الوجهات، أو مستويات المخطط بعد التوليد.

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

---

**آخر تحديث:** 2026-03-20  
**تم الاختبار مع:** Aspose.Words for Java 25.3  
**المؤلف:** Aspose