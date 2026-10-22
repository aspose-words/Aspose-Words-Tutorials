---
category: general
date: 2026-09-24
description: แทรกแผนภูมิวงกลมในไฟล์ DOCX ด้วย Aspose.Words for Java. เรียนรู้การตั้งค่าขนาดรู,
  การแยกชิ้นส่วนของแผนภูมิวงกลม, การเน้นชิ้นส่วนของแผนภูมิวงกลม, และการสร้างแผนภูมิ
  DOCX อย่างง่ายดาย.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: th
lastmod: 2026-09-24
og_description: แทรกแผนภูมิวงกลมในไฟล์ DOCX ด้วย Aspose.Words for Java. ตั้งค่าขนาดรู,
  แยกชิ้นพาย, เน้นชิ้นแผนภูมิวงกลม, และสร้างแผนภูมิ DOCX ภายในไม่กี่นาที.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: แทรกแผนภูมิวงกลมใน Java – สอนแบบทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: แทรกคำแผนภูมิวงกลมใน Java – คู่มือฉบับสมบูรณ์
url: /th/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกแผนภูมิวงกลมใน Java – คู่มือเต็ม

หากคุณต้องการ **แทรกแผนภูมิวงกลม** ในไฟล์ DOCX, บทแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนทั้งหมดโดยใช้ Aspose.Words for Java คุณจะได้เห็นกระบวนการทำงานตั้งแต่การสร้างเอกสารจนถึงการปรับแต่งแผนภูมิให้ส่วนหนึ่งระเบิดออก, ตั้งค่าขนาดรูเป็นศูนย์, และเน้นส่วนที่ต้องการ

การทำงานกับแผนภูมิในเอกสาร Word มักรู้สึกเหมือนเป็นเรื่องแยกจากการประมวลผลข้อความทั่วไป, แต่ Aspose.Words ทำให้ทั้งสองอย่างรวมเป็นหนึ่งเดียวได้ ในขั้นตอนต่อไปคุณจะได้เรียนรู้วิธี **สร้างแผนภูมิ DOCX** ที่พร้อมเปิดใน Microsoft Word, Google Docs หรือโปรแกรมดู DOCX ใด ๆ ที่รองรับ

## สิ่งที่คุณจะทำสำเร็จ

* **แทรกแผนภูมิวงกลม** ลงในเอกสารเปล่า  
* **ตั้งค่าขนาดรู** เพื่อทำให้แผนภูมิเป็นวงกลมเต็ม (ไม่มีโดนัท)  
* **ระเบิดชิ้นส่วนของแผนภูมิ** เพื่อดึงความสนใจไปยังส่วนที่ต้องการ  
* **เน้นชิ้นส่วนของแผนภูมิวงกลม** ด้วยการจัดรูปแบบแบบกำหนดเอง  
* **สร้างแผนภูมิ DOCX** ที่สามารถแชร์หรือแก้ไขต่อได้  

### ข้อกำหนดเบื้องต้น

* Java 17 หรือใหม่กว่า (โค้ดยังคอมไพล์ได้กับ Java 8 ด้วย)  
* ไลบรารี Aspose.Words for Java (เวอร์ชัน 23.9 หรือใหม่กว่า)  
* IDE หรือเครื่องมือสร้าง (Maven/Gradle) ที่สามารถดึง Aspose.Words dependency ได้  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## วิธีแทรกแผนภูมิวงกลมใน DOCX ด้วย Aspose.Words

ขั้นตอนแรกคือการสร้างเอกสารเปล่าใหม่และรับ `DocumentBuilder` ตัวสร้างจะให้คุณเข้าถึงสตรีมเนื้อหาในเอกสารโดยตรง ทำให้การ **แทรกแผนภูมิวงกลม** เป็นเรื่องง่าย

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### ทำไมสิ่งนี้สำคัญ
`Document` แทนไฟล์ Word ทั้งไฟล์, ส่วน `DocumentBuilder` เป็น API ระดับสูงที่ให้คุณแทรกย่อหน้า, ตาราง, และแผนภูมิได้โดยไม่ต้องจัดการ XML ระดับต่ำ การเริ่มต้นด้วยเอกสารเปล่าช่วยให้แผนภูมิที่คุณเพิ่มเป็นเนื้อหาเดียวในเอกสาร ซึ่งเหมาะสำหรับการเรียนรู้หรือการสร้างรายงานจากเทมเพลต

## ตั้งค่าขนาดรูเพื่อสร้างวงกลมเต็ม

โดยค่าเริ่มต้น Aspose.Words จะสร้างแผนภูมิโดนัทเมื่อคุณขอแผนภูมิวงกลม เพื่อทำให้แผนภูมิเป็นวงกลมจริง ๆ คุณต้อง **ตั้งค่าขนาดรู** เป็น `0` ซึ่งจะลบรูภายในและให้รูปแบบแผนภูมิวงกลมคลาสสิก

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### เคล็ดลับปฏิบัติ
หากคุณต้องการเปลี่ยนเป็นแผนภูมิโดนัทในภายหลัง เพียงเปลี่ยนค่า `holeSize` เป็นเปอร์เซ็นต์ (เช่น `30`) API เดียวกันทำงานได้กับทั้งสองประเภทของแผนภูมิ

## ระเบิดชิ้นส่วนของแผนภูมิวงกลมเพื่อเน้นส่วน

การระเบิดชิ้นส่วนทำให้ชิ้นนั้นโดดเด่นออกจากแผนภูมิ **ระเบิดชิ้นส่วนของแผนภูมิวงกลม** จะย้ายชิ้นที่เลือกออกไปทางด้านนอกตามเปอร์เซ็นต์ของรัศมีแผนภูมิ

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### ทำไมต้องระเบิด?
ชิ้นส่วนที่ระเบิดจะดึงสายตาของผู้อ่านไปยังจุดข้อมูลที่สำคัญที่สุด—เหมาะสำหรับแดชบอร์ดหรือสรุปสำหรับผู้บริหาร ค่า `20` หมายถึง 20 % ของรัศมี; คุณสามารถปรับได้ตั้งแต่ `0` (ไม่มีการระเบิด) ถึง `100` (แยกออกเต็มที่)

## เน้นชิ้นส่วนของแผนภูมิวงกลมด้วยการจัดรูปแบบแบบกำหนดเอง

นอกจากการระเบิดแล้ว คุณอาจต้องการ **เน้นชิ้นส่วนของแผนภูมิวงกลม** โดยเปลี่ยนสีเติมหรือขอบ แม้โค้ดสาธิตจะเน้นที่การระเบิด คุณสามารถขยายได้ดังนี้:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### หมายเหตุสำหรับผู้เชี่ยวชาญ
การเปลี่ยนสีเติมของชิ้นส่วนเฉพาะต้องเข้าถึงอ็อบเจ็กต์ `DataPoint` หากมีหลายซีรีส์ ให้วนลูปผ่าน `series.getDataPoints()` แล้วกำหนดสไตล์ตามเงื่อนไข

## บันทึกและตรวจสอบแผนภูมิ DOCX ที่สร้าง

สุดท้ายคุณ **สร้างแผนภูมิ DOCX** โดยการบันทึก `Document` ไฟล์ที่ได้สามารถเปิดใน Microsoft Word เพื่อดูแผนภูมิวงกลมที่จัดรูปแบบแล้ว

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### ผลลัพธ์ที่คาดหวัง
การเปิด `PieChartFormatted.docx` จะเห็นแผนภูมิวงกลมเดียว:

* แผนภูมิใช้พื้นที่ 400 × 300 pt.  
* ขนาดรูเป็น `0` ทำให้แผนภูมิเป็นวงกลมเต็ม.  
* ชิ้นส่วนแรกระเบิดออก 20 % และเปลี่ยนเป็นสีแดง (หากคุณเพิ่มการจัดรูปแบบเพิ่มเติม).  

ตอนนี้คุณมี **แผนภูมิ DOCX** ที่สามารถแจกจ่าย, ฝังในอีเมล, หรือแก้ไขต่อด้วยโปรแกรมได้

---

## ความแตกต่างและกรณีขอบที่พบบ่อย

| สถานการณ์ | วิธีปรับโค้ด |
|----------|----------------------|
| **หลายซีรีส์** | วนลูป `pieChart.getChart().getSeries()` แล้วตั้งค่า `Explosion` หรือ `FillColor` ต่อซีรีส์ |
| **ข้อมูลแบบไดนามิก** | เติมค่าลงในซีรีส์จากฐานข้อมูลหรือ CSV ก่อนเรียก `setExplosion` |
| **ขนาดแผนภูมิต่างกัน** | เปลี่ยนค่า width/height ใน `insertChart(ChartType.PIE, width, height)` |
| **ส่งออกเป็น PDF** | หลังบันทึก DOCX ให้เรียก `doc.save("output.pdf")` เพื่อสร้างไฟล์ PDF ของแผนภูมิเช่นเดียวกัน |
| **การแปลภาษา** | ใช้ `DocumentBuilder.insertChart` พร้อมรูปแบบตัวเลขตาม locale สำหรับป้ายชื่อ |

### เคล็ดลับสำหรับผู้เชี่ยวชาญ
ควรเรียก `setHoleSize(0)` **หลังจาก** `insertChart` หากเรียกก่อนการแทรก Aspose.Words จะรีเซ็ตเป็นขนาดโดนัทเริ่มต้นเมื่อสร้างแผนภูมิ

---

## สรุป

คุณได้เรียนรู้วิธี **แทรกแผนภูมิวงกลม** ลงในเอกสาร Word ด้วย Java, วิธี **ตั้งค่าขนาดรู** เพื่อให้เป็นวงกลมเต็ม, วิธี **ระเบิดชิ้นส่วนของแผนภูมิ** เพื่อดึงความสนใจ, และวิธี **เน้นชิ้นส่วนของแผนภูมิวงกลม** ด้วยสีและขอบแบบกำหนดเอง ตัวอย่างเต็มยังแสดงวิธี **สร้างแผนภูมิ DOCX** ที่พร้อมแจกจ่าย

---

## ขั้นตอนต่อไป

* สำรวจประเภทแผนภูมิอื่น ๆ (`BAR`, `LINE`, `SCATTER`) ด้วย `ChartType`.  
* ผสานการสร้างแผนภูมิกับ mail merge เพื่อสร้างรายงานส่วนบุคคล  
* ผสาน DOCX ที่สร้างเข้ากับเว็บเซอร์วิสที่ส่งไฟล์ตามคำขอ  

หากพบปัญหา อย่าลืมตรวจสอบว่าคุณใช้เวอร์ชันที่เข้ากันได้ของ Aspose.Words และไดเรกทอรีปลายทางมีอยู่และสามารถเขียนได้

ขอให้เขียนโค้ดสนุก!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมโค้ดตัวอย่างทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานอื่น ๆ ในโครงการของคุณ

- [วิธีสร้างแผนภูมิคอลัมน์โดยใช้ Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [การใช้ Word Chart API](/words/english/net/programming-with-charts/)
- [แทรกแผนภูมิบับเบิลใน Word โดยใช้ Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}