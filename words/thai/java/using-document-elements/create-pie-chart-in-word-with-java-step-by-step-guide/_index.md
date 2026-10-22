---
category: general
date: 2026-08-14
description: สร้างแผนภูมิวงกลมใน Word ด้วย Java โดยใช้ Aspose.Words เรียนรู้วิธีเพิ่มข้อมูลซีรีส์ลงในแผนภูมิและหมุนชิ้นส่วนของแผนภูมิวงกลมด้วยเพียงไม่กี่บรรทัด.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: th
lastmod: 2026-08-14
og_description: สร้างแผนภูมิวงกลมใน Word ด้วย Java โดยใช้ Aspose.Words บทเรียนนี้แสดงวิธีเพิ่มข้อมูลชุดข้อมูลลงในแผนภูมิและหมุนชิ้นส่วนของแผนภูมิวงกลมอย่างรวดเร็ว.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: สร้างแผนภูมิวงกลมใน Word ด้วย Java – คู่มือการเขียนโค้ดครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: สร้างแผนภูมิวงกลมใน Word ด้วย Java – คู่มือขั้นตอนโดยละเอียด
url: /th/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างแผนภูมิวงกลมใน Word ด้วย Java – คู่มือขั้นตอนโดยละเอียด

หากคุณต้องการ **create pie chart in Word** อย่างอัตโนมัติ คู่มือนี้จะแสดงให้คุณเห็นขั้นตอนทั้งหมดด้วย Java และ Aspose.Words คุณจะได้เรียนรู้กระบวนการทำงานครบถ้วน ตั้งแต่การแทรกแผนภูมิ การเพิ่มจุดข้อมูล ไปจนถึงการหมุนชิ้นแรกของแผนภูมิ

การสร้างแผนภูมิโดยตรงในไฟล์ `.docx` จะลบขั้นตอนคัดลอก‑วางด้วยมือออกและทำให้คุณสามารถอัตโนมัติรายงาน ใบแจ้งหนี้ หรือแดชบอร์ดได้ ในระหว่างนี้เราจะครอบคลุม **how to add series data to chart** และ **rotate pie chart slice** เพื่อเน้นภาพให้ดีขึ้น

## สร้างแผนภูมิวงกลมใน Word – ภาพรวม

Aspose.Words for Java ให้ API `DocumentBuilder` ที่ใช้งานง่ายซึ่งสามารถแทรกอ็อบเจกต์แผนภูมิลงในเอกสาร Word ประเภทแผนภูมิที่คุณเลือกจะกำหนดรูปแบบเริ่มต้น และคุณสามารถปรับแต่ง series, colors, angles และแม้กระทั่งสลับเป็นรูปทรง doughnut ด้วยการเรียกเมธอดเดียว

### ทำไมต้องใช้ Aspose.Words?

* **No Microsoft Office required** – ไลบรารีทำงานบนเซิร์ฟเวอร์หรือสภาพแวดล้อม CI ใดก็ได้  
* **Full .docx fidelity** – แผนภูมิที่สร้างขึ้นดูเหมือนกับที่สร้างด้วยมือใน Word อย่างเต็มที่  
* **Single‑file dependency** – เพียงเพิ่มไฟล์ JAR แล้วคุณก็พร้อมใช้งาน  

## วิธีเพิ่ม series data ไปยังแผนภูมิ

แผนภูมิที่ไม่มีข้อมูลเป็นเพียงตัวแทน `Chart` object เปิดเผยคอลเลกชัน `Series`; แต่ละ series จะเก็บรายการค่าตัวเลขที่แมปกับชิ้น (สำหรับ pie) หรือจุด (สำหรับ line) การเพิ่มข้อมูลทำได้อย่างตรงไปตรงมา:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**สิ่งที่โค้ดทำ:**  
* `chart.getSeries()` คืนค่า `List<ChartSeries>`.  
* `get(0)` เลือก series แรกเนื่องจากแผนภูมิวงกลมโดยกำหนดมีเพียง series เดียว  
* `add(double)` เพิ่มจุดข้อมูล ค่าจะถูกแปลงเป็นเปอร์เซ็นต์โดยอัตโนมัติที่รวมกันเป็น 100 % เมื่อแผนภูมิแสดงผล  

> **Pro tip:** หากแหล่งข้อมูลของคุณมีมากกว่าสามประเภท ให้เพิ่มค่าอย่างต่อเนื่องในรูปแบบเดียวกัน Aspose.Words จะสร้างชิ้นเพิ่มเติมโดยอัตโนมัติ  

## หมุนชิ้นของแผนภูมิวงกลม

บางครั้งคุณอาจต้องการให้ชิ้นเฉพาะเริ่มที่มุมที่กำหนดเพื่อให้ส่วนที่สำคัญที่สุดหันไปทางผู้ชม เมธอด `setFirstSliceAngle(double)` จะหมุนแผนภูมิทั้งหมด ทำให้ตำแหน่งเริ่มต้นของชิ้นแรกเปลี่ยนไป:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

มุมวัดเป็นองศาในทิศทางตามเข็มนาฬิกาจากแกนแนวตั้ง การตั้งค่าเป็น `0` (ค่าเริ่มต้น) จะทำให้ชิ้นแรกอยู่ที่ด้านบน ปรับค่าตามต้องการเพื่อเน้นชิ้นหรือให้สอดคล้องกับแนวทางการออกแบบ  

> **Common question:** *การหมุนมีผลต่อลำดับข้อมูลหรือไม่?*  
> ไม่. ลำดับข้อมูลยังคงเดิม; มีเพียงตำแหน่งเริ่มต้นของภาพที่เปลี่ยนเท่านั้น  

## ตัวอย่าง Java เต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่สมบูรณ์พร้อมรันที่สร้างเอกสาร Word พร้อมแผนภูมิวงกลม เพิ่ม series data, หมุนชิ้น, และบันทึกไฟล์ รายการ import ที่จำเป็นทั้งหมดถูกระบุไว้เพื่อให้คุณคัดลอกโค้ดไปวางใน IDE ใดก็ได้

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ชื่อ **PieChart.docx** ปรากฏในโฟลเดอร์ `output`.  
* การเปิดไฟล์ใน Microsoft Word จะแสดงแผนภูมิวงกลมสีสันสดใสที่มีสามชิ้น (40 %, 30 %, 30 %).  
* แผนภูมิถูกหมุน 45° ตามเข็มนาฬิกา ทำให้ชิ้นแรกเริ่มเล็กน้อยทางขวาของแกนแนวตั้ง  

## ข้อผิดพลาดทั่วไปและแนวทางปฏิบัติที่ดีที่สุด

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|--------|
| **Chart appears blank** | เอกสารถูกบันทึกก่อนที่แผนภูมิจะเรนเดอร์เสร็จสมบูรณ์. | เรียก `doc.save()` **หลังจาก** การแก้ไขแผนภูมิทั้งหมด. |
| **Slice values don’t sum to 100 %** | การเพิ่มตัวเลขดิบที่ไม่เป็นเปอร์เซ็นต์อาจทำให้การสเกลไม่คาดคิด. | ให้ค่าที่เป็นส่วนของทั้งหมดอย่างมีเหตุผล หรือให้ Aspose.Words คำนวณเปอร์เซ็นต์โดยอัตโนมัติ. |
| **Rotation has no effect** | การใช้ `ChartType.DOUGHNUT` โดยไม่ได้ตั้งค่า `holeSize` อาจทำให้ผลของการหมุนไม่แสดง. | เก็บแผนภูมิเป็น `PIE` หรือปรับ `holeSize` หลังจากตั้งค่ามุม. |
| **File path errors** | เส้นทางแบบ relative อาจแตกต่างกันระหว่าง Windows และ Linux. | ใช้ `Paths.get("output", "PieChart.docx").toString()` หรือเส้นทางแบบ absolute สำหรับโค้ดการผลิต. |

### เคล็ดลับสำหรับการใช้งานใน production

* **Reuse the `DocumentBuilder`** – คุณสามารถแทรกแผนภูมิหลายรายการในเอกสารเดียวกันโดยเรียก `insertChart` ซ้ำหลายครั้ง.  
* **Styling** – ใช้ `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` เพื่อแสดงเปอร์เซ็นต์โดยตรงบนแผนภูมิ.  
* **Performance** – สร้างแผนภูมิครั้งเดียวแล้วทำสำเนา (`chart.deepClone()`) หากต้องการแผนภูมิที่เหมือนกันในหลายตำแหน่ง.  

## หมุนชิ้นของแผนภูมิวงกลม – สถานการณ์ขั้นสูง

* **Dynamic angle** – คำนวณมุมตามข้อมูล (เช่น ทำให้ชิ้นที่ใหญ่ที่สุดเริ่มที่ด้านบน).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Multiple series** – แม้ว่าแผนภูมิวงกลมโดยทั่วไปจะมี series เดียว, Aspose.Words อนุญาตให้เพิ่มมากกว่าสำหรับ pie แบบ stacked. การหมุนยังคงใช้กับ series แรกเท่านั้น.  

## สรุป

ตอนนี้คุณรู้วิธี **create pie chart in Word** ด้วย Java, วิธี **add series data to chart**, และวิธี **rotate pie chart slice** เพื่อเน้นภาพ ตัวอย่างเต็มแสดงกระบวนการทำงานทั้งหมด—from การเริ่มต้นเอกสารจนถึงการบันทึกไฟล์ `.docx` สุดท้าย—เพื่อให้คุณสามารถรวมการสร้างแผนภูมิลงใน pipeline รายงานอัตโนมัติใดก็ได้.  

### ต่อไปคืออะไร?

* สำรวจประเภทแผนภูมิอื่น (`ChartType.BAR`, `ChartType.LINE`) เพื่อขยายเครื่องมืออัตโนมัติของคุณ.  
* ผสานการสร้างแผนภูมิกับ **mail merge** เพื่อสร้างรายงานส่วนบุคคลสำหรับผู้รับแต่ละคน.  
* ศึกษา **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) เพื่อให้สอดคล้องกับแบรนด์ขององค์กรคุณ.  

อย่าลังเลที่จะทดลองกับชุดข้อมูล มุม และสไตล์แผนภูมิที่แตกต่างกัน. ขอให้เขียนโค้ดอย่างสนุก!  

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}