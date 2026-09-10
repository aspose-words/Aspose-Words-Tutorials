---
category: general
date: 2026-01-03
description: สร้างรูปสี่เหลี่ยมใน Word ด้วย C# แล้วเพิ่มเงาให้รูป เรียนรู้วิธีแทรกรูปใน
  Word, เพิ่มเงาให้รูป, และสร้างเอกสาร Word อย่างอัตโนมัติ.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: th
og_description: สร้างรูปสี่เหลี่ยมใน Word ด้วย C# และเพิ่มเงาให้รูป ปฏิบัติตามคู่มือนี้เพื่อแทรกรูปใน
  Word ตั้งค่าเงา และสร้างเอกสารโดยอัตโนมัติ
og_title: สร้างรูปสี่เหลี่ยมใน Word ด้วย C# – คู่มือเต็มขั้น
tags:
- C#
- Word Automation
- Aspose.Words
title: สร้างรูปสี่เหลี่ยมใน Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด
url: /th/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมใน Word ด้วย C# – บทเรียนเต็ม

เคยต้องการ **create rectangle shape** ในเอกสาร Word แต่ไม่แน่ใจว่าจะเริ่มอย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนาหลายคนเจออุปสรรคเดียวกันเมื่อพวกเขาต้องการ **add shadow to shape** เพื่อให้ดูเป็นมืออาชีพ ในบทเรียนนี้เราจะอธิบายขั้นตอนที่แม่นยำเพื่อ **insert shape in Word**, ใส่เงาที่ละเอียดอ่อน, และสุดท้าย **c# generate word document** ไฟล์ที่คุณสามารถส่งให้ผู้ใช้ได้.

เราจะครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโปรเจกต์จนถึงการปรับคุณสมบัติเชด, และจะสรุปด้วยตัวอย่างโค้ดที่พร้อมรัน. ไม่มีส่วนเกิน, เพียงส่วนที่ใช้งานจริงที่ทำให้สำเร็จ.

## สิ่งที่คุณจะได้เรียนรู้

- วิธี **create rectangle shape** ด้วย Aspose.Words (หรือ Open XML) ใน C#
- คุณสมบัติเฉพาะที่คุณต้องการเพื่อ **add shadow to shape** ให้มีความลึก
- ตำแหน่งที่ใส่รูปโดยใช้ `DocumentBuilder`
- วิธีบันทึกไฟล์เพื่อให้เปิดได้อย่างถูกต้องใน Microsoft Word
- เคล็ดลับ, จุดบกพร่อง, และรูปแบบต่าง ๆ สำหรับสถานการณ์จริง

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดทำงานบน .NET Core และ .NET Framework)
- แพคเกจ NuGet ที่สามารถจัดการไฟล์ Word – เราจะใช้ **Aspose.Words for .NET** เนื่องจาก API ของมันกระชับ. หากคุณชอบใช้ Open XML SDK, แนวคิดเดียวกัน, เพียงแต่คลาสต่างกัน.
- Visual Studio, VS Code, หรือ IDE C# ใด ๆ ที่คุณชอบ

> **Pro tip:** หากคุณมีงบประมาณจำกัด, Aspose มีเวอร์ชันทดลองฟรีที่เหมาะสำหรับการเรียนรู้. เพียงเปลี่ยนบรรทัดลิขสิทธิ์เป็นคอมเมนต์เมื่อทดสอบ.

## ขั้นตอน 1: ติดตั้งไลบรารีการประมวลผล Word

แรก, เพิ่มไลบรารีลงในโปรเจกต์ของคุณ. เปิดเทอร์มินัลในโฟลเดอร์โซลูชันและรัน:

```bash
dotnet add package Aspose.Words
```

หากคุณใช้ Open XML SDK, คำสั่งจะเป็น `dotnet add package DocumentFormat.OpenXml`. ส่วนที่เหลือของคู่มือนี้ถือว่าใช้ Aspose.Words, แต่การสลับการเรียก API นั้นทำได้ง่าย.

## ขั้นตอน 2: สร้างเอกสารเปล่าใหม่

เมื่อไลบรารีพร้อมแล้ว, เราสามารถ **create rectangle shape** โดยเริ่มจากอ็อบเจกต์ `Document` ที่ว่างเปล่า. คิดว่าเป็นผืนผ้าใบใหม่.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` ให้วิธีระดับสูงในการแทรกเนื้อหาโดยไม่ต้องลึกลงไปในโครงสร้างโหนดระดับต่ำ.

## ขั้นตอน 3: แทรกรูปสี่เหลี่ยม

เมื่อมี builder อยู่ในมือ, เราสามารถ **insert shape in Word**. เมธอด `InsertShape` รับประเภทของรูปและขนาด (ความกว้าง, ความสูง) เป็นหน่วย points.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

ในขั้นตอนนี้สี่เหลี่ยมปรากฏในเอกสาร, แต่ดูแบนเล็กน้อย. ขั้นตอนต่อไปจะช่วยแก้.

## ขั้นตอน 4: เพิ่มเงาให้รูป

เงาจะทำให้รูปมีความลึก. อ็อบเจกต์ `Shadow` ให้เราปรับค่า blur, distance, angle, color, และ transparency อย่างละเอียด. ด้านล่างเป็นการตั้งค่าครบที่ทำงานได้ดีสำหรับรายงานส่วนใหญ่.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**ทำไมถึงใช้ค่าต่าง ๆ เหล่านี้?**  
- **BlurRadius** ที่ `5.0` ทำให้ขอบเรียบโดยไม่ดูเบลอ.  
- **Distance** ที่ `4.0` ทำให้เงาเลื่อนออกมาพอให้สังเกตเห็น.  
- **Angle** `45` จำลองแสงธรรมชาติจากด้านบน‑ซ้าย, เป็นมาตรฐาน UI ที่พบบ่อย.  
- **Transparency** `0.3` ป้องกันไม่ให้เงาเกินกว่าการเติมสีของรูป.

หากต้องการเอฟเฟกต์ที่เด่นชัดขึ้น, เพิ่มค่า `BlurRadius` และลดค่า `Transparency`. สำหรับการยกที่ละเอียดและเกือบมองไม่เห็น, ปรับค่าตรงกันข้าม.

## ขั้นตอน 5: บันทึกเอกสาร

สุดท้าย, เขียนไฟล์ลงดิสก์. เมธอด `Save` ตรวจจับรูปแบบจากส่วนขยายไฟล์, ดังนั้น `.docx` จะให้รูปแบบ Word สมัยใหม่.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

เปิด `ShadowRectangle.docx` ใน Microsoft Word, แล้วคุณจะเห็นสี่เหลี่ยมคมชัดพร้อมเงานุ่ม—ตรงกับที่คุณต้องการเมื่อถาม “**how to add shape**” ด้วยการทำให้ดูเป็นมืออาชีพ.

![สร้างรูปสี่เหลี่ยมพร้อมเงาใน Word](placeholder-image.png "สร้างรูปสี่เหลี่ยมพร้อมเงาใน Word")

*ข้อความแทนภาพ: สร้างรูปสี่เหลี่ยมพร้อมเงาใน Word*

## ตัวอย่างทำงานเต็ม

รวมทุกอย่างเข้าด้วยกัน, นี่คือโปรแกรมที่สมบูรณ์พร้อมรัน. คัดลอก‑วางลงในแอปคอนโซลและกด **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

- ไฟล์ `ShadowRectangle.docx` ที่สร้างขึ้นมี **หนึ่งรูปสี่เหลี่ยม** อยู่ตรงกลางตำแหน่งที่เคอร์เซอร์วาง.  
- สี่เหลี่ยมแสดง **เงาดำนุ่ม, โปร่งแสง 30 %** ที่เลื่อนออกที่มุม 45°.  
- ไม่มีเนื้อหาอื่นเพิ่ม, ทำให้ไฟล์มีขนาดเบาและง่ายต่อการฝังในรายงานที่ใหญ่ขึ้น.

## คำถามทั่วไป & กรณีขอบ

### ถ้าต้องการรูปแบบอื่น?

แทนที่ `ShapeType.Rectangle` ด้วยค่า `ShapeType` ใด ๆ ที่ต้องการ (เช่น `Ellipse`, `Triangle`). API ของเงาทำงานเช่นเดียวกัน, ดังนั้นคุณสามารถใช้การตั้งค่าเดิมได้.

### จะเปลี่ยนสีเติมอย่างไร?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### สามารถเพิ่มรูปลงในย่อหน้าที่ระบุได้หรือไม่?

ได้. ย้าย `DocumentBuilder` ไปยังย่อหน้าที่ต้องการด้วย `builder.MoveToParagraph(index)` ก่อนเรียก `InsertShape`. วิธีนี้ทำให้รูปปรากฏตรงตำแหน่งที่ต้องการ.

### แล้วรูปแบบ Word เก่า (.doc) ล่ะ?

เพียงเปลี่ยนส่วนขยาย:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

ฟีเจอร์เงาถูกสนับสนุนตั้งแต่ Word 2003 ขึ้นไป, ดังนั้นคุณยังจะเห็นเอฟเฟกต์.

### ใช้ Open XML SDK แทน Aspose?

ขั้นตอนยังคงเหมือนเดิม: สร้าง `WordprocessingDocument`, เพิ่มองค์ประกอบ `Drawing`, ตั้งค่าคุณสมบัติ `<a:shadow>`. XML จะยาวกว่า, แต่แนวคิดเดียวกัน (ขนาด, blur, distance, angle) ยังคงใช้ได้.

## เคล็ดลับเพื่อหลีกเลี่ยงข้อผิดพลาด

- **อย่าลืมลิขสิทธิ์** หากคุณใช้เวอร์ชัน Aspose ที่ต้องชำระเงิน; มิฉะนั้นคุณจะได้รับลายน้ำ.  
- **หน่วยเป็น points**, ไม่ใช่พิกเซล. พิกเซลหน้าจอทั่วไป ≈ 0.75 pt, ดังนั้นปรับขนาดตามนั้น.  
- **คุณสมบัติของเงาจะถูกละเลย** หาก `WrapType` ของรูปตั้งเป็น `Inline`. ใช้ `WrapType = WrapType.Square` สำหรับรูปแบบลอยที่ให้เงาถูกเรนเดอร์.  
- **การบันทึกไปยังแชร์เครือข่าย** อาจต้องการสิทธิ์ที่เหมาะสม; ควรทดสอบเส้นทางก่อนเสมอ.

## สรุป

ตอนนี้คุณรู้วิธี **create rectangle shape** ในเอกสาร Word ด้วย C#, **add shadow to shape**, และ **c# generate word document** ที่ดูเป็นมืออาชีพตั้งแต่แรก. ขั้นตอนหลัก—ติดตั้งไลบรารี, สร้างอินสแตนซ์ `Document`, แทรกรูป, ตั้งค่าเงา, และบันทึก—ง่ายต่อการจำและปรับใช้กับรูปแบบอื่น, สีอื่น, หรือแม้แต่ข้อมูลแบบไดนามิก.

ต่อไปทำอะไร? ลองวางหลายรูปซ้อนกัน, ฝังรูปภาพ, หรือสร้างรายงานเต็มรูปแบบด้วยตารางและแผนภูมิ. คุณยังสามารถสำรวจการจัดรูปแบบตามเงื่อนไข—เปลี่ยนความเข้มของเงาตามค่าข้อมูล—เพื่อทำให้เอกสารของคุณไม่เพียงทำงานได้ แต่ยังดึงดูดสายตา.

ทดลองได้ตามสบาย, และหากเจอปัญหาใด ๆ, ทิ้งคอมเมนต์ด้านล่าง. โค้ดดิ้งให้สนุก, และขอให้เอกสาร Word ของคุณมีเงาที่สมบูรณ์แบบเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}