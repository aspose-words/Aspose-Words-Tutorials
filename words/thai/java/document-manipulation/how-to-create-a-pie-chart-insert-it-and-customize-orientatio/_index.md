---
category: general
date: 2026-11-25
description: เรียนรู้วิธีสร้างแผนภูมิวงกลมใน Java, แทรกแผนภูมิวงกลมลงในเอกสาร Word,
  แยกชิ้นส่วนของแผนภูมิและเปลี่ยนทิศทางของแผนภูมิด้วยตัวอย่างโค้ดที่ชัดเจน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: th
lastmod: 2026-11-25
og_description: สร้างแผนภูมิวงกลมใน Java, แทรกแผนภูมิวงกลมลงในเอกสาร, แยกชิ้นส่วนของแผนภูมิและเปลี่ยนทิศทางของแผนภูมิด้วยโค้ดทีละขั้นตอน.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: สร้างแผนภูมิวงกลมใน Java – แทรก, แยกชิ้น, และหมุน
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: วิธีสร้างแผนภูมิวงกลม แทรกลงในโปรแกรม และปรับทิศทางใน Java
url: /th/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างแผนภูมิวงกลม แทรกลงในเอกสาร และปรับทิศทางใน Java

หากคุณต้องการ **สร้างแผนภูมิวงกลม** ภายในไฟล์ Word คำแนะนำนี้จะแสดงขั้นตอนทั้งหมดให้คุณทำได้ คุณจะได้เรียนรู้วิธี **แทรกแผนภูมิวงกลม** การทำให้ส่วนหนึ่งของแผนภูมิระเบิดเพื่อเน้นจุดสำคัญ และ **เปลี่ยนทิศทางของแผนภูมิ** ด้วยการหมุนอย่างง่าย

บทเรียนนี้ครอบคลุมทุกอย่างที่คุณต้องการ ตั้งแต่การตั้งค่าไลบรารี Aspose.Words for Java จนถึงการสร้างไฟล์ `.docx` สุดท้ายที่แสดงแผนภูมิวงกลมที่ถูกหมุนและระเบิด ไม่ต้องอ้างอิงเอกสารภายนอก เพียงทำตามขั้นตอนและรันโค้ด

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* Java 17 หรือใหม่กว่า
* Maven หรือ Gradle สำหรับจัดการ dependencies
* ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (หรือใช้โหมดทดลองฟรี)

เพิ่ม dependency ของ Aspose.Words ลงใน `pom.xml` (Maven) หรือ `build.gradle` (Gradle) ตัวอย่างสำหรับ Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **เคล็ดลับ:** ควรอัปเดตเวอร์ชันของไลบรารีให้เป็นล่าสุด; เวอร์ชันล่าสุด (24.10 ณ เวลาที่เขียน) มีการแก้ไขบั๊กสำหรับการแสดงผลแผนภูมิ

## ขั้นตอนที่ 1: สร้างแผนภูมิวงกลมและแทรกลงในเอกสาร

ขั้นตอนแรกคือ **สร้างแผนภูมิวงกลม** แล้วฝังลงในไฟล์ Word โค้ดด้านล่างจะสร้างเอกสารง่าย ๆ เพิ่มตัวแทนแผนภูมิ และแทรกแผนภูมิวงกลมขนาด 400 × 300 พิกเซล

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**เหตุผลที่สำคัญ:** `builder.insertChart` สร้างตัวแทนแผนภูมิที่ Aspose.Words จะเปลี่ยนเป็นแผนภูมิ OOXML โดยอัตโนมัติเมื่อบันทึกเอกสาร พารามิเตอร์ `ChartType.PIE` บอกไลบรารีให้เรนเดอร์เป็นแผนภูมิวงกลม ซึ่งสอดคล้องกับความต้องการ **แทรกแผนภูมิวงกลม**

## ขั้นตอนที่ 2: ระเบิดส่วนของแผนภูมิเพื่อเน้นข้อมูล

การระเบิดส่วนของแผนภูมิช่วยดึงความสนใจไปยังจุดข้อมูลที่ต้องการ บรรทัดต่อไปนี้จะระเบิดส่วนแรก (index 0) ด้วยระยะ 10 จุด

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

คุณสามารถเปลี่ยนค่า index เพื่อระเบิดส่วนอื่นได้ หรือปรับระยะระเบิดเพื่อให้เอฟเฟกต์ดูอ่อนลง การระเบิดส่วนเป็นวิธีมาตรฐานในการ **ระเบิดส่วนของแผนภูมิวงกลม** ใน Aspose.Words

## ขั้นตอนที่ 3: เปลี่ยนทิศทางของแผนภูมิโดยการหมุน

การหมุนแผนภูมิจะให้มุมมองใหม่ ใช้ `setRotationAngle` เพื่อหมุนแผนภูมิทั้งหมดตามเข็มนาฬิกา (มุมวัดเป็นองศา)

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

การเรียกใช้ข้างต้นตอบสนองความต้องการ **หมุนแผนภูมิวงกลม** และ **เปลี่ยนทิศทางของแผนภูมิ** ใด ๆ ระหว่าง 0 ถึง 360 องศาจะรับได้

## ตัวอย่างที่สามารถรันได้ทั้งหมด

รวมทุกขั้นตอนเข้าด้วยกัน นี่คือโปรแกรมสมบูรณ์ที่สร้างแผนภูมิวงกลม ระเบิดส่วนหนึ่ง และหมุนแผนภูมิ รันจาก IDE หรือจากคอมมานด์ไลน์ด้วย `java -cp <classpath> PieChartDemo`

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

* จะมีไฟล์ชื่อ **CreatePieChartDemo.docx** ปรากฏในไดเรกทอรีทำงาน
* เปิดไฟล์ด้วย Microsoft Word จะเห็นแผนภูมิวงกลมขนาด 400 × 300 พิกเซล
* ส่วนแรก (Q1) จะถูกย้ายออกด้านนอก 10 จุด สร้างเอฟเฟกต์ **ระเบิดส่วนของแผนภูมิวงกลม**
* แผนภูมิทั้งหมดจะถูกเอียง 45 องศา แสดง **การเปลี่ยนทิศทางของแผนภูมิ** และ **การหมุนแผนภูมิวงกลม**

## ความแตกต่างทั่วไปและกรณีขอบ

| สถานการณ์ | วิธีปรับโค้ด |
|-----------|--------------|
| **ขนาดแผนภูมิต่างกัน** | เปลี่ยนค่า `400, 300` ใน `insertChart` |
| **หลายชุดข้อมูล** | เพิ่มอ็อบเจ็กต์ `ChartSeries` ลงใน `chart.getSeries()` |
| **ระเบิดส่วนอื่น** | ใช้ `setExplode(sliceIndex, distance)` พร้อม `sliceIndex` ที่ต้องการ |
| **ไม่ต้องการหมุน** | ลบการเรียก `setRotationAngle` หรือกำหนดมุมเป็น `0` |
| **ส่งออกเป็น PDF แทน DOCX** | หลังจากสร้างเอกสารแล้วเรียก `doc.save("output.pdf")` พร้อมระบุฟอร์แมต PDF |

> **ระวัง:** การใช้ระยะระเบิดเป็นค่าลบจะทำให้เกิด `IllegalArgumentException` ควรให้ค่าที่ไม่เป็นลบเสมอ

## เคล็ดลับด้านประสิทธิภาพ

หากคุณสร้างแผนภูมิหลาย ๆ แผนภูมิในลูป ให้ใช้ `DocumentBuilder` ตัวเดียวและเรียก `insertChart` เฉพาะในแต่ละรอบ การทำเช่นนี้จะลดการใช้หน่วยความจำและเร่งการประมวลผล

## สรุป

ตอนนี้คุณรู้วิธี **สร้างแผนภูมิวงกลม**, **แทรกแผนภูมิวงกลม**, **ระเบิดส่วนของแผนภูมิวงกลม**, และ **หมุนแผนภูมิวงกลม** ด้วย Aspose.Words for Java ตัวอย่างเต็มแสดงขั้นตอนการทำงานทั้งหมด ตั้งแต่การเริ่มต้นเอกสารจนถึงการบันทึกไฟล์ที่แสดงแผนภูมิวงกลมที่ถูกหมุนและระเบิด

ต่อไปคุณอาจลอง **เปลี่ยนทิศทางของแผนภูมิ** เพิ่มเติมโดยใช้เอฟเฟกต์ 3‑D หรือทดลองกับประเภทแผนภูมิอื่น ๆ เช่น **Bar** หรือ **Line** รูปแบบ API เดียวกันทำให้การขยายบทเรียนนี้เป็นเรื่องง่าย

ปรับเปลี่ยนข้อมูล, ดัชนีส่วน, หรือมุมการหมุนให้ตรงกับความต้องการของคุณ แล้วแชร์ผลลัพธ์กับชุมชน!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้เกี่ยวกับหัวข้อที่ใกล้เคียงและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [วิธีแทรกแผนภูมิวงกลมลงในเอกสาร Word ด้วย Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [วิธีระเบิดส่วนของแผนภูมิวงกลมใน Java – บทเรียนแผนภูมิ Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}