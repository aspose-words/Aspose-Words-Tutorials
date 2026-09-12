---
category: general
date: 2026-09-11
description: บันทึกเอกสาร Word หลังจากแก้ไขแผนภูมิโดนัทด้วย Aspose.Words for Java.
  เรียนรู้วิธีเปลี่ยนขนาดรูของโดนัท, หมุนแผนภูมิโดนัท, และแก้ไขคุณสมบัติของแผนภูมิโดนัท.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: th
lastmod: 2026-09-11
og_description: บันทึกเอกสาร Word หลังจากแก้ไขแผนภูมิโดนัทโดยใช้ Aspose.Words for
  Java บทเรียนนี้แสดงวิธีเปลี่ยนขนาดรูของโดนัท, หมุนแผนภูมิโดนัท, และปรับแต่งลักษณะของแผนภูมิ
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: บันทึกเอกสาร Word หลังจากแก้ไขแผนภูมิโดนัท – คู่มือ Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: บันทึกเอกสาร Word หลังจากแก้ไขแผนภูมิโดนัทใน Java
url: /th/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# บันทึกเอกสาร Word หลังจากแก้ไขแผนภูมิ doughnut ใน Java

หากคุณต้องการ **บันทึกเอกสาร Word** ที่มีแผนภูมิ doughnut ที่ปรับแต่งแล้ว คู่มือนี้จะแสดงวิธีทำอย่างละเอียด เพียงไม่กี่บรรทัดของ Java คุณสามารถเปลี่ยนขนาดรูของ doughnut, หมุนแผนภูมิ doughnut, และเขียนผลลัพธ์กลับไปยังดิสก์ได้

คุณจะได้เห็นตัวอย่างที่สมบูรณ์และสามารถรันได้ซึ่งใช้ Aspose.Words for Java พร้อมเคล็ดลับในการจัดการหลายแผนภูมิ, ตรวจสอบประเภทของโหนด, และหลีกเลี่ยงข้อผิดพลาดทั่วไป ไม่จำเป็นต้องอ้างอิงภายนอก—ทุกอย่างที่คุณต้องการรวมอยู่แล้ว

## ข้อกำหนดเบื้องต้น

- Java 17 หรือใหม่กว่า ที่ติดตั้งแล้ว
- Maven หรือ Gradle เพื่อจัดการ dependencies
- Aspose.Words for Java (เวอร์ชัน 23.9 หรือใหม่กว่า) ที่เพิ่มเข้าในโปรเจคของคุณ  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- ไฟล์ Word (`input.docx`) ที่มีแผนภูมิ doughnut เพียงหนึ่งรายการ

## ขั้นตอนที่ 1: โหลดเอกสาร Word

ขั้นตอนแรกคือการเปิดไฟล์ต้นฉบับ ขั้นตอนนี้สำคัญเนื่องจากการดำเนินการต่อ ๆ ไปทั้งหมดทำงานบนอ็อบเจ็กต์ `Document` ที่อยู่ในหน่วยความจำ

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **ทำไม?** การโหลดเอกสารสร้างการแสดงผลแบบ DOM ที่ทำให้คุณสามารถเดินทางผ่าน shapes, tables, และ charts ได้ หากไฟล์ไม่สามารถเปิดได้ Aspose.Words จะโยน exception ทำให้คุณทราบทันทีว่าพาธไม่ถูกต้อง

## ขั้นตอนที่ 2: ค้นหา shape ของแผนภูมิ doughnut

แผนภูมิจะถูกเก็บไว้ภายในโหนด `Shape` เราจะดึง shape ตัวแรกที่มีแผนภูมิและแคสต์ renderer ของมันเป็น `Chart`

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **ทำไม?** การตรวจสอบ `isChart()` ป้องกัน `ClassCastException` เมื่อเอกสารมีรูปภาพหรือ shape อื่น ๆ ก่อนแผนภูมิ ทำให้โค้ดมีความทนทานต่อเอกสารที่มีเนื้อหาผสมกัน

## ขั้นตอนที่ 3: เปลี่ยนขนาดรูของ doughnut  

ตอนนี้เราจะแก้ไขรูของ doughnut เมธอด `setHoleSize` ต้องการค่าร้อยละของรัศมีแผนภูมิ (10 – 90)

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **ทำไม?** การเปลี่ยนรูของ doughnut (`change doughnut hole` / `change chart hole size`) ช่วยให้คุณเน้นหรือไม่เน้นพื้นที่ศูนย์กลาง ค่าที่อยู่นอกช่วง 10‑90 % จะถูก API เพิกเฉย

## ขั้นตอนที่ 4: หมุนแผนภูมิ doughnut  

เพื่อควบคุมตำแหน่งเริ่มต้นของชิ้นส่วนแรก ให้ตั้งค่า first‑slice angle ซึ่งจะทำให้ **rotate doughnut chart** อย่างมีประสิทธิภาพ

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **ทำไม?** การหมุนแผนภูมิเป็นประโยชน์เมื่อคุณต้องการให้ชิ้นส่วนใดชิ้นหนึ่งปรากฏที่ด้านบนหรือให้ตรงกับข้อกำหนดการออกแบบ

## ขั้นตอนที่ 5: บันทึกเอกสารที่อัปเดต  

สุดท้ายให้เขียนการเปลี่ยนแปลงกลับไปยังไฟล์ใหม่ นี่คือช่วงที่คุณ **บันทึกเอกสาร Word** พร้อมแผนภูมิที่แก้ไขแล้ว

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **ผลลัพธ์ที่คาดหวัง:** `output.docx` มีเนื้อหาเดิมอยู่ แต่แผนภูมิ doughnut ตอนนี้มีรูขนาด 30 % และชิ้นส่วนแรกเริ่มที่ 45 ° การเปิดไฟล์ใน Microsoft Word จะเห็นแผนภูมิที่เปลี่ยนแปลงแล้ว

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงใน IDE ของคุณได้ รวมถึงการ import ทั้งหมดและการจัดการข้อผิดพลาดที่จำเป็นสำหรับการ **edit doughnut chart** และ **save Word document** อย่างปลอดภัย

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิด `output.docx`:

- รูศูนย์กลางของแผนภูมิ doughnut ครอบคลุมประมาณหนึ่งในสามของรัศมีแผนภูมิ
- ชิ้นส่วนแรกเริ่มที่ตำแหน่ง 45 องศา ทำให้แผนภูมิทั้งหมดเลื่อนตามเข็มนาฬิกา

การเปลี่ยนแปลงทั้งสองด้านจะปรากฏทันทีใน Word

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | วิธีจัดการ |
|-----------|------------|
| **หลายแผนภูมิ** | วนลูปผ่าน `doc.getChildNodes(NodeType.SHAPE, true)` และกรอง `shape.isChart()`; ใช้ `setHoleSize` / `setFirstSliceAngle` กับแต่ละ `Chart` |
| **แผนภูมิไม่ใช่ doughnut** | ตรวจสอบ `chart.getType()`; เรียก `setHoleSize` เฉพาะเมื่อ `chart.getType() == ChartType.DOUGHNUT` |
| **ต้องการเปลี่ยนขนาดรูแบบไดนามิก** | คำนวณเปอร์เซ็นต์ที่ต้องการจากค่าข้อมูล แล้วเรียก `setHoleSize(computedValue)` |
| **บันทึกเป็นสตรีม** | ใช้ |

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจคของคุณ

- [วิธีสร้างแผนภูมิคอลัมน์โดยใช้ Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [วิธีบันทึกเอกสารเป็น pdf ด้วย Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [บันทึก Word ด้วยรหัสผ่านโดยใช้ Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}