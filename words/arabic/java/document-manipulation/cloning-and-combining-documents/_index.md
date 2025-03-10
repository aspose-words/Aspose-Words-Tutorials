---
title: استنساخ ودمج المستندات في Aspose.Words لـ Java
linktitle: استنساخ ودمج المستندات
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية استنساخ المستندات ودمجها في Aspose.Words for Java. دليل خطوة بخطوة مع أمثلة على أكواد المصدر.
weight: 27
url: /ar/java/document-manipulation/cloning-and-combining-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استنساخ ودمج المستندات في Aspose.Words لـ Java


## مقدمة حول استنساخ ودمج المستندات في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية استنساخ المستندات ودمجها باستخدام Aspose.Words for Java. وسنغطي سيناريوهات مختلفة، بما في ذلك استنساخ مستند، وإدراج مستندات في نقاط الاستبدال، والإشارات المرجعية، وأثناء عمليات دمج البريد.

## الخطوة 1: استنساخ مستند

 لاستنساخ مستند في Aspose.Words for Java، يمكنك استخدام`deepClone()` الطريقة. فيما يلي مثال بسيط:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

سيقوم هذا الكود بإنشاء نسخة طبق الأصل من المستند الأصلي وحفظه كملف جديد.

## الخطوة 2: إدخال المستندات في نقاط الاستبدال

يمكنك إدراج مستندات عند نقاط استبدال محددة في مستند آخر. وإليك كيفية القيام بذلك:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

 في هذا المثال، نستخدم`FindReplaceOptions` كائن لتحديد معالج استدعاء للاستبدال.`InsertDocumentAtReplaceHandler` تتعامل الفئة مع منطق الإدراج.

## الخطوة 3: إدراج المستندات في الإشارات المرجعية

لإدراج مستند عند إشارة مرجعية محددة في مستند آخر، يمكنك استخدام الكود التالي:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

 هنا نجد الإشارة المرجعية بالاسم ونستخدم`insertDocument` طريقة لإدراج محتوى`subDoc` المستند في موقع الإشارة المرجعية.

## الخطوة 4: إدراج المستندات أثناء دمج البريد

يمكنك إدراج المستندات أثناء عملية دمج البريد في Aspose.Words for Java. وإليك الطريقة:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

 في هذا المثال، قمنا بتعيين معاودة الاتصال لدمج الحقول باستخدام`InsertDocumentAtMailMergeHandler` الفئة التي تتعامل مع إدراج المستند المحدد بواسطة الحقل "Document_1".

## خاتمة

يمكن استنساخ المستندات ودمجها في Aspose.Words for Java باستخدام تقنيات مختلفة. سواء كنت بحاجة إلى استنساخ مستند أو إدراج محتوى عند نقاط الاستبدال أو الإشارات المرجعية أو أثناء دمج البريد، يوفر Aspose.Words ميزات قوية للتعامل مع المستندات بسلاسة.

## الأسئلة الشائعة

### كيف يمكنني استنساخ مستند في Aspose.Words لـ Java؟

 يمكنك استنساخ مستند في Aspose.Words for Java باستخدام`deepClone()` الطريقة. فيما يلي مثال:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### كيف يمكنني إدراج مستند في الإشارة المرجعية؟

 لإدراج مستند في إشارة مرجعية في Aspose.Words for Java، يمكنك العثور على الإشارة المرجعية حسب الاسم ثم استخدام`insertDocument` طريقة لإدراج المحتوى. إليك مثال:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### كيف أقوم بإدراج المستندات أثناء دمج البريد في Aspose.Words لـ Java؟

يمكنك إدراج المستندات أثناء دمج البريد في Aspose.Words for Java عن طريق تعيين معاودة الاتصال بدمج الحقول وتحديد المستند المراد إدراجه. فيما يلي مثال:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

 في هذا المثال،`InsertDocumentAtMailMergeHandler`تعمل الفئة على معالجة منطق الإدراج لـ "DocumentField" أثناء دمج البريد.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
