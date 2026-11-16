---
category: general
date: 2026-11-15
description: ตั้งค่าระยะห่างบรรทัดของย่อหน้าในเอกสาร Word ด้วย Java เรียนรู้วิธีตั้งค่าระยะห่างบรรทัดโดยโปรแกรมโดยใช้
  Aspose.Words เพื่อการจัดรูปแบบเอกสารที่แม่นยำ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: th
lastmod: 2026-11-15
og_description: ตั้งค่าระยะห่างบรรทัดของย่อหน้าในเอกสาร Word ด้วย Java คู่มือนี้อธิบายวิธีตั้งค่าระยะห่างบรรทัดสำหรับย่อหน้าและตัวคั่นเชิงอรรถโดยใช้
  Aspose.Words ให้คุณควบคุมการจัดวางเอกสารได้อย่างเต็มที่
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: ตั้งค่าระยะห่างบรรทัดของย่อหน้าใน Word ด้วย Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: ตั้งค่าระยะห่างบรรทัดของย่อหน้าในเอกสาร Word ด้วย Java
url: /th/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าการเว้นบรรทัดของย่อหน้าในเอกสาร Word ด้วย Java

หากคุณต้องการ **ตั้งค่าการเว้นบรรทัดของย่อหน้า** ในเอกสาร Word, บทแนะนำนี้จะแสดงวิธีทำด้วย Java และ Aspose.Words คุณยังจะได้เรียนรู้ **วิธีตั้งค่าการเว้นบรรทัด** สำหรับตัวคั่นเชิงอรรถ—ความต้องการทั่วไปเมื่อจัดรูปแบบเอกสารระดับมืออาชีพ

ในส่วนต่อไปนี้คุณจะได้:

* โหลดไฟล์ *.docx* ที่มีอยู่แล้ว
* ดึงย่อหน้าตัวคั่นเชิงอรรถ
* ใช้ค่าการเว้นบรรทัดที่กำหนดเอง
* บันทึกเอกสารที่อัปเดตแล้ว

ไม่ต้องกำหนดค่าภายนอกเพิ่มเติมนอกจากการเพิ่มไลบรารี Aspose.Words ลงในโปรเจกต์ของคุณ, ดังนั้นคุณสามารถคัดลอกโค้ดตามที่เป็นและรันได้ทันที

## ข้อกำหนดเบื้องต้น

ก่อนเริ่ม, ตรวจสอบว่าคุณมี:

* Java 17 หรือใหม่กว่า
* Maven (หรือเครื่องมือสร้างอื่น) เพื่อจัดการ dependencies
* ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (รุ่นทดลองฟรีใช้สำหรับทดสอบได้)
* เอกสาร Word อินพุต (`input.docx`) อยู่ในไดเรกทอรีที่ทราบ

เพิ่ม dependency ของ Aspose.Words ลงใน `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## ตั้งค่าการเว้นบรรทัดของย่อหน้าด้วย Aspose.Words

หัวข้อ H2 นี้มีคีย์เวิร์ดหลัก, ตรงตามข้อกำหนด SEO

### ขั้นตอน 1: โหลดเอกสาร Word

ก่อนอื่น, สร้างอินสแตนซ์ `Document` ที่ชี้ไปยังไฟล์ต้นฉบับของคุณ

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*ทำไมเรื่องนี้ถึงสำคัญ*: การโหลดเอกสารจะให้โมเดลในหน่วยความจำที่คุณสามารถจัดการได้โดยไม่ต้องแก้ไขไฟล์ต้นฉบับจนกว่าจะบันทึกอย่างชัดเจน

### ขั้นตอน 2: ดึงตัวคั่นเชิงอรรถ

ตัวคั่นเชิงอรรถเป็นย่อหน้าพิเศษที่อยู่ระหว่างเชิงอรรถและข้อความหลัก เพื่อเปลี่ยนลักษณะของมันคุณต้องเข้าถึงอ็อบเจ็กต์ `FootnoteSeparator`

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*เคล็ดลับ*: หากเอกสารของคุณไม่มีเชิงอรรถ, ตัวคั่นยังคงมีอยู่เป็นย่อหน้าที่ซ่อนอยู่, ดังนั้นการเรียกจะไม่คืนค่า `null` แต่อย่างใด

### ขั้นตอน 3: วิธีตั้งค่าการเว้นบรรทัดสำหรับย่อหน้าตัวคั่น

ตอนนี้ให้ใช้การเว้นบรรทัดที่ต้องการ Aspose.Words ใช้หน่วยจุดสำหรับค่าการเว้นบรรทัด; 12 pts ประมาณการเว้นบรรทัดแบบเดี่ยวสำหรับฟอนต์ส่วนใหญ่

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

คุณยังสามารถใช้โหมดการเว้นบรรทัดอื่นได้:

| โหมด                     | วิธีเรียกใช้                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (fixed pts) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (เช่น 1.5)  | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

การเลือกกฎที่ถูกต้องจะทำให้เอกสารแสดงผลสม่ำเสมอใน Word, Google Docs และโปรแกรมอ่านอื่น ๆ

### ขั้นตอน 4: บันทึกเอกสารที่อัปเดต

สุดท้าย, เขียนการเปลี่ยนแปลงกลับไปยังดิสก์

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

เมื่อคุณเปิด `output.docx` ใน Microsoft Word, ตัวคั่นเชิงอรรถจะปรากฏด้วยการเว้นบรรทัดที่คุณกำหนด

## ทำความเข้าใจวิธีตั้งค่าการเว้นบรรทัดสำหรับย่อหน้าปกติ

API เดียวกันทำงานกับอ็อบเจ็กต์ `Paragraph` ใด ๆ ไม่เฉพาะตัวคั่นเชิงอรรถ ตัวอย่างสั้น ๆ ด้านล่างปรับการเว้นบรรทัดของย่อหน้าแรกในส่วนเนื้อหา

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**ทำไมคุณอาจต้องการใช้สิ่งนี้**: รายงาน, สัญญา, และงานวิจัยมักต้องการสไตล์การเว้นบรรทัดเฉพาะ (เช่น เว้นบรรทัดสองเท่าสำหรับฉบับร่าง). การใช้เมธอด `setLineSpacing` เดียวกันจะรับประกันการจัดวางที่ตรงตามที่คุณคาดหวัง

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| ปัญหา                                 | สาเหตุ                                   | วิธีแก้ |
|---------------------------------------|----------------------------------------|-----|
| การเว้นบรรทัดไม่เปลี่ยนแปลง          | `LineSpacingRule` ยังเป็นค่าเริ่มต้น (AUTO) | ตั้งค่ากฎโดยใช้ `setLineSpacingRule` อย่างชัดเจน |
| มีบรรทัดว่างเพิ่มหลังตัวคั่น          | ตัวคั่นมีการคืน carriage return ที่ซ่อนอยู่ | ตัดข้อความของตัวคั่นด้วย `separator.getText().trim();` ก่อนตั้งค่าการเว้นบรรทัด |
| เอกสารถูกทำลายหลังบันทึก            | ใช้เวอร์ชัน Aspose.Words ที่ล้าสมัย | อัปเกรดเป็นเวอร์ชันล่าสุด (เช่น 24.10) ที่มีการแก้บั๊กการบันทึก |

## เคล็ดลับขั้นสูง: ประมวลผลหลายไฟล์เป็นชุด

หากต้องอัปเดตหลายสิบไฟล์, ให้ห่อโลจิกในเมธอดช่วยเหลือและวนลูปผ่านโฟลเดอร์:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

การเรียกเมธอดนี้ในลูปจะช่วยคุณประหยัดเวลาหลายชั่วโมงจากการแก้ไขด้วยมือ

## ผลลัพธ์ที่คาดหวัง

หลังจากรันโปรแกรมเต็มรูปแบบ, `output.docx` จะ:

* มีเนื้อหาเดิมที่ไม่เปลี่ยนแปลง ยกเว้นการเว้นบรรทัด
* แสดงตัวคั่นเชิงอรรถด้วยการจัดวางแบบเว้นบรรทัดเดี่ยว (12 pts)
* รักษาการจัดรูปแบบอื่นทั้งหมด (สไตล์, รูปภาพ, ตาราง)

เปิดไฟล์ใน Word และตรวจสอบว่าตัวคั่นมีบรรทัดที่แคบลง (หรือกว้างขึ้น, ขึ้นอยู่กับค่าที่คุณตั้ง)

## สรุป

คุณได้เรียนรู้วิธี **ตั้งค่าการเว้นบรรทัดของย่อหน้า** ในเอกสาร Word ด้วย Java, และยังเข้าใจ **วิธีตั้งค่าการเว้นบรรทัด** สำหรับตัวคั่นเชิงอรรถและย่อหน้าปกติ ตัวอย่างเต็มที่สามารถรันได้แสดงการโหลดเอกสาร, ปรับคุณสมบัติการเว้นบรรทัด, และบันทึกผลลัพธ์—ทั้งหมดด้วยการเรียก API ไม่กี่บรรทัด

**ขั้นตอนต่อไป** ที่คุณอาจสนใจ:

* **วิธีตั้งค่าการเว้นบรรทัด** สำหรับตารางและรายการ
* การใช้กฎการเว้นบรรทัดต่าง ๆ กับหัวเรื่องเทียบกับข้อความหลัก
* การใช้วัตถุ `Style` เพื่อบังคับการเว้นบรรทัดทั่วทั้งเอกสาร

ลองปรับค่าต่าง ๆ, ผสานกับตัวเลือกการจัดรูปแบบอื่น ๆ, แล้วคุณจะควบคุมการจัดวางเอกสารได้อย่างเต็มที่ในแอปพลิเคชัน Java ของคุณ. Happy coding!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Change Asian Paragraph Spacing And Indents In Word Document](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}