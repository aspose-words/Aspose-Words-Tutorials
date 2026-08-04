---
category: general
date: 2026-08-04
description: แทรกรูปสี่เหลี่ยมในเอกสาร Word ด้วย C# เรียนรู้วิธีจัดกลุ่มรูปใน Word
  บันทึกเอกสารเป็นไฟล์ docx และใช้ DocumentBuilder สำหรับการจัดวางขั้นสูง
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: th
lastmod: 2026-08-04
og_description: แทรกรูปสี่เหลี่ยมผืนผ้าในไฟล์ Word ด้วย C# แล้วจัดกลุ่มรูปเพื่อการจัดวางขั้นสูง
  บทเรียนนี้ยังครอบคลุมการบันทึกเอกสารเป็นไฟล์ docx และการใช้ DocumentBuilder อย่างมีประสิทธิภาพ
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: แทรกรูปสี่เหลี่ยมใน Word – คู่มือขั้นตอน C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: แทรกรูปสี่เหลี่ยมใน Word ด้วย C# – คู่มือฉบับสมบูรณ์
url: /th/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกรูปสี่เหลี่ยมผืนผ้าใน Word ด้วย C# – คู่มือเต็ม

หากคุณต้องการ **แทรกรูปสี่เหลี่ยมผืนผ้า** ในเอกสาร Word ด้วย C# บทแนะนำนี้จะแสดงให้คุณเห็นอย่างชัดเจน คุณยังจะได้เรียนรู้ **วิธีการจัดกลุ่มรูปทรง** ใน Word, **การบันทึกเอกสารเป็น docx**, และ **วิธีใช้ Builder** เพื่อให้โค้ดสะอาดและดูแลรักษาได้ง่าย

การทำงานกับรูปทรงเป็นความต้องการทั่วไปเมื่อสร้างรายงาน, ใบรับรอง, หรือเลย์เอาต์แบบกำหนดเองโดยอัตโนมัติ เมื่ออ่านจบคู่มือนี้คุณจะมีตัวอย่างที่สามารถรันได้เต็มรูปแบบซึ่งสร้างสี่เหลี่ยมผืนผ้า, เพิ่มวงรี, จัดกลุ่มพวกมัน, และบันทึกผลลัพธ์เป็นไฟล์ DOCX

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 หรือใหม่กว่า ติดตั้งแล้ว  
* Visual Studio 2022 (หรือ IDE ใดก็ได้ที่รองรับ C#)  
* ไลบรารี **Aspose.Words for .NET** (สามารถติดตั้งผ่าน NuGet)  

คุณสามารถเพิ่มไลบรารีด้วยคำสั่งต่อไปนี้:

```bash
dotnet add package Aspose.Words
```

## แทรกรูปสี่เหลี่ยมผืนผ้าด้วย DocumentBuilder

ขั้นตอนแรกคือการสร้าง `Document` ใหม่และ `DocumentBuilder` ตัวสร้างให้ API แบบ fluent สำหรับแทรกเนื้อหา รวมถึงรูปทรงต่าง ๆ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

อินสแตนซ์ `DocumentBuilder` คืออ็อบเจกต์หลักที่คุณจะใช้เพื่อ **แทรกรูปสี่เหลี่ยมผืนผ้า** และองค์ประกอบอื่น ๆ มันติดตามตำแหน่งเคอร์เซอร์ปัจจุบันภายในเอกสาร ดังนั้นการแทรกใด ๆ จะเกิดขึ้นที่ตำแหน่งที่คุณต้องการอย่างแม่นยำ

## วิธีแทรกรูปสี่เหลี่ยมผืนผ้า

เมื่อพร้อมกับ builder ให้เรียก `InsertShape` คุณต้องระบุ `ShapeType`, ความกว้าง และความสูงเป็นหน่วยจุด (1 pt ≈ 1/72 in)

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*ทำไมเรื่องนี้สำคัญ*: การตั้งค่า `FillColor` และ `StrokeColor` ทำให้สี่เหลี่ยมผืนผ้ามีลักษณะเด่นชัด ซึ่งช่วยให้คุณสามารถจัดกลุ่มกับรูปทรงอื่นได้ง่ายขึ้นในขั้นตอนต่อไป

## วิธีจัดกลุ่มรูปทรงใน Word

การจัดกลุ่มรูปทรงทำให้คุณสามารถย้าย, หมุน, หรือจัดรูปแบบหลายวัตถุเป็นหน่วยเดียว หลังจากแทรกสี่เหลี่ยมผืนผ้าแล้ว ให้เพิ่มรูปทรงอีกหนึ่งรูป (วงรีในตัวอย่างนี้) แล้วสร้าง `GroupShape`

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

การเรียก `InsertGroupShape` จะสร้างตัวแทนที่สามารถบรรจุรูปทรงลูกได้หลายรูปโดยไม่จำกัด โดยการต่อสี่เหลี่ยมผืนผ้าและวงรีเข้าด้วยกัน คุณจึง **จัดกลุ่มรูปทรงใน Word** ได้อย่างมีประสิทธิภาพ กลุ่มทำงานเหมือนรูปทรงเดียว—you can reposition it, apply a border, or resize it without affecting the internal layout of each child.

### เคล็ดลับพิเศษ

หลังจากจัดกลุ่มแล้ว คุณสามารถเปลี่ยนตำแหน่งของกลุ่มสัมพันธ์กับหน้าได้:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## บันทึกเอกสารเป็น docx

เมื่อรูปทรงจัดเรียงเรียบร้อยแล้ว คุณต้องบันทึกไฟล์ `Document.Save` จะกำหนดรูปแบบโดยอัตโนมัติตามส่วนขยายของไฟล์ เพื่อ **บันทึกเอกสารเป็น docx** ให้ใส่พาธที่ลงท้ายด้วย `.docx`

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

การรันโปรแกรมจะสร้าง `output.docx` เปิดไฟล์ใน Microsoft Word แล้วคุณจะเห็นสี่เหลี่ยมสีฟ้าอ่อนและวงรีสีโคโรลอ่อนที่จัดกลุ่มอยู่ด้วยกัน คุณสามารถคลิกที่กลุ่มแล้วย้ายได้เป็นวัตถุเดียว

## วิธีใช้ DocumentBuilder อย่างมีประสิทธิภาพ

`DocumentBuilder` ไม่ได้เป็นเพียงตัวแทรกรูปทรงเท่านั้น; มันยังจัดการข้อความ, ตาราง, ส่วนหัว, และส่วนท้ายได้ด้วย เมื่อคุณผสานการสร้างรูปทรงกับข้อความ จำไว้ว่าต้องรีเซ็ตเคอร์เซอร์หากต้องการแทรกเนื้อหาในตำแหน่งอื่น:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

การทำให้สถานะของ builder ชัดเจนช่วยหลีกเลี่ยงการเขียนทับโดยบังเอิญและทำให้โค้ดดูแลรักษาง่ายขึ้น

## กรณีขอบและความแตกต่าง

| สถานการณ์ | แนวทางที่แนะนำ |
|-----------|----------------------|
| **มากกว่าสองรูปทรง** | แทรกรูปแต่ละรูป แล้วเรียก `AppendChild` สำหรับทุกรูปก่อนบันทึก |
| **กลุ่มซ้อนกัน** | สร้างกลุ่ม, เพิ่มรูปทรง, แล้วแทรกกลุ่มนั้นเข้าไปใน `GroupShape` อีกอันหนึ่ง |
| **หน่วยวัดที่แตกต่างกัน** | ใช้ `builder.ConvertPixelsToPoints` หากคุณมีขนาดเป็นพิกเซล |
| **ความเข้ากันได้กับเวอร์ชัน Word เก่า** | บันทึกเป็น `.doc` โดยเปลี่ยนส่วนขยาย; ฟีเจอร์รูปทรงส่วนใหญ่ยังทำงานได้ |

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในโปรเจกต์คอนโซลใหม่ ไม่ต้องมีโค้ดเพิ่มเติมใด ๆ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**ผลลัพธ์ที่คาดหวัง**: การเปิด `output.docx` จะเห็นสี่เหลี่ยมสีฟ้าอ่อนและวงรีสีโคโรลอ่อนที่จัดกลุ่มอยู่ด้วยกัน อยู่ห่างจากขอบซ้าย 150 pt และจากขอบบน 100 pt คำอธิบายจะปรากฏใต้กลุ่ม

## สรุป

คุณได้เรียนรู้วิธี **แทรกรูปสี่เหลี่ยมผืนผ้า** ในไฟล์ Word ด้วย C#, **วิธีจัดกลุ่มรูปทรงใน Word**, และ **วิธีบันทึกเอกสารเป็น docx** ด้วย Aspose.Words `DocumentBuilder` ด้วยการเชี่ยวชาญขั้นตอนเหล่านี้ คุณสามารถสร้างเลย์เอาต์ซับซ้อน—เช่น ใบรับรอง, รายงาน, หรือแบบฟอร์มแบบกำหนดเอง—ทั้งหมดผ่านโค้ด

ต่อไปให้สำรวจหัวข้อที่เกี่ยวข้อง เช่น **การเพิ่มกล่องข้อความ**, **การทำงานกับตาราง**, หรือ **การส่งออกเป็น PDF** แต่ละหัวข้อสร้างบนพื้นฐาน `DocumentBuilder` เดียวกันที่คุณเพิ่งฝึกฝน

พร้อมที่จะทำอัตโนมัติเอกสาร Word ของคุณหรือยัง? ลองขยายตัวอย่างด้วยรูปทรงเพิ่มเติม, ใช้การไล่สี, หรือวนลูปข้อมูลเพื่อสร้างรายงานเต็มรูปแบบในครั้งเดียว ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโครงการของคุณ

- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [แทรกรูปทรงในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [สร้างรูปสี่เหลี่ยมผืนผ้าใน Word ด้วย Aspose.Words – คู่มือแบบขั้นตอน](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}