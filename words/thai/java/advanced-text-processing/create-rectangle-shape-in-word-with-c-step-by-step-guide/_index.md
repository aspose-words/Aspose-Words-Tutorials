---
category: general
date: 2026-03-04
description: เรียนรู้วิธีสร้างรูปสี่เหลี่ยม, เพิ่มเงาให้รูปและใช้เอฟเฟกต์เงาในเอกสาร
  Word, แล้วบันทึกเอกสาร Word โดยอัตโนมัติ.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: th
og_description: สร้างรูปสี่เหลี่ยม, เพิ่มเงาให้รูปและใช้เอฟเฟกต์เงาในเอกสาร Word ด้วย
  C#. ทำตามคู่มือนี้เพื่อบันทึกเอกสาร Word อย่างง่ายดาย.
og_title: Create rectangle shape in Word – Complete C# Tutorial
tags:
- C#
- Aspose.Words
- Document Automation
title: สร้างรูปสี่เหลี่ยมใน Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด
url: /th/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมใน Word ด้วย C# – คู่มือการเขียนโปรแกรมเต็มรูปแบบ

เคยต้องการ **สร้างรูปสี่เหลี่ยม** ในไฟล์ Word แต่ไม่แน่ใจว่าจะเริ่มอย่างไรหรือไม่? คุณไม่ได้อยู่คนเดียว—นักพัฒนาหลายคนเจออุปสรรคนี้เมื่อต้องเริ่มต้นการสร้างเอกสารโดยโปรแกรม วิธีที่ดีคือด้วยไม่กี่บรรทัดของ C# คุณสามารถแทรกรูปสี่เหลี่ยม, **เพิ่มเงาให้รูป** และ **ใช้เอฟเฟกต์เงา** ได้โดยไม่ต้องเปิด Word ด้วยตนเอง ในคู่มือนี้เราจะพาคุณผ่านกระบวนการทั้งหมด ตั้งแต่ **สร้างเอกสารเปล่า** ใหม่จนถึงการบันทึก **บันทึกไฟล์ Word** สุดท้ายลงดิสก์

เราจะครอบคลุมทุกอย่างที่คุณต้องการ: แพ็กเกจ NuGet ที่จำเป็น, API ที่ต้องใช้, เหตุผลที่แต่ละคุณสมบัติมีความสำคัญ, และเคล็ดลับเล็กน้อยเพื่อหลีกเลี่ยงข้อผิดพลาดที่พบบ่อยที่สุด เมื่อเสร็จสิ้นคุณจะมีตัวอย่างที่สามารถรันได้เต็มรูปแบบซึ่งสามารถนำไปใส่ในโครงการ .NET ใดก็ได้

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ทำงานได้กับ .NET Framework 4.7+ ด้วย)
- Visual Studio 2022 หรือ IDE ใดที่คุณชอบ
- **Aspose.Words for .NET** ติดตั้งผ่าน NuGet (`Install-Package Aspose.Words`)
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#

ไม่จำเป็นต้องใช้ไลบรารี Word interop เพิ่มเติม—Aspose.Words จัดการทุกอย่างในหน่วยความจำ

## ขั้นตอนที่ 1 – สร้างเอกสารเปล่า

สิ่งแรกที่เราทำคือ **สร้างเอกสารเปล่า** คิดว่าเป็นผืนผ้าใบว่างที่เราจะ **สร้างรูปสี่เหลี่ยม** ต่อไป

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **ทำไมเรื่องนี้ถึงสำคัญ:** การเริ่มต้นด้วยอ็อบเจ็กต์ `Document` ที่สะอาดช่วยรับประกันว่าไม่มีสไตล์หรือส่วนที่ซ่อนอยู่แทรกแซงตำแหน่งของรูปในภายหลัง

## ขั้นตอนที่ 2 – แทรกรูปสี่เหลี่ยมลงในเอกสาร

ตอนนี้เราจริง ๆ **สร้างรูปสี่เหลี่ยม** เราจะกำหนดขนาด, ตำแหน่ง, และบอก Word ไม่ให้ห่อข้อความรอบ ๆ รูป

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **เคล็ดลับ:** หากคุณต้องการให้รูปสี่เหลี่ยมอยู่ภายในเซลล์ตาราง ให้เปลี่ยน `WrapType` เป็น `WrapType.Inline` สำหรับรายงานส่วนใหญ่ `None` จะทำให้รูปลอยอยู่เหนือข้อความ

## ขั้นตอนที่ 3 – เพิ่มเงาให้รูปและกำหนดลักษณะการแสดงผล

นี่คือจุดที่เกิดความมหัศจรรย์: เรา **เพิ่มเงาให้รูป** และ **ใช้เอฟเฟกต์เงา** เงาจะทำให้รูปสี่เหลี่ยมโดดเด่นบนหน้า โดยเฉพาะเมื่อพิมพ์ออกมา

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **ทำไมต้องใช้ค่าดังนี้?**  
> - **BlurRadius** ควบคุมความเบลอของขอบ; ค่าใกล้เคียง `5` ให้ลุคที่ละเอียดอ่อนและเป็นมืออาชีพ  
> - **Transparency** ทำให้ข้อความพื้นหลังยังคงอ่านได้  
> - **OffsetX/Y** ย้ายเงาออกจากรูปเพื่อสร้างความลึก  
> - การใช้สี **น้ำเงิน** เป็นเพียงตัวอย่าง—คุณสามารถใช้ `System.Drawing.Color` ใดก็ได้

## ขั้นตอนที่ 4 – เพิ่มรูปที่กำหนดค่าแล้วลงในส่วนเนื้อหาเอกสาร

เมื่อรูปสี่เหลี่ยมได้รับการจัดรูปแบบครบถ้วน เราจะ **เพิ่มรูปสี่เหลี่ยม** ลงในส่วนแรกของเอกสาร ขั้นตอนนี้เป็นการวางรูปลงในไฟล์จริง

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **กรณีขอบ:** หากเอกสารของคุณมีหลายส่วนอยู่แล้ว คุณอาจต้องการระบุส่วนเฉพาะ (`doc.Sections[2]` เป็นตัวอย่าง) โค้ดด้านบนทำงานกับเอกสารที่มีเพียงส่วนเดียว ซึ่งเป็นที่พบบ่อยสำหรับรายงานแบบเร็ว

## ขั้นตอนที่ 5 – บันทึกไฟล์ Word

สุดท้าย เรา **บันทึกไฟล์ Word** ลงดิสก์ ไฟล์จะมีรูปสี่เหลี่ยมพร้อมเงา พร้อมเปิดใน Microsoft Word

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **เคล็ดลับ:** ใช้ `doc.Save(outputPath, SaveFormat.Docx)` หากคุณต้องการระบุรูปแบบอย่างชัดเจน เมธอด `Save` จะตรวจจับนามสกุลไฟล์โดยอัตโนมัติ แต่การระบุอย่างชัดเจนสามารถหลีกเลี่ยงความสับสนเมื่อเส้นทางไฟล์ถูกสร้างโดยโปรแกรม

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปพลิเคชันคอนโซล มันรวมคำสั่ง `using` ทั้งหมดและเมธอด `Main` ทำให้คุณสามารถรันได้ทันที

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิดไฟล์ *shadowed_rectangle.docx* ใน Microsoft Word คุณจะเห็นรูปสี่เหลี่ยมที่มีเส้นขอบสีฟ้าลอยอยู่ใกล้ด้านบนของหน้าแรก พร้อมเงาสีฟ้าอ่อนที่เลื่อน 8 pt ไปทางขวาและล่าง ไม่มีข้อความเพิ่มเติมล้อมรอบเนื่องจากเราได้ตั้งค่า `WrapType.None`

## คำถามที่พบบ่อยและรูปแบบต่าง ๆ

| Question | Answer |
|----------|--------|
| **ฉันสามารถเปลี่ยนรูปเป็นวงรีได้หรือไม่?** | ได้—เปลี่ยน `ShapeType.Rectangle` เป็น `ShapeType.Ellipse` คุณสมบัติเงาทั้งหมดจะคงเดิม |
| **ถ้าฉันต้องการหลายรูปล่ะ?** | เพียงทำซ้ำขั้นตอน 2‑4 สำหรับแต่ละอินสแตนซ์ `Shape` ใหม่ ปรับ `OffsetX/Y` หรือ `Left/Top` เพื่อหลีกเลี่ยงการทับซ้อน |
| **มีวิธีทำให้สีเงาตรงกับสีเติมของรูปหรือไม่?** | แน่นอน ตั้งค่า `rectangle.FillColor` ก่อน แล้วกำหนด `rectangle.ShadowFormat.Color = rectangle.FillColor;` |
| **ฉันจะแทรกรูปลงในเซลล์ตารางอย่างไร?** | ใช้ `cell.FirstParagraph.AppendChild(rectangle);` หลังจากค้นหาอ็อบเจ็กต์ `Cell` ที่ต้องการ |
| **วิธีนี้จะทำงานบน .NET Core หรือไม่?** | ได้—Aspose.Words รองรับหลายแพลตฟอร์ม เพียงตรวจสอบว่าคุณอ้างอิงเวอร์ชัน NuGet ที่เหมาะสมสำหรับ .NET Core/5/6 |

## ข้อผิดพลาดทั่วไปและเคล็ดลับมืออาชีพ

- **ข้อผิดพลาด:** ลืมตั้งค่า `ShadowFormat.Visible = true` คุณสมบัติเงาจะถูกละเลยโดยไม่มีการแจ้งเตือน  
  **วิธีแก้:** ควรเปิดการมองเห็นเสมอก่อนปรับพารามิเตอร์เงาอื่น ๆ
- **ข้อผิดพลาด:** ใช้ `BlurRadius` ใหญ่เกินไป (เช่น 20) ทำให้เงาดูเบลอและไม่เป็นมืออาชีพ  
  **วิธีแก้:** ใช้ค่าระหว่าง `3` ถึง `8` สำหรับเอกสารธุรกิจส่วนใหญ่
- **เคล็ดลับ:** หากคุณต้องการให้รูปสามารถเลือกได้ในภายหลัง (เช่น เพื่อให้ผู้ใช้แก้ไข) ควรหลีกเลี่ยงการตั้งค่า `WrapType.Inline` รูปแบบลอย (`WrapType.None`) จะย้ายได้ง่ายกว่าโดยโปรแกรม
- **เคล็ดลับ:** เมื่อสร้างเอกสารหลายไฟล์ในลูป ให้ใช้ `Document` ตัวเดียวและเรียก `doc.Clone(true)` สำหรับแต่ละรอบเพื่อเพิ่มประสิทธิภาพ

## หัวข้อที่เกี่ยวข้องที่คุณอาจสนใจต่อไป

- **เพิ่มข้อความภายในรูปสี่เหลี่ยม** – เรียนรู้การใช้ `Shape.TextPath` สำหรับป้ายชื่อ  
- **สร้างแผนภาพซับซ้อน** – รวมหลายรูป, ตัวเชื่อมต่อ, และการจัดกลุ่ม  
- **ส่งออกเป็น PDF** – แปลงเอกสารเดียวกันเป็น PDF ด้วยคำสั่ง `doc.Save("output.pdf")` เพียงครั้งเดียว  
- **ใช้สไตล์การเติมที่ต่างกัน** – การไล่สี, เนื้อผิว, หรือแม้กระทั่งรูปภาพภายในรูป

## สรุป

เราได้ **สร้างรูปสี่เหลี่ยม**, **เพิ่มเงาให้รูป**, และ **ใช้เอฟเฟกต์เงา** ในไฟล์ Word ด้วย C# แล้ว ด้วยการทำตามห้าขั้นตอนสั้น ๆ นี้คุณจะมีรูปแบบที่นำกลับมาใช้ได้สำหรับสถานการณ์อัตโนมัติของเอกสารใด ๆ และคุณรู้วิธี **บันทึกไฟล์ Word** อย่างมั่นใจ อย่าลังเลที่จะปรับขนาด, สี, หรือแม้แต่เปลี่ยนรูปสี่เหลี่ยมเป็นรูปทรงอื่น—Aspose.Words ทำให้ทุกอย่างง่ายดาย

หากคุณพบว่าคู่มือนี้เป็นประโยชน์ ให้กดดาวบน GitHub หรือแบ่งปันรูปแบบของคุณในคอมเมนต์ ขอให้สนุกกับการเขียนโค้ด และขอให้เอกสารของคุณดูเรียบหรูเสมอเหมือนรูปสี่เหลี่ยมที่มีเงานี้!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}