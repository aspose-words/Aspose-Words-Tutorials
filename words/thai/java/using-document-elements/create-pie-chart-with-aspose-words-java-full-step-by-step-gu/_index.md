---
category: general
date: 2026-07-16
description: สร้างแผนภูมิวงกลมใน Java ด้วย Aspose.Words เรียนรู้วิธีเพิ่มเส้นนำ, แสดงคำอธิบายแผนภูมิ,
  และแยกชิ้นส่วนออกในบทเรียนเดียว.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: th
lastmod: 2026-07-16
og_description: สร้างแผนภูมิวงกลมใน Java ด้วย Aspose.Words คู่มือนี้จะแสดงวิธีเพิ่มเส้นเชื่อม,
  แสดงคำอธิบายแผนภูมิ, และแยกชิ้นส่วนออก ทำให้คุณได้ภาพที่ดูเรียบหรูในไม่กี่นาที.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: สร้างแผนภูมิวงกลมด้วย Aspose.Words Java – บทเรียนการจัดรูปแบบอย่างครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: สร้างแผนภูมิวงกลมด้วย Aspose.Words Java – คู่มือเต็มขั้นตอนโดยละเอียด
url: /th/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างแผนภูมิวงกลมด้วย Aspose.Words Java – คู่มือเต็มขั้นตอน

เคยสงสัยไหมว่าจะแบบใดที่จะ **สร้างแผนภูมิวงกลม** ด้วยโปรแกรมใน Java โดยไม่ต้องต่อสู้กับ API การวาดระดับต่ำ? คุณไม่ได้เป็นคนเดียว นักพัฒนาจำนวนมากต้องการภาพรวดเร็วสำหรับรายงาน, แดชบอร์ด, หรือเอกสารอัตโนมัติ และพวกเขาจึงเลือกใช้ Aspose.Words เพราะมันจัดการงานหนักให้

ในบทแนะนำนี้ เราจะเดินผ่านตัวอย่างที่สมบูรณ์และพร้อมรัน ซึ่งไม่เพียงแต่ **สร้างแผนภูมิวงกลม** แต่ยังแสดงวิธี **เพิ่มเส้นนำ**, **แสดง chart legend**, และแม้กระทั่ง **explode slice** เพื่อเน้นย้ำ. เมื่อเสร็จคุณจะได้ไฟล์ `.docx` ที่ดูเรียบหรูพอที่จะทำให้ลูกค้าประทับใจ.

> **ผลลัพธ์เร็ว:** โค้ดสแนปช็อตด้านล่างทำงานได้ทันทีกับ Aspose.Words for Java 23.9 (หรือเวอร์ชันใหม่กว่า) ไม่ต้องพึ่งพาไลบรารีเพิ่มเติม เพียงแค่ JAR.

## สิ่งที่คุณจะได้เรียนรู้

- ตั้งค่าเอกสาร Word ว่างด้วย `DocumentBuilder`.
- แทรก **แผนภูมิวงกลม** ขนาดกำหนดเอง.
- ใช้ฟีเจอร์ **explode slice** เพื่อเน้นจุดข้อมูล.
- เปิดใช้งาน **leader lines** เพื่อให้ส่วนที่ระเบิดเชื่อมต่อกับป้ายกำกับ.
- เปิด **chart legend** เพื่อให้ผู้อ่านสามารถระบุแต่ละส่วนได้ทันที.
- บันทึกผลลัพธ์เป็นไฟล์ `.docx` ที่คุณสามารถเปิดใน Microsoft Word หรือ LibreOffice.

**ข้อกำหนดเบื้องต้น** – คุณจะต้องมี:

1. ติดตั้ง Java 17 (หรือใหม่กว่า)
2. มี JAR ของ Aspose.Words for Java อยู่ใน classpath ของคุณ
3. IDE หรือโปรแกรมแก้ไขข้อความพื้นฐาน—IntelliJ IDEA, Eclipse, VS Code, หรือที่คุณชอบ

ตอนนี้ เรามาเริ่มกันเลย.

## ขั้นตอนที่ 1: เริ่มต้น Document และ Builder – เตรียม **สร้างแผนภูมิวงกลม**

ก่อนอื่น เราต้องการผืนผ้าใบเอกสารที่สะอาด `Document` แทนไฟล์ Word ทั้งหมด ส่วน `DocumentBuilder` เป็นตัวช่วยที่ให้เราสามารถเพิ่มเนื้อหาได้

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **ทำไมเรื่องนี้สำคัญ:** การเริ่มต้นด้วย `Document` ใหม่รับประกันว่าจะไม่มีสไตล์ที่ซ่อนอยู่หรือวัตถุที่เหลือซึ่งอาจขัดขางการแสดงแผนภูมิ

## ขั้นตอนที่ 2: แทรก **แผนภูมิวงกลม** – ขนาดสำคัญ

Aspose.Words ทำให้การแทรกแผนภูมิเป็นบรรทัดเดียว ที่นี่เราขอแผนภูมิวงกลมขนาด 400 × 300 จุด—ประมาณ 5.5 × 4.2 นิ้วบนหน้าจอทั่วไป

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **เคล็ดลับ:** หากต้องการขนาดอื่น เพียงเปลี่ยนตัวเลขสองค่า API ทำงานเป็นจุด โดยที่ 72 จุด = 1 นิ้ว

## ขั้นตอนที่ 3: **วิธีการ explode slice** – เน้นจุดข้อมูลสำคัญ

การ explode slice จะดึงส่วนออกจากส่วนอื่นของวงกลม ทำให้ผู้อ่านสนใจ จุด `setExplosion` รับจำนวนเต็มที่แสดงระยะทางเป็นจุด

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **ถ้าคุณมีหลาย series?** คุณสามารถเรียก `setExplosion` บนดัชนี series ใดก็ได้ (`get(1)`, `get(2)`, …) เพื่อ explode ส่วนต่าง ๆ

## ขั้นตอนที่ 4: **เพิ่ม leader lines** และ **แสดง chart legend** – เชื่อมต่อจุดต่าง ๆ

เมื่อส่วนหนึ่งถูก explode ป้ายกำกับอาจหลุดออกไป เส้นนำ (leader lines) จะทำให้ป้ายกำกับเชื่อมต่ออยู่ คงความอ่านง่าย ในขณะเดียวกัน คำอธิบาย (legend) ให้คีย์อย่างรวดเร็วสำหรับทุกส่วน

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **ทำไมต้องเปิดใช้ leader lines?** หากไม่มี เส้นเหล่านี้ ป้ายกำกับอาจดูลอยอยู่ ทำให้ผู้ใช้สับสนว่าเป็นของส่วนไหน  
> **ต้องการตำแหน่ง legend ที่กำหนดเอง?** ใช้ `chart.getLegend().setPosition(LegendPosition.TOP)` หรือค่า enum อื่น ๆ

## ขั้นตอนที่ 5: บันทึก Document – ขั้นตอนสุดท้ายของ **สร้างแผนภูมิวงกลม**

สุดท้าย เราจะบันทึกเอกสารลงดิสก์ ปรับเส้นทางให้เป็นโฟลเดอร์ที่คุณมีสิทธิ์เขียน

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

รันโปรแกรม เปิดไฟล์ `PieChartDemo.docx` ที่สร้างขึ้น และคุณควรเห็นแผนภูมิวงกลมที่จัดรูปแบบอย่างดีพร้อมส่วนแรกที่ explode, เส้นนำ, และ legend ที่มองเห็นได้

![ตัวอย่างแผนภูมิวงกลมที่แสดงส่วนที่ explode และ legend](pie-chart-example.png){: .center-image alt="ตัวอย่างการสร้างแผนภูมิวงกลมที่มีส่วนที่ explode, เส้นนำ, และ legend"}

### ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิดไฟล์ Word แผนภูมิจะมีลักษณะประมาณนี้:

- แผนภูมิวงกลมขนาด 400 × 300 pt.
- ส่วนแรกถูกย้ายออกโดย 10 pt.
- เส้นนำบางเส้นเชื่อมส่วนที่ explode กับป้ายกำกับ.
- legend ใต้แผนภูมิแสดงชื่อแต่ละ series.

หากคุณไม่เห็นเส้นนำ ตรวจสอบให้แน่ใจว่าได้เรียก `setLeaderLines(true)` *หลังจาก* การตั้งค่า explosion—ลำดับสำคัญ

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **ไม่มี legend ปรากฏ** | `setShowLegend(true)` ถูกละเว้นหรือเรียกบนอ็อบเจ็กต์ chart ที่ผิด | ตรวจสอบให้เรียก `chart.setShowLegend(true)` **หลังจาก** ดึง `Chart` จาก shape |
| **ไม่มี leader line** | ส่วนไม่ได้ถูก explode หรือประเภทแผนภูมิไม่รองรับ leader lines | เฉพาะ `ChartType.PIE` (หรือ `PIE_3D`) ที่รองรับ leader lines. เรียก `setExplosion` ก่อน แล้วจึง `setLeaderLines(true)` |
| **ส่วนไม่เคลื่อนที่** | ค่าการ explosion ต่ำเกินไป (0‑2 pt) | เพิ่มค่าตัวเลข เช่น `setExplosion(10)` หรือสูงกว่า เพื่อให้เอฟเฟกต์เด่นชัด |
| **แผนภูมิบิดเบี้ยว** | การใช้ขนาดที่ไม่เป็นสี่เหลี่ยมจัตุรัส (ความกว้าง ≠ ความสูง) ทำให้วงกลมบีบอัด | ให้ความกว้างและความสูงเท่ากันหรือใกล้เคียง; 400 × 300 ทำงานได้แต่ 400 × 400 ให้วงกลมสมบูรณ์ |

## การปรับแต่งขั้นสูง (ทางเลือก)

หากคุณต้องการไปไกลกว่าพื้นฐาน ให้พิจารณา:

- **สีกำหนดเอง**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **ป้ายข้อมูล**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **เอฟเฟกต์ 3‑D**: Replace `ChartType.PIE` with `ChartType.PIE_3D`.

ตัวเลือกเหล่านี้ทำให้คุณปรับแต่งภาพให้ตรงกับแนวทางการสร้างแบรนด์ขององค์กร

## สรุป – สิ่งที่เราทำสำเร็จ

เราเริ่มด้วยเอกสาร Word ว่าง, **สร้างแผนภูมิวงกลม**, **explode ส่วนแรก**, **เพิ่ม leader lines**, และ **แสดง chart legend**. ทั้งหมดนี้อยู่ในเมธอด `main` สั้น ๆ ทำให้ง่ายต่อการนำไปใช้ใน pipeline รายงานที่ใหญ่ขึ้น

## ขั้นตอนต่อไป

- **เพิ่ม series เพิ่มเติม**: เติมข้อมูลแผนภูมิด้วยข้อมูลจริงจากฐานข้อมูลหรือ CSV.
- **ส่งออกเป็น PDF**: ใช้ `doc.save("output.pdf", SaveFormat.PDF);` เพื่อสร้างเวอร์ชัน PDF.
- **รวมกับรูปทรงอื่น**: แทรกตาราง, รูปภาพ, หรือแผนภูมิเพิ่มเติมสำหรับรายงานเต็มรูปแบบ.

หากคุณสนใจประเภทแผนภูมิอื่น—คอลัมน์, แถบ, เส้น—เพียงเปลี่ยน `ChartType.PIE` เป็น enum ที่เหมาะสมและทำตามขั้นตอนการจัดรูปแบบเดียวกัน

---

*สนุกกับการทำแผนภูมิ!* อย่าลังเลที่จะคอมเมนต์หากมีสิ่งที่ไม่ทำงานตามคาด หรือแชร์วิธีที่คุณปรับตำแหน่ง legend ของคุณ ความคิดเห็นของคุณช่วยให้เราทุกคนสร้างเอกสารอัตโนมัติที่ดียิ่งขึ้น

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโครงการของคุณ

- [วิธีสร้างแผนภูมิคอลัมน์โดยใช้ Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [วิธีสร้างเอกสาร PDF ด้วย Aspose.Words for Java | Document Processing API](/words/english/java/)
- [วิธีเพิ่มลายน้ำให้เอกสารโดยใช้ Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}