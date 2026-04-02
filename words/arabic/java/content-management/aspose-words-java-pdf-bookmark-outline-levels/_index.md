---
date: '2026-04-02'
description: تعرّف على كيفية إنشاء إشارات مرجعية متداخلة، وتحديد مستويات مخطط الإشارة
  المرجعية، وحفظ مستندات Word بصيغة PDF باستخدام Aspose.Words for Java.
keywords:
- create nested bookmarks
- how to set bookmark
- save word pdf bookmarks
title: إنشاء إشارات مرجعية متداخلة وتعيين مستويات المخطط في ملفات PDF باستخدام Aspose.Words
  for Java
url: /ar/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء إشارات مرجعية متداخلة وتعيين مستويات المخطط في ملفات PDF باستخدام Aspose.Words للغة Java

## مقدمة
هل تواجه صعوبة في إدارة الإشارات المرجعية عند تحويل مستندات Word إلى PDF؟ **يُظهر لك هذا البرنامج التعليمي كيفية إنشاء إشارات مرجعية متداخلة**، وتكوين مستويات المخطط الخاصة بها، وحفظ النتيجة كملف PDF نظيف وسهل التنقل باستخدام Aspose.Words للغة Java. في نهاية هذا الدليل ستحصل على ملف PDF بمظهر احترافي يمكن للقراء القفز مباشرة إلى الأقسام التي يحتاجونها.

**ما ستتعلمه**
- إعداد Aspose.Words للغة Java في مشروعك  
- **إنشاء إشارات مرجعية متداخلة** في مستند Word  
- **كيفية تعيين مستويات المخطط للإشارات المرجعية** لتسلسل هرمي واضح  
- **حفظ إشارات مرجعية PDF من Word** بالهيكل الصحيح  

### إجابات سريعة
- **ما هي الفئة الأساسية لإنشاء المستندات؟** `DocumentBuilder`  
- **ما الطريقة التي تضيف مستوى مخطط للإشارة المرجعية؟** `BookmarksOutlineLevels.add()`  
- **هل أحتاج إلى ترخيص لتصدير ملفات PDF؟** A license is required for production; a free trial works for evaluation.  
- **هل يمكنني تعشيق الإشارات المرجعية بعمق تعسفي؟** Yes, but keep the hierarchy readable for end users.  
- **ما إصدار Aspose.Words المطلوب؟** Version 25.3 or later.

## ما هو “إنشاء إشارات مرجعية متداخلة”؟
الإشارات المرجعية المتداخلة هي إشارات مرجعية توضع داخل إشارات مرجعية أخرى، مكونةً تسلسلًا هرميًا من النوع أب‑ابن. في ملف PDF تظهر كعناصر قابلة للتوسيع في لوحة الإشارات المرجعية، مما يسمح للقراء بطي أو توسيع الأقسام حسب الحاجة.

## لماذا يتم تعيين مستويات مخطط الإشارات المرجعية؟
تحدد مستويات المخطط ترتيب التداخل البصري في لوحة الإشارات المرجعية لملف PDF. تحسين المستويات بشكل صحيح يعزز التنقل، خاصةً في العقود القانونية الطويلة، أو التقارير التقنية، أو الكتب الإلكترونية حيث يحتاج المستخدمون إلى العثور على المعلومات بسرعة.

## المتطلبات المسبقة
- **المكتبات والاعتمادات**: Aspose.Words للغة Java (الإصدار 25.3 أو أحدث).  
- **البيئة**: JDK 8+ وبيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- **المعرفة**: معرفة أساسية بـ Java، وإلمام بـ Maven أو Gradle.

### إعداد Aspose.Words
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
Aspose.Words هو منتج تجاري، لكن يمكنك البدء بتجربة مجانية.

1. **Free Trial** – قم بالتنزيل من [Aspose's release page](https://releases.aspose.com/words/java/) لاختبار جميع الإمكانيات.  
2. **Temporary License** – قدّم طلبًا في [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) إذا كنت بحاجة إلى مفتاح قصير الأمد.  
3. **Purchase** – اشترِ ترخيصًا دائمًا عبر [Aspose’s purchasing portal](https://purchase.aspose.com/buy).

قم بتهيئة ملف الترخيص في الكود قبل استخدام أي من واجهات Aspose لفتح جميع الميزات.

## دليل التنفيذ

### كيفية إنشاء إشارات مرجعية متداخلة في مستند Word
سنقوم بإنشاء مستند بسيط وإضافة ثلاث إشارات مرجعية، إحداها يحتوي على إشارة مرجعية أخرى.

#### الخطوة 1: تهيئة المستند والباني
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### الخطوة 2: إدراج الإشارة المرجعية الأولى (الأصلية)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### الخطوة 3: تعشيق إشارة مرجعية ثانية داخل الأولى
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### الخطوة 4: إغلاق الإشارة المرجعية الخارجية
```java
builder.endBookmark("Bookmark 1");
```

#### الخطوة 5: إضافة إشارة مرجعية ثالثة مستقلة
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### كيفية تعيين مستويات مخطط الإشارات المرجعية لتصدير PDF
الآن سنقوم بتكوين تسلسل المستويات الذي سيظهر في ملف PDF النهائي.

#### الخطوة 1: إعداد `PdfSaveOptions`
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### الخطوة 2: تعيين مستويات المخطط لكل إشارة مرجعية
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### الخطوة 3: حفظ المستند كملف PDF مع الإشارات المرجعية المكوَّنة
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## المشكلات الشائعة والحلول
- **الإشارات المرجعية المفقودة** – تحقق من أن كل `startBookmark` له `endBookmark` مطابق.  
- **التسلسل الهرمي غير الصحيح** – تحقق مرة أخرى من أرقام المستويات التي تعينها؛ الرقم الأقل يعني مستوى أعلى (أب).  
- **الترخيص غير مفعَّل** – إذا اختفت الإشارات المرجعية، تأكد من تحميل ملف الترخيص قبل أي معالجة للمستند.  

## التطبيقات العملية
1. **العقود القانونية** – القفز بسرعة إلى البنود، والبنود الفرعية، والملحقات.  
2. **التقارير التقنية** – التنقل بين الأقسام والجداول والرسوم دون التمرير.  
3. **المواد التعليمية الإلكترونية** – السماح للطلاب بتوسيع الفصول وطي الأمثلة حسب الحاجة.

## نصائح الأداء
- إزالة الأقسام أو الصور غير المستخدمة قبل الحفظ للحفاظ على حجم PDF صغير.  
- بالنسبة للمستندات الكبيرة جدًا، استدعِ `doc.cleanup()` أو عالج الملف على دفعات لتقليل الضغط على الذاكرة.

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words للغة Java؟**  
أ: أضف الاعتماد Maven أو Gradle الموضح أعلاه، ثم ضع ملف الترخيص في المشروع وتهيئه في الكود.

**س: هل يمكنني استخدام الإشارات المرجعية دون تعيين مستويات المخطط؟**  
أ: نعم، ولكن بدون مستويات المخطط ستظهر لوحة الإشارات المرجعية في PDF كقائمة مسطحة، مما يجعل التنقل أصعب.

**س: هل هناك حد لعمق تعشيق الإشارات المرجعية؟**  
أ: تقنيًا لا يوجد حد، لكن احرص على أن يكون التسلسل الهرمي معقولًا (3‑4 مستويات) لسهولة قراءة المستخدم.

**س: كيف يتعامل Aspose مع ملفات Word الكبيرة جدًا؟**  
أ: المكتبة تقوم ببث المحتوى وتوفر طرقًا مثل `Document.optimizeResources()` للحفاظ على استهلاك الذاكرة منخفضًا.

**س: هل يمكنني تعديل الإشارات المرجعية بعد إنشاء ملف PDF؟**  
أ: نعم، يمكنك استخدام Aspose.PDF للغة Java لتعديل عناوين الإشارات المرجعية أو وجهاتها أو التسلسل الهرمي بعد الإنشاء.

## الموارد
- [توثيق Aspose.Words](https://reference.aspose.com/words/java/)
- [تحميل أحدث الإصدارات](https://releases.aspose.com/words/java/)
- [شراء ترخيص](https://purchase.aspose.com/buy)
- [تجربة مجانية](https://releases.aspose.com/words/java/)
- [طلب ترخيص مؤقت](https://purchase.aspose.com/temporary-license/)
- [منتدى دعم Aspose](https://forum.aspose.com/c/words/10)

---

**آخر تحديث:** 2026-04-02  
**تم الاختبار مع:** Aspose.Words 25.3 للغة Java  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}