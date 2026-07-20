---
category: general
date: 2026-07-20
description: วิธีแทรกแผนภูมิวงกลมใน Word ด้วย Aspose.Words. เรียนรู้การเพิ่มป้ายข้อมูลเปอร์เซ็นต์และแสดงเปอร์เซ็นต์บนแผนภูมิสำหรับเอกสารระดับมืออาชีพ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: th
lastmod: 2026-07-20
og_description: วิธีแทรกแผนภูมิวงกลมใน Word ด้วย Aspose.Words คู่มือนี้แสดงวิธีเพิ่มเปอร์เซ็นต์ของป้ายข้อมูลและแสดงเปอร์เซ็นต์บนแผนภูมิในไม่กี่บรรทัด
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: วิธีแทรกแผนภูมิวงกลมใน Word – คู่มือด่วน
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: วิธีแทรกแผนภูมิวงกลมใน Word – เพิ่มเปอร์เซ็นต์ป้ายข้อมูล
url: /th/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทรกแผนภูมิวงกลมใน Word – เพิ่มป้ายข้อมูลเปอร์เซ็นต์

เคยสงสัย **วิธีแทรกแผนภูมิวงกลม** ลงในเอกสาร Word โดยไม่ต้องต่อสู้กับ UI หรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายสถานการณ์การรายงานคุณต้อง *เพิ่มแผนภูมิวงกลมลงใน Word* และที่สำคัญกว่า **แสดงเปอร์เซ็นต์บนแผนภูมิวงกลม** เพื่อให้ผู้อ่านเข้าใจการกระจายข้อมูลได้ทันที

ในบทแนะนำนี้เราจะเดินผ่านกระบวนการทั้งหมดโดยใช้ Aspose.Words for Java. เมื่อจบคุณจะรู้วิธี **เพิ่มป้ายข้อมูลเปอร์เซ็นต์**, **แสดงเปอร์เซ็นต์บนแผนภูมิ**, และได้แผนภูมิวงกลมที่ดูดีตั้งแต่ครั้งแรก ไม่ต้องใช้ปลั๊กอินเพิ่มเติม ไม่ต้องปรับแต่งด้วยมือ—แค่โค้ดสะอาดที่คุณสามารถใส่ลงในโปรเจกต์ใดก็ได้

---

## Prerequisites

- Java 17 (หรือใหม่กว่า) – เวอร์ชัน LTS ปัจจุบันที่ Aspose.Words รองรับ
- Aspose.Words for Java 24.x (รุ่นล่าสุด ณ เวลาที่เขียน, กรกฎาคม 2026)
- การตั้งค่า Maven หรือ Gradle เบื้องต้นเพื่อดึงไลบรารี
- IDE ที่คุณชอบ (IntelliJ IDEA, Eclipse, VS Code… ใช้ได้ทุกตัว)

หากคุณมีทั้งหมดนี้แล้ว เยี่ยม—มาเริ่มกันเลย

---

## Step 1: Set up the project and import the library

First, add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). This gives you access to the `Document`, `DocumentBuilder`, and chart classes.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Keep the version number up‑to‑date; newer releases often add chart‑related fixes that make **display percentages on chart** more reliable.

---

## Step 2: Create a new Word document and a builder

The builder is your Swiss‑army knife for inserting content. Here we create a fresh document and attach a `DocumentBuilder` to it.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ทำไมเราต้องใช้ builder? มันทำหน้าที่เป็นชั้นนามธรรมของโครงสร้าง OpenXML ระดับต่ำ ให้เรามุ่งเน้นที่ *สิ่งที่ต้องการ* — เช่น **add pie chart to word** — แทนที่จะกังวลว่า XML จะเป็นอย่างไร

---

## Step 3: Insert the pie chart

Now comes the core of **how to insert pie chart**. We ask the builder to place a pie chart of a specific size. The dimensions are in points (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

ในขั้นตอนนี้แผนภูมิก็ยังว่างเปล่า แต่ตำแหน่งที่วางไว้ได้ถูกแทรกลงในเอกสารแล้ว คุณจึง **add pie chart to word** ด้วยโปรแกรมได้แล้ว

---

## Step 4: Populate the chart with data

A pie chart needs at least one series of values. Let’s feed it some sample data that represents market share.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

หากต้องการหลาย series (pie แบบ stacked, doughnut ฯลฯ) คุณสามารถเรียก `pieChart.getSeries().add()` แล้วทำซ้ำขั้นตอนเดิมได้ ตรรกะเดียวกันใช้ได้เมื่อคุณต้องการ **display percentages on chart** สำหรับแต่ละชิ้น

---

## Step 5: **add data label percent** – show the percentages on the slices

This is the part most developers forget: configuring the data labels to show percentages. Without it, the chart only shows raw numbers, which can be ambiguous.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

การเรียก `setShowPercent(true)` บอก Aspose.Words ให้เรนเดอร์ป้ายเป็น “30 %”, “45 %” เป็นต้น นั่นคือวิธีที่คุณ **show percent on pie chart** โดยไม่ต้องทำการจัดรูปแบบเพิ่มเติม

---

## Step 6: Save the document

Finally, write the document to disk. You can choose `.docx`, `.pdf`, or even `.html`. For this guide we’ll stick with the modern `.docx` format.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Run the program, open `PieChartDemo.docx`, and you’ll see a neatly rendered pie chart with percentage labels on each slice.

---

## Expected output

Below is a screenshot of the generated Word file. Notice how each slice displays its share as a percentage—exactly what we wanted when we set **add data label percent**.

![Screenshot of a Word document containing a pie chart with percentage labels](/images/pie-chart-percent.png){.center width=600px alt="ภาพหน้าจอแสดงวิธีแทรกแผนภูมิวงกลมใน Word พร้อมป้ายเปอร์เซ็นต์"}

*The alt text includes the primary keyword, satisfying both SEO and accessibility.*

---

## Common questions & edge‑case handling

| คำถาม | คำตอบ |
|----------|--------|
| **Can I change the font of the percentage labels?** | ใช่ หลังจากเปิดใช้งาน `setShowPercent(true)` ให้ดึงอ็อบเจ็กต์ `DataLabel` แล้วปรับคุณสมบัติ `Font` (`dataLabel.getFont().setSize(10);`). |
| **What if I need a doughnut chart instead of a pie?** | แทนที่ `ChartType.PIE` ด้วย `ChartType.DOUGHNUT` ในการเรียก `insertChart` การทำงานของ **add data label percent** ยังคงใช้ได้. |
| **Do older Word versions (2007‑2010) display the percentages correctly?** | Aspose.Words เขียน XML พื้นฐานในรูปแบบที่ไม่ขึ้นกับเวอร์ชัน ดังนั้นเปอร์เซ็นต์จะแสดงใน Word ใดก็ได้ที่รองรับแผนภูมิ (2007+). |
| **How to add a title to the chart?** | ใช้ `pieChart.getTitle().setText("Market Share");` ก่อนบันทึกไฟล์. |
| **Can I insert the chart into a specific paragraph or table cell?** | แน่นอน ย้าย `DocumentBuilder` ไปยังตำแหน่งที่ต้องการ (`builder.moveToParagraph(index, true);` หรือ `builder.moveToCell(table, row, column, true);`) ก่อนเรียก `insertChart`. |

---

## Tips and tricks from the field

- **Pro tip:** หากต้องสร้างแผนภูมิหลาย ๆ ชิ้นในลูป ให้ใช้ `DocumentBuilder` ตัวเดียวซ้ำหลายครั้ง; จะช่วยลดการใช้หน่วยความจำ.
- **Watch out for:** ชิ้นที่เล็กมาก (< 2 %). Aspose.Words อาจละเว้นป้ายเพื่อหลีกเลี่ยงความแออัด; คุณสามารถบังคับให้แสดงด้วย `dataLabel.setShowLabel(true);`.
- **Performance note:** การเรนเดอร์แผนภูมิใช้ CPU มาก สำหรับการสร้างรายงานจำนวนมาก ควรพิจารณาใช้ multi‑threading แต่ต้องให้แต่ละเธรดทำงานกับอ็อบเจ็กต์ `Document` ของตนเอง.
- **Version check:** เมธอด `setShowPercent` ถูกเพิ่มใน Aspose.Words 22.8. หากคุณใช้เวอร์ชันเก่า ให้อัปเกรดหรือคำนวณเปอร์เซ็นต์เองแล้วตั้งเป็นป้ายแบบกำหนดเอง.

---

## Recap

เราได้ครอบคลุม **how to insert pie chart** ลงในเอกสาร Word ด้วย Aspose.Words, แสดงวิธี **add data label percent**, และสาธิตวิธี **display percentages on chart** ที่ง่ายที่สุด ด้วยเพียงไม่กี่บรรทัด Java คุณก็สามารถ **add pie chart to word** และ **show percent on pie chart** ทำให้ตัวเลขดิบกลายเป็นภาพที่อ่านง่ายทันที

---

## What’s next?

- ทดลองใช้ประเภทแผนภูมิอื่น (`BAR`, `LINE`, `AREA`) แล้วดูว่าตรรกะ **add data label percent** ทำงานอย่างไรในแต่ละแบบ
- ผสานแผนภูมิกับตารางเพื่อสร้างรายงานที่หลากหลาย—Aspose.Words ทำให้การวางแผนภูมิติดข้างตารางเป็นเรื่องง่าย
- สำรวจการส่งออกเอกสารเดียวกันเป็น PDF หรือ HTML เพื่อดูว่าการแสดงเปอร์เซ็นต์ทำงานข้ามฟอร์แมตอย่างไร

อย่าลืมปรับขนาด, สี, หรือแหล่งข้อมูล (เช่น คำสั่ง query จากฐานข้อมูล) แล้วดูรายงาน Word ของคุณมีชีวิตชีวาขึ้น หากเจอปัญหาใด ๆ คอมเมนต์ด้านล่างได้เลย—ขอให้สนุกกับการสร้างแผนภูมิ!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}