---
"description": "เรียนรู้วิธีแยกเนื้อหาจากเอกสารอย่างง่ายดายโดยใช้ Aspose.Words สำหรับ Java คำแนะนำทีละขั้นตอนและตัวอย่างโค้ดของเราจะทำให้กระบวนการนี้ง่ายขึ้น"
"linktitle": "การดึงเนื้อหาจากเอกสาร"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การแยกเนื้อหาจากเอกสารใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-manipulation/extracting-content-from-documents/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การแยกเนื้อหาจากเอกสารใน Aspose.Words สำหรับ Java


## บทนำสู่การแยกเนื้อหาจากเอกสารใน Aspose.Words สำหรับ Java

ในโลกของการประมวลผลเอกสาร การดึงเนื้อหาจากเอกสารถือเป็นข้อกำหนดทั่วไป ไม่ว่าคุณจะต้องดึงข้อความ ตาราง รูปภาพ หรือองค์ประกอบเฉพาะของเอกสาร Aspose.Words สำหรับ Java ก็มีเครื่องมืออันทรงพลังที่จะทำให้ภารกิจนี้เป็นเรื่องง่าย ในคู่มือฉบับสมบูรณ์นี้ เราจะแนะนำคุณเกี่ยวกับกระบวนการดึงเนื้อหาจากเอกสารโดยใช้ Aspose.Words สำหรับ Java 

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มกระบวนการสกัด ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

1. Aspose.Words สำหรับ Java: คุณควรติดตั้งและตั้งค่า Aspose.Words สำหรับ Java ในสภาพแวดล้อมการพัฒนา Java ของคุณ คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-aspose.com/words/java/).

2. เอกสารสำหรับแยกเนื้อหา: สำหรับคู่มือนี้ เราจะใช้เอกสารตัวอย่างชื่อ "Extract content.docx" ตรวจสอบให้แน่ใจว่าคุณมีเอกสารที่คล้ายกันพร้อมสำหรับการแยกเนื้อหา

## การแยกเนื้อหาระหว่างโหนดระดับบล็อก

```java
// ตัวอย่างโค้ด Java สำหรับการแยกเนื้อหาระหว่างโหนดระดับบล็อก
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

## การแยกเนื้อหาออกจากบุ๊กมาร์ก

```java
// ตัวอย่างโค้ด Java สำหรับการแยกเนื้อหาระหว่างบุ๊กมาร์ก
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

## การแยกเนื้อหาระหว่างช่วงความคิดเห็น

```java
// ตัวอย่างโค้ด Java สำหรับการแยกเนื้อหาระหว่างช่วงความคิดเห็น
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

## การสกัดเนื้อหาระหว่างย่อหน้า

```java
// ตัวอย่างโค้ด Java สำหรับการแยกเนื้อหาระหว่างย่อหน้า
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## การแยกเนื้อหาออกจากรูปแบบย่อหน้า

```java
// ตัวอย่างโค้ด Java สำหรับการแยกเนื้อหาระหว่างรูปแบบย่อหน้า
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## การแยกเนื้อหาระหว่างการทำงาน

```java
// ตัวอย่างโค้ด Java สำหรับการแยกเนื้อหาระหว่างการรัน
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## การแยกเนื้อหาโดยใช้ DocumentVisitor

```java
// ตัวอย่างโค้ด Java สำหรับการแยกเนื้อหาโดยใช้ DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## การแยกเนื้อหาโดยใช้ฟิลด์

```java
// ตัวอย่างโค้ด Java สำหรับการแยกเนื้อหาโดยใช้ Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## การดึงข้อมูลสารบัญ

```java
// ตัวอย่างโค้ด Java สำหรับการแยกสารบัญ
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

## การแยกข้อความเท่านั้น

```java
// ตัวอย่างโค้ด Java สำหรับการแยกข้อความเท่านั้น
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## การสกัดเนื้อหาตามรูปแบบ

```java
// ตัวอย่างโค้ด Java สำหรับการแยกเนื้อหาตามรูปแบบ
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

## การแยกและการพิมพ์ข้อความ

```java
// ตัวอย่างโค้ด Java สำหรับการแยกและพิมพ์ข้อความ
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## การแยกภาพไปยังไฟล์

```java
// ตัวอย่างโค้ด Java สำหรับการแยกภาพไปยังไฟล์
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

## บทสรุป

ขอแสดงความยินดี! คุณได้เรียนรู้วิธีการแยกเนื้อหาจากเอกสารโดยใช้ Aspose.Words สำหรับ Java แล้ว คู่มือนี้ครอบคลุมเทคนิคการแยกข้อมูลต่างๆ รวมถึงเนื้อหาระหว่างโหนดระดับบล็อก บุ๊กมาร์ก ช่วงคำอธิบาย ย่อหน้า และอื่นๆ อีกมากมาย ตอนนี้คุณพร้อมที่จะจัดการการแยกเนื้อหาเอกสารอย่างมีประสิทธิภาพในแอปพลิเคชัน Java ของคุณแล้ว

## คำถามที่พบบ่อย

### ฉันจะดึงเนื้อหาจากส่วนต่างๆ ของเอกสารที่เจาะจงได้อย่างไร

ในการแยกเนื้อหาจากส่วนต่างๆ ของเอกสารที่เจาะจง คุณสามารถระบุจุดเริ่มต้นและจุดสิ้นสุดของส่วนต่างๆ และใช้เมธอด Aspose.Words for Java ที่เหมาะสมเพื่อแยกเนื้อหาระหว่างส่วนต่างๆ

### ฉันสามารถดึงเนื้อหาจากเอกสารที่ป้องกันด้วยรหัสผ่านได้หรือไม่

ใช่ Aspose.Words สำหรับ Java มีฟังก์ชันสำหรับดึงเนื้อหาจากเอกสารที่ป้องกันด้วยรหัสผ่าน คุณสามารถระบุรหัสผ่านเมื่อเปิดเอกสารโดยใช้ `Document` ตัวสร้างคลาส

### ฉันจะแยกเนื้อหาและบันทึกในรูปแบบต่างๆ เช่น ข้อความธรรมดา หรือ HTML ได้อย่างไร

คุณสามารถแยกเนื้อหาจากเอกสารและบันทึกในรูปแบบต่างๆ ได้โดยใช้ Aspose.Words สำหรับ Java หลังจากแยกเนื้อหาแล้ว คุณสามารถใช้ `Document` วิธีการคลาสที่จะบันทึกในรูปแบบเช่นข้อความธรรมดา, HTML หรืออื่น ๆ

### มีวิธีแยกเนื้อหาจากองค์ประกอบเอกสารเฉพาะ เช่น ตารางหรือรูปภาพหรือไม่

ใช่ คุณสามารถแยกเนื้อหาจากองค์ประกอบเอกสารเฉพาะ เช่น ตารางหรือรูปภาพได้โดยใช้ Aspose.Words สำหรับ Java ระบุองค์ประกอบที่คุณต้องการแยก จากนั้นใช้เมธอดที่เหมาะสมเพื่อแยกเนื้อหา

### ฉันจะทำให้กระบวนการแยกเนื้อหาอัตโนมัติในแอปพลิเคชัน Java ของฉันได้อย่างไร

หากต้องการทำให้กระบวนการแยกเนื้อหาในแอปพลิเคชัน Java เป็นแบบอัตโนมัติ คุณสามารถสร้างโค้ดที่กำหนดเองตามเทคนิคที่อธิบายไว้ในคู่มือนี้ นอกจากนี้ คุณยังสามารถใช้ตรรกะเพื่อวนซ้ำผ่านเอกสารหลายฉบับและแยกเนื้อหาตามต้องการได้อีกด้วย


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}