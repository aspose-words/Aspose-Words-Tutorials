---
category: general
date: 2026-10-07
description: เรียนรู้วิธีสร้างแผนภูมิวงกลมใน Word, เพิ่มชุดข้อมูล, และบันทึกแผนภูมิเป็น
  PNG ด้วย Java. ปฏิบัติตามคู่มือขั้นตอนต่อขั้นตอนเพื่อผลลัพธ์ที่รวดเร็ว.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: th
lastmod: 2026-10-07
og_description: 'สร้างแผนภูมิวงกลมใน Word อย่างรวดเร็ว: บทเรียนนี้แสดงวิธีเพิ่มชุดข้อมูล,
  สร้างแผนภูมิ, และบันทึกแผนภูมิ Word เป็นภาพ (PNG). ทำตามตัวอย่างโค้ดเต็ม.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: สร้างแผนภูมิวงกลมใน Word และส่งออกเป็น PNG – คู่มือ
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: วิธีสร้างแผนภูมิวงกลมใน Word และบันทึกเป็น PNG
url: /th/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างแผนภูมิวงกลมใน Word และบันทึกเป็น PNG

หากคุณต้องการ **สร้างแผนภูมิวงกลม** ภายในไฟล์ Microsoft Word คำแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนทั้งหมดด้วย Java คุณยังจะได้เรียนรู้วิธี **เพิ่มชุดข้อมูล** ลงในแผนภูมิและ **บันทึกแผนภูมิเป็น PNG** เพื่อให้ภาพสามารถนำไปใช้ซ้ำนอก Word ได้

การสร้างแผนภูมิโดยตรงในเอกสารช่วยให้คุณไม่ต้องส่งออกข้อมูลไปยังเครื่องมือกราฟิกแยกต่างหาก เมื่อจบบทเรียนนี้คุณจะมีไฟล์ Word ที่ทำงานได้เต็มรูปแบบซึ่งประกอบด้วยแผนภูมิวงกลมและไฟล์ PNG ที่สอดคล้องกันบนดิสก์

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* Java 17 หรือใหม่กว่า
* **GroupDocs.Viewer for Java** (หรือไลบรารีที่เข้ากันได้ซึ่งให้คลาส `Document`, `Chart`, `ChartType` และ `ImageSaveOptions`)
* โครงการ Maven หรือ Gradle ที่คุณสามารถเพิ่มการอ้างอิงไลบรารีได้
* ไฟล์ Word เข้า (`input.docx`) ที่อยู่ในโฟลเดอร์ที่คุณสามารถอ้างอิงจากโค้ดได้

หากคุณใช้ Maven ให้เพิ่มการอ้างอิง (แทนที่ `VERSION` ด้วยเวอร์ชันล่าสุด):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## วิธีสร้างแผนภูมิวงกลมใน Word

หัวใจของวิธีแก้ปัญหานี้ประกอบด้วยสามขั้นตอนหลัก:

1. โหลดไฟล์ `.docx` ต้นฉบับ
2. **เพิ่มชุดข้อมูล** ลงในอ็อบเจกต์ `Chart` ใหม่ประเภท `PIE`
3. **บันทึกแผนภูมิเป็น PNG** เพื่อให้ได้ไฟล์ภาพที่อยู่ข้างไฟล์ Word

แต่ละขั้นตอนจะอธิบายรายละเอียดต่อไปนี้ พร้อมด้วยโค้ด Java ที่คุณต้องใช้

### ขั้นตอน 1: โหลดเอกสารต้นฉบับ

คุณต้องเปิดไฟล์ Word ที่จะเป็นที่เก็บแผนภูมิ คลาส `Document` จะอ่านเนื้อหา `.docx` เข้าไปในหน่วยความจำ

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*เหตุผล*: การโหลดเอกสารจะสร้างโมเดลที่สามารถแก้ไขได้ การดำเนินการกับแผนภูมิทั้งหมดต่อจากนี้จะทำกับตัวแทนในหน่วยความจำนี้ ซึ่งคุณจะบันทึกกลับไปยังดิสก์ในขั้นตอนต่อไป

### ขั้นตอน 2: เพิ่มชุดข้อมูลลงในแผนภูมิ

การสร้าง **แผนภูมิวงกลม** เริ่มจากการสร้างอินสแตนซ์ `Chart` ตัวสร้างรับพารามิเตอร์เป็น `Document` พาเรนท์และประเภทแผนภูมิ (`ChartType.PIE`) หลังจากที่อ็อบเจกต์แผนภูมิถูกสร้างขึ้นแล้ว คุณจะเติมค่าตัวเลขและป้ายกำกับ (ถ้ามี) ลงไป

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*เหตุผล*: เมธอด `add` **เพิ่มชุดข้อมูล** ลงในแผนภูมิ แต่ละค่าใน `values` จะกลายเป็นส่วนของวงกลม ส่วน `categories` จะเป็นป้ายกำกับในตารางอธิบาย คุณสามารถใส่จำนวนจุดได้ตามต้องการ ไลบรารีจะคำนวณมุมของแต่ละส่วนโดยอัตโนมัติ

### ขั้นตอน 3: บันทึกแผนภูมิเป็น PNG

เมื่อแผนภูมิเป็นส่วนหนึ่งของเอกสารแล้ว คุณสามารถส่งออกภาพที่แสดงผลได้ เมธอด `save` ของอ็อบเจกต์แผนภูมิพื้นฐานจะเขียนไฟล์ PNG ไปยังระบบไฟล์

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*เหตุผล*: การบันทึกแผนภูมิเป็น PNG จะให้ภาพเรสเตอร์ที่สามารถฝังในหน้าเว็บ อีเมล หรือรายงานได้โดยไม่ต้องอ้างอิงไฟล์ Word ดั้งเดิม `ImageSaveOptions` ช่วยให้คุณควบคุมรูปแบบ ความละเอียด และการตั้งค่าอื่น ๆ ของการส่งออก

## สร้างแผนภูมิวงกลมใน Word – ปรับแต่งรูปลักษณ์

นอกเหนือจากขั้นตอนพื้นฐาน คุณอาจต้องการปรับสี ชื่อเรื่อง หรือป้ายข้อมูล จุดสำคัญคือหลายไลบรารีมีอ็อบเจกต์ `ChartOptions` หรือคล้ายกัน ตัวอย่างสั้น ๆ ด้านล่างเพิ่มชื่อเรื่องและเปลี่ยนสีของส่วนต่าง ๆ:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

การปรับแต่งเหล่านี้เป็นทางเลือก แต่ช่วยแสดงให้เห็นว่าคุณสามารถ **สร้างแผนภูมิวงกลมใน Word** ให้สอดคล้องกับแบรนด์ของคุณได้อย่างไร

## บันทึกแผนภูมิ Word เป็นภาพ – วิธีทางเลือก

หากคุณต้องการเพียงภาพเท่านั้นและไม่ต้องการแผนภูมิอยู่ในเอกสาร คุณสามารถข้ามขั้นตอนการแทรกรูปร่างแผนภูมิลงในไฟล์ Word แล้วเรียกเมธอด `save` ทันทีหลังสร้างแผนภูมิ โค้ดยังคงเหมือนเดิม เพียงแค่ละเว้นขั้นตอนที่เพิ่มแผนภูมิลงในเนื้อหาเอกสาร

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

เทคนิคนี้มีประโยชน์เมื่อคุณต้องสร้างแผนภูมิจำนวนมากในกระบวนการแบบแบตช์และต้องการผลลัพธ์เป็น PNG เท่านั้น

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

คัดลอกคลาสต่อไปนี้ไปยังโปรเจกต์ของคุณ ปรับเส้นทางไฟล์ให้ตรงกับสภาพแวดล้อมของคุณ แล้วรัน โปรแกรมจะทำการ:

1. โหลด `input.docx`
2. **สร้างแผนภูมิวงกลม**, **เพิ่มชุดข้อมูล**, และฝังลงในเอกสาร
3. **บันทึกแผนภูมิเป็น PNG** (`radial.png`)
4. บันทึกไฟล์ Word ที่แก้ไขแล้วเป็น `output.docx`



## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบต่าง ๆ ในโครงการของคุณเอง

- [วิธีสร้างแผนภูมิคอลัมน์โดยใช้ Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [สร้างแผนภูมิกระจายใน Word โดยใช้ Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [แทรกแผนภูมิคอลัมน์ใน Word โดยใช้ Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}