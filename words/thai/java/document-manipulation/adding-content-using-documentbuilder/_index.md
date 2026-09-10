---
date: 2026-01-01
description: เรียนรู้วิธีสร้างฟิลด์ฟอร์มและเพิ่มข้อความ ตาราง รูปภาพ ไฮเปอร์ลิงก์
  และอื่น ๆ ด้วย Aspose.Words for Java DocumentBuilder คู่มือขั้นตอนต่อขั้นสำหรับนักพัฒนา
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words สำหรับ
  Java
url: /th/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java

## แนะนำการเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java

ในคู่มือขั้นตอนนี้ คุณจะ **สร้างฟิลด์ฟอร์ม** และเพิ่มเนื้อหาต่าง ๆ — ข้อความ ตาราง เส้นแนวนอน HTML ลิงก์รูปภาพ และอื่น ๆ — ลงในเอกสาร Word ด้วย Aspose.Words for Java ไม่ว่าคุณจะสร้างรายงาน เทมเพลตสัญญา หรือฟอร์มโต้ตอบ `DocumentBuilder` จะให้การควบคุมระดับละเอียดต่อทุกองค์ประกอบ มาดูกันเลย!

## คำตอบสั้น
- **จะสร้างฟิลด์ฟอร์มอย่างไร?** ใช้ `insertTextInput`, `insertCheckBox` หรือ `insertComboBox` บน `DocumentBuilder`
- **เมธอดใดใช้เพิ่มข้อความธรรมดา?** เรียก `builder.write("Your text")` หรือ `builder.writeln("Your text")`
- **สามารถแทรกเส้นแนวนอนได้หรือไม่?** ได้ — `builder.insertHorizontalRule()` จะเพิ่มเส้นแบ่ง
- **จะแทรก HTML อย่างไร?** ใช้ `builder.insertHtml("<p>HTML content</p>")`
- **จะแทรกรูปภาพแบบอินไลน์อย่างไร?** `builder.insertImage("path/to/image.png")` จะวางรูปภาพในกระแสข้อความ

## DocumentBuilder คืออะไรและทำไมต้องใช้เพื่อสร้างฟิลด์ฟอร์ม?

`DocumentBuilder` คือ API แบบ fluent ของ Aspose.Words สำหรับสร้างและแก้ไขเอกสาร Word ด้วยโปรแกรม มันซ่อนโครงสร้าง OpenXML ระดับต่ำไว้ ทำให้คุณโฟกัสที่ *สิ่งที่* ต้องการเพิ่ม — เช่น **ฟิลด์ฟอร์ม** — แทนที่จะกังวลว่า XML จะเป็นอย่างไร เหมาะอย่างยิ่งสำหรับการสร้างฟอร์มไดนามิก สัญญา หรือเอกสารใด ๆ ที่ต้องการการโต้ตอบจากผู้ใช้

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Aspose.Words for Java ในโปรเจกต์ของคุณแล้ว สามารถดาวน์โหลดได้จาก [here](https://releases.aspose.com/words/java/)

## การเพิ่มข้อความ (how to add text)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## การเพิ่มตาราง

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## การเพิ่มเส้นแนวนอน (add horizontal rule)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## การเพิ่มฟิลด์ฟอร์ม (create form fields)

### ฟิลด์ฟอร์มแบบ Text Input

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### ฟิลด์ฟอร์มแบบ Check Box

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### ฟิลด์ฟอร์มแบบ Combo Box

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## การเพิ่ม HTML (insert html word)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## การเพิ่มไฮเปอร์ลิงก์ (how to add hyperlink)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## การเพิ่มสารบัญ

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## การเพิ่มรูปภาพ

### รูปภาพแบบอินไลน์ (insert inline image)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### รูปภาพแบบลอย

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## การเพิ่มย่อหน้า

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## การย้ายเคอร์เซอร์ (Step 10)

คุณสามารถควบคุมตำแหน่งเคอร์เซอร์ภายในเอกสารได้ด้วยเมธอดเช่น `moveToParagraph`, `moveToCell` เป็นต้น

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

เหล่านี้เป็นการดำเนินการทั่วไปที่คุณสามารถทำได้ด้วย `DocumentBuilder` ของ Aspose.Words for Java สำรวจเอกสารของไลบรารีเพื่อดูฟีเจอร์ขั้นสูงและตัวเลือกการปรับแต่งเพิ่มเติม ขอให้สนุกกับการสร้างเอกสาร!

## สรุป

ในคู่มือฉบับครบถ้วนนี้ เราได้แสดงวิธี **สร้างฟิลด์ฟอร์ม** และเพิ่มประเภทเนื้อหาต่าง ๆ — ข้อความ ตาราง เส้นแนวนอน HTML ไฮเปอร์ลิงก์ สารบัญ รูปภาพ ย่อหน้าที่จัดรูปแบบ และการนำทางเคอร์เซอร์ — ด้วย `DocumentBuilder` ของ Aspose.Words for Java ตอนนี้คุณมีพื้นฐานที่มั่นคงสำหรับการสร้างเอกสาร Word ไดนามิกและโต้ตอบได้ด้วยโปรแกรม

## คำถามที่พบบ่อย

### Q: Aspose.Words for Java คืออะไร?

A: Aspose.Words for Java เป็นไลบรารี Java ที่ช่วยให้นักพัฒนาสร้าง แก้ไข และจัดการเอกสาร Microsoft Word ด้วยโปรแกรม มันให้ฟีเจอร์หลากหลายสำหรับการสร้างเอกสาร การจัดรูปแบบ และการแทรกเนื้อหา

### Q: จะเพิ่มสารบัญในเอกสารอย่างไร?

A: เพื่อเพิ่มสารบัญ ใช้ `DocumentBuilder` แทรกฟิลด์ TOC แล้วเรียก `doc.updateFields()` หลังจากเพิ่มเนื้อหาแล้ว

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: จะใส่รูปภาพลงในเอกสารโดยใช้ Aspose.Words for Java อย่างไร?

A: คุณสามารถแทรกรูปภาพได้ทั้งแบบอินไลน์และแบบลอยโดยใช้ `DocumentBuilder`

#### รูปภาพแบบอินไลน์:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### รูปภาพแบบลอย:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: สามารถจัดรูปแบบข้อความและย่อหน้าเมื่อเพิ่มเนื้อหาได้หรือไม่?

A: ได้ คุณสามารถจัดรูปแบบข้อความและย่อหน้าโดยใช้ `DocumentBuilder` ตั้งค่าคุณสมบัติฟอนต์ การจัดแนวย่อหน้า การเยื้อง และอื่น ๆ ก่อนเขียนเนื้อหา

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: จะย้ายเคอร์เซอร์ไปยังตำแหน่งเฉพาะในเอกสารอย่างไร?

A: ใช้เมธอดเช่น `moveToParagraph`, `moveToCell` เป็นต้น เพื่อกำหนดตำแหน่งเคอร์เซอร์ก่อนแทรกเนื้อหาใหม่

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

คำตอบเหล่านี้ครอบคลุมสถานการณ์ที่พบบ่อยที่สุดเมื่อทำงานกับ `DocumentBuilder` ของ Aspose.Words for Java สำหรับรายละเอียดเพิ่มเติม โปรดดูที่ [library's documentation](https://reference.aspose.com/words/java/) หรือเข้าร่วมชุมชน Aspose.Words เพื่อรับการสนับสนุน

---

**Last Updated:** 2026-01-01  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}