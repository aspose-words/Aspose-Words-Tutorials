---
date: '2026-03-28'
description: تعلم كيفية إضافة إشارات مرجعية إلى ملفات PDF وإدارة الإشارات المرجعية
  المتداخلة في PDF باستخدام Aspose.Words for Java. عزّز تنقل المستندات بمستويات مخطط
  واضحة.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: إضافة إشارات مرجعية ومستويات المخطط إلى PDF باستخدام Aspose.Words Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة إشارات PDF ومستويات المخطط باستخدام Aspose.Words Java

## مقدمة
إذا كنت تواجه صعوبة في **إضافة إشارات PDF** التي تبقى منظمة عند تحويل مستندات Word إلى ملفات PDF، فقد وجدت المكان المناسب. في هذا البرنامج التعليمي سنستعرض كيفية استخدام Aspose.Words for Java لإنشاء **إشارات متداخلة في PDF**، وتعيين مستويات المخطط، وإنتاج ملف PDF نظيف وسهل التنقل.

**ما ستتعلمه**
- إعداد Aspose.Words for Java في مشروعك  
- إنشاء **إشارات متداخلة في PDF** مباشرة من مستند Word  
- تكوين مستويات مخطط الإشارة لعرض هرمي  
- حفظ المستند النهائي كملف PDF مع إشارات منظمة بشكل صحيح  

### إجابات سريعة
- **ما هي الفائدة الأساسية من إضافة إشارات PDF؟** يحسن التنقل وتجربة المستخدم في المستندات الكبيرة.  
- **أي مكتبة تتيح إنشاء إشارات PDF بسهولة في Java؟** Aspose.Words for Java.  
- **هل أحتاج إلى ترخيص لاستخدام ميزات الإشارات؟** نسخة تجريبية مجانية تكفي للتقييم؛ الترخيص مطلوب للإنتاج.  
- **هل يمكنني تعيين مستويات مخطط مختلفة لكل إشارة؟** نعم، باستخدام `BookmarksOutlineLevelCollection` في `PdfSaveOptions`.  
- **هل هذه الطريقة متوافقة مع أحدث إصدار من Aspose.Words؟** بالتأكيد – تعمل مع الإصدار 25.3 وما بعده.  

## ما هو “إضافة إشارات PDF”؟
إضافة إشارات PDF تعني إدراج مدخلات قابلة للنقر في لوحة تنقل PDF التي تشير إلى أقسام محددة من المستند. عند دمجها مع مستويات المخطط، تشكل هذه الإشارات هيكلًا شجريًا يعكس تسلسل المستند الهرمي.

## لماذا نستخدم إشارات متداخلة في PDF؟
تتيح الإشارات المتداخلة للقراء الانتقال من الأقسام العليا إلى الفروع التفصيلية دون الحاجة للتمرير عبر الصفحات. وهذا يكون ذا قيمة خاصة للـ **العقود القانونية**، **التقارير التقنية**، و**دليل التعلم الإلكتروني** حيث يكون الإشارة السريعة ضرورية.

## المتطلبات المسبقة
- **المكتبات والاعتمادات**: Aspose.Words for Java (الإصدار 25.3 أو أحدث).  
- **البيئة**: JDK 8+ وIDE مثل IntelliJ IDEA أو Eclipse.  
- **المعرفة**: أساسيات Java، إلمام بـ Maven أو Gradle.  

## إعداد Aspose.Words
للبدء، قم بإضافة الاعتمادات اللازمة إلى مشروعك. إليك كيفية القيام بذلك باستخدام Maven وGradle:

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
Aspose.Words هو منتج تجاري، ولكن يمكنك البدء بنسخة تجريبية مجانية:
1. **نسخة تجريبية** – قم بتنزيلها من [صفحة إصدارات Aspose](https://releases.aspose.com/words/java/) لاختبار جميع القدرات.  
2. **ترخيص مؤقت** – قدِّم طلبًا على [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/) إذا كنت بحاجة إلى مفتاح قصير الأجل.  
3. **شراء** – احصل على ترخيص دائم من [بوابة الشراء الخاصة بـ Aspose](https://purchase.aspose.com/buy).

بعد الحصول على ملف الترخيص، حمّله في الكود الخاص بك لفتح جميع الميزات.

## دليل التنفيذ
دعونا نقسم التنفيذ إلى خطوات واضحة مرقمة.

### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
هذا ينشئ مستند Word جديد سنملأه بالمحتوى والإشارات.

### الخطوة 2: إدراج إشارات متداخلة
#### إنشاء الإشارة الأولى (الأصل)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### إدراج إشارة فرعية داخل الأصل
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### إغلاق إشارة الأصل
```java
builder.endBookmark("Bookmark 1");
```

#### إضافة إشارة ثالثة مستقلة
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### الخطوة 3: تكوين مستويات مخطط الإشارة
#### إعداد `PdfSaveOptions`
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### تعيين مستويات الهرمية
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### حفظ المستند كملف PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### المشكلات الشائعة والحلول
- **الإشارات المفقودة** – تحقق من أن كل `startBookmark` له `endBookmark` مطابق.  
- **هرمية المخطط غير صحيحة** – راجع أرقام المستويات؛ الرقم الأقل يعني مستوى أعلى في لوحة التنقل.  
- **المستندات الكبيرة** – استدعِ `doc.optimizeResources()` قبل الحفظ لتقليل استهلاك الذاكرة.

## التطبيقات العملية
1. **المستندات القانونية** – الانتقال سريعًا إلى البنود والبنود الفرعية.  
2. **التقارير السنوية** – التنقل بين الفصول، الأقسام، وجداول المحتويات.  
3. **المواد التعليمية** – توفير منهج قابل للنقر للطلاب داخل PDF.

## اعتبارات الأداء
- إزالة أي صور غير ضرورية أو أقسام مخفية قبل التحويل.  
- استخدام واجهات برمجة التطبيقات المتدفقة للملفات الكبيرة جدًا للحفاظ على انخفاض استهلاك الذاكرة.

## الخلاصة
أصبح لديك الآن طريقة كاملة وجاهزة للإنتاج **لإضافة إشارات PDF**، وتكوين مستويات المخطط الخاصة بها، وإنشاء PDF منظم جيدًا باستخدام Aspose.Words for Java. هذه التقنية تحسن بشكل كبير من قابلية استخدام المستند وتمنحك تحكمًا دقيقًا في تنقل PDF.

**الخطوات التالية** – جرّب دمج هذه الطريقة مع Aspose.PDF for Java لتعديل أو إضافة إشارات إضافية بعد إنشاء ملف PDF.

## قسم الأسئلة المتكررة
1. **كيف أقوم بتثبيت Aspose.Words for Java؟**  
   قم بإدراجه كاعتماد Maven أو Gradle وحمّل ملف الترخيص الخاص بك أثناء التشغيل.  
2. **هل يمكنني استخدام الإشارات بدون مستويات المخطط؟**  
   نعم، لكن مستويات المخطط توفر عرضًا هرميًا يجعل التنقل أسهل بكثير.  
3. **ما هي حدود تداخل الإشارات؟**  
   لا يوجد حد ثابت، لكن احرص على أن تكون الهرمية منطقية لأفضل تجربة للمستخدم.  
4. **كيف يتعامل Aspose مع المستندات الكبيرة؟**  
   يقوم بتدفق الموارد بكفاءة؛ ومع ذلك، يجب عليك استدعاء `optimizeResources()` للملفات الكبيرة جدًا.  
5. **هل يمكنني تعديل الإشارات بعد حفظ PDF؟**  
   بالتأكيد – استخدم Aspose.PDF for Java لتعديل الإشارات بعد التحويل.

## أسئلة متكررة إضافية
**س: هل تعمل هذه التقنية عند تحويل DOCX إلى PDF؟**  
ج: نعم، خطوات إنشاء الإشارات نفسها تنطبق بغض النظر عن تنسيق Word المصدر.

**س: هل يمكن تعيين ألوان أو أيقونات مخصصة للإشارات؟**  
ج: مظهر الإشارة يتحكم فيه عارض PDF؛ Aspose.Words يركز على الهرمية والتسمية.

**س: هل ستظهر مستويات المخطط في جميع عارضات PDF؟**  
ج: معظم عارضات PDF الحديثة (Adobe Acrobat، Foxit، Chrome) تحترم الهرمية التي يحددها Aspose.Words.

## الموارد
- [توثيق Aspose.Words](https://reference.aspose.com/words/java/)  
- [تحميل أحدث الإصدارات](https://releases.aspose.com/words/java/)  
- [شراء ترخيص](https://purchase.aspose.com/buy)  
- [نسخة تجريبية](https://releases.aspose.com/words/java/)  
- [طلب ترخيص مؤقت](https://purchase.aspose.com/temporary-license/)  
- [منتدى دعم Aspose](https://forum.aspose.com/c/words/10)

---

**آخر تحديث:** 2026-03-28  
**تم الاختبار مع:** Aspose.Words 25.3 for Java  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}