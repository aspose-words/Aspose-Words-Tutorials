---
category: general
date: 2026-08-07
description: วิธีทำให้ชิ้นพายแยกออกใน Java ด้วย Aspose.Words. เรียนรู้การเพิ่มเส้นนำไปยังพาย,
  สร้างแผนภูมิ Word, และปรับแต่งชิ้นพายของแผนภูมิพาย.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: th
lastmod: 2026-08-07
og_description: วิธีแยกชิ้นพายใน Java ด้วย Aspose.Words คู่มือนี้จะแสดงวิธีเพิ่มเส้นเชื่อมไปยังพาย
  สร้างแผนภูมิ Word และปรับแต่งชิ้นพายของแผนภูมิเพื่อให้ได้ผลกระทบภาพที่ชัดเจน
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: วิธีแยกชิ้นพายใน Java – คู่มือ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: วิธีทำให้ชิ้นพายแยกออกใน Java – บทแนะนำแผนภูมิ Aspose.Words
url: /th/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีทำให้ชิ้นพายระเบิดใน Java – บทแนะนำการใช้แผนภูมิ Aspose.Words

หากคุณต้องการทราบ **วิธีทำให้ชิ้นพายระเบิด** ในเอกสาร Word ด้วย Java, บทแนะนำนี้ครอบคลุมทั้งหมด เราจะสาธิต **วิธีเพิ่มเส้นเชื่อมต่อ (leader lines) ให้กับแผนภูมิพาย**, **java create word chart** objects, และ **การปรับแต่งชิ้นพาย** เพื่อให้ได้ผลลัพธ์ที่ดูเป็นมืออาชีพ เมื่ออ่านจบคุณจะมีตัวอย่างที่ทำงานได้เต็มรูปแบบและสามารถนำไปใช้ในโปรเจกต์ Java ใดก็ได้

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน, โปรดตรวจสอบว่าคุณมี:

* Java Development Kit (JDK) 8 หรือสูงกว่า
* Maven หรือ Gradle สำหรับจัดการ dependencies
* ใบอนุญาต Aspose.Words for Java (รุ่นทดลองฟรีใช้เพื่อการเรียนรู้ได้)
* ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java และแนวคิดเชิงวัตถุ

> **เคล็ดลับ:** แม้ว่า Aspose.Words จะมีรุ่นทดลองฟรี, การซื้อใบอนุญาตจะทำให้ลบลายน้ำการประเมินผลออกจากเอกสารที่สร้างขึ้น

## สิ่งที่บทแนะนำนี้ครอบคลุม

* การสร้างเอกสาร Word ใหม่ตั้งแต่ต้น  
* การแทรก **แผนภูมิพาย** ด้วย `DocumentBuilder`  
* **การทำให้ชิ้นพายระเบิด** เพื่อเน้นข้อมูลจุดหนึ่ง  
* **การเพิ่มเส้นเชื่อมต่อให้กับพาย** เพื่อทำให้ป้ายชื่อชัดเจนขึ้น  
* การปรับแต่งลักษณะของชิ้นพาย เช่น สีและขอบ  
* การบันทึกเอกสารลงดิสก์และตรวจสอบผลลัพธ์

---

## วิธีทำให้ชิ้นพายระเบิดด้วย Aspose.Words ใน Java

ขั้นตอนแรกคือการตั้งค่าอ็อบเจ็กต์แผนภูมิและทำให้ชิ้นที่ต้องการระเบิดออกมา Aspose.Words เปิดเผยแผนภูมิผ่านคลาส `Shape` และแต่ละชิ้นเป็น `ChartPoint` โดยการตั้งค่า `Explosion` คุณจะควบคุมระยะที่ชิ้นพายเคลื่อนออกจากศูนย์กลาง

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**ทำไมถึงทำงานได้:**  
`setExplosion(20)` บอกให้เอนจินแผนภูมิเลื่อนชิ้นพายออกไป 20 จุดจากศูนย์กลางของแผนภูมิ ค่าเป็นสัมพัทธ์; ตัวเลขที่ใหญ่ขึ้นจะให้เอฟเฟกต์ที่โดดเด่นยิ่งขึ้น คุณสามารถทำให้ชิ้นใดก็ได้ระเบิดโดยเปลี่ยนดัชนี (`get(1)`, `get(2)`, …)

## เพิ่มเส้นเชื่อมต่อให้กับพายเพื่อทำให้ป้ายชื่อชัดเจนขึ้น

เส้นเชื่อมต่อทำหน้าที่เชื่อมป้ายชื่อของชิ้นพายกับขอบของมัน, ซึ่งมีประโยชน์อย่างยิ่งเมื่อชิ้นพายถูกระเบิดหรือแผนภูมิมีหลายส่วนเล็ก ๆ การเรียก `setLeaderLines(true)` จะเปิดใช้งานฟีเจอร์นี้สำหรับซีรีส์ทั้งหมด

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**ทำไมคุณต้องการเส้นเชื่อมต่อ:**  
เมื่อชิ้นพายระเบิด, ป้ายชื่อเริ่มต้นอาจทับซ้อนกับองค์ประกอบอื่น ๆ เส้นเชื่อมต่อช่วยให้ป้ายชื่ออ่านง่ายโดยการวาดเส้นสั้นจากชิ้นพายไปยังกล่องข้อความ

## Java create Word chart – การแทรกชุดข้อมูล

แผนภูมิที่ไม่มีข้อมูลจะไม่มีประโยชน์ คุณต้องเติมชุดข้อมูลด้วย **หมวดหมู่** และ **ค่า** ด้านล่างเราจะเพิ่มสามหมวดหมู่ที่แสดงส่วนแบ่งตลาด

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**คำอธิบาย:**  
`ChartSeries` เก็บทั้งหมวดหมู่ (ชื่อชิ้นพาย) และค่าตัวเลข การเปิดใช้งาน `ShowCategoryName` และ `ShowPercentage` ทำให้แผนภูมิอธิบายตัวเองได้ดี ซึ่งเข้ากันอย่างลงตัวกับเส้นเชื่อมต่อที่เรา **เพิ่มไว้ก่อนหน้า**

## ปรับแต่งชิ้นพายนอกเหนือจากการระเบิด

นอกเหนือจากการทำให้ชิ้นพายระเบิด, คุณมักต้องการปรับสี, ขอบ, หรือแม้กระทั่งซ่อนชิ้นพายทั้งหมด ตัวอย่างโค้ดต่อไปนี้แสดงการปรับแต่งสามอย่างที่พบบ่อย

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**ทำไมต้องปรับแต่งชิ้นพาย:**  
สีที่กำหนดเองทำให้แผนภูมิตรงกับแบรนด์ขององค์กร, ขอบช่วยเพิ่มความอ่านง่ายบนหน้าพิมพ์, การซ่อนชิ้นพายเป็นประโยชน์เมื่อคุณต้องการรักษาโมเดลข้อมูลไว้แต่ต้องการไม่แสดงหมวดหมู่บางอย่างในผลลัพธ์ภาพ

## บันทึกเอกสารและตรวจสอบผลลัพธ์

สุดท้าย, เขียนเอกสารลงดิสก์ คุณสามารถเปิดไฟล์ `.docx` ที่สร้างขึ้นใน Microsoft Word, LibreOffice หรือโปรแกรมดูไฟล์ใด ๆ ที่รองรับฟอร์แมตนี้

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**ผลลัพธ์ที่คาดหวัง:**  
เมื่อคุณเปิด `PieChartDemo.docx`, คุณจะเห็นแผนภูมิพายที่ชิ้นแรก (Product A) ระเบิดออกไป, เส้นเชื่อมต่อชี้จากแต่ละชิ้นไปยังป้ายชื่อ, และชิ้นพายแสดงสีเขียว, น้ำเงิน, และส้มตามที่กำหนดไว้ ชิ้นที่ซ่อน (Product C) จะไม่ปรากฏ, แต่เปอร์เซ็นต์ยังคงรวมเป็น 100 % เนื่องจากข้อมูลยังคงอยู่ในซีรีส์ของแผนภูมิ

---

## ตัวอย่างเต็มที่พร้อมรัน

ด้านล่างเป็นโปรแกรมทั้งหมดที่คุณสามารถคัดลอก, วาง, และรันได้หลังจากเพิ่ม dependency ของ Aspose.Words ลงในโปรเจกต์ของคุณ

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Dependency (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}