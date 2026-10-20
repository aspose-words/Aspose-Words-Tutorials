---
category: general
date: 2026-09-11
description: วิธีแก้ไขแผนภูมิในเอกสาร Word ด้วย Java – เรียนรู้การอัปเดตการตั้งค่าแผนภูมิ,
  เปิดใช้งานเส้นกริดของแผนภูมิ, เปลี่ยนตัวเลือกแผนภูมิ, และบันทึกเอกสารที่อัปเดต
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: th
lastmod: 2026-09-11
og_description: วิธีแก้ไขแผนภูมิในเอกสาร Word ด้วย Java. ปฏิบัติตามคำแนะนำนี้เพื่ออัปเดตการตั้งค่าแผนภูมิ,
  เปิดใช้งานเส้นกริดของแผนภูมิ, เปลี่ยนตัวเลือกแผนภูมิ, และบันทึกเอกสารที่อัปเดตแล้ว.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: วิธีแก้ไขแผนภูมิในเอกสาร Word ด้วย Java – คู่มือเต็ม
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: วิธีแก้ไขแผนภูมิในเอกสาร Word ด้วย Java
url: /th/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแก้ไขแผนภูมิในเอกสาร Word ด้วย Java

หากคุณต้องการ **วิธีแก้ไขแผนภูมิ** ในไฟล์ Word คำแนะนำนี้จะแสดงขั้นตอนที่ชัดเจน คุณจะได้เรียนรู้วิธีอัปเดตการตั้งค่าแผนภูมิ, เปิดใช้งานเส้นกริดของแผนภูมิ, เปลี่ยนตัวเลือกของแผนภูมิ, และสุดท้าย **บันทึกเอกสารที่อัปเดต** โดยไม่สูญเสียการจัดรูปแบบใด ๆ  

การทำงานกับแผนภูมิแบบโปรแกรมมักรู้สึกเหมือนการดำเนินการแบบกล่องดำ, โดยเฉพาะเมื่อคุณต้องการปรับรายละเอียดภาพเช่นการแบ่งระดับหรือเส้นกริด. บทเรียนนี้ครอบคลุมทุกสิ่งที่คุณต้องรู้, ตั้งแต่การโหลดเอกสารจนถึงการบันทึกการเปลี่ยนแปลง. ไม่ต้องใช้เครื่องมือภายนอก—เพียงไลบรารี Aspose.Words for Java (เวอร์ชัน 24.9 หรือใหม่กว่า).  

โดยตอนท้ายของบทความนี้คุณจะสามารถ:

* โหลดไฟล์ `.docx` ที่มีแผนภูมิ.  
* ค้นหา shape ของแผนภูมิและแก้ไขคุณสมบัติของมัน.  
* เปิดใช้งานเส้นกริดของแผนภูมิ (graduations) และปรับตัวเลือกอื่น ๆ.  
* **บันทึกเอกสารที่อัปเดต** ไปยังไฟล์ใหม่.  

## ข้อกำหนดเบื้องต้น

* Java 17 หรือใหม่กว่า ติดตั้งบนเครื่องของคุณ.  
* Maven หรือ Gradle เพื่อจัดการ dependencies.  
* Aspose.Words for Java 24.9+ (เวอร์ชันที่แนะนำ `setShowGraduations`).  
* เอกสาร Word (`input.docx`) ที่มีแผนภูมิอย่างน้อยหนึ่งรายการ.  

หากคุณไม่คุ้นเคยกับ Aspose.Words, ให้คิดว่าเป็น API ที่ครบถ้วนซึ่งช่วยให้คุณอ่าน, แก้ไข, และเขียนเอกสาร Word ด้วยโปรแกรม—คล้ายกับการจัดการ DOM ในเว็บเบราว์เซอร์.  

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้าไลบรารี

สร้างโปรเจกต์ Maven ใหม่หรือเพิ่ม dependency ลงในโปรเจกต์ที่มีอยู่:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **เคล็ดลับ:** ใช้รุ่น stable ล่าสุดเพื่อให้แน่ใจว่ามีเมธอด `setShowGraduations`. รุ่นเก่าจะไม่คอมไพล์.  

## ขั้นตอนที่ 2: โหลดเอกสาร Word ที่มีแผนภูมิ

การกระทำแรกในกระบวนการ **วิธีแก้ไขแผนภูมิ** ใด ๆ คือการโหลดไฟล์ต้นทาง. Aspose.Words แสดงเอกสารทั้งหมดด้วยคลาส `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

`Document` object ให้คุณเข้าถึงทุกโหนดภายในไฟล์, รวมถึง shape, ตาราง, และย่อหน้า.  

## ขั้นตอนที่ 3: ค้นหา shape ของแผนภูมิแรกในเอกสาร

แผนภูมิจะถูกเก็บเป็นโหนด `Shape` ที่ renderer เป็น `Chart`. เพื่อแก้ไขแผนภูมิคุณต้องดึงโหนดนั้นก่อน.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

หากเอกสารมีหลายแผนภูมิ, ให้วนลูป `shapes` และตรวจสอบ `chartShape.getChart() != null` ก่อนทำการแคสต์. สิ่งนี้จะป้องกัน `ClassCastException` และทำให้คุณ **เปลี่ยนตัวเลือกของแผนภูมิ** เฉพาะบนอ็อบเจ็กต์แผนภูมิที่ถูกต้อง.  

## ขั้นตอนที่ 4: เปิดใช้งานเส้นกริดของแผนภูมิ (graduations) – คุณสมบัติใหม่ในเวอร์ชัน 24.9

คุณสมบัติ `setShowGraduations` สลับการแสดงผลของเส้นกริดย่อยบนแกนค่า. การเปิดใช้งานมักช่วยเพิ่มความอ่านง่ายสำหรับชุดข้อมูลที่หนาแน่น.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **ทำไมเรื่องนี้สำคัญ:** เส้นกริดให้ผู้ชมอ้างอิงภาพสำหรับแต่ละจุดข้อมูล, ทำให้แนวโน้มง่ายต่อการสังเกต. ค่าเริ่มต้นคือ `false`, ดังนั้นคุณต้องเปิดใช้งานอย่างชัดเจนเมื่อจำเป็น.  

คุณยังสามารถปรับแต่งด้านอื่น ๆ เช่น เส้นกริดหลัก, ชื่อแกน, หรือการวางตำแหน่ง legend. ด้านล่างเป็นตัวอย่างการเปลี่ยนชื่อแผนภูมิและตำแหน่ง legend—ซึ่งเป็นส่วนหนึ่งของ **เปลี่ยนตัวเลือกของแผนภูมิ**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## ขั้นตอนที่ 5: บันทึกเอกสารพร้อมการตั้งค่าแผนภูมิที่อัปเดต

หลังจากแก้ไขแผนภูมิแล้ว, ให้บันทึกการเปลี่ยนแปลง. ขั้นตอนนี้เสร็จสิ้นขั้นตอน **บันทึกเอกสารที่อัปเดต**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `output.docx` ที่แผนภูมิแสดงเส้นกริด, ชื่อใหม่, และ legend ที่ย้ายตำแหน่ง. เปิดไฟล์ใน Microsoft Word เพื่อยืนยันการเปลี่ยนแปลงภาพ.  

## โค้ดเต็ม (สามารถรันได้)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิด `output.docx`:

* แผนภูมิแสดงเส้นกริดย่อยบนแกนค่า.  
* ชื่อแสดงเป็น **“Sales Overview 2026”**.  
* legend ปรากฏที่ด้านล่างของแผนภูมิ.  

หากแผนภูดิมาตรฐานมีเส้นกริดแล้ว, รูปลักษณ์ภาพจะไม่เปลี่ยนแปลง, ยืนยันว่าโค้ดเป็น **idempotent**.  

## คำถามทั่วไปและการจัดการกรณีขอบ

### ถ้าเอกสารไม่มีแผนภูมิ?

การพยายามแคสต์ shape ที่ไม่ใช่แผนภูมิจะทำให้เกิด `ClassCastException`. ป้องกันโดยตรวจสอบประเภทของ shape:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### วิธีแก้ไขแผนภูมิเฉพาะแทนแผนภูมิแรก?

วนลูป `shapes` และจับคู่กับชื่อที่รู้จักหรือ identifier อื่น:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### สามารถปิดเส้นกริดอีกครั้งในภายหลังได้หรือไม่?

ได้, เพียงตั้งค่าคุณสมบัติเป็น `false`:

```java
chart.setShowGraduations(false);
```

### วิธีนี้ทำงานกับไฟล์ `.doc` (binary) หรือไม่?

Aspose.Words แยกความแตกต่างของรูปแบบไฟล์, ดังนั้นโค้ดเดียวกันทำงานได้กับ `.doc` และ `.docx`. อย่างไรก็ตาม, คุณลักษณะแผนภูมิใหม่บางอย่าง (เช่น graduations) จะถูกเก็บเฉพาะในรูปแบบ OOXML, ดังนั้นคุณจะเห็นผลเฉพาะเมื่อบันทึกเป็น `.docx`.  

## เคล็ดลับสำหรับโค้ดพร้อมใช้งานในโปรดักชัน

* **Validate input paths** – ใช้ `Files.exists(Paths.get(inputPath))` ก่อนโหลด.  
* **Wrap API calls** ในบล็อก try‑catch เพื่อแสดงรายละเอียดของ `Exception`, โดยเฉพาะเมื่อจัดการกับเอกสารที่เสียหาย.  
* **Dispose resources** – แม้ว่า Aspose.Words จะจัดการหน่วยความจำ, การเรียก `doc.close()` (หรือใช้ try‑with‑resources หากมี) สามารถปล่อย native handles ได้เร็วขึ้น.  
* **Version check** – ตรวจสอบให้แน่ใจว่าเวอร์ชันไลบรารีรันไทม์เป็น ≥ 24.9 ก่อนเรียก `setShowGraduations`. คุณสามารถสอบถาม `License.getVersion()` หากต้องการการตรวจสอบแบบโปรแกรม.  

## สรุป

ตอนนี้คุณรู้ **วิธีแก้ไขแผนภูมิ** ในเอกสาร Word ด้วย Java แล้ว. กระบวนการ—โหลดเอกสาร, ค้นหาแผนภูมิ, เปิดใช้งานเส้นกริดของแผนภูมิ, เปลี่ยนตัวเลือกของแผนภูมิ, และ **บันทึกเอกสารที่อัปเดต**—ครอบคลุมสถานการณ์ที่พบบ่อยที่สุดสำหรับการจัดการแผนภูมิแบบโปรแกรม.  

จากนี้คุณสามารถสำรวจการปรับแต่งเพิ่มเติม เช่น การเปลี่ยนสีของ series ข้อมูล, การใช้สไตล์แผนภูมิ, หรือการส่งออกแผนภูมิเป็นภาพ. งานแต่ละอย่างทำตามรูปแบบเดียวกัน: ดึงอินสแตนซ์ `Chart`, ปรับคุณสมบัติ, และ **บันทึกเอกสารที่อัปเดต**.  

ขอให้สนุกกับการเขียนโค้ด, และอย่าลังเลที่จะทดลองตั้งค่าแผนภูมิอื่น ๆ เพื่อให้ตรงกับความต้องการของการรายงานของคุณ!  

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญคุณลักษณะ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโปรเจกต์ของคุณ.

- [วิธีสร้างแผนภูมิคอลัมน์โดยใช้ Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [วิธีบันทึกเอกสารเป็น pdf ด้วย Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [ตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูลในแผนภูมิ](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}