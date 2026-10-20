---
category: general
date: 2026-10-20
description: วิธีจัดกลุ่มรูปร่างใน Aspose.Words for Java – เรียนรู้วิธีแทรกรูปสี่เหลี่ยม,
  จัดกลุ่ม, และบันทึกเอกสารในคู่มือเดียว
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: th
lastmod: 2026-10-20
og_description: วิธีจัดกลุ่มรูปร่างใน Aspose.Words สำหรับ Java. บทแนะนำนี้แสดงวิธีแทรกรูปสี่เหลี่ยม
  จัดกลุ่มพวกมัน และส่งออกผลลัพธ์.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: วิธีจัดกลุ่มรูปร่างใน Aspose.Words for Java – คู่มือแบบทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: วิธีจัดกลุ่มรูปร่างใน Aspose.Words สำหรับ Java
url: /th/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการจัดกลุ่มรูปร่างใน Aspose.Words for Java

หากคุณต้องการ **how to group shapes** ในเอกสาร Word โดยใช้ Aspose.Words for Java คำแนะนำนี้จะแสดงขั้นตอนการทำงานทั้งหมด คุณจะได้เรียนรู้วิธี **insert rectangle shape**, เพิ่มสี่เหลี่ยมอีกอันหนึ่ง, จัดกลุ่มสองรูปร่าง, และสุดท้ายบันทึกไฟล์—ทั้งหมดด้วยโค้ดที่ชัดเจนและสามารถรันได้.

การจัดกลุ่มรูปร่างมีประโยชน์เมื่อคุณต้องการย้าย, หมุน, หรือจัดสไตล์หลายภาพวาดเป็นหน่วยเดียว ไม่ว่าคุณจะสร้างเทมเพลตรายงาน, แผนภาพ, หรือโบรชัวร์แบบกำหนดเอง การเชี่ยวชาญการจัดกลุ่มรูปร่างจะช่วยประหยัดเวลาและทำให้การจัดวางของคุณสอดคล้องกัน

ในบทแนะนำนี้คุณจะ:

* สร้าง `Document` ใหม่และ `DocumentBuilder`
* **How to insert rectangle** รูปร่างด้วยขนาดที่แม่นยำ
* จัดกลุ่มสี่เหลี่ยมเป็น `GroupShape`
* บันทึกเอกสารและตรวจสอบผลลัพธ์

> **Prerequisite** – คุณต้องมี Aspose.Words for Java (v23.12 หรือใหม่กว่า) เพิ่มในโปรเจกต์ของคุณ ผู้ใช้ Maven สามารถรวม dependency ที่แสดงด้านล่าง

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## สิ่งที่คุณต้องการ

| รายการ | เหตุผล |
|------|--------|
| Java 17+ | ฟีเจอร์ภาษาใหม่และประสิทธิภาพที่ดีกว่า |
| Aspose.Words for Java | ให้ `DocumentBuilder`, `Shape`, และ `GroupShape` API |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | เพื่อคอมไพล์และรันตัวอย่าง |
| Write permission to a folder | เอกสารจะถูกบันทึกลงดิสก์ |

## วิธีการแทรกสี่เหลี่ยม

ขั้นตอนแรกคือการสร้าง `Document` และ `DocumentBuilder` Builder จะให้เมธอดเช่น `insertShape` เพื่อวางวัตถุวาด

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Why this matters** – การใช้ `insertShape` เป็นวิธีมาตรฐาน **how to insert rectangle** วัตถุใน Aspose.Words มันจะเพิ่มรูปร่างลงในพารากราฟปัจจุบันของเอกสารโดยอัตโนมัติ ดังนั้นคุณไม่ต้องจัดการกับ OpenXML ระดับต่ำ

## การปรับตำแหน่งสี่เหลี่ยม (ไม่บังคับ)

หากสี่เหลี่ยมที่สองต้องการตำแหน่งที่กำหนดเองสัมพันธ์กับสี่เหลี่ยมแรก คุณสามารถแก้ไขคุณสมบัติ `left` และ `top` ของมันได้ ขั้นตอนนี้ไม่บังคับแต่มักจำเป็นสำหรับการจัดวางแผนภาพที่แม่นยำ

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tip:** การวัดทั้งหมดเป็นหน่วย points (1 pt ≈ 1/72 in). ใช้ `convertPointsToPixels` หากคุณต้องการค่าพิกเซลสำหรับการคำนวณบน UI

## วิธีการจัดกลุ่มรูปร่าง

เมื่อสี่เหลี่ยมมีอยู่แล้ว คุณสามารถใส่พวกมันเข้าไปใน `GroupShape` การจัดกลุ่มทำให้สี่เหลี่ยมสองอันทำงานเหมือนอ็อบเจกต์เดียว—การย้าย, หมุน, หรือจัดรูปแบบกลุ่มจะส่งผลต่อทั้งสองรูปร่าง

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Why grouping works** – `GroupShape` สืบทอดจาก `Shape` ดังนั้นคุณสามารถปฏิบัติกับกลุ่มได้เช่นเดียวกับวัตถุวาดอื่น ๆ เมื่อคุณเรียก `appendChild` รูปร่างจะถูกลบจากตำแหน่งเดิมและกลายเป็นลูกของกลุ่ม

## การบันทึกเอกสารที่มีรูปร่างที่จัดกลุ่ม

สุดท้าย ให้เขียนเอกสารลงดิสก์ ไฟล์จะมี `GroupShape` เดียวที่มีสี่เหลี่ยมสองอันอยู่ภายใน

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เปิด `GroupShape.docx` ใน Microsoft Word:

* คุณจะเห็นสี่เหลี่ยมสองอัน (สีน้ำเงินและสีเขียว) วางเคียงกัน
* การเลือกสี่เหลี่ยมใดอันหนึ่งจะเลือกทั้งกลุ่ม—การลากจะย้ายทั้งสองพร้อมกัน
* กลุ่มมีเส้นขอบสีแดงบาง ๆ ยืนยันว่าคุณสมบัติ `GroupShape` ถูกนำไปใช้

หากคุณคลิกขวาที่กลุ่มและเลือก **Group → Ungroup** สี่เหลี่ยมจะกลับเป็นรูปร่างอิสระ แสดงว่าการจัดกลุ่มสามารถย้อนกลับได้

## ความหลากหลายทั่วไปและกรณีขอบ

| สถานการณ์ | วิธีจัดการ |
|-----------|------------|
| **More than two shapes** | แทรกแต่ละรูปร่าง แล้วเพิ่มทั้งหมดเข้าไปใน `GroupShape` เดียวกัน |
| **Different shape types** (e.g., ellipse, picture) | ใช้ `builder.insertShape(ShapeType.ELLIPSE, …)` หรือ `builder.insertImage(...)` ก่อนทำการเพิ่ม |
| **Scaling the group** | เรียก `group.setWidth(newWidth)` หรือ `group.setHeight(newHeight)`; ลูกจะปรับขนาดตามสัดส่วน |
| **Rotating the group** | `group.setRotationAngle(45);` หมุนคอลเลกชันทั้งหมดรอบศูนย์กลาง |
| **Preserving original positions** | บันทึกค่า `left`/`top` ของแต่ละรูปร่างก่อนจัดกลุ่มและคืนค่าใหม่หลังจากยกเลิกการจัดกลุ่มหากจำเป็น |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นคลาส Java เต็มรูปแบบที่คุณสามารถคัดลอกและวางลงใน IDE ของคุณ มันรวมการ import ทั้งหมด, การจัดการข้อผิดพลาด, และคอมเมนต์เพื่อความชัดเจน

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

รันโปรแกรม, เปิดไฟล์ `GroupShape.docx` ที่ได้, และคุณจะเห็นสี่เหลี่ยมที่จัดกลุ่มตามที่อธิบายไว้

## สรุป

ตอนนี้คุณรู้วิธี **how to group shapes** ใน Aspose.Words for Java แล้ว ตั้งแต่การสร้างเอกสาร, การแทรกสี่เหลี่ยม, การปรับตำแหน่ง, และสุดท้ายการจัดกลุ่มด้วย `GroupShape` เทคนิคนี้ทำให้คุณสามารถจัดการหลายภาพวาดเป็นเอกเทศเดียว, ทำให้การปรับแต่งเลย์เอาต์และความสอดคล้องของภาพง่ายขึ้น

**ขั้นตอนต่อไป**

- สำรวจ **how to insert rectangle** รูปร่างด้วยรูปแบบการเติมหรือเส้นขอบที่แตกต่าง
- ผสาน **insert rectangle shape** กับกล่องข้อความเพื่อสร้างแผนภาพที่มีป้ายกำกับ
- ทดลองหมุนหรือปรับขนาดกลุ่มเพื่อสร้างกราฟิกที่ซับซ้อนมากขึ้น

คุณสามารถปรับโค้ดให้เข้ากับประเภทรูปร่างอื่น, กลุ่มที่ใหญ่ขึ้น, หรือสถานการณ์การสร้างเอกสารแบบไดนามิกได้ตามต้องการ ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโครงการของคุณ

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [how to insert group shape in Java – Complete Guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [How to Set Shadow on a Shape in Aspose.Words – Complete Guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}