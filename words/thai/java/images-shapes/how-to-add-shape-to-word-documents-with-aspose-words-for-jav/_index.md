---
category: general
date: 2026-11-22
description: เรียนรู้วิธีเพิ่มรูปทรงใน Word ด้วย Aspose.Words for Java – แทรกสี่เหลี่ยมผืนผ้าและซ่อนโดยโปรแกรม
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: th
lastmod: 2026-11-22
og_description: เพิ่มรูปร่างใน Word ด้วย Aspose.Words for Java. บทแนะนำนี้แสดงวิธีแทรกสี่เหลี่ยม,
  ซ่อนรูปร่าง, และบันทึกเอกสาร.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: เพิ่มรูปร่างใน Word ด้วย Aspose.Words – คู่มือ Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: วิธีเพิ่มรูปทรงในเอกสาร Word ด้วย Aspose.Words สำหรับ Java
url: /th/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มรูปทรงในเอกสาร Word ด้วย Aspose.Words for Java

หากคุณต้องการ **เพิ่มรูปทรงใน Word** เอกสารโดยโปรแกรม, Aspose.Words for Java ทำให้เป็นเรื่องง่าย ในคู่มือนี้คุณจะได้เรียนรู้ **วิธีแทรกรูปทรง**, ควบคุมการมองเห็น, และ **วิธีซ่อนรูปทรง** เพื่อให้ไฟล์สุดท้ายดูตรงตามที่คุณคาดหวัง

คุณจะได้ทำตามตัวอย่างที่สมบูรณ์และสามารถรันได้ ซึ่งโหลดไฟล์ `.docx` ที่มีอยู่, แทรกสี่เหลี่ยม, ซ่อนมัน, แล้วบันทึกผลลัพธ์ ไม่ต้องใช้สคริปต์ภายนอกหรือขั้นตอนด้วยมือใด ๆ และบทเรียนนี้ครอบคลุมการเปลี่ยนแปลงทั่วไป เช่น การสร้างเอกสารใหม่จากศูนย์หรือการซ่อนรูปทรงเฉพาะเมื่อพิมพ์

## ข้อกำหนดเบื้องต้น

* Java 17 (หรือใหม่กว่า) ที่ติดตั้งแล้ว – เวอร์ชันเก่าก็ทำงานได้แต่ LTS ล่าสุดให้ประสิทธิภาพที่ดีกว่า  
* Maven 3.8+ สำหรับการจัดการ dependencies  
* ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (รุ่นทดลองฟรีใช้สำหรับการเรียนรู้)  
* IDE หรือโปรแกรมแก้ไขข้อความที่คุณชอบ (เช่น IntelliJ IDEA, VS Code)

## ขั้นตอนที่ 1: เพิ่ม Aspose.Words ไปยังโครงการ Maven ของคุณ

เพิ่ม dependency ต่อไปนี้ในไฟล์ `pom.xml` ของคุณ ซึ่งจะดึงเวอร์ชันเสถียรล่าสุด (ณ พฤศจิกายน 2026)

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **เคล็ดลับระดับมืออาชีพ:** ใช้แท็ก `<scope>provided</scope>` หากคุณวางแผนจะจัดจำหน่าย JAR พร้อมตรรกะการให้ลิขสิทธิ์ของคุณเอง

## เพิ่มรูปทรงใน Word – การเริ่มต้นเอกสาร

ขั้นตอนการทำงานแรกคือการได้มาซึ่งอ็อบเจ็กต์ `Document` คุณสามารถโหลดไฟล์ที่มีอยู่หรือสร้างไฟล์ใหม่ได้

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Why this matters*: คลาส `Document` เป็นจุดเริ่มต้นสำหรับการจัดการ Word ทั้งหมด การโหลดไฟล์ที่มีอยู่จะคงสไตล์, ส่วนหัว, และส่วนท้ายไว้ ในขณะที่เอกสารใหม่จะให้พื้นที่ว่างเปล่าสำหรับคุณ

## วิธีแทรกรูปทรงในเอกสาร Word

ต่อไป, สร้าง `DocumentBuilder` เพื่อแก้ไขเนื้อหาในเอกสาร Builder จะให้เมธอดสำหรับแทรกข้อความ, ตาราง, และ **shapes**  

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

เมธอด `insertShape` จะคืนค่าอ็อบเจ็กต์ `Shape` ที่คุณสามารถกำหนดค่าเพิ่มเติม (สี, เส้นขอบ, ข้อความ ฯลฯ) ขนาดจะระบุเป็นจุด (1 pt = 1/72 in)

*Why you might use a rectangle*: สี่เหลี่ยมเป็นคอนเทนเนอร์ที่ใช้บ่อยที่สุดสำหรับคำอธิบาย, ลายน้ำ, หรือที่วางตัวคุณสามารถเปลี่ยน `ShapeType.RECTANGLE` เป็น `ShapeType.ELLIPSE`, `ShapeType.LINE` เป็นต้น เพื่อให้ตรงกับความต้องการด้านภาพต่าง ๆ

## วิธีซ่อนรูปทรงใน Word

บางครั้งคุณต้องการให้รูปทรงอยู่เพื่อคำนวณเลย์เอาต์แต่ไม่ต้องการให้แสดงผลในขั้นสุดท้าย Aspose.Words มีเมธอด `setHidden(true)` เพื่อทำเช่นนี้

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

แฟล็ก hidden ทำงานคล้ายกับตัวเลือกการฟอร์แมต **Hidden** ใน Microsoft Word: รูปทรงจะไม่แสดงในเลย์เอาต์ภาพแต่ยังคงเป็นส่วนหนึ่งของโมเดลอ็อบเจ็กต์ของเอกสาร ซึ่งมีประโยชน์สำหรับ:

* การเก็บ metadata หรือเครื่องหมายที่แอปพลิเคชันของคุณจะอ่านในภายหลัง  
* การสร้างที่วางตัวที่ถูกลบก่อนการเผยแพร่  
* การควบคุมการมองเห็นสำหรับรูปแบบผลลัพธ์ต่าง ๆ (เช่น ซ่อนใน HTML แต่คงไว้ใน PDF)

> **หมายเหตุ:** รูปทรงที่ซ่อนอยู่ยังคงถูกส่งออกเป็น PDF โดยค่าเริ่มต้น หากคุณต้องการให้ไม่รวมใน PDF ด้วย ให้ตั้งค่า `rectangle.getWrapType( ) = WrapType.NONE` และปรับคุณสมบัติ `Hidden` ตามที่ต้องการ

## ขั้นตอนที่ 4: บันทึกเอกสารที่แก้ไข

สุดท้าย, บันทึกการเปลี่ยนแปลงลงไฟล์ใหม่

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

เมื่อคุณเปิด `output.docx` ใน Microsoft Word, สี่เหลี่ยมจะไม่ปรากฏให้เห็น แต่ยังคงเป็นส่วนหนึ่งของโครงสร้างเอกสาร คุณสามารถตรวจสอบการมีอยู่ของมันโดยโปรแกรมได้โดยโหลดไฟล์ใหม่และตรวจสอบ `Shape.isHidden()`

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ `output.docx` เปิดโดยไม่มีรูปทรงที่มองเห็นได้  
* หากคุณตรวจสอบเอกสารด้วย Aspose.Words (เช่น `doc.getChildNodes(NodeType.SHAPE, true).size()`), จำนวนรูปทรงจะเป็น **1**, ยืนยันว่ารูปทรงมีอยู่แต่ถูกซ่อน

## ความหลากหลายขั้นสูงและกรณีขอบ

### 1. การสร้างรูปทรงในเอกสารใหม่

หากคุณเริ่มจากศูนย์, แทนบรรทัดการโหลดด้วย:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. การกำหนดตำแหน่งรูปทรงอย่างแม่นยำ

โดยค่าเริ่มต้น, `insertShape` จะวางรูปทรงที่ตำแหน่งเคอร์เซอร์ปัจจุบัน เพื่อกำหนดตำแหน่งแบบแน่นอน:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. การควบคุมการมองเห็นตามรูปแบบผลลัพธ์

หากคุณต้องการให้รูปทรงมองเห็นได้ใน UI ของ Word แต่ซ่อนเมื่อส่งออกเป็น PDF, ใช้ `Shape.setWrapType(WrapType.NONE)` ร่วมกับ `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. การเพิ่มข้อความภายในรูปทรง

สี่เหลี่ยมสามารถบรรจุ text frame ได้:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

จากนั้นคุณสามารถซ่อนกล่องข้อความด้วยการเรียก `setHidden(true)` เดียวกัน

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| Symptom | Cause | Fix |
|---------|-------|-----|
| รูปทรงยังปรากฏหลังจาก `setHidden(true)` | เอกสารถูกบันทึกก่อนที่แฟล็ก hidden จะถูกตั้งค่า | ตรวจสอบให้แน่ใจว่าคุณเรียก `setHidden(true)` **ก่อน** `doc.save()` |
| ขนาดรูปทรงดูบิดเบี้ยว | สับสนระหว่าง points กับ pixels บนหน้าจอ DPI สูง | ใช้ points (72 pt = 1 in) เพื่อให้ขนาดคงที่บนทุกแพลตฟอร์ม |
| รูปทรงที่ซ่อนยังพิมพ์ออกมา | เครื่องพิมพ์บางรุ่นไม่สนใจแฟล็ก hidden | ตั้งค่า `Shape.setWrapType(WrapType.NONE)` และยังต้องล้าง `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)` |

## สรุป

ตอนนี้คุณรู้วิธี **เพิ่มรูปทรงใน Word** ด้วย Aspose.Words for Java, **วิธีแทรกรูปทรง**, และ **วิธีซ่อนรูปทรง** เพื่อให้มันไม่ปรากฏต่อผู้ใช้สุดท้ายแต่ยังคงเป็นส่วนหนึ่งของโครงสร้างเอกสาร ตัวอย่างเต็มที่ให้ด้านบนโหลดไฟล์, แทรกสี่เหลี่ยม, ซ่อนมัน, แล้วบันทึกผลลัพธ์ ครอบคลุมทั้งกรณีการใช้งานทั่วไปและหลายกรณีขอบ

จากนี้คุณสามารถสำรวจหัวข้อที่เกี่ยวข้อง เช่น **วิธีแทรกรูปทรง** ด้วยสีเติมแบบกำหนดเอง, **วิธีซ่อนรูปทรงใน Word** สำหรับการพิมพ์ตามเงื่อนไข, หรือการทำอัตโนมัติการประมวลผลเอกสารจำนวนมากด้วย Aspose.Words ทดลองใช้ค่า `ShapeType` ต่าง ๆ, ตัวเลือกการวางตำแหน่ง, และแฟล็กการมองเห็นเพื่อให้เข้ากับกระบวนการทำงานของคุณ

ขอให้เขียนโค้ดอย่างสนุกและเพลิดเพลินกับความยืดหยุ่นที่การจัดการ Word ด้วยโปรแกรมมิ่งนำมาสู่แอปพลิเคชัน Java ของคุณ!

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณเอง

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}