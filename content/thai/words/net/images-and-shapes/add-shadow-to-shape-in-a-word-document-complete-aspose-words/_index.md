---
category: general
date: 2025-12-08
description: เพิ่มเงาให้กับรูปทรงอย่างรวดเร็วด้วย Aspose.Words. เรียนรู้วิธีสร้างเอกสาร
  Word ด้วย Aspose, วิธีเพิ่มเงาให้รูปทรง, และการใช้ความโปร่งใสของเงาใน C#
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: th
og_description: เพิ่มเงาให้กับรูปร่างในไฟล์ Word ด้วย Aspose.Words คู่มือแบบทีละขั้นตอนนี้แสดงวิธีสร้างเอกสาร,
  เพิ่มรูปร่าง, และกำหนดความโปร่งใสของเงา.
og_title: เพิ่มเงาให้รูปร่าง – บทแนะนำ Aspose.Words C#
tags:
- Aspose.Words
- C#
- Word Automation
title: เพิ่มเงาให้รูปทรงในเอกสาร Word – คู่มือ Aspose.Words ฉบับสมบูรณ์
url: /thai/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# เพิ่มเงาให้รูปทรง – คู่มือ Aspose.Words ฉบับสมบูรณ์

เคยต้องการ **เพิ่มเงาให้รูปทรง** ในไฟล์ Word แต่ไม่แน่ใจว่าจะใช้ API ใด? คุณไม่ได้เป็นคนเดียว นักพัฒนาหลายคนเจออุปสรรคเมื่อลองเพิ่มเงาตกให้กับสี่เหลี่ยมหรือองค์ประกอบการวาดใด ๆ ครั้งแรก โดยเฉพาะเมื่อทำงานกับ Aspose.Words สำหรับ .NET  

ในบทแนะนำนี้เราจะพาคุณผ่านทุกอย่างที่ต้องรู้: ตั้งแต่ **การสร้างเอกสาร Word ด้วย Aspose** ไปจนถึงการกำหนดค่าเงา ปรับความเบลอ ระยะห่าง มุม และแม้กระทั่ง **การใช้ความโปร่งใสของเงา**. เมื่อจบคุณจะมีโปรแกรม C# ที่พร้อมรันซึ่งสร้างไฟล์ `.docx` ที่มีสี่เหลี่ยมที่มีเงาอย่างสวยงาม—ไม่ต้องแก้ไขด้วยตนเองใน Word  

---

## สิ่งที่คุณจะได้เรียนรู้

- วิธีตั้งค่าโครงการ Aspose.Words ใน Visual Studio.  
- ขั้นตอนที่แน่นอนในการ **สร้างเอกสาร Word ด้วย Aspose** และแทรกรูปทรง.  
- **วิธีเพิ่มเงาให้รูปทรง** พร้อมการควบคุมเต็มที่ของความเบลอ ระยะห่าง มุม และความโปร่งใส.  
- เคล็ดลับการแก้ไขปัญหาที่พบบ่อย (เช่น ไฟล์ใบอนุญาตหาย, หน่วยไม่ถูกต้อง).  
- ตัวอย่างโค้ดที่ครบถ้วนพร้อมคัดลอก‑วางที่คุณสามารถรันได้วันนี้.  

> **ข้อกำหนดเบื้องต้น:** .NET 6+ (หรือ .NET Framework 4.7.2+), ใบอนุญาต Aspose.Words ที่ถูกต้อง (หรือทดลองใช้ฟรี), และความคุ้นเคยพื้นฐานกับ C#.

## ขั้นตอนที่ 1 – ตั้งค่าโครงการของคุณและเพิ่ม Aspose.Words

สิ่งแรกที่ต้องทำ เปิด Visual Studio, สร้าง **Console App (.NET Core)** ใหม่, และเพิ่มแพคเกจ NuGet ของ Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **เคล็ดลับ:** หากคุณมีไฟล์ใบอนุญาต (`Aspose.Words.lic`), คัดลอกไปยังโฟลเดอร์รากของโครงการและโหลดในตอนเริ่มต้น. วิธีนี้จะหลีกเลี่ยงลายน้ำที่ปรากฏในโหมดทดลองใช้ฟรี.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

## ขั้นตอนที่ 2 – สร้างเอกสารเปล่าใหม่

ตอนนี้เราจริง ๆ **สร้างเอกสาร Word ด้วย Aspose**. วัตถุนี้จะทำหน้าที่เป็นผ้าใบสำหรับรูปทรงของเรา.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

`Document` class เป็นจุดเริ่มต้นสำหรับทุกอย่างอื่น—ย่อหน้า, ส่วน, และแน่นอนว่าอ็อบเจกต์การวาด.

## ขั้นตอนที่ 3 – แทรกรูปทรงสี่เหลี่ยม

เมื่อเอกสารพร้อม เราสามารถเพิ่มรูปทรงได้ ที่นี่เราเลือกสี่เหลี่ยมง่าย ๆ แต่ตรรกะเดียวกันใช้ได้กับวงกลม, เส้น, หรือรูปหลายเหลี่ยมที่กำหนดเอง.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

**ทำไมต้องใช้รูปทรง?** ใน Aspose.Words อ็อบเจกต์ `Shape` สามารถเก็บข้อความ, รูปภาพ, หรือทำหน้าที่เป็นองค์ประกอบตกแต่ง. การเพิ่มเงาให้รูปทรงง่ายกว่าการจัดการกับกรอบรูปภาพมาก.

## ขั้นตอนที่ 4 – กำหนดค่าเงา (เพิ่มเงาให้รูปทรง)

นี่คือหัวใจของบทแนะนำ—**วิธีเพิ่มเงาให้รูปทรง** และปรับแต่งลักษณะอย่างละเอียด. คุณสมบัติ `ShadowFormat` ให้คุณควบคุมเต็มที่.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### สิ่งที่แต่ละคุณสมบัติทำ

| Property | Effect | Typical Values |
|----------|--------|----------------|
| **Visible** | เปิดหรือปิดเงา. | `true` / `false`| **Blur** | ทำให้ขอบเงานุ่มนวล. | `0` (hard) to `10` (very soft) |
| **Distance** | ย้ายเงาออกจากรูปทรง. | `1`–`5` points is common |
| **Angle** | ควบคุมทิศทางของการเลื่อน. | `0`–`360` degrees |
| **Transparency** | ทำให้เงาโปร่งแสงบางส่วน. | `0` (opaque) to `1` (invisible) |

**กรณีขอบ:** หากคุณตั้งค่า `Transparency` เป็น `1` เงาจะหายไปทั้งหมด—มีประโยชน์สำหรับการสลับเงาโดยโปรแกรม.

## ขั้นตอนที่ 5 – เพิ่มรูปทรงลงในเอกสาร

ตอนนี้เราจะผูกรูปทรงกับย่อหน้าแรกของส่วนเนื้อหาเอกสาร. Aspose จะสร้างย่อหน้าโดยอัตโนมัติหากไม่มี.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

หากเอกสารของคุณมีเนื้อหาอยู่แล้ว คุณสามารถแทรกรูปทรงที่โหนดใดก็ได้โดยใช้ `InsertAfter` หรือ `InsertBefore`.

## ขั้นตอนที่ 6 – บันทึกเอกสาร

สุดท้าย เขียนไฟล์ลงดิสก์. คุณสามารถเลือกฟอร์แมตที่รองรับใดก็ได้ (`.docx`, `.pdf`, `.odt`, เป็นต้น) แต่สำหรับบทแนะนำนี้เราจะใช้ฟอร์แมต Word ดั้งเดิม.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

เปิดไฟล์ `ShadowedShape.docx` ที่สร้างขึ้นใน Microsoft Word, คุณจะเห็นสี่เหลี่ยมที่มีเงานุ่ม, มุม 45°, ความโปร่งใส 30 %—ตรงกับที่เราตั้งค่า.

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรม **ครบถ้วนพร้อมคัดลอก‑วาง** ที่รวมทุกขั้นตอนข้างต้น. บันทึกเป็น `Program.cs` แล้วรันด้วย `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** ไฟล์ชื่อ `ShadowedShape.docx` ที่มีสี่เหลี่ยมเดียวที่มีเงาตกแบบครึ่งโปร่งใสและมุม 45°.

## ความแปรผันและเคล็ดลับขั้นสูง

### การเปลี่ยนสีเงา

โดยค่าเริ่มต้นเงาจะสืบทอดสีเติมของรูปทรง, แต่คุณสามารถตั้งค่าสีกำหนดเองได้:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### หลายรูปทรงพร้อมเงาต่างกัน

หากต้องการหลายรูปทรง เพียงทำซ้ำขั้นตอนการสร้างและกำหนดค่า. จำไว้ว่าต้องตั้งชื่อแต่ละรูปทรงให้เป็นเอกลักษณ์หากต้องการอ้างอิงในภายหลัง.

### การส่งออกเป็น PDF พร้อมรักษาเงา

Aspose.Words จะรักษาเอฟเฟกต์เงาเมื่อบันทึกเป็น PDF:

```csharp
doc.Save("ShadowedShape.pdf");
```

### ปัญหาที่พบบ่อย

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|-------|-------------------|---------|
| เงาไม่แสดง | `ShadowFormat.Visible` ถูกทิ้งไว้เป็น `false` | ตั้งค่าเป็น `true |
| เงาดูแข็งเกินไป | `Blur` ตั้งเป็น `0` | เพิ่มค่า `Blur` เป็น 3–6. |
| เงาหายไปใน PDF | ใช้เวอร์ชันเก่าของ Aspose.Words (< 22.9) | อัปเกรดเป็นไลบรารีล่าสุด. |

## สรุป

เราได้ครอบคลุม **วิธีเพิ่มเงาให้รูปทรง** ด้วย Aspose.Words ตั้งแต่การเริ่มต้นเอกสารจนถึงการปรับแต่งความเบลอ, ระยะ, มุม, และ **การใช้ความโปร่งใสของเงา**. ตัวอย่างเต็มแสดงวิธีที่สะอาดและพร้อมใช้งานในผลิตภัณฑ์ที่คุณสามารถปรับใช้กับรูปทรงหรือเลย์เอาต์เอกสารใดก็ได้.  

มีคำถามเกี่ยวกับ **การสร้างเอกสาร Word ด้วย Aspose** สำหรับสถานการณ์ที่ซับซ้อนกว่า—เช่น ตารางที่มีเงาหรือรูปทรงที่สร้างจากข้อมูลแบบไดนามิก? แสดงความคิดเห็นด้านล่างหรือดูบทแนะนำที่เกี่ยวข้องเกี่ยวกับการจัดการภาพและการจัดรูปแบบย่อหน้าใน Aspose.Words.  

ขอให้เขียนโค้ดอย่างสนุกสนานและเพลิดเพลินกับการเพิ่มความสวยงามให้กับเอกสาร Word ของคุณ!  

--- 

![ตัวอย่างการเพิ่มเงาให้รูปทรง](shadowed_shape.png "ตัวอย่างการเพิ่มเงาให้รูปทรง")

{{< layout-end >}}

{{< layout-end >}}