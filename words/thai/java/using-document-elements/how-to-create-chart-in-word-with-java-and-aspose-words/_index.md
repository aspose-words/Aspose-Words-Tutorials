---
category: general
date: 2026-09-24
description: เรียนรู้วิธีสร้างแผนภูมิใน Word ด้วย Java, แทรกแผนภูมิแบบรัศมี, และบันทึกเอกสารเป็นไฟล์
  docx ด้วย Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: th
lastmod: 2026-09-24
og_description: สร้างแผนภูมิใน Word ด้วย Java และ Aspose.Words บทเรียนนี้จะแสดงวิธีเพิ่มแผนภูมิรัศมี
  ปรับแต่งข้อมูล และบันทึกเอกสารเป็นไฟล์ docx
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: สร้างแผนภูมิใน Word ด้วย Java – คู่มือทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: วิธีสร้างแผนภูมิใน Word ด้วย Java และ Aspose.Words
url: /th/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างแผนภูมิใน Word ด้วย Java และ Aspose.Words

หากคุณต้องการ **สร้างแผนภูมิใน Word** จากแอปพลิเคชัน Java คำแนะนำนี้จะพาคุณผ่านกระบวนการทั้งหมด คุณจะได้เห็นวิธีเพิ่มแผนภูมิแบบรัศมี (radial chart) โดยอาจเติมข้อมูลให้ซีรีส์ของมัน และสุดท้าย **บันทึกเอกสารเป็น docx** ด้วยไลบรารี Aspose.Words for Java

การสร้างข้อมูลภาพภายในไฟล์ Word เป็นความต้องการทั่วไปสำหรับการรายงาน, การออกใบแจ้งหนี้, หรือการสร้างเอกสารอัตโนมัติ เมื่อจบบทเรียนนี้คุณจะสามารถทำโครงการ **create word document java** ที่ **add chart to Word** ไฟล์โดยไม่ต้องแก้ไขด้วยตนเอง

## ข้อกำหนดเบื้องต้น

* Java Development Kit (JDK) 8 หรือใหม่กว่า.
* Maven หรือ Gradle สำหรับการจัดการ dependencies.
* IDE เช่น IntelliJ IDEA, Eclipse หรือ VS Code.
* ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (รุ่นทดลองฟรีใช้ได้สำหรับการพัฒนา).

เครื่องมือเหล่านี้เป็นพื้นฐานสำหรับตัวอย่างโค้ดต่อไป

## ขั้นตอนที่ 1: ตั้งค่าโครงการ Maven

สร้างโครงการ Maven ใหม่ (หรืออัปเดตโครงการที่มีอยู่) และเพิ่ม dependency ของ Aspose.Words ไปยังไฟล์ `pom.xml` ของคุณ:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

การรัน `mvn clean install` จะดาวน์โหลดไลบรารีและทำให้คลาสเช่น `Document`, `DocumentBuilder` และ `ChartType` พร้อมใช้งานใน classpath.

> **เคล็ดลับ:** ควรอัปเดตเวอร์ชันของไลบรารีให้เป็นปัจจุบัน เวอร์ชันใหม่จะเพิ่มประเภทแผนภูมิและปรับปรุงประสิทธิภาพการเรนเดอร์.

## ขั้นตอนที่ 2: สร้างเอกสาร Word ใหม่

ขั้นตอนโปรแกรมแรกในการ **สร้างแผนภูมิใน Word** คือการสร้างอินสแตนซ์ของ `Document` ว่างเปล่า วัตถุนี้แทนแพคเกจ `.docx` ทั้งหมด.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` ทำงานคล้ายเคอร์เซอร์; มันรู้ตำแหน่งการแทรกปัจจุบันและให้เมธอดสำหรับข้อความ, ตาราง, และแผนภูมิ ตอนนี้คุณได้ **created word document java** สไตล์ – พื้นผิวว่างที่พร้อมสำหรับเนื้อหา.

## ขั้นตอนที่ 3: แทรกแผนภูมิแบบรัศมี

Aspose.Words รองรับหลายประเภทของแผนภูมิ เพื่อ **insert radial chart** ให้เรียก `insertChart` พร้อม `ChartType.RADIAL` เมธอดนี้ยังต้องระบุความกว้างและความสูงเป็นหน่วย point (1 point ≈ 1/72 inch).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

อ็อบเจ็กต์ `Shape` ที่คืนมาจะบรรจุแผนภูมิพื้นฐาน แผนภูมิจะเรนเดอร์การแบ่งระดับอัตโนมัติสำหรับการจัดวาง 24.9° ซึ่งเป็นค่าเริ่มต้นของแผนภูมิแบบรัศมีใน Word.

### ทำไมต้องใช้แผนภูมิแบบรัศมี?

แผนภูมิแบบรัศมีแสดงข้อมูลที่ล้อมรอบวงกลม ทำให้เหมาะสำหรับการแสดงรูปแบบวนรอบ (เช่น ยอดขายรายเดือน, ตัวชี้วัดแบบหน้านาฬิกา) API เดียวกันสามารถแทรกแผนภูมิแบบแท่ง, พาย หรือเส้นได้ แต่ประเภทรัศมีให้ลุคที่โดดเด่นโดยไม่ต้องเขียนโค้ดสไตล์เพิ่มเติม.

## ขั้นตอนที่ 4: (ทางเลือก) เติมข้อมูลซีรีส์ของแผนภูมิ

หากคุณต้องการให้แผนภูมิแสดงค่าจริง คุณต้องเพิ่มซีรีส์และจุดข้อมูล โค้ดต่อไปนี้เพิ่มซีรีส์เดียวที่มีสามจุดข้อมูล:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

คุณสามารถทำซ้ำการเรียก `add` สำหรับจำนวนจุดที่ต้องการ Aspose.Words จะอัปเดตการแสดงผลโดยอัตโนมัติ ทำให้คุณเห็นส่วนของแผนภูมิรัศมีปรับตามค่าที่ใหม่.

> **คำถามทั่วไป:** *ถ้าฉันต้องการเชื่อมข้อมูลจากฐานข้อมูลล่ะ?*  
> ดึงแถวข้อมูล, วนลูปผ่านแต่ละแถว, และเรียก `series.getDataPoints().add(value, label)` ภายในลูป API นี้ปลอดภัยต่อการทำงานหลายเธรดและทำงานกับ `ResultSet` ใด ๆ ที่คุณให้.

## ขั้นตอนที่ 5: บันทึกเอกสารเป็น DOCX

เมื่อแผนภูมิพร้อม ขั้นตอนสุดท้ายคือ **บันทึกเอกสารเป็น docx** เมธอด `save` จะกำหนดรูปแบบเอาต์พุตจากนามสกุลไฟล์.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

ไฟล์ที่สร้างขึ้นจะมีแผนภูมิรัศมีที่ทำงานเต็มรูปแบบซึ่งสามารถเปิดได้ใน Microsoft Word, LibreOffice หรือโปรแกรมดูไฟล์ใด ๆ ที่รองรับรูปแบบ DOCX เนื่องจากเราใช้ส่วนขยาย `.docx` Word จะบันทึกไฟล์ในรูปแบบ Open XML ซึ่งเป็นมาตรฐานสมัยใหม่สำหรับเอกสาร Word.

### ตรวจสอบผลลัพธ์

เปิด `RadialChartDemo.docx` ใน Word:

1. คุณควรเห็นหน้าเดียวที่มีแผนภูมิรัศมีอยู่ตรงกลาง.
2. หากคุณเพิ่มข้อมูลซีรีส์ แผนภูมิจะแสดงสี่ส่วนที่มีป้าย Q1‑Q4.
3. คลิกขวาที่แผนภูมิ → **Edit Data** เพื่อยืนยันตารางข้อมูลพื้นฐาน.

หากแผนภูมิเกิดเป็นสีขาวเปล่า ให้ตรวจสอบอีกครั้งว่าคุณได้เรียก `chart.getChart()` ก่อนเพิ่มซีรีส์ และตรวจให้แน่ใจว่าเคอร์เซอร์ของ DocumentBuilder อยู่ในตำแหน่งที่คุณต้องการแทรกแผนภูมิ.

## ขั้นตอนที่ 6: เคล็ดลับขั้นสูงสำหรับการทำงานกับแผนภูมิ

| Tip | Why it matters |
|-----|----------------|
| **ตั้งสไตล์แผนภูมิ** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | ปรับปรุงความสอดคล้องของภาพโดยไม่ต้องจัดรูปแบบแต่ละองค์ประกอบด้วยตนเอง. |
| **ปรับขนาดหลังการแทรก** – `chart.setWidth(500); chart.setHeight(350);` | ช่วยให้คุณปรับขนาดแผนภูมิให้เหมาะสมกับการจัดหน้า. |
| **เพิ่มหัวเรื่อง** – `chart.getChart().getTitle().setText("Revenue Overview");` | ให้บริบทแก่ผู้อ่านที่ดูเอกสารโดยไม่มีข้อความรอบ ๆ. |
| **ส่งออกเป็น PDF** – `doc.save("RadialChartDemo.pdf");` | มีประโยชน์เมื่อคุณต้องการเวอร์ชันที่ไม่สามารถแก้ไขได้สำหรับการแจกจ่าย. |
| **จัดการใบอนุญาต** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | ป้องกันลายน้ำการประเมินผลในรุ่นผลิต. |

การปรับปรุงเหล่านี้เป็นทางเลือก แต่แสดงให้เห็นว่าคุณสามารถปรับแต่งแผนภูมิได้เพิ่มเติมหลังจากที่คุณได้เรียนรู้วิธี **add chart to Word**.

## สรุป

ตอนนี้คุณมีตัวอย่างที่ครบถ้วนและเป็นอิสระที่แสดงวิธี **create chart in Word** ด้วย Java, **insert radial chart**, เติมข้อมูลตามต้องการ, และ **save document as docx** รูปแบบเดียวกันทำงานกับประเภทแผนภูมิอื่น ๆ ดังนั้นคุณสามารถขยายบทเรียนนี้ไปยังแผนภูมิแท่ง, เส้น, หรือพายตามต้องการ.

ต่อไปคุณอาจสำรวจ:

* **create word document java** โครงการที่รวมตาราง, รูปภาพ, และหลายแผนภูมิ.
* ใช้ **save document as docx** ร่วมกับ **save document as pdf** สำหรับการรายงานหลายรูปแบบ.
* เพิ่มข้อมูลแบบไดนามิกจาก REST APIs หรือฐานข้อมูลไปยังแผนภูมิของคุณ.

คุณสามารถทดลองกับตัวเลือกการจัดสไตล์, ขนาดแผนภูมิ, และแหล่งข้อมูลได้ตามต้องการ ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}