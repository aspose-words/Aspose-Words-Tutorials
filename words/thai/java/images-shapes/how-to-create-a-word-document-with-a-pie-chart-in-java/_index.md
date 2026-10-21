---
category: general
date: 2026-09-18
description: เรียนรู้วิธีสร้างเอกสาร Word และแทรกแผนภูมิวงกลมโดยใช้ Aspose.Words for
  Java รวมถึงการหมุนแผนภูมิวงกลมและขั้นตอนการสร้างไฟล์ Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: th
lastmod: 2026-09-18
og_description: สร้างเอกสาร Word และแทรกแผนภูมิวงกลมโดยใช้ Java ปฏิบัติตามคำแนะนำนี้เพื่อหมุนแผนภูมิวงกลม
  แยกชิ้นส่วนออก และสร้างไฟล์ Word
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: สร้างเอกสาร Word พร้อมแผนภูมิวงกลม – คู่มือ Java ทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: วิธีสร้างเอกสาร Word พร้อมแผนภูมิวงกลมใน Java
url: /th/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างเอกสาร Word พร้อมแผนภูมิวงกลมใน Java

หากคุณต้อง **สร้างเอกสาร Word** ที่แสดงข้อมูลแบบกราฟิก คำแนะนำนี้จะแสดงวิธีทำด้วย Aspose.Words for Java คุณจะได้เรียนรู้การแทรกแผนภูมิวงกลม, ทำให้ส่วนหนึ่งของแผนภูมิแยกออก, หมุนแผนภูมิ, และสุดท้าย **สร้างไฟล์ Word** ที่สามารถเปิดด้วย Microsoft Word

การสร้างรายงานที่รวมข้อความและแผนภูมิไม่จำเป็นต้องใช้เครื่องมือกราฟิกแยกต่างหาก หลังจากทำตามบทเรียนนี้แล้ว คุณจะมีโปรแกรมที่ทำงานได้สมบูรณ์ซึ่งสร้างไฟล์ .docx ที่มีแผนภูมิวงกลมที่กำหนดค่าอย่างเต็มที่

## ข้อกำหนดเบื้องต้น

- Java 17 หรือใหม่กว่า (โค้ดยังคอมไพล์ได้กับ Java 8+)
- Maven หรือ Gradle สำหรับจัดการ dependency
- ไลเซนส์ Aspose.Words for Java (รุ่นทดลองฟรีใช้ได้กับตัวอย่างนี้)
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java

## ขั้นตอนที่ 1: ตั้งค่าโครงการ Maven

สร้างโครงการ Maven ใหม่และเพิ่ม dependency ของ Aspose.Words ลงใน `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **เคล็ดลับ:** คอยอัปเดตหมายเลขเวอร์ชันอยู่เสมอ; รุ่นใหม่มักมีการปรับปรุงประเภทแผนภูมิและแก้บั๊ก

## ขั้นตอนที่ 2: สร้างเอกสาร Word ใหม่

การดำเนินการแรกเมื่อ **สร้างเอกสาร Word** ด้วยโปรแกรมคือการสร้างอ็อบเจ็กต์ `Document` ซึ่งอ็อบเจ็กต์นี้แทนไฟล์ .docx ทั้งหมดในหน่วยความจำ

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

คลาส `Document` เป็นจุดเริ่มต้นของฟีเจอร์การประมวลผล Word ทั้งหมด ไม่มีไฟล์ใดถูกเขียนลงดิสก์ในขั้นตอนนี้; ทุกอย่างเกิดขึ้นใน RAM จนกว่าคุณจะเรียก `save`

## ขั้นตอนที่ 3: วิธีแทรกแผนภูมิวงกลม

`DocumentBuilder` ช่วยให้คุณเพิ่มเนื้อหาเข้าไปในเอกสาร ด้วย `insertChart` คุณสามารถ **แทรกแผนภูมิวงกลม** ได้โดยตรง

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` บอก Aspose.Words ให้สร้างแผนภูมิวงกลม ขนาดจะระบุเป็นจุด (1 pt ≈ 1/72 in) หลังจากเรียกนี้แล้วแผนภูมิจะปรากฏในย่อหน้าใหม่

## ขั้นตอนที่ 4: เติมข้อมูลให้แผนภูมิ

แผนภูมิวงกลมต้องการชุดค่าตัวเลข เราจะเพิ่มสามประเภท: “Apples”, “Bananas”, และ “Cherries”

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

เมธอด `add` สร้างซีรีส์และสร้างรายการใน legend โดยอัตโนมัติ คุณสามารถใช้รูปแบบนี้กับชุดข้อมูลตัวเลขใด ๆ ก็ได้

## ขั้นตอนที่ 5: เน้นส่วนแรกของแผนภูมิ

การทำให้ส่วนหนึ่ง “แยกออก” (explode) จะดึงความสนใจไปยังค่าที่ต้องการ ส่วนแรก (index 0) จะถูกแยกออก 20 จุด

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

การตั้งค่า `explode` บนซีรีส์จะส่งผลต่อแผนภูมิทั้งหมด ดังนั้นจึงมีเพียงจุดข้อมูลแรกเท่านั้นที่ถูกย้ายออก

## ขั้นตอนที่ 6: วิธีหมุนแผนภูมิวงกลม

การหมุนแผนภูมิช่วยให้สมดุลภาพโดยเฉพาะเมื่อส่วนที่ใหญ่ที่สุดไม่ได้อยู่ด้านบน เมธอด `setRotationAngle` รับค่ามุมเป็นองศา

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

การหมุน 45° จะทำให้มุมเริ่มต้นเลื่อนตามเข็มนาฬิกา ทำให้แผนภูมิอ่านง่ายขึ้นในหลายรูปแบบการจัดวาง

## ขั้นตอนที่ 7: บันทึกเอกสารและสร้างไฟล์ Word

สุดท้ายให้เขียนเอกสารลงดิสก์ ขั้นตอนนี้ **generate word file** ที่สามารถเปิดด้วย Microsoft Word, LibreOffice หรือโปรแกรมดูไฟล์ที่รองรับอื่น ๆ

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

เมธอด `save` จะตรวจจับส่วนขยาย .docx โดยอัตโนมัติและเขียนแพ็กเกจที่เข้ากันได้กับ Word โฟลเดอร์ `output` ต้องมีอยู่แล้วหรือคุณสามารถสร้างมันด้วยโค้ดได้

### ผลลัพธ์ที่คาดหวัง

หลังจากรันโปรแกรมแล้ว เปิด `output/PieChart.docx` คุณควรเห็น:

- หน้าหนึ่งหน้าเดียวที่มีแผนภูมิวงกลมขนาด 400 × 300 pt
- ส่วน “Apples” แยกออกจากศูนย์ 20 pt
- แผนภูมิทั้งหมดหมุน 45° ตามเข็มนาฬิกา
- Legend ที่ตรงกับสามประเภทผลไม้

## ความแตกต่างทั่วไปและกรณีขอบ

### การแทรกหลายแผนภูมิ

หากต้องการแผนภูมิมากกว่าหนึ่งอัน ให้เรียก `builder.insertChart` อีกครั้งหลังจากย้ายเคอร์เซอร์:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### การเปลี่ยนสีแผนภูมิ

คุณสามารถกำหนดสีของแต่ละส่วนได้ผ่านคอลเลกชัน `getPoints()` ของซีรีส์:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### การจัดการชุดข้อมูลขนาดใหญ่

สำหรับชุดข้อมูลที่มีมากกว่า 10 ส่วน ควรพิจารณาใช้แผนภูมิดอนัท (`ChartType.DOUGHNUT`) เพื่อให้ภาพดูชัดเจนยิ่งขึ้น

## สรุป

ตอนนี้คุณรู้วิธี **สร้างเอกสาร Word**, **แทรกแผนภูมิวงกลม**, **หมุนแผนภูมิวงกลม**, และ **สร้างไฟล์ Word** ด้วย Aspose.Words for Java โซลูชันเต็มรูปแบบนี้แสดงขั้นตอนการทำงานตั้งแต่การเริ่มต้นเอกสารจนถึงการส่งออกไฟล์สุดท้าย พร้อมอธิบาย “วิธีทำ” และ “ทำไม” ของแต่ละขั้นตอน

ต่อไปลองสำรวจหัวข้อที่เกี่ยวข้อง เช่น **วิธีสร้างข้อมูลแผนภูมิวงกลม** จากฐานข้อมูล, การเพิ่มป้ายข้อมูล, หรือการส่งออกแผนภูมิเป็นรูปภาพ ทดลองใช้ประเภทแผนภูมิต่าง ๆ (แถบ, เส้น, ดอนัท) เพื่อขยายเครื่องมืออัตโนมัติของ Word ของคุณ

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโครงการของคุณ

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}