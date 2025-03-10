---
title: การใช้ Structured Document Tags (SDT) ใน Aspose.Words สำหรับ Java
linktitle: การใช้แท็กเอกสารที่มีโครงสร้าง (SDT)
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีใช้ Structured Document Tags (SDT) ใน Aspose.Words สำหรับ Java ด้วยคู่มือฉบับสมบูรณ์นี้ สร้าง แก้ไข และเชื่อมโยง SDT กับข้อมูล XML ที่กำหนดเอง
weight: 19
url: /th/java/document-manipulation/using-structured-document-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การใช้ Structured Document Tags (SDT) ใน Aspose.Words สำหรับ Java


## บทนำเกี่ยวกับการใช้ Structured Document Tags (SDT) ใน Aspose.Words สำหรับ Java

Structured Document Tags (SDT) เป็นฟีเจอร์อันทรงพลังใน Aspose.Words สำหรับ Java ที่ช่วยให้คุณสร้างและจัดการเนื้อหาที่มีโครงสร้างภายในเอกสารของคุณได้ ในคู่มือฉบับสมบูรณ์นี้ เราจะแนะนำคุณเกี่ยวกับแง่มุมต่างๆ ของการใช้ SDT ใน Aspose.Words สำหรับ Java ไม่ว่าคุณจะเป็นมือใหม่หรือผู้พัฒนาที่มีประสบการณ์ คุณจะพบข้อมูลเชิงลึกอันมีค่าและตัวอย่างเชิงปฏิบัติในบทความนี้

## การเริ่มต้น

ก่อนที่เราจะลงรายละเอียด เรามาตั้งค่าสภาพแวดล้อมและสร้าง SDT พื้นฐานกันก่อน ในส่วนนี้ เราจะครอบคลุมหัวข้อต่อไปนี้:

- การสร้างเอกสารใหม่
- การเพิ่มแท็กเอกสารที่มีโครงสร้าง
- การบันทึกเอกสาร

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// สร้างแท็กเอกสารที่มีโครงสร้างประเภท CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// บันทึกเอกสาร
doc.save("WorkingWithSDT.docx");
```

## การตรวจสอบสถานะปัจจุบันของกล่องกาเครื่องหมาย SDT

เมื่อคุณเพิ่ม SDT ของกล่องกาเครื่องหมายลงในเอกสารแล้ว คุณอาจต้องการตรวจสอบสถานะปัจจุบันของเอกสารด้วยโปรแกรม ซึ่งอาจมีประโยชน์เมื่อคุณต้องตรวจสอบอินพุตของผู้ใช้หรือดำเนินการเฉพาะตามสถานะของกล่องกาเครื่องหมาย

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // ช่องกาเครื่องหมายถูกทำเครื่องหมายแล้ว
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## การปรับเปลี่ยนการควบคุมเนื้อหา

ในส่วนนี้ เราจะมาดูวิธีการปรับเปลี่ยนการควบคุมเนื้อหาภายในเอกสารของคุณ เราจะครอบคลุมการควบคุมเนื้อหาสามประเภท ได้แก่ ข้อความธรรมดา รายการดรอปดาวน์ และรูปภาพ

### การปรับเปลี่ยนการควบคุมเนื้อหาข้อความธรรมดา

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // ล้างเนื้อหาที่มีอยู่
    sdtPlainText.removeAllChildren();

    // เพิ่มข้อความใหม่
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### การแก้ไขการควบคุมเนื้อหารายการแบบดรอปดาวน์

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // เลือกรายการที่สองจากรายการ
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### การแก้ไขการควบคุมเนื้อหารูปภาพ

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // เปลี่ยนรูปภาพใหม่
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## การสร้างตัวควบคุมเนื้อหา ComboBox

ComboBox Content Control ช่วยให้ผู้ใช้เลือกจากรายการตัวเลือกที่กำหนดไว้ล่วงหน้า มาสร้างรายการตัวเลือกในเอกสารของเรากัน

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## การทำงานกับการควบคุมเนื้อหาข้อความที่มีรูปแบบหลากหลาย

การควบคุมเนื้อหาข้อความแบบ Rich Text เหมาะอย่างยิ่งสำหรับการเพิ่มข้อความที่มีรูปแบบลงในเอกสารของคุณ มาสร้างและกำหนดเนื้อหากันเลย

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## การตั้งค่ารูปแบบการควบคุมเนื้อหา

คุณสามารถใช้รูปแบบกับตัวควบคุมเนื้อหาเพื่อปรับปรุงรูปลักษณ์ของเอกสารของคุณ มาดูวิธีการตั้งค่ารูปแบบของตัวควบคุมเนื้อหากัน

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// ใช้รูปแบบที่กำหนดเอง
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## การผูก SDT กับข้อมูล XML ที่กำหนดเอง

ในบางสถานการณ์ คุณอาจต้องผูก SDT กับข้อมูล XML ที่กำหนดเองเพื่อสร้างเนื้อหาแบบไดนามิก มาลองดูวิธีการดำเนินการนี้กัน

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## การสร้างตารางที่มีส่วนที่ซ้ำกันซึ่งแมปกับข้อมูล XML ที่กำหนดเอง

ตารางที่มีส่วนที่ซ้ำกันอาจมีประโยชน์อย่างยิ่งในการนำเสนอข้อมูลที่มีโครงสร้าง มาสร้างตารางดังกล่าวและจับคู่กับข้อมูล XML ที่กำหนดเองกัน

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## การทำงานกับแท็กเอกสารที่มีโครงสร้างหลายส่วน

แท็กเอกสารที่มีโครงสร้างสามารถครอบคลุมหลายส่วนในเอกสารเดียวได้ ในส่วนนี้ เราจะมาสำรวจวิธีการทำงานกับ SDT หลายส่วน

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## บทสรุป

แท็กเอกสารที่มีโครงสร้างใน Aspose.Words สำหรับ Java มอบวิธีที่หลากหลายในการจัดการและจัดรูปแบบเนื้อหาภายในเอกสารของคุณ ไม่ว่าคุณจะต้องสร้างเทมเพลต แบบฟอร์ม หรือเอกสารแบบไดนามิก SDT ก็มอบความยืดหยุ่นและการควบคุมที่คุณต้องการได้ ด้วยการทำตามตัวอย่างและแนวทางที่ให้ไว้ในบทความนี้ คุณสามารถใช้ประโยชน์จากความสามารถของ SDT เพื่อปรับปรุงงานประมวลผลเอกสารของคุณได้

## คำถามที่พบบ่อย

### วัตถุประสงค์ของแท็กเอกสารที่มีโครงสร้าง (SDT) คืออะไร

แท็กเอกสารที่มีโครงสร้าง (SDT) มีวัตถุประสงค์เพื่อจัดระเบียบและจัดรูปแบบเนื้อหาภายในเอกสาร ทำให้การสร้างเทมเพลต แบบฟอร์ม และเอกสารที่มีโครงสร้างเป็นเรื่องง่ายยิ่งขึ้น

### ฉันจะตรวจสอบสถานะปัจจุบันของ Checkbox SDT ได้อย่างไร

 คุณสามารถตรวจสอบสถานะปัจจุบันของ Checkbox SDT ได้โดยใช้`setChecked` วิธีการดังที่แสดงไว้ในบทความ

### ฉันสามารถนำสไตล์ไปใช้กับการควบคุมเนื้อหาได้หรือไม่

ใช่ คุณสามารถใช้รูปแบบกับตัวควบคุมเนื้อหาเพื่อปรับแต่งลักษณะที่ปรากฏในเอกสารได้

### สามารถผูก SDT กับข้อมูล XML แบบกำหนดเองได้หรือไม่

ใช่ คุณสามารถผูก SDT กับข้อมูล XML ที่กำหนดเองได้ ช่วยให้สร้างเนื้อหาแบบไดนามิกและทำการแมปข้อมูลได้

### การทำซ้ำส่วนต่างๆ ใน SDT คืออะไร

การทำซ้ำส่วนต่างๆ ใน SDT ช่วยให้คุณสามารถสร้างตารางที่มีข้อมูลแบบไดนามิก ซึ่งสามารถทำซ้ำแถวต่างๆ ได้โดยอิงตามข้อมูล XML ที่แมปไว้
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
