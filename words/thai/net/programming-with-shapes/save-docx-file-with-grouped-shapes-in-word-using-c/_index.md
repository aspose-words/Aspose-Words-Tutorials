---
category: general
date: 2026-08-04
description: บันทึกไฟล์ docx อย่างอัตโนมัติพร้อมเพิ่มรูปสี่เหลี่ยมและจัดกลุ่มรูปใน
  Word. เรียนรู้การตั้งค่าขนาดรูปและสร้างกล่องข้อความอย่างอัตโนมัติ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: th
lastmod: 2026-08-04
og_description: บันทึกไฟล์ docx ด้วย C# โดยเพิ่มรูปสี่เหลี่ยม, จัดกลุ่มรูปใน Word,
  ตั้งค่าขนาดของรูป, และสร้างกล่องข้อความแบบโปรแกรมมิ่ง.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: บันทึกไฟล์ docx พร้อมรูปทรงที่จัดกลุ่มใน Word – คู่มือขั้นตอน C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: บันทึกไฟล์ docx พร้อมกลุ่มรูปทรงใน Word ด้วย C#
url: /th/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# บันทึกไฟล์ docx พร้อมรูปทรงที่จัดกลุ่มใน Word ด้วย C#

หากคุณต้องการ **save docx file** ที่มีหลายรูปทรงจัดเรียงร่วมกัน คู่มือนี้จะแสดงวิธีทำด้วย C# คุณจะได้เรียนรู้วิธี **add rectangle shape**, การจัดกลุ่มหลายรูปทรงในเอกสาร Word, **set shape dimensions**, และ **create textbox programmatically** โซลูชันนี้ทำงานกับ Aspose.Words for .NET เวอร์ชันล่าสุดและทำงานบน .NET 6 หรือใหม่กว่า

บทแนะนำจะพาคุณผ่านทุกขั้นตอน ตั้งแต่การตั้งค่าโปรเจกต์จนถึงการเรียก `doc.Save` ครั้งสุดท้าย เมื่อเสร็จสิ้นคุณจะมีโค้ดสแนปช็อตที่สามารถนำไปวางในโปรเจกต์คอนโซลหรือ ASP.NET ใดก็ได้ ไม่จำเป็นต้องใช้สคริปต์ภายนอกหรือแก้ไขไฟล์ DOCX ด้วยตนเอง

## ข้อกำหนดเบื้องต้น

* .NET 6 SDK (หรือใหม่กว่า) ที่ติดตั้งไว้
* ใบอนุญาตที่ถูกต้องสำหรับ **Aspose.Words for .NET** (รุ่นทดลองฟรีใช้สำหรับการทดสอบ)
* Visual Studio 2022, VS Code หรือ IDE ใดก็ได้ที่สามารถสร้างโปรเจกต์ .NET

โค้ดใช้เพียง namespace ของ Aspose.Words เท่านั้น ดังนั้นไม่จำเป็นต้องเพิ่มแพ็กเกจ NuGet ใดเพิ่มเติม

## บันทึกไฟล์ docx พร้อมรูปทรงที่จัดกลุ่มใน Word

หัวใจของโซลูชันคือการสร้าง `GroupShape` ที่ประกอบด้วยสี่เหลี่ยมและกล่องข้อความ จากนั้นแทรกกลุ่มนี้ลงในเอกสารและเรียก `doc.Save` ส่วนต่อไปนี้จะแบ่งกระบวนการออกเป็นชิ้นส่วนที่จัดการได้ง่าย

### 1. สร้างเอกสารใหม่และ Builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*ทำไมขั้นตอนนี้สำคัญ* – วัตถุ `Document` ใหม่แสดงถึงไฟล์ *.docx* ว่างเปล่า `DocumentBuilder` ให้เมธอดระดับสูงเช่น `InsertNode` ซึ่งเราจะใช้เพื่อวางรูปทรงกลุ่ม

### 2. เพิ่มรูปสี่เหลี่ยมลงในกลุ่ม

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*ทำไมขั้นตอนนี้สำคัญ* – การดำเนินการ **add rectangle shape** แสดงวิธีกำหนดองค์ประกอบภาพที่มีขนาดและตำแหน่งที่แน่นอน สี่เหลี่ยมอยู่ภายใน `group` ดังนั้นการย้ายกลุ่มในภายหลังจะย้ายสี่เหลี่ยมโดยอัตโนมัติ

### 3. จัดกลุ่มรูปทรงในเอกสาร Word

คลาส `GroupShape` รวมวัตถุการวาดหลายรายการ การจัดกลุ่มเป็นประโยชน์เมื่อคุณต้องการจัดการหลายวัตถุเป็นหน่วยเดียว (เช่น การย้าย, การหมุน, หรือการคัดลอกพร้อมกัน)

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*ทำไมเราจึงจัดกลุ่ม* – การจัดกลุ่มลดความซับซ้อนของการจัดวาง แทนที่จะกำหนดตำแหน่งแต่ละรูปทรงแยกบนหน้า คุณปรับค่า `Left`, `Top`, `Width`, และ `Height` ของกลุ่มเพียงครั้งเดียว

### 4. ตั้งค่าขนาดรูปทรงเพื่อการจัดวางที่แม่นยำ

ทั้งกลุ่มและรูปทรงลูกต้องมีขนาดที่ระบุอย่างชัดเจน มิฉะนั้น Word จะใช้ขนาดเริ่มต้นที่อาจไม่ตรงกับการออกแบบของคุณ

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*ทำไมเราตั้งค่าขนาด* – การวัดที่แม่นยำทำให้แน่ใจว่าสี่เหลี่ยมและกล่องข้อความไม่ทับซ้อนโดยไม่ได้ตั้งใจและไฟล์ **save docx file** สุดท้ายตรงกับการจัดวางที่ต้องการ

### 5. สร้างกล่องข้อความโดยโปรแกรมภายในกลุ่ม

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*ทำไมขั้นตอนนี้สำคัญ* – ส่วน **create textbox programmatically** แสดงวิธีฝังข้อความที่มีรูปแบบภายในรูปทรง การใช้ `Paragraph` และ `Run` ให้คุณควบคุมการจัดรูปแบบได้เต็มที่ในภายหลัง

### 6. แทรกรูปทรงกลุ่มและ **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*ทำไมขั้นตอนสุดท้ายนี้สำคัญ* – การเรียก `InsertNode` จะวางรูปทรงที่จัดกลุ่มไว้ที่ตำแหน่งเคอร์เซอร์ของ builder อย่างแม่นยำ เมธอด `doc.Save` ทำการ **save docx file** โดยเขียนเอกสาร Word ที่เต็มรูปแบบลงดิสก์

> **ผลลัพธ์:** การเปิด *GroupShape.docx* ใน Microsoft Word จะแสดงสี่เหลี่ยมด้านซ้ายและกล่องข้อความด้านขวา ทั้งสองถูกล็อกไว้ด้วยกันในกลุ่มเดียว คุณสามารถย้ายกลุ่มเป็นหน่วยเดียว ปรับขนาด หรือใช้การจัดรูปแบบเพิ่มเติมได้

## ตัวอย่างเต็มที่สามารถรันได้

คัดลอกโค้ดด้านล่างไปยังโปรเจกต์คอนโซลใหม่ (`dotnet new console`) แล้วรัน `dotnet run` โปรแกรมจะสร้างไฟล์ `GroupShape.docx` ในโฟลเดอร์ผลลัพธ์ของโปรเจกต์

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ชื่อ **GroupShape.docx** ปรากฏในไดเรกทอรีผลลัพธ์
* การเปิดไฟล์จะแสดงรูปสี่เหลี่ยมด้านซ้ายและกล่องข้อความที่มีข้อความ “Grouped text” ด้านขวา ทั้งสองถูกล็อกไว้ด้วยกัน
* การเลือกรูปทรงใดรูปหนึ่งจะย้ายกลุ่มทั้งหมด ยืนยันว่าฟังก์ชัน **group shapes word** ทำงานตามที่ตั้งใจ

## ความหลากหลายทั่วไปและกรณีขอบ

| สถานการณ์ | คำแนะนำ |
|-----------|----------------|
| ต้องการรูปทรงมากกว่าสองรูป | เพิ่มอ็อบเจ็กต์ `Shape` เพิ่มเติมลงใน `group` ก่อนเรียก `builder.InsertNode` |
| ต้องการให้กลุ่มปรากฏบนหน้าที่กำหนด | ย้ายเคอร์เซอร์ของ builder ด้วย `builder.MoveToDocumentEnd()` หรือ `builder.MoveToPage(pageNumber)` |
| ต้องการหน่วยที่แตกต่าง (เช่น เซนติเมตร) | ใช้ `ConvertUtil.InchToPoint(1.0)` เพื่อแปลงนิ้วเป็นพอยต์ ซึ่งเป็นหน่วยที่ Word คาดหวัง |
| ต้องการให้กล่องข้อความตัดคำ | ตั้งค่า `textBox.TextBoxWrap = TextBoxWrapType.Square` หลังจากสร้างกล่องข้อความ |
| ทำงานกับเวอร์ชัน .NET Framework เก่า | API เดียวกันทำงานกับ .NET Framework 4.7+ แต่ต้องตรวจสอบว่าคุณอ้างอิงเวอร์ชัน Aspose.Words ที่ถูกต้อง |

**เคล็ดลับ:** ควรตั้งค่า `Width` และ `Height` ของกลุ่ม *หลัง* จากการเพิ่มรูปทรงลูกทั้งหมด ซึ่งจะรับประกันว่ากลุ่มครอบคลุมเนื้อหาทั้งหมด ป้องกันการตัดขอบเมื่อเปิดเอกสารใน Word

## สรุป

ตอนนี้คุณรู้วิธี **save docx file** พร้อมกับ **add rectangle shape**, **group shapes word**, **set shape dimensions**, และ **create textbox programmatically** ด้วย Aspose.Words for .NET ตัวอย่างเต็มแสดงรูปแบบที่สะอาดและทำซ้ำได้ซึ่งคุณสามารถปรับใช้กับการจัดวางที่ซับซ้อนยิ่งขึ้น เช่น แผนภูมิ, รูปภาพ,

## สิ่งที่คุณควรเรียนต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโครงการของคุณ

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}