---
category: general
date: 2026-03-30
description: เรียนรู้วิธีตั้งเงาบนรูปร่างใน Word ด้วย C# คู่มือนี้ยังแสดงวิธีเพิ่มเงารูปร่าง
  ปรับความโปร่งใสของรูปร่าง และเพิ่มเงาสี่เหลี่ยม.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: th
og_description: วิธีตั้งเงาบนรูปร่างใน Word ด้วย C#? ทำตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อเพิ่มเงารูปร่าง
  ปรับความโปร่งใสของรูปร่าง และเพิ่มเงาสี่เหลี่ยม.
og_title: วิธีตั้งเงาบนรูปร่างใน Word – สอน C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: วิธีตั้งเงาบนรูปร่างใน Word – บทเรียน C#
url: /th/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งเงาบนรูปร่างใน Word – คำแนะนำ C#

เคยสงสัย **วิธีตั้งเงา** บนรูปร่างในเอกสาร Word โดยไม่ต้องคลิก UI หรือเปล่า? คุณไม่ได้เป็นคนเดียว ในหลายรายงานหรือสไลด์การตลาด เงาแบบเบา ๆ ทำให้สี่เหลี่ยมเด่นขึ้น และการทำแบบโปรแกรมช่วยประหยัดเวลามาก

ในคู่มือนี้เราจะเดินผ่านตัวอย่างที่พร้อมรันเต็มรูปแบบ ไม่เพียงแสดง **วิธีตั้งเงา** เท่านั้น แต่ยังครอบคลุม **add shape shadow**, **adjust shape transparency**, และแม้กระทั่ง **add rectangle shadow** สำหรับกล่องอธิบายคลาสสิก เมื่อเสร็จคุณจะได้ไฟล์ Word (`output.docx`) ที่ดูเรียบหรู และเข้าใจว่าทำไมแต่ละคุณสมบัติจึงสำคัญ

## ข้อกำหนดเบื้องต้น

- .NET 6+ (หรือ .NET Framework 4.7.2) พร้อมคอมไพเลอร์ C#  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
- ความคุ้นเคยพื้นฐานกับ C# และโมเดลออบเจ็กต์ของ Word  

ไม่ต้องใช้ไลบรารีเพิ่มเติม—ทั้งหมดอยู่ใน Aspose.Words

---

## วิธีตั้งเงาบนรูปร่างใน Word ด้วย C#

ด้านล่างเป็นไฟล์ซอร์สเต็มรูปแบบ บันทึกเป็น `Program.cs` แล้วรันจาก IDE หรือ `dotnet run` โค้ดจะโหลดไฟล์ `.docx` ที่มีอยู่, ค้นหารูปร่างแรก (โดยปกติคือสี่เหลี่ยม), เปิดใช้งานเงา, ปรับพารามิเตอร์ภาพบางอย่าง, แล้วบันทึกผลลัพธ์

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **สิ่งที่คุณจะเห็น** – สี่เหลี่ยมตอนนี้มีเงาดำแบบ drop‑shadow ที่โปร่งแสง 30 % เลื่อน 5 pt ไปทางขวาและลง, พร้อมเบลออ่อน ๆ เปิด `output.docx` ใน Word เพื่อตรวจสอบ

## ปรับความโปร่งใสของรูปร่าง – ทำไมจึงสำคัญ

ความโปร่งใสไม่ใช่แค่ตัวควบคุมความสวยงาม; มันส่งผลต่อการอ่านค่า ค่า 0.0 ทำให้เงาเต็มที่, ส่วน 1.0 จะซ่อนเงาเลย ในโค้ดข้างบนเราใช้ `0.3` เพื่อให้ได้เอฟเฟกต์เบา ๆ ที่ทำงานได้ทั้งพื้นหลังสว่างและมืด คุณสามารถทดลองปรับได้ตามต้องการ:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

จำไว้ว่า **adjust shape transparency** สามารถนำไปใช้กับสีเติมของรูปร่างได้เช่นกัน หากคุณต้องการสี่เหลี่ยมที่มีความโปร่งใสบางส่วน

## เพิ่มเงาให้รูปร่างต่าง ๆ

โค้ดที่เราใช้มุ่งเป้าไปที่ออบเจ็กต์ `Shape` แต่คุณสมบัติ `ShadowFormat` เหมือนกันกับ **Image**, **Chart**, และแม้กระทั่ง **TextBox** นี่คือตัวอย่างแบบคัดลอก‑วางเร็ว:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

ดังนั้นไม่ว่าคุณจะ **add shape shadow** ให้โลโก้หรือไอคอนตกแต่ง, วิธีการก็เหมือนกัน

## วิธีเพิ่มเงาให้รูปร่างใดก็ได้ – กรณีเฉพาะ

1. **รูปร่างที่ไม่มีกรอบ** – รูปร่าง Word บางประเภท (เช่น เส้นวาดอิสระ) ไม่รองรับเงา การตั้งค่า `ShadowFormat.Visible` จะล้มเหลวโดยไม่มีการแจ้งเตือน ตรวจสอบ `shape.IsShadowSupported` หากต้องการความปลอดภัย  
2. **เวอร์ชัน Word เก่า** – คุณสมบัติเชิงเงาตรงกับฟีเจอร์ Word 2007+ หากต้องสนับสนุน Word 2003 เงาจะถูกละเลยเมื่อเปิดไฟล์  
3. **หลายเงา** – ปัจจุบัน Aspose.Words รองรับเงาเดียวต่อรูปร่าง หากต้องการเอฟเฟกต์สองชั้น ให้ทำสำเนารูปร่าง, เลื่อนตำแหน่ง, แล้วตั้งค่าเงาต่างกัน

## เพิ่มเงาสี่เหลี่ยม – ตัวอย่างการใช้งานจริง

ลองนึกว่าคุณกำลังสร้างรายงานไตรมาสและหัวข้อแต่ละส่วนเป็นสี่เหลี่ยมสี การ **add rectangle shadow** จะทำให้หน้าเอกสารดูเหมือน “การ์ด” ขั้นตอนเหมือนกับตัวอย่างพื้นฐาน; เพียงตรวจสอบว่ารูปร่างที่คุณเลือกเป็นสี่เหลี่ยมจริง (`shape.ShapeType == ShapeType.Rectangle`) หากต้องสร้างสี่เหลี่ยมตั้งแต่ต้น ดูโค้ดด้านล่าง:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

รันโปรแกรมเต็มรูปแบบพร้อมส่วนเพิ่มนี้ คุณจะได้สี่เหลี่ยมใหม่ที่มีเอฟเฟกต์ **add rectangle shadow** ตามต้องการ

---

![Word shape with shadow](placeholder-image.png){alt="วิธีตั้งเงาบนรูปร่างใน Word"}

*รูป: สี่เหลี่ยมหลังจากตั้งค่าเงาแล้ว*

## สรุปสั้น ๆ (Cheat Sheet แบบหัวข้อ)

- **Load** เอกสารด้วย `new Document(path)`  
- **Locate** รูปร่างด้วย `doc.GetChild(NodeType.Shape, index, true)`  
- **Enable** เงา: `shape.ShadowFormat.Visible = true;`  
- **Set color** ด้วย `System.Drawing.Color` ใดก็ได้  
- **Adjust transparency** (`0.0–1.0`) เพื่อควบคุมความทึบ  
- **OffsetX / OffsetY** เลื่อนเงาแนวนอน/แนวตั้ง (หน่วยเป็น points)  
- **BlurRadius** ทำให้ขอบเงานุ่มขึ้น—ค่าสูง = เงานุ่มกว่า  
- **Save** ไฟล์และเปิดใน Word เพื่อดูผลลัพธ์

## สิ่งที่ควรลองต่อไป?

- **Dynamic colors** – ดึงสีเงาจากธีมหรืออินพุตของผู้ใช้  
- **Conditional shadows** – ใส่เงาเฉพาะเมื่อความกว้างของรูปร่างเกินค่าที่กำหนด  
- **Batch processing** – วนลูปผ่านรูปร่างทั้งหมดในเอกสารและ **add shape shadow** อัตโนมัติ  

หากคุณทำตามขั้นตอนครบแล้ว คุณจะรู้ **วิธีตั้งเงา**, วิธี **adjust shape transparency**, และวิธี **add rectangle shadow** เพื่อให้เอกสารดูเป็นมืออาชีพ อย่ากลัวทดลอง, ทำให้พัง, แล้วแก้ไขต่อ—การเขียนโค้ดคือครูที่ดีที่สุด

---

*Happy coding! หากบทเรียนนี้เป็นประโยชน์ อย่าลืมแสดงความคิดเห็นหรือแชร์เทคนิคเงาของคุณเอง ความรู้ที่เราแบ่งปันกันจะทำให้เอกสาร Word ของเราสวยงามยิ่งขึ้น*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}