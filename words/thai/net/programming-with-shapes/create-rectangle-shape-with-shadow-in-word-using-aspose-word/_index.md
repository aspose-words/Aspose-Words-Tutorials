---
category: general
date: 2026-03-06
description: สร้างรูปสี่เหลี่ยมใน Word และเพิ่มเงาให้รูปด้วย Aspose.Words. เรียนรู้วิธีแทรกรูปสี่เหลี่ยมใน
  Word และวิธีเพิ่มเงาให้รูปใน C#
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: th
og_description: สร้างรูปสี่เหลี่ยมผืนผ้าใน Word และเพิ่มเงาให้รูปด้วย Aspose.Words
  คู่มือแบบขั้นตอนที่แสดงวิธีแทรกรูปสี่เหลี่ยมผืนผ้าใน Word และวิธีเพิ่มเงาให้รูป.
og_title: สร้างรูปสี่เหลี่ยมพร้อมเงาใน Word ด้วย Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: สร้างรูปสี่เหลี่ยมพร้อมเงาใน Word ด้วย Aspose.Words
url: /th/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมผืนผ้าพร้อมเงาใน Word ด้วย Aspose.Words

เคยต้องการ **สร้างรูปสี่เหลี่ยมผืนผ้า** ในเอกสาร Word แต่ไม่แน่ใจว่าจะทำให้ดูเป็นมืออาชีพได้อย่างไรหรือไม่? คุณไม่ได้อยู่คนเดียว—นักพัฒนาส่วนใหญ่มักเจออุปสรรคเดียวกันเมื่อต้องการเพิ่มความสวยงามให้กับเอกสารอัตโนมัติ ข่าวดีคือ? ด้วย Aspose.Words for .NET คุณสามารถ **สร้างรูปสี่เหลี่ยมผืนผ้า** และ **เพิ่มเงาให้รูป** ได้เพียงไม่กี่บรรทัดของ C# เท่านั้น

ในบทแนะนำนี้เราจะอธิบาย **วิธีแทรกรูปสี่เหลี่ยมใน Word** อย่างละเอียด จากนั้นแสดง **วิธีเพิ่มเงาให้รูป** เพื่อให้รูปดูโดดเด่นออกจากหน้า เมื่อทำตามเสร็จแล้วคุณจะได้ไฟล์ `Shadow.docx` ที่พร้อมบันทึก สามารถเปิดใน Word แล้วเห็นสี่เหลี่ยมสีเทาพร้อมเงาตกเบา ๆ ไม่ต้องใช้ไฟล์รูปเพิ่มเติม ไม่ต้องปรับมือ—แค่โค้ดเท่านั้น

## สิ่งที่คุณจะได้เรียนรู้

- คำสั่ง C# ที่จำเป็นสำหรับ **สร้างรูปสี่เหลี่ยมผืนผ้า** ด้วย Aspose.Words  
- วิธีเปิดใช้งานและกำหนดค่าเงาโดยใช้วัตถุ `Shadow`  
- ทำไมแต่ละคุณสมบัติจึงสำคัญ (เช่น `Transparency`, `Blur`, `Angle`)  
- จุดบกพร่องที่พบบ่อย (หน่วย, ความเข้ากันของเวอร์ชัน) และวิธีแก้อย่างรวดเร็ว  
- โปรแกรมเต็มรูปแบบพร้อมคัดลอก‑วางที่คุณสามารถรันได้ทันที

### ข้อกำหนดเบื้องต้น

- .NET 6+ (หรือ .NET Framework 4.7+)  
- Aspose.Words for .NET 23.10 หรือใหม่กว่า (แพ็กเกจ NuGet คือ `Aspose.Words`)  
- ความเข้าใจพื้นฐานเกี่ยวกับ C# และ Visual Studio (หรือ IDE ที่คุณชอบ)

หากคุณมีทั้งหมดนี้แล้ว มาเริ่มกันเลย

---

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า namespace

แรกสุด สร้างแอปคอนโซลใหม่ (หรือใช้แอปที่มีอยู่แล้ว) แล้วเพิ่มแพ็กเกจ Aspose.Words ผ่าน NuGet:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

จากนั้นนำเข้า namespace ที่จำเป็นในไฟล์ `Program.cs` ของคุณ:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **เคล็ดลับ:** หากคุณใช้ .NET 6+ สามารถเปิดใช้ `global using` เพื่อไม่ต้องเขียนบรรทัดเหล่านี้ซ้ำในทุกไฟล์

---

## ขั้นตอนที่ 2: **สร้างรูปสี่เหลี่ยมผืนผ้า** ในเอกสาร Word ว่าง

เราจะเริ่มด้วยอ็อบเจกต์ `Document` ใหม่และ `DocumentBuilder` เพื่อจัดการเอกสาร เมธอด `InsertShape` ของ builder คือจุดที่ทำให้เกิด “เวทมนตร์”

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

ทำไมต้องใช้ขนาด 200 × 100 จุด? ใน Word หนึ่งจุดเท่ากับ 1/72 นิ้ว ดังนั้นสี่เหลี่ยมจะมีขนาดประมาณ 2.8 × 1.4 นิ้ว—พอเห็นชัดเจนแต่ไม่ใหญ่เกินไป คุณสามารถเปลี่ยนตัวเลขเหล่านี้ให้เหมาะกับการออกแบบของคุณได้ เพียงจำไว้ว่าเป็น **จุด** ไม่ใช่พิกเซล

---

## ขั้นตอนที่ 3: **เพิ่มเงาให้รูป** – กำหนดลักษณะการแสดงผล

ตอนนี้เรามีสี่เหลี่ยมแล้ว ให้เพิ่มเงาเทาอ่อน ๆ วัตถุ `Shadow` อยู่บน `Shape` และมีคุณสมบัติต่าง ๆ ที่สะดวกต่อการตั้งค่า

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### รายละเอียดของแต่ละคุณสมบัติ

| Property | Effect | Typical values |
|----------|--------|----------------|
| **Enabled** | เปิดหรือปิดเงา | `true` หรือ `false` |
| **Color** | สีพื้นฐานของเงา | ใด ๆ ที่เป็น `System.Drawing.Color` |
| **Transparency** | ความทึบ (0 = ทึบเต็ม, 1 = โปร่งใส) | 0.0 – 1.0 |
| **Blur** | ความนุ่มของขอบ | 0 – 10 (ค่าสูง = นุ่มกว่า) |
| **Distance** | ระยะห่างระหว่างรูปกับเงา | 0 – 20 จุด |
| **Angle** | ทิศทางของแสงที่ทำให้เกิดเงา | 0 – 360 องศา |
| **Size** | ขนาดของเงาเทียบกับรูป | 0 – 200 % |

> **ทำไมต้องตั้งค่าเหล่านี้?**  
> การปรับเงาให้เหมาะสมช่วยให้คุณสอดคล้องกับแนวทางแบรนด์ (เช่น เงาโปร่งใส 20 % เพื่อความเป็นมืออาชีพ) โดยไม่ต้องใช้โปรแกรมแก้รูปภายนอก

---

## ขั้นตอนที่ 4: บันทึกเอกสารและตรวจสอบผลลัพธ์

สุดท้าย ให้เขียนไฟล์ลงดิสก์ คุณสามารถเลือกโฟลเดอร์ใดก็ได้—เพียงเปลี่ยน `YOUR_DIRECTORY` ให้เป็นพาธจริงของคุณ

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

เปิด `Shadow.docx` ด้วย Microsoft Word แล้วคุณจะเห็นสี่เหลี่ยมสีเทาพร้อมเงาตกอ่อน ๆ ที่เอียง 45° เงานี้ทำให้รูปดู “ลอย” จากหน้า—เหมาะกับรายงานหรือใบแจ้งหนี้ที่ต้องการความเป็นมืออาชีพ

---

## ตัวอย่างโค้ดเต็มที่ทำงานได้

ด้านล่างเป็นโปรแกรมทั้งหมดที่คุณสามารถคัดลอก‑วางลงใน `Program.cs` ได้โดยตรง ไม่มีส่วนใดหายไป; สามารถคอมไพล์และรันได้ทันที

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

- **ไฟล์:** `Shadow.docx` จะถูกสร้างในโฟลเดอร์การทำงานของโปรเจกต์  
- **ภาพ:** สี่เหลี่ยมหนึ่งอันอยู่กึ่งกลางหน้า, เติมสีขาวตามค่าเริ่มต้น, และเงาสีเทาเอียง 4 จุดไปด้านล่าง‑ขวา, เบลอเล็กน้อยเพื่อให้ดูเป็นธรรมชาติ

---

## คำถามที่พบบ่อย & กรณีพิเศษ

### 1. ต้องการใช้หน่วยอื่น (เช่น เซนติเมตร) จะทำอย่างไร?

Aspose.Words ใช้หน่วยเป็นจุด แต่คุณสามารถแปลงเซนติเมตรเป็นจุดได้ด้วยสูตรง่าย ๆ:  
`points = centimeters * 28.3465`

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. ทำงานกับเวอร์ชัน Aspose.Words เก่ากว่าได้หรือไม่?

API `Shadow` ถูกเพิ่มตั้งแต่เวอร์ชัน 14.0 หากคุณใช้เวอร์ชันเก่ากว่า จะต้องอัปเกรดผ่าน NuGet ส่วนโค้ดส่วนสร้างรูปยังคงเสถียรมานานหลายปี จึงไม่มีการเปลี่ยนแปลงที่ทำให้โค้ดเสีย

### 3. สามารถเพิ่มเงาให้รูปอื่น ๆ (เช่น วงกลม) ได้หรือไม่?

ได้เลย—ทุกอ็อบเจกต์ `Shape` มีคุณสมบัติ `Shadow` เพียงเปลี่ยน `ShapeType.Rectangle` เป็น `ShapeType.Ellipse` หรือ `ShapeType.Cloud` แล้วใช้การตั้งค่าเงาเดียวกัน

### 4. ต้องการเงาสี (เช่น น้ำเงินตามแบรนด์) จะทำอย่างไร?

เปลี่ยน `Color.Gray` เป็นสีที่ต้องการได้เลย:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

อย่าลืมปรับ `Transparency` เพื่อไม่ให้สีเงาโดดเด่นเกินไป

---

## 🎨 สรุปภาพรวม

![สร้างรูปสี่เหลี่ยมผืนผ้าพร้อมเงาใน Word ด้วย Aspose.Words](image-placeholder.png "สร้างรูปสี่เหลี่ยมผืนผ้าพร้อมเงาใน Word ด้วย Aspose.Words")

*ข้อความแทนภาพ: สร้างรูปสี่เหลี่ยมผืนผ้าพร้อมเงาใน Word ด้วย Aspose.Words*

ภาพตัวอย่าง (placeholder) แสดงเอกสารสุดท้าย—เพียงสี่เหลี่ยมและเงาสีเทาอ่อน

---

## สรุป

ตอนนี้คุณรู้วิธี **สร้างรูปสี่เหลี่ยมผืนผ้า** ในไฟล์ Word, **เพิ่มเงาให้รูป**, และปรับแต่งลักษณะภาพทั้งหมดด้วย Aspose.Words for .NET โปรแกรมสั้น ๆ ที่เราเขียนครอบคลุมขั้นตอนทั้งหมด—from

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}