---
category: general
date: 2026-10-26
description: สร้างแผนภูมโดนัทและแทรกแผนภูมิพายใน Java ด้วยโค้ดทีละขั้นตอน เรียนรู้กระบวนการทำงานเต็มรูปแบบสำหรับการแสดงผลแผนภูมิที่ยืดหยุ่น
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: th
lastmod: 2026-10-26
og_description: สร้างแผนภูมิดอนัทใน Java ด้วยคู่มือนี้ ซึ่งยังแสดงวิธีแทรกแผนภูมิพายเพื่อการแสดงผลที่ยืดหยุ่น.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: สร้างแผนภูมิดอนัทและแทรกแผนภูมิวงกลม – คู่มือ Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: วิธีสร้างแผนภูมิดอนัทและแทรกแผนภูมิพาย
url: /th/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างแผนภูมิดอนัทและแทรกแผนภูมิพาย

หากคุณต้องการ **create doughnut chart** ใน Java, บทแนะนำนี้จะพาคุณผ่านขั้นตอนอย่างละเอียด เราจะสาธิตวิธี **insert pie chart** ด้วย Builder API เดียวกัน เพื่อให้คุณสลับสไตล์การแสดงผลได้อย่างง่ายดาย เมื่อจบคู่มือคุณจะได้โปรแกรมที่ทำงานได้สมบูรณ์ สามารถสร้างแผนภูมิทั้งสองประเภทและแสดงการปรับแต่งทั่วไป

บทแนะนำครอบคลุม:

* การเริ่มต้น Chart Builder ที่มาจากไลบรารีที่เลือกใช้  
* การสร้างแผนภูมิดอนัทและกำหนดขนาดของรูตรงกลาง  
* การแทรกแผนภูมีพายและทำการ explode slice เพื่อเน้น  
* เคล็ดลับการจัดการกรณีขอบเขต เช่น series ที่หายไปหรือประเภทแผนภูมิที่ไม่รองรับ  

คุณต้องมี JDK เวอร์ชันล่าสุด (8 หรือใหม่กว่า) และไฟล์ JAR ของไลบรารีแผนภูมิใน classpath เท่านั้น ไม่ต้องใช้บริการภายนอกใด ๆ

---

## ข้อกำหนดเบื้องต้น

| รายการ | เหตุผล |
|------|--------|
| Java Development Kit (JDK) 8+ | จำเป็นสำหรับคอมไพล์และรันตัวอย่าง |
| Chart library (เช่น **Aspose.Cells for Java** หรือ **JFreeChart**) | มี `ChartBuilder`, `ChartType` และเมธอดจัดการ series ที่ใช้ในโค้ด |
| An IDE or a text editor | เพื่อเขียนและรันไฟล์ซอร์ส Java |

ตรวจสอบให้แน่ใจว่าไฟล์ JAR ของไลบรารีได้ถูกเพิ่มเข้าไปใน build path ของโปรเจกต์ หากคุณใช้ Maven ให้เพิ่ม dependency ที่เหมาะสม; หากไม่ใช้ ให้วาง JAR ไว้ในโฟลเดอร์ `libs` แล้วอ้างอิงในขั้นตอนคอมไพล์

---

## ขั้นตอนที่ 1: ตั้งค่า Chart Builder

ขั้นตอนแรกคือการสร้างอินสแตนซ์ `ChartBuilder` (หรือเทียบเท่า) ที่จะสร้างอ็อบเจกต์แผนภูมิ อ็อบเจกต์นี้ทำหน้าที่เป็น factory และถือ worksheet หรือ canvas ที่แผนภูมิจะถูกวางไว้

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
Builder จะผูกแผนภูมิกับ worksheet เฉพาะ ทำให้แผนภูมิที่สร้างต่อมาทั้งหมดใช้พื้นผิวการวาดเดียวกัน หากข้ามขั้นตอนนี้จะไม่มีตำแหน่งเป้าหมายสำหรับองค์ประกอบภาพ

---

## ขั้นตอนที่ 2: **Create doughnut chart**

ตอนนี้เราจะสร้างแผนภูมิดอนัทโดยกำหนดขนาดรูตรงกลาง ขนาดรูจะกำหนดว่ากลางแผนภูมิจะว่างเปล่าเท่าใด ทำให้พายธรรมดากลายเป็นดอนัท

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Explanation:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` สร้างอ็อบเจกต์แผนภูมิและจองพื้นที่บน worksheet  
* `setHoleSize(30)` แปลงพายเป็นดอนัทโดยมีศูนย์ว่าง 30 %  
* `add("{10, 20, 30, 40}", true)` ส่งค่าข้อมูลสี่จุด; ธง `true` บอกไลบรารีให้ถือค่าดังกล่าวเป็น series เดียว  

**Edge case:** หากประเภทแผนภูมิที่เลือกไม่รองรับรู (เช่น แผนภูมิแท่ง) การเรียก `getDoughnutChart()` จะทำให้เกิด exception ควรตรวจสอบประเภทแผนภูมิก่อนปรับขนาดรู

---

## ขั้นตอนที่ 3: **Insert pie chart**

หลังจากดอนัทพร้อมแล้ว เราจะแสดงวิธี **insert pie chart** ด้วย Builder เดียวกัน ขั้นตอนนี้เน้นความคล้ายคลึงระหว่างสองประเภทแผนภูมิและวิธีเน้น slice

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Explanation:**  

* `ChartType.PIE` บอก Builder ให้สร้างแผนภูมีพายแบบคลาสสิก  
* `setExplode(10)` เลื่อน slice แรกออกจากศูนย์ 10 % ของรัศมี เป็นเทคนิคทั่วไปเพื่อเน้นข้อมูลสำคัญ  

**Tip:** เมธอด `setExplode` ทำงานได้เฉพาะ series แรกของแผนภูมีพาย หากมีหลาย series ต้องระบุ index ที่ถูกต้อง

---

## ขั้นตอนที่ 4: บันทึก Workbook

สุดท้ายให้เขียน workbook ลงไฟล์เพื่อให้คุณสามารถดูแผนภูมิใน Excel หรือโปรแกรมดูไฟล์ที่รองรับได้

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Why save now:** การบันทึก workbook จะสรุปการดำเนินการวาดทั้งหมด หากพยายามเปิดไฟล์ก่อนบันทึกจะได้เอกสารที่ว่างเปล่าหรือไม่สมบูรณ์  

**Result:** การเปิด *DoughnutAndPieChart.xlsx* จะเห็นแผนภูมิดอนัทที่มีรู 30 % อยู่ด้านซ้าย และแผนภูมีพายที่ slice แรกถูก explode อยู่ด้านขวา

---

## ขั้นตอนที่ 5: ตัวแปรทั่วไปและการแก้ปัญหา

| สถานการณ์ | การปรับเปลี่ยน |
|-----------|------------|
| **Different chart dimensions** | เปลี่ยนค่า width และ height ใน `insertChart` |
| **Multiple data series** | เรียก `add` หลายครั้งหรือส่งสตริงอาร์เรย์ 2‑D |
| **Dynamic hole size** | คำนวณขนาดรูจากช่วงข้อมูลแล้วเรียก `setHoleSize` |
| **Explode multiple slices** | วนลูป `chart.getSeries().get(i).setExplode(percent)` สำหรับแต่ละ slice ที่ต้องการ offset |
| **Library not supporting doughnut** | ใช้แผนภูมีพายแล้ววาดวงกลมสีขาวทับเอง แม้จะแม่นยำน้อยกว่า |

**Pro tip:** ควรเรียก `builder.flush()` (หากมี) หลังจากแทรกแผนภูมิเมื่อทำงานกับ workbook ขนาดใหญ่ เพื่อปล่อยบัฟเฟอร์ภายในและป้องกัน memory leak

![Java code creating a doughnut chart and inserting a pie chart](https://example.com/images/doughnut-pie-java.png "create doughnut chart example in Java")

*ภาพแสดงเลย์เอาต์สุดท้ายของ workbook ที่มีแผนภูมิทั้งสองข้างกัน*

---

## สรุป

ตอนนี้คุณรู้วิธี **create doughnut chart** และ **insert pie chart** ใน Java ด้วย Fluent Builder API ตัวอย่างเต็มครอบคลุมการเริ่มต้น, การกำหนดขนาด, การตั้งค่ารู, การ explode slice, และการส่งออกไฟล์ จากนี้คุณสามารถสำรวจการปรับแต่งเพิ่มเติม เช่น สี, legend, และ data label เพื่อให้ตรงกับความต้องการรายงานของคุณ

**ขั้นตอนต่อไป**

* ทดลองใช้คุณลักษณะ **chart customization Java** เช่น gradient fill และ data label  
* ผสานการสร้างแผนภูมิกับเว็บเซอร์วิสที่ส่งคืน workbook ตามคำขอ  
* เปรียบเทียบแนวทาง Builder กับไลบรารีอื่น (เช่น JFreeChart) เพื่อเลือกวิธีที่เหมาะกับโปรเจกต์ของคุณ

ขอให้สนุกกับการสร้างแผนภูมิ!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ

- [วิธีสร้างแผนภูมิดอนัทในเอกสาร Word ด้วย Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [บันทึกเอกสาร Word หลังแก้ไขแผนภูมิดอนัทใน Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [แทรกแผนภูมีพายใน Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}