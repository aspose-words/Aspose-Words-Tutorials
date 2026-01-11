---
date: 2026-01-11
description: تعلم كيفية إظهار وإخفاء العلامات المرجعية وإنشاء علامة مرجعية في Java
  باستخدام Aspose.Words for Java للتنقل الفعال في المستندات ومعالجتها.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: إظهار وإخفاء العلامات المرجعية باستخدام Aspose.Words للـ Java
url: /ar/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إظهار وإخفاء العلامات المرجعية باستخدام Aspose.Words for Java

## مقدمة لاستخدام العلامات المرجعية في Aspose.Words for Java

العلامات المرجعية هي ميزة قوية في Aspose.Words for Java تتيح لك **create bookmark java**، والتنقل إلى محتوى محدد، وحتى **show hide bookmarks** عندما تحتاج إلى إنشاء إصدارات مختلفة من المستند. في هذا الدليل خطوة بخطوة سنستعرض إنشاء العلامات المرجعية، الوصول إليها، تحديثها، نسخها، وتبديل رؤيتها، مما يمنحك سيطرة كاملة على تعديل المستند.

## إجابات سريعة
- **ما هو الغرض الأساسي من العلامات المرجعية؟** لتمييز واسترجاع أجزاء محددة من المستند لاحقًا.  
- **هل يمكنني إخفاء علامات العلامة المرجعية في الناتج النهائي؟** نعم—استخدم واجهة برمجة تطبيقات show/hide لتبديل رؤيتها.  
- **كيف يمكنني إنشاء علامة مرجعية داخل خلية جدول؟** ابدأ وانهِ العلامة باستخدام `DocumentBuilder` بينما يكون المؤشر داخل الخلية.  
- **هل يمكن نسخ النص المعلَّم إلى مستند آخر؟** بالطبع—استخدم `NodeImporter` للحفاظ على التنسيق.  
- **ما نسخة Aspose.Words المطلوبة؟** أي إصدار حديث؛ يعمل الكود مع أحدث نسخة 2026.

## ما هو “إظهار إخفاء العلامات المرجعية”؟

تتيح لك ميزة **show hide bookmarks** عرض أو إخفاء محددات العلامة المرجعية برمجيًا في المستند المحفوظ. هذا مفيد عندما ترغب في إنشاء مخرجات نظيفة للمستخدمين النهائيين مع الحفاظ على بيانات العلامات المرجعية للمعالجة الداخلية.

## لماذا نستخدم العلامات المرجعية في أتمتة المستندات بجافا؟

- **تنقل فعال** – الانتقال مباشرة إلى الأقسام دون فحص الملف بالكامل.  
- **إنشاء محتوى ديناميكي** – إدراج، استبدال أو إزالة نص مرتبط بعلامة مرجعية.  
- **رؤية شرطية** – إظهار أو إخفاء علامات العلامة المرجعية بناءً على تفضيلات المستخدم أو تنسيق المخرج.  
- **قابلية إعادة الاستخدام** – نسخ أجزاء معلَّمة بين المستندات مع الحفاظ على الأنماط.

## المتطلبات المسبقة
- مجموعة تطوير جافا (JDK) 8 أو أعلى.  
- مكتبة Aspose.Words for Java مضافة إلى مشروعك (Maven/Gradle أو JAR).  
- إلمام أساسي بفئات `Document` و `DocumentBuilder`.

## دليل خطوة بخطوة

### الخطوة 1: إنشاء علامة مرجعية (create bookmark java)

لإضافة علامة مرجعية، تبدأها، تكتب المحتوى، ثم تنهيها. يوضح هذا المثال إنشاء علامة مرجعية بسيطة باسم **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### الخطوة 2: الوصول إلى العلامات المرجعية (access bookmarks java)

يمكن استرجاع العلامات المرجعية إما بواسطة الفهرس الصفري أو بالاسم. يوضح الكود أدناه كلا النهجين.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### الخطوة 3: تحديث بيانات العلامة المرجعية (update bookmark text)

يمكنك إعادة تسمية علامة مرجعية أو استبدال محتوى نصها. هذا مفيد عندما يتغير المستند الأساسي.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### الخطوة 4: العمل مع النص المعلَّم (copy bookmarked text)

نسخ جزء معلَّم إلى مستند آخر مع الحفاظ على التنسيق الأصلي سهل باستخدام `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### الخطوة 5: إظهار وإخفاء العلامات المرجعية (show hide bookmarks)

المقتطف التالي يوضح كيفية إخفاء علامات العلامة المرجعية في الملف المحفوظ. مرّر `false` للإخفاء، `true` للإظهار.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### الخطوة 6: فك تشابك علامات الصف (bookmark table cell)

عند امتداد العلامات المرجعية عبر صفوف الجدول، قد تتشابك. الطرق المساعدة أدناه تفك هذا التشابك وتسمح لك بحذف صف محدد بواسطة علامته المرجعية.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## المشكلات الشائعة والحلول

| المشكلة | الحل |
|-------|----------|
| **العلامة المرجعية غير موجودة** | تحقق من أن اسم العلامة المرجعية يطابق تمامًا (حسّاس لحالة الأحرف) وأن المستند تم حفظه بعد الإنشاء. |
| **فقدان تنسيق النص المنسوخ** | استخدم `ImportFormatMode.KEEP_SOURCE_FORMATTING` مع `NodeImporter` كما هو موضح في الخطوة 4. |
| **إظهار/إخفاء لا يؤثر على المخرجات** | تأكد من استدعاء `showHideBookmarkedContent` **قبل** حفظ المستند. |
| **العلامة المرجعية داخل خلية جدول يتم تجاهلها** | ضع استدعاءات البداية/النهاية بينما يكون مؤشر الـ builder داخل الخلية المستهدفة. |

## الأسئلة المتكررة

**س: كيف يمكنني إنشاء علامة مرجعية في خلية جدول؟**  
ج: استخدم `DocumentBuilder` لنقل المؤشر إلى الخلية المطلوبة، ثم استدعِ `startBookmark` و `endBookmark` حول محتوى الخلية.

**س: هل يمكنني نسخ علامة مرجعية إلى مستند آخر؟**  
ج: نعم—استخدم فئة `NodeImporter` (انظر الخطوة 4) لاستيراد العقدة المعلَّمة مع الحفاظ على تنسيقها الأصلي.

**س: كيف يمكنني حذف صف بواسطة علامته المرجعية؟**  
ج: أولاً حدد الصف الذي يحتوي على العلامة المرجعية، ثم استدعِ `remove` على عقدة الصف (كما هو موضح في الخطوة 6).

**س: ما هي بعض حالات الاستخدام الشائعة للعلامات المرجعية؟**  
ج: إنشاء جدول محتويات، استخراج أقسام محددة للتقارير، وأتمتة تجميع المستندات بناءً على اختيارات المستخدم.

**س: أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words for Java؟**  
ج: للحصول على وثائق مفصلة وتنزيلات، زر [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**آخر تحديث:** 2026-01-11  
**تم الاختبار مع:** Aspose.Words for Java 24.11 (2026)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}