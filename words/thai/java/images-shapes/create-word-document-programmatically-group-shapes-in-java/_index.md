---
category: general
date: 2026-09-21
description: สร้างเอกสาร Word อย่างอัตโนมัติด้วย Java. เรียนรู้วิธีจัดกลุ่มรูปร่างใน
  Word, แทรกรูปสี่เหลี่ยม, ตั้งค่าขนาดของรูปร่าง, และเพิ่มรูปร่างลงในเอกสาร Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: th
lastmod: 2026-09-21
og_description: 'สร้างเอกสาร Word ด้วยโปรแกรม Java: คู่มือนี้แสดงวิธีจัดกลุ่มรูปร่างใน
  Word, แทรกรูปสี่เหลี่ยม, ตั้งค่าขนาดรูปร่าง, และเพิ่มรูปร่างลงในเอกสาร Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: สร้างเอกสาร Word อย่างอัตโนมัติ, จัดกลุ่มรูปร่างใน Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: สร้างเอกสาร Word อย่างอัตโนมัติ, จัดกลุ่มรูปร่างใน Java
url: /th/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word ด้วยโปรแกรม, จัดกลุ่มรูปร่างใน Java

หากคุณต้องการ **สร้างเอกสาร Word ด้วยโปรแกรม**, คู่มือนี้จะพาคุณผ่านโซลูชันที่สมบูรณ์ คุณจะได้เห็นวิธี **จัดกลุ่มรูปร่างใน Word**, แทรกสี่เหลี่ยมผืนผ้า, ตั้งขนาด, และเพิ่มรูปร่างอื่น ๆ — ทั้งหมดโดยใช้ Java และไลบรารี Aspose.Words for Java

บทเรียนนี้ครอบคลุมทุกขั้นตอนตั้งแต่การตั้งค่าโปรเจกต์จนถึงการบันทึกไฟล์ .docx สุดท้าย เมื่อเสร็จแล้วคุณจะสามารถสร้างเอกสาร Word ที่มีสี่เหลี่ยมผืนผ้าและรูปภาพที่ถูกห่อหุ้มอยู่ในกลุ่มเดียว ทำให้ย้ายหรือปรับขนาดได้พร้อมกัน ไม่จำเป็นต้องมีประสบการณ์ก่อนกับ Aspose.Words API, แต่ควรมีสภาพแวดล้อมการพัฒนา Java เบื้องต้น

## ข้อกำหนดเบื้องต้น

* Java Development Kit (JDK) 8 หรือใหม่กว่า  
* Maven หรือ Gradle สำหรับจัดการ dependencies  
* Aspose.Words for Java 23.9 (หรือเวอร์ชันล่าสุด) – ไลบรารีนี้ใช้ฟรีสำหรับการประเมินผล  
* ไฟล์รูปภาพ (เช่น `sample.jpg`) ที่วางไว้ในไดเรกทอรีที่รู้จัก  

การมีสิ่งเหล่านี้พร้อมจะทำให้โค้ดทำงานได้โดยไม่ต้องกำหนดค่าเพิ่มเติม

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า Aspose.Words

สร้างโปรเจกต์ Maven (หรือเพิ่ม dependency ลงใน `pom.xml` ของคุณ):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

หากคุณใช้ Gradle, เพิ่มส่วนต่อไปนี้ใน `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

หลังจาก dependencies ถูกดึงมาเรียบร้อยแล้ว, ให้ import คลาสที่จำเป็นในไฟล์ Java ของคุณ:

```java
import com.aspose.words.*;
import java.io.File;
```

## ขั้นตอนที่ 2: สร้างเอกสาร Word ด้วยโปรแกรม

การดำเนินการแรกในทุกสถานการณ์อัตโนมัติคือการสร้างอ็อบเจกต์ `Document` และ `DocumentBuilder` ตัว builder จะทำให้การแทรกข้อความ, รูปภาพ, และรูปร่างง่ายขึ้น

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ในขณะนี้เอกสารยังอยู่ในหน่วยความจำเท่านั้น คุณสามารถเริ่มเพิ่มรูปร่างได้เลย

## ขั้นตอนที่ 3: แทรกสี่เหลี่ยมผืนผ้า – วิธีแทรกสี่เหลี่ยมผืนผ้า

สี่เหลี่ยมผืนผ้าเป็น `Shape` พื้นฐานที่มี `ShapeType.RECTANGLE` คุณสามารถควบคุมขนาดด้วย `setWidth`, `setHeight` และกำหนดตำแหน่งด้วย `setTop` และ `setLeft`

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**ทำไมจึงสำคัญ:** การกำหนดขนาดและตำแหน่งอย่างชัดเจน (`set shape size word`) จะทำให้สี่เหลี่ยมปรากฏตรงตำแหน่งที่คุณต้องการ ไม่ว่าจะมีการจัดวางเริ่มต้นของเอกสารอย่างไร

## ขั้นตอนที่ 4: แทรกรูปภาพ – เพิ่มรูปร่างลงในเอกสาร Word

`DocumentBuilder` สามารถแทรกรูปภาพโดยตรงจากเส้นทางไฟล์ หลังจากแทรกแล้ว คุณสามารถย้ายตำแหน่งรูปภาพได้เช่นเดียวกับรูปร่างอื่น ๆ

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

ตอนนี้สี่เหลี่ยมและรูปภาพเป็นรูปร่างอิสระภายในเอกสารแล้ว

## ขั้นตอนที่ 5: จัดกลุ่มรูปร่าง – วิธีจัดกลุ่มรูปร่างใน Word

การจัดกลุ่มรูปร่างเป็นประโยชน์เมื่อคุณต้องการย้ายหรือปรับขนาดหลายรูปร่างพร้อมกัน Aspose.Words มีคอนเทนเนอร์ `GroupShape` สำหรับจุดประสงค์นี้

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

เมื่อกลุ่มถูกบันทึก, Word จะถือรูปร่างลูกสองอันเป็นอ็อบเจกต์ตรรกะเดียว คุณสามารถเลือกกลุ่มแล้วลากได้, ทั้งสี่เหลี่ยมและรูปภาพจะเคลื่อนที่ตาม

## ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้าย, เขียนเอกสารลงดิสก์ เส้นทางต้องสามารถเขียนได้โดยกระบวนการ Java

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

การเรียกใช้เมธอด `main` จะสร้างไฟล์ชื่อ **GroupShapeExample.docx** เปิดไฟล์นี้ใน Microsoft Word คุณจะเห็นสี่เหลี่ยมและรูปภาพที่ล็อกไว้ด้วยกันในกลุ่ม การเลือกกลุ่มจะทำให้ทั้งสองอ็อบเจกต์เคลื่อนที่พร้อมกัน, ยืนยันว่าการจัดกลุ่มสำเร็จ

## ผลลัพธ์ที่คาดหวัง

* ไฟล์ Word (`GroupShapeExample.docx`) อยู่ในไดเรกทอรีที่คุณระบุ  
* ภายในไฟล์, สี่เหลี่ยม (เติมสีเทาอ่อน) ปรากฏที่มุมบนซ้าย, และรูปภาพอยู่ด้านล่างโดยตรง  
* ทั้งสองอ็อบเจกต์เป็นส่วนหนึ่งของกลุ่มเดียว, ดังนั้นการลากอันหนึ่งจะลากอีกอันด้วย

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | คำแนะนำ |
|-----------|----------|
| **รูปแบบภาพที่ต่างกัน** | Aspose.Words รองรับ PNG, BMP, GIF, และ TIFF. ใช้นามสกุลไฟล์ที่เหมาะสมใน `insertImage`. |
| **ขนาดเป็นค่าลบ** | API จะโยน `ArgumentException`. ควรตรวจสอบความกว้างและความสูงก่อนเรียก `setWidth` / `setHeight`. |
| **เอกสารขนาดใหญ่** | การจัดกลุ่มรูปร่างจำนวนมากอาจทำให้ไฟล์ใหญ่ขึ้น. พิจารณาแปลงรูปร่างหลายอันเป็นรูปภาพเดียวเมื่อประสิทธิภาพเป็นเรื่องสำคัญ. |
| **ความเข้ากันได้กับเวอร์ชัน Word** | GroupShape ทำงานกับ Word 2007 (`.docx`) และรุ่นต่อ ๆ ไป. สำหรับไฟล์ `.doc` เก่า, กลุ่มจะถูกแปลงเป็นแบน. |
| **การกำหนดตำแหน่งแบบไดนามิก** | ใช้การคำนวณจากขนาดหน้า (`doc.getFirstSection().getPageSetup().getPageWidth()`) หากต้องการวางตำแหน่งแบบปรับตัว. |

**เคล็ดลับมืออาชีพ:** หลังจากสร้างกลุ่ม, คุณสามารถเปลี่ยนแปลง  

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณเอง

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}