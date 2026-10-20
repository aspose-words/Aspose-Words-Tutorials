---
category: general
date: 2026-04-28
description: วิธีตั้งเงาบนรูปร่างอย่างรวดเร็ว เรียนรู้วิธีเพิ่มเงารูปร่าง ตั้งค่าสีเงา
  และปรับแต่งเงารูปร่างด้วย Aspose.Words for .NET.
draft: false
keywords:
- how to set shadow
- add shape shadow
- set shadow color
- how to add shadow
- customize shape shadow
language: th
og_description: วิธีตั้งเงาบนรูปร่างใน C# ด้วย Aspose.Words คู่มือขั้นตอนโดยละเอียดที่ครอบคลุมการเพิ่มเงารูปร่าง
  การตั้งค่าสีเงา และการปรับแต่งเงารูปร่าง
og_title: วิธีตั้งเงาบนรูปทรงใน C# – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Automation
title: วิธีตั้งเงาบนรูปทรงใน C# – เพิ่มเงารูปทรงได้ง่าย
url: /th/java/images-shapes/how-to-set-shadow-on-a-shape-in-c-add-shape-shadow-easily/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งเงาบนรูปร่างใน C# – เพิ่มเงารูปร่างได้อย่างง่ายดาย

เคยสงสัย **วิธีตั้งเงา** บนรูปร่างโดยไม่ต้องค้นหาเอกสาร API ที่ไม่มีที่สิ้นสุดหรือไม่? คุณไม่ได้อยู่คนเดียว นักพัฒนาหลายคนเจออุปสรรคเมื่อพวกเขาต้องการเงาตกแบบละเอียดเพื่อทำให้แผนภาพโดดเด่น แต่ไม่สามารถหาตัวอย่างที่ชัดเจนซึ่งแสดงทั้ง “อะไร” และ “ทำไม”  

ในบทแนะนำนี้เราจะเดินผ่านการเพิ่มเงารูปร่าง, การเปลี่ยนสีเงา, และการปรับค่าความเบลอ, การเลื่อนตำแหน่ง, และความโปร่งใส – ทั้งหมดโดยใช้ Aspose.Words for .NET. เมื่อเสร็จคุณจะได้โค้ดสั้นที่พร้อมรันและสามารถใส่ลงในโปรเจกต์ C# ใดก็ได้ พร้อมกับเคล็ดลับหลายอย่างสำหรับการปรับแต่งเงารูปร่างในสถานการณ์ที่ซับซ้อนยิ่งขึ้น

> **หมายเหตุ:** โค้ดทำงานกับ Aspose.Words 22.9 หรือใหม่กว่าและต้องการ .NET 6+ (หรือ .NET Framework 4.7.2+).  

![รูปร่างพร้อมเงาที่กำหนดเอง](shape-shadow.png "รูปร่างพร้อมเงาที่กำหนดเอง")

## สิ่งที่คุณจะได้เรียนรู้

- **เพิ่มเงารูปร่าง** ผ่านโปรแกรมให้กับรูปร่างแรกในเอกสาร Word  
- **ตั้งค่าสีเงา** ให้เป็น `System.Drawing.Color` ใดก็ได้  
- **ปรับแต่งเงารูปร่าง** โดยการเปลี่ยนค่ารัศมีเบลอ, การเลื่อนตำแหน่ง, และความโปร่งใส  
- วิธีจัดการกับหลายรูปร่างและรีเซ็ตการตั้งค่าเงาหากจำเป็น  

ไม่มีเครื่องมือภายนอก, ไม่มีแมโคร Visual Basic—เพียง C# แท้ๆ

---

## ข้อกำหนดเบื้องต้น

| ข้อกำหนด | ทำไมจึงสำคัญ |
|-------------|----------------|
| **Aspose.Words for .NET** (แพคเกจ NuGet `Aspose.Words`) | ให้คลาส `Document`, `Shape`, และ `ShadowFormat` ที่ใช้ในตัวอย่าง |
| **.NET 6 SDK** (หรือ .NET Framework 4.7.2) | รับประกันความเข้ากันได้กับ API ล่าสุด |
| **ไฟล์ .docx** ที่มีอย่างน้อยหนึ่งรูปร่าง (เช่น สี่เหลี่ยมผืนผ้าหรือรูปภาพ) | บทแนะนำนี้จัดการกับ *รูปร่างแรก*; คุณสามารถสร้างรูปร่างใน Word หากยังไม่มี |

ติดตั้งไลบรารีด้วย:

```bash
dotnet add package Aspose.Words
```

---

## ขั้นตอน‑โดย‑ขั้นตอน: วิธีตั้งเงาบนรูปร่าง

### 1. โหลดเอกสาร Word

เราจะเริ่มโดยเปิดไฟล์ `.docx`. ตัวสร้าง `Document` จะอ่านไฟล์เข้าสู่หน่วยความจำ ทำให้เรามีการเข้าถึงโหนดทั้งหมดได้เต็มที่

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **ทำไม?** การโหลดเอกสารเป็นพื้นฐาน—หากไม่มีคุณจะไม่สามารถเดินทางผ่านโครงสร้างรูปร่างได้

### 2. ดึงรูปร่างแรก (หรือรูปร่างใดที่คุณต้องการ)

Aspose.Words เก็บรูปร่างเป็นโหนดประเภท `NodeType.SHAPE`. เมธอด `GetChild` ช่วยให้เราดึงรูปร่างที่ *n‑th*; ที่นี่เราดึงดัชนี 0 คือรูปร่างแรก

```csharp
// Grab the first shape in the document (depth‑first search)
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

> **เคล็ดลับ:** หากต้องการ **เพิ่มเงารูปร่าง** ให้กับรูปร่างเฉพาะ, ให้เปลี่ยนดัชนีเป็นค่าที่เหมาะสมหรือวนลูปผ่าน `doc.GetChildNodes(NodeType.Shape, true)`

### 3. เข้าถึงออบเจ็กต์การจัดรูปแบบเงา

ทุก `Shape` มีคุณสมบัติ `ShadowFormat` ที่เปิดเผยการตั้งค่าเกี่ยวกับเงาทั้งหมด

```csharp
ShadowFormat shadow = firstShape.ShadowFormat;
```

ตอนนี้เราสามารถเริ่มปรับแต่งเงาได้แล้ว

### 4. ตั้งค่ารัศมีเบลอ – ทำให้ขอบนุ่มขึ้น

รัศมีเบลอที่ใหญ่ขึ้นทำให้เงาดูกระจายมากขึ้น ค่าเป็นหน่วยจุด (1 pt ≈ 1/72 inch)

```csharp
shadow.BlurRadius = 5.0; // 5 pt blur – looks nicely soft
```

> **ปรับเมื่อใด?** หากรูปร่างของคุณเล็ก, เบลอ 2–3 pt อาจพอ; สำหรับแบนเนอร์ขนาดใหญ่ให้เพิ่มเป็น 8–10 pt

### 5. กำหนดการเลื่อนแนวนอนและแนวตั้ง

การเลื่อนกำหนดระยะที่เงาจะห่างจากรูปร่าง ค่าเป็นบวกจะเลื่อนขวา/ลง; ค่าเป็นลบจะเลื่อนซ้าย/ขึ้น

```csharp
shadow.DistanceX = 3.0; // 3 pt to the right
shadow.DistanceY = 3.0; // 3 pt downwards
```

### 6. ปรับความโปร่งใส (ความทึบ)

`Transparency` มีค่าตั้งแต่ `0.0` (ทึบเต็ม) ถึง `1.0` (โปร่งใสเต็ม). ค่าใกล้ `0.3` ให้ลุคเงาแบบกึ่ง‑โปร่งใสที่ละเอียดอ่อน

```csharp
shadow.Transparency = 0.3; // 30 % transparent
```

### 7. เลือกสีเงา – **ตั้งค่าสีเงา** ให้เป็น `System.Drawing.Color` ใดก็ได้

คุณสามารถเลือกสีที่กำหนดไว้ล่วงหน้าหรือสร้างสีกำหนดเองด้วยค่า RGB

```csharp
shadow.Color = Color.FromArgb(0, 120, 215); // A calm blue shade
```

หากต้องการเงาสีดำคลาสสิก, เพียงใช้ `Color.Black`

### 8. บันทึกเอกสารที่แก้ไขแล้ว

สุดท้ายให้บันทึกการเปลี่ยนแปลง คุณสามารถเขียนทับไฟล์เดิมหรือบันทึกไปยังตำแหน่งใหม่ได้

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
```

---

## ตัวอย่างทำงานเต็มรูปแบบ (รวมทุกขั้นตอนในบล็อกเดียว)

คัดลอก‑วางโค้ดต่อไปนี้ลงในเมธอด `Main` ของแอปคอนโซล. โค้ดคอมไพล์ได้ทันที หากติดตั้งแพคเกจ NuGet แล้ว

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape (add shape shadow)
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3. Get the shadow formatting object
        ShadowFormat shadow = shape.ShadowFormat;

        // 4. Set blur radius
        shadow.BlurRadius = 5.0;

        // 5. Define offsets
        shadow.DistanceX = 3.0;
        shadow.DistanceY = 3.0;

        // 6. Adjust transparency (0 = opaque, 1 = fully transparent)
        shadow.Transparency = 0.3;

        // 7. Set shadow color (set shadow color)
        shadow.Color = Color.GetBlue(); // or any custom color

        // 8. Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิด `output_with_shadow.docx` ใน Word; รูปร่างแรกจะแสดงเงาสีฟ้าอ่อน, เลื่อน 3 pt, มีเบลออ่อนและความโปร่งใส 30 %

---

## ความแปรผันทั่วไป & กรณีขอบ

### เพิ่มเงาให้กับ *ทุก* รูปร่าง

หากเอกสารของคุณมีหลายแผนภาพ, คุณอาจต้องการวนลูปผ่านทุกรูปร่าง:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.BlurRadius = 4.0;
    sf.DistanceX = 2.0;
    sf.DistanceY = 2.0;
    sf.Transparency = 0.25;
    sf.Color = Color.Gray;
}
```

### รีเซ็ตเงา

บางครั้งรูปร่างอาจมีเงาที่ต้องการลบออก. ตั้งค่า `ShadowFormat.Visible` เป็น `false`:

```csharp
shape.ShadowFormat.Visible = false;
```

### ใช้สีกำหนดเองพร้อมอัลฟา (กึ่ง‑โปร่งใส)

```csharp
shadow.Color = Color.FromArgb(128, 255, 0, 0); // 50 % transparent red
```

### หมายเหตุเรื่องความเข้ากันได้

API `ShadowFormat` มีความเสถียรข้ามเวอร์ชัน Aspose.Words, แต่รุ่นเก่า (< 19.1) ใช้ฟิลด์ `ShadowFormat` ที่มีชื่อแตกต่างกันเล็กน้อย. ควรใช้แพคเกจ NuGet เวอร์ชันล่าสุดเพื่อผลลัพธ์ที่ดีที่สุด

---

## เคล็ดลับระดับมืออาชีพสำหรับเงาที่ดูดี

- **สมดุลระหว่างเบลอและการเลื่อน:** เบลอหนักกับการเลื่อนเล็กน้อยอาจดู “แสงสว่าง” มากกว่าเงาตกจริงๆ. ทดลองปรับ `BlurRadius` × `DistanceX/Y`  
- **สอดคล้องกับธีมเอกสาร:** หากไฟล์ Word ใช้ธีมมืด, เงาอ่อน (`Color.White`) สามารถสร้างเอฟเฟกต์ยกขึ้นอย่างละเอียดอ่อน  
- **ประสิทธิภาพ:** การเปลี่ยนเงาบนร้อยรูปอาจเพิ่มเวลาเพียงไม่กี่มิลลิวินาทีต่อรูป. ควรทำเป็นชุดหากต้องประมวลผลรายงานขนาดใหญ่  
- **การทดสอบ:** เปิดไฟล์ `.docx` ที่ได้ในทั้ง Word Desktop และ Word Online เพื่อให้แน่ใจว่าเงาแสดงผลสอดคล้องกัน

---

## สรุป

เราได้ครอบคลุม **วิธีตั้งเงา** บนรูปร่างด้วย C# แล้ว. ด้วยแปดขั้นตอนข้างต้นคุณสามารถ **เพิ่มเงารูปร่าง**, **ตั้งค่าสีเงา**, และ **ปรับแต่งเงารูปร่าง** ให้ตรงกับสไตล์การออกแบบใดก็ได้ ตัวอย่างเป็นอิสระ, ทำงานได้ทันที, และเป็นฐานที่แข็งแรงสำหรับการขยายโลจิกไปยังหลายรูปร่าง, สีไดนามิก, หรือพารามิเตอร์ที่ผู้ใช้กำหนดเอง

พร้อมรับความท้าทายต่อไปหรือยัง? ลองผสานเทคนิคนี้กับ **การหมุนรูปร่าง**, หรือสร้างรายงานที่แต่ละแผนภูมิมีเงาแบรนด์ของตนเอง. ความเป็นไปได้ไม่มีที่สิ้นสุด, และโค้ดที่คุณเพิ่งเรียนรู้เป็นจุดเริ่มต้นที่ดี

หากคุณพบว่าคู่มือเล่มนี้เป็นประโยชน์, อย่าลืมกดดาวที่รีโพสิตอรี, แสดงความคิดเห็น, หรือแบ่งปันเทคนิคการปรับเงาของคุณด้านล่าง. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}