---
category: general
date: 2026-10-10
description: เรียนรู้วิธีการหมุนแผนภูมิในไฟล์ Word และแก้ไขแผนภูมิใน Word เพื่อเปลี่ยนขนาดแผนภูมิโดนัทพร้อมตัวอย่าง
  Java ที่สมบูรณ์.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: th
lastmod: 2026-10-10
og_description: วิธีหมุนแผนภูมิในไฟล์ Word และแก้ไขแผนภูมิใน Word เพื่อเปลี่ยนขนาดแผนภูมิโดนัทโดยใช้
  Aspose.Words for Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: วิธีหมุนแผนภูมิในเอกสาร Word – คู่มือ Java ทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: วิธีหมุนแผนภูมิในเอกสาร Word ด้วย Aspose.Words
url: /th/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการหมุนแผนภูมิในเอกสาร Word ด้วย Aspose.Words

หากคุณต้องการ **how to rotate chart** ภายในไฟล์ Microsoft Word คำแนะนำนี้จะแสดงขั้นตอนที่แน่นอนให้คุณ คุณจะได้เรียนรู้วิธี **modify chart in Word** เพื่อ **change doughnut chart size** โดยไม่ต้องออกจากโค้ด Java ของคุณ

การทำงานอัตโนมัติของ Word มักรู้สึกเหมือนเป็นชุดของการเรียก API ที่ไม่ต่อเนื่องกัน แต่ด้วย Aspose.Words คุณสามารถจัดการแผนภูมิได้เช่นเดียวกับโหนดเอกสารอื่น ๆ เมื่อจบบทเรียนนี้ คุณจะมีโปรแกรมที่สามารถรันได้ซึ่งโหลดไฟล์ `.docx` ที่มีอยู่แล้ว, หมุนแผนภูมิ doughnut ไป 45°, ลดขนาดรูเป็น 50 % ของรัศมี, และบันทึกผลลัพธ์เป็นไฟล์ใหม่

## ข้อกำหนดเบื้องต้น

* Java 17 หรือใหม่กว่าติดตั้งแล้ว.
* Maven (หรือ Gradle) เพื่อจัดการ dependencies.
* เอกสาร Word อินพุต (`input.docx`) ที่มีแผนภูมิ doughnut อยู่แล้ว.
* ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (หรือใช้โหมดประเมินผล).

## ขั้นตอนที่ 1: ตั้งค่าโครงการ Maven

สร้างโครงการ Maven ใหม่หรือเพิ่ม dependency ต่อไปนี้ลงใน `pom.xml` ของคุณที่มีอยู่แล้ว:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

การรัน `mvn clean install` จะดาวน์โหลดไลบรารีและทำให้คลาสพร้อมใช้งานใน classpath ของคุณ.

## ขั้นตอนที่ 2: โหลดเอกสาร Word ที่มีแผนภูมิ

การดำเนินการแรกคือการเปิดเอกสารที่มีอยู่แล้ว คลาส `Document` แทนไฟล์ทั้งหมด.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

การโหลดไฟล์ **ไม่** ทำการแก้ไขไฟล์; มันเพียงสร้างการแสดงผลในหน่วยความจำที่คุณสามารถสอบถามและแก้ไขได้.

## ขั้นตอนที่ 3: สร้าง DocumentBuilder เพื่อการนำทาง

`DocumentBuilder` ให้ API แบบเคอร์เซอร์เพื่อเดินผ่านโครงสร้างต้นไม้ของเอกสาร เราจะใช้มันเพื่อค้นหา shape ของแผนภูมิแรก.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder จะเริ่มที่จุดเริ่มต้นของเอกสาร แต่คุณสามารถย้ายไปยังโหนดใดก็ได้ในภายหลังหากต้องการ.

## ขั้นตอนที่ 4: ดึง shape ของแผนภูมิแรก

แผนภูมิจะถูกจัดเก็บเป็นโหนด `Shape` โดยการกรองโหนดลูกที่เป็นประเภท `NodeType.SHAPE` เราสามารถดึงอ็อบเจ็กต์แผนภูมิออกมาได้.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

หากเอกสารมีแผนภูมิหลายรายการ คุณสามารถวนลูป `getChildNodes` และตรวจสอบแต่ละ `Shape` ด้วย `hasChart()` ก่อนทำการแคสต์.

## ขั้นตอนที่ 5: หมุนแผนภูมิ (how to rotate chart)

แผนภูมิ doughnut คือแผนภูมิพายที่มีรู การหมุนมันจะเปลี่ยนมุมเริ่มต้นของชิ้นแรก.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

เมธอด `setStartAngle` คาดหวังค่า double ที่แสดงเป็นองศา ค่าเป็นบวกจะหมุนตามเข็มนาฬิกา ส่วนค่าลบจะหมุนทวนเข็มนาฬิกา.

## ขั้นตอนที่ 6: เปลี่ยนขนาดรูของ doughnut (change doughnut chart size)

ขนาดของรูจะแสดงเป็นส่วนของรัศมีแผนภูมิ ค่า `0.5` หมายความว่ารูครอบคลุม 50 % ของรัศมีทั้งหมด.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**เคล็ดลับ:** ช่วงค่าที่ถูกต้องคือ `0.0` (ไม่มีรู, คือพายปกติ) ถึง `0.9` (วงแหวนบางมาก) ค่าที่อยู่นอกช่วงนี้จะทำให้เกิด `IllegalArgumentException`.

## ขั้นตอนที่ 7: บันทึกเอกสารที่แก้ไขแล้ว

สุดท้าย ให้เขียนการเปลี่ยนแปลงกลับไปยังดิสก์.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

เมื่อคุณเปิด `DoughnutFormatted.docx` ใน Microsoft Word คุณจะเห็นแผนภูมิ doughnut ถูกหมุน 45° และรูลดลงเหลือครึ่งหนึ่งของขนาดเดิม.

## ตัวอย่างเต็มที่สามารถรันได้

เมื่อรวมส่วนต่าง ๆ เข้าด้วยกัน นี่คือโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงใน IDE ของคุณ:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

การรันโปรแกรมจะแสดงผล:

```
Chart rotated and doughnut size changed successfully.
```

การเปิด `DoughnutFormatted.docx` แสดงแผนภูมิ doughnut ที่ชิ้นแรกเริ่มที่ตำแหน่ง 45° และรัศมีภายในครอบคลุมครึ่งหนึ่งของรัศมีภายนอก.

## ความแตกต่างทั่วไปและกรณีขอบ

| สถานการณ์ | สิ่งที่ต้องปรับ | เหตุผลที่สำคัญ |
|-----------|----------------|----------------|
| **หลายแผนภูมิ** | วนลูป `getChildNodes(NodeType.SHAPE, true)` และตรวจสอบ `shape.hasChart()` สำหรับแต่ละรายการ | รับรองว่าคุณแก้ไขแผนภูมิที่ต้องการ ไม่ใช่แผนภูมิแรก |
| **แผนภูมิแท่งหรือเส้น** | `setStartAngle` ไม่ใช้; ใช้ `chart.getSeries().get(0).setFillFormat(...)` สำหรับการปรับแต่งภาพอื่น | ไม่ใช่ทุกประเภทแผนภูมิที่รองรับการหมุน; แผนภูมิ doughnut/pie เป็นประเภทเดียวที่มีมุมเริ่มต้น |
| **แผนภูมิที่ไม่มีรู doughnut** | ข้าม `setDoughnutHoleSize` หรือแปลงประเภทแผนภูมิเป็น doughnut ก่อนโดยใช้ `chart.setChartType(ChartType.DONUT)` | การเปลี่ยนขนาดรูบนแผนภูมิที่ไม่ใช่ doughnut จะทำให้เกิดข้อยกเว้น |
| **เอกสารขนาดใหญ่** | ใช้ `DocumentBuilder.moveToDocumentStart()` และ `builder.moveToNode(chartShape)` เพื่อการนำทางที่เจาะจง | ปรับปรุงประสิทธิภาพโดยหลีกเลี่ยงการเดินทางเต็มของโหนดที่ไม่เกี่ยวข้อง |

## เคล็ดลับระดับมืออาชีพสำหรับการจัดการแผนภูมิที่เชื่อถือได้

* **Cache the chart reference** – หากคุณวางแผนจะแก้ไขหลายคุณสมบัติ ให้เก็บตัวแปร `Chart` ภายในไว้แทนการเรียก `chartShape.getChart()` ซ้ำ ๆ.
* **Validate input values** – ก่อนเรียก `setStartAngle` หรือ `setDoughnutHoleSize` ให้ตรวจสอบช่วงค่าเพื่อหลีกเลี่ยงข้อผิดพลาดขณะรัน.
* **Use a license** – โหมดประเมินผลจะใส่ลายน้ำบนหน้าแรก การใช้ใบอนุญาต (`License license = new License(); license.setLicense("Aspose.Words.lic");`) จะลบลายน้ำออก.

## ขั้นตอนต่อไป

เมื่อคุณรู้แล้วว่า **how to rotate chart** และ **change doughnut chart size** คุณสามารถสำรวจสถานการณ์ **modify chart in Word** อื่น ๆ ได้:

* เปลี่ยนสีของชิ้นด้วย `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* เพิ่มป้ายข้อมูลโดยเรียก `chart.getSeries().get(0).setHasDataLabel(true)`.
* ส่งออกแผนภูมิเป็นภาพโดยใช้ `chart.toImage(300, 300, ImageType.PNG)`.

แต่ละส่วนขยายเหล่านี้ทำตามรูปแบบเดียวกัน: รับอ็อบเจ็กต์ `Chart`, เรียกเมธอด setter ที่เหมาะสม, แล้วบันทึกเอกสาร.

---

**คุณเพิ่งเชี่ยวชาญการหมุนและปรับขนาดแผนภูมิ doughnut ใน Word ด้วย Java** คุณสามารถปรับโค้ดให้เข้ากับประเภทแผนภูมิอื่น ๆ, ผสานเข้ากับกระบวนการสร้างเอกสารขนาดใหญ่, หรือรวมกับ Aspose.Slides สำหรับการทำอัตโนมัติ PowerPoint ได้อย่างอิสระ. Happy coding!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญคุณสมบัติเพิ่มเติมของ API และสำรวจแนวทางการนำไปใช้ทางเลือกในโครงการของคุณ.

- [วิธีสร้างแผนภูมิคอลัมน์โดยใช้ Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [ซ่อนแกนแผนภูมิในเอกสาร Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [แทรกแผนภูมิบับเบิลในเอกสาร Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}