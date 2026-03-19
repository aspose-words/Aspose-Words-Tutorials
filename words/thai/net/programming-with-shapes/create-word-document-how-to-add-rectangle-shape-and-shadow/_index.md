---
category: general
date: 2026-03-19
description: สร้างเอกสาร Word ด้วย C# และ Aspose.Words, เรียนรู้วิธีเพิ่มรูปทรง, เพิ่มรูปสี่เหลี่ยม,
  ใส่เงา, และบันทึกเอกสารเป็นไฟล์ docx ภายในไม่กี่นาที.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: th
og_description: สร้างเอกสาร Word ด้วย Aspose.Words, เพิ่มรูปสี่เหลี่ยม, ใช้เงานอก,
  แล้วบันทึกเอกสารเป็นไฟล์ docx. คู่มือแบบทีละขั้นตอน.
og_title: สร้างเอกสาร Word – เพิ่มรูปสี่เหลี่ยมและเงา
tags:
- Aspose.Words
- C#
- Document Automation
title: สร้างเอกสาร Word – วิธีเพิ่มรูปสี่เหลี่ยมและเงา
url: /th/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word – วิธีเพิ่มรูปสี่เหลี่ยมและเงา

เคยต้องการ **create word document** ด้วยโปรแกรมและสงสัยว่าจะเริ่มต้นอย่างไรหรือไม่? คุณไม่ได้อยู่คนเดียว นักพัฒนาหลายคนเจออุปสรรคเดียวกันเมื่อต้องสร้างไฟล์ .docx ที่มีกราฟิกแบบกำหนดเอง ในบทเรียนนี้เราจะพาคุณผ่านกระบวนการทั้งหมด—วิธีเพิ่ม shape, โดยเฉพาะ **add rectangle shape**, ให้มี **add shadow to shape** ที่สวยงาม, และสุดท้าย **save document as docx**.  

เมื่อจบคู่มือคุณจะได้สคริปต์ C# ที่พร้อมใช้งานซึ่งสามารถนำไปใส่ในโปรเจกต์ .NET ใดก็ได้ ไม่มีการอ้างอิงที่คลุมเครือ เพียงตัวอย่างที่สมบูรณ์และสามารถรันได้  

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดทำงานกับ .NET Framework ด้วย)  
- ติดตั้ง Aspose.Words for .NET (แพ็กเกจ NuGet `Aspose.Words`)  
- ความเข้าใจพื้นฐานของไวยากรณ์ C#—ไม่ต้องการความซับซ้อนใดๆ  

หากคุณยังไม่มีไลบรารี ให้รัน:

```bash
dotnet add package Aspose.Words
```

เท่านี้—ไม่มี SDK เพิ่มเติม, ไม่มี COM interop, เพียงการอ้างอิง NuGet เดียว.

## ขั้นตอนที่ 1: สร้างเอกสาร Word (เป้าหมายหลัก)

สิ่งแรกที่เราต้องการคือผืนผ้าใบที่สะอาด คิดว่า `Document` class เป็นหน้ากระดาษใหม่ใน Microsoft Word; มันเก็บ sections, paragraphs, และทุกอย่างที่คุณจะเพิ่มต่อไป.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

ทำไมต้องเริ่มด้วย `Document` ว่าง? เพราะมันรับประกันว่าจะไม่มีการฟอร์แมตที่ซ่อนอยู่จากเทมเพลต ในประสบการณ์ของผม การเริ่มจากศูนย์ช่วยหลีกเลี่ยงการเปลี่ยนแปลงเลย์เอาต์ที่ไม่คาดคิดเมื่อคุณแทรก shape ต่อมา.

## ขั้นตอนที่ 2: แทรกรูปสี่เหลี่ยม – การเพิ่มองค์ประกอบภาพ

ตอนนี้เรามีเอกสารแล้ว ให้ **add rectangle shape** ไปยังย่อหน้าแรก `Shape` object มีความยืดหยุ่น; คุณสามารถเลือก `ShapeType.Rectangle`, `Ellipse` หรือแม้กระทั่งการวาดแบบกำหนดเอง นี่คือโค้ดที่สั้นที่สุด:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**อะไรกำลังเกิดขึ้นเบื้องหลัง?**  

- `ShapeType.Rectangle` บอก Aspose ว่าเราต้องการกล่องง่ายๆ  
- `WrapType.Inline` ทำให้สี่เหลี่ยมเคลื่อนที่ตามการไหลของข้อความ ซึ่งเป็นสิ่งที่คาดหวังในสถานการณ์การประมวลผลคำ  
- โดยการต่อท้าย `FirstParagraph` เราหลีกเลี่ยงการต้องแทรกย่อหน้าใหม่ด้วยตนเอง; Aspose จะสร้างให้ถ้าเอกสารว่างเปล่า  

> **เคล็ดลับ:** หากคุณต้องการให้ shape อยู่ *ด้านหลัง* ข้อความ ให้เปลี่ยน `WrapType` เป็น `WrapType.Transparent`. การเปลี่ยนแปลงเล็กน้อยนี้สามารถทำให้ภาพดูแตกต่างอย่างมาก.

## ขั้นตอนที่ 3: ใส่เงานอก – ปรับปรุงรูปลักษณ์

สี่เหลี่ยมแบนเป็น… แค่แบน การเพิ่ม **add shadow to shape** จะทำให้มีมิติโดยไม่ต้องใช้รูปภาพเพิ่มเติม `ShadowFormat` ของ Aspose ทำให้เป็นบรรทัดเดียว.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

ทำไมต้องใช้ค่าที่ระบุเหล่านั้น?  

- **Blur** ที่ `5.0` ให้ขอบที่เบาบางและดูเป็นมืออาชีพบนจอส่วนใหญ่  
- **Distance** ที่ `3.0` และ **Angle** ที่ `45` สร้างแหล่งแสงธรรมชาติจากด้านบน‑ซ้าย ซึ่งเป็นแนวทางการออกแบบทั่วไป  
- `Color.Gray` ทำงานได้ทั้งธีมสว่างและมืด; คุณสามารถเปลี่ยนเป็น `Color.Black` หากต้องการคอนทราสต์ที่แรงขึ้น  

หากต้องการ *inner* shadow (เช่น ปุ่มที่กดลง) เพียงเปลี่ยน `ShadowType.OuterShadow` เป็น `ShadowType.InnerShadow`. คุณสมบัติเหล่านั้นยังคงใช้ได้

## ขั้นตอนที่ 4: บันทึกเอกสารเป็น DOCX – เก็บงานของคุณ

ความสนุกทั้งหมดดี แต่สุดท้ายคุณต้องการไฟล์บนดิสก์ ขั้นตอน **save document as docx** ง่ายมาก:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

หมายเหตุบางประการ:  

- `SaveFormat.Docx` enum รับประกันรูปแบบ Office Open XML สมัยใหม่ ซึ่งเข้ากันได้กับ Word 2007+.  
- หากต้องการสตรีมไฟล์โดยตรงไปยังการตอบสนองเว็บ ให้แทนที่เส้นทางไฟล์ด้วย `MemoryStream` แล้วเขียนไปยัง HTTP response.  

หลังจากรันโค้ด เปิดไฟล์ `ShadowedRectangle.docx` ใน Microsoft Word คุณควรเห็นสี่เหลี่ยมสีเทาพร้อมเงานุ่มนวล อยู่ในแนวเดียวกับย่อหน้าแรก—ตรงกับที่เราตั้งเป้าหมาย.

## วิธีเพิ่ม Shape – วิธีทางเลือก

ตัวอย่างข้างต้นใช้วิธี *inline* แต่บางครั้งคุณต้องการ shape ที่ลอยเหนือข้อความ นั่นคือจุดที่ **how to add shape** พร้อมการห่อหุ้มแบบต่างๆ เข้ามาใช้.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

ที่นี่เราเปลี่ยน `WrapType` เป็น `Square` และจัดศูนย์ shape บนหน้า รูปแบบนี้มีประโยชน์สำหรับหน้าปกหรือแบนเนอร์ตกแต่ง จำไว้ว่า: shape ที่ลอยจะทำให้ไฟล์ขนาดใหญ่ขึ้นเล็กน้อยเนื่องจาก Word เก็บข้อมูลตำแหน่งเพิ่มเติม.

## ผลลัพธ์ที่คาดหวังและการตรวจสอบ

เมื่อคุณเปิดไฟล์ที่สร้างขึ้น คุณควรเห็น:

- ย่อหน้าเดียวที่มีสี่เหลี่ยมสีเทา  
- สี่เหลี่ยมมีขนาดประมาณ 2.8 × 1.4 นิ้ว  
- เงานอกแบบเบาบางที่เลื่อนไปด้านล่าง‑ขวา  

หาก shape ปรากฏ *นอก* ย่อหน้า ให้ตรวจสอบ `WrapType` อีกครั้ง หากเงาดูแรงเกินไป ให้ลดค่าของ `Blur` หรือเปลี่ยน `Color` เป็นเฉดสีอ่อนกว่า.

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Shape หายหลังบันทึก | `WrapType` ตั้งเป็น `Inline` แต่ย่อหน้าถูกลบ | ตรวจสอบให้ย่อหน้ามีอยู่; ใช้ `doc.FirstSection.Body.FirstParagraph` เพื่อรับประกัน |
| Shadow ดูเป็นพิกเซล | ใช้ค่า `Blur` ต่ำมาก | เพิ่มค่า `Blur` อย่างน้อยเป็น `3.0` เพื่อให้ขอบเรียบ |
| ขนาดไฟล์พุ่งสูง | เพิ่มรูปภาพความละเอียดสูงหลายรูปพร้อมกับ shape | ใช้ `doc.RemoveUnusedResources()` ก่อนบันทึกหากคุณได้เพิ่มรูปภาพ |
| สีไม่แสดงในโหมดมืด | ใช้ `Color` สีเข้มสำหรับ shape เอง | เลือกสีที่ตัดกัน (เช่น `Color.White`) เพื่อให้มองเห็นได้ชัดเจน |

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโค้ดที่สมบูรณ์พร้อมคัดลอก‑วางที่รวมทุกอย่างที่เราได้พูดถึง คุณสามารถรันเป็นแอปคอนโซลได้เลย.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Explanation of each block** อยู่ในบรรทัดคอมเมนต์, ตอบสนองผู้อ่าน SEO และผู้ช่วย AI ที่ชอบคำตอบที่มีทุกอย่างในตัว.

## สรุป

เราเพิ่ง **create word document** ตั้งแต่ต้น, เรียนรู้ **how to add shape**, โดยเฉพาะ **add rectangle shape**, ให้มี **add shadow to shape**, และสุดท้าย **save document as docx** ขั้นตอนง่าย โค้ดกระชับ และผลลัพธ์ดูเรียบหรู  

หากคุณพร้อมพัฒนาเพิ่มเติม ลองเปลี่ยนสี่เหลี่ยมเป็นรูปภาพกำหนดเอง, ทดลองสีเงาต่างๆ, หรือสร้างรายงานเต็มรูปแบบที่มีหลายส่วนที่มี shape API Aspose.Words มีความยืดหยุ่นพอที่จะจัดการทุกอย่างตั้งแต่ใบแจ้งหนี้จนถึงโบรชัวร์การตลาด  

มีคำถามเกี่ยวกับประเภท shape อื่นหรืออยากได้ความช่วยเหลือในการผสานเข้ากับบริการ ASP.NET Core? แสดงความคิดเห็นด้านล่าง แล้วขอให้สนุกกับการเขียนโค้ด!  

![สร้างเอกสาร word พร้อมรูปสี่เหลี่ยมและเงา](placeholder-image.png "สร้างเอกสาร word พร้อมรูปสี่เหลี่ยมและเงา

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}