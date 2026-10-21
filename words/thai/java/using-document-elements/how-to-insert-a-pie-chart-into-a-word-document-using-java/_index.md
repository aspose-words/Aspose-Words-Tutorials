---
category: general
date: 2026-09-27
description: เรียนรู้วิธีแทรกแผนภูมิวงกลมลงในเอกสาร Word ด้วย Java, สร้างแผนภูมิวงกลมใน
  Word, และแสดงเปอร์เซ็นต์บนแผนภูมิวงกลมเพื่อให้เข้าใจข้อมูลได้อย่างชัดเจน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: th
lastmod: 2026-09-27
og_description: วิธีแทรกแผนภูมิวงกลมลงในเอกสาร Word ด้วย Java คู่มือนี้จะแสดงวิธีสร้างแผนภูมิวงกลมใน
  Word แสดงเปอร์เซ็นต์บนแผนภูมิวงกลม และเพิ่มเส้นนำ.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: วิธีแทรกแผนภูมิวงกลมลงในเอกสาร Word ด้วย Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: วิธีแทรกแผนภูมิวงกลมลงในเอกสาร Word ด้วย Java
url: /th/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทรกแผนภูมิวงกลมลงในเอกสาร Word ด้วย Java

หากคุณต้องการ **how to insert pie chart** ลงในไฟล์ Word คำแนะนำนี้จะพาคุณผ่านกระบวนการทั้งหมด คุณจะได้เห็นวิธี **create pie chart in Word**, แสดงเปอร์เซ็นต์บนแต่ละชิ้น และเพิ่มเส้นนำสำหรับรูปลักษณ์ที่เรียบหรู.

การทำอัตโนมัติของ Word มักรู้สึกหนักหน่วง แต่ด้วย Aspose.Words for Java คุณสามารถสร้างเอกสารที่จัดรูปแบบเต็มรูปแบบโดยอัตโนมัติได้ จากตอนท้ายของบทแนะนำนี้คุณจะมีโค้ด Java ที่สามารถรันได้ซึ่งสร้างเอกสาร Word ที่มีแผนภูมิวงกลมที่จัดสไตล์แล้ว.

## ข้อกำหนดเบื้องต้น

- Java 17 หรือใหม่กว่า ที่ติดตั้งแล้ว
- Maven หรือ Gradle เพื่อจัดการ dependencies
- Aspose.Words for Java (เวอร์ชัน 23.11 หรือใหม่กว่า) ที่เพิ่มในโปรเจกต์ของคุณ
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java

คุณไม่จำเป็นต้องมีประสบการณ์ก่อนหน้ากับ chart APIs; ขั้นตอนด้านล่างครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโปรเจกต์จนถึงผลลัพธ์สุดท้าย.

## ขั้นตอนที่ 1: ตั้งค่า Maven dependency

เพิ่มไลบรารี Aspose.Words ไปยัง `pom.xml` ของคุณ dependency เพียงรายการเดียวนี้จะทำให้คุณเข้าถึง `Document`, `DocumentBuilder` และคลาส chart.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

หากคุณใช้ Gradle, รูปแบบที่เทียบเท่าคือ:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** ใช้เวอร์ชัน stable ล่าสุดเพื่อรับประโยชน์จากการแก้บั๊กและคุณลักษณะ chart ใหม่.

## ขั้นตอนที่ 2: สร้างเอกสารใหม่และ builder

`Document` object แทนไฟล์ Word, ส่วน `DocumentBuilder` ช่วยให้คุณแทรกเนื้อหา นี่เป็นพื้นฐานสำหรับ **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ตอนนี้ builder พร้อมที่จะวางอ็อบเจกต์ได้ทุกที่ในเอกสาร.

## ขั้นตอนที่ 3: แทรกแผนภูมิวงกลม

Aspose.Words รองรับหลายประเภทของ chart; เราเลือก `ChartType.PIE`. ขนาดระบุเป็น points (1 point = 1/72 นิ้ว).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

ในขั้นตอนนี้ chart มี series ของข้อมูลเริ่มต้นพร้อมค่าตัวแทน คุณสามารถแทนที่ค่าดังกล่าวในภายหลังได้หากต้องการ.

## ขั้นตอนที่ 4: เข้าถึง series ของ chart

แผนภูมิวงกลมมี series เดียวที่เก็บค่าชิ้นส่วนของแต่ละ slice. ดึงมันออกมาเพื่อทำการจัดรูปแบบ.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## ขั้นตอนที่ 5: ทำให้ slice แรก explode

การทำให้ slice explode จะดึงความสนใจไปยังจุดข้อมูลเฉพาะ นี่เป็นสัญญาณภาพที่พบบ่อยเมื่อคุณต้องการเน้นเมตริกสำคัญ.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## ขั้นตอนที่ 6: แสดงเปอร์เซ็นต์บนแต่ละ slice

การแสดงเปอร์เซ็นต์โดยตรงบน chart ช่วยเพิ่มการเข้าใจข้อมูล นี่ตอบสนองความต้องการ **show percentages on pie chart**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## ขั้นตอนที่ 7: เพิ่มเส้นนำเพื่อทำให้ป้ายชื่อชัดเจนขึ้น

เส้นนำเชื่อมป้ายชื่อของ slice กับส่วนที่สอดคล้องกัน, ขจัดความกำกวม นี่ตอบสนอง **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## ขั้นตอนที่ 8: บันทึกเอกสาร

สุดท้าย, เขียนเอกสารลงดิสก์ คุณสามารถเลือกโฟลเดอร์ใดก็ได้ที่คุณมีสิทธิ์เขียน.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

การรันโปรแกรมจะสร้าง `output/PieFormatted.docx`. เปิดไฟล์ใน Microsoft Word, แล้วคุณจะเห็นแผนภูมิวงกลมที่:

- Slice แรกถูก explode.
- แต่ละ slice แสดงค่าร้อยละของมัน.
- เส้นนำชี้จากเปอร์เซ็นต์ไปยัง slice ที่สอดคล้องกัน.

### ผลลัพธ์ที่คาดหวัง

![แผนภูมิวงกลมที่จัดรูปแบบใน Word](/images/pie-formatted.png){: .center-image alt="แผนภูมิวงกลมที่จัดรูปแบบแล้วแทรกลงในเอกสาร Word"}

ภาพหน้าจอ (ข้อความ alt ใช้คีย์เวิร์ดหลัก) แสดงลักษณะสุดท้าย: แผนภูมิวงกลมที่สะอาดและขับเคลื่อนด้วยข้อมูล พร้อมสำหรับรายงาน, ข้อเสนอ, หรือแดชบอร์ด.

## ความแปรผันทั่วไปและกรณีขอบ

### การเปลี่ยนค่าของ slice

หากคุณต้องการข้อมูลกำหนดเอง, ให้แทนที่ค่าของ series เริ่มต้นด้วย:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### หลาย series (donut chart)

แม้ว่า pie chart ธรรมดาจะมีหนึ่ง series, Aspose.Words ยังรองรับ donut chart ที่มีหลาย series. เปลี่ยน `ChartType.PIE` เป็น `ChartType.DONUT` แล้วทำซ้ำขั้นตอนการกำหนดค่า series.

### การส่งออกเป็น PDF

หากกระบวนการต่อไปของคุณต้องการ PDF, ให้เรียก `doc.save("output/PieFormatted.pdf");` หลังจากสร้าง chart แล้ว การจัดวางภาพยังคงเหมือนเดิม.

## รายการซอร์สโค้ดเต็ม

ด้านล่างเป็นไฟล์ Java ที่สมบูรณ์และเป็นอิสระที่คุณสามารถคัดลอกและวางลงใน IDE ของคุณได้.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

คอมไพล์และรันโปรแกรมด้วย `mvn compile exec:java -Dexec.mainClass=PieChartExample` (หรือคำสั่ง Gradle ที่เทียบเท่า). ไฟล์ Word ที่สร้างจะมีแผนภูมิวงกลมที่จัดรูปแบบเต็ม.

## สรุป

ตอนนี้คุณรู้แล้วว่า **how to insert pie chart** ลงในเอกสาร Word ด้วย Java, วิธี **create pie chart in Word**, วิธี **show percentages on pie chart**, และวิธี **add chart to word document** พร้อมเส้นนำ ตัวอย่างเต็มแสดงแต่ละขั้นตอน, อธิบายเหตุผลที่โค้ดเขียนเช่นนั้น, และให้เคล็ดลับสำหรับการปรับแต่ง.

ต่อไปคุณอาจสำรวจ:

- เพิ่มป้ายข้อมูลด้วยฟอนต์กำหนดเอง (**show percentages on pie chart** variations)
- รวมหลาย chart ไว้ในเอกสารเดียว (**add chart to word document** use case)
- ทำอัตโนมัติการสร้างรายงานด้วยตารางและ chart ร่วมกัน

อย่าลังเลที่จะทดลองกับสี, การจัดลำดับ slice, หรือการส่งออกเป็น PDF. ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ.

- [วิธีสร้าง column chart ด้วย Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [ซ่อนแกน Chart ในเอกสาร Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [สร้าง Line Chart ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}