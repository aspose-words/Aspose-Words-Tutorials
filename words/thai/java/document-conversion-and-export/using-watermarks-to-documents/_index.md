---
date: 2025-12-18
description: เรียนรู้วิธีเพิ่มลายน้ำลงในเอกสารด้วย Aspose.Words for Java รวมถึงตัวอย่างลายน้ำรูปภาพ
  การเปลี่ยนสีลายน้ำ การตั้งค่าความโปร่งใสของลายน้ำ และการลบลายน้ำออกจากเอกสาร
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: วิธีเพิ่มลายน้ำในเอกสารโดยใช้ Aspose.Words สำหรับ Java
url: /th/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มลายน้ำลงในเอกสารโดยใช้ Aspose.Words for Java

## บทนำการเพิ่มลายน้ำลงในเอกสารด้วย Aspose.Words for Java

ในบทเรียนนี้คุณจะได้เรียนรู้ **วิธีเพิ่มลายน้ำ** ลงในเอกสาร Word ด้วย Aspose.Words for Java ลายน้ำเป็นวิธีที่รวดเร็วในการระบุไฟล์ว่าเป็นความลับ, ฉบับร่าง, หรือได้รับการอนุมัติ และสามารถเป็นแบบข้อความหรือแบบรูปภาพได้ เราจะอธิบายขั้นตอนการตั้งค่าไลบรารี, การสร้างลายน้ำข้อความและรูปภาพ, การปรับแต่งลักษณะของลายน้ำ (รวมถึงการเปลี่ยนสีลายน้ำและการตั้งค่าความโปร่งใสของลายน้ำ) และแม้กระทั่งการลบลายน้ำออกจากเอกสารเมื่อไม่ต้องการใช้แล้ว.

## คำตอบอย่างรวดเร็ว
- **ลายน้ำคืออะไร?** การซ้อนทับแบบกึ่งโปร่งใส (ข้อความหรือรูปภาพ) ที่ปรากฏอยู่ด้านหลังเนื้อหาเอกสารหลัก.  
- **ฉันสามารถเพิ่มลายน้ำหลายรายการได้หรือไม่?** ได้ – สร้างอ็อบเจ็กต์ `Shape` หลายตัวและเพิ่มแต่ละอันลงในส่วนที่ต้องการ.  
- **ฉันจะเปลี่ยนสีลายน้ำได้อย่างไร?** ปรับคุณสมบัติ `Color` ใน `TextWatermarkOptions`.  
- **มีตัวอย่างลายน้ำรูปภาพหรือไม่?** ดูส่วน “Adding Image Watermarks” ด้านล่าง.  
- **ฉันต้องมีลิขสิทธิ์เพื่อเอาลายน้ำออกหรือไม่?** จำเป็นต้องมีลิขสิทธิ์ Aspose.Words ที่ถูกต้องสำหรับการใช้งานในสภาพแวดล้อมการผลิต.

## การตั้งค่า Aspose.Words for Java

ก่อนที่เราจะเริ่มเพิ่มลายน้ำลงในเอกสาร เราต้องตั้งค่า Aspose.Words for Java ก่อน ทำตามขั้นตอนต่อไปนี้เพื่อเริ่มต้น:

1. ดาวน์โหลด Aspose.Words for Java จาก [ที่นี่](https://releases.aspose.com/words/java/).  
2. เพิ่มไลบรารี Aspose.Words for Java ไปยังโครงการ Java ของคุณ.  
3. นำเข้าคลาสที่จำเป็นในโค้ด Java ของคุณ.

เมื่อเราตั้งค่าไลบรารีเรียบร้อยแล้ว ให้ดำดิ่งสู่การสร้างลายน้ำจริง.

## การเพิ่มลายน้ำข้อความ

ลายน้ำข้อความเป็นตัวเลือกที่พบบ่อยเมื่อคุณต้องการเพิ่มข้อมูลข้อความลงในเอกสารของคุณ นี่คือวิธีการเพิ่มลายน้ำข้อความโดยใช้ Aspose.Words for Java:

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

**ทำไมเรื่องนี้ถึงสำคัญ:** โดยการปรับ `setFontFamily`, `setFontSize` และ `setColor` คุณสามารถ **เปลี่ยนสีลายน้ำ** ให้ตรงกับแบรนด์ของคุณ, และ `setSemitransparent(true)` ทำให้คุณ **ตั้งค่าความโปร่งใสของลายน้ำ** เพื่อให้ได้เอฟเฟกต์ที่ละเอียดอ่อน.

## การเพิ่มลายน้ำรูปภาพ

นอกจากลายน้ำข้อความแล้ว คุณยังสามารถเพิ่มลายน้ำรูปภาพลงในเอกสารของคุณได้ ด้านล่างเป็น **ตัวอย่างลายน้ำรูปภาพ** ที่แสดงวิธีฝังโลโก้หรือแสตมป์ PNG:

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

คุณสามารถทำซ้ำบล็อกนี้ด้วยรูปภาพหรือตำแหน่งที่ต่างกันเพื่อ **เพิ่มลายน้ำหลายรายการ** ในไฟล์เดียว.

## การปรับแต่งลายน้ำ

คุณสามารถปรับแต่งลายน้ำได้โดยการปรับลักษณะและตำแหน่งของมัน สำหรับลายน้ำข้อความ คุณสามารถเปลี่ยนแบบอักษร, ขนาด, สี, และการจัดวางได้ สำหรับลายน้ำรูปภาพ คุณสามารถปรับขนาด, การหมุน, และการจัดตำแหน่งตามที่แสดงในตัวอย่างก่อนหน้า

## การลบลายน้ำ

หากคุณต้องการ **ลบเนื้อหาลายน้ำออกจากเอกสาร** โค้ดต่อไปนี้จะวนผ่านรูปทรงทั้งหมดและลบรูปทรงที่ระบุว่าเป็นลายน้ำออก:

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

## กรณีการใช้งานทั่วไปและเคล็ดลับ

- **ร่างเอกสารลับ:** ใช้ลายน้ำข้อความกึ่งโปร่งใสเช่น “CONFIDENTIAL”.
- **การสร้างแบรนด์:** ใช้ลายน้ำรูปภาพที่มีโลโก้บริษัทของคุณ.
- **ลายน้ำเฉพาะส่วน:** วนลูปผ่าน `doc.getSections()` และเพิ่มลายน้ำเฉพาะในส่วนที่คุณเลือก.
- **เคล็ดลับประสิทธิภาพ:** ใช้ `TextWatermarkOptions` ตัวเดียวกันซ้ำเมื่อใส่ลายน้ำเดียวกันในหลายเอกสาร.

## คำถามที่พบบ่อย

### ฉันจะเปลี่ยนแบบอักษรของลายน้ำข้อความได้อย่างไร?

เพื่อเปลี่ยนแบบอักษรของลายน้ำข้อความ ให้แก้ไขคุณสมบัติ `setFontFamily` ใน `TextWatermarkOptions` ตัวอย่างเช่น:

```java
options.setFontFamily("Times New Roman");
```

### ฉันสามารถเพิ่มลายน้ำหลายรายการในเอกสารเดียวได้หรือไม่?

ได้ คุณสามารถเพิ่มลายน้ำหลายรายการในเอกสารได้โดยการสร้างอ็อบเจ็กต์ `Shape` หลายตัวที่มีการตั้งค่าต่างกันและเพิ่มเข้าไปในเอกสาร

### สามารถหมุนลายน้ำได้หรือไม่?

ได้ คุณสามารถหมุนลายน้ำได้โดยตั้งค่าคุณสมบัติ `setRotation` ในอ็อบเจ็กต์ `Shape` ค่าบวกจะหมุนลายน้ำตามเข็มนาฬิกา และค่าลบจะหมุนในทิศทางตรงกันข้าม

### ฉันจะทำให้ลายน้ำกึ่งโปร่งใสได้อย่างไร?

เพื่อทำให้ลายน้ำกึ่งโปร่งใส ให้ตั้งค่าคุณสมบัติ `setSemitransparent` เป็น `true` ใน `TextWatermarkOptions`

### ฉันสามารถเพิ่มลายน้ำในส่วนเฉพาะของเอกสารได้หรือไม่?

ได้ คุณสามารถเพิ่มลายน้ำในส่วนเฉพาะของเอกสารได้โดยการวนลูปผ่านส่วนต่าง ๆ และเพิ่มลายน้ำในส่วนที่ต้องการ

---

**อัปเดตล่าสุด:** 2025-12-18  
**ทดสอบด้วย:** Aspose.Words for Java 24.12  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}