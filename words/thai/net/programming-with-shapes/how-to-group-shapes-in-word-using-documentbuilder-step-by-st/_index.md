---
category: general
date: 2026-09-08
description: เรียนรู้วิธีจัดกลุ่มรูปร่างใน Word ด้วย DocumentBuilder, สร้างเอกสาร
  Word เปล่า, และแทรกรูปสี่เหลี่ยมโดยใช้เพียงไม่กี่บรรทัดของโค้ด C#
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: th
lastmod: 2026-09-08
og_description: จัดกลุ่มรูปร่างใน Word ด้วย DocumentBuilder บทเรียนนี้จะแสดงวิธีสร้างเอกสาร
  Word เปล่า แทรกรูปสี่เหลี่ยม และรวมรูปร่างเป็น GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: จัดกลุ่มรูปร่างใน Word ด้วย DocumentBuilder – ตัวอย่าง C# ครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีจัดกลุ่มรูปร่างใน Word ด้วย DocumentBuilder – คู่มือทีละขั้นตอน
url: /th/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการจัดกลุ่มรูปทรงใน Word ด้วย DocumentBuilder – คู่มือขั้นตอนโดยละเอียด

หากคุณต้องการ **จัดกลุ่มรูปทรงใน Word** อย่างโปรแกรมเมติก คู่มือฉบับนี้จะแสดงวิธีแก้ไขแบบครบถ้วนด้วย C# คุณจะได้เห็นวิธี **สร้างเอกสาร Word เปล่า**, ใช้ **DocumentBuilder**, และ **แทรกรูปสี่เหลี่ยม** ก่อนจะจัดกลุ่มกับรูปวงรี ผลลัพธ์คือ `GroupShape` เดียวที่คุณสามารถย้าย, ปรับขนาด, หรือกำหนดสไตล์ได้เหมือนเป็นอ็อบเจกต์หนึ่งเดียว

คำแนะนำนี้ครอบคลุมทุกอย่างที่คุณต้องรู้เพื่อสร้างเอกสาร Word ที่มีกราฟิกจัดกลุ่มโดยใช้ไลบรารี Aspose.Words for .NET เมื่ออ่านจบบทความแล้ว คุณจะมีโปรเจกต์ที่สามารถรันได้ซึ่งสร้างไฟล์ `GroupedShapes.docx` ที่มีรูปสี่เหลี่ยมและรูปวงรีรวมเป็นรูปทรงเดียว

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานได้กับ .NET Framework 4.7.2+)
- แพคเกจ NuGet ของ Aspose.Words for .NET (`Aspose.Words`) – เวอร์ชัน 23.12 หรือใหม่กว่า
- IDE สำหรับ C# เช่น Visual Studio 2022 หรือ Visual Studio Code
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C# และการเขียนโปรแกรมเชิงวัตถุ

> **เคล็ดลับ:** ติดตั้งแพคเกจ NuGet ผ่านบรรทัดคำสั่งเพื่อให้โปรเจกต์ของคุณเป็นระเบียบ:  
> `dotnet add package Aspose.Words --version 23.12.0`

## ขั้นตอนที่ 1: สร้างเอกสาร Word เปล่า

การดำเนินการแรกคือการสร้างอ็อบเจกต์ `Document` ซึ่งเป็นตัวแทนของไฟล์ Word ว่างเปล่า และ `DocumentBuilder` ที่ให้คุณเพิ่มเนื้อหาได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**ทำไมเรื่องนี้สำคัญ:** `Document` ทำหน้าที่เป็นคอนเทนเนอร์ของไฟล์ ส่วน `DocumentBuilder` ให้ API แบบ fluent สำหรับแทรกข้อความ, รูปภาพ, และรูปทรง หากไม่มี `DocumentBuilder` คุณจะต้องจัดการกับโครงสร้างโหนดของเอกสารด้วยตนเอง ซึ่งเสี่ยงต่อข้อผิดพลาดสูง

## ขั้นตอนที่ 2: แทรกรูปสี่เหลี่ยม

สี่เหลี่ยมเป็นบล็อกพื้นฐานที่ใช้บ่อยในไดอะแกรม ใช้ `InsertShape` พร้อม `ShapeType.Rectangle` และระบุความกว้างและความสูงเป็นพอยต์ (1 pt ≈ 1/72 in)

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**ทำไมเรื่องนี้สำคัญ:** การกำหนดค่า `Left` และ `Top` ทำให้สี่เหลี่ยมวางตำแหน่งได้อย่างแม่นยำบนหน้า ซึ่งจำเป็นเมื่อคุณจะจัดกลุ่มกับรูปทรงอื่น ๆ หลังจากนั้น `InsertShape` จะเพิ่มรูปทรงลงในพารากราฟปัจจุบันโดยอัตโนมัติ

## ขั้นตอนที่ 3: แทรกรูปวงรี

ต่อไปให้เพิ่มรูปวงรีที่วางอยู่ข้างสี่เหลี่ยม

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**ทำไมเรื่องนี้สำคัญ:** การใช้ `ShapeType` ที่แตกต่างกันแสดงให้เห็นว่า API ของ `DocumentBuilder` สามารถสร้างกราฟิกที่หลากหลายได้อย่างไร การวางตำแหน่งวงรีให้ทับกับสี่เหลี่ยมทำให้ผลของการจัดกลุ่มชัดเจนขึ้น

## ขั้นตอนที่ 4: จัดกลุ่มรูปทรงสองรูป

`GroupShape` ทำหน้าที่เหมือนคอนเทนเนอร์ โดยการเพิ่มสี่เหลี่ยมและวงรีเป็นลูก จะทำให้พวกมันทำงานเป็นอ็อบเจกต์เดียว

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**ทำไมเรื่องนี้สำคัญ:** คุณสมบัติ `Bounds` บอก Word ว่ากลุ่มอยู่ที่ตำแหน่งใดบนหน้า โดยการเพิ่มรูปทรงลูกเข้าไป คุณจะคงการจัดรูปแบบของแต่ละรูปไว้ได้พร้อมกับเปิดใช้งานการแปลงรวม (ย้าย, หมุน, ปรับขนาด)

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายให้เขียนเอกสารลงดิสก์ คุณสามารถเปลี่ยนเส้นทางให้เป็นโฟลเดอร์ใดก็ได้ที่ต้องการ

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

เมื่อคุณเปิดไฟล์ `GroupedShapes.docx` ด้วย Microsoft Word คุณจะเห็นสี่เหลี่ยมและวงรีที่จัดกลุ่มอยู่ด้วยกัน การเลือกกลุ่มจะไฮไลต์รูปทรงทั้งสองพร้อมกัน ทำให้คุณสามารถลากหรือปรับขนาดได้เป็นหน่วยเดียว

### ผลลัพธ์ที่คาดหวัง

- ไฟล์ Word ชื่อ **GroupedShapes.docx**
- หน้าแรกมี **สี่เหลี่ยม** (100 pt × 50 pt) ที่ตำแหน่ง (50, 50)
- **วงรี** (80 pt × 80 pt) ที่ตำแหน่ง (200, 70)
- รูปทรงทั้งสองเป็นส่วนหนึ่งของ **GroupShape** ที่มีกรอบล้อมรอบขนาด 300 pt × 200 pt

## ความแตกต่างทั่วไปและกรณีขอบ

| สถานการณ์ | การปรับเปลี่ยน |
|----------|------------|
| **ขนาดหน้ากระดาษต่างกัน** | ตั้งค่า `document.Sections[0].PageSetup.PageWidth` และ `PageHeight` ก่อนแทรกรูปทรง |
| **รูปทรงมากกว่าสองรูป** | สร้างอ็อบเจกต์ `Shape` เพิ่มเติมและเรียก `groupShape.AppendChild(newShape)` สำหรับแต่ละอัน |
| **กำหนดสีเติม** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **หมุนกลุ่ม** | `groupShape.Rotation = 45;` (หน่วยเป็นองศา) |
| **ส่งออกเป็น PDF** | หลังบันทึก DOCX ให้เรียก `document.Save("GroupedShapes.pdf");` |

## โค้ดเต็ม (พร้อมรัน)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

คัดลอกโค้ดไปยังโปรเจกต์คอนโซลใหม่, ทำการรีสโตร์แพคเกจ Aspose.Words NuGet, แล้วรัน โปรแกรมคอนโซลจะแจ้งตำแหน่งไฟล์, และการเปิดไฟล์จะเห็นกราฟิกที่จัดกลุ่มแล้ว

## สรุป

ตอนนี้คุณรู้ **วิธีจัดกลุ่มรูปทรงใน Word** ด้วย Aspose.Words `DocumentBuilder` แล้ว คู่มือได้อธิบายขั้นตอนการสร้าง **เอกสาร Word เปล่า**, **แทรกรูปสี่เหลี่ยม**, เพิ่มวงรี, และรวมเป็น `GroupShape` ด้วยพื้นฐานนี้คุณสามารถสร้างไดอะแกรม, แผนผัง, หรือกราฟิกแบบกำหนดเองจาก C# ได้อย่างเต็มที่

### ขั้นตอนต่อไปคืออะไร?

- สำรวจ **การใช้ DocumentBuilder** สำหรับตาราง, ส่วนหัว, และส่วนท้าย
- ผสานเทคนิค **insert rectangle shape Word** กับกล่องข้อความเพื่อสร้างไดอะแกรมที่มีคำอธิบาย
- ใช้ **create blank word doc** เป็นแม่แบบสำหรับการสร้างรายงานอัตโนมัติ

อย่ากลัวที่จะทดลองสี, การไล่สี, และรูปทรงเพิ่มเติม ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ ทุกแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณเอง

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}