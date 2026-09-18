---
category: general
date: 2026-09-18
description: สร้างรูปสี่เหลี่ยมผืนผ้าในเอกสาร Word ด้วย C#. เรียนรู้วิธีเพิ่มหลายรูปทรง,
  เพิ่มรูปทรงเข้าไปในกลุ่ม, และแทรกรูปทรงกลุ่มด้วย Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: th
lastmod: 2026-09-18
og_description: สร้างรูปสี่เหลี่ยมผืนผ้าในไฟล์ Word ด้วย C# คู่มือนี้แสดงวิธีการเพิ่มหลายรูปทรง,
  เพิ่มรูปทรงเข้าไปในกลุ่ม, และแทรกรูปทรงกลุ่มโดยใช้ Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: สร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: สร้างรูปสี่เหลี่ยมและจัดกลุ่มหลายรูปใน C#
url: /th/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมและจัดกลุ่มหลายรูปใน C#

หากคุณต้องการ **สร้างรูปสี่เหลี่ยม** ในเอกสาร Word, บทแนะนำนี้จะแสดงวิธีแก้ไขแบบครบถ้วน คุณจะได้เห็นวิธี **เพิ่มหลายรูป**, **เพิ่มรูปลงในกลุ่ม**, และ **แทรกรูปกลุ่ม** โดยใช้ Aspose.Words API สำหรับ .NET

การทำงานกับรูปเป็นความต้องการทั่วไปเมื่อสร้างรายงาน, สัญญา หรือวัสดุการตลาดโดยอัตโนมัติ ในตอนท้ายของคู่มือนี้คุณจะมีแอปพลิเคชันคอนโซล C# ที่สามารถรันได้ซึ่งสร้างไฟล์ `.docx` ที่มีรูปสี่เหลี่ยม, รูปวงรี, และกลุ่มที่บรรจุรูปทั้งสองไว้

ข้อกำหนดเบื้องต้นเพียงอย่างเดียวคือ .NET SDK เวอร์ชันล่าสุด (6.0 หรือใหม่กว่า) และสำเนา Aspose.Words for .NET ที่มีลิขสิทธิ์ ไม่จำเป็นต้องใช้เครื่องมือเพิ่มเติม

## ข้อกำหนดเบื้องต้น

- .NET 6.0 SDK หรือใหม่กว่า  
- Aspose.Words for .NET (แพ็คเกจ NuGet `Aspose.Words`)  
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#  

คุณสามารถติดตั้งแพ็คเกจด้วยคำสั่งต่อไปนี้:

```bash
dotnet add package Aspose.Words
```

## ขั้นตอนที่ 1: สร้างรูปสี่เหลี่ยมด้วย Aspose.Words

ขั้นตอนแรกคือการสร้างอ็อบเจกต์ `Shape` ชนิด `Rectangle` อ็อบเจกต์นี้แทนรูปสี่เหลี่ยมที่จะแสดงในเอกสาร

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**ทำไมเรื่องนี้สำคัญ:** `ShapeType.Rectangle` บอก Aspose.Words ให้วาดรูปสี่เหลี่ยมเชิงเรขาคณิต การตั้งค่า `Width` และ `Height` กำหนดขนาดเป็นจุด (1 point = 1/72 นิ้ว) การเพิ่มสีเติมและสีเส้นทำให้รูปปรากฏโดยไม่ต้องใช้การจัดรูปแบบเพิ่มเติม

## ขั้นตอนที่ 2: เพิ่มหลายรูปลงในเอกสาร

หลังจากรูปสี่เหลี่ยม คุณสามารถสร้างรูปเพิ่มเติมได้ตามจำนวน ในตัวอย่างนี้เราจะเพิ่มรูปวงรีเพื่อสาธิตวิธีการ **เพิ่มหลายรูป** ทำงาน

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**ทำไมเรื่องนี้สำคัญ:** การเรียก `new Shape` แต่ละครั้งจะสร้างอ็อบเจกต์การวาดแยกกัน การแทรกแบบต่อเนื่องทำให้คุณสร้างคอลเลกชันของรูปที่สามารถจัดกลุ่มหรือกำหนดตำแหน่งแยกกันในภายหลัง

## ขั้นตอนที่ 3: เพิ่มรูปลงในกลุ่ม

การจัดกลุ่มรูปทำให้การจัดการเลย์เอาต์ง่ายขึ้น เพราะกลุ่มทำงานเป็นโหนดเดียว ขั้นตอนนี้แสดงวิธี **เพิ่มรูปลงในกลุ่ม** ด้วย `GroupShape`

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**ทำไมเรื่องนี้สำคัญ:** `GroupShape` ทำหน้าที่เหมือนคอนเทนเนอร์ เมื่อคุณย้าย, หมุน, หรือปรับขนาดกลุ่ม รูปลูกทั้งหมดจะตามโดยอัตโนมัติ กล่องขอบเขต (200 × 200 จุด) กำหนดพื้นที่พิกัดสำหรับรูปลูก

## ขั้นตอนที่ 4: แทรกรูปกลุ่มลงในเอกสาร

เมื่อกลุ่มมีรูปสี่เหลี่ยมและวงรีแล้ว คุณต้อง **แทรกรูปกลุ่ม** ที่ตำแหน่งที่ต้องการ ตัวสร้าง (builder) ได้วางกลุ่มเปล่าไว้แล้ว แต่คุณก็สามารถแทรกที่อื่นได้หากต้องการ

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**ทำไมเรื่องนี้สำคัญ:** การปรับค่า `Left` และ `Top` จะย้ายกลุ่มทั้งหมดภายในหน้า การบันทึกเอกสารจะเขียนลำดับชั้นของรูปลงในไฟล์ `.docx` ที่สามารถเปิดด้วย Microsoft Word, LibreOffice หรือโปรแกรมดูไฟล์ที่รองรับอื่นๆ

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่รวมทุกขั้นตอน คัดลอกโค้ดไปยังโปรเจกต์คอนโซลใหม่และรันเพื่อสร้างไฟล์ `GroupShapeExample.docx`

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:**  
การเปิด `GroupShapeExample.docx` จะเห็นกลุ่มเดียวที่บรรจุรูปสี่เหลี่ยมสีฟ้าอ่อนและรูปวงรีสีส้มอ่อน ทั้งสองอยู่ภายในคอนเทนเนอร์ขนาด 200 × 200 จุด กลุ่มสามารถเลือกเป็นอ็อบเจกต์เดียวใน Word ยืนยันว่า **เพิ่มรูปลงในกลุ่ม** สำเร็จ

## ความหลากหลายทั่วไปและกรณีขอบ

| สถานการณ์ | การปรับแนะนำ |
|-----------|------------------------|
| ประเภทรูปที่แตกต่าง (เช่น `ShapeType.Line`) | สร้างรูปด้วย `ShapeType` ที่ต้องการและตั้งค่ารูปทรงตามนั้น. |
| ต้องการหมุนรูป | ใช้ `shape.Rotation = 45;` (องศา) ก่อนเพิ่มลงในกลุ่ม. |
| เอกสารขนาดใหญ่ที่มีหลายกลุ่ม | ใช้อินสแตนซ์ `DocumentBuilder` เพียงตัวเดียว; หลีกเลี่ยงการสร้าง builder ใหม่สำหรับแต่ละกลุ่มเพื่อลดการใช้หน่วยความจำ. |
| บันทึกเป็น PDF แทน DOCX | เรียก `doc.Save("output.pdf", SaveFormat.Pdf);` หลังจากแทรกกลุ่ม. |

**เคล็ดลับมืออาชีพ:** ควรกำหนดค่า `Left` และ `Top` อย่างชัดเจนสำหรับกลุ่มเมื่อคุณต้องการการวางตำแหน่งที่แม่นยำ หากละเว้นค่าเหล่านี้ กลุ่มจะสืบทอดตำแหน่งเคอร์เซอร์ปัจจุบันของ builder ซึ่งอาจทำให้ผลลัพธ์การจัดวางไม่คาดคิด

## สรุป

ตอนนี้คุณรู้วิธี **สร้างรูปสี่เหลี่ยม**, **เพิ่มหลายรูป**, **เพิ่มรูปลงในกลุ่ม**, และ **แทรกรูปกลุ่ม** ในเอกสาร Word ด้วย C# ตัวอย่างเต็มแสดงขั้นตอนการทำงานทั้งหมดตั้งแต่การสร้างเอกสารจนถึงการบันทึกไฟล์ขั้นสุดท้าย.  

ต่อไปสำรวจหัวข้อที่เกี่ยวข้องเช่น **การวางตำแหน่งรูปสัมพันธ์กับข้อความ**, **การใช้การห่อหุ้มข้อความ**, และ **การส่งออกรูปที่จัดกลุ่มเป็น PDF** ส่วนขยายเหล่านี้ช่วยให้คุณสร้างเลย์เอาต์เอกสารที่ซับซ้อนและโปรแกรมได้ด้วย Aspose.Words.

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบอื่นในโครงการของคุณ

- [สร้างรูปสี่เหลี่ยมใน Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [สร้างรูปกลุ่มในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [สร้างเอกสาร Word ว่างพร้อมรูปสี่เหลี่ยมเงา – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}