---
category: general
date: 2026-09-11
description: จัดกลุ่มรูปร่างใน Word และเพิ่มรูปสี่เหลี่ยมโดยใช้ Aspose.Words for Java
  เรียนรู้วิธีตั้งค่าขนาดของรูปร่าง จัดกลุ่มวัตถุ และบันทึกเอกสาร.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: th
lastmod: 2026-09-11
og_description: จัดกลุ่มรูปร่างใน Word และเพิ่มรูปสี่เหลี่ยมโดยใช้ Aspose.Words for
  Java บทเรียนนี้แสดงวิธีตั้งค่าขนาดของรูปร่าง, จัดกลุ่มรูปร่าง, และส่งออกเอกสาร.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: จัดกลุ่มรูปร่างใน Word – เพิ่มสี่เหลี่ยมผืนผ้าด้วย Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: จัดกลุ่มรูปร่างใน Word และเพิ่มสี่เหลี่ยมผืนผ้าด้วย Aspose.Words
url: /th/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การจัดกลุ่มรูปร่างใน Word และเพิ่มสี่เหลี่ยมผืนผ้าด้วย Aspose.Words

หากคุณต้องการ **จัดกลุ่มรูปร่างใน Word** ขณะเพิ่มสี่เหลี่ยมผืนผ้าแบบโปรแกรมมิ่ง คำแนะนำนี้จะให้โซลูชันที่สมบูรณ์และพร้อมรัน คุณจะได้เห็นวิธีแทรกกลุ่มรูปร่าง, เพิ่มรูปร่างสี่เหลี่ยมผืนผ้า, ตั้งขนาดรูปร่าง, และสุดท้ายบันทึกเอกสารเพื่อดูผลลัพธ์ทันที

การทำงานกับเอกสาร Word มักหมายถึงการจัดเรียงออบเจ็กต์หลาย ๆ อย่าง—รูปภาพ, แผนภูมิ, หรือรูปร่างเรขาคณิตง่าย ๆ—ให้เป็นหน่วยตรรกะเดียว การจัดกลุ่มออบเจ็กต์เหล่านี้ทำให้การย้าย, หมุน, หรือกำหนดสไตล์ทำได้ง่ายขึ้น ในบทเรียนนี้เราจะครอบคลุม **วิธีเพิ่มสี่เหลี่ยมผืนผ้า** และ **การตั้งขนาดรูปร่าง** เพื่อควบคุมการจัดวางอย่างแม่นยำ

## สิ่งที่คุณจะได้เรียนรู้

* วิธีสร้างเอกสาร Word ใหม่ด้วย Aspose.Words for Java  
* **วิธีจัดกลุ่มรูปร่าง** ให้ทำงานเป็นออบเจ็กต์เดียว  
* **เพิ่มรูปร่างสี่เหลี่ยมผืนผ้า** ไปยังกลุ่มและแทรกรูปภาพในกลุ่มเดียวกัน  
* **ตั้งขนาดรูปร่าง** สำหรับสี่เหลี่ยมผืนผ้าและรูปภาพ  
* บันทึกเอกสารและเปิดใน Microsoft Word เพื่อตรวจสอบผลลัพธ์

### ข้อกำหนดเบื้องต้น

* Java 17 หรือใหม่กว่า  
* Maven หรือ Gradle สำหรับจัดการ dependencies  
* ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (หรือคีย์ทดลองใช้ฟรี)  
* ไฟล์รูปภาพ (`sample.png`) ที่วางไว้ในไดเรกทอรีที่รู้จัก (แทนที่ `YOUR_DIRECTORY` ด้วยพาธจริงของคุณ)

---

## วิธีจัดกลุ่มรูปร่างใน Word ด้วย Aspose.Words

ขั้นตอนแรกคือการสร้าง `Document` และ `DocumentBuilder` Builder จะให้ API ที่สะดวกสำหรับแทรกรูปร่าง, ข้อความ, และองค์ประกอบอื่น ๆ

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **ทำไมจึงสำคัญ:** `DocumentBuilder` ทำงานโดยตรงกับออบเจ็กต์ `Document` พื้นฐาน ช่วยให้คุณแทรกรูปร่างได้โดยไม่ต้องจัดการคอลเลกชันโหนดระดับต่ำด้วยตนเอง

### เพิ่มกลุ่มรูปร่าง

กลุ่มรูปร่างเป็นคอนเทนเนอร์ที่สามารถเก็บรูปร่างอื่น ๆ ได้ คิดว่าเป็นโฟลเดอร์สำหรับออบเจ็กต์การวาด

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

เมธอด `insertGroupShape()` จะสร้างโหนด `GroupShape` และคืนค่าให้คุณสามารถต่อเติมรูปร่างลูกได้ในภายหลัง  

---

## เพิ่มสี่เหลี่ยมผืนผ้าไปยังกลุ่ม

ต่อไปเราจะ **เพิ่มสี่เหลี่ยมผืนผ้า** ไปยังกลุ่มที่สร้างไว้ก่อนหน้านี้ สี่เหลี่ยมผืนผ้าจะทำหน้าที่เป็นพื้นหลังหรือกรอบสำหรับรูปภาพ

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **เคล็ดลับ:** การตั้งค่า `FillColor` และ `StrokeColor` ทำให้สี่เหลี่ยมผืนผ้าเห็นได้ในเอกสารสุดท้าย หากคุณละเว้นคุณสมบัติเหล่านี้ รูปร่างอาจปรากฏเป็นโปร่งใส

### วิธีเพิ่มสี่เหลี่ยมผืนผ้า

โค้ดด้านบนแสดง **วิธีเพิ่มสี่เหลี่ยมผืนผ้า** โดยการสร้างอินสแตนซ์ `Shape` ด้วย `ShapeType.RECTANGLE` แล้วต่อท้ายลงใน `GroupShape` รูปแบบนี้ใช้ได้กับรูปร่างประเภทอื่น ๆ (เช่น `ELLIPSE`, `POLYLINE`)

---

## ตั้งขนาดรูปร่างสำหรับสี่เหลี่ยมผืนผ้าและรูปภาพ

การกำหนดขนาดอย่างเหมาะสมทำให้สี่เหลี่ยมผืนผ้าและรูปภาพจัดตำแหน่งกันได้อย่างถูกต้อง ที่นี่เรายัง **ตั้งขนาดรูปร่าง** สำหรับรูปภาพที่จะแทรกต่อไป

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

ตอนนี้สี่เหลี่ยมผืนผ้าและรูปภาพมีขนาดเดียวกัน (100 × 50 points) เนื่องจากอยู่ในกลุ่มเดียวกัน การย้ายหรือหมุนกลุ่มจะส่งผลต่อรูปร่างทั้งสองพร้อมกัน

> **ทำไมต้องจับคู่ขนาด?** การทำให้มิติเท่ากันรับประกันว่ารูปภาพจะอยู่ภายในสี่เหลี่ยมผืนผ้าอย่างเรียบร้อย สร้างเอฟเฟกต์ “รูปภาพในกรอบ” ที่สะอาดตา

---

## บันทึกเอกสารและดูผลลัพธ์

สุดท้าย เราจะเขียนเอกสารลงดิสก์ การเปิดไฟล์ใน Microsoft Word จะแสดงกลุ่มรูปร่างเป็นออบเจ็กต์ที่เลือกได้เป็นหนึ่งเดียว

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

เมื่อคุณเปิด `output.docx` คุณจะเห็นสี่เหลี่ยมผืนผ้าที่มีรูปภาพอยู่ภายใน การคลิกที่รูปร่างจะเลือกทั้งสี่เหลี่ยมผืนผ้าและรูปภาพพร้อมกัน เพราะพวกมัน **ถูกจัดกลุ่ม** แล้ว

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*ข้อความแทนภาพ:* *group shapes in word example* – เอกสาร Word ที่แสดงสี่เหลี่ยมผืนผ้าและรูปภาพที่จัดกลุ่ม

---

## คำถามทั่วไปและการจัดการกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ถ้าต้องการขนาดรูปภาพที่ต่างออกไปจะทำอย่างไร?** | ปรับ `picture.setWidth()` และ `picture.setHeight()` หลังจากแทรก รูปสี่เหลี่ยมผืนผ้าสามารถคงขนาดเดิม หรือคุณก็สามารถปรับขนาดให้ตรงกันได้ |
| **สามารถเพิ่มรูปร่างอื่น ๆ ลงในกลุ่มเดียวกันได้ไหม?** | ได้ เรียก `group.appendChild(newShape)` สำหรับออบเจ็กต์ `Shape` ใด ๆ ที่ต้องการเพิ่ม |
| **จะหมุนกลุ่มทั้งหมดอย่างไร?** | ใช้ `group.setRotationAngle(double angleInRadians)` การหมุนจะใช้กับรูปร่างลูกทุกตัว |
| **ถ้าไฟล์รูปภาพหายไปจะเกิดอะไรขึ้น?** | `insertImage` จะโยน `FileNotFoundException` ให้ห่อการเรียกในบล็อก try‑catch และเตรียมรูปร่างสำรองเป็น placeholder |
| **สามารถแยกกลุ่มออกภายหลังได้หรือไม่?** | เรียก `group.removeAllChildren()` เพื่อตัดลูกออก แล้วแทรกพวกมันกลับเข้าเอกสารเป็นออบเจ็กต์แยกกัน |

---

## สรุป

ตอนนี้คุณมีตัวอย่างที่สมบูรณ์และสามารถรันได้ ซึ่งแสดง **วิธีจัดกลุ่มรูปร่างใน Word**, **เพิ่มสี่เหลี่ยมผืนผ้า**, **ตั้งขนาดรูปร่าง**, และ **บันทึก** เอกสารด้วย Aspose.Words for Java การจัดกลุ่มสี่เหลี่ยมผืนผ้าและรูปภาพทำให้คุณสามารถย้าย, ปรับขนาด, หรือหมุนได้เป็นหน่วยเดียว—สิ่งที่หลายสถานการณ์การทำอัตโนมัติของเอกสารต้องการ

ต่อจากนี้คุณอาจสำรวจต่อ:

* การเพิ่มกล่องข้อความไปยังกลุ่มเดียวกัน (`how to add rectangle`‑style text)  
* การใช้รูปแบบการเติมสีหรือไล่สีต่าง ๆ (`set shape size` ร่วมกับการสไตลิ่ง)  
* การใช้เทคนิคเดียวกันเพื่อจัดกลุ่มแผนภูมิ, ตาราง, หรือ SmartArt (`how to group shapes` กับประเภทออบเจ็กต์อื่น)  

ลองทดลองกับประเภทรูปร่าง, สี, และตัวเลือกการจัดวางอื่น ๆ ได้เลย ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณเอง

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}