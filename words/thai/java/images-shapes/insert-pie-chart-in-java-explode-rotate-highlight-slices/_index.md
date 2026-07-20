---
category: general
date: 2026-07-20
description: แทรกแผนภูมิวงกลมใน Java พร้อมคู่มือขั้นตอนโดยละเอียด เรียนรู้วิธีแยกชิ้นส่วน,
  วิธีหมุนแผนภูมิวงกลม, เน้นชิ้นส่วนของแผนภูมิวงกลมและปรับแต่งชิ้นส่วนของแผนภูมิวงกลม
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: th
lastmod: 2026-07-20
og_description: แทรกแผนภูมิวงกลมใน Java และเชี่ยวชาญการทำให้ส่วนของแผนภูมิแยกออก,
  การหมุนแผนภูมิวงกลม, การไฮไลท์ส่วนของแผนภูมิ, และการปรับแต่งส่วนของแผนภูมิเพื่อสร้างรายงานภาพที่สวยงามและเป็นมืออาชีพ.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: แทรกแผนภูมิวงกลมใน Java – แยกชิ้น, หมุน & เน้น
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: แทรกแผนภูมิวงกลมใน Java – แยกชิ้น, หมุนและไฮไลท์ส่วน
url: /th/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกแผนภูมิวงกลมใน Java – แยกส่วน, หมุน และไฮไลท์สไลซ์

เคยต้องการ **insert pie chart** ในรายงาน Java แต่ไม่แน่ใจว่าจะทำให้สไลซ์เดียวเด้งออกมาอย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว ไม่ว่าคุณจะสร้างแดชบอร์ด, สร้างใบแจ้งหนี้, หรือเพียงแค่แสดงผลการสำรวจ, แผนภูมิวงกลมที่ออกแบบดีสามารถเปลี่ยนตัวเลขดิบให้เป็นข้อมูลเชิงลึกที่เข้าใจได้ทันที.

ในบทแนะนำนี้คุณจะได้เห็นตัวอย่างที่สมบูรณ์และพร้อมทำงานที่แสดงวิธีการแทรกแผนภูมิวงกลม, **how to explode slice**, **how to rotate pie chart**, และแม้กระทั่ง **highlight pie chart slice** ด้วยสีที่กำหนดเอง. เมื่อเสร็จคุณจะมีโค้ดสั้นที่สามารถนำไปใช้ในโครงการ Java ใด ๆ ที่ใช้ไลบรารี *JFreeChart* ที่เป็นที่นิยม (หรือ API ที่คล้ายกัน).

## ความต้องการเบื้องต้น

- Java 17 หรือใหม่กว่า (โค้ดสามารถคอมไพล์กับเวอร์ชันเก่าได้, แต่เราจะใช้ไวยากรณ์ `var` สมัยใหม่เพื่อความกระชับ).  
- Maven หรือ Gradle เพื่อดึง dependency `org.jfree:jfreechart`.  
- ความเข้าใจพื้นฐานเกี่ยวกับคลาส Java และแนวคิดของ chart builder.  

หากคุณยังไม่เคยเพิ่มไลบรารีลงในโครงการ Maven, เพียงแค่ใส่ส่วนนี้ลงในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

แค่นั้น—ไม่ต้องตั้งค่าเพิ่มเติม.

## ขั้นตอนที่ 1: แทรกแผนภูมิวงกลม – สร้าง Builder และอ็อบเจ็กต์ Chart

สิ่งแรกที่ต้องทำคือเราต้องการ *builder* (คิดว่าเป็นโรงงาน) ที่รู้วิธีสร้างแผนภูมิ. ใน JFreeChart `ChartFactory` ทำหน้าที่หลัก.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

ทำไมเราถึงเริ่มจากชุดข้อมูล? เพราะแผนภูมิเองเป็นเพียงกรอบภาพที่ห่อหุ้มตัวเลข. โดย **inserting pie chart** ที่นี่เราจะมีแคนวาสขนาด 400 × 300 (ขนาดจะถูกกำหนดในภายหลังเมื่อเราวาดเป็นภาพ).

## ขั้นตอนที่ 2: How to Explode Slice – เน้นส่วนแรก

เมื่อแผนภูมิพร้อมแล้ว, ให้ทำให้สไลซ์แรกโดดเด่น. การแยกสไลซ์ (explode) จะทำให้มันเลื่อนออกจากวงกลมเล็กน้อย, ดึงความสนใจของผู้อ่าน.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

สังเกตว่าเราใช้วลี **how to explode slice** ในชื่อเมธอด; ทำให้เจตนาชัดเจน. เมธอด `setExplodePercent` รับคีย์ (ป้ายสไลซ์) และเปอร์เซ็นต์, ดังนั้นคุณสามารถปรับระยะ “pop‑out” ตามต้องการ.

## ขั้นตอนที่ 3: How to Rotate Pie Chart – เปลี่ยนมุมเริ่มต้น

แผนภูมิวงกลมเริ่มต้นโดยค่าเริ่มต้นที่ตำแหน่ง 12 นาฬิกา. บางครั้งคุณอาจต้องการให้สไลซ์แรกเริ่มที่ตำแหน่งอื่น—อาจเพื่อให้สอดคล้องกับการออกแบบต้นแบบหรือเพื่อให้ตรงกับแผนภูมิอื่น.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

การเรียก `rotateChart(chart, 45)` จะหมุนวงกลมทั้งหมดให้สไลซ์ “Apples” เริ่มที่มุม 45 องศา, ตรงกับความต้องการของ **how to rotate pie chart**.

## ขั้นตอนที่ 4: Highlight Pie Chart Slice – สีและป้ายกำกับแบบกำหนดเอง

นอกจากการแยกสไลซ์, คุณอาจต้องการให้สไลซ์มีสีเฉพาะหรือป้ายที่หนาเพื่อ **highlight pie chart slice** อย่างแท้จริง.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

ที่นี่เราได้ **customize pie chart slice** โดยการเปลี่ยนสีและสไตล์ของป้าย. คุณสามารถเปลี่ยนสีหรือฟอนต์ให้ตรงกับพาเลตของแบรนด์คุณได้.

## ขั้นตอนที่ 5: เรนเดอร์แผนภูมิเป็นภาพ (เป็นตัวเลือกแต่สะดวก)

แอปพลิเคชันส่วนใหญ่ในโลกจริงต้องการแผนภูมิในรูปแบบ PNG, JPEG หรือแม้แต่ PDF. ด้านล่างเป็นวิธีรวดเร็วในการบันทึกแผนภูมิเป็นไฟล์.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

การรันขั้นตอนทั้งหมดจะสร้าง PNG ขนาด 400 × 300 ที่มีลักษณะประมาณนี้:

![Insert pie chart example](image.png){: alt="ตัวอย่างการแทรกแผนภูมิวงกลมแสดงสไลซ์ที่แยกและหมุน"}

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน, นี่คือเมธอด `main` ที่คุณสามารถคัดลอกและวางลงในคลาส Java ใหม่และรันได้:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### ผลลัพธ์ที่คาดหวัง

การรันโปรแกรมจะสร้างไฟล์ชื่อ **fruit-pie.png**. เปิดไฟล์แล้วคุณจะเห็น:

- แผนภูมิวงกลมขนาด 400 × 300 มีหัวเรื่อง “Fruit Distribution”.  
- สไลซ์ “Apples” แยกออกไปด้านนอก 15 %.  
- แผนภูมิทั้งหมดหมุนให้ “Apples” เริ่มที่ตำแหน่ง 45‑degree.  
- ส่วนที่แยก  

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งรวมตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Insert Scatter Chart](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Insert Area Chart](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}