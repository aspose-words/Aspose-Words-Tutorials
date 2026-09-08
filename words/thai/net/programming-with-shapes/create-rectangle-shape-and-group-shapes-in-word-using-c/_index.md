---
category: general
date: 2026-09-08
description: สร้างรูปสี่เหลี่ยมผืนผ้าในเอกสาร Word ด้วย C# เรียนรู้การตั้งค่าขนาดของรูป,
  การจัดกลุ่มหลายรูป, และการสร้างเอกสาร Word ว่างโดยอัตโนมัติ
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: th
lastmod: 2026-09-08
og_description: สร้างรูปสี่เหลี่ยมผืนผ้าในเอกสาร Word ด้วย C# คู่มือนี้แสดงวิธีตั้งค่าขนาดของรูป,
  รวมหลายรูปเข้าด้วยกัน, และสร้างเอกสาร Word ว่างโดยอัตโนมัติ
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: สร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Word ด้วย C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: สร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Word ด้วย C#
url: /th/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมผืนผ้าและจัดกลุ่มรูปใน Word ด้วย C#

หากคุณต้องการ **สร้างรูปสี่เหลี่ยมผืนผ้า** ภายในไฟล์ Word, บทแนะนำนี้จะให้วิธีแก้ที่สมบูรณ์และพร้อมรัน คุณจะได้เห็นวิธีตั้งขนาดรูป, จัดกลุ่มหลายรูป, และสร้างเอกสาร Word เปล่าตั้งแต่ต้น—ทั้งหมดด้วยไลบรารี Aspose.Words for .NET

การทำงานกับเอกสาร Word ด้วยโปรแกรมมักรู้สึกเหมือนต้องจัดการรายละเอียดเล็ก ๆ มากมาย เมื่ออ่านจบคู่มือนี้ คุณจะมีเมธอดเดียวที่สร้างไฟล์ `.docx` ที่มีรูปสี่เหลี่ยมและรูปวงรีจัดกลุ่มไว้ด้วยกัน พร้อมสำหรับการแก้ไขหรือพิมพ์ต่อไป

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน, โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+)
* สำเนาไลเซนส์ของ **Aspose.Words for .NET** (คุณสามารถใช้คีย์ทดลองฟรี)
* IDE เช่น Visual Studio 2022 หรือ Visual Studio Code
* ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#

ไม่จำเป็นต้องติดตั้ง NuGet package เพิ่มเติมนอกจาก `Aspose.Words`

## ขั้นตอนที่ 1: สร้างเอกสาร Word เปล่า

ขั้นตอนแรกคือการสร้างเอกสารเปล่าที่จะเป็นที่เก็บรูปต่าง ๆ ซึ่งสอดคล้องกับความต้องการ *สร้างเอกสาร Word เปล่า*  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

การสร้างเอกสารเปล่าให้คุณมีผืนใบว่าง `Document` ตัวแทนไฟล์ `.docx` ทั้งหมด, และ `FirstSection.Body.FirstParagraph` คือจุดแทรกเริ่มต้นสำหรับโหนดใหม่

## ขั้นตอนที่ 2: สร้างรูปสี่เหลี่ยมผืนผ้า

ตอนนี้คุณสามารถเพิ่มรูปสี่เหลี่ยมได้ นี่คือจุดที่ทำงาน **สร้างรูปสี่เหลี่ยมผืนผ้า**  

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

การตั้งค่าขนาดโดยตรงตอบสนองคีย์เวิร์ด **ตั้งขนาดรูป** ค่าแต่ละค่าถูกระบุเป็นจุด (points) ซึ่งให้การควบคุมที่แม่นยำต่อการแสดงผลของรูปในเอกสารขั้นสุดท้าย

## ขั้นตอนที่ 3: สร้างรูปเพิ่มเติม (วงรี)

กรณีการใช้งานทั่วไปคือการรวมหลายรูปเข้าด้วยกัน ที่นี่เราจะเพิ่มรูปวงรีที่จะอยู่ในคอนเทนเนอร์เดียวกันในภายหลัง  

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

รูปทั้งสองยังคงเป็นอิสระกันในขณะนี้ ขั้นตอนต่อไปจะแสดงวิธี **จัดกลุ่มหลายรูป** เข้าด้วยกัน

## ขั้นตอนที่ 4: จัดกลุ่มรูปใน Word

การจัดกลุ่มรูปทำให้คุณสามารถย้าย, ปรับขนาด, หรือจัดรูปแบบได้เป็นหน่วยเดียว ซึ่งสอดคล้องกับความต้องการ **จัดกลุ่มรูปใน Word** และ **จัดกลุ่มหลายรูป**  

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

คุณสมบัติ `GroupShape.Bounds` กำหนดระบบพิกัดสำหรับรูปลูก เมื่อใส่สี่เหลี่ยมและวงรีไว้ใน `GroupShape` เดียวกัน คุณสามารถย้ายหรือหมุนพวกมันพร้อมกันด้วยคำสั่งเดียว

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายให้เขียนเอกสารลงดิสก์ ไฟล์จะมีรูปที่จัดกลุ่มไว้แล้ว  

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

หลังจากรันโปรแกรม, เปิด `GroupedShapes.docx` ด้วย Microsoft Word คุณควรเห็นสี่เหลี่ยมและวงรีที่จัดกลุ่มไว้ด้วยกัน; การเลือกรูปหนึ่งจะเลือกอีกรูปหนึ่งด้วย, ยืนยันว่าการจัดกลุ่มสำเร็จ

## โค้ดเต็ม

คัดลอกโปรแกรมต่อไปนี้ลงในโครงการ console‑app ใหม่และรัน ไม่ต้องเพิ่มโค้ดอื่นใด  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

การรันโปรแกรมจะสร้าง `GroupedShapes.docx` การเปิดไฟล์ใน Word จะแสดง:

* **สี่เหลี่ยมผืนผ้า** (100 pt × 50 pt) มีเส้นขอบสีน้ำเงินและพื้นสีเทาอ่อน
* **วงรี** (80 pt × 80 pt) มีเส้นขอบสีเขียวเข้มและพื้นสีเหลืองอ่อน
* รูปทั้งสองอยู่ในกลุ่มเดียวกัน, ดังนั้นการย้ายรูปหนึ่งจะย้ายอีกรูปหนึ่งด้วย

## คำถามที่พบบ่อยและกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ฉันสามารถเพิ่มรูปมากก่าสองรูปในกลุ่มได้หรือไม่?** | ได้. สร้างอ็อบเจ็กต์ `Shape` เพิ่มเติมและเรียก `group.AppendChild(yourShape)` สำหรับแต่ละรูป |
| **ถ้าต้องการหมุนกลุ่มล่ะ?** | ตั้งค่า `group.RotationAngle = 45;` (หน่วยเป็นองศา) รูปลูกทั้งหมดจะหมุนพร้อมกัน |
| **สามารถจัดกลุ่มรูปหลังจากบันทึกเอกสารได้หรือไม่?** | ต้องแก้ไขโครงสร้างเอกสารก่อนบันทึก; มิฉะนั้นคุณต้องโหลดไฟล์, ค้นหารูป, แล้วสร้างกลุ่มใหม่ |
| **ต้องทำการ dispose อ็อบเจ็กต์ใดบ้างหรือไม่?** | Aspose.Words จัดการทรัพยากรของตนเอง, แต่คุณควร dispose `FileStream` หากเปิดสตรีมด้วยตนเอง |
| **โค้ดจะทำงานกับรูปแบบ .doc (binary) ได้หรือไม่?** | ได้, เปลี่ยนเป็น `doc.Save("output.doc")`. พฤติกรรมการจัดกลุ่มจะเหมือนเดิม |

## สรุป

ตอนนี้คุณรู้วิธี **สร้างรูปสี่เหลี่ยมผืนผ้า**, **ตั้งขนาดรูป**, และ **จัดกลุ่มหลายรูป** ภายในไฟล์ Word ด้วย C# วิธีนี้ช่วยให้คุณสร้างแผนภาพซับซ้อน, วอเตอร์มาร์ค, หรือรายงานเทมเพลตโดยอัตโนมัติโดยไม่ต้องแก้ไขด้วยมือ

### ขั้นตอนต่อไป

* สำรวจ **จัดกลุ่มรูปใน Word** เพิ่มเติมโดยเพิ่มกล่องข้อความหรือรูปภาพในกลุ่มเดียวกัน
* ใช้รูปแบบ `SetShapeSize` เพื่อคำนวณขนาดแบบไดนามิกตามการจัดหน้า
* ผสานเทคนิคนี้กับฟิลด์เมล‑เมิร์จเพื่อสร้างเอกสารส่วนบุคคลในปริมาณมาก

ลองทดลองกับประเภทรูปต่าง ๆ, สี, และการแปลงกลุ่มตามต้องการได้เลย ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจคของคุณ

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}