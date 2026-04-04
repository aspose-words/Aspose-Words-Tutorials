---
category: general
date: 2026-04-04
description: สร้างรูปสี่เหลี่ยมใน C# ด้วย Aspose.Words และเรียนรู้วิธีเพิ่มเงา, ทำให้เงาเบลอ,
  และทำให้เงาโปร่งใส – คู่มือขั้นตอนโดยละเอียด
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: th
og_description: สร้างรูปสี่เหลี่ยมใน C# ด้วย Aspose.Words เรียนรู้วิธีเพิ่มเงา, ทำให้เงาเบลอ,
  และทำให้เงาโปร่งใสในบทแนะนำสั้น ๆ.
og_title: สร้างรูปสี่เหลี่ยมและวิธีเพิ่มเงาใน C#
tags:
- Aspose.Words
- C#
- Document Automation
title: สร้างรูปสี่เหลี่ยมและวิธีเพิ่มเงาใน C#
url: /th/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมและวิธีเพิ่มเงาใน C#

เคยต้องการ **create rectangle shape** ในเอกสาร Word แต่ไม่แน่ใจว่าจะให้เงาที่ละเอียดอ่อนอย่างไร? คุณไม่ได้เป็นคนเดียว ในหลายสถานการณ์การรายงานหรือการสร้างแบรนด์ รูปสี่เหลี่ยมง่ายๆ ที่มีเงาอ่อนๆ แบบกึ่งโปร่งแสงสามารถทำให้การจัดวางดูเรียบหรูโดยไม่ต้องใช้ความพยายามมาก

ในบทแนะนำนี้ เราจะอธิบาย **how to create document** ด้วย Aspose.Words แล้วแสดง **how to add shadow**, **apply blur to shadow**, และแม้กระทั่ง **make shadow transparent**. เมื่อเสร็จคุณจะมีโค้ดสแนป C# ที่พร้อมรันซึ่งสร้างไฟล์ *.docx* ที่มีรูปสี่เหลี่ยมที่มีเงาอย่างสวยงาม—ทั้งหมดในไม่กี่นาที

## สิ่งที่คุณต้องการ

- .NET 6 หรือใหม่กว่า (API ทำงานกับ .NET Framework 4.6+ ด้วย)
- Aspose.Words for .NET (รุ่นทดลองฟรีใช้ได้กับตัวอย่างนี้)
- โปรแกรมแก้ไขโค้ด – Visual Studio, VS Code, Rider, หรืออะไรก็ตามที่คุณชอบ
- ความรู้พื้นฐาน C# – ไม่ต้องซับซ้อน เพียงแค่สามารถรันแอปคอนโซลได้

ถ้าคุณมีทั้งหมดนี้ เราก็สามารถกระโดดเข้าสู่การแก้ปัญหาได้ทันที

## ขั้นตอน 1 – วิธีสร้างเอกสารและเริ่มต้นแคนวาส

สิ่งแรกที่ต้องทำคือ คุณต้องมีอ็อบเจ็กต์ `Document` ว่างเปล่า คิดว่าเป็นกระดาษเปล่าที่ Aspose.Words จะเปลี่ยนเป็นไฟล์ Word ในภายหลัง.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

ทำไมเราถึงสร้างอินสแตนซ์ `Document` แทนการโหลดเทมเพลต? การเริ่มจากศูนย์รับประกันว่าจะไม่มีสไตล์หรือส่วนที่ซ่อนอยู่แทรกแซงสี่เหลี่ยมของเรา อีกทั้งยังทำให้ขนาดไฟล์เล็กลง – นิสัยที่ดีเมื่อคุณสร้างเอกสารหลายไฟล์ในลูป

## ขั้นตอน 2 – สร้างรูปสี่เหลี่ยม (หัวใจของคีย์เวิร์ดหลักของเรา)

ตอนนี้เราจริงๆ แล้ว **create rectangle shape**. คลาส `Shape` มีความยืดหยุ่น; คุณบอกประเภท (Rectangle), ขนาด, และวิธีการห่อหุ้มกับข้อความรอบข้าง.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

สังเกตการใช้ syntax ของ object initializer – มันกระชับและลดความเสี่ยงที่จะลืมตั้งค่าคุณสมบัติในภายหลัง สี่เหลี่ยมจะอยู่ภายในย่อหน้าแรก ซึ่งเราจะเพิ่มในขั้นตอนต่อไป

## ขั้นตอน 3 – วิธีเพิ่มเงาและปรับแต่งลักษณะของมัน

การเพิ่มเงาไม่ได้เป็นแค่บรรทัดเดียว; คุณมีหลายคุณสมบัติให้ปรับแต่ง ที่นี่คือจุดที่คีย์เวิร์ดรอง **apply blur to shadow** และ **make shadow transparent** เข้ามามีบทบาท.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

หมายเหตุสั้นๆ เกี่ยวกับตัวเลข: `BlurRadius` ที่ 5 ให้การเบลออ่อนๆ; เพิ่มเป็น 10 เพื่อให้ดูนุ่มขึ้น หรือ ลดเป็น 2 เพื่อให้ขอบคมชัด. ค่าของ `Transparency` อยู่ระหว่าง 0 (ทึบ) ถึง 1 (โปร่งใส). ปรับตามความต้องการความคอนทราสต์ของแบรนด์ของคุณ

### เคล็ดลับพิเศษ

หากคุณต้องการเงาสี (เช่นสีน้ำเงินของบริษัท) เพียงเปลี่ยน `Color.DarkGray` เป็น `Color.FromArgb(80, 0, 120, 215)`. อาร์กิวเมนต์แรกคือช่อง alpha – ควรตั้งค่าน้อยเพื่อความละเอียดอ่อน

## ขั้นตอน 4 – แทรกรูปร่างลงในเอกสาร

เมื่อสี่เหลี่ยมและเงาพร้อมแล้ว เราจะวางมันลงในย่อหน้าแรกของเอกสาร ขั้นตอนนี้ทำให้รูปปรากฏที่ส่วนบนสุดของไฟล์.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

ทำไมถึงใช้ย่อหน้าแรก? มันเป็นค่าเริ่มต้นที่ปลอดภัยและทำงานได้แม้เอกสารจะว่างเปล่า หากคุณต้องการตำแหน่งเฉพาะ (เช่น หลังหัวข้อ) คุณจะต้องค้นหาโหนดนั้นและแทรกรูปร่างที่นั่นแทน

## ขั้นตอน 5 – บันทึกไฟล์และตรวจสอบผลลัพธ์

สุดท้าย เราจะบันทึกเอกสารลงดิสก์ คุณสามารถเลือกเส้นทางใดก็ได้ที่ต้องการ; เพียงตรวจสอบให้โฟลเดอร์มีอยู่

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

เมื่อคุณเปิด *ShadowRectangle.docx* ใน Microsoft Word คุณควรเห็นสี่เหลี่ยมขนาด 200 × 100‑point ที่มีเงาสีเทาเข้ม, เบลอเล็กน้อย, โปร่งใส 30 % และเลื่อนตำแหน่งสามพอยต์ไปทางขวาและลงลง ผลลัพธ์เป็นเงาที่ละเอียดอ่อนแต่เพิ่มความลึกให้กับการจัดวางที่แบนราบ

![สร้างรูปสี่เหลี่ยมพร้อมเงาใน Aspose.Words](https://example.com/placeholder-image.png "สร้างรูปสี่เหลี่ยมพร้อมเงาใน Aspose.Words")

*ข้อความอธิบายภาพ:* **สร้างรูปสี่เหลี่ยมพร้อมเงาใน Aspose.Words** – ภาพแสดงเอกสารสุดท้ายที่มีสี่เหลี่ยมที่มีเงา

## ความหลากหลายทั่วไปและกรณีขอบ

### การเปลี่ยนสีเงาแบบไดนามิก

หากแอปของคุณรองรับธีม คุณอาจดึงสีเงาจากไฟล์การกำหนดค่า:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### ทำให้รูปไม่เป็นอินไลน์

บางครั้งคุณอาจต้องการให้สี่เหลี่ยมลอยเหนือข้อความ เปลี่ยน `WrapType` เป็น `WrapType.Square` และตั้งค่า `RelativeHorizontalPosition` เป็น `RelativeHorizontalPosition.Margin` เพื่อควบคุมมากขึ้น

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### การจัดการหลายหน้า

หากคุณต้องการสี่เหลี่ยมบนทุกหน้า ให้วนลูปผ่าน `doc.Sections` และเพิ่มรูปที่คล cloned ไปยังย่อหน้าแรกของแต่ละส่วน อย่าลืมเรียก `rect.Clone(true)` เพื่อทำสำเนาการตั้งค่าเงาด้วย

## สรุป – สิ่งที่เราทำสำเร็จ

- **Created rectangle shape** using Aspose.Words
- **How to add shadow** with colour, offset, blur, and transparency
- Demonstrated **apply blur to shadow** and **make shadow transparent**
- บันทึกไฟล์ Word ที่คุณสามารถเปิดได้ทันที

ทั้งหมดนี้ทำได้ด้วยเพียงไม่กี่บรรทัด แสดงให้เห็นว่าการปรับแต่งภาพที่ซับซ้อนไม่จำเป็นต้องใช้ไลบรารีกราฟิกขนาดใหญ่เสมอ

## ต่อไปคืออะไร?

- ทดลองใช้ `ShapeType` อื่นๆ (Ellipse, Cloud, ฯลฯ) และดูว่าเงาตอบสนองอย่างไร
- ผสานสี่เหลี่ยมกับกล่องข้อความเพื่อสร้าง call‑outs ที่มีป้ายกำกับ
- ศึกษา **how to create document** เทมเพลตที่มีตัวแทนสำหรับรูปแล้วเติมข้อมูลโดยโปรแกรม

ปรับค่า blur radius, สี, หรือความโปร่งใสได้ตามต้องการจนกว่าเงาจะดูพอดีกับภาษาการออกแบบของคุณ API มีความยืดหยุ่นและการเปลี่ยนแปลงจะเห็นได้ทันทีเมื่อคุณรันแอปคอนโซลใหม่

ขอให้เขียนโค้ดอย่างสนุกสนาน และขอให้เอกสารของคุณมีมิติที่เพิ่มขึ้นเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}