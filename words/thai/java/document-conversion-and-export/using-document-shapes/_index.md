---
date: 2026-02-16
description: เรียนรู้วิธีสร้างกล่องข้อความ, เพิ่มลายน้ำคำ, รวมหลายรูปทรงเป็นกลุ่ม,
  ตั้งอัตราส่วนของรูปทรง, และวางรูปทรงในเซลล์ของตารางโดยใช้ Aspose.Words for Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: วิธีสร้างกล่องข้อความและใช้รูปทรงเอกสารใน Aspose.Words สำหรับ Java
url: /th/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

 all shortcodes and code block placeholders.

Now craft final answer.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้รูปทรงเอกสารใน Aspose.Words สำหรับ Java

## บทนำการใช้รูปทรงเอกสารใน Aspose.Words สำหรับ Java

ในคู่มือฉบับครอบคลุมนี้, **คุณจะได้เรียนรู้วิธีสร้างวัตถุ text box** และรูปทรงที่ทรงพลังอื่น ๆ ด้วย Aspose.Words สำหรับ Java. รูปทรงช่วยให้คุณเพิ่มความหลากหลายให้กับเอกสาร Word ด้วยการอธิบาย, ปุ่ม, ลายน้ำ, SmartArt, และอื่น ๆ — ทำให้ดูน่าสนใจและโต้ตอบได้. เราจะเดินผ่านตัวอย่างจากโลกจริง, ตั้งแต่การแทรก text box ง่าย ๆ ไปจนถึงการจัดกลุ่มหลายรูปทรง, การตั้งอัตราส่วน, และการวางรูปทรงภายในเซลล์ตาราง.

## คำตอบอย่างรวดเร็ว
- **วิธีหลักในการเพิ่ม text box คืออะไร?** Use `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **ฉันสามารถจัดกลุ่มรูปทรงเข้าด้วยกันได้หรือไม่?** Yes – create a `GroupShape` and append child shapes.
- **ฉันจะล็อกหรือปลดล็อกอัตราส่วนของรูปทรงอย่างไร?** Call `shape.setAspectRatioLocked(true/false)`.
- **สามารถเพิ่มลายน้ำด้วยรูปทรงได้หรือไม่?** Absolutely – insert a `Shape` with `TEXT_PLAIN_TEXT` and set its fill/stroke.
- **ไดอะแกรม SmartArt ทำงานกับ Aspose.Words หรือไม่?** Yes – detect with `shape.hasSmartArt()` and update via `shape.updateSmartArtDrawing()`.

## text box คืออะไรและทำไมต้องสร้างรูปทรง text box?

text box คือคอนเทนเนอร์ที่สามารถบรรจุข้อความที่จัดรูปแบบ, รูปภาพ, หรือรูปทรงอื่น ๆ. การใช้ **create text box** ในการทำอัตโนมัติของคุณทำให้คุณสามารถวางเนื้อหาแบบลอยได้ทุกตำแหน่งบนหน้า, เหมาะสำหรับหมายเหตุ, การอธิบาย, หรือองค์ประกอบตกแต่งโดยไม่กระทบต่อการไหลของเอกสารหลัก.

## วิธีเพิ่มรูปทรง

ก่อนที่เราจะลงลึกในโค้ด, ตรวจสอบให้แน่ใจว่า Aspose.Words สำหรับ Java ถูกอ้างอิงในโปรเจกต์ของคุณ. หากคุณยังไม่ได้เพิ่ม, ดาวน์โหลดไลบรารีจากเว็บไซต์อย่างเป็นทางการ:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### การเพิ่มรูปทรงลงในเอกสาร

## วิธีจัดกลุ่มหลายรูปทรง

`GroupShape` ช่วยให้คุณจัดการหลายรูปทรงแยกเป็นหน่วยเดียว—มีประโยชน์สำหรับการย้ายหรือหมุนพร้อมกัน.

### การแทรก GroupShape

ด้านล่างเป็นตัวอย่างเต็มที่สร้างกลุ่ม, เพิ่มรูปทรงสองแบบที่แตกต่างกัน, และแทรกกลุ่มลงในเอกสาร.

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## วิธีสร้าง text box (create text box)

### การแทรกรูปทรง Text Box

เมธอด `insertShape` ทำให้การเพิ่ม text box เป็นเรื่องง่าย. ตัวอย่างด้านล่างแสดงสองวิธีในการกำหนดตำแหน่งและหมุน text box.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## วิธีตั้งค่าอัตราส่วนของรูปทรง

### การจัดการอัตราส่วน

บางครั้งคุณอาจต้องการให้รูปทรงยืดออกโดยไม่รักษาสัดส่วนเดิม. โค้ดต่อไปนี้แสดงการปลดล็อกอัตราส่วนของรูปทรงภาพ.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## วิธีวางรูปทรงในเซลล์ตาราง

### การวางรูปทรงภายในเซลล์ตาราง

ด้านล่างเป็นตัวอย่างขั้นตอนต่อขั้นตอนที่สร้างตาราง, จากนั้นแทรกรูปทรงลายน้ำที่กำหนดตำแหน่งสัมพันธ์กับหน้าแต่ยังสามารถวางภายในเซลล์ได้.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## การทำงานกับรูปทรง SmartArt

### การตรวจจับรูปทรง SmartArt

คุณสามารถค้นหาอ็อบเจกต์ SmartArt ในเอกสารโดยใช้เมธอด `hasSmartArt()` อย่างโปรแกรมได้.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### การอัปเดตการวาด SmartArt

เมื่อคุณพบรูปทรง SmartArt แล้ว, คุณสามารถรีเฟรชข้อมูลการวาดภายในของพวกมันด้วย `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## สรุป

ในคู่มือนี้, เราได้ครอบคลุมวิธี **สร้าง text box** วัตถุ, จัดกลุ่มหลายรูปทรง, ปรับอัตราส่วน, ฝังรูปทรงภายในเซลล์ตาราง, เพิ่มลายน้ำ, และทำงานกับไดอะแกรม SmartArt ด้วย Aspose.Words สำหรับ Java. เทคนิคเหล่านี้ทำให้คุณสามารถสร้างเอกสาร Word ที่มีการจัดรูปแบบอย่างละเอียดและโต้ตอบได้โดยอัตโนมัติ.

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ Java คืออะไร?

Aspose.Words สำหรับ Java เป็นไลบรารี Java ที่ช่วยให้นักพัฒนาสามารถสร้าง, แก้ไข, และแปลงเอกสาร Word อย่างอัตโนมัติ. มันมีคุณลักษณะและเครื่องมือหลากหลายสำหรับการทำงานกับเอกสารในรูปแบบต่าง ๆ.

### ฉันจะดาวน์โหลด Aspose.Words สำหรับ Java ได้อย่างไร?

คุณสามารถดาวน์โหลด Aspose.Words สำหรับ Java จากเว็บไซต์ Aspose โดยคลิกที่ลิงก์นี้: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### ประโยชน์ของการใช้รูปทรงในเอกสารคืออะไร?

รูปทรงในเอกสารเพิ่มองค์ประกอบภาพและการโต้ตอบให้กับเอกสารของคุณ, ทำให้ดูน่าสนใจและให้ข้อมูลมากขึ้น. ด้วยรูปทรง, คุณสามารถสร้างการอธิบาย, ปุ่ม, รูปภาพ, ลายน้ำ, และอื่น ๆ, เพื่อเสริมประสบการณ์ผู้ใช้โดยรวม.

### ฉันสามารถปรับแต่งลักษณะของรูปทรงได้หรือไม่?

ได้, คุณสามารถปรับแต่งลักษณะของรูปทรงโดยการปรับคุณสมบัติต่าง ๆ เช่น ขนาด, ตำแหน่ง, การหมุน, และสีเติม. Aspose.Words สำหรับ Java มีตัวเลือกที่หลากหลายสำหรับการปรับแต่งรูปทรง.

### Aspose.Words สำหรับ Java รองรับ SmartArt หรือไม่?

ใช่, Aspose.Words สำหรับ Java รองรับรูปทรง SmartArt, ทำให้คุณสามารถทำงานกับไดอะแกรมและกราฟิกที่ซับซ้อนได้ในเอกสารของคุณ.

## คำถามที่พบบ่อย

**Q: ฉันสามารถรวม text box กับรูปภาพภายในรูปทรงเดียวกันได้หรือไม่?**  
A: ได้. แทรกรูปภาพลงในรูปทรง text box โดยใช้ `builder.insertImage()` หลังจากสร้างรูปทรง, จากนั้นปรับเลย์เอาต์ตามต้องการ.

**Q: ฉันจะทำให้ลายน้ำปรากฏอยู่ด้านหลังเนื้อหาเอกสารทั้งหมดได้อย่างไร?**  
A: ตั้งค่า `WrapType` ของรูปทรงเป็น `NONE` และปรับ `RelativeHorizontalPosition` และ `RelativeVerticalPosition` เป็น `PAGE`. วิธีนี้ทำให้ลายน้ำอยู่ด้านหลังการไหลหลักของเอกสาร.

**Q: สามารถทำให้รูปทรงที่จัดกลุ่มเคลื่อนไหวใน Word ได้หรือไม่?**  
A: แม้ว่า Aspose.Words จะสามารถสร้างและจัดกลุ่มรูปทรงได้, แต่ฟีเจอร์การเคลื่อนไหวไม่รองรับเนื่องจากต้องอาศัยความสามารถของ UI ของ Word.

**Q: เวอร์ชันของ Aspose.Words ที่ต้องการสำหรับการรองรับ SmartArt คืออะไร?**  
A: การตรวจจับและอัปเดต SmartArt มีให้ใช้งานตั้งแต่ Aspose.Words 20.9 สำหรับ Java เป็นต้นไป.

**Q: ไลบรารีสามารถจัดการเอกสารขนาดใหญ่ที่มีรูปทรงจำนวนมากได้อย่างมีประสิทธิภาพหรือไม่?**  
A: ได้. ใช้ `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` หรือเวอร์ชันที่สูงกว่าเพื่อปรับปรุงประสิทธิภาพของเอกสารที่มีรูปทรงจำนวนมาก.

---

**อัปเดตล่าสุด:** 2026-02-16  
**ทดสอบด้วย:** Aspose.Words for Java 24.12  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}