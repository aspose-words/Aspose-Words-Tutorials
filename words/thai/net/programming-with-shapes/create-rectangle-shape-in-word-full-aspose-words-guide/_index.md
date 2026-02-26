---
category: general
date: 2026-02-26
description: สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words และเรียนรู้วิธีเพิ่มรูปลงใน
  Word ใส่เงาให้รูป และตั้งค่าความโปร่งใสของรูปภายในไม่กี่นาที
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: th
og_description: สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words เรียนรู้วิธีเพิ่มรูปลงใน
  Word ใช้เงากับรูป และตั้งค่าความโปร่งใสของรูปอย่างรวดเร็ว
og_title: สร้างรูปสี่เหลี่ยมใน Word – คู่มือ Aspose.Words ฉบับเต็ม
tags:
- Aspose.Words
- C#
- Word Automation
title: สร้างรูปสี่เหลี่ยมใน Word – คู่มือ Aspose.Words ฉบับเต็ม
url: /th/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

Proceed.

Let's produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมใน Word – คู่มือ Aspose.Words ฉบับเต็ม

เคยต้อง **สร้างรูปสี่เหลี่ยม** ในเอกสาร Word แต่ไม่รู้จะเริ่มจากตรงไหนหรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนาหลายคนเจออุปสรรคนี้เมื่อต้องทำอัตโนมัติรายงานหรือใบแจ้งหนี้ ในบทแนะนำนี้เราจะพาคุณผ่านตัวอย่างที่พร้อมรันเต็มรูปแบบ ที่แสดงวิธี **เพิ่มรูปลงใน Word**, ใส่เงาแบบนุ่มนวล, และควบคุมความโปร่งใสของรูป ทั้งหมดนี้ด้วย Aspose.Words for .NET

เมื่ออ่านจบคุณจะได้ไฟล์ `.docx` ที่มีสี่เหลี่ยมเรียบพร้อมเงาที่ดูเป็นมืออาชีพ—เหมาะสำหรับแบรนด์, การเน้นข้อความ, หรือเพียงแค่ทำให้เอกสารดูดีขึ้น ไม่ต้องใช้เครื่องมือภายนอก เพียงไม่กี่บรรทัดของ C# เท่านั้น

## สิ่งที่คุณต้องมี

- **Aspose.Words for .NET** (เวอร์ชันล่าสุด ณ ต้นปี 2026) คุณสามารถดาวน์โหลดจาก NuGet (`Install-Package Aspose.Words`)  
- สภาพแวดล้อมการพัฒนา .NET (Visual Studio, Rider, หรือ VS Code พร้อมส่วนขยาย C#)  
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#—ไม่ต้องซับซ้อน เพียง `using` statements และการสร้างอ็อบเจ็กต์ทั่วไป  

ถ้าคุณมีทั้งหมดนี้แล้ว เยี่ยม—มาเริ่มกันเลย

## สร้างรูปสี่เหลี่ยม – ขั้นตอนหลัก

ด้านล่างเป็นโค้ดเต็มคัดลอก‑วางลงในโปรเจกต์คอนโซลใหม่ กด **F5** แล้วคุณจะเห็นไฟล์ `ShadowDemo.docx` ปรากฏในโฟลเดอร์ที่กำหนด

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### ทำไมวิธีนี้ถึงได้ผล

- **`Document`** เป็นจุดเริ่มต้น; แทนไฟล์ Word ทั้งหมด  
- **`Shape`** พร้อม `ShapeType.Rectangle` บอก Aspose ว่าเราต้องการวัตถุรูปสี่เหลี่ยม  
- การตั้งค่า **`Width`** และ **`Height`** ให้ขนาดรูปที่แน่นอน; หากไม่ตั้งค่า จะเป็น placeholder ขนาดเล็ก  
- อ็อบเจ็กต์ **`Shadow`** ให้เราปรับแต่งทุกแง่มุมของเงา: ความเบลอ, ระยะ, ทิศทาง, สี, ความโปร่งใส, และการกระจาย นี่คือหัวใจของ *apply shadow to shape*  
- สุดท้าย **`AppendChild`** แทรกรูปเข้าไปในพารากราฟแรกของเอกสาร ซึ่งเป็นวิธีที่ง่ายที่สุดในการ *add shape to Word* โดยไม่ต้องจัดการกับตารางหรือส่วนหัว  

เมื่อคุณเปิด `ShadowDemo.docx` คุณจะเห็นสี่เหลี่ยมสีเทานั่งอยู่ในเอกสารอย่างสบาย ๆ พร้อมเงาที่เอียงลง‑ขวาที่มุม 45° เงานั้นไม่ใช่บล็อกสีทึบ; รัศมีเบลอทำให้ขอบนุ่มนวล และความโปร่งใสทำให้ดูเหมือนเงาตกธรรมชาติ ไม่ใช่การทับสีที่แข็งกระด้าง

![create rectangle shape example](image.png "create rectangle shape with shadow in Word using Aspose.Words")

*(รูปด้านบนแสดงผลลัพธ์สุดท้ายของโค้ดสคริปต์)*

## เพิ่มรูปลงในเอกสาร Word – ตัวเลือกการวางตำแหน่ง

ตัวอย่างใช้ **พารากราฟแรก** เพราะเป็นวิธีที่เร็วที่สุดในการเห็นผลบนหน้าจอ ในสถานการณ์จริงคุณอาจต้องการ:

- แทรกรูปลงใน **section** หรือ **header/footer** เฉพาะ  
- วางไว้ใน **cell ของตาราง** เพื่อให้สอดคล้องกับข้อมูลตาราง  
- ใช้ตัวเลือก **text wrapping** (เช่น `WrapType.Square`) เพื่อให้ข้อความรอบ ๆ ไหลรอบสี่เหลี่ยม  

นี่คือตัวอย่างสั้น ๆ ที่วางรูปลงในพารากราฟใหม่พร้อมสไตล์กำหนดเอง:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*เคล็ดลับ:* ควรเพิ่มรูป **หลังจาก** ตั้งค่าคุณสมบัติต่าง ๆ เสร็จแล้ว; หากทำก่อนอาจต้องเรียก `UpdateLayout` เพื่อรีเฟรชการแสดงผล

## ใส่เงาให้รูป – ปรับแต่งรูปลักษณ์อย่างละเอียด

เงาสามารถเปลี่ยนบรรยากาศของเอกสารได้อย่างมาก คลาส `Shadow` มีคุณสมบัติต่าง ๆ ดังนี้:

| คุณสมบัติ | สิ่งที่ควบคุม | ค่าที่พบบ่อย |
|-----------|--------------|--------------|
| `BlurRadius` | ความนุ่มของขอบเงา | 2.0 – 10.0 |
| `Distance` | ระยะห่างของเงาจากรูป | 1.0 – 8.0 |
| `Direction` | มุมเป็นองศา (0 = ซ้าย, 90 = ขึ้น) | 0 – 360 |
| `Color` | สีของเงา (any `System.Drawing.Color`) | Gray, Black, Custom |
| `Transparency` | ความทึบ (0 = ทึบเต็ม, 1 = โปร่งใส) | 0.0 – 0.5 |
| `Spread` | การขยายของเงาก่อนเบลอ | 0.0 – 1.0 |

หากต้องการ **ลุคที่ละเอียดอ่อนและเป็นมืออาชีพ** ให้ตั้ง `BlurRadius` ประมาณ 4‑6 และ `Transparency` ใกล้ 0.2 เหมือนโค้ดด้านบน สำหรับ **เอฟเฟกต์ที่โดดเด่น** ให้เพิ่ม `Distance` เป็น 6, ตั้ง `Direction` ที่ 135°, และลด `Transparency` ลงเหลือ 0.05

## ตั้งค่าความโปร่งใสของรูปและการกระจายเงา

ความโปร่งใสไม่ได้จำกัดแค่เงา; คุณยังสามารถทำให้สี่เหลี่ยมเองบางส่วนได้:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

การผสมสีเติมแบบกึ่งโปร่งใสกับเงานุ่มมักให้ความรู้สึก UI สมัยใหม่—เหมาะกับแดชบอร์ดหรือโมเดลการออกแบบที่ฝังอยู่ในรายงาน

### กรณีที่ต้องระวัง

1. **เวอร์ชัน Word เก่า** (ก่อน 2007) ไม่รองรับคุณสมบัติเชิงเงาบางอย่าง หากคุณสร้างไฟล์ `.doc` ควรทำให้เงาง่ายลง (เช่น ตั้ง `BlurRadius` เป็น 0)  
2. **หน้าจอ DPI สูง** อาจทำให้เงาปรากฏแตกต่างเล็กน้อย ทดสอบบนสภาพแวดล้อมเป้าหมายหากความแม่นยำของภาพสำคัญ  
3. **รูปทับซ้อน**—Aspose จะเรนเดอร์เงาตามลำดับการเพิ่มรูป แทรกรูปจากด้านหลังไปด้านหน้าเพื่อหลีกเลี่ยงการบังที่ไม่ต้องการ  

## บันทึกและตรวจสอบผลลัพธ์

เมธอด `Document.Save` จะตรวจจับรูปแบบเอาต์พุตจากส่วนขยายไฟล์โดยอัตโนมัติ สำหรับไฟล์ **`.docx`** จะได้รูปแบบ Open XML ซึ่งโปรเซสเซอร์ Word สมัยใหม่ส่วนใหญ่รองรับ หากต้องการเวอร์ชัน **PDF** ที่มีสไตล์เดียวกัน เพียงเปลี่ยนส่วนขยายไฟล์:

```csharp
document.Save("ShadowDemo.pdf");
```

การเปิด `ShadowDemo.docx` (หรือ `ShadowDemo.pdf`) ควรแสดง **สี่เหลี่ยมพร้อมเงา** อย่างชัดเจน ยืนยันว่าคุณได้ทำสำเร็จในการ *create rectangle shape* และ *apply shadow to shape* ด้วย Aspose.Words

## คำถามที่พบบ่อย

**Q: สามารถใช้รูปแบบอื่น เช่น วงรีได้หรือไม่?**  
A: แน่นอน แค่เปลี่ยน `ShapeType.Rectangle` เป็น `ShapeType.Ellipse` (หรือค่า `ShapeType` ใด ๆ) คุณสมบัติของเงาจะยังคงเหมือนเดิม

**Q: ถ้าต้องการให้สี่เหลี่ยมคลิกได้ต้องทำอย่างไร?**  
A: สามารถกำหนด hyperlink ให้กับรูปได้:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: ทำงานบน .NET 6+ ได้หรือไม่?**  
A: ได้ Aspose.Words 23.11 ขึ้นไปรองรับ .NET 6, .NET 7, และ .NET 8 อย่างเต็มรูปแบบ เพียงอ้างอิงแพ็กเกจ NuGet ที่เหมาะสม

**Q: จะเปลี่ยนสีเงาให้ตรงกับแบรนด์ของฉันได้อย่างไร?**  
A: ใช้ `System.Drawing.Color` ใดก็ได้ที่คุณต้องการ:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## สรุป

เราได้ครอบคลุมทุกอย่างที่คุณต้องการเพื่อ **create rectangle shape** ในเอกสาร Word, **add shape to Word**, **apply shadow to shape**, และ **set shape transparency** โค้ดเต็มที่รันได้อยู่ด้านบนของหน้านี้ และคำอธิบายควรทำให้คุณมั่นใจพอที่จะปรับขนาด, สี, และพารามิเตอร์ของเงาให้เหมาะกับโครงการใด ๆ

พร้อมก้าวต่อไปหรือยัง? ลองทดลองกับ:

- รูปหลายรูปซ้อนกันเพื่อสร้างเอฟเฟกต์แบจ  
- การกำหนดขนาดแบบไดนามิกตามเนื้อหาเอกสาร (เช่น คำนวณความกว้างจากคอลัมน์ตาราง)  
- การส่งออกเอกสารเป็น PDF หรือ HTML พร้อมรักษาเงาไว้  

หากเจออุปสรรคหรือมีไอเดียเพิ่มเติม อย่าลังเลที่จะแสดงความคิดเห็น หรือแบ่งปันการปรับแต่ง “สี่เหลี่ยมพร้อมเงา” ของคุณเอง

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}