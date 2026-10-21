---
category: general
date: 2026-10-04
description: เรียนรู้วิธีการแยกชิ้นส่วนในแผนภูมิ Word, แยกชิ้นส่วนของแผนภูมิวงกลมและเปลี่ยนขนาดแผนภูมิโดนัทด้วยตัวอย่าง
  Java ทีละขั้นตอน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: th
lastmod: 2026-10-04
og_description: วิธีแยกส่วนของแผนภูมิใน Word และปรับแต่งแผนภูมิวงกลมหรือโดนัทด้วย
  Java. ติดตามตัวอย่างเต็มเพื่อแก้ไขแผนภูมิใน Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: วิธีแยกชิ้นส่วนในแผนภูมิ Word – คู่มือ Java ฉบับเต็ม
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: วิธีแยกชิ้นส่วนในแผนภูมิ Word และปรับแต่งลักษณะของมัน
url: /th/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการ explode slice ในแผนภูมิ Word และปรับแต่งลักษณะของมัน

หากคุณต้องการ **how to explode slice** ในแผนภูมิ Word คู่มือนี้จะแสดงให้คุณเห็นอย่างชัดเจน ไม่ว่าคุณจะกำลังเตรียมการนำเสนอการขายหรือรายงานการเงิน การ explode พาย‑chart slice หรือการปรับขนาด doughnut hole สามารถทำให้ข้อมูลที่สำคัญที่สุดโดดเด่นขึ้น ในส่วนต่อไปนี้คุณจะได้เรียนรู้วิธี **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, และ **customize pie chart word** เอกสารโดยใช้ Aspose.Words for Java.

คุณจะจบบทเรียนนี้ด้วยโปรแกรม Java ที่สมบูรณ์และพร้อมรัน ซึ่งโหลดไฟล์ `.docx` , explode slice แรกของพาย‑chart, ปรับขนาด doughnut hole, และบันทึกผลลัพธ์ ไม่จำเป็นต้องใช้สคริปต์ภายนอกหรือการแก้ไขด้วยมือ

## ข้อกำหนดเบื้องต้น

- Java 17 หรือใหม่กว่า ติดตั้งบนเครื่องพัฒนาของคุณ  
- Maven 3.6+ (หรือ Gradle) เพื่อจัดการ dependencies  
- ไลบรารี Aspose.Words for Java (เวอร์ชันทดลองใช้งานฟรีสำหรับการพัฒนา)  
- เอกสาร Word (`input.docx`) ที่มีอย่างน้อยหนึ่งแผนภูมิ (พายหรือ doughnut)

## ขั้นตอนที่ 1: เพิ่ม Aspose.Words ลงในโปรเจกต์ของคุณ

หากคุณใช้ Maven ให้เพิ่ม dependency ต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

สำหรับ Gradle ให้วางโค้ดนี้ในไฟล์ `build.gradle` :

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **เคล็ดลับ:** ควรอัปเดตเวอร์ชันของไลบรารีให้เป็นล่าสุด; รุ่นใหม่จะเพิ่มการสนับสนุนประเภทแผนภูมิเพิ่มเติมและปรับปรุงประสิทธิภาพ

## ขั้นตอนที่ 2: โหลดเอกสาร Word ที่มีแผนภูมิ

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**ทำไมจึงสำคัญ:** การโหลดเอกสารจะสร้างการแสดงผลในหน่วยความจำที่ Aspose.Words สามารถสำรวจได้ หากไม่มีอ็อบเจ็กต์นี้คุณจะไม่สามารถเข้าถึงโหนดแผนภูมิได้

## ขั้นตอนที่ 3: ดึงแผนภูมิแรกในเอกสาร

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **คำอธิบาย:** `NodeType.SHAPE` ครอบคลุมวัตถุการวาดทั้งหมด รวมถึงแผนภูมิด้วย อาร์กิวเมนต์ `true` บอกให้ Aspose ค้นหาแบบเรียกซ้ำ เพื่อให้แน่ใจว่าแผนภูมิแรกจะถูกพบแม้ว่าจะอยู่ภายในตาราง

## ขั้นตอนที่ 4: Explode slice แรกของพาย‑chart

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**วิธีการทำงาน:** เมธอด `setExplosion` รับค่าตัวเลขที่กำหนดระยะที่ slice จะเคลื่อนออกจากศูนย์กลาง ค่า `20` จะเห็นได้ชัดเจนโดยไม่ทำให้รูปแบบแผนภูมิเสียหาย

## ขั้นตอนที่ 5: ปรับขนาด doughnut hole สำหรับแผนภูมิ doughnut

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**ทำไมจึงช่วยได้:** doughnut hole ที่ใหญ่ขึ้นสามารถทำให้อ่านง่ายขึ้นเมื่อมีจุดข้อมูลหลายจุด เมธอด `setDoughnutHoleSize` รับค่าเป็นเปอร์เซ็นต์ (0‑100)

## ขั้นตอนที่ 6: บันทึกเอกสารที่แก้ไขแล้ว

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### ผลลัพธ์ที่คาดหวัง

- Slice แรกของพาย‑chart แรกจะถูกย้ายออกด้านนอก ทำให้โดดเด่น  
- หากแผนภูมิเป็น doughnut, ช่องกลางจะขยายเป็น 40 % ของรัศมีแผนภูมิ  
- ไฟล์ผลลัพธ์ `PieChart.docx` สามารถเปิดได้ใน Microsoft Word, LibreOffice หรือโปรแกรมดูที่รองรับอื่น ๆ แสดงการเปลี่ยนแปลงภาพที่คุณทำโดยอัตโนมัติ

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมทั้งหมดในบล็อกเดียว คัดลอกไปยังไฟล์ `ChartExploder.java`, ปรับเส้นทางไฟล์ตามต้องการ, แล้วรันด้วยคำสั่ง `mvn compile exec:java` (หรือการตั้งค่า run ของ IDE ของคุณ)

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

การรันโค้ดนี้จะ **modify chart in Word**, **explode pie chart slice**, และ **change doughnut chart size** โดยอัตโนมัติ

## คำถามที่พบบ่อยและกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| *ถ้าเอกสารมีหลายแผนภูมิจะทำอย่างไร?* | ตัวอย่างนี้มุ่งเป้าไปที่แผนภูมิ **แรก** (`NodeType.SHAPE, 0`). หากต้องการทำงานกับแผนภูมิอื่น ให้เปลี่ยนดัชนีหรือวนลูปผ่าน `doc.getChildNodes(NodeType.SHAPE, true)` และกรองด้วย `shape.getChart() != null`. |
| *ฉันสามารถ explode slice ที่ไม่ใช่อันแรกได้หรือไม่?* | ได้. เข้าถึงซีรีส์ที่ต้องการผ่าน `chart.getSeries().get(seriesIndex)` แล้วเรียก `setExplosion(value)`. ดัชนีเริ่มจากศูนย์. |
| *โค้ดนี้ทำงานกับไฟล์ Word 2007‑2021 หรือไม่?* | Aspose.Words รองรับไฟล์ `.doc`, `.docx`, `.dot` และ `.dotx`. โค้ดเดียวกันทำงานได้ในทุกเวอร์ชันเนื่องจากไลบรารีแยกความแตกต่างของรูปแบบไฟล์ออก. |
| *ถ้าแผนภูมิเป็นแบบแท่งหรือเส้นจะทำอย่างไร?* | `setExplosion` และ `setDoughnutHoleSize` ใช้ได้เฉพาะแผนภูมิประเภทพายเท่านั้น โค้ดจะข้ามการทำงานเหล่านี้อย่างปลอดภัยเมื่อประเภทแผนภูมิแตกต่าง. |
| *ฉันต้องการไลเซนส์สำหรับ Aspose.Words หรือไม่?* | ไลเซนส์ทดลองฟรีจะลบข้อจำกัด 30 วันแต่จะเพิ่มลายน้ำ สำหรับการใช้งานจริงควรซื้อไลเซนส์เพื่อเอาลายน้ำออกและเปิดใช้งานฟังก์ชันเต็ม. |

## สรุป

ตอนนี้คุณรู้แล้วว่า **how to explode slice** ในแผนภูมิ Word, วิธี **modify chart in Word**, และวิธี **change doughnut chart size** ด้วย Aspose.Words for Java ตัวอย่างเต็มแสดงขั้นตอนการทำงานทั้งหมด — ตั้งแต่การโหลดเอกสาร, ค้นหาแผนภูมิ, ปรับแต่งภาพ, จนถึงการบันทึกผลลัพธ์ — เพื่อให้คุณสามารถนำขั้นตอนเหล่านี้ไปใช้ในกระบวนการรายงานหรือการสร้างเอกสารใด ๆ

**ขั้นตอนต่อไป**

- สำรวจการปรับแต่งแผนภูมิอื่น ๆ เช่น การเปลี่ยนสี, การเพิ่มป้ายข้อมูล, หรือการสลับประเภทแผนภูมิ (`chart.setChartType(ChartType.BAR_CLUSTERED)`)  
- ผสานตรรกะนี้กับ Aspose.PDF เพื่อสร้างเวอร์ชัน PDF ของรายงานเดียวกัน  
- ทำกระบวนการอัตโนมัติสำหรับชุดเอกสารโดยวนลูปไฟล์ในไดเรกทอรี

คุณสามารถทดลองใช้ค่า explosion หรือเปอร์เซ็นต์ doughnut hole ที่แตกต่างเพื่อให้ตรงกับแนวทางการออกแบบของคุณได้เลย สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}