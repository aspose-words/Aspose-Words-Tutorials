---
category: general
date: 2026-02-18
description: เพิ่มเงาให้กับรูปทรงใน Word ด้วย Aspose.Words. เรียนรู้วิธีเปลี่ยนสีเงาใน
  Word, ตั้งค่าการเยื้อง, ความเบลอและความทึบแค่ไม่กี่บรรทัด.
draft: false
keywords:
- add shadow to shape
- how to change shadow color in word
language: th
og_description: เพิ่มเงาให้กับรูปร่างใน Word ด้วย Aspose.Words. บทเรียนนี้แสดงวิธีเปลี่ยนสีเงาใน
  Word ปรับความเบลอ การเยื้องตำแหน่ง และความทึบแสง.
og_title: เพิ่มเงาให้รูปทรงใน Word – คู่มือ Aspose.Words ฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Word Automation
title: เพิ่มเงาให้รูปทรงใน Word – คู่มือ Aspose.Words ฉบับสมบูรณ์
url: /th/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มเงาให้กับรูปร่างใน Word – คู่มือ Aspose.Words ฉบับสมบูรณ์

เคยต้องการ **เพิ่มเงาให้กับรูปร่าง** ในเอกสาร Word แต่ไม่แน่ใจว่าจะเริ่มอย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนามักถาม *วิธีเปลี่ยนสีเงาใน Word* เมื่อพวกเขาต้องการความโดดเด่นเพิ่มเติม  

ในบทแนะนำนี้เราจะเดินผ่านตัวอย่างจากโลกจริงโดยใช้ไลบรารี Aspose.Words for .NET. เมื่อจบคุณจะมีโปรแกรมพร้อมรันที่โหลดไฟล์ DOCX, ดึงรูปร่างแรก, และใส่เงาสีฟ้าแบบกึ่งโปร่งใสพร้อมการเบลอและการชิดตำแหน่งที่กำหนดเอง ไม่ใช่การอ้างอิง “ดูเอกสาร” ที่คลุมเครือ—แต่เป็นโซลูชันที่ครบถ้วนพร้อมคัดลอก‑วาง

## สิ่งที่คุณจะได้เรียนรู้

- วิธีโหลดเอกสาร Word และค้นหาโหนดรูปร่าง  
- คำเรียก API ที่แม่นยำเพื่อ **เพิ่มเงาให้กับรูปร่าง**  
- วิธี **เปลี่ยนสีเงาใน Word**, ตั้งค่ารัศมีการเบลอ, การชิดตำแหน่ง X/Y, และความทึบแสง  
- เคล็ดลับการจัดการหลายรูปร่าง, เงาที่มีอยู่แล้ว, และเวอร์ชันของ Word  

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดสามารถคอมไพล์กับเวอร์ชันก่อนหน้าได้ แต่แนะนำให้ใช้ .NET 6)  
- NuGet package ของ Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- ความเข้าใจพื้นฐานเกี่ยวกับ C# และโมเดลวัตถุของ Word  

ถ้าคุณมีสิ่งเหล่านี้แล้ว ไปต่อกันเลย

---

## ขั้นตอนที่ 1 – โหลดเอกสาร Word ที่มีรูปร่าง

ก่อนอื่นเราจะสร้างอินสแตนซ์ `Document` ที่ชี้ไปยังไฟล์ต้นฉบับของเรา พาธสามารถเป็นแบบเต็มหรือสัมพันธ์กับไฟล์ที่ทำงานได้

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the DOCX that already contains at least one shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **ทำไมเรื่องนี้สำคัญ:** คลาส `Document` เป็นจุดเริ่มต้นของการทำงานทั้งหมดของ Aspose.Words การโหลดไฟล์เพียงครั้งเดียวช่วยลดการใช้หน่วยความจำและทำให้เราสามารถสอบถามโครงสร้างโหนดได้อย่างมีประสิทธิภาพ

## ขั้นตอนที่ 2 – ดึงโหนดรูปร่างแรก

รูปร่างอยู่ภายในลำดับชั้นของโหนดในเอกสาร เราจะขอโหนดประเภท `NodeType.SHAPE` ตัวแรก ธง `true` หมายถึง “ค้นหาอย่างลึก”

```csharp
// Grab the first Shape object in the document (depth‑first search).
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    System.Console.WriteLine("No shape found in the document.");
    return;
}
```

> **เคล็ดลับ:** หากต้องการเจาะจงรูปร่างเฉพาะ ให้กรองด้วย `firstShape.Name` หรือ `firstShape.AlternativeText` แทนการเลือกโหนดแรกเสมอ

## ขั้นตอนที่ 3 – รับอ็อบเจ็กต์เงาที่เชื่อมกับรูปร่าง

ทุก `Shape` มีคุณสมบัติ `Shadow` ซึ่งอาจเป็น `null` หากยังไม่มีเงา การเข้าถึงคุณสมบัตินี้จะให้เราได้อินสแตนซ์ `Shadow` ที่สามารถแก้ไขได้

```csharp
// The Shadow object is automatically created if it doesn't exist.
Shadow shapeShadow = firstShape.Shadow;
```

> **กรณีขอบ:** ไฟล์ Word เก่า (ก่อน‑2007) บางครั้งจัดเก็บเงาในรูปแบบที่ต่างกัน Aspose.Words ทำให้เป็นมาตรฐานเดียวกัน ดังนั้น API เดียวกันทำงานได้กับ DOC, DOCX, และแม้กระทั่ง RTF

## ขั้นตอนที่ 4 – กำหนดรัศมีการเบลอ (หน่วยเป็นจุด)

รัศมีการเบลอ `5.0` จุดให้ขอบนุ่มโดยไม่ดูพร่ามัว

```csharp
shapeShadow.BlurRadius = 5.0;   // points
```

## ขั้นตอนที่ 5 – ตั้งค่าการชิดตำแหน่งแนวนอนและแนวตั้ง

การชิดตำแหน่งจะย้ายเงาเทียบกับรูปร่าง ค่าเป็นบวกจะเลื่อนขวา/ลง; ค่าเป็นลบจะเลื่อนซ้าย/ขึ้น

```csharp
shapeShadow.OffsetX = 3.0;      // move right 3 points
shapeShadow.OffsetY = 3.0;      // move down 3 points
```

## ขั้นตอนที่ 6 – เลือกสีฟ้าสำหรับเงา  

ที่นี่เราจะแสดง **วิธีเปลี่ยนสีเงาใน Word** ด้วยการใช้ `System.Drawing.Color`

```csharp
shapeShadow.Color = Color.Blue;   // any System.Drawing.Color works
```

> **ทำไมสีถึงสำคัญ:** เงาสีฟ้าสามารถให้ความรู้สึกเย็นและเป็นมืออาชีพ ในขณะที่สีเทาเข้มจะดูเป็นกลาง เลือกสีที่สอดคล้องกับแบรนด์ของคุณ

## ขั้นตอนที่ 7 – ปรับความทึบของเงา

ค่าความทึบอยู่ระหว่าง `0.0` (โปร่งใส) ถึง `1.0` (ทึบเต็ม). เราจะใช้ `0.6` เพื่อให้ได้เอฟเฟกต์ที่ละเอียดอ่อน

```csharp
shapeShadow.Opacity = 0.6;   // 60% opacity
```

## ขั้นตอนที่ 8 – บันทึกเอกสารที่แก้ไขแล้ว

สุดท้ายให้เขียนการเปลี่ยนแปลงกลับไปยังดิสก์ คุณสามารถเขียนทับไฟล์เดิมหรือสร้างไฟล์ใหม่ได้

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
System.Console.WriteLine("Shadow applied and document saved.");
```

### ตัวอย่างโปรแกรมเต็มที่ทำงานได้

รวมทุกขั้นตอนเข้าด้วยกัน นี่คือโปรแกรมสมบูรณ์ที่คุณสามารถคัดลอก, วาง, และรันได้:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class AddShadowToShapeDemo
{
    static void Main()
    {
        // 1️⃣ Load the document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Find the first shape
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (firstShape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Get (or create) the shadow object
        Shadow shapeShadow = firstShape.Shadow;

        // 4️⃣ Set blur radius
        shapeShadow.BlurRadius = 5.0;

        // 5️⃣ Set offsets
        shapeShadow.OffsetX = 3.0;
        shapeShadow.OffsetY = 3.0;

        // 6️⃣ Change shadow color (how to change shadow color in Word)
        shapeShadow.Color = Color.Blue;

        // 7️⃣ Set opacity
        shapeShadow.Opacity = 0.6;

        // 8️⃣ Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        System.Console.WriteLine("Shadow applied and document saved.");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิด `output_with_shadow.docx` ใน Microsoft Word. รูปร่างแรกจะแสดงเงาสีฟ้านุ่ม, เลื่อน 3 pt ไปทางขวาและลง, พร้อมการเบลอระดับพอเหมาะและความทึบ 60 %

---

## การจัดการหลายรูปร่าง

หากเอกสารของคุณมีกราฟิกหลายรายการ ให้วนลูปผ่านพวกมัน:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shp in shapes)
{
    // Apply the same shadow settings to each shape
    shp.Shadow.BlurRadius = 5.0;
    shp.Shadow.OffsetX = 3.0;
    shp.Shadow.OffsetY = 3.0;
    shp.Shadow.Color = Color.Blue;
    shp.Shadow.Opacity = 0.6;
}
```

> **หมายเหตุ:** วิธีนี้จะเขียนทับการตั้งค่าเงาที่มีอยู่ หากต้องการเก็บค่าตั้งต้นไว้ ให้ทำการโคลนอ็อบเจ็กต์ `Shadow` ก่อน

## ข้อผิดพลาดทั่วไป & เคล็ดลับ

| ปัญหา | วิธีหลีกเลี่ยง |
|---------|-----------------|
| **`Shape` เป็น `null`** – เอกสารไม่มีกราฟิก | ตรวจสอบ `null` หลังจาก `GetChild` เสมอ |
| **เงามีอยู่แล้ว** – อาจบังสไตล์ที่กำหนดเองโดยไม่ได้ตั้งใจ | อ่านคุณสมบัติของ `shapeShadow` ปัจจุบันก่อนทำการเปลี่ยน |
| **สีไม่ตรง** – ใช้ `System.Drawing.Color` กับ Word เวอร์ชันเก่าอาจทำให้สีเปลี่ยน | ใช้สีมาตรฐานหรือกำหนด ARGB ด้วยตนเอง (`Color.FromArgb(255, 0, 0, 255)`) |
| **ประสิทธิภาพลดลงกับไฟล์ขนาดใหญ่** – การวนลูปหลายพันโหนดอาจช้า | ใช้ `doc.GetChildNodes(NodeType.Shape, false)` หากต้องการเฉพาะรูปร่างระดับบน |

---

## ถ้าต้องการเอฟเฟกต์เงาแบบอื่น?

- **ขอบแข็ง:** ตั้ง `BlurRadius = 0`  
- **ชิดตำแหน่งมาก:** เพิ่ม `OffsetX`/`OffsetY` เป็น 10 pt หรือมากกว่า  
- **ความทึบต่างกัน:** ใช้ค่าเช่น `0.3` สำหรับแสงสว่างอ่อนหรือ `0.9` สำหรับลุคที่เด่นชัด  
- **เงาไล่สี:** Aspose.Words ไม่รองรับเงาไล่สีโดยตรง; คุณต้องแทรกรูปภาพที่มีเอฟเฟกต์ที่เรนเดอร์ไว้ล่วงหน้า  

---

## ตรวจสอบผลลัพธ์ด้วยโปรแกรม

บางครั้งคุณอาจต้องยืนยันการตั้งค่าเงาโดยไม่ต้องเปิด Word:

```csharp
Shadow s = firstShape.Shadow;
System.Console.WriteLine($"Blur: {s.BlurRadius}, OffsetX: {s.OffsetX}, OffsetY: {s.OffsetY}, " +
                         $"Color: {s.Color}, Opacity: {s.Opacity}");
```

หากคอนโซลพิมพ์ค่าที่คุณตั้งไว้ คุณก็รู้ว่าเรียก API สำเร็จแล้ว

---

## สรุป

เราได้แสดง **วิธีเพิ่มเงาให้กับรูปร่าง** ในเอกสาร Word ด้วย Aspose.Words, และสาธิต **วิธีเปลี่ยนสีเงาใน Word** พร้อมการเบลอ, การชิดตำแหน่ง, และความทึบ โค้ดที่ทำงานได้เต็มรูปแบบด้านบนช่วยให้คุณใส่เงาให้กับรูปร่างใดก็ได้ในไม่กี่วินาที พร้อมเคล็ดลับเพิ่มเติมเพื่อหลีกเลี่ยงข้อผิดพลาดทั่วไป  

พร้อมสำหรับความท้าทายต่อไปหรือยัง? ลองเปลี่ยนสีต่าง ๆ ให้กับรูปร่างแต่ละอัน, หรือผสมเงากับการสะท้อนเพื่อเอฟเฟกต์ที่ลึกซึ้งยิ่งขึ้น คุณยังสามารถสำรวจคลาส `ShapeStyle` ของ Aspose.Words เพื่อปรับความหนาของเส้น, รูปแบบการเติม, หรือการหมุน 3‑D  

หากคุณพบว่าคู่มือนี้เป็นประโยชน์ อย่าลืมแชร์ให้ทีม, กดดาวที่รีโปของ Aspose.Words, หรือแสดงความคิดเห็นพร้อมการทดลองของคุณเอง ขอให้เขียนโค้ดอย่างสนุก!  

![รูปร่าง Word พร้อมเงาสีฟ้า – ตัวอย่างการเพิ่มเงาให้กับรูปร่าง](https://example.com/images/shape-shadow.png "ตัวอย่างการเพิ่มเงาให้กับรูปร่าง")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}