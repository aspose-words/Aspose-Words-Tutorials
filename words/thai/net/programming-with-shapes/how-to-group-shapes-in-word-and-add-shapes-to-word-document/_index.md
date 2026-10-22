---
category: general
date: 2026-08-07
description: วิธีจัดกลุ่มรูปร่างใน Word ด้วย Aspose.Words และเพิ่มรูปร่างลงในเอกสาร
  Word ด้วย C# ทำตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อโค้ดที่สะอาดและนำกลับมาใช้ใหม่ได้
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: th
lastmod: 2026-08-07
og_description: วิธีการจัดกลุ่มรูปร่างใน Word ด้วย Aspose.Words สำหรับ .NET. บทเรียนนี้จะแสดงวิธีเพิ่มรูปร่างลงในเอกสาร
  Word, จัดกลุ่มพวกมัน, และบันทึกไฟล์ด้วยโค้ด C# ที่ชัดเจน.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: วิธีจัดกลุ่มรูปร่างใน Word – คู่มือ C# อย่างรวดเร็ว
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: วิธีจัดกลุ่มรูปร่างใน Word และเพิ่มรูปร่างลงในเอกสาร Word
url: /th/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการจัดกลุ่มรูปทรงใน Word และเพิ่มรูปทรงลงในเอกสาร Word

หากคุณต้องการ **how to group shapes in Word**, คู่มือนี้จะพาคุณผ่านกระบวนการทั้งหมดโดยใช้ Aspose.Words for .NET คุณจะได้เรียนรู้ **add shapes to Word document** ด้วยโค้ด C# เพียงไม่กี่บรรทัด ทำให้ผลลัพธ์พร้อมสำหรับการรายงานหรือการสร้างเทมเพลตใด ๆ

บทเรียนนี้ครอบคลุมทุกสิ่งที่คุณต้องการ: แพคเกจ NuGet ที่จำเป็น, ไฟล์ซอร์สเต็ม, และคำอธิบายว่าทำไมแต่ละขั้นตอนจึงสำคัญ เมื่อเสร็จสิ้นคุณจะสามารถสร้างไฟล์ DOCX ที่มีสี่เหลี่ยมและวงรีรวมเป็นรูปทรงกลุ่มเดียวได้

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน, ตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า  
* Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ .NET)  
* Aspose.Words for .NET NuGet package (`Aspose.Words`) – เวอร์ชันทดลองฟรีใช้สำหรับการทดสอบ แต่ใบอนุญาตจะลบลายน้ำการประเมินผล  

รายการเหล่านี้เป็นการพึ่งพาภายนอกเพียงอย่างเดียวสำหรับ **add shapes to Word document**.

## วิธีการจัดกลุ่มรูปทรงใน Word

แกนหลักของวิธีแก้คือการสร้างรูปทรงแต่ละอัน, วางลงบนหน้า, แล้วห่อหุ้มด้วย `GroupShape` ขั้นตอนต่อไปนี้สะท้อนลำดับตรรกะของโค้ด

### ขั้นตอน 1: สร้างเอกสารและ Builder

อ็อบเจ็กต์ `Document` แทนไฟล์ DOCX ทั้งหมด `DocumentBuilder` ให้ API ที่สะดวกสำหรับการแก้ไขเอกสาร

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*ทำไมจึงสำคัญ*: `Document` คือคอนเทนเนอร์สำหรับทุกองค์ประกอบของ Word. `DocumentBuilder` จะติดตามตำแหน่งเคอร์เซอร์ปัจจุบัน ซึ่งจำเป็นเมื่อคุณแทรกรูปทรงที่จัดกลุ่มในภายหลัง

### ขั้นตอน 2: เพิ่มรูปสี่เหลี่ยม

สี่เหลี่ยมถูกสร้างโดยระบุ `ShapeType.Rectangle` ความกว้าง, ความสูง, และตำแหน่งตั้งค่าเป็นหน่วยจุด (1 pt ≈ 1/72 in)

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*ทำไมจึงสำคัญ*: การตั้งค่า `StrokeColor` ทำให้รูปทรงมองเห็นได้เมื่อเปิดเอกสาร คุณยังสามารถเติมสีภายในด้วย `FillColor` หากต้องการพื้นสีทึบ

### ขั้นตอน 3: เพิ่มรูปวงรี

วงรีใช้ `ShapeType.Ellipse` ขนาดและตำแหน่งของมันแยกจากสี่เหลี่ยม ทำให้คุณควบคุมการจัดวางสุดท้ายของกลุ่มได้

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*ทำไมจึงสำคัญ*: การกำหนดตำแหน่งวงรีที่ `Left = 120` ทำให้ไม่ทับซ้อนกับสี่เหลี่ยม ทำให้กลุ่มดูแตกต่างกันอย่างชัดเจน

### ขั้นตอน 4: จัดกลุ่มรูปทรงสองรูป

`GroupShape` ทำหน้าที่เป็นคอนเทนเนอร์ที่ถือเด็กของมันเป็นอ็อบเจ็กต์เดียว นี่คือการดำเนินการสำคัญสำหรับ **how to group shapes in Word**

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*ทำไมจึงสำคัญ*: การจัดกลุ่มทำให้คุณย้าย, ปรับขนาด, หรือหมุนรูปทรงทั้งสองพร้อมกัน การแปลงใด ๆ ที่ทำกับ `groupShape` จะส่งต่อไปยังเด็กของมัน

### ขั้นตอน 5: แทรกรูปทรงที่จัดกลุ่มลงในเอกสาร

`DocumentBuilder.InsertNode` วาง `GroupShape` ที่ตำแหน่งเคอร์เซอร์ปัจจุบัน เนื่องจากเราไม่ได้ย้าย Builder กลุ่มจะแสดงที่จุดเริ่มต้นของหน้าแรก

```csharp
builder.InsertNode(groupShape);
```

*ทำไมจึงสำคัญ*: การแทรกโหนดโดยตรงช่วยหลีกเลี่ยงการต้องสร้างย่อหน้าหรือเซลล์ตารางแยกต่างหาก กลุ่มจึงเป็นส่วนหนึ่งของการไหลของเอกสาร

### ขั้นตอน 6: บันทึกเอกสาร

สุดท้าย, เขียนไฟล์ DOCX ลงดิสก์ ใช้เส้นทางเต็มที่แอปพลิเคชันของคุณสามารถเขียนได้

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*ทำไมจึงสำคัญ*: `doc.Save` สรุปการเปลี่ยนแปลงทั้งหมด ไฟล์ที่ได้สามารถเปิดด้วย Microsoft Word, LibreOffice, หรือโปรแกรมดู DOCX ใด ๆ

## ไฟล์ซอร์สเต็ม

คัดลอกโค้ดด้านล่างไปยังโปรเจกต์คอนโซลใหม่ (`dotnet new console`) แล้วรัน โปรแกรมจะสร้างไฟล์ชื่อ `GroupShape.docx` ที่มีสี่เหลี่ยมและวงรีจัดกลุ่มอยู่

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เปิด `GroupShape.docx` คุณจะเห็นอ็อบเจ็กต์ภาพเดียวที่มีสี่เหลี่ยมสีน้ำเงินอยู่ด้านซ้ายและวงรีสีเขียวอยู่ด้านขวา การเลือกอ็อบเจ็กต์ใน Word จะไฮไลท์รูปทรงทั้งสองพร้อมกัน — พยานว่า **how to group shapes in Word** สำเร็จ

## คำถามทั่วไปและกรณีขอบ

* **Can I add more than two shapes?**  
  ใช่. เรียก `groupShape.AppendChild` สำหรับแต่ละ `Shape` เพิ่มเติมก่อนแทรกกลุ่ม

* **What if I need to rotate the group?**  
  ตั้งค่า `groupShape.RotationAngle = 45;` (มุมเป็นองศา) หลังจากสร้างกลุ่มเสร็จ

* **Do I need to call `doc.UpdatePageLayout()`?**  
  ไม่จำเป็นสำหรับสถานการณ์นี้ การจัดวางจะอัปเดตอัตโนมัติเมื่อบันทึกเอกสาร

* **How does licensing affect the code?**  
  เมื่อมีใบอนุญาต Aspose.Words ที่ถูกต้อง (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) เอกสารที่สร้างจะไม่มีลายน้ำการประเมินผล

## สรุป

คุณตอนนี้รู้แล้วว่า **how to group shapes in Word** และ **add shapes to Word document** ด้วย Aspose.Words for .NET บทเรียนได้อธิบายการสร้างเอกสาร, การกำหนดรูปทรงแต่ละอัน, การจัดกลุ่ม, การแทรกกลุ่ม, และการบันทึกไฟล์  

จากนี้คุณสามารถทดลองกับ:

* การเพิ่มกล่องข้อความหรือรูปภาพลงในกลุ่ม  
* การเปลี่ยนสีเติม, สไตล์เส้น, หรือเอฟเฟกต์เงา  
* การจัดกลุ่มรูปทรงภายในตารางหรือส่วนหัว  

ส่วนขยายเหล่านี้ช่วยให้คุณสร้างเทมเพลต Word ที่ซับซ้อนได้โดยโปรแกรมเมติก พร้อมรักษาโค้ดให้สะอาดและดูแลได้ง่าย ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโปรเจกต์ของคุณเอง

- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [แทรกรูปทรงในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [สร้างเอกสาร Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}