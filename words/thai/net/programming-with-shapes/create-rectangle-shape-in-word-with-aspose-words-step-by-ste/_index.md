---
category: general
date: 2026-02-18
description: สร้างรูปสี่เหลี่ยมโดยใช้ Aspose.Words และเรียนรู้วิธีเพิ่มเงา ตั้งขนาดรูปทรง
  และบันทึกเอกสาร Word ในเวลาไม่กี่นาที
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: th
og_description: สร้างรูปสี่เหลี่ยมในไฟล์ Word, เรียนรู้วิธีเพิ่มเงา, ตั้งค่าขนาดรูป,
  และบันทึกเอกสารด้วย Aspose.Words ใน C#
og_title: สร้างรูปสี่เหลี่ยมใน Word – คู่มือ Aspose.Words อย่างสมบูรณ์
tags:
- Aspose.Words
- C#
- Word automation
title: สร้างรูปสี่เหลี่ยมผืนผ้าใน Word ด้วย Aspose.Words – คู่มือแบบทีละขั้นตอน
url: /th/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

"เขียนโค้ดให้สนุก!"

Also translate "Step 1: Initialize the document – the foundation of **how to create document**" etc.

Make sure to keep bold formatting.

Also blockquote > lines.

Let's produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด

เคยต้อง **สร้างรูปสี่เหลี่ยม** ในไฟล์ Word แต่ไม่รู้จะเริ่มต้นอย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนามักถามว่า “จะเพิ่มเงาให้รูปแล้วยังคงให้เอกสารแก้ไขได้อย่างไร?” ในบทเรียนนี้เราจะตอบคำถามนั้นและยังแสดงให้คุณเห็น **วิธีเพิ่มเงา**, **ตั้งขนาดรูป**, และ **บันทึกไฟล์ Word** ทั้งหมดในกระบวนการเดียวที่ราบรื่น

เราจะพาคุณผ่านทุกขั้นตอนที่ต้องการ ตั้งแต่การเริ่มต้นเอกสารใหม่ (ใช่, นั่นคือขั้นตอนแรกของ **วิธีสร้างเอกสาร**) จนถึงการบันทึกไฟล์ *.docx* สุดท้ายบนดิสก์ ไม่ต้องอ้างอิงภายนอก เพียงตัวอย่างที่สามารถคัดลอก‑วางไปยัง Visual Studio แล้วรันได้ทันที

---

## ข้อกำหนดเบื้องต้น

- .NET 6+ (หรือ .NET Framework 4.7+). Aspose.Words ทำงานกับ runtime .NET ใดก็ได้ที่ทันสมัย
- ใบอนุญาต Aspose.Words ที่ถูกต้อง (หรือคีย์ทดลองฟรี) – หากไม่มีจะเห็นลายน้ำ
- Visual Studio, Rider, หรือเครื่องมือแก้ไข C# ที่คุณชื่นชอบ
- ความรู้พื้นฐาน C#—ไม่ต้องซับซ้อน เพียงสามารถรันแอปคอนโซลได้

> **เคล็ดลับระดับมืออาชีพ:** หากคุณใช้ Mac, โค้ดเดียวกันทำงานได้บน .NET 6 กับ VS Code—แค่ตรวจสอบให้แน่ใจว่าได้อ้างอิงแพคเกจ NuGet `Aspose.Words`

---

## ขั้นตอนที่ 1: เริ่มต้นเอกสาร – พื้นฐานของ **วิธีสร้างเอกสาร**

ก่อนที่เราจะวาดอะไรได้ เราต้องมีผืนผ้าใบเปล่า Aspose.Words เรียกสิ่งนี้ว่า `Document`  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **ทำไมจึงสำคัญ:** วัตถุ `Document` แทนไฟล์ *.docx* ทั้งหมด รูป, ย่อหน้า, และส่วนต่าง ๆ ที่คุณเพิ่มจะเป็นลูกของวัตถุนี้ การเริ่มต้นด้วยเอกสารเปล่าช่วยให้ไม่มีสไตล์ที่ซ่อนอยู่มาขัดขวางรูปสี่เหลี่ยมของคุณ

---

## ขั้นตอนที่ 2: กำหนดรูปสี่เหลี่ยมและ **ตั้งขนาดรูป**

รูปสี่เหลี่ยมคือเพียง `Shape` ที่มี `ShapeType.Rectangle` เราจะกำหนดขนาดอย่างชัดเจนเพื่อให้แสดงตามที่ต้องการ  

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **ความหมายของตัวเลข:** Aspose.Words ใช้หน่วยจุด (1 pt = 1/72 in) ปรับค่าตามการจัดวางของคุณ; สำหรับหน้า A4 ปกติ 200 pt เป็นความกว้างที่พอเหมาะ

---

## ขั้นตอนที่ 3: **วิธีเพิ่มเงา** – ทำให้รูปโดดเด่น

เงาช่วยให้มองเห็นว่ารูป “ลอย” จากหน้า `Shadow` ให้คุณปรับสี, ระยะ, ความโปร่งใส, และความเบลอ  

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **ทำไมต้องใช้ความโปร่งใส?** เงาที่ทึบเต็มจะดูแข็งกระด้าง การตั้งค่าเป็น 0.4 ทำให้เอฟเฟกต์ดูอ่อนโยนและเป็นมืออาชีพ

---

## ขั้นตอนที่ 4: กำหนดตำแหน่งรูปสี่เหลี่ยม – การไหลแบบ inline กับข้อความรอบข้าง

หากต้องการให้รูปทำงานเหมือนอักขระในย่อหน้า ตั้ง `WrapType` เป็น `Inline` วิธีนี้ทำให้การจัดวางคาดเดาได้ง่าย โดยเฉพาะเมื่อเอกสารถูกแก้ไขในภายหลัง  

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **กรณีพิเศษ:** หากต้องการให้รูปลอยเหนือข้อความ (เช่น ลายน้ำ) ให้เปลี่ยน `WrapType` เป็น `Square` หรือ `BehindText`

---

## ขั้นตอนที่ 5: แทรกรูปลงในเนื้อหาเอกสาร

ตอนนี้เราจะวางรูปสี่เหลี่ยมลงในย่อหน้าแรก หากเอกสารยังไม่มีเนื้อหา `FirstParagraph` จะถูกสร้างโดยอัตโนมัติ  

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **เคล็ดลับ:** คุณสามารถสร้างย่อหน้าใหม่ก่อนแล้วค่อยต่อรูปเข้าไป—เป็นประโยชน์เมื่อต้องการข้อความรอบ ๆ รูป

---

## ขั้นตอนที่ 6: **บันทึกไฟล์ Word** – ขั้นตอนสุดท้าย

เมื่อทุกอย่างพร้อม การบันทึกไฟล์ทำได้ในบรรทัดเดียว เลือกพาธใดก็ได้ที่คุณต้องการ; ตัวอย่างใช้พาธตัวแปรที่คุณควรแทนที่ด้วยไดเรกทอรีของคุณเอง  

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **ผลลัพธ์:** เปิดไฟล์ *.docx* ที่สร้างขึ้นใน Microsoft Word คุณจะเห็นรูปสี่เหลี่ยมที่มีเงาสีดำ, กว้าง 200 pt และสูง 100 pt, อยู่ในแนว inline กับย่อหน้าแรก

---

## ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิด **ShadowShape.docx**, เอกสารจะแสดง:

- ย่อหน้าเดียวที่มีรูปสี่เหลี่ยม
- รูปมีเงาสีดำอ่อนที่เลื่อนออก 5 pt
- ขนาดรูปตรงกับค่าที่ตั้งในขั้นตอน 2
- ไม่มีข้อความเพิ่มเติมปรากฏ เว้นแต่คุณจะเพิ่มเอง

หากรูปไม่แสดง ตรวจสอบว่าคุณอ้างอิงเวอร์ชัน Aspose.Words ที่ถูกต้องและใบอนุญาต (หรือรุ่นทดลอง) ยังใช้งานอยู่

---

## คำถามทั่วไปและรูปแบบต่าง ๆ

| คำถาม | คำตอบ |
|----------|--------|
| *ฉันสามารถเปลี่ยนสีเงาเป็นสีอื่นที่ไม่ใช่สีดำได้หรือไม่?* | แน่นอน—ตั้งค่า `rectangleShape.Shadow.Color = Color.Blue;` หรือ `System.Drawing.Color` ใดก็ได้ |
| *ถ้าต้องการรูปสี่เหลี่ยมขนาดใหญ่ขึ้นล่ะ?* | ปรับค่า `Width` และ `Height` ตามต้องการ จำไว้ว่าเป็นหน่วยจุด; 72 pt = 1 in |
| *สามารถวางรูปที่ตำแหน่งคงที่ได้หรือไม่?* | ทำได้—ใช้ `WrapType = WrapType.Absolute` แล้วตั้งค่า `Top`/`Left` |
| *ทำงานกับ .NET Core ได้หรือไม่?* | ทำได้ Aspose.Words รองรับหลายแพลตฟอร์ม; เพียงติดตั้งแพคเกจ NuGet สำหรับ .NET Standard |
| *ฉันสามารถใส่ข้อความภายในรูปสี่เหลี่ยมได้หรือไม่?* | ไม่โดยตรง; คุณต้องใช้รูป `TextBox` แทนรูปสี่เหลี่ยมธรรมดา |

---

## ตัวอย่างทำงานเต็ม (พร้อมคัดลอก‑วาง)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

เรียกใช้โปรแกรม, ไปที่ `C:\Temp\ShadowShape.docx`, แล้วคุณจะเห็นรูปสี่เหลี่ยมที่มีเงาตามที่อธิบายไว้

---

## สรุป

คุณได้เรียนรู้วิธี **สร้างรูปสี่เหลี่ยม** ในไฟล์ Word ด้วย Aspose.Words, วิธี **ตั้งขนาดรูป**, **เพิ่มเงา**, และสุดท้าย **บันทึกไฟล์ Word** พร้อมการเปลี่ยนแปลงทั้งหมด กระบวนการทั้งหมด—from **วิธีสร้างเอกสาร** ถึงการบันทึกผลลัพธ์—ใช้เพียงไม่กี่บรรทัดของ C# และสามารถขยายต่อเพื่อจัดวางที่ซับซ้อนยิ่งขึ้นได้

พร้อมรับความท้าทายต่อไปหรือยัง? ลองเปลี่ยนรูปสี่เหลี่ยมเป็นรูปมุมโค้ง, ทดลองสีเงาต่าง ๆ, หรือฝังรูปภายในเซลล์ตาราง การปรับแต่งแต่ละครั้งจะช่วยย้ำแนวคิดหลักที่เราได้อธิบายไว้

หากคุณพบว่าคู่มือเล่มนี้เป็นประโยชน์ อย่าลืมแชร์, แสดงความคิดเห็นพร้อมตัวอย่างของคุณ, หรือสำรวจบทเรียนอื่น ๆ ของเราที่เกี่ยวกับการอัตโนมัติ Word เช่น การแทรกรูปภาพหรือการสร้างตารางด้วย Aspose.Words. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}