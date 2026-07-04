---
category: general
date: 2026-05-01
description: วิธีย้ายเงาบนรูปร่างใน Aspose.Words ด้วย C#. เรียนรู้การเพิ่มเงาให้กับรูปร่าง,
  ปรับความเบลอ, ตั้งค่าความโปร่งใส, และหมุนเงาในเวลาไม่กี่นาที.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: th
og_description: วิธีย้ายเงาบนรูปร่างใน Aspose.Words ด้วย C# บทเรียนนี้จะแสดงวิธีเพิ่มเงาให้กับรูปร่าง
  ปรับความเบลอ ตั้งค่าความโปร่งใส และหมุนเงา
og_title: วิธีย้ายเงาใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Automation
title: วิธีย้ายเงาใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
url: /th/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีย้ายเงาใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์

เคยสงสัย **วิธีย้ายเงา** บนรูปทรงในเอกสาร Word โดยไม่ต้องเปิด Word ด้วยตนเองไหม? ในงานประจำวันของผม ผมมักต้องปรับเงาของรูปทรงโดยโปรแกรม—ไม่ว่าจะเป็นเพื่อรายงานที่ดูเป็นมืออาชีพหรือเทมเพลตแบบไดนามิก ข่าวดีคือ? ด้วย Aspose.Words คุณสามารถทำได้ในไม่กี่บรรทัด และคุณยังจะได้เรียนรู้ **add shadow to shape**, **how to change blur**, **how to set transparency**, และ **how to rotate shadow** ในขั้นตอนเดียว

ในบทแนะนำนี้ เราจะเดินผ่านสถานการณ์จริง: โหลดไฟล์ DOCX ที่มีรูปทรงอยู่แล้ว, ปรับตำแหน่งเงา, ความนุ่ม, ความทึบแสง, และทิศทางของเงา, แล้วบันทึกผลลัพธ์. เมื่อจบคุณจะได้โค้ดสั้นที่นำกลับไปใช้ใหม่ได้ในโปรเจกต์ .NET ใดก็ได้ และคุณจะเข้าใจว่าทำไมแต่ละคุณสมบัติจึงสำคัญ

## ข้อกำหนดเบื้องต้น – สิ่งที่คุณต้องมีก่อนเริ่ม

- **Aspose.Words for .NET** (เวอร์ชัน 23.12 หรือใหม่กว่า) คุณสามารถดาวน์โหลดได้จาก NuGet ด้วยคำสั่ง `Install-Package Aspose.Words`.
- สภาพแวดล้อมการพัฒนา .NET 6+ (Visual Studio, VS Code, Rider—ตามที่คุณชอบ).
- ไฟล์ Word เข้า (`input.docx`) ที่มีอย่างน้อยหนึ่งรูปทรงอยู่แล้ว (เช่น สี่เหลี่ยม, วงกลม, หรือรูปภาพก็ได้).
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#—ไม่ต้องลึกซึ้ง.

หากคุณขาดสิ่งใดสิ่งหนึ่งจากรายการนี้ ให้หยุดพักแล้วติดตั้งไลบรารี; ส่วนที่เหลือของคู่มือถือว่ามีการอ้างอิงแพคเกจแล้ว.

## ขั้นตอนที่ 1: โหลดเอกสารและดึงรูปทรงเป้าหมาย – **How to Move Shadow** เริ่มต้นที่นี่

สิ่งแรกที่เราทำคือโหลดเอกสารต้นฉบับและค้นหารูปทรงที่ต้องการแก้ไข. Aspose.Words ถือว่าวัตถุทุกอย่าง (ย่อหน้า, ตาราง, รูปทรง) เป็นโหนดในโครงสร้างต้นไม้, ดังนั้นเราสามารถสอบถามได้โดยตรง.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **ทำไมเรื่องนี้ถึงสำคัญ:** การโหลดเอกสารเพียงครั้งเดียวและใช้อินสแตนซ์ `Document` เดียวกันซ้ำเป็นการทำงานที่มีประสิทธิภาพ. การเรียก `GetChild` ปลอดภัยเพราะจะคืนค่า `null` หากดัชนีอยู่นอกช่วง, ทำให้เราจัดการกับรูปทรงที่หายไปได้อย่างราบรื่น.

## ขั้นตอนที่ 2: ปรับค่า Blur Radius – Master **How to Change Blur**

เงานุ่มให้ความรู้สึกเป็นมืออาชีพ, ในขณะที่ขอบแข็งอาจดูราคาถูก. คุณสมบัติ `BlurRadius` ควบคุมความนุ่มในหน่วยจุด (1 pt ≈ 1/72 inch). เรามาเพิ่มเป็น 8 pt กัน.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **เคล็ดลับ:** ค่าเบลอเริ่มต้นคือ 0.5 pt. ค่าที่มากกว่า 5 pt มักจะสังเกตได้ชัดเจน, แต่ระวังไม่ให้ใหญ่เกินไป—อาจทำให้รูปทรงดูแยกจากหน้า.

## ขั้นตอนที่ 3: ตั้งค่า Transparency – คำตอบสำหรับ **How to Set Transparency**

Transparency กำหนดว่ามองผ่านเงาได้แค่ไหน. ค่า `0` หมายถึงทึบเต็มที่; `1` หมายถึงโปร่งใสทั้งหมด. เพื่อเอฟเฟกต์ที่ละเอียดอ่อน เราจะใช้ค่า `0.3` (โปร่งใส 30 %).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **ทำไมคุณอาจสนใจ:** หากรูปทรงสีเข้ม, เงาทึบเต็มที่อาจทำให้ข้อความด้านล่างหายไป. การปรับ Transparency ทำให้เอกสารอ่านง่ายขึ้นพร้อมยังคงให้ความลึก.

## ขั้นตอนที่ 4: ย้ายเงา – แกนหลักของ **How to Move Shadow**

คุณสมบัติ `Distance` กำหนดระยะห่างของเงาจากรูปทรง, วัดเป็นจุด. ระยะห่างที่ใหญ่ขึ้นทำให้เงาอยู่ไกลออกไป, สร้างเอฟเฟกต์ที่โดดเด่นยิ่งขึ้น.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **ถ้าต้องการระยะเล็กน้อย?** การตั้งค่า `Distance` เป็น `0` จะทำให้เงาอยู่ตรงหลังรูปทรง, ซึ่งอาจเป็นประโยชน์สำหรับเอฟเฟกต์การอัดลาย.

## ขั้นตอนที่ 5: หมุนแหล่งแสง – แก้ไข **How to Rotate Shadow**

เงาไม่ได้อยู่แค่ลงตรงลงล่าง; มันตามมุมของแหล่งแสง. คุณสมบัติ `Angle` (เป็นองศา) หมุนเงารอบรูปทรง. เรามาเอียงที่ 45° กัน.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **ทดลองเร็ว:** ลองค่า `90` เพื่อให้เงาอยู่ด้านขวา หรือ `-30` เพื่อให้เงาเอียงซ้าย. การเปลี่ยนแปลงจะเห็นได้ทันที.

## ขั้นตอนที่ 6: บันทึกเอกสาร – ดูผลลัพธ์ของ **Add Shadow to Shape**

ตอนนี้เราได้ปรับเงาแล้ว, เราจะเขียนเอกสารกลับไปยังดิสก์. คุณสามารถเขียนทับไฟล์เดิมหรือสร้างไฟล์ใหม่; ตัวอย่างใช้ไฟล์ผลลัพธ์ใหม่.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **ผลลัพธ์ที่คาดหวัง:** เปิด `output.docx`. เงาของรูปทรงจะดูนุ่มขึ้น, เลื่อนตำแหน่งเล็กน้อย, กึ่ง‑โปร่งใส, และเอียงที่ 45°. หากเปรียบเทียบข้างกันกับ `input.docx`, ความแตกต่างจะเห็นได้ชัดเจน.

### ตัวอย่างทำงานเต็ม (พร้อมคัดลอก‑วาง)

ด้านล่างเป็นโปรแกรมทั้งหมดในบล็อกเดียว. คัดลอกไปยังโปรเจกต์คอนโซลใหม่, แทนที่ `YOUR_DIRECTORY` ด้วยเส้นทางโฟลเดอร์จริง, แล้วรัน.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## คำถามทั่วไป & กรณีขอบ

### ถ้าเอกสารมีหลายรูปทรงล่ะ?

คุณสามารถวนลูปผ่านรูปทรงทั้งหมดได้:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### ฉันสามารถเพิ่มเงาให้รูปทรงที่ยังไม่มีเงาได้ไหม?

แน่นอน. วัตถุ `ShadowFormat` มีอยู่เสมอ; คุณแค่ต้องเปิดใช้งานมัน:

```csharp
shape.ShadowFormat.Enabled = true;
```

### วิธีนี้ทำงานกับรูปภาพและ SmartArt หรือไม่?

ใช่. โหนดใด ๆ ที่สืบทอดจาก `Shape`—รวมถึงรูปภาพ, แผนภูมิ, และ SmartArt—มี `ShadowFormat`. คุณสมบัติเหมือนกันใช้ได้.

### ฉันจะควบคุมสีของเงาอย่างไร?

ใช้คุณสมบัติ `Color`:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### ความกังวลเรื่องความเข้ากันได้?

Aspose.Words 23.12+ รองรับ .NET 6, .NET Core 3.1, และ .NET Framework 4.6.2+. API ที่แสดงนี้คงที่ในเวอร์ชันเหล่านี้.

## สรุป

เราได้อธิบาย **วิธีย้ายเงา** บนรูปทรงโดยใช้ Aspose.Words, และในระหว่างนั้นยังได้สาธิต **add shadow to shape**, **how to change blur**, **how to set transparency**, และ **how to rotate shadow**. ตัวอย่างที่สมบูรณ์และสามารถรันได้ทำให้คุณปรับเงาของรูปทรงใดก็ได้ในไม่กี่วินาที, ทำให้เอกสารของคุณดูเรียบหรูและเป็นมืออาชีพโดยไม่ต้องเปิด Word.

พร้อมสำหรับขั้นตอนต่อไปหรือยัง? ลองผสานการปรับเงานี้กับ **conditional formatting**—เช่น ใช้เงาที่ลึกกว่าเฉพาะหัวข้อหรือแผนภูมิที่ใหญ่เกินขนาดที่กำหนด. หรือสำรวจ **gradient fills** สำหรับรูปทรงเองเพื่อสร้างการออกแบบที่ดึงดูดสายตาอย่างแท้จริง.

หากคุณเจออุปสรรคใด ๆ, ฝากคอมเมนต์ด้านล่างได้เลย. ขอให้เขียนโค้ดอย่างสนุกสนาน, และขอให้เงาของคุณตกลงในตำแหน่งที่คุณต้องการเสมอ!

![Diagram showing the effect of moving a shadow on a shape – how to move shadow example](https://example.com/images/shadow-demo.png "how to move shadow example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}