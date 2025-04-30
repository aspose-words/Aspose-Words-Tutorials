---
"description": "สร้างเอกสารอย่างมืออาชีพด้วย Aspose.Words สำหรับ Java คำแนะนำทีละขั้นตอนในการเพิ่มข้อความ ตาราง รูปภาพ และอื่นๆ สร้างเอกสาร Word ที่สวยงามได้อย่างง่ายดาย"
"linktitle": "การเพิ่มเนื้อหาโดยใช้ DocumentBuilder"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words สำหรับ Java


## การแนะนำการเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words สำหรับ Java

ในคู่มือทีละขั้นตอนนี้ เราจะมาดูวิธีใช้ DocumentBuilder ของ Aspose.Words สำหรับ Java เพื่อเพิ่มเนื้อหาประเภทต่างๆ ลงในเอกสาร Word เราจะครอบคลุมการแทรกข้อความ ตาราง แนวระนาบ ฟิลด์ฟอร์ม HTML ไฮเปอร์ลิงก์ สารบัญ รูปภาพแบบอินไลน์และแบบลอย ย่อหน้า และอื่นๆ อีกมากมาย มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าไลบรารี Aspose.Words สำหรับ Java ไว้ในโปรเจ็กต์ของคุณแล้ว คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-aspose.com/words/java/).

## การเพิ่มข้อความ

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกข้อความย่อหน้าแบบง่าย
builder.write("This is a simple text paragraph.");

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

## การเพิ่มตาราง

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// เริ่มต้นตาราง
Table table = builder.startTable();

// แทรกเซลล์และเนื้อหา
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// จบตาราง
builder.endTable();

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

## การเพิ่มเส้นแนวนอน

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกไม้บรรทัดแนวนอน
builder.insertHorizontalRule();

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

## การเพิ่มฟิลด์ฟอร์ม

### ฟอร์มป้อนข้อความ

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกช่องฟอร์มป้อนข้อความ
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

### แบบฟอร์มช่องกาเครื่องหมาย

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกช่องกาเครื่องหมายแบบฟอร์ม
builder.insertCheckBox("CheckBox", true, true, 0);

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

### ฟอร์มกล่องคอมโบ

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// กำหนดรายการสำหรับกล่องคอมโบ
String[] items = { "Option 1", "Option 2", "Option 3" };

// แทรกฟิลด์ฟอร์มกล่องรวม
builder.insertComboBox("DropDown", items, 0);

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

## การเพิ่ม HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกเนื้อหา HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

## การเพิ่มไฮเปอร์ลิงก์

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกไฮเปอร์ลิงก์
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", เท็จ);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

## การเพิ่มสารบัญ

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกสารบัญ
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// เพิ่มเนื้อหาเอกสาร
// -

// อัปเดตสารบัญ
doc.updateFields();

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

## การเพิ่มรูปภาพ

### ภาพอินไลน์

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกภาพอินไลน์
builder.insertImage("path/to/your/image.png");

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

### ภาพลอยน้ำ

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกภาพลอย
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

## การเพิ่มย่อหน้า

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// ตั้งค่าการจัดรูปแบบย่อหน้า
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

// แทรกย่อหน้า
builder.writeln("This is a formatted paragraph.");

// บันทึกเอกสาร
doc.save("path/to/your/document.docx");
```

## ขั้นตอนที่ 10: การย้ายเคอร์เซอร์

คุณสามารถควบคุมตำแหน่งเคอร์เซอร์ภายในเอกสารได้โดยใช้หลากหลายวิธี เช่น `moveToParagraph`- `moveToCell`และอื่นๆ นี่คือตัวอย่าง:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// เลื่อนเคอร์เซอร์ไปที่ย่อหน้าที่ต้องการ
builder.moveToParagraph(2, 0);

// เพิ่มเนื้อหาที่ตำแหน่งเคอร์เซอร์ใหม่
builder.writeln("This is the 3rd paragraph.");
```

เหล่านี้คือการดำเนินการทั่วไปบางอย่างที่คุณสามารถทำได้โดยใช้ Aspose.Words สำหรับ DocumentBuilder ของ Java สำรวจเอกสารของไลบรารีเพื่อดูคุณลักษณะขั้นสูงและตัวเลือกการปรับแต่ง สร้างเอกสารอย่างมีความสุข!


## บทสรุป

ในคู่มือฉบับสมบูรณ์นี้ เราได้สำรวจความสามารถของ DocumentBuilder ของ Aspose.Words สำหรับ Java ในการเพิ่มเนื้อหาประเภทต่างๆ ลงในเอกสาร Word เราได้ครอบคลุมข้อความ ตาราง กฎแนวนอน ฟิลด์ฟอร์ม HTML ไฮเปอร์ลิงก์ สารบัญ รูปภาพ ย่อหน้า และการเคลื่อนเคอร์เซอร์

## คำถามที่พบบ่อย

### ถาม: Aspose.Words สำหรับ Java คืออะไร?

A: Aspose.Words for Java เป็นไลบรารี Java ที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และจัดการเอกสาร Microsoft Word ได้ด้วยโปรแกรม โดยมีคุณสมบัติมากมายสำหรับการสร้างเอกสาร การจัดรูปแบบ และการแทรกเนื้อหา

### ถาม: ฉันจะเพิ่มสารบัญลงในเอกสารของฉันได้อย่างไร

ก: หากต้องการเพิ่มสารบัญ ให้ใช้ `DocumentBuilder` เพื่อแทรกฟิลด์สารบัญลงในเอกสารของคุณ อย่าลืมอัปเดตฟิลด์ในเอกสารหลังจากเพิ่มเนื้อหาเพื่อเติมลงในสารบัญ นี่คือตัวอย่าง:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกช่องสารบัญ
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// เพิ่มเนื้อหาเอกสาร
// -

// อัปเดตสารบัญ
doc.updateFields();
```

### ถาม: ฉันจะแทรกภาพลงในเอกสารโดยใช้ Aspose.Words สำหรับ Java ได้อย่างไร

A: คุณสามารถแทรกภาพได้ทั้งแบบอินไลน์และแบบลอยโดยใช้ `DocumentBuilder`. ต่อไปนี้เป็นตัวอย่างของทั้งสอง:

#### ภาพอินไลน์:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกภาพอินไลน์
builder.insertImage("path/to/your/image.png");
```

#### ภาพลอย:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกภาพลอย
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### ถาม: ฉันสามารถจัดรูปแบบข้อความและย่อหน้าเมื่อเพิ่มเนื้อหาได้หรือไม่

A: ใช่ คุณสามารถจัดรูปแบบข้อความและย่อหน้าโดยใช้ `DocumentBuilder`คุณสามารถตั้งค่าคุณสมบัติของแบบอักษร การจัดตำแหน่งย่อหน้า การเยื้องย่อหน้า และอื่นๆ ได้ ต่อไปนี้คือตัวอย่าง:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// ตั้งค่ารูปแบบฟอนต์และย่อหน้า
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

// แทรกย่อหน้าที่มีการจัดรูปแบบแล้ว
builder.writeln("This is a formatted paragraph.");
```

### ถาม: ฉันจะย้ายเคอร์เซอร์ไปยังตำแหน่งเฉพาะภายในเอกสารได้อย่างไร

A: คุณสามารถควบคุมตำแหน่งเคอร์เซอร์ได้โดยใช้วิธีการเช่น `moveToParagraph`- `moveToCell`และอื่นๆ นี่คือตัวอย่าง:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// เลื่อนเคอร์เซอร์ไปที่ย่อหน้าที่ต้องการ
builder.moveToParagraph(2, 0);

// เพิ่มเนื้อหาที่ตำแหน่งเคอร์เซอร์ใหม่
builder.writeln("This is the 3rd paragraph.");
```

เหล่านี้เป็นคำถามและคำตอบทั่วไปที่จะช่วยให้คุณเริ่มต้นใช้งาน Aspose.Words สำหรับ DocumentBuilder ของ Java ได้ หากคุณมีคำถามเพิ่มเติมหรือต้องการความช่วยเหลือเพิ่มเติม โปรดดูที่ [เอกสารประกอบของห้องสมุด](https://reference.aspose.com/words/java/) หรือขอความช่วยเหลือจากชุมชน Aspose.Words และทรัพยากรสนับสนุน


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}