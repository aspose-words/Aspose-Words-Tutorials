---
category: general
date: 2026-11-15
description: แก้ไขเอกสาร Word ด้วยโปรแกรมเพื่อแทรกปุ่มคำสั่ง เรียนรู้วิธีเพิ่มปุ่ม
  ตั้งชื่อปุ่มคำสั่ง และสร้างปุ่มฟอร์มใน Word ภายในไม่กี่นาที.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: th
lastmod: 2026-11-15
og_description: แก้ไขเอกสาร Word ด้วยโปรแกรมและแทรกปุ่มคำสั่ง คู่มือนี้แสดงวิธีเพิ่มปุ่ม
  ตั้งชื่อปุ่มคำสั่ง และสร้างปุ่มฟอร์มใน Word อย่างรวดเร็ว.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: แก้ไขเอกสาร Word โดยใช้โค้ด – เพิ่มปุ่มคำสั่ง
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: แก้ไขเอกสาร Word ด้วยโปรแกรมและเพิ่มปุ่มคำสั่ง
url: /th/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แก้ไขเอกสาร Word ด้วยโปรแกรมและเพิ่มปุ่มคำสั่ง

หากคุณต้องการ **แก้ไขเอกสาร Word ด้วยโปรแกรม** วิธีที่เร็วที่สุดคือใช้ Aspose.Words API บทเรียนนี้จะแสดงให้คุณเห็น **วิธีเพิ่มปุ่ม** ควบคุม, ตั้งค่าคำบรรยายของมัน, และ **ตั้งชื่อปุ่มคำสั่ง** เพื่อให้เอกสารทำหน้าที่เป็นฟอร์มง่าย ๆ เมื่อเสร็จแล้วคุณจะได้ไฟล์ *.docx* ที่สามารถแก้ไขได้เต็มรูปแบบซึ่งมีปุ่มคำสั่งทำงานพร้อมสำหรับการประมวลผลต่อไป

คุณจะได้เรียนรู้ **การแทรกคำสั่งปุ่ม** , **การสร้างคำปุ่มฟอร์ม** และการจัดการคุณสมบัติปุ่มโดยไม่ต้องเปิด Word ด้วยตนเอง สิ่งที่ต้องมีคือสภาพแวดล้อมการพัฒนา Java ขั้นพื้นฐานและไลบรารี Aspose.Words for Java

## ข้อกำหนดเบื้องต้น

- Java 17 หรือใหม่กว่า (โค้ดทำงานได้กับ Java 8+ ด้วย)
- Aspose.Words for Java (ดาวน์โหลดจาก [Aspose.Words for Java](https://products.aspose.com/words/java/))
- เอกสาร Word ที่มีอยู่ (`input.docx`) ที่คุณต้องการแก้ไข
- ความคุ้นเคยกับ Maven หรือ Gradle เพื่อเพิ่ม dependency ของ Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## ขั้นตอนที่ 1: โหลดเอกสาร Word

การดำเนินการแรกเมื่อคุณ **แก้ไขเอกสาร Word ด้วยโปรแกรม** คือการโหลดไฟล์ต้นฉบับเข้าสู่วัตถุ `Document` วัตถุนี้แทนไฟล์ Word ทั้งหมดในหน่วยความจำ ทำให้คุณสามารถจัดการเนื้อหาต่าง ๆ ได้

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **ทำไมจึงสำคัญ:** การโหลดเอกสารจะสร้างโครงสร้างคล้าย DOM ที่ Aspose.Words สามารถเดินทางและแก้ไขได้ หากข้ามขั้นตอนนี้คุณจะไม่มีเป้าหมายสำหรับการแทรกปุ่ม

## ขั้นตอนที่ 2: สร้าง `DocumentBuilder` เพื่อแก้ไขเอกสาร

`DocumentBuilder` ทำหน้าที่เหมือนเคอร์เซอร์ภายในไฟล์ Word มันช่วยให้คุณแทรกข้อความ, รูปภาพ, และฟอร์มคอนโทรลได้ที่ตำแหน่งปัจจุบัน

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **เคล็ดลับ:** หากคุณต้องการปุ่มในย่อหน้าที่เฉพาะเจาะจง ให้ย้าย builder ก่อนด้วย `builder.moveToParagraph(index, true);`

## ขั้นตอนที่ 3: แทรก Forms2OleControl (ปุ่มคำสั่ง)

ตอนนี้เราตอบคำถามหลัก **วิธีเพิ่มปุ่ม** ในไฟล์ Word วิธี `insertForms2OleControl()` จะสร้างปุ่มคำสั่ง *Forms2.0* แบบเก่า ซึ่งเป็นคอนโทรลที่เข้ากันได้ดีที่สุดกับหลายเวอร์ชันของ Word

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **กรณีพิเศษ:** คอนโทรล Forms2.0 จะมองเห็นได้เฉพาะใน *Design Mode* ของ Word หากคุณต้องการปุ่ม ActiveX รุ่นใหม่ ให้พิจารณาใช้ `insertOleControl()` แทน แต่คอนโทรลแบบเก่าจะทำงานได้ในหลายสถานการณ์อัตโนมัติ

## ขั้นตอนที่ 4: ตั้งค่าคุณสมบัติของปุ่ม

หลังจากแทรกคอนโทรลแล้ว คุณสามารถ **ตั้งชื่อปุ่มคำสั่ง** และ **แทรกคำสั่งปุ่ม** (คำบรรยาย) เพื่อให้ใช้งานง่ายขึ้น

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **ทำไมต้องตั้งค่าดังกล่าว?**  
> - `setName` ให้ปุ่มมีตัวระบุที่ VBA หรือเครื่องมือภายนอกสามารถอ้างอิงได้  
> - `setCaption` คือป้ายชื่อที่แสดงผล, เป็นการ **สร้างคำปุ่มฟอร์ม** ที่ผู้ใช้คลิกได้

คุณยังสามารถปรับขนาด, ตำแหน่ง, หรือเพิ่มแมโครโดยเข้าถึงอ็อบเจกต์ OLE ด้านล่างได้ แต่หัวข้อเหล่านั้นอยู่นอกขอบเขตของคู่มือสั้นนี้

## ขั้นตอนที่ 5: บันทึกเอกสารที่แก้ไขแล้ว

สุดท้ายให้บันทึกการเปลี่ยนแปลงลงไฟล์ใหม่ ขั้นตอนนี้ **สร้างคำปุ่มฟอร์ม** ในเอกสารผลลัพธ์

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **ผลลัพธ์:** เมื่อเปิด `output.docx` ด้วย Microsoft Word คุณจะเห็นปุ่มที่มีข้อความ “Submit” หากสลับ Word ไปที่ *Design Mode* (Developer → Design Mode) คุณสามารถดับเบิล‑คลิกปุ่มเพื่อแนบแมโครหรือใช้เป็นตัวแทนในฟอร์มได้

### ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิดไฟล์ที่บันทึกไว้:

- จุดแทรกของเคอร์เซอร์จะถูกแทนที่ด้วยปุ่ม
- ปุ่มแสดงคำบรรยาย **Submit**
- ชื่อภายในของปุ่มคือ **cmdSubmit** ซึ่งคุณสามารถอ้างอิงใน VBA หรือสคริปต์อัตโนมัติภายนอกได้

## คำถามที่พบบ่อยและรูปแบบต่าง ๆ

### วิธีเพิ่มปุ่มในย่อหน้าที่กำหนด?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### วิธีแทรกปุ่มภายในเซลล์ตาราง?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### ถ้าต้องการปุ่มขนาดใหญ่ขึ้นทำอย่างไร?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### วิธี **แทรกคำสั่งปุ่ม** ด้วยภาษาที่แตกต่าง (เช่น C#)?

หลักการเดียวกัน; แค่เปลี่ยนไวยากรณ์ Java เป็น C# ที่เทียบเท่า:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## เคล็ดลับระดับมืออาชีพและข้อควรระวัง

- **เคล็ดลับระดับมืออาชีพ:** ควรเรียก `builder.moveToDocumentEnd()` ก่อนแทรกปุ่มหากต้องการให้มันอยู่ที่ส่วนท้ายของเอกสาร  
- **ระวัง:** การบันทึกทับไฟล์เดียวกับที่เปิดอยู่อาจทำให้เอกสารเสียหายหากเกิดข้อยกเว้น ใช้เส้นทางไฟล์ผลลัพธ์แยกต่างหากตามที่แสดง  
- **ความเข้ากันได้:** ปุ่ม Forms2.0 แบบเก่าทำงานใน Word 2007‑2021 สำหรับ Word บนเว็บ ให้พิจารณาใช้คอนเทนต์คอนโทรลแทน  
- **ประสิทธิภาพ:** การโหลดเอกสารขนาดใหญ่มาก (>100 MB) อาจใช้หน่วยความจำสูง ใช้ `Document.load(InputStream, LoadOptions)` พร้อม `LoadOptions.setLoadFormat(LoadFormat.DOCX)` เพื่อลดการใช้ทรัพยากร

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรม Java ที่พร้อมรัน คัดลอกไปยังคลาสชื่อ `WordButtonDemo.java` ปรับเส้นทางไฟล์ตามต้องการ แล้วรัน `mvn compile exec:java`

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

รันโปรแกรมและเปิด `output.docx` เพื่อตรวจสอบว่าปุ่มปรากฏตามที่คาดไว้

## สรุป

คุณได้เรียนรู้วิธี **แก้ไขเอกสาร Word ด้วยโปรแกรม** เพื่อ **แทรกคำสั่งปุ่ม**, **สร้างคำปุ่มฟอร์ม**, และ **ตั้งชื่อปุ่มคำสั่ง** ด้วย Aspose.Words for Java วิธีนี้ช่วยลดการแก้ไขด้วยมือ, ทำให้สามารถประมวลผลฟอร์มเป็นชุดได้, และเชื่อมต่ออย่างราบรื่นกับเวิร์กโฟลว์อัตโนมัติ

ต่อไปคุณอาจสำรวจ:

- การเพิ่มแมโคร VBA ให้กับปุ่ม (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- การใช้ **คอนเทนต์คอนโทรล** เพื่อประสบการณ์ฟอร์มที่หลากหลาย (`builder.insertCheckBox()` เป็นต้น)  
- การทำอัตโนมัติการแทรกแบบจำนวนมากในหลายเอกสารด้วยลูป  

ลองปรับขนาด, ตำแหน่ง, และการจัดการเหตุการณ์ของปุ่มให้เหมาะกับสถานการณ์ของคุณเอง ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการนำไปใช้ในโครงการของคุณเอง

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Create word document programmatically and add ActiveX button](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}