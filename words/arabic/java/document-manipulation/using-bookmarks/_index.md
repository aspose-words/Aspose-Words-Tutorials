---
title: استخدام الإشارات المرجعية في Aspose.Words للغة Java
linktitle: استخدام الإشارات المرجعية
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: قم بتحسين معالجة المستندات باستخدام Aspose.Words for Java. تعلم كيفية استخدام الإشارات المرجعية للتنقل بين المحتويات ومعالجتها بكفاءة في هذا الدليل خطوة بخطوة.
weight: 17
url: /ar/java/document-manipulation/using-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدام الإشارات المرجعية في Aspose.Words للغة Java


## مقدمة حول استخدام الإشارات المرجعية في Aspose.Words للغة Java

تُعد العلامات المرجعية ميزة قوية في Aspose.Words for Java تتيح لك وضع علامات على أجزاء معينة من المستند ومعالجتها. في هذا الدليل التفصيلي، سنستكشف كيفية استخدام العلامات المرجعية في Aspose.Words for Java لتحسين معالجة المستندات. 

## الخطوة 1: إنشاء إشارة مرجعية

لإنشاء إشارة مرجعية، اتبع الخطوات التالية:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// ابدأ الإشارة المرجعية
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

//إنهاء الإشارة المرجعية
builder.endBookmark("My Bookmark");
```

## الخطوة 2: الوصول إلى الإشارات المرجعية

يمكنك الوصول إلى الإشارات المرجعية في مستند باستخدام فهرسها أو اسمها. وإليك الطريقة:

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// حسب الفهرس:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// حسب الاسم:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

## الخطوة 3: تحديث بيانات الإشارة المرجعية

لتحديث بيانات الإشارة المرجعية، استخدم الكود التالي:

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

## الخطوة 4: العمل مع النص المُضاف إليه إشارة مرجعية

يمكنك نسخ النص الذي قمت بإضافته إلى مستند آخر. وإليك الطريقة:

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## الخطوة 5: إظهار وإخفاء الإشارات المرجعية

يمكنك إظهار أو إخفاء الإشارات المرجعية في المستند. إليك مثال على ذلك:

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

## الخطوة 6: فك تشابك علامات الصفوف

يتيح لك فك تشابك علامات الصفوف العمل معها بشكل أكثر فعالية:

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## خاتمة

إن استخدام الإشارات المرجعية في Aspose.Words for Java يمكن أن يبسط مهام معالجة المستندات إلى حد كبير. سواء كنت بحاجة إلى التنقل أو استخراج أو معالجة المحتوى، فإن الإشارات المرجعية توفر آلية قوية للقيام بذلك بكفاءة.

## الأسئلة الشائعة

### كيف أقوم بإنشاء إشارة مرجعية في خلية جدول؟

 لإنشاء إشارة مرجعية في خلية جدول، استخدم`DocumentBuilder` الفصل وبدء وإنهاء الإشارة المرجعية داخل الخلية.

### هل يمكنني نسخ الإشارة المرجعية إلى مستند آخر؟

 نعم، يمكنك نسخ إشارة مرجعية إلى مستند آخر باستخدام`NodeImporter` الفئة للتأكد من الحفاظ على التنسيق.

### كيف يمكنني حذف صف من خلال الإشارة المرجعية الخاصة به؟

بإمكانك حذف صف من خلال الإشارة المرجعية الخاصة به عن طريق العثور أولاً على الصف الذي تم وضع الإشارة المرجعية عليه ثم إزالته من المستند.

### ما هي بعض حالات الاستخدام الشائعة للإشارات المرجعية؟

تُستخدم العلامات المرجعية عادةً لإنشاء جدول المحتويات، واستخراج محتوى معين، وأتمتة عمليات إنشاء المستندات.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words for Java؟

 للحصول على وثائق مفصلة والتنزيلات، قم بزيارة[توثيق Aspose.Words للغة Java](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
