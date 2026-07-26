---
category: general
date: 2026-07-26
description: แทรกรูปสี่เหลี่ยมผืนผ้าใน Java ด้วย Aspose.Words. เรียนรู้วิธีตั้งขนาดรูป,
  กำหนดตำแหน่งรูป, และวิธีจัดกลุ่มรูปในไฟล์ DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: th
lastmod: 2026-07-26
og_description: แทรกรูปสี่เหลี่ยมใน Java เพื่อสร้างกราฟิก DOCX ที่หลากหลาย ทำตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อกำหนดขนาดรูป,
  ตั้งตำแหน่งรูป, และจัดกลุ่มรูปได้อย่างง่ายดาย.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: แทรกรูปสี่เหลี่ยมผืนผ้าใน Java – เชี่ยวชาญการจัดกลุ่มและการวางตำแหน่ง
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: แทรกรูปสี่เหลี่ยมใน Java – จัดกลุ่มและกำหนดตำแหน่งรูป
url: /th/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกรูปสี่เหลี่ยมใน Java – การจัดกลุ่มและกำหนดตำแหน่งรูป

เคยต้อง **แทรกรูปสี่เหลี่ยม** ลงในเอกสาร Word ขณะเขียนโค้ด Java หรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนาที่สร้างรายงาน, ใบแจ้งหนี้ หรือเทมเพลตแบบกำหนดเองมักเจอปัญหานี้บ่อยครั้ง ข่าวดีคือด้วยเพียงไม่กี่บรรทัดของ Aspose.Words for Java คุณก็สามารถ **แทรกรูปสี่เหลี่ยม**, **กำหนดขนาดรูป**, **กำหนดตำแหน่งรูป**, และแม้แต่ **วิธีการจัดกลุ่มรูป** เพื่อให้เคลื่อนที่เป็นหน่วยเดียวได้

ในคู่มือนี้เราจะพาคุณผ่านกระบวนการทั้งหมดตั้งแต่การสร้างเอกสารเปล่าไปจนถึงการบันทึกไฟล์ `.docx` ที่มีสี่เหลี่ยมสองรูปจัดกลุ่มอย่างเรียบร้อย เมื่ออ่านจบคุณจะรู้ **วิธีการเพิ่มสี่เหลี่ยม** เข้าไป, ควบคุมมิติของมัน, วางตำแหน่งได้ตามต้องการ, และรวมไว้ในกลุ่มที่นำกลับมาใช้ใหม่ได้ ไม่ต้องใช้ไลบรารีภายนอกใด ๆ นอกเหนือจาก Aspose.Words และโค้ดทำงานได้กับ Java 8‑plus

## ข้อกำหนดเบื้องต้น

- Java 8 หรือใหม่กว่า (ฉันใช้ JDK 17, แต่ใด ๆ ที่รองรับ Maven ก็ใช้ได้)
- Aspose.Words for Java 23.9 หรือใหม่กว่า – เพิ่ม dependency ไปที่ `pom.xml` ของคุณหรือดาวน์โหลด JAR
- ความเข้าใจพื้นฐานเกี่ยวกับไวยากรณ์ Java (ถ้าคุณเขียนเมธอด `main` ได้ก็พอ)
- IDE หรือโปรแกรมแก้ไขข้อความที่คุณชอบ (IntelliJ IDEA, Eclipse, VS Code…)

> **เคล็ดลับ:** หากคุณใช้ Maven, การอ้างอิง dependency จะเป็นแบบนี้:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

เมื่อเราตั้งค่าพื้นฐานเรียบร้อยแล้ว, มาเริ่มเขียนโค้ดกันเลย

## แทรกรูปสี่เหลี่ยมและกำหนดขนาดของมัน

สิ่งแรกที่คุณทำคือสร้าง `Document` ใหม่และ `DocumentBuilder` ตัวสร้างนี้คือ “ปากกา” ของคุณที่วาดรูปลงบนหน้า ด้านล่างเราจะ **แทรกรูปสี่เหลี่ยม** และทันที **กำหนดขนาดรูป** เป็น 100 × 80 จุด

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

สังเกตว่าเมธอด `setWidth`/`setHeight` **กำหนดขนาดรูป** เป็นหน่วยจุด (1 pt ≈ 1/72 inch) คุณก็สามารถใช้ `setSize` หากต้องการเมธอดเดียว, แต่การเรียกอย่างชัดเจนทำให้เจตนาชัดเจนยิ่งขึ้น

## กำหนดตำแหน่งรูปบนหน้า

หลังจากที่เรามีสี่เหลี่ยมแรกแล้ว เราต้อง **กำหนดตำแหน่งรูป** ของสี่เหลี่ยมที่สองเพื่อไม่ให้ทับกัน การกำหนดตำแหน่งทำงานแบบเดียวกัน: คุณตั้งค่า `Left` และ `Top` ตามจุดอ้างอิงของกลุ่ม

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

หากคุณสงสัยว่าทำไมเราใช้ `setLeft` แทน `setX` นั่นเป็นเพราะ Aspose.Words ใช้ระบบพิกัดคลาสสิกของ Windows GDI—`Left` คือการเลื่อนแนวนอน, `Top` คือการเลื่อนแนวตั้ง การเปลี่ยนค่าเหล่านี้ทำให้คุณปรับแต่งเลย์เอาต์ได้โดยไม่ต้องยุ่งกับตารางหรือย่อหน้า

## วิธีการจัดกลุ่มรูป

คุณอาจถามว่า “ทำไมต้องจัดกลุ่มเลย?” การจัดกลุ่มมีประโยชน์เมื่อคุณต้องการให้รูปเคลื่อนที่พร้อมกัน, หมุนเป็นหน่วยเดียว, หรือใช้สไตล์ร่วมกัน ในตัวอย่างข้างบนเราได้สร้าง `GroupShape` ผ่าน `builder.insertGroupShape` แล้ว วัตถุนี้ทำหน้าที่เป็นคอนเทนเนอร์—คิดว่าเป็นโฟลเดอร์ที่เก็บไฟล์รูปอื่น ๆ

> **ทำไมเรื่องนี้สำคัญ:** หากคุณต่อมาต้องการเพิ่มคำอธิบายหรือหมุนแผนภาพทั้งหมด, คุณเพียงแก้ไขกลุ่มเดียว ไม่ต้องแก้ไขสี่เหลี่ยมแต่ละอันแยกกัน

## วิธีการเพิ่มสี่เหลี่ยมเข้าไปในกลุ่ม

การ **วิธีการเพิ่มสี่เหลี่ยม** เข้าไปในกลุ่มทำได้โดยเรียก `group.appendChild(rectangle)` เท่านั้น ภายใต้พื้นฐาน Aspose.Words จะอัปเดตคอลเลกชันภายในของกลุ่มและคำนวณกล่องขอบอัตโนมัติ เพื่อให้กลุ่มยังคงพอดีกับความกว้างและความสูงที่กำหนด

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

คุณสามารถทดลองใช้ `ShapeType` อื่น ๆ — `ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` เป็นต้น — และรูปแบบ `appendChild` เดียวกันก็ทำงานได้

## บันทึกเอกสาร

สุดท้ายเราจะบันทึกเอกสารลงดิสก์ พาธสามารถเป็นแบบสัมบูรณ์หรือสัมพัทธ์; เพียงตรวจสอบให้โฟลเดอร์มีอยู่แล้ว

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

เมื่อคุณเปิด `GroupShape.docx` ใน Microsoft Word, คุณจะเห็นสี่เหลี่ยมสองรูปเรียงข้างกัน, ทั้งสองถูกล็อกไว้ภายในกล่องสีเทาอ่อน การเลือกกล่องสีเทาจะทำให้สี่เหลี่ยมทั้งสองไฮไลท์พร้อมกัน — พิสูจน์ว่า **วิธีการจัดกลุ่มรูป** ทำงานจริง

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="ตัวอย่างการแทรกรูปสี่เหลี่ยมแสดงสองสี่เหลี่ยมที่จัดกลุ่มในไฟล์ DOCX ที่สร้างด้วย Java"}

*ข้อความแทนภาพ (SEO):* **ตัวอย่างการแทรกรูปสี่เหลี่ยมแสดงสองสี่เหลี่ยมที่จัดกลุ่มในไฟล์ DOCX ที่สร้างด้วย Java**.

## ผลลัพธ์ที่คาดหวัง

- ไฟล์ `GroupShape.docx` อยู่ในโฟลเดอร์ `output`
- ภายในเอกสาร: กลุ่มขนาด 400 × 200 pt ที่บรรจุสี่เหลี่ยมสองรูป (100 × 80 pt และ 120 × 60 pt) ตั้งตำแหน่งที่ (20, 30) และ (150, 50) ตามลำดับ
- กลุ่มมีเส้นขอบสีดำบางและพื้นสีเทาอ่อน ทำให้การจัดกลุ่มเห็นได้ชัดเจน

เปิดไฟล์และลองลากกล่องสีเทา — สี่เหลี่ยมทั้งสองควรเคลื่อนที่พร้อมกัน หากไม่เป็นเช่นนั้น, ตรวจสอบให้แน่ใจว่าคุณได้เรียก `group.appendChild` สำหรับแต่ละรูปแล้ว

## ข้อผิดพลาดทั่วไปและกรณีขอบ

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|--------|
| **สี่เหลี่ยมปรากฏอยู่นอกหน้า** | ค่า `Left`/`Top` เกินขนาดของกลุ่ม | เพิ่มขนาดกลุ่ม (`insertGroupShape(width, height)`) หรือ ลดค่าออฟเซ็ต |
| **กลุ่มหายไปหลังบันทึก** | `Width`/`Height` ของกลุ่มถูกตั้งเป็น 0 | ระบุขนาดที่ไม่เป็นศูนย์เมื่อเรียก `insertGroupShape` |
| **สีของรูปแสดงผลไม่ถูกต้อง** | การเติมสีเริ่มต้นเป็นโปร่งแสง; Word อาจแสดงเป็นสีขาว | ตั้งค่า `setFillColor` อย่างชัดเจนหรือใช้ `ShapeStyle` |
| **Exception `ArgumentOutOfRangeException`** | ใช้ค่าพิกัดเป็นลบ | ให้ค่า `Left` และ `Top` เป็นค่าที่ไม่เป็นลบ |

การจัดการกับปัญหาเหล่านี้ตั้งแต่แรกจะช่วยคุณหลีกเลี่ยงอาการ “ทำไมรูปของฉันหายไป?” ที่หลายคนใหม่มักเจอ

## สรุปและขั้นตอนต่อไป

เราได้ครอบคลุมวงจรชีวิตเต็มรูปแบบของ **แทรกรูปสี่เหลี่ยม** ใน Java: การสร้างเอกสาร, **กำหนดขนาดรูป**, **กำหนดตำแหน่งรูป**, **วิธีการจัดกลุ่มรูป**, และ **วิธีการเพิ่มสี่เหลี่ยม** เข้าไปในกลุ่ม ตัวอย่างที่ทำงานได้เต็มรูปแบบอยู่ในโค้ดบล็อกข้างบน, คุณสามารถคัดลอกไปวางในโปรเจกต์ Maven เพื่อดูผลลัพธ์ได้ทันที

ต่อไปคุณอาจลองทำสิ่งต่อไปนี้:

- เพิ่มข้อความภายในแต่ละสี่เหลี่ยมโดย

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่อธิบายในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจกต์ของคุณ

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}