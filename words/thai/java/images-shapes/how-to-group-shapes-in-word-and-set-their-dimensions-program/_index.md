---
category: general
date: 2026-11-25
description: วิธีการจัดกลุ่มรูปร่างใน Word ด้วย Java และวิธีการตั้งค่าขนาดรูปร่างในไฟล์
  DOCX ด้วย Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: th
lastmod: 2026-11-25
og_description: วิธีจัดกลุ่มรูปร่างใน Word ด้วย Aspose.Words Java API และตั้งขนาดรูปร่างใน
  Word อย่างรวดเร็ว ทำตามวิธีแก้ปัญหาแบบครบถ้วนและเป็นขั้นตอน
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: วิธีจัดกลุ่มรูปร่างใน Word และตั้งค่าขนาด – คู่มือ Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: วิธีจัดกลุ่มรูปร่างใน Word และตั้งค่าขนาดของมันโดยเขียนโปรแกรม
url: /th/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการจัดกลุ่มรูปร่างใน Word และกำหนดขนาดของพวกมันโดยโปรแกรม

หากคุณต้องการ **วิธีการจัดกลุ่มรูปร่างใน Word** และควบคุมขนาดที่แม่นยำ คู่มือนี้จะแสดงวิธีแก้ไขที่สมบูรณ์และสามารถรันได้ โดยใช้ Aspose.Words for Java คุณสามารถสร้างสี่เหลี่ยมผืนผ้า, วงรี, เพิ่มพวกมันเข้าไปใน `GroupShape` แล้ว **วิธีการตั้งค่าขนาดของรูปร่าง** เช่น ความกว้างและความสูงในไฟล์ DOCX เดียว

คุณจะได้เรียนรู้วิธี:

* สร้างเอกสาร Word ใหม่ตั้งแต่ต้น  
* แทรก `GroupShape` (API ใหม่ในเวอร์ชัน 24.9)  
* เพิ่มสี่เหลี่ยมผืนผ้าและวงรีเข้าไปในกลุ่ม  
* **ตั้งค่าขนาดรูปร่างใน Word** อย่างแม่นยำด้วย `setWidth` และ `setHeight`  
* บันทึกเอกสารลงดิสก์

ไม่ต้องใช้เครื่องมือภายนอก—เพียง Java 17+, Maven, และไลบรารี Aspose.Words for Java

## ข้อกำหนดเบื้องต้น

* Java Development Kit 17 หรือใหม่กว่า  
* Maven (หรือ Gradle) สำหรับการจัดการ dependency  
* Aspose.Words for Java 24.9 หรือใหม่กว่า (API `GroupShape` ถูกเพิ่มใน 24.9)  
* ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java และแนวคิดเชิงวัตถุ

หากคุณยังไม่ได้เพิ่ม Aspose.Words ลงในโปรเจกต์ของคุณ ให้ใส่ dependency ของ Maven ดังต่อไปนี้:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## ขั้นตอนที่ 1: สร้างเอกสารใหม่และ DocumentBuilder

คลาส `Document` แทนไฟล์ Word ทั้งหมด ในขณะที่ `DocumentBuilder` ให้วิธีที่สะดวกในการเพิ่มเนื้อหา

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*ทำไมต้องทำขั้นตอนนี้?*  
การสร้าง `Document` ใหม่ให้คุณมีผ้าใบที่สะอาด `DocumentBuilder` เป็นตัวช่วยระดับสูงที่ทำให้คุณสามารถแทรกย่อหน้า, ตาราง, และในกรณีนี้คือรูปร่างได้

## ขั้นตอนที่ 2: แทรก GroupShape (API ใหม่ในเวอร์ชัน 24.9)

`GroupShape` ทำหน้าที่เป็นคอนเทนเนอร์; รูปร่างใด ๆ ที่คุณเพิ่มจะกลายเป็นส่วนหนึ่งของกลุ่มภาพเดียวกัน

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*ทำไมต้องใช้ `GroupShape`?*  
การจัดกลุ่มรูปร่างทำให้การย้าย, หมุน, หรือกำหนดรูปแบบหลายวัตถุพร้อมกันเป็นเรื่องง่าย API นี้เพิ่มใน 24.9 ดังนั้นเวอร์ชันเก่าจะไม่สามารถคอมไพล์บรรทัดนี้ได้

## ขั้นตอนที่ 3: สร้างสี่เหลี่ยมผืนผ้า, ตั้งค่าขนาด, แล้วเพิ่มเข้าไปในกลุ่ม

ที่นี่เราจะแสดง **วิธีการตั้งค่าขนาดของรูปร่าง** สำหรับสี่เหลี่ยมผืนผ้า

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*ทำไมต้องกำหนดความกว้างและความสูงอย่างชัดเจน?*  
Word เก็บขนาดของรูปร่างเป็นหน่วยจุด (points) การเรียก `setWidth` และ `setHeight` ทำให้คุณควบคุมพื้นที่การแสดงผลได้อย่างแม่นยำ ซึ่งจำเป็นเมื่อคุณต้องการการจัดวางที่ละเอียดหรือเมื่อต้องส่งออกเป็น PDF

## ขั้นตอนที่ 4: สร้างวงรี, ตั้งค่าขนาด, แล้วเพิ่มเข้าไปในกลุ่มเดียวกัน

เทคนิค **set shape size word** เดียวกันทำงานได้กับรูปแบบใด ๆ

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*ทำไมต้องเพิ่มวงรีเข้าไปใน `GroupShape` เดียวกัน?*  
รูปร่างทั้งสองจะเคลื่อนที่ร่วมกันเป็นหน่วยเดียว ซึ่งมีประโยชน์สำหรับการสร้างไอคอน, โลโก้, หรือไดอะแกรมซับซ้อนที่ต้องการให้ตำแหน่งสัมพันธ์กัน

## ขั้นตอนที่ 5: บันทึกเอกสารพร้อมรูปร่างที่จัดกลุ่ม

สุดท้ายให้บันทึกไฟล์ DOCX ลงดิสก์

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

การรันโปรแกรมนี้จะสร้างไฟล์ชื่อ **GroupShape.docx** ที่มีสี่เหลี่ยมผืนผ้าและวงรีจัดกลุ่มไว้ด้วยกัน เมื่อเปิดไฟล์ใน Microsoft Word คุณจะเห็นว่ารูปร่างทั้งสองทำงานเป็นอ็อบเจกต์เดียว—you can drag, resize, or rotate them together.

### ผลลัพธ์ที่คาดหวัง

* เอกสาร Word (`GroupShape.docx`) หนึ่งหน้า  
* `GroupShape` ที่ประกอบด้วยสี่เหลี่ยมผืนผ้า 100 × 50 pt และวงรี 80 × 80 pt  
* การเลือกรูปร่างใดรูปร่างหนึ่งจะเลือกทั้งกลุ่ม

## คำถามทั่วไปและกรณีขอบ

### วิธีการเปลี่ยนตำแหน่งของรูปร่างที่จัดกลุ่ม?

หลังจากสร้าง `GroupShape` แล้ว คุณสามารถตั้งค่า `left` และ `top` ได้ดังนี้:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

พิกัดเหล่านี้ก็วัดเป็นหน่วยจุดเช่นกัน

### ถ้าต้องการเพิ่มรูปร่างมากกว่าสองรูป?

`GroupShape` ทำงานเหมือนคอนเทนเนอร์อื่น ๆ เรียก `groupShape.appendChild(yourShape)` สำหรับแต่ละรูปร่างที่เพิ่มเข้าไป API ไม่จำกัดจำนวนลูก

### สามารถกำหนดสไตล์ (สีเติม, ความหนาของเส้น) ให้กับรูปร่างแต่ละอันได้หรือไม่?

ได้ แต่ละอ็อบเจกต์ `Shape` มีคุณสมบัติการจัดรูปแบบดังนี้:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### โค้ดนี้ทำงานกับ Aspose.Words เวอร์ชันเก่าได้หรือไม่?

เมธอด `insertGroupShape` ถูกเพิ่มในเวอร์ชัน 24.9 หากคุณใช้เวอร์ชันก่อนหน้า คุณต้องสร้าง `GroupShape` ด้วยตนเองผ่านโครงสร้าง node ซึ่งซับซ้อนกว่า การอัปเกรดเป็นวิธีที่แนะนำ

## เคล็ดลับระดับมืออาชีพ

* **ใช้หน่วยจุดเพื่อความสอดคล้อง** – หน่วยภายในของ Word คือจุด (1/72 inch) การแปลงจากพิกเซลหรือเซนติเมตรอาจทำให้ขนาดไม่ตรงตามที่คาด  
* **จัดกลุ่มก่อนกำหนดตำแหน่ง** – กำหนดตำแหน่งของ `GroupShape` หลังจากเพิ่มลูกทั้งหมดแล้ว; มิฉะนั้นคุณอาจต้องคำนวณออฟเซ็ตใหม่  
* **ใช้ DocumentBuilder ซ้ำ** – คุณสามารถแทรกหลายกลุ่มในเอกสารเดียวกันได้โดยย้ายเคอร์เซอร์ของ builder (`builder.moveTo`) ก่อนเรียก `insertGroupShape` ทุกครั้ง

## สรุป

ตอนนี้คุณมีตัวอย่างครบวงจรจากต้นจนจบของ **วิธีการจัดกลุ่มรูปร่างใน Word** และ **วิธีการตั้งค่าขนาดของรูปร่าง** ด้วย Aspose.Words for Java บทเรียนได้ครอบคลุมการสร้างเอกสาร, แทรก `GroupShape`, เพิ่มสี่เหลี่ยมผืนผ้าและวงรี, ตั้งค่าขนาดที่แม่นยำ, และบันทึกผลลัพธ์

ต่อจากนี้คุณสามารถสำรวจต่อได้:

* เพิ่มกล่องข้อความหรือรูปภาพเข้าไปในกลุ่มเดียวกัน  
* ทำแอนิเมชันให้กับรูปร่างที่จัดกลุ่มโดยใช้ฟีเจอร์ SmartArt ของ Word (ผ่าน API)  
* ส่งออกรูปร่างที่จัดกลุ่มเป็น PDF หรือ SVG เพื่อใช้บนเว็บ

อย่ากลัวที่จะทดลองกับประเภทรูปร่าง, ขนาด, และตำแหน่งต่าง ๆ—การจัดกลุ่มให้คุณควบคุมการจัดวางที่ซับซ้อนได้อย่างมีประสิทธิภาพในเอกสาร Word

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}