---
category: general
date: 2026-11-15
description: สร้างรูปสี่เหลี่ยมใน Word ด้วย Java และเรียนรู้วิธีเพิ่มรูปทรงใน Word
  ตั้งค่าขนาดรูปทรง และบันทึกเอกสาร Word อย่างมีประสิทธิภาพ
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: th
lastmod: 2026-11-15
og_description: สร้างรูปสี่เหลี่ยมผืนผ้าในเอกสาร Word ด้วย Java เรียนรู้วิธีเพิ่มรูปทรงใน
  Word ตั้งค่าขนาดรูปทรง และบันทึกเอกสาร Word ได้ในไม่กี่นาที.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: สร้างรูปสี่เหลี่ยมใน Word ด้วย Java – คู่มือขั้นตอนต่อขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: สร้างรูปสี่เหลี่ยมผืนผ้าในเอกสาร Word ด้วย Java
url: /th/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java

หากคุณต้องการ **สร้างรูปสี่เหลี่ยม** ภายในไฟล์ Word คำแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนที่ทำด้วย Java อย่างชัดเจน คุณจะได้เรียนรู้วิธี **เพิ่มรูปทรงลงใน Word**, ควบคุม **การตั้งค่าขนาดรูปทรง**, และสุดท้าย **บันทึกเอกสาร Word** โดยไม่ต้องออกจาก IDE ของคุณ  

ในส่วนต่อไปนี้คุณจะได้รับตัวอย่างที่ทำงานได้เต็มรูปแบบ คำอธิบายของแต่ละบรรทัด และเคล็ดลับสำหรับปัญหาที่พบบ่อย เช่น ปัญหาขนาดและความเข้ากันได้ของเอกสาร ไม่จำเป็นต้องอ้างอิงภายนอก—เพียงแค่ใช้ไลบรารี Aspose.Words for Java

## สิ่งที่คุณจะได้เรียนรู้

* วิธีการเริ่มต้น `Document` และ `DocumentBuilder`
* วิธีการแทรก **group shape** และวางสี่เหลี่ยมภายใน
* วิธี **กำหนดขนาดรูปทรง** ด้วย `setWidth` และ `setHeight`
* วิธี **บันทึกเอกสาร Word** ในรูปแบบ `.docx`
* การจัดการกรณีขอบสำหรับขนาดหน้าและการตั้งค่า DPI ที่แตกต่างกัน

### ข้อกำหนดเบื้องต้น

* Java 17 หรือใหม่กว่า (โค้ดยังคอมไพล์ได้กับ Java 8 ด้วย)
* Aspose.Words for Java 23.10 หรือใหม่กว่า – สามารถดาวน์โหลดได้จาก Maven Central
* ความเข้าใจพื้นฐานเกี่ยวกับไวยากรณ์ Java และแนวคิดเชิงวัตถุ

> **Pro tip:** หากคุณวางแผนจะเพิ่มรูปทรงอื่นในภายหลัง (เช่น วงกลมหรือกล่องข้อความ) ให้เก็บไว้ใน `GroupShape` เดียวกัน จะทำให้การย้าย, การหมุน, หรือการจัดรูปแบบของคอลเลกชันทั้งหมดทำได้ง่ายขึ้น

## ขั้นตอนที่ 1: เริ่มต้นเอกสารและ builder

ขั้นตอนแรกคือการสร้างไฟล์ Word เปล่าและ `DocumentBuilder` ที่ช่วยให้คุณเขียนเนื้อหา  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*ทำไมจึงสำคัญ:* `Document` แทนไฟล์ทั้งหมด ในขณะที่ `DocumentBuilder` ให้เมธอดระดับสูงสำหรับแทรกข้อความ, ตาราง, และ **รูปทรง** หากไม่มี builder คุณจะต้องจัดการโหนดระดับต่ำด้วยตนเอง

## ขั้นตอนที่ 2: แทรก group shape เพื่อเก็บหลายรูปทรง

**group shape** ทำหน้าที่เหมือนคอนเทนเนอร์; คุณสามารถเพิ่มรูปทรงหลายรูปและจัดการเป็นอ็อบเจกต์เดียวในภายหลัง (เช่น ย้ายหรือหมุนพร้อมกัน)

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*ทำไมต้องใช้ group shape?* หากคุณในภายหลังต้องการเพิ่มลูกศร, วงกลม, หรือป้ายกำกับรอบสี่เหลี่ยม กลุ่มนี้จะทำให้ทุกอย่างจัดตำแหน่งได้อย่างสอดคล้อง นอกจากนี้ยังทำให้ขั้นตอน **add shapes to Word** ง่ายขึ้นเพราะคุณต้องเรียก `appendChild` เพียงครั้งเดียวต่อรูปทรงใหม่

## ขั้นตอนที่ 3: สร้างรูปสี่เหลี่ยม

ตอนนี้เราจะสร้างสี่เหลี่ยมจริงที่อยู่ภายใน group ตัวสร้าง `Shape` ต้องการ `Document` เจ้าของและประเภทของรูปทรงที่ต้องการ

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*ทำไมต้องเป็นสี่เหลี่ยม?* `ShapeType.RECTANGLE` เป็น primitive ที่ใช้บ่อยที่สุดสำหรับไฮไลท์ส่วน, สร้าง placeholder, หรือวาด mock‑up UI อย่างง่ายโดยตรงใน Word

## ขั้นตอนที่ 4: กำหนดขนาดของสี่เหลี่ยม

การตั้งค่ามิติเป็นจุดที่ **set shape dimensions** มีความสำคัญ คุณสามารถใช้หน่วยวัดใดก็ได้ที่ Aspose.Words รองรับ; ค่าเริ่มต้นคือ points (1 pt = 1/72 inch)

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Note:** หากต้องการใช้มิลลิเมตร ให้เรียก `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` โดยที่ `1.39 in ≈ 35 mm` ตัวอย่างนี้แสดงความยืดหยุ่นของ **define shape size**

## ขั้นตอนที่ 5: เพิ่มสี่เหลี่ยมลงใน group shape

การต่อสี่เหลี่ยมเข้ากับ group ที่สร้างไว้ก่อนหน้านี้ทำให้มันปรากฏในเอกสาร

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

ในขณะนี้สี่เหลี่ยมจะอยู่ที่มุมซ้ายบนของ group คุณสามารถย้ายภายหลังด้วย `rectangle.setLeft(...)` และ `rectangle.setTop(...)` หากต้องการตำแหน่งที่แม่นยำ

## ขั้นตอนที่ 6: (ทางเลือก) บันทึกเอกสารเพื่อดูผลลัพธ์

สุดท้ายให้เขียนเอกสารลงดิสก์ นี่คือขั้นตอน **save Word document** ที่สร้างไฟล์ `.docx` ที่คุณสามารถเปิดใน Microsoft Word, LibreOffice, หรือ Google Docs

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `RectangleShapeDemo.docx` ที่มีสี่เหลี่ยมหนึ่งรูปอยู่ภายใน group shape การเปิดไฟล์จะแสดงสี่เหลี่ยมสีขาวธรรมดา—ขนาดตรงตามที่คุณกำหนด

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ Word ชื่อ `RectangleShapeDemo.docx`
* ในย่อหน้าแรก มี group shape ที่บรรจุสี่เหลี่ยมขนาด 100 pt × 50 pt
* ไม่มีข้อความใดเพิ่มเข้าไป ดังนั้นสี่เหลี่ยมจะแสดงบนหน้าเปล่า

## ความแตกต่างทั่วไปและกรณีขอบ

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Different page size** (e.g., A4) | Call `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` before inserting the shape. |
| **Higher DPI for printing** | Multiply width/height by the desired DPI factor, e.g., `rectangle.setWidth(200 * 2);` for double resolution. |
| **Adding a text label inside the rectangle** | Create a `Shape` of type `TEXT_BOX`, set its `setWidth`/`setHeight` to match the rectangle, then add it to the same `GroupShape`. |
| **Rotating the rectangle** | Use `rectangle.setRotationAngle(45);` to rotate 45 degrees clockwise. |
| **Saving as PDF instead of DOCX** | Replace `document.save("output.docx");` with `document.save("output.pdf");` – the same API works for PDF, preserving the rectangle. |

## เคล็ดลับระดับมืออาชีพสำหรับการทำงานที่มั่นคง

1. **Reuse the builder** – หลังจากแทรก group shape แล้ว คุณสามารถเพิ่มย่อหน้า หรือ ตารางต่อได้โดยไม่ต้องสร้าง builder ใหม่
2. **Dispose resources** – แม้ว่า garbage collector ของ Java จะจัดการส่วนใหญ่แล้ว การเรียก `document.close();` (ถ้าใช้ stream) อย่างชัดเจนจะช่วยป้องกันการรั่วของ file‑handle
3. **Validate dimensions** – ก่อนเรียก `setWidth`/`setHeight` ให้ตรวจสอบว่าค่ามีค่าเป็นบวก; ค่าลบจะทำให้เกิด `IllegalArgumentException`
4. **Version compatibility** – โค้ดทำงานกับ Aspose.Words 23.x ขึ้นไป เวอร์ชันก่อนอาจต้องใช้ `Shape.setSize(width, height)` แทนการตั้งค่าแยก

## ตัวอย่างเต็มที่สามารถรันได้

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Result verification:** เปิด `output/RectangleShapeDemo.docx` ใน Microsoft Word คุณควรเห็นสี่เหลี่ยมขนาดที่กำหนดไว้ อยู่กึ่งกลางด้านบนของหน้าแรก หากสี่เหลี่ยมแสดงขนาดเล็กเกินไป ให้ปรับค่าที่ส่งให้ `setWidth` และ `setHeight`

## สรุป

คุณได้เรียนรู้วิธี **สร้างรูปสี่เหลี่ยม** ในไฟล์ Word ด้วย Java, วิธี **เพิ่มรูปทรงลงใน Word** ผ่าน `GroupShape`, วิธี **ตั้งค่าขนาดรูปทรง** และ **กำหนดขนาดรูปทรง**, และสุดท้ายวิธี **บันทึกเอกสาร Word** เพื่อแจกจ่าย รูปแบบเดียวกันนี้ใช้ได้กับรูปทรงอื่น ๆ ทำให้คุณสามารถสร้างแผนภาพซับซ้อนได้โดยอัตโนมัติ

### ขั้นตอนต่อไปคืออะไร?

* สำรวจ **add shapes to Word** ด้วยการแทรกวงกลม, ลูกศร, หรือกล่องข้อความ
* รวมหลายรูปทรงเป็น `GroupShape` เดียวและใช้การแปลง (หมุน, พลิก)
* สร้างรายงานที่ฝังแผนภูมิเป็นรูปทรง แล้ว **บันทึกเอกสาร Word** เป็น PDF เพื่อแชร์

ลองปรับขนาด, สี, และตำแหน่งตามความต้องการของคุณเอง Happy coding!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}