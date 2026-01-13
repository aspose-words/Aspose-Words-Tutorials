---
category: general
date: 2026-01-13
description: สร้างเอกสาร Word ด้วย Aspose.Words และเรียนรู้วิธีแทรกรูปสี่เหลี่ยม วิธีเพิ่มเงา
  และเพิ่มเงาให้รูปใน C# พร้อมตัวอย่างครบถ้วนรวมอยู่ด้วย.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: th
og_description: สร้างเอกสาร Word ด้วย Aspose.Words, ดูวิธีแทรกรูปสี่เหลี่ยมและวิธีเพิ่มเงา.
  ทำตามตัวอย่าง C# อย่างครบถ้วน.
og_title: สร้างเอกสาร Word พร้อมสี่เหลี่ยมเงา – บทเรียนเต็ม
tags:
- Aspose.Words
- C#
- Document Automation
title: สร้างเอกสาร Word พร้อมสี่เหลี่ยมเงา – คู่มือขั้นตอนโดยละเอียด
url: /th/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word พร้อมสี่เหลี่ยมเงา – คู่มือขั้นตอนโดยละเอียด

เคยต้องการ **create word document** ที่มีสี่เหลี่ยมที่มีเงาสวยงามอยู่บ้างหรือไม่ แต่ไม่แน่ใจว่าจะเริ่มต้นอย่างไร? คุณไม่ได้เป็นคนเดียว—นักพัฒนาหลายคนเจออุปสรรคเดียวกันเมื่อต้องเริ่มต้นใช้งาน Aspose.Words.  

ในบทแนะนำนี้ เราจะพาคุณผ่านทุกอย่างที่คุณต้องการเพื่อ **create word document** อย่างโปรแกรม, **insert rectangle shape**, และแสดง **how to add shadow** เพื่อให้รูปทรงโดดเด่นขึ้น สุดท้ายคุณจะได้โค้ดสแนป C# ที่พร้อมรันและสามารถนำไปใส่ในโปรเจค .NET ใดก็ได้.

## สิ่งที่คุณจะได้เรียนรู้

- โค้ดที่แม่นยำสำหรับ **how to insert shape** (สี่เหลี่ยม) ลงในไฟล์ Word  
- คุณสมบัติที่ต้องปรับเพื่อ **add shape shadow** และควบคุมลักษณะการแสดงผล  
- วิธีบันทึกผลลัพธ์และตรวจสอบว่าเงาปรากฏอยู่  
- เคล็ดลับเชิงปฏิบัติและหมายเหตุกรณีขอบที่ช่วยลดปัญหาในภายหลัง  

ไม่ต้องอ้างอิงเอกสารภายนอก—ทุกอย่างอยู่ที่นี่

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มลงลึก ตรวจสอบให้แน่ใจว่าคุณมี:

1. **.NET 6.0** (หรือเวอร์ชัน .NET ล่าสุด) ที่ติดตั้งไว้  
2. **license** สำหรับ Aspose.Words for .NET, หรือคุณสามารถใช้โหมดประเมินผลฟรีสำหรับการทดสอบ  
3. สภาพแวดล้อมการพัฒนา—Visual Studio 2022 ทำงานได้ดี, แต่เครื่องมือแก้ไขใด ๆ ที่สามารถคอมไพล์ C# ก็ใช้ได้  

เท่านี้เอง ไม่ต้องการแพ็กเกจ NuGet เพิ่มเติมนอกจาก `Aspose.Words`

## ขั้นตอนที่ 1 – ตั้งค่าโปรเจคและอ้างอิง Aspose.Words

ขั้นแรก สร้างแอปคอนโซลใหม่และเพิ่มแพ็กเกจ Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** หากคุณใช้รุ่นทดลองฟรี อย่าลืมเรียก `License.SetLicense` พร้อมไฟล์ลิขสิทธิ์ของคุณ; มิฉะนั้นไลบรารีจะใส่น้ำหนักโลโก้

## ขั้นตอนที่ 2 – เริ่มต้น Document Builder

ตอนนี้เราจะเริ่มกระบวนการ **create word document** จริง ๆ คลาส `Document` ให้ผืนผ้าใบเปล่า, และ `DocumentBuilder` ให้เราวาดบนมัน.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

ทำไมเราต้องใช้ builder? มันซ่อนรายละเอียดระดับต่ำของ OpenXML ทำให้คุณโฟกัสที่ *สิ่งที่* ต้องการแทนที่จะเป็น *วิธี* ที่ไฟล์ถูกจัดโครงสร้าง นี่คือหัวใจของ **how to insert shape** อย่างรวดเร็ว

## ขั้นตอนที่ 3 – แทรกสี่เหลี่ยม

นี่คือจุดที่เราจริง ๆ **insert rectangle shape** สี่เหลี่ยมจะมีขนาด 150 × 100 จุด (ประมาณ 2 นิ้ว × 1.3 นิ้ว)

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

เมธอด `InsertShape` จะคืนค่าเป็นอ็อบเจ็กต์ `Shape` ซึ่งเราสามารถปรับแต่งต่อได้ ณ จุดนี้สี่เหลี่ยมเป็นกล่องสีขาวทึบ—ยังไม่มีเงา

## ขั้นตอนที่ 4 – วิธีเพิ่มเงา (Add Shape Shadow)

การเพิ่มเงานั้นง่ายกว่าที่คิดเมื่อคุณรู้ว่าต้องแก้ไขคุณสมบัติใด `ShadowFormat` ควบคุมการมองเห็น, สี, ความเบลอ, การเลื่อน, และขนาด

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

บล็อกนั้นตอบ **how to add shadow** อย่างตรงไปตรงมา: เปิดใช้งาน, เลือกสี, ปรับความโปร่งใส, การเลื่อน, ความเบลอ, และขนาด คุณสามารถทดลองค่าต่าง ๆ เพื่อให้ได้เงาหนาแบบดรอปชัดหรือเงาบางเบา

### การปรับเปลี่ยนทั่วไป

- **Different colours:** ใช้ `Color.Black` สำหรับเงาดรอปคลาสสิก, หรือ `Color.BlueViolet` สำหรับเอฟเฟกต์สไตล์  
- **Zero blur:** ตั้งค่า `BlurRadius = 0` เพื่อให้ขอบคมชัด  
- **Larger offsets:** เพิ่มค่า `OffsetX`/`OffsetY` เพื่อดันเงาให้ห่างจากรูปทรงมากขึ้น

## ขั้นตอนที่ 5 – บันทึกเอกสารและตรวจสอบ

สุดท้าย เขียนเอกสารลงดิสก์ ไฟล์จะเป็น `.docx` มาตรฐานที่โปรแกรมประมวลผล Word สมัยใหม่ใด ๆ ก็เปิดได้

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

เปิดไฟล์ *ShadowRectangle.docx* ที่สร้างขึ้นใน Microsoft Word คุณควรเห็นสี่เหลี่ยมที่มีเงาสีเทานุ่มเลื่อนไปด้านล่าง‑ขวา—ตรงกับที่โค้ดระบุ

> **Expected output:** ผลลัพธ์ที่คาดหวัง: ไฟล์ Word หน้าหนึ่งที่มีสี่เหลี่ยมขนาด 150 × 100 จุด พร้อมเงาสีเทาโปร่งใส 30 % เลื่อน 5 จุด, เบลอ 4 จุด, และขนาดที่ 75 % ของรูปทรง

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมที่สมบูรณ์พร้อมรัน:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

รันโปรแกรม (`dotnet run`) แล้วคุณจะได้ไฟล์ Word ใหม่ที่มีสี่เหลี่ยมเงานุ่ม—เหมาะสำหรับรายงาน, ใบรับรอง, หรือสัญญาณภาพใด ๆ ที่คุณต้องการ

## คำถามที่พบบ่อย (FAQs)

**Q: ฉันสามารถแทรกรูปทรงอื่น (วงรี, ดาว) และยังใช้โค้ดเงาเดียวกันได้ไหม?**  
A: แน่นอน เมธอด `InsertShape` รองรับค่า `ShapeType` ใดก็ได้ เมื่อคุณมีอ็อบเจ็กต์ `Shape` คุณสมบัติ `ShadowFormat` ทำงานเช่นเดียวกัน ดังนั้น **how to add shadow** ไม่ขึ้นกับรูปทรง  

**Q: ถ้าฉันต้องการเงาทั้งสองด้านของรูปทรงจะทำอย่างไร?**  
A: Aspose.Words รองรับเงาดรอปเดียวต่อรูปทรงเท่านั้น เพื่อจำลองเอฟเฟกต์สองด้าน ให้ทำสำเนารูปทรง, เลื่อนแต่ละสำเนาแตกต่างกัน, และตั้งค่า `ShadowFormat.Visible` ของหนึ่งเป็น `false` ส่วนอีกอันให้เงาแสดงอยู่  

**Q: โค้ดนี้ทำงานบน .NET Framework 4.8 หรือไม่?**  
A: ใช่ API ไม่ขึ้นกับเวอร์ชัน; เพียงอ้างอิง DLL Aspose.Words ที่เหมาะกับเฟรมเวิร์กเป้าหมายของคุณ  

## เคล็ดลับและข้อควรระวัง

- **อย่าลืมตั้งค่า `Visible = true`**—หากไม่ตั้งค่า คุณสมบัติของเงาจะถูกละเลย  
- **ค่าความโปร่งใสอยู่ระหว่าง 0.0 (ทึบ) ถึง 1.0 (โปร่งใสเต็ม)** ความผิดพลาดทั่วไปคือใช้ `30` แทน `0.3`  
- **การบันทึกลงโฟลเดอร์ที่อ่าน‑อย่างอย่างเดียวจะทำให้เกิดข้อยกเว้น** ตรวจสอบให้แน่ใจว่าไดเรกทอรีปลายทางสามารถเขียนได้  

## ขั้นตอนต่อไป

ตอนนี้คุณรู้ **how to insert shape**, **add shape shadow**, และ **create word document** ด้วย Aspose.Words แล้ว คุณอาจอยากสำรวจ:

- เพิ่ม **text inside the rectangle** ด้วย `builder.InsertParagraph()` ก่อนแทรกรูปทรง  
- ใช้ **gradient fills** หรือ **patterned borders** เพื่อสไตล์ภาพที่หลากหลายขึ้น  
- ทำอัตโนมัติการสร้างหลายหน้า แต่ละหน้ามีรูปทรงเงาต่างกัน เพื่อสร้างรายงานแบบไดนามิก  

ทดลองได้ตามสบาย—การเปลี่ยนสี, ความเบลอ, หรือขนาดของเงาสามารถเปลี่ยนรูปลักษณ์ของเอกสารได้อย่างมาก

*พร้อมนำไปใช้ในผลิตภัณฑ์จริงหรือยัง? ดึงโค้ด, ปรับพารามิเตอร์, แล้วดูไฟล์ Word ของคุณได้รับการตกแต่งระดับมืออาชีพในไม่กี่วินาที*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}