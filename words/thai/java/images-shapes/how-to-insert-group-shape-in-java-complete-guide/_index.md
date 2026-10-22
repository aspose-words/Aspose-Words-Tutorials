---
category: general
date: 2026-07-16
description: วิธีแทรกกลุ่มรูปทรงใน Java ด้วย Aspose.Words – เพิ่มรูปสี่เหลี่ยม, ตั้งค่าขนาดรูปทรง,
  และสร้างสี่เหลี่ยมสีและวงกลม.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: th
lastmod: 2026-07-16
og_description: 'วิธีแทรกกลุ่มรูปทรงใน Java: คู่มือเชิงปฏิบัติเพื่อเพิ่มรูปสี่เหลี่ยม,
  ตั้งค่าขนาดรูปทรง, และสร้างสี่เหลี่ยมสีและวงกลมสีด้วย Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: แทรก Group Shape ใน Java – บทเรียน Aspose.Words อย่างเต็ม
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: วิธีแทรกกลุ่มรูปร่างใน Java – คู่มือฉบับสมบูรณ์
url: /th/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทรกกลุ่มรูปทรงใน Java – คู่มือฉบับสมบูรณ์

เคยสงสัย **วิธีแทรกกลุ่มรูปทรง** ในเอกสาร Word ด้วย Java หรือไม่? คุณไม่ได้เป็นคนเดียว ไม่ว่าคุณจะสร้างตัวสร้างรายงานหรือผู้สร้างโบรชัวร์แบบไดนามิก การจัดกลุ่มรูปทรงช่วยให้การจัดวางของคุณเป็นระเบียบและโค้ดของคุณจัดการได้ง่ายขึ้น.

ในบทแนะนำนี้เราจะเดินผ่านขั้นตอนที่แน่นอนเพื่อ **เพิ่มรูปสี่เหลี่ยม**, **ตั้งค่าขนาดรูปทรง**, และ **สร้างสี่เหลี่ยมสี** และ **สร้างวงกลมสี** โดยใช้ไลบรารี Aspose.Words. เมื่อเสร็จคุณจะมีโปรแกรมที่สามารถรันได้ซึ่งสร้างไฟล์ .docx ที่มีสี่เหลี่ยมสีน้ำเงินและวงกลมสีแดงที่ถูกห่ออย่างเรียบร้อยภายในกลุ่ม.

## ข้อกำหนดเบื้องต้น

- Java 17 (หรือ JDK ล่าสุดใด ๆ) ที่ติดตั้งและกำหนดค่าแล้ว.
- Maven หรือ Gradle เพื่อจัดการ dependencies.
- Aspose.Words for Java 23.9 หรือใหม่กว่า – คุณสามารถดาวน์โหลดได้จาก Maven Central.
- ความเข้าใจพื้นฐานของไวยากรณ์ Java – ไม่จำเป็นต้องมีอะไรซับซ้อน.

หากคุณขาดสิ่งใดสิ่งหนึ่งเหล่านี้ ให้ดาวน์โหลด JDK จากเว็บไซต์ของ Oracle และเพิ่ม dependency ของ Aspose.Words ลงใน `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

เมื่อพื้นฐานพร้อมแล้ว มาเริ่มทำกันเลย.

## วิธีแทรกกลุ่มรูปทรง – ภาพรวม

แนวคิดหลักง่าย ๆ คือ: สร้าง `Document` เปิด `DocumentBuilder` แทรก **กลุ่มรูปทรง**, จากนั้นใส่รูปทรงแต่ละอัน (สี่เหลี่ยมและวงกลม) ลงในกลุ่มนั้น กลุ่มทำหน้าที่เป็นคอนเทนเนอร์ ดังนั้นการย้ายภายหลังจะทำให้ทุกอย่างภายในเคลื่อนที่ไปด้วย – เหมาะสำหรับการจัดวางที่ซับซ้อน.

ด้านล่างเป็นโค้ดเต็มที่พร้อมรัน คุณสามารถคัดลอกและวางลงในคลาส Java ใหม่ชื่อ `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **เคล็ดลับ:** ค่า `setLeft` และ `setTop` จะอิงตามจุดเริ่มต้นของกลุ่ม ไม่ใช่หน้ากระดาษ ซึ่งทำให้การย้ายตำแหน่งของกลุ่มทั้งหมดเป็นเรื่องง่ายในภายหลัง.

### เกิดอะไรขึ้นบ้าง?

1. **Document & Builder** – เราเริ่มต้นไฟล์ Word เปล่าและ `DocumentBuilder` ที่ให้เราสามารถแทรกเนื้อหาได้.
2. **Group Shape** – `builder.insertGroupShape()` สร้างคอนเทนเนอร์ คิดว่าเป็นโฟลเดอร์สำหรับวัตถุการวาด.
3. **Blue Rectangle** – เราสร้างอินสแตนซ์ของ `Shape` ชนิด `RECTANGLE` ตั้งขนาด ตำแหน่ง และเติมสีฟ้า – นี่คือขั้นตอน **create colored rectangle**.
4. **Red Circle** – ใช้รูปแบบเดียวกัน แต่ใช้ `ELLIPSE` เพื่อสร้างวงกลมที่สมบูรณ์ แล้วเติมสีแดง – นี่คือส่วน **create colored circle**.
5. **Saving** – สุดท้ายเราบันทึกทุกอย่างเป็น `GroupShapeDemo.docx`.

รันโปรแกรม (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) แล้วเปิดไฟล์ที่ได้ คุณควรเห็นสี่เหลี่ยมสีน้ำเงินทางซ้ายและวงกลมสีแดงทางขวา ทั้งสองถูกล็อคอยู่ภายในกล่องกลุ่มเดียว.

## การเพิ่มรูปสี่เหลี่ยม

หากคุณต้องการสี่เหลี่ยมโดยไม่ต้องจัดกลุ่ม คุณสามารถข้ามการเรียก `insertGroupShape()` และเพิ่มสี่เหลี่ยมโดยตรงลงใน body ของเอกสาร อย่างไรก็ตาม การจัดกลุ่มให้ความยืดหยุ่นในการย้าย, หมุน, หรือ ลบหลายรูปพร้อมกัน.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

สังเกตว่าเราใช้ตรรกะ **add rectangle shape** ที่นี่ สี่เหลี่ยมปรากฏบนหน้าเป็นวัตถุอิสระ ในสถานการณ์จริงส่วนใหญ่คุณจะต้องการกลุ่ม เนื่องจากมันรักษาการจัดตำแหน่งเชิงสัมพันธ์.

## การตั้งค่าขนาดรูปทรง

เมื่อคุณเห็นเมธอดเช่น `setWidth` และ `setHeight` จำไว้ว่า พวกมันรับค่าเป็น **points** (1/72 inch). หากคุณต้องการใช้มิลลิเมตร ให้แปลงก่อน:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

โค้ดส่วนนี้แสดงการ **set shape dimensions** พร้อมการแปลงหน่วย – มีประโยชน์เมื่อสเปคการออกแบบของคุณมาจาก mockup UI ที่ใช้หน่วยเมตริก.

## การสร้างสี่เหลี่ยมสี

การเติมสีให้รูปทรงง่ายเพียงเรียก `getFill().setForeColor()` คุณสามารถส่งค่า `java.awt.Color` ใดก็ได้ ต้องการไล่สี? ใช้ `setForeColor` สำหรับสีเริ่มต้นและ `setBackColor` สำหรับสีสุดท้าย.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

นี่เป็นวิธีเร็วในการ **create colored rectangle** ด้วยการเติมไล่สีแทนสีทึบ.

## การสร้างวงกลมสี

วงกลมเป็นเพียง ellipse ที่มีความกว้างและความสูงเท่ากัน ตรรกะการเติมสีเดียวกันใช้ได้:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

หากคุณต้องการเติมสีโปร่งใส ให้ตั้งค่า alpha channel:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

ตอนนี้คุณได้เชี่ยวชาญเทคนิค **create colored circle** แล้ว.

## การบันทึกเอกสาร

Aspose.Words ให้คุณส่งออกเป็นหลายรูปแบบ: DOCX, PDF, HTML, PNG, ตามที่คุณต้องการ สำหรับการสาธิตนี้เรายังคงใช้ DOCX เพราะมันรักษารูปทรงเวกเตอร์ได้อย่างสมบูรณ์.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

การเปลี่ยน `SaveFormat` เพียงเท่านี้ก็สามารถสร้างเวอร์ชัน PDF ของงานศิลปะที่จัดกลุ่มเดียวกันได้.

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

- **ลืมเพิ่มรูปทรงเข้าไปในกลุ่ม?** รูปทรงจะปรากฏบนหน้าแต่จะไม่เคลื่อนที่พร้อมกับกลุ่ม ต้องเรียก `group.appendChild(yourShape)` เสมอ.

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ.

- [สร้างเอกสาร Word ด้วย Java – เพิ่มรูปสี่เหลี่ยมพร้อมเอฟเฟกต์เงา](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}