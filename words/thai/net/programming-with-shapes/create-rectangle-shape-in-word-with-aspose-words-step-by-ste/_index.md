---
category: general
date: 2025-12-29
description: สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Aspose.Words C#. เรียนรู้การตั้งค่าความโปร่งใสของรูป,
  ตั้งค่าสีเงา, และบันทึกเอกสาร Word อย่างง่ายดาย.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: th
og_description: สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Aspose.Words C#. คู่มือนี้แสดงวิธีตั้งค่าความโปร่งใสของรูปทรง,
  ตั้งค่าสีเงา, และบันทึกเอกสาร Word.
og_title: สร้างรูปสี่เหลี่ยมใน Word – บทเรียน Aspose.Words อย่างสมบูรณ์
tags:
- Aspose.Words
- C#
- Word Automation
title: สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือแบบทีละขั้นตอน
url: /th/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมใน Word – บทเรียน Aspose.Words อย่างครบถ้วน

เคยต้อง **สร้างรูปสี่เหลี่ยม** ในเอกสาร Word แต่ไม่รู้จะเริ่มจากตรงไหนหรือไม่? คุณไม่ได้เป็นคนเดียว; นักพัฒนาหลายคนเจออุปสรรคนี้เมื่อต้องทำอัตโนมัติรายงานหรือใบแจ้งหนี้ ในคู่มือนี้เราจะพาคุณผ่านขั้นตอนที่แน่นอนเพื่อ **สร้างรูปสี่เหลี่ยม**, ตั้งค่าความโปร่งใสของรูป, ตั้งค่าสีเงา, และสุดท้าย **บันทึกเอกสาร Word** ด้วย Aspose.Words for .NET  

เราจะครอบคลุมทุกอย่างตั้งแต่การสร้างอ็อบเจ็กต์ Document เริ่มต้นจนถึงไฟล์ `.docx` สุดท้ายบนดิสก์, ดังนั้นเมื่ออ่านจบคุณจะสามารถ **สร้างเอกสาร Word** ด้วยโปรแกรมได้โดยไม่ต้องเดา ไม่ต้องอ้างอิงภายนอก, เพียงโซลูชันที่พร้อมคัดลอก‑วางเข้าโปรเจกต์ของคุณ

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+)
- NuGet package ของ Aspose.Words for .NET (`Install-Package Aspose.Words`)
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#
- IDE ที่คุณชอบ (Visual Studio, Rider, VS Code ฯลฯ)

> **เคล็ดลับ:** หากคุณใช้รุ่นทดลองฟรีของ Aspose.Words, ไลบรารีจะใส่ลายน้ำในไฟล์ผลลัพธ์ สำหรับการใช้งานจริงคุณต้องมีไลเซนส์ที่ถูกต้อง

## ขั้นตอนที่ 1: เริ่มต้น Document และ Builder

สิ่งแรกที่เราทำคือสร้างเอกสาร Word ว่างเปล่าใหม่และ `DocumentBuilder` ที่ช่วยให้เราสามารถแทรกเนื้อหาได้ คิดว่า Builder คือปากกาเสมือนที่วาดบนหน้า

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **ทำไมถึงสำคัญ:** หากไม่มี `DocumentBuilder` คุณจะต้องจัดการกับโครงสร้างโหนดระดับต่ำโดยตรง ซึ่งทำให้เกิดข้อผิดพลาดได้ง่ายและอ่านยาก

## ขั้นตอนที่ 2: สร้างรูปสี่เหลี่ยม

ตอนนี้เราจะ **สร้างรูปสี่เหลี่ยม** จริง ๆ เมธอด `InsertShape` รับค่า `ShapeType` enum, ความกว้าง, และความสูง (หน่วยเป็น points) วัตถุ `Shape` ที่คืนค่ามาจะให้เราปรับคุณสมบัติด้านภาพต่อไป

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

ในขณะนี้รูปสี่เหลี่ยมเป็นกล่องสีดำทึบที่ยึดกับย่อหน้าปัจจุบัน คุณสามารถย้าย, ปรับขนาด, หรือแม้แต่หมุนมันในภายหลังได้หากต้องการ

![สร้างรูปสี่เหลี่ยมพร้อมเงา](/images/rectangle-shadow.png "เอกสาร Word แสดงรูปสี่เหลี่ยมพร้อมเงาสีเทา")

*Image alt text: สร้างรูปสี่เหลี่ยมพร้อมเงาในเอกสาร Word*

## ขั้นตอนที่ 3: ตั้งค่าความโปร่งใสของรูป

ความโปร่งใสคือระดับ “มองทะลุ” ของสีเติมรูป Aspose.Words ใช้คุณสมบัติ `Transparency` ที่มีค่าตั้งแต่ `0.0` (ทึบ) ถึง `1.0` (โปร่งใสเต็ม) ที่นี่เราจะ **ตั้งค่าความโปร่งใสของรูป** เป็น 40 % เพื่อให้ข้อความพื้นหลังยังอ่านได้

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **กรณีพิเศษ:** หากต้องการรูปที่มองไม่เห็นเลยแต่ยังต้องการให้เงาปรากฏ, ตั้งค่า `Transparency` เป็น `1.0` แล้วกำหนดความกว้างเส้นขอบที่ไม่เป็นศูนย์

## ขั้นตอนที่ 4: ตั้งค่าเงา

เงาตกแบบละเอียดจะเพิ่มความลึก เราจะ **ตั้งค่าสีเงา** เป็นสีเทากลาง, ปรับรัศมีเบลอ, และเลื่อนตำแหน่งเล็กน้อยทั้งแนวนอนและแนวตั้ง

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **ทำไมถึงสำคัญ:** เงาที่คมเกินไปหรือสีเข้มเกินไปอาจดูเหมือนข้อบกพร่องของการพิมพ์ ปรับค่า `Blur` และ `Transparency` จนรู้สึกเป็นธรรมชาติ

## ขั้นตอนที่ 5: บันทึกเอกสาร Word

สุดท้ายเราจะ **บันทึกเอกสาร Word** ลงดิสก์ เมธอด `Save` จะกำหนดรูปแบบไฟล์อัตโนมัติตามส่วนขยาย; `.docx` คือรูปแบบ OpenXML สมัยใหม่

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

หากโฟลเดอร์ไม่มีอยู่, Aspose.Words จะโยน `ArgumentException` ตรวจสอบให้แน่ใจว่าเส้นทางถูกต้องหรือสร้างไดเรกทอรีล่วงหน้า

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่พร้อมรันครบทุกขั้นตอน คัดลอกไปยังโปรเจกต์คอนโซลใหม่และกด **F5**

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เปิด `ShadowRectangle.docx` ด้วย Microsoft Word คุณควรเห็นรูปสี่เหลี่ยมสีเทาอ่อนพร้อมเงานุ่มเล็กน้อยที่เลื่อนตำแหน่งเล็กน้อย, ทั้งสองแสดงที่ความโปร่งใส 40 % รูปอยู่บนหน้าเปล่า, พร้อมสำหรับเนื้อหาเพิ่มเติม

## คำถามที่พบบ่อยและการปรับใช้

**ต้องการรูปแบบอื่น?**  
เปลี่ยน `ShapeType.Rectangle` เป็นค่า enum อื่น (`Ellipse`, `Triangle`, `Star` ฯลฯ) ส่วนโค้ดที่เหลือคงเดิม

**เปลี่ยนสีเส้นขอบได้หรือไม่?**  
ได้—ใช้ `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` และอาจตั้งค่า `rectangleShape.StrokeWeight = 1.5;`

**วางรูปที่ตำแหน่งเฉพาะบนหน้าอย่างไร?**  
ตั้งค่า `rectangleShape.WrapType = WrapType.None;` แล้วปรับ `rectangleShape.Left` และ `rectangleShape.Top` (หน่วยเป็น points)

**ใส่ข้อความภายในรูปได้หรือไม่?**  
ทำได้เลย หลังจากสร้างรูปให้เรียก `rectangleShape.AppendChild(new Paragraph(document))` แล้วเพิ่ม `Run` ที่มีข้อความของคุณ อย่าลืมตั้งค่า `rectangleShape.TextBox` หากต้องการฟอร์แมตขั้นสูง

## เคล็ดลับระดับมืออาชีพและข้อควรระวัง

- **ใส่ไลเซนส์ตั้งแต่ต้น:** หากลืมใส่ไลเซนส์ Aspose.Words จะใส่ลายน้ำบนหน้าแรก ซึ่งอาจทำให้การทดสอบสับสน
- **เคล็ดลับประสิทธิภาพ:** เมื่อสร้างเอกสารหลายไฟล์ในลูป, ใช้ `Document` ตัวเดียวและเรียก `document.RemoveAllChildren();` หลังแต่ละการบันทึก เพื่อลดภาระ GC
- **ความมองเห็นของเงา:** บนหน้าจอความละเอียดต่ำเงาอ่อนอาจมองไม่เห็น เพิ่มค่า `Blur` หรือ `OffsetX/Y` เพื่อดีบัก แล้วลดลงสำหรับการผลิต

## ขั้นตอนต่อไป

ตอนนี้คุณรู้วิธี **สร้างรูปสี่เหลี่ยม**, **ตั้งค่าความโปร่งใสของรูป**, **ตั้งค่าสีเงา**, และ **บันทึกเอกสาร Word** แล้ว ลองขยายบทเรียนต่อ:

- เพิ่มหลายรูปและจัดกลุ่ม
- แทรกรูปสี่เหลี่ยมลงในเซลล์ตารางสำหรับเลย์เอาต์รายงาน
- ผสานรูปกับ `DocumentBuilder.InsertHtml` เพื่อวางเนื้อหา HTML‑styled
- สำรวจเอฟเฟกต์ภาพอื่น ๆ เช่น `Glow` หรือ `Reflection` เพื่อสร้างเอกสารที่ดูเหมือน UI มากขึ้น

ทดลอง, ทำให้พัง, แล้วปรับปรุงต่อ—การสร้างเอกสารแบบโปรแกรมเป็นสนามเด็กเล่นที่การออกแบบภาพมาบรรจบกับโค้ด

---

*ขอให้สนุกกับการเขียนโค้ด! หากเจออุปสรรคใด ๆ แสดงความคิดเห็นด้านล่าง เราจะช่วยกันแก้ไข*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}