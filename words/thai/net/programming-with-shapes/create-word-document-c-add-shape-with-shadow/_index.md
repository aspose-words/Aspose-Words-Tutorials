---
category: general
date: 2026-03-27
description: สร้างเอกสาร Word ด้วย C# และเรียนรู้วิธีเพิ่มรูปทรง, ใส่เงาให้รูปทรง,
  และตั้งค่าระยะเงา คู่มือขั้นตอนโดยละเอียดสำหรับ Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: th
og_description: สร้างเอกสาร Word ด้วย C# พร้อมรูปสี่เหลี่ยมและเงาที่กำหนดเอง ทำตามบทเรียนฉบับเต็มนี้เพื่อกำหนดระยะห่างและสไตล์ของเงา.
og_title: สร้างเอกสาร Word ด้วย C# – เพิ่มรูปทรงพร้อมเงา
tags:
- Aspose.Words
- C#
- Document Automation
title: สร้างเอกสาร Word ด้วย C# – เพิ่มรูปทรงพร้อมเงา
url: /th/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้าง Word Document C# – เพิ่มรูปร่างพร้อมเงา

เคยต้องการ **create word document c#** ที่มีสี่เหลี่ยมผืนผ้าตกแต่งอย่างสวยงามหรือไม่? บางทีคุณอาจกำลังสร้างเทมเพลตรายงานและต้องการเงาตกที่ละเอียดเพื่อทำให้การจัดวางโดดเด่นขึ้น ในบทแนะนำนี้เราจะอธิบายขั้นตอนนั้น – วิธีเพิ่มรูปร่าง, ใช้เงากับรูปร่าง, และแม้กระทั่งปรับระยะเงาโดยใช้ Aspose.Words.

เราจะเริ่มจากเอกสารเปล่า, แทรกสี่เหลี่ยม, ให้เงาตั้งล่วงหน้า, แล้วบันทึกไฟล์ เมื่อเสร็จคุณจะได้ไฟล์ .docx ที่พร้อมใช้งานซึ่งสามารถเปิดใน Word และเห็นผลทันที ไม่ต้องใช้เครื่องมือภายนอก เพียงแค่โค้ด C# ธรรมดา

## ข้อกำหนดเบื้องต้น

- .NET 6 (หรือ .NET Framework เวอร์ชันล่าสุด) ที่ติดตั้งแล้ว
- Visual Studio 2022 หรือ VS Code พร้อมส่วนขยาย C#
- Aspose.Words for .NET NuGet package (`Aspose.Words` version 23.12 หรือใหม่กว่า)  
  คุณสามารถเพิ่มได้ผ่าน Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

แค่นั้นเอง – ไม่ต้องใช้ DLL เพิ่มเติมหรือ COM interop

## ขั้นตอนที่ 1: เริ่มต้นเอกสารใหม่และ Builder – *create word document c#* Basics

ก่อนอื่นเราต้องการอ็อบเจ็กต์ `Document` ที่เป็นตัวแทนไฟล์ Word และ `DocumentBuilder` เพื่อแก้ไขมัน

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **ทำไมขั้นตอนนี้สำคัญ:** คลาส `Document` เป็นคอนเทนเนอร์สำหรับส่วนต่าง ๆ ของ Word (หน้า, สไตล์, รูปภาพ) Builder เป็น API ระดับสูงที่ซ่อนการจัดการโหนดระดับล่าง ทำให้คุณสามารถ **create word document c#** ได้ง่ายโดยไม่ต้องจัดการ XML ด้วยตนเอง

## ขั้นตอนที่ 2: แทรกรูปร่างสี่เหลี่ยม – *how to create rectangle*  

ตอนนี้เราจะวางสี่เหลี่ยมบนหน้า ขนาดจะระบุเป็นจุด (1 pt ≈ 1/72 in)

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **เคล็ดลับ:** หากต้องการรูปร่างอื่น เพียงเปลี่ยน `ShapeType.Rectangle` เป็น `ShapeType.Ellipse`, `ShapeType.Triangle` ฯลฯ โค้ดเดียวกันทำงานได้กับ **how to add shape** ทุกประเภท

## ขั้นตอนที่ 3: ใช้เงาตั้งล่วงหน้าและปรับแต่ง – *apply shadow to shape*  

Aspose.Words มีเงาตั้งล่วงหน้าหลายแบบ เราจะใช้ `Preset1` แล้วปรับระยะ, ความเบลอ, ความโปร่งใส, และสีตามต้องการ

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **ทำไมต้องปรับเงา:** คุณสมบัติ `Distance` ควบคุมระยะห่างของเงาจากสี่เหลี่ยม – เหมือนกับ “การยก” ที่เห็นในเรนเดอร์ 3‑D การเปลี่ยน `BlurRadius` ทำให้ขอบนุ่มขึ้น ส่วน `Transparency` ช่วยสร้างลุคที่ละเอียดและเป็นมืออาชีพ สิ่งนี้ตอบสนองความต้องการ **set shadow distance** และแสดงวิธี **apply shadow to shape** อย่างยืดหยุ่น

## ขั้นตอนที่ 4: บันทึกเอกสาร – *create word document c#* Completion

สุดท้ายให้เขียนเอกสารลงดิสก์ ปรับเส้นทางให้ชี้ไปยังโฟลเดอร์ที่คุณมีสิทธิ์เขียน

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

เปิดไฟล์ที่ได้ใน Microsoft Word คุณจะเห็นสี่เหลี่ยมสีฟ้าอ่อนพร้อมเงาสีเทานุ่มที่เลื่อนออก 5 pt นั่นคือหลักฐานว่าคุณได้ **create word document c#** พร้อมรูปร่างที่ตกแต่งเรียบร้อยแล้ว

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="สร้างเอกสาร word c# ตัวอย่างแสดงสี่เหลี่ยมพร้อมเงา"}

## ตัวแปรเพิ่มเติม & กรณีขอบ

| Scenario | What to Change | Why it Matters |
|----------|----------------|----------------|
| **สไตล์เงาที่แตกต่าง** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | ให้ลุคที่ดราม่ามากขึ้นโดยไม่ต้องเขียนโค้ดเพิ่มเติม |
| **ไม่มี preset – เงากำหนดเอง** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | ควบคุมเต็มที่เกี่ยวกับทิศทางและความลึก |
| **หลายรูปร่าง** | Call `builder.InsertShape` again before saving. | มีประโยชน์สำหรับเทมเพลตซับซ้อนที่มีไอคอน, โลโก้ ฯลฯ |
| **ความเข้ากันได้กับเวอร์ชัน Aspose เก่า** | Use `ShadowEffect` class (available in v20.x). | ทำให้แน่ใจว่าโค้ดของคุณทำงานบนโครงการเก่า |
| **บันทึกเป็น PDF** | `document.Save("ShadowShape.pdf");` | การเรนเดอร์เงาเดียวกันจะปรากฏในไฟล์ PDF |

> **คำถามทั่วไป:** *ถ้าเงาไม่แสดงใน Word จะทำอย่างไร?*  
> ตรวจสอบว่าคุณใช้ Aspose.Words เวอร์ชันล่าสุด (≥ 22.9) รุ่นเก่ามีการสนับสนุนเงาที่จำกัด และตรวจสอบว่าเปิดเอกสารด้วย Word เวอร์ชันใหม่ (2016+) ด้วย

## ตัวอย่างการทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่พร้อมคัดลอกและวาง ใช้ `using` directive ทั้งหมด, คอมเมนต์, และการจัดการข้อผิดพลาดเพื่อประสบการณ์ที่ราบรื่น

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

เรียกใช้โปรแกรม, ไปที่ `C:\Temp\ShadowShape.docx` แล้วคุณจะเห็นสี่เหลี่ยมพร้อมเงาที่กำหนดไว้ตรงตามที่ตั้งค่า

## สรุป & ขั้นตอนต่อไป

- ตอนนี้คุณรู้วิธี **create word document c#**, แทรกสี่เหลี่ยม, และ **apply shadow to shape** พร้อม **set shadow distance** ที่กำหนดเอง  
- ตัวอย่างใช้ Aspose.Words ซึ่งทำให้ซับซ้อนของ OpenXML หายไปและรับประกันการเรนเดอร์ที่สม่ำเสมอในทุกเวอร์ชันของ Word  
- อยากไปต่อ? ลองรวมหลายรูปร่าง, เพิ่มข้อความภายในสี่เหลี่ยม, หรือส่งออกเป็น PDF เพื่อดูว่าการเงาถูกแปลงอย่างไร

### หัวข้อที่เกี่ยวข้องที่คุณอาจสนใจ

- **How to add shape** ไปยังส่วนหัว/ส่วนท้ายเพื่อสร้างแบรนด์  
- ใช้ **Aspose.Words** แทรกแผนภูมิและตารางโดยอัตโนมัติ  
- ปรับแต่ง **shadow effects** บนรูปภาพแทนรูปเวกเตอร์  
- อัตโนมัติการสร้างเอกสารจำนวนมากสำหรับใบแจ้งหนี้หรือใบรับรอง

ทดลองเล่น, ทำให้โค้ดพัง, แล้วสร้างใหม่ – นั่นคือวิธีที่เร็วที่สุดในการทำความเข้าใจแนวคิด หากเจออุปสรรคใด ๆ คอมเมนต์ด้านล่างหรือดูเอกสาร Aspose.Words อย่างเป็นทางการเพื่อข้อมูลเชิงลึกของ API

ขอให้เขียนโค้ดอย่างสนุกและทำให้ไฟล์ Word ของคุณดูเป็นมืออาชีพยิ่งขึ้น!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}