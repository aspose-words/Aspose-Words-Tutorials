---
category: general
date: 2026-11-22
description: เพิ่มรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java ตั้งขนาดรูปทรง จัดกลุ่มหลายรูปทรง
  และเพิ่มรูปเข้าไปในกลุ่มอย่างมีประสิทธิภาพ
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: th
lastmod: 2026-11-22
og_description: เพิ่มรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java จากนั้นตั้งค่าขนาดของรูป,
  จัดกลุ่มหลายรูป, และเพิ่มรูปเข้าไปในกลุ่มในกระบวนการทำงานเดียว.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: เพิ่มรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Java – คู่มือฉบับเต็ม
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: เพิ่มรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Java
url: /th/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มรูปสี่เหลี่ยมและจัดกลุ่มรูปร่างใน Java

หากคุณต้องการ **add rectangle shape** ไปยังเอกสาร Word ด้วย Java คำแนะนำนี้จะพาคุณผ่านขั้นตอนอย่างละเอียด คุณจะได้เรียนรู้วิธี **set shape size**, **group multiple shapes**, และ **append shape to group** โดยไม่ต้องออกจาก IDE

การทำงานกับกราฟิกเวกเตอร์ภายในไฟล์ DOCX มักจะรู้สึกเหมือนต้องจัดการกับ API หลายตัว ในตอนท้ายของบทแนะนำนี้คุณจะมีโปรแกรมเดียวที่ทำงานอิสระซึ่งสร้างรูปสี่เหลี่ยม, รูปวงรี, และรูปร่างเพิ่มเติมที่คุณอาจต้องการ แล้วจัดกลุ่มพวกมันเพื่อให้เคลื่อนที่เป็นวัตถุเดียว ไม่จำเป็นต้องใช้เครื่องมือภายนอกใด ๆ นอกจาก Aspose.Words for Java

## ข้อกำหนดเบื้องต้น

* ติดตั้ง Java 17 หรือรุ่นที่ใหม่กว่า
* Maven 3.8+ (หรือ Gradle) เพื่อจัดการ dependencies
* ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (รุ่นทดลองใช้ได้สำหรับการทดสอบ)
* IDE เช่น IntelliJ IDEA หรือ VS Code แม้ว่าเครื่องมือแก้ไขข้อความใด ๆ ก็ใช้ได้

ข้อกำหนดเหล่านี้ทำให้โค้ดสามารถคอมไพล์และรันได้บนสภาพแวดล้อมการพัฒนาที่ทันสมัยใด ๆ

## ขั้นตอนที่ 1: ตั้งค่าโครงการ Maven

สร้างโครงการ Maven ใหม่หรือเพิ่ม dependency ของ Aspose.Words ลงใน `pom.xml` ที่มีอยู่:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

## ขั้นตอนที่ 2: โหลดเอกสารและสร้าง DocumentBuilder

`DocumentBuilder` ให้ API ที่เป็น fluent สำหรับแทรกเนื้อหา โหลด DOCX ที่มีอยู่หรือเริ่มจากเอกสารเปล่า:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

การสร้าง builder ตั้งแต่ต้นจะทำให้คุณมีเคอร์เซอร์อยู่ที่จุดเริ่มต้นของเอกสาร พร้อมสำหรับการแทรกรูปร่าง

## เพิ่มรูปสี่เหลี่ยมลงในเอกสาร Word

### ขั้นตอนที่ 3: แทรกรูปสี่เหลี่ยม

รูปสี่เหลี่ยมเป็นองค์ประกอบภาพแรกที่เราต้องการวางในเอกสาร โดยใช้คอนสตรัคเตอร์ `Shape` กับ `ShapeType.RECTANGLE` คุณจะได้อ็อบเจกต์ที่สามารถแก้ไขได้เต็มที่

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

การเพิ่มรูปสี่เหลี่ยมในขั้นตอนนี้จะไม่ส่งผลต่อการจัดวางจนกว่าจะกำหนดขนาดและเพิ่มเข้าไปในคอนเทนเนอร์

### ตั้งค่าขนาดและมิติของรูปร่าง

#### ขั้นตอนที่ 4: กำหนดความกว้างและความสูง

การตั้งค่ามิติของรูปร่างจะกำหนดว่ามันแสดงผลบนหน้าอย่างไร ค่า ความกว้างและความสูงวัดเป็นจุด (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

คุณสามารถปรับตัวเลขเหล่านี้ให้ตรงกับความต้องการออกแบบของคุณ วิธีเดียวกันใช้ได้กับอ็อบเจกต์ `Shape` ใด ๆ ดังนั้นคุณจึงสามารถนำกลับมาใช้ใหม่สำหรับวงกลม, ลูกศร หรือการวาดแบบกำหนดเอง

#### ขั้นตอนที่ 5: แทรกรูปสี่เหลี่ยมลงในเอกสาร

เมื่อรูปสี่เหลี่ยมมีขนาดแล้ว ให้วางลงบนหน้า เมธอด `insertShape` ของ `DocumentBuilder` จะเพิ่มรูปร่างที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

ในขั้นตอนนี้รูปสี่เหลี่ยมจะแสดงเป็นอันเดียวบนหน้า ขั้นตอนต่อไปจะแสดงวิธีรวมกับรูปร่างอื่น

## จัดกลุ่มหลายรูปร่างเข้าด้วยกัน

การจัดกลุ่มรูปร่างทำให้คุณสามารถย้าย, หมุน หรือปรับขนาดเป็นหน่วยเดียว ซึ่งมีประโยชน์อย่างยิ่งสำหรับการสร้างแผนภาพซับซ้อน

### ขั้นตอนที่ 6: สร้างคอนเทนเนอร์ group shape

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

การเรียก `insertGroupShape` จะเพิ่มคอนเทนเนอร์ว่างลงในเอกสาร รูปร่างใด ๆ ที่เพิ่มเข้าไปในคอนเทนเนอร์นี้จะเป็นส่วนหนึ่งของกลุ่ม

### เพิ่มรูปร่างเข้าไปในกลุ่ม

#### ขั้นตอนที่ 7: เพิ่มรูปสี่เหลี่ยมเข้าไปในกลุ่ม

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

การเพิ่มจะย้ายรูปสี่เหลี่ยมจากเนื้อหาเอกสารไปยังคอลเลกชันภายในของกลุ่ม ตอนนี้รูปสี่เหลี่ยมจะเคารพการแปลงของกลุ่ม

#### ขั้นตอนที่ 8: เพิ่มรูปวงรีเพื่อสาธิต

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

รูปวงรีใช้พื้นที่พิกัดเดียวกับรูปสี่เหลี่ยม ดังนั้นคุณสามารถจัดตำแหน่งให้ตรงกันโดยปรับคุณสมบัติ `setLeft` และ `setTop` หากจำเป็น

### ขั้นตอนที่ 9: บันทึกเอกสาร

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `output.docx` เปิดไฟล์ใน Microsoft Word หรือ LibreOffice คุณจะเห็นรูปสี่เหลี่ยมและรูปวงรีที่จัดกลุ่มไว้ด้วยกัน การเลือกรูปร่างใดรูปร่างหนึ่งจะไฮไลท์ทั้งกลุ่ม ยืนยันว่า **append shape to group** สำเร็จ

![Add rectangle shape example in Java](image.png){alt="ตัวอย่างการเพิ่มรูปสี่เหลี่ยมใน Java"}

*ภาพหน้าจอแสดงรูปสี่เหลี่ยมและวงรีภายในกลุ่มเดียวพร้อมสำหรับการจัดการร่วมกัน*

## ทำไมวิธีนี้ถึงสำคัญ

* **Single source of truth** – ทุกคุณสมบัติของรูปร่างถูกตั้งค่าก่อนสร้างกลุ่ม เพื่อป้องกันข้อบกพร่องในการจัดวาง
* **Reusability** – เมธอด `setWidth`/`setHeight` ทำงานกับรูปร่างใดก็ได้ ดังนั้นคุณสามารถขยายตัวอย่างเป็นลูกศร, ดาว, หรือ SVG ที่กำหนดเอง
* **Performance** – การจัดกลุ่มลดจำนวนอ็อบเจกต์การวาดที่ตัวเรนเดอร์ของ Word ต้องจัดการ ซึ่งช่วยเพิ่มความเร็วในการเปิดเอกสารขนาดใหญ่
* **Maintainability** – การเก็บตรรกะการสร้างรูปร่างและการจัดกลุ่มไว้ด้วยกันทำให้ผู้พัฒนาต่อไปสามารถแก้ไขมิติหรือเพิ่มรูปร่างใหม่ได้โดยไม่ต้องค้นหาโค้ดที่ไม่เกี่ยวข้อง

## ความแปรผันทั่วไปและกรณีขอบ

| Scenario | Adjustment |
|----------|------------|
| **หน่วยต่างกัน** | ใช้การแปลง `PointsToPixels` หรือกำหนด `Shape.setWrapType(WrapType.INLINE)` สำหรับการวางแบบอินไลน์ |
| **การหมุนกลุ่ม** | เรียก `groupShape.setRotation(45);` เพื่อหมุนรูปร่างลูกทั้งหมด 45° |
| **การเพิ่มข้อความลงในรูปร่าง** | ใช้ `Shape.setText("Label");` หลังจากกำหนดขนาด |
| **การกำหนดขนาดแบบไดนามิก** | ดึงมิติของหน้าโดยใช้ `doc.getFirstSection().getPageSetup().getPageWidth()` และคำนวณขนาดรูปร่างตามสัดส่วน |

ความแปรผันเหล่านี้แสดงให้เห็นว่ารูปแบบหลัก—**add rectangle shape**, **set shape size**, **group multiple shapes**, **append shape to group**—สามารถปรับใช้กับความต้องการจริงหลายประเภท

## สรุป

ตอนนี้คุณรู้วิธี **add rectangle shape** ไปยังเอกสาร Word ด้วย Java, **set shape size**, **group multiple shapes**, และ **append shape to group** อย่างเป็นระเบียบและดูแลรักษาง่าย ตัวอย่างเต็มจะคอมไพล์เป็นคลาสเดียวที่สามารถรันได้ และไฟล์ DOCX ที่ได้จะแสดงผลลัพธ์ตามที่คาดหวัง

จากนี้คุณสามารถสำรวจต่อได้:

* เพิ่มป้ายข้อความหรือไฮเปอร์ลิงก์ให้กับแต่ละรูปร่าง
* ซ้อนกลุ่มเพื่อสร้างแผนภาพแบบลำดับชั้น
* ส่งออกเอกสารเป็น PDF พร้อมคงกลุ่มรูปร่าง

อย่าลังเลที่จะทดลองกับมิติ, สี, และประเภทรูปร่างเพิ่มเติม การเชี่ยวชาญการจัดการรูปร่างจะเปิดประตูสู่การสร้างรายงานอัตโนมัติ, แผนภาพแบบไดนามิก, และประสบการณ์เอกสารที่หลากหลาย—ทั้งหมดจากโค้ด Java โดยตรง

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบอื่นในโครงการของคุณ

- [แทรกรูปสี่เหลี่ยมใน Java – จัดกลุ่มและตำแหน่งรูปร่าง](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [วิธีสร้างและแทรกรูปวงรีและสี่เหลี่ยมภายในกลุ่มรูปร่างในเอกสาร Word ด้วย Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}