---
category: general
date: 2026-09-18
description: เรียนรู้วิธีสร้างแผนภูมิรัศมีในเอกสาร Word ด้วย Java, เพิ่มป้ายข้อมูลบนแผนภูมิ,
  และแทรกข้อมูลซีรีส์พร้อมตัวอย่างโค้ดเต็มรูปแบบ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: th
lastmod: 2026-09-18
og_description: สร้างแผนภูมิรัศมีในเอกสาร Word โดยใช้ Java, เพิ่มป้ายข้อมูลของแผนภูมิ,
  และแทรกข้อมูลซีรีส์ในบทแนะนำเดียว.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: สร้างแผนภูมิรัศมีใน Word ด้วย Java – คู่มือทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: วิธีสร้างแผนภูมิรัศมีในเอกสาร Word ด้วย Java
url: /th/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างแผนภูมิรัศมีในเอกสาร Word ด้วย Java

หากคุณต้องการสร้างแผนภูมิรัศมีในเอกสาร Word คำแนะนำนี้จะแสดงขั้นตอนที่แม่นยำให้คุณได้เห็น นอกจากนี้คุณยังจะได้เรียนรู้วิธีเพิ่มป้ายข้อมูลแผนภูมิและแทรกข้อมูลซีรีส์เพื่อให้แผนภูมิเ�พร้อมสำหรับการนำเสนอ

การสร้างแผนภูมิโดยอัตโนมัติช่วยลดงานจัดรูปแบบด้วยตนเองและรับประกันความสอดคล้องระหว่างรายงานต่าง ๆ บทเรียนนี้สมมติว่าคุณมีความรู้พื้นฐานของ Java และได้ติดตั้งไลบรารี Aspose.Words for Java รุ่นล่าสุดไว้แล้ว

## สิ่งที่คุณต้องมี

* Java 17 หรือใหม่กว่า  
* Aspose.Words for Java (เวอร์ชัน 23.12 หรือใหม่กว่า)  
* IDE หรือเครื่องมือสร้างที่สามารถจัดการ dependencies ของ Maven/Gradle ได้  

การมีสิ่งเหล่านี้ติดตั้งไว้จะทำให้คุณสามารถรันตัวอย่างได้โดยไม่ต้องกำหนดค่าเพิ่มเติม

## วิธีสร้างแผนภูมิรัศมีในเอกสาร Word

ขั้นตอนแรกคือการสร้างไฟล์ Word เปล่าที่จะเป็นที่เก็บแผนภูมิ ไฟล์เอกสารเปล่าจะให้พื้นที่ทำงานที่สะอาดและหลีกเลี่ยงสไตล์ที่ไม่ต้องการ

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` แทนไฟล์ .docx ทั้งหมด ส่วน `DocumentBuilder` จะให้เมธอดสำหรับแทรกองค์ประกอบต่าง ๆ เช่น ย่อหน้า ตาราง และแผนภูมิ

## วิธีแทรกแผนภูมิ

ต่อไปคุณจะทำการแทรกแผนภูมิเข้าไปโดยตรง เมธอด `insertChart` จะสร้างอ็อบเจกต์แผนภูมิและวางไว้ที่ตำแหน่งเคอร์เซอร์ปัจจุบันของ builder

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

แผนภูมิพอลลาร์จะแสดงจุดข้อมูลรอบแกนศูนย์กลาง ซึ่งเหมาะสำหรับการแสดงข้อมูลแบบวนรอบ ขนาดของแผนภูมิระบุเป็นหน่วยจุด (1 pt ≈ 1/72 inch)

## เพิ่มข้อมูลซีรีส์ลงในแผนภูมิ

แผนภูมิที่ไม่มีข้อมูลซีรีส์จะว่างเปล่า คุณสามารถเพิ่มซีรีส์ด้วยตนเองหรือผูกกับแหล่งข้อมูล ตัวอย่างด้านล่างเพิ่มซีรีส์เดียวที่มีสามจุดข้อมูล

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` รับชื่อซีรีส์ รายการป้ายชื่อหมวดหมู่ และรายการค่าตัวเลขที่สอดคล้องกัน คุณสามารถทำซ้ำบล็อกนี้เพื่อเพิ่มซีรีส์เพิ่มเติม (`addSeriesData`)

## เพิ่มป้ายข้อมูลแผนภูมิให้กับซีรีส์แรก

ป้ายข้อมูลช่วยให้แผนภูมิเข้าใจได้โดยไม่ต้องชี้เมาส์ไปที่จุด ข้อความต่อไปนี้เปิดใช้งานป้ายค่าตัวเลขสำหรับซีรีส์แรก

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

การตั้งค่า `showValue` เป็น `true` จะทำให้ค่าของแต่ละจุดแสดงโดยตรงบนแผนภูมิ คุณยังสามารถเปิดใช้งานชื่อหมวดหมู่ เปอร์เซ็นต์ หรือเส้นนำ (leader lines) ผ่านอ็อบเจกต์ `DataLabelFormat` เดียวกันได้

## บันทึกไฟล์ Word

หลังจากตั้งค่าแผนภูมิเรียบร้อยแล้ว ให้เขียนเอกสารลงดิสก์ เลือกตำแหน่งที่แอปพลิเคชันของคุณสามารถเข้าถึงได้

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

ไฟล์ `RadialChart.docx` ตอนนี้มีแผนภูมิรัศมีพร้อมป้ายข้อมูลทำงานเต็มรูปแบบแล้ว

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่สมบูรณ์แบบซึ่งคุณสามารถคัดลอก คอมไพล์ และรันได้ มันแสดงขั้นตอนทั้งหมดตั้งแต่การสร้างเอกสาร Word เปล่าไปจนถึงการบันทึกแผนภูมิรัศมีพร้อมป้ายข้อมูล

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง**

เมื่อคุณเปิด `output/RadialChart.docx` ใน Microsoft Word คุณจะเห็นแผนภูมิรัศมีที่มีชื่อ *Quarterly Sales* แต่ละจุดจะแสดงค่าตัวเลข (เช่น “15000”) ข้างเครื่องหมาย

## ความแตกต่างทั่วไปและกรณีขอบ

| สถานการณ์ | การเปลี่ยนแปลงที่แนะนำ |
|-----------|--------------------|
| คุณต้องการประเภทแผนภูมิอื่น | แทนที่ `ChartType.POLAR` ด้วยค่า `ChartType` ใด ๆ ที่ต้องการ (เช่น `ChartType.COLUMN`) |
| แผนภูมิต้องใช้ช่วงข้อมูลจาก Excel ภายนอก | ใช้ `chart.setDataRange("Sheet1!A1:B5")` หลังจากสร้างแผนภูมิและโหลด workbook |
| คุณต้องการซ่อน legend | `chart.getLegend().setVisible(false);` |
| ต้องการบันทึกเอกสารเป็น PDF | เรียก `doc.save("RadialChart.pdf");` – Aspose.Words จะทำการแปลงแผนภูมิโดยอัตโนมัติ |

การปรับเปลี่ยนเหล่านี้ทำให้ตรรกะหลักคงเดิมในขณะที่ปรับผลลัพธ์ให้ตรงกับความต้องการเฉพาะ

## เคล็ดลับระดับมืออาชีพ

* **ใช้ builder ซ้ำ** – คุณสามารถแทรกหลายแผนภูมิในเอกสารเดียวกันโดยเรียก `builder.insertChart` หลายครั้ง |
* **ประสิทธิภาพ** – เมื่อสร้างแผนภูมิจำนวนมาก ให้สร้างอินสแตนซ์ `DocumentBuilder` เพียงหนึ่งตัวและใช้ซ้ำ เพื่อลดภาระการจัดสรรอ็อบเจกต์ |
* **การจัดรูปแบบ** – ลักษณะของแผนภูมิ (สี ความหนาของเส้น) ควบคุมผ่านเมธอด `Chart` เช่น `getSeries().get(i).getFormat()` ทดลองปรับค่าเหล่านี้เพื่อให้สอดคล้องกับแบรนด์ขององค์กร |

## สรุป

คุณได้เรียนรู้วิธีสร้างแผนภูมิรัศมีในเอกสาร Word ด้วย Java การเพิ่มข้อมูลซีรีส์และป้ายข้อมูลแผนภูมิก่อนบันทึกไฟล์ ตัวอย่างเต็มรูปแบบสามารถต่อยอดเพื่อจัดการซีรีส์เพิ่มเติม สไตล์ที่กำหนดเอง หรือรูปแบบผลลัพธ์อื่น ๆ

สำรวจหัวข้อที่เกี่ยวข้องเช่น **วิธีแทรกแผนภูมิ** จากแหล่งข้อมูลภายนอก, **สร้างเอกสาร Word เปล่า** ด้วยเทมเพลตที่กำหนดล่วงหน้า, และ **เพิ่มข้อมูลซีรีส์** อย่างไดนามิกจากฐานข้อมูล ทดลองใช้ประเภทแผนภูมิต่าง ๆ เพื่อค้นหาว่าวิธีการนำเสนอใดสื่อสารข้อมูลของคุณได้ดีที่สุด


## คุณควรเรียนรู้อะไรต่อไป?


บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญคุณสมบัติ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโครงการของคุณ

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}