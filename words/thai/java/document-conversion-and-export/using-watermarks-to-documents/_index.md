---
"description": "เรียนรู้วิธีการเพิ่มลายน้ำในเอกสารใน Aspose.Words สำหรับ Java ปรับแต่งลายน้ำข้อความและรูปภาพเพื่อให้เอกสารดูเป็นมืออาชีพ"
"linktitle": "การใช้ลายน้ำบนเอกสาร"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การใช้ลายน้ำกับเอกสารใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้ลายน้ำกับเอกสารใน Aspose.Words สำหรับ Java


## บทนำสู่การเพิ่มลายน้ำลงในเอกสารใน Aspose.Words สำหรับ Java

ในบทช่วยสอนนี้ เราจะมาเรียนรู้วิธีการเพิ่มลายน้ำลงในเอกสารโดยใช้ Aspose.Words for Java API ลายน้ำเป็นวิธีที่มีประโยชน์ในการใส่ข้อความหรือกราฟิกในเอกสารเพื่อระบุสถานะ ความลับ หรือข้อมูลที่เกี่ยวข้องอื่นๆ เราจะกล่าวถึงลายน้ำทั้งที่เป็นข้อความและรูปภาพในคู่มือนี้

## การตั้งค่า Aspose.Words สำหรับ Java

ก่อนที่เราจะเริ่มเพิ่มลายน้ำลงในเอกสาร เราจะต้องตั้งค่า Aspose.Words สำหรับ Java ก่อน ทำตามขั้นตอนเหล่านี้เพื่อเริ่มต้น:

1. ดาวน์โหลด Aspose.Words สำหรับ Java จาก [ที่นี่](https://releases-aspose.com/words/java/).
2. เพิ่มไลบรารี Aspose.Words สำหรับ Java ลงในโปรเจ็กต์ Java ของคุณ
3. นำเข้าคลาสที่จำเป็นลงในโค้ด Java ของคุณ

ตอนนี้เราได้ตั้งค่าไลบรารีเรียบร้อยแล้ว ต่อไปเราจะดำเนินการเพิ่มลายน้ำกัน

## การเพิ่มลายน้ำข้อความ

ลายน้ำข้อความเป็นตัวเลือกทั่วไปเมื่อคุณต้องการเพิ่มข้อมูลข้อความลงในเอกสารของคุณ ต่อไปนี้เป็นวิธีที่คุณสามารถเพิ่มลายน้ำข้อความโดยใช้ Aspose.Words สำหรับ Java:

```java
// สร้างอินสแตนซ์เอกสาร
Document doc = new Document("Document.docx");

// กำหนดตัวเลือก TextWatermark
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// ตั้งค่าข้อความลายน้ำและตัวเลือก
doc.getWatermark().setText("Test", options);

// บันทึกเอกสารด้วยลายน้ำ
doc.save("DocumentWithWatermark.docx");
```

## การเพิ่มลายน้ำบนภาพ

นอกจากลายน้ำข้อความแล้ว คุณยังสามารถเพิ่มลายน้ำภาพลงในเอกสารของคุณได้อีกด้วย วิธีเพิ่มลายน้ำภาพมีดังนี้:

```java
// สร้างอินสแตนซ์เอกสาร
Document doc = new Document("Document.docx");

// โหลดภาพสำหรับลายน้ำ
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// ตั้งค่าขนาดและตำแหน่งของลายน้ำ
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// เพิ่มลายน้ำลงในเอกสาร
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// บันทึกเอกสารด้วยลายน้ำ
doc.save("DocumentWithImageWatermark.docx");
```

## การปรับแต่งลายน้ำ

คุณสามารถปรับแต่งลายน้ำได้โดยปรับเปลี่ยนลักษณะและตำแหน่งของลายน้ำ สำหรับลายน้ำข้อความ คุณสามารถเปลี่ยนแบบอักษร ขนาด สี และเค้าโครงได้ สำหรับลายน้ำรูปภาพ คุณสามารถปรับขนาดและตำแหน่งของลายน้ำได้ดังที่แสดงในตัวอย่างก่อนหน้านี้

## การลบลายน้ำ

หากต้องการลบลายน้ำออกจากเอกสาร คุณสามารถใช้โค้ดดังต่อไปนี้:

```java
// สร้างอินสแตนซ์เอกสาร
Document doc = new Document("DocumentWithWatermark.docx");

// ลบลายน้ำ
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// บันทึกเอกสารโดยไม่ต้องใส่ลายน้ำ
doc.save("DocumentWithoutWatermark.docx");
```


## บทสรุป

ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการเพิ่มลายน้ำในเอกสารโดยใช้ Aspose.Words สำหรับ Java ไม่ว่าคุณจะต้องเพิ่มลายน้ำในข้อความหรือรูปภาพ Aspose.Words ก็มีเครื่องมือที่ช่วยให้คุณปรับแต่งและจัดการลายน้ำได้อย่างมีประสิทธิภาพ นอกจากนี้ คุณยังสามารถลบลายน้ำได้เมื่อไม่ต้องการใช้อีกต่อไป ทำให้มั่นใจได้ว่าเอกสารของคุณจะสะอาดและเป็นมืออาชีพ

## คำถามที่พบบ่อย

### ฉันจะเปลี่ยนแบบอักษรของลายน้ำข้อความได้อย่างไร?

หากต้องการเปลี่ยนแบบอักษรของลายน้ำข้อความ ให้แก้ไข `setFontFamily` ทรัพย์สินใน `TextWatermarkOptions`. ตัวอย่างเช่น:

```java
options.setFontFamily("Times New Roman");
```

### ฉันสามารถเพิ่มลายน้ำหลาย ๆ อันลงในเอกสารเดียวได้หรือไม่

ใช่ คุณสามารถเพิ่มลายน้ำหลาย ๆ ลายลงในเอกสารได้โดยการสร้างลายน้ำหลาย ๆ ลาย `Shape` วัตถุที่มีการตั้งค่าที่แตกต่างกันและการเพิ่มลงในเอกสาร

### สามารถหมุนลายน้ำได้หรือไม่?

ใช่ คุณสามารถหมุนลายน้ำได้โดยการตั้งค่า `setRotation` ทรัพย์สินใน `Shape` วัตถุ ค่าบวกจะหมุนลายน้ำตามเข็มนาฬิกา และค่าลบจะหมุนทวนเข็มนาฬิกา

### ฉันจะทำให้ลายน้ำเป็นแบบโปร่งแสงได้อย่างไร?

หากต้องการให้ลายน้ำเป็นแบบโปร่งแสง ให้ตั้งค่า `setSemitransparent` ทรัพย์สินที่จะ `true` ใน `TextWatermarkOptions`-

### ฉันสามารถเพิ่มลายน้ำลงในส่วนเฉพาะของเอกสารได้หรือไม่

ใช่ คุณสามารถเพิ่มลายน้ำลงในส่วนที่เจาะจงของเอกสารได้โดยการทำซ้ำตามส่วนต่างๆ และเพิ่มลายน้ำลงในส่วนที่ต้องการ


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}