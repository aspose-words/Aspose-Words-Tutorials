---
category: general
date: 2026-11-22
description: สร้างแผนภูมิวงกลมใน Java และเรียนรู้วิธีตั้งขนาดแผนภูมิ, เพิ่มป้ายข้อมูล,
  แสดงเปอร์เซ็นต์, และหมุนชิ้นแรกเพื่อให้ได้ภาพที่ชัดเจน
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: th
lastmod: 2026-11-22
og_description: สร้างแผนภูมิวงกลมใน Java จากนั้นตั้งขนาดแผนภูมิ แสดงเปอร์เซ็นต์บนป้ายข้อมูล
  และหมุนชิ้นส่วนแรก—ทั้งหมดในตัวอย่างเดียวที่สามารถรันได้
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: สร้างแผนภูมิวงกลมด้วยขนาดกำหนดเอง, ป้ายชื่อ และการหมุนใน Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: สร้างแผนภูมิวงกลมด้วยขนาดที่กำหนดเอง, ป้ายข้อมูล, และการหมุนใน Java
url: /th/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างแผนภูมิวงกลมด้วยขนาดที่กำหนดเอง, ป้ายข้อมูล, และการหมุนใน Java

หากคุณต้องการ **create pie chart** ใน Java คู่มือนี้จะพาคุณผ่านกระบวนการทั้งหมด คุณจะได้เรียนรู้วิธี **set chart size**, เปิดใช้งาน **show percentages pie chart**, เพิ่ม **data labels pie chart**, และ **rotate pie chart slice** เพื่อให้ส่วนแรกของแผนภูมิเริ่มที่มุม 45 องศา

ตัวอย่างนี้ใช้ **Aspose.Slides for Java**, ไลบรารีที่ใช้กันอย่างแพร่หลายสำหรับการจัดการไฟล์ PowerPoint แนวคิดเดียวกันสามารถใช้กับไลบรารีการสร้างแผนภูมิอื่น ๆ; เพียงแทนที่การเรียก API ด้วยเทียบเท่าในชุดเครื่องมือของคุณ

## ข้อกำหนดเบื้องต้น

* ติดตั้ง Java 17 หรือใหม่กว่า  
* Maven 3.8+ (หรือ Gradle) สำหรับการจัดการ dependencies  
* มีความเข้าใจพื้นฐานเกี่ยวกับไวยากรณ์ของ Java  
* เข้าถึงไฟล์ไบนารี Aspose.Slides for Java (คุณสามารถรับรุ่นทดลองฟรีจากเว็บไซต์ทางการ)

Add the dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## สร้างแผนภูมิวงกลม – ตัวอย่างเต็ม

โปรแกรมต่อไปนี้สร้างสไลด์ PowerPoint ที่มีแผนภูมิวงกลมพร้อมขนาดที่กำหนดเอง, ป้ายข้อมูลเปอร์เซ็นต์, และส่วนแรกที่หมุน

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### ทำไมแต่ละขั้นตอนจึงสำคัญ

| ขั้นตอน | จุดประสงค์ | ความสัมพันธ์กับคีย์เวิร์ด |
|------|---------|--------------------------------|
| **Insert chart** | **Create pie chart** – วัตถุหลักที่จะเรนเดอร์ภาพ | ตรงกับความต้องการ *create pie chart* อย่างตรงไปตรงมา. |
| **Set dimensions** | การเรียก `addChart(..., 400, 300)` แสดงตัวอย่าง **set chart size**. | ควบคุมความกว้าง (400 px) และความสูง (300 px). |
| **Show percentages** | `setShowPercentage(true)` ทำให้แผนภูมิ **show percentages pie chart** บนแต่ละส่วน. | ผู้ใช้มักต้องการเปอร์เซ็นต์แทนค่าดิบ. |
| **Add data labels** | การกำหนดค่า `DataLabelFormat` เพิ่ม **data labels pie chart** พร้อมการมองเห็นตามต้องการ. | ป้ายช่วยเพิ่มความอ่านง่ายและสามารถปรับแต่งได้. |
| **Rotate slice** | `setFirstSliceAngle(45)` หมุนแผนภูมิให้ส่วนแรกเริ่มที่มุม 45 องศา, ทำให้ตรงกับ **rotate pie chart slice**. | เพิ่มการเน้นภาพสำหรับส่วนที่ต้องการ. |

## การแยกขั้นตอนทีละขั้นตอน

### 1. แทรกแผนภูมิวงกลมและตั้งขนาดแผนภูมิ

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*เมธอด `addChart` สร้างแผนภูมิและตั้ง **set chart size** เป็น 400 × 300 จุดพร้อมกัน.*  
หากต้องการขนาดอื่น ปรับค่าอาร์กิวเมนต์สองตัวสุดท้าย.

### 2. เติมข้อมูลลงในแผนภูมิ

ตัวอย่างเพิ่มสามหมวดหมู่และซีรีส์เดียว แทนที่ตัวเลขที่กำหนดไว้ล่วงหน้าด้วยข้อมูลจากฐานข้อมูล, CSV, หรือการป้อนข้อมูลของผู้ใช้ตามต้องการ.

### 3. Show percentages on each slice

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*การเปิดใช้งาน `setShowPercentage(true)` ทำให้แผนภูมิ **show percentages pie chart** คำนวณสัดส่วนของแต่ละส่วนจากยอดรวมโดยอัตโนมัติ.*

### 4. Add detailed data labels

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

คุณสามารถสลับตัวเลือกป้ายอื่น ๆ (`setShowValue`, `setShowSeriesName`, เป็นต้น) เพื่อปรับประสบการณ์ **add data labels pie chart** ให้เหมาะสม.

### 5. Rotate the first slice

```java
chart.setFirstSliceAngle(45);
```

*การเรียก `setFirstSliceAngle(45)` **rotate pie chart slice** ทำให้ส่วนแรกเริ่มที่มุม 45 องศา, ทำให้เด่นขึ้น.*

### 6. บันทึกและดูผลลัพธ์

การรันโปรแกรมจะสร้างไฟล์ `output/PieChartDemo.pptx`. เปิดไฟล์ใน PowerPoint หรือโปรแกรมดูที่รองรับเพื่อดูแผนภูมิวงกลมขั้นสุดท้าย:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="ภาพหน้าจอของแผนภูมิวงกลมที่สร้างขึ้นพร้อมขนาดที่กำหนดเอง, ป้ายเปอร์เซ็นต์, และส่วนแรกที่หมุน"}

ภาพด้านบนแสดงผลลัพธ์ของ **create pie chart**, ยืนยันว่าขนาด, ป้าย, เปอร์เซ็นต์, และการหมุนถูกนำไปใช้อย่างถูกต้อง.

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | การปรับเปลี่ยน |
|-----------|------------|
| **Different chart dimensions** | เปลี่ยนพารามิเตอร์ความกว้าง/ความสูงใน `addChart`. |
| **Multiple series** | เพิ่มอ็อบเจ็กต์ `IChartSeries` เพิ่มเติม; แต่ละซีรีส์สามารถมีการตั้งค่าป้ายของตนเอง. |
| **Custom label format** | ใช้ `series.getDataLabelFormat().setNumberFormat("0.0%")` เพื่อควบคุมตำแหน่งทศนิยม. |
| **Rotating to another angle** | ส่งค่าเต็มจำนวนใด ๆ (0‑360) ให้กับ `setFirstSliceAngle`. |
| **Export as image** | หลังบันทึก, เรียก `chart.writeAsSvg(outPath)` หรือ `chart.writeAsPng(outPath)` เพื่อรับรุ่นภาพราสเตอร์. |

> **เคล็ดลับ:** หากคุณวางแผนสร้างแผนภูมิจำนวนมากในลูป, ให้ใช้วัตถุ `Presentation` เดียวกันและแทนที่ข้อมูลแผนภูมิเท่านั้น. วิธีนี้จะลดการใช้หน่วยความจำและเร่งการประมวลผล.

## สรุป

ตอนนี้คุณรู้วิธี **create pie chart** ใน Java, **set chart size**, เปิดใช้งาน **show percentages pie chart**, **add data labels pie chart**, และ **rotate pie chart slice** เพื่อเน้นภาพให้ดีขึ้น ตัวอย่างที่สมบูรณ์และสามารถรันได้แสดงทุกขั้นตอนตั้งแต่การเริ่มต้นจนถึงการบันทึกไฟล์ PowerPoint สุดท้าย.

### ต่อไปคืออะไร?

* สำรวจประเภทแผนภูมิอื่น ๆ (Bar, Line, Area) ด้วย `ChartType` enum เดียวกัน.  
* รวมหลายแผนภูมิในสไลด์เดียวเพื่อสร้างแดชบอร์ด.  
* ส่งออกแผนภูมิเป็น PNG หรือ SVG เพื่อใช้ในแอปพลิเคชันเว็บ.  

อย่าลังเลที่จะทดลองสี, คำอธิบาย, และเอฟเฟกต์แอนิเมชัน—การแสดงผลข้อมูลของคุณถูกจำกัดเพียงจินตนาการ. ขอให้สนุกกับการสร้างแผนภูมิ!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณเอง.

- [วิธีแทรกแผนภูมิวงกลมใน Word – เพิ่มป้ายข้อมูลเปอร์เซ็นต์](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [วิธีแยกส่วนแผนภูมิวงกลมใน Java – บทแนะนำแผนภูมิ Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [แทรกแผนภูมิวงกลมใน Java – แยกส่วน, หมุน & ไฮไลท์ส่วน](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}