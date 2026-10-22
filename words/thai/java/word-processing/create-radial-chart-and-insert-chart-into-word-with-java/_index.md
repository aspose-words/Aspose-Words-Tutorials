---
category: general
date: 2026-09-27
description: สร้างแผนภูมิรัศมีใน Java และแทรกแผนภูมิลงใน Word เรียนรู้วิธีตั้งขนาดแผนภูมิ
  เพิ่มชุดข้อมูล และสร้างเอกสาร Word เปล่า.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: th
lastmod: 2026-09-27
og_description: สร้างแผนภูมิรัศมีใน Java แล้วแทรกแผนภูมิลงใน Word คู่มือนี้แสดงวิธีตั้งขนาดแผนภูมิ
  เพิ่มชุดข้อมูล และสร้างเอกสาร Word เปล่า
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: สร้างแผนภูมิแบบรัศมีและแทรกแผนภูมิลงใน Word ด้วย Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: สร้างแผนภูมิรัศมีและแทรกแผนภูมิลงใน Word ด้วย Java
url: /th/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างแผนภูมิรัศมีและแทรกแผนภูมิลงใน Word ด้วย Java

หากคุณต้องการ **สร้างแผนภูมิรัศมี** ในไฟล์ Word ด้วย Java, บทแนะนำนี้จะแสดงวิธีทำอย่างละเอียด คุณจะได้เห็นวิธี **แทรกแผนภูมิลงใน Word**, ตั้งค่าขนาดของแผนภูมิ, และสร้าง **เอกสาร Word เปล่า** ตั้งแต่ต้น

เราจะเดินผ่านทุกขั้นตอนที่จำเป็น ตั้งแต่การเริ่มต้นเอกสารจนถึงการเพิ่มชุดข้อมูลและบันทึกไฟล์ `.docx` สุดท้าย เมื่อเสร็จคุณจะมีไฟล์ Word ที่ทำงานได้เต็มรูปแบบซึ่งมีแผนภูมิรัศมีอยู่ และคุณจะเข้าใจ **วิธีตั้งค่าขนาดแผนภูมิ** และ **เพิ่มชุดข้อมูลแผนภูมิ** สำหรับการปรับแต่งในอนาคต

## ข้อกำหนดเบื้องต้น

* Java 17 หรือใหม่กว่า (โค้ดสามารถคอมไพล์ด้วย JDK สมัยใหม่ใดก็ได้)
* Aspose.Words for Java 24.9 หรือใหม่กว่า – เมธอด `setShowGraduations` มีให้ใช้ตั้งแต่เวอร์ชันนี้เท่านั้น
* IDE หรือเครื่องมือสร้าง (Maven/Gradle) ที่สามารถรวมไฟล์ JAR ของ Aspose.Words
* ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java และการจัดการ dependency ของ Maven/Gradle

> **เคล็ดลับ:** หากคุณใช้ Maven, เพิ่มส่วนต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## ขั้นตอนที่ 1: สร้างเอกสาร Word เปล่า

เอกสารเปล่าเป็นผืนผ้าใบที่แผนภูมิจะถูกวางไว้ คลาส `Document` แทนไฟล์ `.docx` ทั้งหมด

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

การสร้างเอกสารเปล่าช่วยให้ไม่มีเนื้อหาที่มีอยู่ก่อนมาขัดขวางการจัดวางแผนภูมิ

## ขั้นตอนที่ 2: เริ่มต้น DocumentBuilder

`DocumentBuilder` มีเมธอดที่สะดวกสำหรับการแทรกอ็อบเจกต์, ข้อความ, และองค์ประกอบอื่น ๆ ลงในเอกสาร

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ตัวสร้างนี้จะถูกใช้ในภายหลังเพื่อ **แทรกแผนภูมิลงใน Word**

## ขั้นตอนที่ 3: สร้างแผนภูมิรัศมี

Aspose.Words รองรับหลายประเภทของแผนภูมิ; `ChartType.RADIAL` จะสร้างแผนภูมิรัศมี (polar)

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

ในขณะนี้แผนภูมิมีอยู่แล้วแต่ยังไม่มีข้อมูล, ขนาด, หรือตัวเลือกการแสดงผล

## ขั้นตอนที่ 4: เพิ่มชุดข้อมูลลงในแผนภูมิ

แผนภูมิที่ไม่มีชุดข้อมูลจะว่างเปล่า เมธอด `add` รับชื่อชุดและอาเรย์ของค่า

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

คุณสามารถเพิ่มหลายชุดได้โดยเรียก `add` ซ้ำ ๆ ซึ่งสอดคล้องกับความต้องการ **add data series chart**

## ขั้นตอนที่ 5: เปิดใช้งานการแบ่งระดับ (เลือกได้)

การแบ่งระดับคือเส้นกริดรัศมีที่ช่วยให้อ่านง่ายขึ้น มีให้ใช้ตั้งแต่เวอร์ชัน 24.9 เท่านั้น

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

หากคุณใช้ Aspose.Words เวอร์ชันเก่า บรรทัดนี้จะทำให้เกิดข้อยกเว้น – ดังนั้นตรวจสอบเวอร์ชันของไลบรารีก่อน

## ขั้นตอนที่ 6: ตั้งค่าขนาดของแผนภูมิ

การควบคุมขนาดแผนภูมิช่วยให้คุณวางให้พอดีกับขอบกระดาษ นี่คือการตอบ **วิธีตั้งค่าขนาดแผนภูมิ**

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

คุณสามารถปรับค่าความกว้างและความสูงให้ตรงกับการออกแบบของคุณได้ จำไว้ว่า 1 point ≈ 1/72 inch

## ขั้นตอนที่ 7: แทรกแผนภูมิลงในเอกสาร Word

ตอนนี้แผนภูมิพร้อมที่จะวางแล้ว เมธอด `insertChart` ของ `DocumentBuilder` จะจัดการการแทรก

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

นี่คือหัวใจของการทำงาน **insert chart into word**

## ขั้นตอนที่ 8: บันทึกเอกสาร

สุดท้ายให้เขียนเอกสารลงดิสก์ ไฟล์จะมีแผนภูมิรัศมีที่คุณสร้างไว้

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `RadialChart.docx` ในไดเรกทอรีทำงานของโครงการ การเปิดไฟล์ใน Microsoft Word จะเห็นแผนภูมิรัศมีที่มีจุดข้อมูลสามจุดและการแบ่งระดับที่มองเห็นได้

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ Word ชื่อ `RadialChart.docx`
* ภายในไฟล์ มีหน้าเดียวที่มีแผนภูมิรัศมีขนาด 400 × 300 points
* แผนภูมิแสดงชุดข้อมูลหนึ่งชื่อ **Series 1** พร้อมค่าที่ **10, 20, 30**
* การแบ่งระดับ (เส้นกริดรัศมี) ปรากฏรอบแผนภูมิ

## ความแตกต่างทั่วไปและกรณีขอบ

| สถานการณ์ | สิ่งที่ต้องเปลี่ยน | เหตุผล |
|-----------|----------------|--------|
| **หลายชุดข้อมูล** | เรียก `chart.getSeries().add(...)` สำหรับแต่ละชุดข้อมูล | ช่วยให้แสดงการเปรียบเทียบข้อมูล |
| **ประเภทแผนภูมิอื่น** | แทนที่ `ChartType.RADIAL` ด้วย `ChartType.COLUMN` (หรือประเภทอื่น) | ใช้ประเภทแผนภูมิที่เหมาะสมกับข้อมูลของคุณที่สุด |
| **สีกำหนดเอง** | เข้าถึง `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | ช่วยปรับปรุงการสร้างแบรนด์ด้วยภาพ |
| **เวอร์ชัน Aspose.Words เก่า** | ละเว้นบรรทัด `setShowGraduations` หรืออัปเกรดไลบรารี | ป้องกัน `NoSuchMethodError` |
| **บันทึกเป็นรูปแบบอื่น** | ใช้ `doc.save("RadialChart.pdf", SaveFormat.PDF)` | สร้างไฟล์ PDF แทน DOCX |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรม Java ที่สมบูรณ์และทำงานได้เอง คัดลอกไปยังไฟล์ชื่อ `RadialChartExample.java`, เพิ่ม dependency ของ Aspose.Words, แล้วรัน

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## สรุป

ตอนนี้คุณรู้วิธี **สร้างแผนภูมิรัศมี** อย่างโปรแกรมเมติก, **เพิ่มชุดข้อมูลแผนภูมิ**, ควบคุม **วิธีตั้งค่าขนาดแผนภูมิ**, และ **แทรกแผนภูมิลงใน Word** โดยเริ่มจาก **เอกสาร Word เปล่า** ตัวอย่างใช้ Aspose.Words for Java 24.9 แต่แนวคิดเดียวกันสามารถนำไปใช้กับไลบรารีแผนภูมิอื่นที่มี API คล้ายกันได้

### ขั้นตอนต่อไป

* สำรวจประเภทแผนภูมิอื่น (`ChartType.PIE`, `ChartType.LINE`, ฯลฯ) – สิ่งนี้เชื่อมโยงกลับไปยังคีย์เวิร์ดรอง **insert chart into word**
* ปรับแต่งป้ายแกน, คำอธิบาย, และสีให้สอดคล้องกับแนวทางแบรนด์ของคุณ
* สร้างแผนภูมิแบบไดนามิกจากการสืบค้นฐานข้อมูลหรือไฟล์ CSV
* แปลงไฟล์ `.docx` ที่ได้เป็น PDF เพื่อการแจกจ่าย (`doc.save("output.pdf", SaveFormat.PDF)`)

ลองทดลองปรับขนาด, ข้อมูลชุด, และตัวเลือกการสไตล์ต่าง ๆ เพื่อสร้างภาพที่คุณต้องการอย่างแม่นยำ ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดที่ทำงานได้เต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโครงการของคุณ

- [วิธีสร้างแผนภูมิคอลัมน์โดยใช้ Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [สร้างเอกสาร Word ด้วย Java – เพิ่มรูปสี่เหลี่ยมผืนผ้าพร้อมเงา](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [แทรกแผนภูมิพื้นที่ลงในเอกสาร Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}