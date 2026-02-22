---
category: general
date: 2026-02-21
description: เพิ่มเงาให้กับรูปทรงใน C# และเรียนรู้วิธีปรับแต่งเงา, ใช้เอฟเฟกต์เงา,
  และตั้งค่าความทึบของเงาด้วยตัวอย่างที่สมบูรณ์และสามารถรันได้
draft: false
keywords:
- add shadow to shape
- how to customize shadow
- apply shadow effect
- how to add shadow
- set shadow opacity
language: th
og_description: เพิ่มเงาให้กับรูปทรงใน C# ด้วยคู่มือนี้ เรียนรู้วิธีปรับแต่งเงา ใช้เอฟเฟกต์เงา
  และตั้งค่าความทึบของเงา เพียงไม่กี่บรรทัดของโค้ด
og_title: เพิ่มเงาให้รูปทรง – คอร์ส C# ฉบับสมบูรณ์
tags:
- C#
- Aspose.Words
- Graphics
- Shadow Effect
title: เพิ่มเงาให้กับรูปร่าง – คู่มือขั้นตอนต่อขั้นตอนสำหรับนักพัฒนา C#
url: /th/net/programming-with-shapes/add-shadow-to-shape-step-by-step-guide-for-c-developers/
---

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มเงาให้กับ Shape – ตัวอย่าง C# ครบถ้วน

เคยต้อง **เพิ่มเงาให้กับ shape** ในเอกสาร Word แต่ไม่รู้ว่าจะเริ่มต้นอย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนาหลายคนเจอปัญหานี้เมื่อต้องทำให้รายงานหรือโบรชัวร์ดูสวยงาม ข่าวดีคือ? เพียงไม่กี่ขั้นตอนคุณก็สามารถเปลี่ยนสี่เหลี่ยมแบนให้กลายเป็นองค์ประกอบสามมิติที่โดดเด่นบนหน้าเอกสารได้

ในคู่มือนี้เราจะเดินผ่าน **ตัวอย่างเต็มที่สามารถรันได้** ที่แสดงวิธีปรับแต่งเงา, ใช้เอฟเฟกต์เงา, และแม้กระทั่งตั้งค่าความทึบของเงาสำหรับ shape ใดก็ได้ เมื่อจบคุณจะได้โค้ดส่วนนำกลับไปใช้ในโปรเจกต์ Aspose.Words ใดก็ได้โดยไม่ต้องอ้างอิงลับ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงมือทำ โปรดตรวจสอบว่าคุณมี:

* **.NET 6.0** (หรือใหม่กว่า) ติดตั้งอยู่ — โค้ดนี้ยังทำงานกับ .NET Framework 4.6+ ด้วย
* **Aspose.Words for .NET** NuGet package — แนะนำให้ใช้เวอร์ชัน 23.9 หรือใหม่กว่า
* ความเข้าใจพื้นฐานเกี่ยวกับ C# และการเขียนโปรแกรมเชิงวัตถุ

หากคุณยังไม่มี NuGet package ให้รัน:

```bash
dotnet add package Aspose.Words
```

เมื่อพื้นฐานพร้อมแล้ว ไปทำกันต่อ

## ขั้นตอนที่ 1 – โหลดหรือสร้าง Document แล้วดึง Shape ตัวแรก

สิ่งแรกที่ต้องมีคืออ็อบเจกต์ `Document` ที่มี shape อยู่ สำหรับตัวอย่างนี้เราจะสร้างเอกสารใหม่, แทรกสี่เหลี่ยมง่าย ๆ, แล้วดึงมันออกมา

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank document
        Document doc = new Document();

        // 2️⃣ Add a new shape (a rectangle) to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;

        // Insert the shape into the document body
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Retrieve the shape we just added (demonstrates add shadow to shape)
        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // The remaining steps modify the shadow of firstShape
```

**เหตุผลที่ทำเช่นนี้:**  
การดึง shape ผ่าน `GetChild` จำลองสถานการณ์จริงที่ shape มีอยู่แล้ว (เช่น โหลดจากเทมเพลต) อีกทั้งยังทำให้โค้ดเงาต่อไปทำงานบนอ็อบเจกต์ที่ถูกต้อง หลีกเลี่ยงข้อผิดพลาด `null‑reference`

> **เคล็ดลับ:** หากคุณต้องจัดการหลาย shape ให้ใช้ `GetChild(NodeType.Shape, index, true)` หรือวนลูปผ่าน `doc.GetChildNodes(NodeType.Shape, true)`

## ขั้นตอนที่ 2 – เปิดใช้งานเอฟเฟกต์เงา

โดยค่าเริ่มต้นเงาของ shape จะถูกปิด การเปิดใช้งานเป็นเงื่อนไขแรกก่อนที่จะทำการปรับแต่งอื่น ๆ

```csharp
        // 4️⃣ Enable the shadow
        firstShape.Shadow.Enabled = true;
```

**ทำไมถึงสำคัญ:**  
หากไม่ได้ตั้งค่า `Enabled = true` การเปลี่ยนแปลงคุณสมบัติต่อ ๆ ไป (สี, เบลอ, ระยะชิด) จะถูกละเลย เหมือนกับการเปิดสวิตช์ไฟก่อนจะปรับความสว่างของโคมไฟ

## ขั้นตอนที่ 3 – เลือกสีของเงา (และทำไมสีดำจึงเป็นจุดเริ่มต้นที่ดี)

การเลือกสีมีผลต่อความลึกที่รับรู้ สีดำ (หรือเทาเข้ม) เป็นสีที่ใช้บ่อยที่สุดเพราะทำงานได้กับพื้นหลังทุกแบบ

```csharp
        // 5️⃣ Set the shadow color – black gives a classic look
        firstShape.Shadow.Color = Color.Black;
```

**ทางเลือก:**  
หากเอกสารของคุณมีพื้นหลังสีเข้ม ให้ลองใช้สีที่อ่อนกว่า:

```csharp
        // firstShape.Shadow.Color = Color.FromArgb(150, 150, 150); // light gray
```

## ขั้นตอนที่ 4 – ตั้งค่าความทึบของเงา (Set Shadow Opacity)

ความทึบระบุเป็นค่าระหว่าง `0.0` (โปร่งใสเต็ม) ถึง `1.0` (ทึบเต็ม) เงาที่มีความโปร่งใส 40 % ให้ความรู้สึกเป็นธรรมชาติสำหรับการออกแบบ UI ส่วนใหญ่

```csharp
        // 6️⃣ Make the shadow 40 % transparent
        firstShape.Shadow.Transparency = 0.4; // 0 = opaque, 1 = invisible
```

**วิธีปรับแต่ง:**  
- **นุ่มนวลกว่า:** `0.2` (โปร่งใส 20 %)  
- **จางมาก:** `0.7` (โปร่งใส 70 %)

## ขั้นตอนที่ 5 – กำหนดค่า Blur และความนุ่มของขอบ

ค่า Blur ควบคุมความนุ่มของขอบเงา ค่า `4.0` ทำงานได้ดีสำหรับ shape ขนาดกลาง

```csharp
        // 7️⃣ Soften the edges with a blur radius
        firstShape.Shadow.Blur = 4.0;
```

**กรณีขอบ:**  
หากตั้ง `Blur` เป็น `0` เงาจะกลายเป็นเงาแบบขอบแข็ง ซึ่งอาจดูแหลมคมเกินไป ในทางกลับกันค่ามากกว่า `10` อาจทำให้เงาดูเหมือนแสงสว่างรอบ ๆ

## ขั้นตอนที่ 6 – กำหนดตำแหน่งเงาเทียบกับ Shape

ค่าการชิด (`OffsetX`, `OffsetY`) ย้ายเงาในแนวนอนและแนวตั้ง ตัวเลขบวกจะทำให้เงาเลื่อนลงและไปทางขวา

```csharp
        // 8️⃣ Position the shadow 5 points right and 5 points down
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;
```

**ทดลอง:**  
- **เงาตกลง:** `OffsetX = 0`, `OffsetY = 10`  
- **เอฟเฟกต์ยกขึ้น:** `OffsetX = -5`, `OffsetY = -5`

## ขั้นตอนที่ 7 – บันทึกและตรวจสอบผลลัพธ์

สุดท้ายให้บันทึกเอกสารลงดิสก์และเปิดด้วย Microsoft Word (หรือโปรแกรมดูที่รองรับ) เพื่อดูเงาที่ทำงาน

```csharp
        // 9️⃣ Save the document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

เมื่อคุณเปิด **ShadowedShape.docx** คุณควรเห็นสี่เหลี่ยมสีฟ้าอ่อนที่มีเงาสีดำโปร่งใสอ่อน ๆ ชิดห่างห้าจุด หากเงาไม่ปรากฏ ให้ตรวจสอบว่า `firstShape.Shadow.Enabled` เป็น `true` และคุณใช้ Aspose.Words เวอร์ชันล่าสุด

### โค้ดเต็ม (พร้อมคัดลอก‑วาง)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        Document doc = new Document();
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // Enable shadow
        firstShape.Shadow.Enabled = true;

        // Choose shadow color
        firstShape.Shadow.Color = Color.Black;

        // Set opacity (40 % transparent)
        firstShape.Shadow.Transparency = 0.4;

        // Soften edges
        firstShape.Shadow.Blur = 4.0;

        // Position shadow
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;

        // Save document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

## คำถามที่พบบ่อย & กรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ถ้า shape เป็นรูปภาพแทนสี่เหลี่ยมจะทำอย่างไร?** | คุณสมบัติเงาเดียวกันใช้ได้; เพียงตรวจสอบให้ `ShapeType` ของ shape เป็น `Picture` |
| **ฉันสามารถทำแอนิเมชันให้เงาได้หรือไม่?** | Aspose.Words ไม่รองรับแอนิเมชัน, แต่คุณสามารถสร้างหลายหน้าโดยเปลี่ยน offset ทีละน้อยแล้วใช้ PowerPoint ทำแอนิเมชัน |
| **เงาใช้งานได้ในไฟล์ PDF หรือไม่?** | ใช่. เมื่อบันทึกเป็น PDF (`doc.Save("out.pdf")`) Aspose.Words จะคงเอฟเฟกต์เงาไว้ |
| **จะลบเงาออกภายหลังอย่างไร?** | ตั้ง `firstShape.Shadow.Enabled = false;` หรือกำหนด `firstShape.Shadow = null;` |
| **มีขีดจำกัดของค่า Blur หรือไม่?** | โดยปฏิบัติค่ามากกว่า `15` ทำให้เงาดูเหมือนฮาโลและอาจเพิ่มขนาดไฟล์ |

## ขั้นตอนต่อไป – รักษาแรงบันดาลใจ

ตอนนี้คุณรู้ **วิธีเพิ่มเงา** และ **ตั้งค่าความทึบของเงา** แล้ว ลองสำรวจต่อ:

* **ปรับเงาเพิ่มเติม** ด้วย `Shadow.Distance` เพื่อเพิ่มระยะชิดให้เด่นชัดขึ้น
* **ใช้เอฟเฟกต์เงา** กับ text frames หรือ WordArt เพื่อออกแบบเอกสารที่หลากหลาย
* **รวมเงาหลายชั้น** (เช่น inner + outer) เพื่อให้ได้ลุคแบบหลายระดับ
* **ส่งออกเป็น HTML** แล้วดูว่า CSS `box‑shadow` ทำงานเหมือนกันอย่างไร

หากคุณกำลังสร้างตัวสร้างรายงาน ลองใส่เงาในหัวเรื่อง, แผนภูมิ, หรือกล่องอธิบาย เพื่อดึงความสนใจของผู้อ่าน ทดลองใช้สีและความโปร่งใสต่าง ๆ — อาจเป็นเงาสีฟ้าอ่อนสำหรับธีมองค์กร

---

### TL;DR

เราได้เดินผ่าน **ตัวอย่างเต็มที่พร้อมใช้งาน** ที่แสดงวิธี **เพิ่มเงาให้กับ shape**, **ปรับแต่งเงา**, **ใช้เอฟเฟกต์เงา**, และ **ตั้งค่าความทึบของเงา** ด้วย Aspose.Words ใน C# โค้ดพร้อมรัน, คำอธิบายครอบคลุมทั้ง *ทำอะไร* และ *ทำไม* และคุณมีพื้นฐานที่มั่นคงสำหรับการสไตล์ shape ใด ๆ ในโครงการอัตโนมัติของ Word

ขอให้สนุกกับการเขียนโค้ด และขอให้เอกสารของคุณมีความเป็นมิติที่เพิ่มขึ้นเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}