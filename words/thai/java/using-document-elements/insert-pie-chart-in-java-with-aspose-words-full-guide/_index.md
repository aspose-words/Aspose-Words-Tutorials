---
category: general
date: 2026-07-29
description: แทรกแผนภูมิวงกลมโดยใช้ Aspose.Words for Java และเรียนรู้วิธีสร้างแผนภูมิโดนัท,
  จัดรูปแบบแผนภูมิวงกลม, จัดรูปแบบแผนภูมิใน Word, และปรับขนาดแผนภูมิให้กำหนดเอง.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: th
lastmod: 2026-07-29
og_description: แทรกแผนภูมิวงกลมด้วย Aspose.Words for Java และเรียนรู้วิธีสร้างแผนภูมิโดนัทอย่างรวดเร็ว
  ปรับรูปแบบแผนภูมิวงกลม ปรับรูปแบบแผนภูมิใน Word และกำหนดขนาดแผนภูมิให้เหมาะกับเอกสารระดับมืออาชีพ
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: แทรกแผนภูมิวงกลมใน Java – บทเรียน Aspose.Words อย่างครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: แทรกแผนภูมิวงกลมใน Java ด้วย Aspose.Words – คู่มือเต็ม
url: /th/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกแผนภูมิวงกลมใน Java ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์

เคยสงสัยไหมว่า **จะแทรกแผนภูมิวงกลม** ลงในเอกสาร Word จากโค้ด Java อย่างไร? คุณไม่ได้เป็นคนเดียว—นักพัฒนาหลายคนเจออุปสรรคนี้เมื่อต้องการวิธีที่รวดเร็วและเป็นโปรแกรมเพื่อแสดงข้อมูล ข่าวดีคือ? ด้วย Aspose.Words for Java คุณทำได้ในไม่กี่บรรทัด และในขณะเดียวกันคุณยังสามารถ **สร้างแผนภูมิโดนัท**, **จัดรูปแบบแผนภูมวงกลม**, **จัดรูปแบบแผนภูมิ Word**, และ **ปรับขนาดแผนภูมิ** ให้ตรงกับแบรนด์ของคุณได้อีกด้วย

ในบทแนะนำนี้เราจะเดินผ่านตัวอย่างจริงที่เริ่มจากการสร้างเอกสารเปล่า, แทรกแผนภูมวงกลม, ปรับคุณสมบัติดีไซน์เล็กน้อย, และสุดท้ายบันทึกไฟล์ เมื่อเสร็จคุณจะได้สคริปต์ที่นำกลับไปใช้ได้ในโปรเจกต์ Java ใด ๆ ที่ต้องการอัตโนมัติการสร้างแผนภูมิ ไม่ต้องใช้ไลบรารีเพิ่มเติม ไม่ต้องยุ่งกับ Office interop—แค่ Java ที่คอมไพล์แล้วเท่านั้น

## สิ่งที่คุณต้องมี

- **Java 17** (หรือ JDK ล่าสุดใดก็ได้; API รองรับเวอร์ชันเก่า)
- **Aspose.Words for Java** 22.12 หรือใหม่กว่า – สามารถดึงจาก Maven artifact หรือไฟล์ .jar จากเว็บไซต์ Aspose
- IDE ที่สะดวก (IntelliJ IDEA, Eclipse, VS Code…) – อะไรก็ตามที่รันเมธอด `main`
- ตัวเลือก: ไฟล์ลิขสิทธิ์ หากไม่ต้องการลายน้ำรุ่นทดลอง

ถ้าคุณมีทั้งหมดนี้ เราก็พร้อมจะกระโดดเข้าสู่โค้ดได้เลย

## ขั้นตอนที่ 1: แทรกแผนภูมวงกลมด้วย Aspose.Words

สิ่งแรกที่เราทำคือ **แทรกแผนภูมวงกลม** ลงในเอกสารใหม่ ขั้นตอนนี้เป็นพื้นฐานสำหรับทุกอย่างต่อไป เพราะอ็อบเจ็กต์แผนภูมิให้เราเข้าถึง series, data points, และการปรับแต่งต่าง ๆ

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **ทำไมจึงสำคัญ:** `DocumentBuilder.insertChart` ไม่เพียงสร้างแผนภูมิ แต่ยังคืนค่าอ็อบเจ็กต์ `Chart` ที่เราสามารถจัดการได้ พารามิเตอร์ความกว้างและความสูงทำให้คุณ **ปรับขนาดแผนภูมิ** ได้ตั้งแต่ขั้นตอนสร้าง ไม่ต้องปรับขนาดภายหลัง

## ขั้นตอนที่ 2: สร้างแผนภูมิโดนัท (ไม่บังคับ)

หากการออกแบบของคุณต้องการช่องว่างตรงกลาง—เช่นแผนภูมิโดนัทคลาสสิก—Aspose ทำให้เป็นบรรทัดเดียวเดียวกัน ตัวอ็อบเจ็กต์ `Chart` เดียวกันสามารถเปลี่ยนจากวงกลมธรรมดาเป็นโดนัทโดยปรับขนาดช่องว่าง

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **เคล็ดลับ:** ขนาดช่องว่างจะทำงานเฉพาะกับ `ChartType.DONUT` เท่านั้น หากคุณยังคงใช้ประเภท `PIE` การตั้งค่านี้จะถูกละเลย ดังนั้นลองทดลองได้เลย

## ขั้นตอนที่ 3: จัดรูปแบบชิ้นส่วนของแผนภูมวงกลม

การแสดงผลที่ดีมักเน้นชิ้นส่วนใดชิ้นหนึ่ง ที่นี่เราจะ **จัดรูปแบบแผนภูมวงกลม** โดยทำให้ชิ้นส่วนแรก “explode” ออกไป 20 points เพื่อดึงความสนใจไปยังข้อมูลสำคัญ

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **เคล็ดลับระดับมืออาชีพ:** คุณสามารถวนลูป `pieChart.getSeries()` หากมีหลาย series และตั้งค่าสี, เส้นขอบ, หรือป้ายข้อมูลแยกกัน นี่คือวิธี **จัดรูปแบบแผนภูมิ Word** ด้วยสไตล์ที่หลากหลาย

## ขั้นตอนที่ 4: เพิ่มข้อมูลลงในแผนภูมิ

แผนภูมิที่ไม่มีข้อมูลก็แค่รูปทรงตกแต่งเท่านั้น เราจะใส่ชุดข้อมูลง่าย ๆ—เช่น ตัวเลขยอดขายไตรมาส

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **เหตุผลที่ทำเช่นนี้:** การเพิ่มอ็อบเจ็กต์ `ChartPoint` อย่างชัดเจนทำให้แผนภูมิงานตามตรรกะธุรกิจของเรา คำสั่ง `setShowCategoryName` และ `setShowValue` เป็นส่วนหนึ่งของ **การจัดรูปแบบแผนภูมวงกลม** เพื่อแสดงทั้งป้ายชื่อและค่าตัวเลข

## ขั้นตอนที่ 5: ปรับแต่งลักษณะ (ปรับขนาดแผนภูมิ & สไตล์)

นอกเหนือจากขนาดเริ่มต้น คุณอาจต้องการปรับ legend, title, หรือแม้แต่ฟอนต์ของป้ายข้อมูล ทั้งหมดนี้อยู่ภายใต้ **ปรับขนาดแผนภูมิ** และการจัดรูปแบบโดยรวม

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **กรณีขอบ:** หากคุณต่อมาจะส่งออกเอกสารเป็น PDF ข้อมูลเวกเตอร์ของแผนภูมิจะคมชัดอยู่ เพราะขนาดกำหนดเป็น points ไม่ใช่พิกเซล นี่คือประโยชน์สำหรับ **จัดรูปแบบแผนภูมิ Word** และรูปแบบไฟล์ต่อไป

## ขั้นตอนที่ 6: บันทึกและดูเอกสาร

ขั้นตอนสุดท้ายง่ายมาก เพียงเรียก `doc.save` ซึ่งจะเขียนไฟล์ `.docx` ที่คุณสามารถเปิดด้วย Microsoft Word, LibreOffice หรือโปรแกรมดูใด ๆ ที่รองรับรูปแบบ OpenXML

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **ผลลัพธ์:** เปิด `PieChart.docx` แล้วคุณจะเห็นแผนภูมิวงกลม (หรือโดนัท) ขนาดพอดีพร้อมชิ้นส่วนที่ “explode”, ชื่อเรื่อง, และ legend—all generated โดยไม่ต้องสัมผัส UI เลย

### ผลลัพธ์ที่คาดหวัง

| Element | สิ่งที่คุณจะเห็น |
|---------|-------------------|
| ชนิดแผนภูมิ | แผนภูมิวงกลม (หรือโดนัทถ้า `holeSize` > 0) |
| การ explode ชิ้นส่วน | ชิ้นส่วนแรกย้ายออก 20 pts |
| Legend | อยู่ด้านขวา |
| Title | “Quarterly Sales Distribution” ตัวหนา 14 pt |
| ป้ายข้อมูล | แสดงชื่อหมวดและค่าบนแต่ละชิ้นส่วน |
| เอกสาร | ไฟล์ Word `.docx` มาตรฐานพร้อมแชร์ |

## คำถามที่พบบ่อย & ข้อควรระวัง

- **ต้องการลิขสิทธิ์หรือไม่?**  
  รุ่นทดลองทำงานได้สำหรับการทดสอบ แต่จะมีลายน้ำ วางไฟล์ `aspose.words.lic` ไว้ใน classpath เพื่อผลลัพธ์ที่สะอาด

- **ใช้กับ Maven ได้หรือไม่?**  
  แน่นอน เพิ่ม dependency ต่อไปนี้ใน `pom.xml` ของคุณ:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **ถ้ามีหลาย series จะทำอย่างไร?**  
  วนลูป `pieChart.getSeries()` แล้วใช้ `setExplosion`, `setFillColor` หรือการจัดรูปแบบอื่น ๆ ต่อ series นั้น นี่คือวิธี **จัดรูปแบบแผนภูมวงกลม** สำหรับข้อมูลหลายมิติ

- **แผนภูมิสามารถแก้ไขใน Word หลังจากสร้างได้หรือไม่?**  
  ได้—บันทึกแล้วคุณสามารถเปิดเอกสารและปรับสี, ฟอนต์, หรือแม้แต่แปลงแผนภูมิวงกลมเป็นแผนภูมิบาร์ได้ตามต้องการ

## สรุป

เราเพิ่ง **แทรกแผนภูมวงกลม** ลงในเอกสาร Word ด้วย Aspose.Words for Java, แสดงวิธี **สร้างแผนภูมิโดนัท**, สาธิตหลายวิธี **จัดรูปแบบแผนภูมวงกลม**, ครอบคลุมแนวปฏิบัติ **จัดรูปแบบแผนภูมิ Word**, และเรียนรู้การ **ปรับขนาดแผนภูมิ** เพื่อให้ดูเป็นมืออาชีพ ตัวอย่างที่ทำงานได้เต็มรูปแบบด้านบนสามารถนำไปวางในโปรเจกต์ Java ใดก็ได้ ให้คุณอัตโนมัติการสร้างแผนภูมิทันทีโดยไม่ต้องพึ่ง COM interop หรือการติดตั้ง Office

ต่อไปทำอะไร? ลองเปลี่ยนแหล่งข้อมูลเป็นฐานข้อมูลแบบเรียลไทม์, เพิ่มสีตามเงื่อนไข, หรือส่งออกเอกสารเดียวกันเป็น PDF เพื่อรายงานพร้อมพิมพ์ ทุกขั้นตอนเหล่านี้ต่อจากพื้นฐานที่เราตั้งไว้ จะทำให้การเปลี่ยนแปลงเป็นเรื่องราบรื่น

หากคุณเจอปัญหา หรือมีไอเดียสำหรับการพัฒนาเพิ่มเติม—เช่นแผนภูมิแท่งซ้อนหรือแผนภูมิเส้น—แสดงความคิดเห็นด้านล่างได้เลย ขอให้สนุกกับการสร้างแผนภูมิ!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ ทุกแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบต่าง ๆ ในโปรเจกต์ของคุณ

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}