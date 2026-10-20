---
category: general
date: 2026-08-20
description: เพิ่มเส้นนำไปยังแผนภูมิวงกลมใน Java อย่างรวดเร็ว เรียนรู้วิธีแทรก, แยกชิ้น,
  เปลี่ยนสี, และตั้งป้ายชื่อส่วนต่าง ๆ ด้วย Chart API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: th
lastmod: 2026-08-20
og_description: เพิ่มเส้นนำไปยังแผนภูมิวงกลมใน Java ด้วยตัวอย่างสั้น ๆ ปฏิบัติตามคำแนะนำนี้เพื่อแทรก,
  แยก, เปลี่ยนสี และตั้งชื่อส่วนต่าง ๆ ด้วย Chart API.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: เพิ่มเส้นเชื่อมไปยังแผนภูมิวงกลมใน Java – คู่มือ Chart API แบบทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: วิธีเพิ่มเส้นนำให้กับแผนภูมิพายใน Java ด้วย Chart API
url: /th/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่ม leader lines ให้กับ pie chart ใน Java ด้วย Chart API

หากคุณต้องการ **เพิ่ม leader lines ให้กับ pie chart** ใน Java คู่มือนี้จะพาคุณผ่านกระบวนการทั้งหมด คุณจะได้เห็นวิธีแทรก pie chart, ระเบิดส่วนหนึ่งของกราฟเพื่อเน้น, เปลี่ยนสีของส่วนนั้น, และในที่สุดเปิดใช้งาน leader lines ที่เชื่อมป้ายกำกับกับส่วนที่ระเบิดออก

ตัวอย่างนี้ใช้ Chart API มาตรฐานที่พบในไลบรารีการรายงานของ Java จำนวนมาก ไม่จำเป็นต้องใช้เครื่องมือภายนอก และโค้ดสามารถทำงานได้บนสภาพแวดล้อม JDK 8+ ใดก็ได้

## สิ่งที่คุณจะได้ทำ

* สร้าง `Chart` ชนิด `ChartType.PIE` พร้อมขนาดที่กำหนดเอง  
* ระเบิดส่วนแรกของ pie chart เพื่อดึงความสนใจ  
* ตั้งค่าสี sector ของส่วนที่ระเบิดเป็นสีฟ้า  
* **เพิ่ม leader lines ให้กับ pie chart** เพื่อให้ป้ายกำกับของส่วนเชื่อมต่ออย่างชัดเจน  

คุณควรมีโปรเจกต์ Java ที่รวมไลบรารี Chart ไว้ใน classpath แล้ว หากคุณใช้ Maven ให้เพิ่ม dependency ที่แสดงในส่วนของข้อกำหนดเบื้องต้น

## ข้อกำหนดเบื้องต้น

* JDK 8 หรือใหม่กว่า ติดตั้งแล้ว  
* ไลบรารี Chart (เช่น `com.example.chart:chart-api:2.5.0`)  
* ความคุ้นเคยพื้นฐานกับคลาสและการเรียกเมธอดของ Java  

---

## วิธีเพิ่ม leader lines ให้กับ pie chart

ด้านล่างเป็นโปรแกรมเต็มที่สามารถรันได้ซึ่งแสดงขั้นตอนทั้งหมด โค้ดถูกออกแบบให้เป็นอิสระโดยเจตนาเพื่อให้คุณสามารถคัดลอก, วาง, และรันได้โดยไม่ต้องแก้ไข

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### คำอธิบายของแต่ละขั้นตอน

| ขั้นตอน | สิ่งที่โค้ดทำ | ทำไมถึงสำคัญ |
|------|-------------------|----------------|
| **1️⃣ แทรก pie chart** | `builder.insertChart(ChartType.PIE, 400, 300)` สร้าง pie chart ขนาด 400 × 300 พิกเซล | กำหนดคอนเทนเนอร์ของแผนภูมิและขนาดของมัน ซึ่งส่งผลต่อการวางป้ายกำกับและความยาวของ leader line |
| **2️⃣ ระเบิดส่วนแรก** | `setExplosion(20)` เลื่อนส่วนออกจากศูนย์กลาง 20 % ของรัศมี | ส่วนที่ระเบิดจะดึงความสนใจของผู้ชมและทำให้ leader line ปรากฏ |
| **3️⃣ ตั้งค่าสี sector** | `setSectorColor(Color.BLUE)` เปลี่ยนสีเติมของส่วนเป็นสีฟ้า | ความแตกต่างของสีช่วยเพิ่มความอ่านง่าย โดยเฉพาะเมื่อส่วนนั้นถูกเน้น |
| **4️⃣ เปิดใช้งาน leader lines** | `setLeaderLines(true)` เปิดใช้งานเส้นเชื่อมที่เชื่อมส่วนกับป้ายกำกับของมัน | leader lines ทำให้ป้ายกำกับยังคงอ่านได้แม้ส่วนจะถูกย้ายออกไปด้านนอก |

`saveAsPng` เป็นการเรียกที่เป็นทางเลือกแต่มีประโยชน์สำหรับการตรวจสอบผลลัพธ์ภาพ หลังจากรันโปรแกรม คุณควรเห็นภาพที่คล้ายกับด้านล่าง

![เพิ่ม leader lines ให้กับ pie chart](https://example.com/assets/pie-leader-lines.png "เพิ่ม leader lines ให้กับ pie chart – ส่วนที่ระเบิดสีฟ้าและ leader lines")

*รูปภาพ: pie chart ที่ส่วนแรกระเบิดออก, มีสีฟ้า, และเชื่อมต่อกับป้ายกำกับด้วย leader line.*

## ปรับแต่ง leader lines (ขั้นสูง)

การเรียก `setLeaderLines(true)` พื้นฐานใช้สไตล์เริ่มต้นของไลบรารี คุณสามารถควบคุมลักษณะเพิ่มเติมได้:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

ตัวเลือกเหล่านี้เป็นประโยชน์เมื่อคุณต้องการให้สอดคล้องกับแบรนด์ขององค์กรหรือปรับปรุงการเข้าถึง

### การจัดการหลาย series

หาก pie chart ของคุณมีมากกว่าหนึ่ง series คุณอาจต้องการ leader lines เฉพาะสำหรับ slice ที่กำหนด ใช้ดัชนี series เพื่อเลือกองค์ประกอบที่ถูกต้อง:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

เมื่อ slice ไม่ได้ระเบิด, leader line จะถูกซ่อนโดยอัตโนมัติโดยทั่วไป แต่คุณสามารถบังคับให้แสดงด้วย `setLeaderLineEnabled(true)`.

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| ปัญหา | อาการ | วิธีแก้ |
|--------|---------|-----|
| **Leader lines ไม่แสดง** | แผนภูมิแสดงโดยไม่มีเส้นเชื่อม | ตรวจสอบให้แน่ใจว่า slice ถูกระเบิด (`setExplosion` > 0) หรือเปิดใช้งาน leader lines อย่างชัดเจนบน slice |
| **ป้ายกำกับทับซ้อน** | ป้ายกำกับชนกัน | เพิ่มขนาดแผนภูมิหรือกำหนด `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)` |
| **สีไม่ถูกตั้งค่า** | Slice ยังคงเป็นสีเริ่มต้น | ตรวจสอบว่าคุณกำลังเลือก series index ที่ถูกต้อง (`getSeries().get(0)`) |
| **ไม่สามารถบันทึกภาพ** | `saveAsPng` ขว้างข้อยกเว้น | ตรวจสอบสิทธิ์การเขียนของไดเรกทอรีปลายทางและว่าไลบรารีรองรับการส่งออกเป็น PNG |

## รายการซอร์สโค้ดเต็ม

เพื่อความสะดวก นี่คือไฟล์ซอร์สเต็มอีกครั้ง รวมถึง import และคอมเมนต์:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

การรันโปรแกรมนี้จะสร้างไฟล์ `pie-with-leader-lines.png` ซึ่งแสดง pie chart ที่มี slice ระเบิดสีฟ้าและ leader line ชัดเจนที่ชี้ไปยังป้ายกำกับของ slice

## สรุป

ตอนนี้คุณรู้วิธี **เพิ่ม leader lines ให้กับ pie chart** ใน Java ด้วย Chart API แล้ว กระบวนการประกอบด้วยการแทรก `ChartType.PIE`, ระเบิด slice ที่ต้องการ, ปรับสีของมัน, และเปิดใช้งาน leader lines ด้วยตัวเลือกการจัดรูปแบบเพิ่มเติม คุณสามารถปรับสีเส้น, ความหนา, และตำแหน่งป้ายกำกับให้ตรงตามความต้องการของการแสดงผลได้

ต่อไป พิจารณาศึกษาหัวข้อที่เกี่ยวข้องเช่น **pie chart explosion Java**, **set sector color Chart API**, และ **builder.insertChart usage** เพื่อสร้างการแสดงผลที่ซับซ้อนยิ่งขึ้น เช่น donut chart, stacked pie, หรือแดชบอร์ดแบบโต้ตอบ

อย่ากลัวที่จะทดลองกับดัชนี slice, สี, และสไตล์ของ leader line ที่แตกต่าง—แผนภูมิของคุณจะมีข้อมูลมากขึ้นและดูสวยงามยิ่งขึ้นกับการปรับแต่งแต่ละครั้ง ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจกต์ของคุณ

- [วิธีสร้าง column chart ด้วย Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [เพิ่มค่า Date Time ให้กับ Axis ของ Chart](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [แทรก Column Chart ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}