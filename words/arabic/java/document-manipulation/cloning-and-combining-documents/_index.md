---
"description": "تعلّم كيفية استنساخ ودمج المستندات في Aspose.Words لجافا. دليل خطوة بخطوة مع أمثلة على الكود المصدري."
"linktitle": "استنساخ ودمج المستندات"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استنساخ ودمج المستندات في Aspose.Words لـ Java"
"url": "/ar/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استنساخ ودمج المستندات في Aspose.Words لـ Java


## مقدمة إلى استنساخ ودمج المستندات في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية استنساخ المستندات ودمجها باستخدام Aspose.Words في جافا. سنغطي سيناريوهات مختلفة، بما في ذلك استنساخ مستند، وإدراج مستندات في نقاط الاستبدال، والإشارات المرجعية، وأثناء عمليات دمج البريد.

## الخطوة 1: استنساخ مستند

لاستنساخ مستند في Aspose.Words for Java، يمكنك استخدام `deepClone()` الطريقة. إليك مثال بسيط:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

سيقوم هذا الكود بإنشاء استنساخ عميق للمستند الأصلي وحفظه كملف جديد.

## الخطوة 2: إدراج المستندات في نقاط الاستبدال

يمكنك إدراج مستندات عند نقاط استبدال محددة في مستند آخر. إليك الطريقة:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

في هذا المثال، نستخدم `FindReplaceOptions` كائن لتحديد معالج استدعاء للاستبدال. `InsertDocumentAtReplaceHandler` تتعامل الفئة مع منطق الإدراج.

## الخطوة 3: إدراج المستندات في الإشارات المرجعية

لإدراج مستند في إشارة مرجعية محددة في مستند آخر، يمكنك استخدام الكود التالي:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

هنا نجد الإشارة المرجعية حسب الاسم ونستخدم `insertDocument` طريقة لإدراج محتوى `subDoc` المستند في موقع الإشارة المرجعية.

## الخطوة 4: إدراج المستندات أثناء دمج البريد

يمكنك إدراج مستندات أثناء عملية دمج البريد في Aspose.Words لجافا. إليك الطريقة:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

في هذا المثال، قمنا بتعيين استدعاء دمج الحقول باستخدام `InsertDocumentAtMailMergeHandler` الفئة للتعامل مع إدراج المستند المحدد بواسطة الحقل "Document_1".

## خاتمة

يمكن استنساخ المستندات ودمجها في Aspose.Words لجافا باستخدام تقنيات متنوعة. سواءً كنت بحاجة إلى استنساخ مستند، أو إدراج محتوى في نقاط الاستبدال، أو الإشارات المرجعية، أو أثناء دمج البريد، يوفر Aspose.Words ميزات فعّالة للتعامل مع المستندات بسلاسة.

## الأسئلة الشائعة

### كيف يمكنني استنساخ مستند في Aspose.Words لـ Java؟

يمكنك استنساخ مستند في Aspose.Words for Java باستخدام `deepClone()` الطريقة. إليك مثال:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### كيف يمكنني إدراج مستند في الإشارة المرجعية؟

لإدراج مستند في إشارة مرجعية في Aspose.Words for Java، يمكنك العثور على الإشارة المرجعية حسب الاسم ثم استخدام `insertDocument` طريقة لإدراج المحتوى. إليك مثال:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### كيف أقوم بإدراج المستندات أثناء دمج البريد في Aspose.Words لـ Java؟

يمكنك إدراج مستندات أثناء دمج البريد في Aspose.Words لجافا عن طريق تعيين استدعاء دمج الحقول وتحديد المستند المراد إدراجه. إليك مثال:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

في هذا المثال، `InsertDocumentAtMailMergeHandler` تتعامل الفئة مع منطق الإدراج لـ "DocumentField" أثناء دمج البريد.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}