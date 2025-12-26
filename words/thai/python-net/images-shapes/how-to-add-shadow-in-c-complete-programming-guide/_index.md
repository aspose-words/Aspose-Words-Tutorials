---
category: general
date: 2025-12-25
description: วิธีเพิ่มเงาใน C# ด้วยตัวอย่างโค้ดง่าย ๆ เรียนรู้วิธีตั้งระยะเงา ปรับสีตามต้องการ
  และสร้างความลึกให้กับกราฟิกของคุณ
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: th
og_description: วิธีเพิ่มเงาใน C# จะอธิบายอย่างเป็นขั้นตอน ติดตามคู่มือเพื่อกำหนดระยะเงา
  สี และความเบลอสำหรับรูปร่างที่ดูเป็นมืออาชีพ
og_title: วิธีเพิ่มเงาใน C# – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: วิธีเพิ่มเงาใน C# – คู่มือการเขียนโปรแกรมครบถ้วน
url: /th/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มเงาใน C# – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์

การเพิ่มเงาใน C# เป็นความต้องการทั่วไปเมื่อคุณต้องการให้กราฟิกของคุณโดดเด่นออกจากหน้า ในบทเรียนนี้เราจะพาคุณผ่านขั้นตอนที่แม่นยำเพื่อกำหนดเงาของรูปทรง รวมถึงการตั้งค่าระยะห่างของเงา การปรับเบลอ และการเลือกสีที่เหมาะสม  

ถ้าคุณเคยมองดูสี่เหลี่ยมแบน ๆ แล้วคิดว่า “นี่ควรมีความลึกบ้าง” คุณมาถูกที่แล้ว เราจะเริ่มจากเอกสารเปล่า ใส่รูปทรงลงไป แล้วจบด้วยเงาที่ดูเป็นมืออาชีพเหมือนออกแบบโดยนักออกแบบ ไม่ได้มีเนื้อหาเกินความจำเป็น เพียงตัวอย่างที่ใช้งานได้จริงที่คุณสามารถคัดลอก‑วางได้ทันที

## สิ่งที่คุณจะได้เรียนรู้

- สร้างเอกสารใหม่และแทรกรูปทรงโดยโปรแกรม  
- ใช้การเบลออ่อน ๆ กับเงาของรูปทรง  
- **วิธีตั้งค่าระยะห่างของเงา** เพื่อให้เงาปรากฏอย่างเป็นธรรมชาติ  
- เลือกสีเงาที่ทำงานได้บนพื้นหลังใด ๆ  
- บันทึกผลลัพธ์เป็น PDF (หรือรูปแบบอื่นที่คุณต้องการ)  

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดทำงานกับ .NET Core และ .NET Framework)  
- Aspose.Words for .NET (รุ่นทดลองฟรีหรือเวอร์ชันที่มีลิขสิทธิ์)  
- ความเข้าใจพื้นฐานเกี่ยวกับไวยากรณ์ C#  

แค่นั้น—ไม่มีไลบรารีเพิ่มเติม ไม่มีเวทมนตร์ มาเริ่มกันเลย

![ตัวอย่างของรูปทรงที่มีเงาดำนุ่ม – วิธีเพิ่มเงา](https://example.com/placeholder-shadow.png "ตัวอย่างวิธีเพิ่มเงา")

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า Namespaces

ก่อนอื่น สร้างแอปคอนโซลใหม่ (หรือโปรเจกต์ C# ใด ๆ) แล้วเพิ่มแพคเกจ NuGet ของ Aspose.Words:

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

จากนั้นเปิด `Program.cs` และนำ Namespaces ที่จำเป็นเข้ามาใช้งาน:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **เคล็ดลับ:** หากคุณใช้ Visual Studio IDE จะเสนอ `using` ให้คุณอัตโนมัติขณะพิมพ์ `Document`

## ขั้นตอนที่ 2: สร้างเอกสารใหม่และเพิ่มรูปทรง

เมื่อไลบรารีพร้อม เราสามารถสร้างอ็อบเจกต์ `Document` แล้ววางสี่เหลี่ยมง่าย ๆ ลงบนหน้าที่หนึ่งได้

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

ทำไมต้องเป็นสี่เหลี่ยม? มันเป็นผืนผ้าใบที่เป็นกลางทำให้เราประเมินผลของเงาได้โดยไม่ถูกรบกวน คุณสามารถเปลี่ยน `ShapeType.Rectangle` เป็น `Ellipse` หรือ `Star` — ลอจิกของเงาจะยังคงเหมือนเดิม

## ขั้นตอนที่ 3: วิธีเพิ่มเงา – ปรับเบลอ, ระยะห่าง, และสี

ต่อมาคือหัวใจของบทเรียน: **วิธีเพิ่มเงา** ให้กับสี่เหลี่ยมดังกล่าว Aspose.Words มีอ็อบเจกต์ `Shadow` บนทุกรูปทรง ให้คุณปรับเบลอ, ระยะห่าง, และสีได้

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

สังเกตคอมเมนต์ `// 3b) Set the shadow's offset distance` บรรทัดนี้ตอบโดยตรงว่า **วิธีตั้งค่าระยะห่างของเงา** โดยการปรับ `shadow.Distance` คุณจะควบคุมช่องว่างระหว่างรูปทรงและเงา ทำให้เหมือนแหล่งแสงที่วางไว้ที่มุมเฉพาะ

### ทำไมต้องใช้ค่าต่าง ๆ เหล่านี้?

- **Blur = 5.0** – เบลออ่อน ๆ ป้องกันเงาให้ดูหยาบเกินไป แต่ยังคงมองเห็นได้ชัดเจน  
- **Distance = 3.0** – ทำให้เงาอยู่ใกล้พอที่จะดูเหมือนถูกสร้างโดยรูปทรงเอง  
- **Color = Black** – รับประกันคอนทราสต์บนพื้นหลังทั้งสว่างและมืด  

คุณสามารถปรับค่าเหล่านี้ได้ตามต้องการ; API รองรับค่า `double` ใด ๆ ที่คุณต้องการ

## ขั้นตอนที่ 4: บันทึกเอกสารและตรวจสอบผลลัพธ์

เมื่อกำหนดค่าเงาเรียบร้อย เราเพียงเขียนไฟล์ลงดิสก์ Aspose.Words สามารถส่งออกหลายรูปแบบ; PDF เป็นตัวเลือกที่นิยมสำหรับการแชร์

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

เปิด `ShadowedShape.pdf` คุณจะเห็นสี่เหลี่ยมสีเทาพร้อมเงาดำอ่อน ๆ ที่เลื่อนเล็กน้อยไปด้านล่าง‑ขวา หากเงาดูจางเกินไป ให้เพิ่ม `shadow.Blur` หรือ `shadow.Distance` แล้วรันใหม่

## คำถามที่พบบ่อย & กรณีเฉพาะ

### ถ้าต้องการเงาโปร่งใสจะทำอย่างไร?

ใช้สี ARGB ที่มีค่าอัลฟา (alpha) น้อยกว่า 255:

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### สามารถใช้เงาเดียวกันกับหลายรูปทรงได้หรือไม่?

ได้เลย สร้างเมธอดช่วยเหลือ:

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

เรียก `ApplyStandardShadow(rectangle);` สำหรับแต่ละรูปทรงที่คุณเพิ่ม

### ทำงานกับ .NET Framework เวอร์ชันเก่าได้หรือไม่?

ใช่ Aspose.Words 22.9+ รองรับ .NET Framework 4.5 ขึ้นไป เพียงปรับไฟล์โปรเจกต์ของคุณให้สอดคล้อง

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมทั้งหมดที่คุณสามารถคัดลอกไปวางใน `Program.cs` มันคอมไพล์และรันได้ทันที (สมมติว่าได้ติดตั้งแพคเกจ NuGet แล้ว)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

รันโปรแกรม:

```bash
dotnet run
```

คุณจะพบ `ShadowedShape.pdf` ในโฟลเดอร์โปรเจกต์ เปิดด้วยโปรแกรมดู PDF ใด ๆ เพื่อยืนยันว่าเงาตรงตามที่อธิบาย

## สรุป

เราได้ครอบคลุม **วิธีเพิ่มเงา** ให้กับรูปทรงใน C# ตั้งแต่ต้นจนจบ และได้แสดง **วิธีตั้งค่าระยะห่างของเงา** พร้อมเบลอและสี ด้วยเพียงไม่กี่บรรทัดของโค้ด คุณก็สามารถให้กราฟิกของคุณดูเป็นมืออาชีพ มีมิติสาม‑มิติ—ไม่ต้องพึ่งเครื่องมือออกแบบภายนอก

เมื่อคุณเชี่ยวชาญพื้นฐานแล้ว ลองทดลองต่อไป:

- เปลี่ยนสีเงาเป็นสีฟ้าอ่อนเพื่อให้บรรยากาศเย็นสบายขึ้น  
- เพิ่มค่าเบลอเพื่อให้ได้เอฟเฟกต์ฝันหรูหรา  
- นำเทคนิคเดียวกันไปใช้กับแผนภูมิ, รูปภาพ, หรือกล่องข้อความ  

แต่ละการปรับเปลี่ยนย้ำแนวคิดหลักเดียวกัน ทำให้คุณคุ้นเคยกับการปรับแต่งเงาในทุกสถานการณ์  

มีคำถามเพิ่มเติม? แสดงความคิดเห็นได้เลย และขอให้สนุกกับการเขียนโค้ด!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}