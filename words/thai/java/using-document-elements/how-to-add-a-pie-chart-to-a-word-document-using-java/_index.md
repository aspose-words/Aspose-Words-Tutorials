---
category: general
date: 2026-11-15
description: เรียนรู้วิธีเพิ่มแผนภูมิวงกลมลงในเอกสาร Word ด้วย Aspose.Words for Java
  รวมถึงการแปลงเป็นแผนภูมิโดนัท, การแยกชิ้นส่วน, และตัวอย่างโค้ดเต็ม
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: th
lastmod: 2026-11-15
og_description: เพิ่มแผนภูมิวงกลมลงในเอกสาร Word ด้วย Aspose.Words for Java. บทแนะนำนี้แสดงวิธีการแยกชิ้นส่วนและเปลี่ยนแผนภูมิให้เป็นรูปโดนัท.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: เพิ่มแผนภูมิวงกลมในเอกสาร Word ด้วย Java – คู่มือขั้นตอนโดยละเอียด
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: วิธีเพิ่มแผนภูมิวงกลมในเอกสาร Word ด้วย Java
url: /th/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มแผนภูมิวงกลมลงในเอกสาร Word – คู่มือ Java ฉบับเต็ม

หากคุณต้องการ **เพิ่มแผนภูมิวงกลมลงในเอกสาร Word** อย่างอัตโนมัติ คู่มือนี้จะแสดงให้คุณเห็นขั้นตอนทั้งหมดโดยใช้ Aspose.Words for Java คุณจะได้เห็นกระบวนการเต็มรูปแบบ: โหลดไฟล์ DOCX, สร้างแผนภูมิวงกลม, แยกชิ้นแรกออก, และแปลงแผนภูมิเป็นโดนัทโดยกำหนดขนาดรู

คู่มือนี้ยังครอบคลุมการปรับเปลี่ยนทั่วไป—เช่น การเพิ่มหลายชุดข้อมูล, การกำหนดสี, และการจัดการเอกสารที่มีแผนภูมิอยู่แล้ว—เพื่อให้คุณสามารถปรับโค้ดให้เข้ากับโครงการจริง เช่น การรายงานอัตโนมัติหรือการนำเสนอแบบไดนามิก

## ข้อกำหนดเบื้องต้น

* Java 17 หรือใหม่กว่า (โค้ดสามารถคอมไพล์กับ JDK 11+ ได้เช่นกัน)
* Maven 3.6+ หรือ Gradle สำหรับการจัดการ dependencies
* ใบอนุญาต Aspose.Words for Java (รุ่นทดลองฟรีใช้สำหรับการทดสอบ)
* ความเข้าใจพื้นฐานเกี่ยวกับไวยากรณ์ Java และโครงสร้างโครงการ Maven

## ขั้นตอนที่ 1: ตั้งค่าโครงการ Maven และนำเข้า Aspose.Words

สร้างโครงการ Maven ใหม่ (หรือเพิ่มในโครงการที่มีอยู่) และเพิ่ม dependency ของ Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **เคล็ดลับ:** หากคุณใช้ Gradle รายการที่เทียบเท่าคือ `implementation 'com.aspose:aspose-words:24.9'`.

Dependency นี้จะนำเข้าคลาส `Document`, `Chart`, และ `ChartType` ที่คุณต้องการใช้ในการจัดการแผนภูมิ

## ขั้นตอนที่ 2: โหลดเอกสารเป้าหมาย

คุณสามารถเริ่มจากไฟล์ `.docx` ที่มีอยู่หรือสร้างเอกสารเปล่าใหม่ ตัวอย่างด้านล่างโหลดเทมเพลตชื่อ `input.docx` ที่อยู่ในโฟลเดอร์ `src/main/resources`

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

หากไฟล์ไม่พบ Aspose.Words จะสร้างเอกสารเปล่าใหม่โดยอัตโนมัติเมื่อคุณเรียก `new Document()` โดยไม่ระบุชื่อไฟล์

## ขั้นตอนที่ 3: สร้างแผนภูมิวงกลมและแทรกลงในเอกสาร

Aspose.Words ถือว่าแผนภูมิเป็นรูปทรงที่สามารถวางได้ทุกตำแหน่งที่ย่อหน้าสามารถปรากฏได้ โค้ดต่อไปนี้สร้าง **แผนภูมิวงกลม**, เพิ่มชุดข้อมูลเดียว, และแทรกแผนภูมิหลังย่อหน้าที่แรก

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**ทำไมขั้นตอนนี้สำคัญ:**  
* `ChartType.PIE` บอก Aspose.Words ให้แสดงแผนภูมิวงกลมแบบดั้งเดิม  
* การเพิ่มชุดข้อมูลที่มีทั้งป้ายชื่อหมวดหมู่และค่าตัวเลขจะเติมชิ้นส่วนของแผนภูมิโดยอัตโนมัติ  
* การแทรกแผนภูมิเป็นลูกของ `Paragraph` จะทำให้การไหลของเอกสารคงที่

## ขั้นตอนที่ 4: แยกชิ้นแรกออกเพื่อเน้นให้เด่น

*ชิ้นที่แยกออก* จะดึงความสนใจไปยังจุดข้อมูลเฉพาะ API มีเมธอด `setExplode(boolean)` บนวัตถุ `ChartSeries` การตั้งค่านี้บนชุดแรก (ดัชนี 0) จะทำให้ชิ้นแรกโผล่ออกมา

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **คำถามทั่วไป:** *ถ้าฉันมีหลายชุดข้อมูลล่ะ?*  
> คุณสามารถระบุชุดข้อมูลที่ต้องการโดยใช้ดัชนีของมัน เช่น `pieChart.getSeries().get(1).setExplode(true)` สำหรับชุดที่สอง

## ขั้นตอนที่ 5: แปลงแผนภูมิวงกลมเป็นโดนัทโดยกำหนดขนาดรู

แผนภูมิโดนัทคือแผนภูมิวงกลมที่มีศูนย์กลางเป็นช่องว่าง Aspose.Words ให้คุณกำหนดขนาดรูเป็นเปอร์เซ็นต์ของรัศมีแผนภูมิ

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

เมธอด `setHoleSize` รับค่าตั้งแต่ **0** (วงกลมปกติ) ถึง **100** (ว่างเปล่าเต็ม) ค่าใกล้ **30‑40** จะให้โดนัทที่สมดุลในเชิงภาพ

## ขั้นตอนที่ 6: บันทึกและตรวจสอบผลลัพธ์

หลังจากทำการแก้ไขทั้งหมดแล้ว ให้บันทึกเอกสาร บรรทัดต่อไปนี้จะเขียนไฟล์ไปยังโฟลเดอร์ `output`

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### ผลลัพธ์ที่คาดหวัง

เปิดไฟล์ `final-pie-doughnut.docx` ใน Microsoft Word:

* แผนภูมิโดนัทปรากฏในตำแหน่งที่ย่อหน้าแรกอยู่  
* ชิ้น “Apples” ถูกแยกออก (แยกออกเล็กน้อยจากส่วนอื่น)  
* แผนภูมิแสดงสี่ชิ้นที่มีป้ายชื่อ *Apples*, *Bananas*, *Cherries*, *Dates* พร้อมเปอร์เซ็นต์ที่คุณระบุ  

หากคุณต้องการผลลัพธ์เป็น PDF ให้เปลี่ยน `SaveFormat` เป็น `SaveFormat.PDF`

## การจัดการกรณีขอบและการปรับเปลี่ยน

### การเพิ่มหลายชุดข้อมูล

หากคุณต้องการหลายชุดข้อมูล (เช่น โดนัทซ้อนกัน) ให้เพิ่มตามลำดับ:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### สีที่กำหนดเอง

คุณสามารถกำหนดสีให้แต่ละชิ้นได้ผ่าน `ChartDataPoint.setFillFormat().setSolidFillColor()` :

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### การทำงานกับแผนภูมิที่มีอยู่แล้ว

หากเอกสารมีแผนภูมิอยู่แล้วและคุณต้องการแก้ไขเท่านั้น ให้ค้นหา shape ของแผนภูมิ:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### การจัดการใบอนุญาต

Aspose.Words ต้องการใบอนุญาตสำหรับการใช้งานในสภาพแวดล้อมการผลิต ให้วางไฟล์ `Aspose.Words.lic` ของคุณใน classpath และโหลดเมื่อแอปพลิเคชันเริ่มทำงาน:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

หากไม่ได้ตั้งค่าใบอนุญาต จะมีลายน้ำปรากฏบนเอกสารที่สร้างขึ้น

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นคลาส Java ฉบับเต็มที่รวมทุกขั้นตอนที่อธิบายไว้ คัดลอกไปยัง `src/main/java/com/example/AddPieChart.java` แล้วรัน `mvn compile exec:java`

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

การรันโปรแกรมจะสร้างแผนภูมิโดนัทตามที่อธิบายไว้ก่อนหน้า ปรับค่า `categories`, `values` หรือ `holeSize` ให้เหมาะกับข้อมูลของคุณ

## สรุป

ตอนนี้คุณรู้วิธี **เพิ่มแผนภูมิวงกลมลงในเอกสาร Word** ด้วย Java และ Aspose.Words แล้ว คู่มือได้ครอบคลุมการโหลดเอกสาร, การสร้างแผนภูมิวงกลม, การแยกชิ้น, การแปลงแผนภูมิเป็นโดนัท, และการจัดการการปรับเปลี่ยนทั่วไป เช่น หลายชุดข้อมูล, สีที่กำหนดเอง, และแผนภูมิที่มีอยู่แล้ว ด้วยพื้นฐานนี้คุณสามารถสร้างเครื่องมือรายงานอัตโนมัติ, สร้างการนำเสนอแบบไดนามิก, หรือฝังการแสดงผลภาพที่หลากหลายโดยตรงในไฟล์ Word

### สิ่งที่ควรสำรวจต่อไป

* **add bar chart to Word document** – ขั้นตอนคล้ายกันแต่ใช้ `ChartType.BAR`  
* **customize chart legends and titles** – ใช้ `pieChart.getTitle().setText("...")` และ `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`  
* **export the Word document as PDF** – เปลี่ยน `SaveFormat` เป็น `PDF` สำหรับไฟล์ที่พร้อมแจกจ่าย  
* **populate chart data from a database** – แทนที่อาร์เรย์คงที่ด้วยผลลัพธ์การ query ของ JDBC  

ลองทดลองกับประเภทแผนภูมิ, แหล่งข้อมูล, และตัวเลือกการจัดรูปแบบต่าง ๆ ได้ตามต้องการ ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดที่ทำงานได้เต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการนำไปใช้ทางเลือกในโครงการของคุณ

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}