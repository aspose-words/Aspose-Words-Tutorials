---
date: 2026-02-19
description: เรียนรู้วิธีสร้างเอกสารพร้อมลายน้ำโดยใช้ Aspose.Words for Java และเพิ่มลายน้ำรูปภาพใน
  Java สำหรับเอกสารที่ดูเป็นมืออาชีพ
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: สร้างเอกสารพร้อมลายน้ำโดยใช้ Aspose.Words สำหรับ Java
url: /th/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสารพร้อมลายน้ำโดยใช้ Aspose.Words for Java

ในบทแนะนำนี้คุณจะ **สร้างเอกสารพร้อมลายน้ำ** โดยใช้ API ของ Aspose.Words for Java ลายน้ำ—ไม่ว่าจะเป็นข้อความหรือรูปภาพ—ช่วยให้คุณระบุไฟล์ว่าเป็นความลับ, ฉบับร่าง, หรือได้รับการอนุมัติ และสามารถนำไปใช้โดยอัตโนมัติกับเอกสาร Word ใดก็ได้ เราจะอธิบายขั้นตอนการตั้งค่าห้องสมุด, การเพิ่มลายน้ำข้อความและรูปภาพ, การปรับแต่งลักษณะของลายน้ำ, และแม้กระทั่งการลบลายน้ำเมื่อไม่ต้องการใช้แล้ว

## คำตอบด่วน
- **ลายน้ำทำหน้าที่อะไร?** มันจะซ้อนข้อความหรือรูปภาพบนแต่ละหน้าเพื่อบ่งบอกสถานะหรือการสร้างแบรนด์  
- **ห้องสมุดใดที่เพิ่มลายน้ำใน Java?** Aspose.Words for Java มีการสนับสนุนลายน้ำในตัว  
- **ฉันสามารถเพิ่มลายน้ำรูปภาพได้หรือไม่?** ได้—ใช้คลาส `Shape` และวิธี `add image watermark java`  
- **ลายน้ำเป็นแบบกึ่งโปร่งใสหรือไม่?** คุณสามารถควบคุมความทึบโดยใช้ `setSemitransparent` สำหรับลายน้ำข้อความ  
- **ฉันต้องการไลเซนส์หรือไม่?** รุ่นทดลองฟรีใช้ได้สำหรับการทดสอบ; ต้องมีไลเซนส์เชิงพาณิชย์สำหรับการใช้งานจริง  

## ลายน้ำคืออะไรและทำไมต้องใช้?

ลายน้ำคือการซ้อนแบบอ่อน—เป็นข้อความหรือกราฟิก—ที่เพิ่มลงในทุกหน้าของเอกสาร มักใช้เพื่อระบุ **ความลับ**, **สถานะฉบับร่าง**, หรือ **การสร้างแบรนด์** โดยไม่เปลี่ยนแปลงเนื้อหาต้นฉบับ การเพิ่มลายน้ำโดยอัตโนมัติช่วยให้ความสอดคล้องในชุดไฟล์จำนวนมากและประหยัดเวลาเมื่อเทียบกับการแก้ไขด้วยตนเอง

## การตั้งค่า Aspose.Words for Java

ก่อนที่เราจะเริ่มเพิ่มลายน้ำ ให้แน่ใจว่าห้องสมุดพร้อมใช้งานในโปรเจกต์ของคุณ:

1. ดาวน์โหลด Aspose.Words for Java จาก [here](https://releases.aspose.com/words/java/).  
2. เพิ่มไฟล์ JAR ที่ดาวน์โหลด (หรือ dependency ของ Maven/Gradle) ไปยัง classpath ของโปรเจกต์ของคุณ.  
3. นำเข้าคลาสที่จำเป็นในไฟล์ซอร์ส Java ของคุณ:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

เมื่อห้องสมุดตั้งค่าเรียบร้อยแล้ว เราจะไปสู่โค้ดลายน้ำจริง

## วิธีเพิ่มลายน้ำข้อความ

ลายน้ำข้อความเหมาะสำหรับการระบุเอกสารว่า “CONFIDENTIAL” หรือ “DRAFT”. โค้ดตัวอย่างต่อไปนี้แสดงวิธีที่สะอาดในการ **สร้างเอกสารพร้อมลายน้ำ** โดยใช้ `TextWatermarkOptions`.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### การปรับแต่งลายน้ำข้อความ
- **แบบอักษรและขนาด** – เปลี่ยน `setFontFamily` และ `setFontSize`.  
- **สี** – ใช้ `java.awt.Color` ใดก็ได้.  
- **การจัดวาง** – เลือก `HORIZONTAL`, `DIAGONAL` เป็นต้น.  
- **ความโปร่งใส** – เปิด/ปิด `setSemitransparent(true)` เพื่อให้ดูอ่อนลง.  

## วิธีเพิ่มลายน้ำรูปภาพ (add image watermark java)

ลายน้ำรูปภาพเหมาะสำหรับโลโก้หรือกราฟิกที่กำหนดเอง ด้านล่างเป็นตัวอย่าง **add image watermark java** ที่แทรกไฟล์ PNG ลงในศูนย์ของแต่ละหน้า.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### เคล็ดลับสำหรับลายน้ำรูปภาพ
- **ปรับขนาด** ด้วย `setWidth` / `setHeight` เพื่อให้พอดีกับหน้า.  
- **ตำแหน่ง** สามารถจัดให้อยู่กึ่งกลางหรือจัดแนวกับขอบใดก็ได้โดยใช้ `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **ความโปร่งใส** สามารถทำได้โดยปรับช่องอัลฟาของภาพก่อนโหลด.  

## วิธีลบลายน้ำ

เมื่อเอกสารไม่ต้องการลายน้ำอีกต่อไป คุณสามารถลบออกโดยอัตโนมัติ โค้ดด้านล่างจะวนผ่านรูปทั้งหมดและลบรูปใดที่มีชื่อว่า “Watermark”

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## ปัญหาที่พบบ่อยและการแก้ไขข้อผิดพลาด
- **ลายน้ำหายหลังการบันทึก** – ตรวจสอบให้แน่ใจว่าคุณเรียก `doc.save()` หลังจากตั้งค่าลายน้ำ.  
- **รูปภาพไม่แสดง** – ตรวจสอบว่าเส้นทางรูปภาพถูกต้องและไฟล์เป็นรูปแบบที่รองรับ (PNG, JPEG, BMP).  
- **ความโปร่งใสไม่ทำงาน** – `setSemitransparent(true)` ใช้ได้เฉพาะลายน้ำข้อความ; สำหรับรูปภาพให้แก้ไขช่องอัลฟของ PNG.  
- **หลายส่วน** – หากเอกสารของคุณมีหลายส่วน ให้เพิ่มลายน้ำใน body ของแต่ละส่วนหรือใช้ `doc.getWatermark().setText(...)` ซึ่งจะใช้ทั่วทั้งเอกสาร.  

## คำถามที่พบบ่อย

**Q: ฉันจะเปลี่ยนแบบอักษรของลายน้ำข้อความได้อย่างไร?**  
A: ปรับคุณสมบัติ `setFontFamily` ใน `TextWatermarkOptions` เช่น `options.setFontFamily("Times New Roman");`.

**Q: ฉันสามารถเพิ่มลายน้ำหลายรายการในเอกสารเดียวได้หรือไม่?**  
A: ได้. สร้างหลายอ็อบเจ็กต์ `Shape` (สำหรับรูปภาพ) หรือเรียก `doc.getWatermark().setText(...)` พร้อมตัวเลือกที่แตกต่างกันสำหรับแต่ละลายน้ำ.

**Q: สามารถหมุนลายน้ำได้หรือไม่?**  
A: สำหรับลายน้ำรูปภาพ ให้ตั้งค่าการหมุนบนอ็อบเจ็กต์ `Shape` ด้วย `watermark.setRotation(angle)`. สำหรับลายน้ำข้อความ ใช้คุณสมบัติ `setLayout` (เช่น `WatermarkLayout.DIAGONAL`).

**Q: ฉันจะทำให้ลายน้ำเป็นกึ่งโปร่งใสได้อย่างไร?**  
A: ตั้งค่า `options.setSemitransparent(true)` ใน `TextWatermarkOptions`. สำหรับรูปภาพ ให้ปรับความทึบของภาพก่อนโหลด.

**Q: ฉันสามารถเพิ่มลายน้ำให้กับส่วนเฉพาะของเอกสารได้หรือไม่?**  
A: ได้. วนผ่าน `doc.getSections()` และเพิ่มลายน้ำเฉพาะในส่วนที่ต้องการเท่านั้น.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**อัปเดตล่าสุด:** 2026-02-19  
**ทดสอบด้วย:** Aspose.Words for Java 24.12 (latest)  
**ผู้เขียน:** Aspose