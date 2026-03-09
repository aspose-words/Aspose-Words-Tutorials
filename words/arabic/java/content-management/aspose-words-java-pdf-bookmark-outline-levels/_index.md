---
date: '2026-03-09'
description: تعلم كيفية إنشاء إشارات مرجعية متداخلة في Java وحفظ إشارات مرجعية Word
  وPDF باستخدام Aspose.Words for Java، وتنظيم مخططات PDF لتسهيل التنقل.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: إنشاء إشارات مرجعية متداخلة في جافا لمستويات مخطط PDF
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء إشارات مرجعية متداخلة Java لمستويات مخطط PDF

## مقدمة
هل تواجه صعوبة في إدارة الإشارات المرجعية عند تحويل مستندات Word إلى PDF؟ في هذا الدرس ستقوم **create nested bookmarks java** باستخدام Aspose.Words for Java، ثم **save word pdf bookmarks** مع هيكل مخطط واضح. في النهاية ستحصل على PDF بمظهر احترافي وسهل التنقل، بغض النظر عن عدد الأقسام التي تضيفها.

**ما ستتعلمه**
- إعداد Aspose.Words for Java
- **Create nested bookmarks java** في مستند Word
- تكوين مستويات مخطط الإشارة المرجعية للتنقل الهيكلي
- **Save word pdf bookmarks** بالهيكل المطلوب

### إجابات سريعة
- **ما هو الصنف الأساسي لإنشاء المستندات؟** `DocumentBuilder`
- **أي خيار يتحكم في هيكل الإشارات المرجعية؟** `BookmarksOutlineLevelCollection`
- **هل يمكنني استخدام Maven أو Gradle؟** نعم، كلاهما مدعومان
- **هل أحتاج إلى ترخيص للإنتاج؟** نعم، يلزم وجود ترخيص صالح لـ Aspose.Words
- **ما نسخة Java الموصى بها؟** JDK 11 أو أعلى

## ما هو “create nested bookmarks java”؟
إنشاء إشارات مرجعية متداخلة يعني وضع إشارة مرجعية داخل أخرى بحيث يستطيع قارئ PDF عرض مخطط قابل للطي. هذا مفيد بشكل خاص للتقارير الكبيرة، العقود القانونية، أو الكتب الإلكترونية حيث يحتاج القارئ إلى الانتقال إلى أقسام معينة بسرعة.

## لماذا نستخدم Aspose.Words لمستويات مخطط الإشارات المرجعية في PDF؟
يتولى Aspose.Words عملية التحويل من Word إلى PDF مع الحفاظ على هيكل الإشارات المرجعية. يمنحك تحكمًا دقيقًا في مستويات المخطط، مما يتيح لك تعريف علاقات الأب‑ابن دون الحاجة إلى تعديل PDF يدويًا.

## المتطلبات المسبقة
- **المكتبات والاعتمادات**: Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **البيئة**: JDK 11+ وIDE مثل IntelliJ IDEA أو Eclipse.  
- **المعرفة**: أساسيات Java، إلمام بـ Maven أو Gradle.

## إعداد Aspose.Words
للبدء، أدرج الاعتمادات اللازمة في مشروعك. إليك كيفية القيام بذلك باستخدام Maven و Gradle:

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
Aspose.Words هو منتج تجاري، ولكن يمكنك البدء بنسخة تجريبية مجانية لاستكشاف ميزاته.

1. **نسخة تجريبية مجانية**: قم بتنزيلها من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاختبار جميع الإمكانيات.  
2. **ترخيص مؤقت**: قدّم طلبًا للحصول على ترخيص مؤقت عبر [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/) إذا لزم الأمر.  
3. **شراء**: للاستخدام المستمر، اشترِ ترخيصًا من [بوابة شراء Aspose](https://purchase.aspose.com/buy).

بمجرد حصولك على ملف الترخيص، قم بتهيئته في مشروعك لفتح جميع الوظائف.

## دليل التنفيذ
سنتناول الشيفرة خطوة بخطوة. كل مقطع يبقى كما هو من الدرس الأصلي، لضمان التوافق الكامل.

### إنشاء إشارات مرجعية متداخلة (create nested bookmarks java)
**الخطوة 1: تهيئة Document و Builder**  
هذا ينشئ مستند Word جديد يمكنك ملؤه بالمحتوى والإشارات المرجعية.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**الخطوة 2: إدراج الإشارة المرجعية الأولى (الأصلية)**  
ابدأ الإشارة المرجعية الخارجية وأضف بعض النص.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

**الخطوة 3: وضع إشارة مرجعية ثانية داخل الأولى**  
الآن نضيف إشارة مرجعية فرعية داخل الأصلية.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

**الخطوة 4: إغلاق الإشارة المرجعية الخارجية**  

```java
builder.endBookmark("Bookmark 1");
```

**الخطوة 5: إضافة أي إشارات مرجعية إضافية على المستوى الأعلى**  
يمكنك الاستمرار في إضافة المزيد من الإشارات حسب الحاجة.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### تكوين مستويات مخطط الإشارة المرجعية (save word pdf bookmarks)
**الخطوة 1: إعداد `PdfSaveOptions`**  
تتيح لك هذه الخيارات تحديد كيفية ظهور الإشارات المرجعية في PDF النهائي.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

**الخطوة 2: تعيين مستويات المخطط لكل إشارة مرجعية**  
المستوى 1 هو إدخال على المستوى الأعلى، المستوى 2 متداخل تحت المستوى 1، وهكذا.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

**الخطوة 3: حفظ المستند كملف PDF**  
سيحتوي PDF الآن على لوحة إشارات مرجعية منظمة.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## المشكلات الشائعة والحلول
- **الإشارات المرجعية المفقودة** – تأكد من أن كل `startBookmark` له `endBookmark` مطابق.  
- **الهيكل غير الصحيح** – راجع أرقام المستويات التي تعينها؛ فهي تحدد ترتيب التداخل.  
- **عدم تطبيق الترخيص** – إذا اختفت الإشارات المرجعية، تأكد من تحميل ملف الترخيص بشكل صحيح قبل الحفظ.

## التطبيقات العملية
1. **العقود القانونية** – الانتقال بسرعة بين البنود والفرعيات.  
2. **التقارير المالية** – التنقل بين الأقسام والجداول والملحقات بسهولة.  
3. **الأدلة التقنية** – توفير جدول محتويات واضح وقابل للطي داخل PDF للقراء.

## اعتبارات الأداء
- **حجم المستند** – احذف الأنماط أو الصور غير المستخدمة قبل الحفظ للحفاظ على خفة PDF.  
- **استخدام الذاكرة** – بالنسبة للمستندات الكبيرة جدًا، فكر في معالجة الصفحات على دفعات أو استخدام `Document.optimizeResources()`.

## الخلاصة
أنت الآن تعرف كيفية **create nested bookmarks java** و **save word pdf bookmarks** باستخدام Aspose.Words for Java. يمنحك هذا النهج تحكمًا كاملاً في تنقل PDF، مما يجعل مستنداتك أكثر احترافية وسهولة للمستخدم.

**الخطوات التالية**  
جرّب إضافة أيقونات مخصصة للإشارات المرجعية، أو دمج هذه العملية في تطبيق معالجة دفعات أكبر.

## قسم الأسئلة المتكررة
1. **كيف أقوم بتثبيت Aspose.Words for Java؟**  
   - أدرجه كاعتماد عبر Maven أو Gradle، ثم قم بإعداد ملف الترخيص الخاص بك.  
2. **هل يمكنني استخدام الإشارات المرجعية دون مستويات المخطط؟**  
   - نعم، لكن استخدام مستويات المخطط يحسن بشكل كبير تنقل PDF.  
3. **ما هي حدود تداخل الإشارات المرجعية؟**  
   - لا يوجد حد صارم، لكن احرص على أن تكون الهرمية منطقية للقراء.  
4. **كيف يتعامل Aspose مع المستندات الكبيرة؟**  
   - يدير الموارد بكفاءة، رغم أنه لا يزال من الأفضل تحسين الملفات الكبيرة.  
5. **هل يمكن تعديل الإشارات المرجعية بعد حفظ PDF؟**  
   - نعم، يمكنك استخدام Aspose.PDF for Java لتعديل الإشارات بعد التحويل.

## الموارد
- [توثيق Aspose.Words](https://reference.aspose.com/words/java/)
- [تحميل أحدث الإصدارات](https://releases.aspose.com/words/java/)
- [شراء ترخيص](https://purchase.aspose.com/buy)
- [نسخة تجريبية مجانية](https://releases.aspose.com/words/java/)
- [طلب ترخيص مؤقت](https://purchase.aspose.com/temporary-license/)
- [منتدى دعم Aspose](https://forum.aspose.com/c/words/10)

---

**آخر تحديث:** 2026-03-09  
**تم الاختبار مع:** Aspose.Words 25.3 for Java  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}