---
date: 2026-10-17
description: เรียนรู้วิธีเปลี่ยนเส้นขอบในเซลล์ตารางด้วย Aspose.Words for Java รวมถึงการตั้งค่า
  cell border styles, การใช้ first column style, และ auto‑fit table contents.
keywords:
- how to change borders
- apply first column style
- Aspose.Words table styling
- Java document processing
lastmod: 2026-10-17
linktitle: วิธีเปลี่ยนเส้นขอบในเซลล์ตารางโดยใช้ Aspose.Words for Java
og_description: วิธีเปลี่ยนเส้นขอบในเซลล์ตารางโดยใช้ Aspose.Words for Java. คู่มือนี้แสดงวิธีตั้งค่า
  cell border thickness, ใช้ first column style, และ auto‑fit tables สำหรับเอกสารระดับมืออาชีพ.
og_image_alt: Screenshot of a Java table with customized cell borders using Aspose.Words
og_title: วิธีเปลี่ยนเส้นขอบในเซลล์ตาราง – Aspose.Words for Java
schemas:
- author: Aspose
  dateModified: '2026-10-17'
  description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  headline: How to change borders in table cells using Aspose.Words for Java
  type: TechArticle
- description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  name: How to change borders in table cells using Aspose.Words for Java
  steps:
  - name: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
    text: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
    text: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
  - name: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
    text: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
  type: HowTo
- questions:
  - answer: Yes, you can create and apply custom styles programmatically. See the
      [Aspose.Words documentation](https://reference.aspose.com/words/java/) for details.
    question: Can I use custom table styles not included in the default options?
  - answer: Use standard Java logic to inspect cell values, then call the appropriate
      formatting methods (e.g., change background colour if a value exceeds a threshold).
    question: How can I apply conditional formatting to cells?
  - answer: Absolutely. After merging cells, apply shading or borders using the same
      `CellFormat` APIs.
    question: Is it possible to format merged cells the same way as regular cells?
  - answer: Adjust column widths or call `autoFit` again after inserting new data
      to recalculate the layout.
    question: What if I need the table to resize dynamically based on user input?
  - answer: The official [Aspose.Words API documentation](https://reference.aspose.com/words/java/)
      contains a comprehensive set of samples.
    question: Where can I find more examples of table styling?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- Aspose.Words
- Java tables
- document formatting
- border styling
title: วิธีเปลี่ยนเส้นขอบในเซลล์ตารางโดยใช้ Aspose.Words for Java
url: /th/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเปลี่ยนเส้นขอบในเซลล์ของตารางโดยใช้ Aspose.Words for Java

## บทนำ

เมื่อคุณต้องการนำเสนอข้อมูลในรูปแบบที่สะอาดและเป็นมืออาชีพ, **การเปลี่ยนเส้นขอบของเซลล์** เป็นหนึ่งในการปรับแต่งภาพแรกที่คุณจะใช้. ใน Java, Aspose.Words มอบ API ที่ครบถ้วนซึ่งช่วยให้คุณจัดรูปแบบตาราง, ปรับเส้นขอบของเซลล์แต่ละเซลล์, เปิดใช้งานสไตล์คอลัมน์แรก, และปรับขนาดอัตโนมัติเพื่อให้เนื้อหาไม่ทำให้ตารางล้นหน้า. บทเรียนนี้จะพาคุณผ่านทุกขั้นตอน, ตั้งแต่การสร้างเอกสารจนถึงการปรับแต่งเส้นขอบแต่ละเส้น, และแสดงว่าฟีเจอร์เหล่านี้สำคัญอย่างไรในรายงานและใบแจ้งหนี้จริง.

## คำตอบอย่างรวดเร็ว
คลาส `DocumentBuilder` ถูกใช้เพื่อสร้างเอกสารและตารางโดยโปรแกรม.  
- **คลาสหลักสำหรับสร้างตารางคืออะไร?** `DocumentBuilder` สร้างตารางและเซลล์โดยโปรแกรม.  
- **ฉันจะเปลี่ยนความหนาของเส้นขอบเซลล์เดียวได้อย่างไร?** ใช้ `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **ฉันสามารถใช้สไตล์ตารางที่กำหนดไว้ล่วงหน้าได้หรือไม่?** ใช่ – เรียก `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **เมธอดใดที่ปรับขนาดตารางให้พอดีกับเนื้อหา?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **ฉันต้องการไลเซนส์สำหรับการใช้งานจริงหรือไม่?** จำเป็นต้องมีไลเซนส์ Aspose.Words ที่ถูกต้องสำหรับการใช้งานที่ไม่ใช่รุ่นทดลอง.

## “วิธีเปลี่ยนเส้นขอบของเซลล์” ใน Aspose.Words คืออะไร
การเปลี่ยนเส้นขอบของเซลล์หมายถึงการปรับแต่งเส้นภาพที่แยกเซลล์—สี, ความกว้าง, และรูปแบบเส้น. Aspose.Words for Java เปิดเผย API รายละเอียดที่ให้คุณตั้งค่าคุณสมบัติเหล่านี้ที่ระดับตาราง, แถว, หรือเซลล์แต่ละเซลล์, ให้คุณควบคุมรูปลักษณ์ของเอกสารได้อย่างแม่นยำ.

## ทำไมต้องใช้การจัดรูปแบบตารางของ Aspose.Words for Java
Aspose.Words รองรับ **รูปแบบการนำเข้าและส่งออกกว่า 35 แบบ** (DOCX, PDF, HTML, ODT, ฯลฯ) และสามารถประมวลผล **เอกสาร 500 หน้าในเวลาน้อยกว่า 3 วินาที** บนฮาร์ดแวร์เซิร์ฟเวอร์ทั่วไปโดยไม่ต้องใช้ Microsoft Word. ไลบรารีทำงานอย่างสม่ำเสมอบน Windows, Linux, และ macOS, ทำให้คุณสามารถสร้างหรือแก้ไขเอกสารบนเซิร์ฟเวอร์, ใช้สไตล์ตารางที่มีอยู่เช่น *สไตล์คอลัมน์แรก*, และปรับขนาดตารางอัตโนมัติเพื่อให้เข้ากับเนื้อหาได้ด้วยการเรียกเมธอดเดียว.

## ข้อกำหนดเบื้องต้น

1. **Java Development Kit (JDK) 8+** – ตรวจสอบให้แน่ใจว่า `java` อยู่ใน PATH ของคุณ.  
2. **IDE** – IntelliJ IDEA, Eclipse, หรือโปรแกรมแก้ไขใด ๆ ที่คุณชอบ.  
3. **Aspose.Words for Java** – ดาวน์โหลด JAR ล่าสุดจาก [official site](https://releases.aspose.com/words/java/).  
4. **Basic Java knowledge** – คุณควรคุ้นเคยกับการสร้างโปรเจกต์ Maven/Gradle และการเพิ่ม JAR ภายนอก.

## นำเข้าแพ็กเกจ

`Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` และคลาสที่เกี่ยวข้องอยู่ในเนมสเปซ `com.aspose.words`. การนำเข้าแพ็กเกจเดียวนี้ทำให้คุณเข้าถึงชุดเครื่องมือการจัดรูปแบบตารางทั้งหมด. คลาส `DocumentBuilder` มีเมธอดสำหรับสร้างและแก้ไขเอกสารโดยโปรแกรม.

```java
import com.aspose.words.*;
```

## วิธีเปลี่ยนเส้นขอบของเซลล์

ด้านล่างเป็นคู่มือสั้น ๆ แบบขั้นตอนที่สร้างตาราง, ตั้งค่าเส้นขอบทั่วทั้งตาราง, แล้วปรับแต่งขอบของเซลล์เดียว.

### คำตอบโดยตรง
`Document` แทนไฟล์ Word, ส่วน `DocumentBuilder` สร้างเนื้อหาเช่นตาราง. โหลด `Document` ใหม่, แทรก `Table` ด้วย `DocumentBuilder`, ตั้งค่าเส้นขอบสีดำ 2‑point สำหรับตารางทั้งหมด, แล้วเพิ่มเส้นขอบซ้าย, ขวา, บน, และล่างของเซลล์ที่สามเป็น 4 point. วิธีนี้ทำให้คุณเน้นเซลล์ใดก็ได้ในขณะที่ตารางส่วนอื่นยังคงมีสไตล์เดียวกัน.

### ขั้นตอนที่ 1: โหลดเอกสารใหม่

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### ขั้นตอนที่ 2: สร้างตารางและตั้งค่าเส้นขอบทั่วทั้งตาราง

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### ขั้นตอนที่ 3: เปลี่ยนเส้นขอบของเซลล์เดียว

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### สิ่งที่โค้ดทำ
- **เส้นขอบทั่วทั้งตาราง** – `table.setBorders` ให้ตารางทั้งหมดมีเส้นสีดำ 2‑point.  
- **การระบายสีเซลล์** – แสดงวิธีการใส่สีให้เซลล์แต่ละเซลล์ (สีแดงและสีเขียว).  
- **เส้นขอบเซลล์แบบกำหนดเอง** – เซลล์ที่สามได้รับเส้นขอบ 4‑point ทั้งสี่ด้าน ทำให้โดดเด่น.

## การใช้สไตล์ตาราง (รวมถึงสไตล์คอลัมน์แรก)

สไตล์ตารางช่วยให้คุณใช้รูปลักษณ์ที่สอดคล้องด้วยการเรียกครั้งเดียว. เราจะเปิดใช้งาน *สไตล์คอลัมน์แรก* และปรับขนาดตารางอัตโนมัติเพื่อให้เข้ากับเนื้อหา.

### คำตอบโดยตรง
`StyleIdentifier` แสดงรายการสไตล์ตารางที่มีอยู่, และ `AutoFitBehavior` ควบคุมว่าตารางปรับตามเนื้อหาอย่างไร. สร้าง `Document` ใหม่, สร้าง `Table`, ตั้งค่า `StyleIdentifier` เป็น `MEDIUM_SHADING_1_ACCENT_1`, เปิดใช้งาน `FirstColumn` และ `RowBands`, แล้วเรียก `autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` เพื่อให้คอลัมน์หดหรือขยายอัตโนมัติเพื่อให้เข้ากับข้อมูลที่แทรก.

### ขั้นตอนที่ 4: สร้างเอกสารใหม่สำหรับการจัดสไตล์

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### ขั้นตอนที่ 5: ใช้สไตล์ที่กำหนดไว้ล่วงหน้าและเปิดใช้งานการจัดรูปแบบคอลัมน์แรก

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### ขั้นตอนที่ 6: เติมข้อมูลลงในตาราง

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### ทำไมเรื่องนี้สำคัญ
- **ตัวระบุสไตล์** – `MEDIUM_SHADING_1_ACCENT_1` ทำให้ตารางดูสะอาดและมีเงา.  
- **สไตล์คอลัมน์แรก** – การเน้นคอลัมน์แรกช่วยเพิ่มความอ่านง่าย, โดยเฉพาะในรายงาน.  
- **แถบแถว** – การสลับสีแถวทำให้ตารางขนาดใหญ่อ่านสบายตาขึ้น.  
- **ปรับขนาดอัตโนมัติ** – ทำให้ความกว้างของตารางปรับตามเนื้อหา, ป้องกันข้อความถูกตัด.

## ปัญหาทั่วไปและการแก้ไขข้อผิดพลาด

| ปัญหา | สาเหตุทั่วไป | วิธีแก้เร็ว |
|-------|----------------|-----------|
| เส้นขอบไม่แสดง | ใช้ `clearFormatting()` หลังจากตั้งค่าเส้นขอบ | ตั้งค่าเส้นขอบ **หลังจาก** ล้างการจัดรูปแบบ, หรือกำหนดใหม่. |
| การระบายสีถูกละเว้นบนเซลล์ที่รวม | ระบายสีก่อนการรวม | ระบายสี **หลังจาก** การรวมเซลล์. |
| ความกว้างของตารางเกินขอบหน้ากระดาษ | ไม่มีการปรับขนาดอัตโนมัติ | เรียก `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` หรือกำหนดความกว้างคงที่. |
| สไตล์ไม่ถูกนำไปใช้ | ค่า `StyleIdentifier` ไม่ถูกต้อง | ตรวจสอบว่าตัวระบุมีอยู่ในเวอร์ชันของ Aspose.Words ที่คุณใช้. |

## คำถามที่พบบ่อย

**Q: ฉันสามารถใช้สไตล์ตารางที่กำหนดเองซึ่งไม่ได้รวมอยู่ในตัวเลือกเริ่มต้นได้หรือไม่?**  
A: ใช่, คุณสามารถสร้างและใช้สไตล์ที่กำหนดเองโดยโปรแกรม. ดูที่ [Aspose.Words documentation](https://reference.aspose.com/words/java/) สำหรับรายละเอียด.

**Q: ฉันจะใช้การจัดรูปแบบตามเงื่อนไขกับเซลล์ได้อย่างไร?**  
A: ใช้ตรรกะ Java มาตรฐานเพื่อตรวจสอบค่าของเซลล์, จากนั้นเรียกเมธอดการจัดรูปแบบที่เหมาะสม (เช่น เปลี่ยนสีพื้นหลังหากค่ามากกว่าขีดจำกัด).

**Q: สามารถจัดรูปแบบเซลล์ที่รวมได้เช่นเดียวกับเซลล์ปกติหรือไม่?**  
A: แน่นอน. หลังจากรวมเซลล์, ให้ใช้ `CellFormat` API เดียวกันเพื่อระบายสีหรือกำหนดเส้นขอบ.

**Q: ถ้าฉันต้องการให้ตารางปรับขนาดตามการป้อนข้อมูลของผู้ใช้จะทำอย่างไร?**  
A: ปรับความกว้างของคอลัมน์หรือเรียก `autoFit` อีกครั้งหลังจากแทรกข้อมูลใหม่เพื่อคำนวณเลย์เอาต์ใหม่.

**Q: ฉันจะหา ตัวอย่างการจัดรูปแบบตารางเพิ่มเติมได้จากที่ไหน?**  
A: [Aspose.Words API documentation](https://reference.aspose.com/words/java/) มีชุดตัวอย่างที่ครอบคลุมอย่างครบถ้วน.

## สรุป

ตอนนี้คุณมีชุดเครื่องมือครบถ้วนสำหรับ **วิธีเปลี่ยนเส้นขอบ** ในเซลล์ของตาราง, ใช้ *สไตล์คอลัมน์แรก*, และ **ปรับขนาดตารางอัตโนมัติ** ด้วย Aspose.Words for Java. ด้วยการเชี่ยวชาญเทคนิคเหล่านี้คุณสามารถสร้างเอกสารที่เต็มไปด้วยข้อมูลและดูสวยงาม—เหมาะสำหรับรายงาน, ใบแจ้งหนี้, และผลลัพธ์ที่สำคัญต่อธุรกิจใด ๆ.

---

**อัปเดตล่าสุด:** 2026-10-17  
**ทดสอบด้วย:** Aspose.Words for Java 24.12 (latest at time of writing)  
**ผู้เขียน:** Aspose

## บทเรียนที่เกี่ยวข้อง

- [บทแนะนำการจัดรูปแบบและสไตล์ Aspose.Words Java - ปรับปรุงเอกสารของคุณ](/words/java/formatting-styles/)
- [ขอบเอกสารขั้นสูงด้วย Aspose.Words for Java: คู่มือฉบับสมบูรณ์](/words/java/headers-footers-page-setup/advanced-document-borders-aspose-words-java/)
- [เพิ่มลายน้ำให้กับเอกสารโดยใช้ Aspose.Words for Java](/words/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}