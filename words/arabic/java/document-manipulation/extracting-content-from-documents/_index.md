---
date: 2026-01-01
description: تعلم كيفية استخراج النص باستخدام Aspose.Words for Java. يوضح هذا الدليل
  خطوة بخطوة تقنيات استخراج متعددة مع عينات شفرة جاهزة للتنفيذ.
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: كيفية استخراج النص باستخدام Aspose.Words للـ Java
url: /ar/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استخراج النص باستخدام Aspose.Words for Java

## كيفية استخراج النص باستخدام Aspose.Words for Java

في عالم معالجة المستندات، **كيفية استخراج النص باستخدام Aspose.Words** هو سؤال متكرر لمطوري Java. سواء كنت تحتاج إلى سحب النص العادي، الجداول، الصور، أو عناصر محددة مثل الإشارات المرجعية أو التعليقات، فإن Aspose.Words for Java يقدم واجهة برمجة تطبيقات غنية تجعل المهمة مباشرة. في هذا الدليل سنستعرض عشرات سيناريوهات الاستخراج، نشرح لماذا كل نهج مهم، ونوفر عينات شفرة جاهزة يمكنك إدراجها في مشروعك.

## إجابات سريعة
- **ما المكتبة التي أحتاجها؟** Aspose.Words for Java (قم بتنزيلها من الموقع الرسمي).  
- **هل يمكن استخراج النص العادي فقط؟** نعم – استخدم `Document.getText()` أو `DocumentBuilder` مع الحقول.  
- **هل يمكن استخراج النص بين الإشارات المرجعية؟** بالتأكيد، استخدم `BookmarkStart`/`BookmarkEnd` مع `ExtractContentHelper`.  
- **هل أحتاج إلى ترخيص للإنتاج؟** الترخيص التجاري مطلوب للاستخدام غير التجريبي.  
- **ما إصدارات Java المدعومة؟** Java 8 وما فوق متوافقة بالكامل.

## المتطلبات المسبقة

1. **Aspose.Words for Java** – ثبّت المكتبة وأضفها إلى مشروعك. يمكنك تنزيلها من [here](https://releases.aspose.com/words/java/).  
2. **مستند تجريبي** – للأمثلة سنستخدم ملفًا باسم `Extract content.docx`. ضعّه في مجلد يمكنك الإشارة إليه من الشفرة.

## استخراج المحتوى بين العقد من المستوى الكتلي

```java
// Java code sample for extracting content between block-level nodes
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getLastSection().getChild(NodeType.PARAGRAPH, 2, true);
Table endTable = (Table) doc.getLastSection().getChild(NodeType.TABLE, 0, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endTable, true);
Collections.reverse(extractedNodes);
while (extractedNodes.size() > 0) {
    endTable.getParentNode().insertAfter((Node) extractedNodes.get(0), endTable);
    extractedNodes.remove(0);
}
doc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBlockLevelNodes.docx");
```

## استخراج المحتوى بين الإشارات المرجعية

```java
// Java code sample for extracting content between bookmarks
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("Bookmark1");
BookmarkStart bookmarkStart = bookmark.getBookmarkStart();
BookmarkEnd bookmarkEnd = bookmark.getBookmarkEnd();
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.IncludingBookmark.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.WithoutBookmark.docx");
```

## استخراج المحتوى بين نطاقات التعليقات

```java
// Java code sample for extracting content between comment ranges
Document doc = new Document("Your Directory Path" + "Extract content.docx");
CommentRangeStart commentStart = (CommentRangeStart) doc.getChild(NodeType.COMMENT_RANGE_START, 0, true);
CommentRangeEnd commentEnd = (CommentRangeEnd) doc.getChild(NodeType.COMMENT_RANGE_END, 0, true);
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.IncludingComment.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.WithoutComment.docx");
```

## استخراج المحتوى بين الفقرات

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## استخراج المحتوى بين أنماط الفقرات

```java
// Java code sample for extracting content between paragraph styles
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## استخراج المحتوى بين القطع النصية (Runs)

```java
// Java code sample for extracting content between runs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## استخراج المحتوى باستخدام DocumentVisitor

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## استخراج المحتوى باستخدام Field

```java
// Java code sample for extracting content using Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## استخراج جدول المحتويات

```java
// Java code sample for extracting table of contents
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
for (Field field : doc.getRange().getFields()) {
    if (field.getType() == FieldType.FIELD_HYPERLINK) {
        FieldHyperlink hyperlink = (FieldHyperlink) field;
        if (hyperlink.getSubAddress() != null && hyperlink.getSubAddress().startsWith("_Toc")) {
            Paragraph tocItem = (Paragraph) field.getStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(tocItem.toString().trim());
            System.out.println("------------------");
            Bookmark bm = doc.getRange().getBookmarks().get(hyperlink.getSubAddress());
            Paragraph pointer = (Paragraph) bm.getBookmarkStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(pointer.toString());
        }
    }
}
```

## استخراج النص فقط

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## استخراج المحتوى بناءً على الأنماط

```java
// Java code sample for extracting content based on styles
Document doc = new Document("Your Directory Path" + "Styles.docx");
final String PARA_STYLE = "Heading 1";
final String RUN_STYLE = "Intense Emphasis";
ArrayList<Paragraph> paragraphs = paragraphsByStyleName(doc, PARA_STYLE);
System.out.println("Paragraphs with \"{paraStyle}\" styles ({paragraphs.Count}):");
for (Paragraph paragraph : paragraphs)
    System.out.println(paragraph.toString(SaveFormat.TEXT));
ArrayList<Run> runs = runsByStyleName(doc, RUN_STYLE);
System.out.println("\nRuns with \"{runStyle}\" styles ({runs.Count}):");
for (Run run : runs)
    System.out.println(run.getRange().getText());
}

public ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}

public ArrayList<Run> runsByStyleName(Document doc, String styleName) {
    ArrayList<Run> runsWithStyle = new ArrayList<Run>();
    NodeCollection runs = doc.getChildNodes(NodeType.RUN, true);
    for (Run run : (Iterable<Run>) runs) {
        if (run.getFont().getStyle().getName().equals(styleName))
            runsWithStyle.add(run);
    }
    return runsWithStyle;
}
```

## استخراج وطباعة النص

```java
// Java code sample for extracting and printing text
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## استخراج الصور إلى ملفات

```java
// Java code sample for extracting images to files
Document doc = new Document("Your Directory Path" + "Images.docx");
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
int imageIndex = 0;
for (Shape shape : (Iterable<Shape>) shapes) {
    if (shape.hasImage()) {
        String imageFileName = MessageFormat.format("Image.ExportImages.{0}_{1}",
                imageIndex, FileFormatUtil.imageTypeToExtension(shape.getImageData().getImageType()));
        shape.getImageData().save("Your Directory Path" + imageFileName);
        imageIndex++;
    }
}
```

## الخلاصة

تهانينا! لديك الآن مجموعة أدوات قوية لـ **كيفية استخراج النص باستخدام Aspose.Words** في Java. من العقد من المستوى الكتلي إلى الإشارات المرجعية، التعليقات، الأنماط، وحتى الصور، توفر API تحكمًا دقيقًا فيما تستخرجه من المستند. استخدم هذه القطع كقاعدة، عدّلها لتناسب هياكل ملفاتك الخاصة، وقم بأتمتة عملية الاستخراج عبر مجموعات مستندات كبيرة.

## الأسئلة المتكررة

**س: كيف يمكن استخراج المحتوى من مستند محمي بكلمة مرور؟**  
ج: حمّل المستند باستخدام مُنشئ كلمة المرور: `new Document(path, new LoadOptions("password"))`، ثم نفّذ أي من طرق الاستخراج المعروضة أعلاه.

**س: هل يمكن استخراج المحتوى من عدة مستندات في تشغيل واحد؟**  
ج: نعم. قم بالتكرار عبر قائمة مسارات الملفات، أنشئ `Document` لكل منها، وطبق نفس منطق الاستخراج داخل الحلقة.

**س: هل هناك طريقة لاستخراج النص الظاهر فقط (متجاهلًا النص المخفي أو أكواد الحقول)؟**  
ج: استخدم `doc.getText()` للنص الظاهر البسيط. للحصول على تحكم أكبر، قم بالتكرار عبر العقد وصَفِّها حسب `NodeType.RUN` و `Run.getFont().getHidden()`.

**س: ما الصيغ التي يمكنني حفظ المحتوى المستخرج إليها؟**  
ج: بعد الاستخراج، يمكنك حفظ `Document` كـ DOCX، PDF، HTML، TXT، أو أي صيغة يدعمها Aspose.Words عبر `doc.save("output.pdf")`.

**س: هل يدعم Aspose.Words استخراج المحتوى من ملفات كبيرة (مئات الميغابايت)؟**  
ج: نعم، لكن يُفضَّل استخدام `LoadOptions` مع `LoadFormat` و `MemoryOptimization` لتقليل استهلاك الذاكرة.

---

**آخر تحديث:** 2026-01-01  
**تم الاختبار مع:** Aspose.Words for Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}