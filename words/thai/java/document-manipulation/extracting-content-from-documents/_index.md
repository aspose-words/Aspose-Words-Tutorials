---
date: 2026-01-01
description: เรียนรู้วิธีการดึงข้อความด้วย Aspose.Words for Java คู่มือแบบขั้นตอนนี้แสดงเทคนิคการดึงข้อมูลหลายวิธีพร้อมตัวอย่างโค้ดที่พร้อมใช้งาน
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: วิธีดึงข้อความโดยใช้ Aspose.Words สำหรับ Java
url: /th/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการดึงข้อความโดยใช้ Aspose.Words สำหรับ Java

## วิธีการดึงข้อความโดยใช้ Aspose.Words สำหรับ Java

ในโลกของการประมวลผลเอกสาร, **วิธีการดึงข้อความโดยใช้ Aspose.Words** เป็นคำถามที่พบบ่อยสำหรับนักพัฒนา Java ไม่ว่าคุณจะต้องการดึงข้อความธรรมดา, ตาราง, รูปภาพ, หรือองค์ประกอบเฉพาะเช่นบุ๊กมาร์กหรือคอมเมนต์, Aspose.Words สำหรับ Java มี API ที่ครอบคลุมทำให้การทำงานเป็นเรื่องง่าย ในคู่มือนี้เราจะพาผ่านหลายกรณีการดึงข้อมูล, อธิบายว่าทำไมแต่ละวิธีจึงสำคัญ, และให้ตัวอย่างโค้ดที่พร้อมใช้งานที่คุณสามารถนำไปใส่ในโปรเจกต์ของคุณได้

## คำตอบอย่างรวดเร็ว
- **ต้องใช้ไลบรารีอะไร?** Aspose.Words for Java (ดาวน์โหลดจากเว็บไซต์อย่างเป็นทางการ).  
- **ฉันสามารถดึงเฉพาะข้อความธรรมดาได้หรือไม่?** ได้ – ใช้ `Document.getText()` หรือ `DocumentBuilder` พร้อมฟิลด์.  
- **สามารถดึงข้อมูลระหว่างบุ๊กมาร์กได้หรือไม่?** แน่นอน, ใช้ `BookmarkStart`/`BookmarkEnd` กับ `ExtractContentHelper`.  
- **ต้องการไลเซนส์สำหรับการใช้งานจริงหรือไม่?** จำเป็นต้องมีไลเซนส์เชิงพาณิชย์สำหรับการใช้งานที่ไม่ใช่แบบทดลอง.  
- **เวอร์ชัน Java ใดที่รองรับ?** Java 8 และใหม่กว่าเข้ากันได้อย่างเต็มที่.

## ข้อกำหนดเบื้องต้น

1. **Aspose.Words for Java** – ติดตั้งไลบรารีและเพิ่มเข้าไปในโปรเจกต์ของคุณ คุณสามารถดาวน์โหลดได้จาก [here](https://releases.aspose.com/words/java/).  
2. **เอกสารตัวอย่าง** – สำหรับตัวอย่างเราจะใช้ไฟล์ชื่อ `Extract content.docx`. วางไว้ในโฟลเดอร์ที่คุณสามารถอ้างอิงจากโค้ดของคุณ.

## การดึงเนื้อหาระหว่างโหนดระดับบล็อก

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

## การดึงเนื้อหาระหว่างบุ๊กมาร์ก

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

## การดึงเนื้อหาระหว่างช่วงคอมเมนต์

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

## การดึงเนื้อหาระหว่างย่อหน้า

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## การดึงเนื้อหาระหว่างสไตล์ย่อหน้า

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

## การดึงเนื้อหาระหว่างรัน

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

## การดึงเนื้อหาโดยใช้ DocumentVisitor

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## การดึงเนื้อหาโดยใช้ Field

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

## การดึงสารบัญ

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

## การดึงเฉพาะข้อความ

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## การดึงเนื้อหาตามสไตล์

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

## การดึงและพิมพ์ข้อความ

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

## การดึงรูปภาพไปยังไฟล์

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

## สรุป

ขอแสดงความยินดี! ตอนนี้คุณมีชุดเครื่องมือที่แข็งแกร่งสำหรับ **วิธีการดึงข้อความโดยใช้ Aspose.Words** ใน Java ตั้งแต่โหนดระดับบล็อกไปจนถึงบุ๊กมาร์ก, คอมเมนต์, สไตล์, และแม้กระทั่งรูปภาพ, API ให้การควบคุมที่ละเอียดในการดึงข้อมูลจากเอกสาร ใช้โค้ดสแนปเหล่านี้เป็นพื้นฐาน ปรับให้เข้ากับโครงสร้างไฟล์ของคุณเอง และอัตโนมัติกระบวนการดึงข้อมูลในชุดเอกสารขนาดใหญ่.

## คำถามที่พบบ่อย

**ถาม: ฉันจะดึงเนื้อหาจากเอกสารที่มีการป้องกันด้วยรหัสผ่านอย่างไร?**  
**ตอบ:** โหลดเอกสารด้วยคอนสตรัคเตอร์ที่รับรหัสผ่าน: `new Document(path, new LoadOptions("password"))`, จากนั้นเรียกใช้วิธีการดึงข้อมูลใด ๆ ที่แสดงด้านบน.

**ถาม: ฉันสามารถดึงเนื้อหาจากหลายเอกสารในการรันเดียวได้หรือไม่?**  
**ตอบ:** ได้. วนลูปผ่านรายการของเส้นทางไฟล์, สร้าง `Document` สำหรับแต่ละไฟล์, และใช้ตรรกะการดึงข้อมูลเดียวกันภายในลูป.

**ถาม: มีวิธีดึงเฉพาะข้อความที่มองเห็นได้ (ละเว้นข้อความที่ซ่อนหรือโค้ดฟิลด์) หรือไม่?**  
**ตอบ:** ใช้ `doc.getText()` เพื่อดึงข้อความที่มองเห็นได้แบบธรรมดา. หากต้องการควบคุมมากขึ้น, ให้วนผ่านโหนดและกรองโดยใช้ `NodeType.RUN` และ `Run.getFont().getHidden()`.

**ถาม: ฉันสามารถบันทึกเนื้อหาที่ดึงออกเป็นรูปแบบใดได้บ้าง?**  
**ตอบ:** หลังจากดึงข้อมูลแล้ว, คุณสามารถบันทึก `Document` เป็น DOCX, PDF, HTML, TXT หรือรูปแบบใด ๆ ที่ Aspose.Words รองรับผ่าน `doc.save("output.pdf")`.

**ถาม: Aspose.Words รองรับการดึงเนื้อหาจากไฟล์ขนาดใหญ่ (หลายร้อย MB) หรือไม่?**  
**ตอบ:** รองรับ, แต่ควรพิจารณาใช้ `LoadOptions` พร้อม `LoadFormat` และ `MemoryOptimization` เพื่อลดการใช้หน่วยความจำ.

---

**อัปเดตล่าสุด:** 2026-01-01  
**ทดสอบด้วย:** Aspose.Words for Java 24.12  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}