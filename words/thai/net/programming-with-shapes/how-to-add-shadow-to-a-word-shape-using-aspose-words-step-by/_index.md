---
category: general
date: 2026-01-06
description: วิธีเพิ่มเงาให้กับรูปทรงใน Word ด้วย Aspose.Words C# — เรียนรู้การใช้เงากับรูปทรง
  ตั้งค่ามุมเงา และปรับระยะห่างของเงาอย่างรวดเร็ว
draft: false
keywords:
- how to add shadow
- apply shadow to shape
- add shape shadow
- set shadow angle
- adjust shadow distance
language: th
og_description: วิธีเพิ่มเงาให้กับรูปร่างใน Word ด้วย C#. บทแนะนำนี้แสดงวิธีการใช้เงากับรูปร่าง
  ตั้งมุมเงา และปรับระยะห่างของเงาด้วย Aspose.Words.
og_title: วิธีเพิ่มเงาให้กับรูปร่างใน Word – คู่มือ Aspose.Words ฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Processing
- Graphics
title: วิธีเพิ่มเงาให้กับรูปร่างใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด
url: /th/net/programming-with-shapes/how-to-add-shadow-to-a-word-shape-using-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มเงาให้กับรูปร่างใน Word ด้วย Aspose.Words

เคยสงสัย **วิธีเพิ่มเงา** ให้กับรูปร่างในเอกสาร Word โดยไม่ต้องเปิด Word เองหรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนามักต้องการการตกแต่งภาพที่ดูดีสำหรับรายงาน ใบแจ้งหนี้ หรือแผ่นพับการตลาด แต่ไม่ต้องการเปิด UI ทุกครั้ง  

ในบทแนะนำนี้ เราจะอธิบายขั้นตอน **วิธีเพิ่มเงา** ให้กับรูปร่างโดยโปรแกรม, อธิบายว่าทำไมแต่ละคุณสมบัติจึงสำคัญ, และแสดงวิธี *apply shadow to shape*, *set shadow angle*, และ *adjust shadow distance* ด้วยเพียงไม่กี่บรรทัดของโค้ด C#  

> **สิ่งที่คุณจะได้:** ตัวอย่างที่สามารถรันได้เต็มรูปแบบที่โหลดไฟล์ DOCX, เพิ่มเงาตกแบบสมจริงให้กับรูปร่างแรก, และบันทึกผลลัพธ์เป็นไฟล์ใหม่ ไม่ต้องใช้เครื่องมือภายนอก เพียงแค่ Aspose.Words สำหรับ .NET.

## ข้อกำหนดเบื้องต้น

- .NET 6.0 (หรือเวอร์ชัน .NET Framework ล่าสุดใดก็ได้)  
- Aspose.Words for .NET ≥ 23.10 (รุ่นเสถียรล่าสุด ณ เวลาที่เขียน)  
- เอกสาร Word (`shapes.docx`) ที่มีอย่างน้อยหนึ่งรูปร่างวาดอยู่แล้ว  
- Visual Studio, Rider, หรือ IDE C# ที่คุณชอบ  

หากคุณยังไม่มีไลบรารีนี้ ให้ดาวน์โหลดจาก NuGet:

```bash
dotnet add package Aspose.Words
```

เมื่อพื้นฐานได้ถูกอธิบายแล้ว เรามาเริ่มขั้นตอนจริงกันเถอะ

## วิธีเพิ่มเงาให้กับรูปร่าง – ภาพรวม

หัวใจของ **วิธีเพิ่มเงา** อยู่ในอ็อบเจ็กต์ `ShadowFormat` ที่ทุก `Shape` มีให้คิดว่า `ShadowFormat` เป็น “สไตล์ชีต” สำหรับเงา—คุณสมบัติต่าง ๆ กำหนดการมองเห็น, สี, ความเบลอ, การเลื่อน, และทิศทาง.  

ต่อไปนี้เป็นแผนภาพระดับสูง:

1. โหลดเอกสารต้นฉบับ.  
2. ดึง `Shape` เป้าหมาย.  
3. รับ `ShadowFormat` ของมัน.  
4. ตั้งค่าคุณสมบัติดูของเงา (รวมถึง *set shadow angle* และ *adjust shadow distance*).  
5. บันทึกเอกสารที่แก้ไขแล้ว.  

แต่ละขั้นตอนจะแยกเป็นส่วนของตนเอง เพื่อให้คุณเลือกใช้ตามต้องการ  

<img src="shadow-example.png" alt="ตัวอย่างการเพิ่มเงาในเอกสาร Word">

## ขั้นตอน 1 – โหลดเอกสาร Word

แรกสุด เราต้องการอินสแตนซ์ `Document` ที่ชี้ไปยังไฟล์ต้นฉบับของเรา การดำเนินการนี้มีต้นทุนต่ำ; Aspose.Words จะสตรีมไฟล์และสร้าง DOM ในหน่วยความจำ  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Load the DOCX that already contains a shape.
Document doc = new Document("YOUR_DIRECTORY/shapes.docx");
```

**ทำไมจึงสำคัญ:** การโหลดเอกสารทำให้เราเข้าถึงโครงสร้างโหนด ที่ซึ่งรูปร่างอยู่ในรูปแบบ `NodeType.Shape`. หากข้ามขั้นตอนนี้ คุณจะไม่มีอะไรให้เพิ่มเงา  

## ขั้นตอน 2 – ดึงรูปร่างแรก (หรือรูปร่างใดก็ได้ที่คุณต้องการ)

คุณสามารถดึงรูปร่างโดยดัชนี, ชื่อ, หรือเงื่อนไขกำหนดเอง สำหรับความง่าย เราจะดึงรูปร่างแรกในเอกสาร วิธี `GetChild` จะเดินทางต้นไม้แบบลึก‑แรก, คืนค่าโหนดที่คุณร้องขอ  

```csharp
// Grab the first shape – change the index if you need a different one.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (shape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

**เคล็ดลับ:** หากเอกสารของคุณมีหลายรูปร่าง ให้วนลูป `doc.GetChildNodes(NodeType.Shape, true)` และเพิ่มเงาให้แต่ละอัน นี่เป็นการใช้งานทั่วไปเมื่อคุณต้องการ *add shape shadow* ให้กับสไลด์หรือหน้าทั้งหมด  

## ขั้นตอน 3 – เข้าถึงและกำหนดค่ากล่องรูปแบบเงา

ตอนนี้เรามาถึงหัวใจของ **วิธีเพิ่มเงา**: `ShadowFormat`. อ็อบเจ็กต์นี้เก็บการปรับแต่งทั้งหมดที่คุณทำได้กับลักษณะของเงา  

```csharp
// Step 3: Get the shadow format for the shape.
ShadowFormat shadow = shape.ShadowFormat;

// Make the shadow visible.
shadow.Visible = true;

// Choose a dark gray color for a subtle effect.
shadow.Color = Color.DarkGray;

// Set transparency to 30 % (0.0 = opaque, 1.0 = fully transparent).
shadow.Transparency = 0.3;

// Blur radius – larger values give a softer edge.
shadow.Size = 5;
```

### ตั้งค่ามุมเงาและปรับระยะเงา

คีย์เวิร์ด *set shadow angle* และ *adjust shadow distance* จะใช้ที่นี่ มุมกำหนดทิศทางของแสงที่ดูเหมือนมาจาก, ส่วนระยะกำหนดว่าระยะการเลื่อนของเงาจากรูปร่างเท่าไหร่  

```csharp
// Angle in degrees – 45° points down‑right.
shadow.Angle = 45;

// Distance in points – how far the shadow is shifted.
shadow.Distance = 3;
```

**ทำไมต้องใช้ตัวเลขเหล่านี้?** มุม 45° พร้อมระยะ 3 pts จำลองแหล่งแสงจากด้านบน‑ซ้าย ซึ่งดูเป็นธรรมชาติสำหรับการจัดหน้าเอกสารส่วนใหญ่ คุณสามารถทดลองได้: 0° ทำให้เงาอยู่ตรงใต้, 180° ทำให้เงาอยู่ด้านบน  

## ขั้นตอน 4 – บันทึกเอกสารและตรวจสอบผลลัพธ์

เมื่อตั้งค่าคุณสมบัติเงาแล้ว คุณเพียงแค่เขียนเอกสารกลับไปยังดิสก์ Aspose.Words จะจัดการ OOXML ระดับล่างทั้งหมดให้คุณ  

```csharp
// Save the modified document with the new shadow effect.
doc.Save("YOUR_DIRECTORY/shadowed.docx");
```

เปิด `shadowed.docx` ด้วย Microsoft Word หรือโปรแกรมดูที่รองรับ—คุณควรเห็นรูปร่างแรกตอนนี้มีเงาตกสีเทาเข้มอ่อนที่มุม 45°  

### รายการตรวจสอบอย่างรวดเร็ว

- **Visibility:** เงาถูกเรนเดอร์จริงหรือไม่? (`shadow.Visible` ต้องเป็น `true`.)  
- **Color & Transparency:** เงาดูเป็นสีเทานุ่มนวลหรือเป็นสีดำเข้ม?  
- **Angle & Distance:** เงาปรากฏการเลื่อนในทิศทางที่คุณกำหนดหรือไม่?  
- **Blur (Size):** ขอบเงานุ่มพอสำหรับการออกแบบของคุณหรือไม่?  

หากมีสิ่งใดดูแปลก ให้ปรับคุณสมบัตินั้นและบันทึกใหม่ การเปลี่ยนแปลงจะเห็นทันที  

## ความแปรผันทั่วไปและการจัดการกรณีขอบ

### การเพิ่มเงาให้หลายรูปร่าง

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.Visible = true;
    sf.Color = Color.Black;
    sf.Transparency = 0.2;
    sf.Size = 4;
    sf.Angle = 30;
    sf.Distance = 2;
}
doc.Save("YOUR_DIRECTORY/all_shapes_shadowed.docx");
```

### การรีเซ็ตเงา (ลบออก)

หากคุณต้องการ *add shape shadow* อย่างมีเงื่อนไข คุณสามารถปิดมันได้ภายหลัง:  

```csharp
shape.ShadowFormat.Visible = false;
```

### หมายเหตุความเข้ากันได้

- Aspose.Words 23.10+ รองรับคุณสมบัติเงาเต็มรูปแบบสำหรับ DOCX, DOC, และแม้กระทั่งการส่งออกเป็น PDF.  
- เอฟเฟกต์เงาจะคงอยู่เมื่อแปลงเป็น PDF ผ่าน `doc.Save("out.pdf")`.  
- เวอร์ชัน Word เก่า (< 2007) ไม่เก็บเงาใน OOXML ดังนั้นเอฟเฟกต์จะหายไปหากบันทึกเป็น `.doc`. ควรใช้ `.docx` เพื่อผลลัพธ์ที่ดีที่สุด.  

## เคล็ดลับ – ใช้วิธีช่วยเหลือเพื่อการนำกลับมาใช้ใหม่

หากคุณพบว่าตัวเองใช้การตั้งค่าเงาเดียวกันในหลายโครงการ ให้ห่อหุ้มตรรกะในเมธอดยูทิลิตี้:  

```csharp
public static void ApplyStandardShadow(Shape target, Color? color = null,
                                        double transparency = 0.3,
                                        double size = 5,
                                        double angle = 45,
                                        double distance = 3)
{
    ShadowFormat sf = target.ShadowFormat;
    sf.Visible = true;
    sf.Color = color ?? Color.DarkGray;
    sf.Transparency = transparency;
    sf.Size = size;
    sf.Angle = angle;
    sf.Distance = distance;
}
```

ตอนนี้บรรทัดเดียว `ApplyStandardShadow(shape);` จะทำงาน *apply shadow to shape* ทั้งหมด  

## สรุป

เราได้อธิบาย **วิธีเพิ่มเงา** ให้กับรูปร่างใน Word ด้วย Aspose.Words ตั้งแต่ต้นจนจบ โดยการโหลดเอกสาร, ดึงรูปร่าง, กำหนดค่า `ShadowFormat` (รวมถึง *set shadow angle* และ *adjust shadow distance*), และบันทึกไฟล์, คุณสามารถให้แผนภาพใด ๆ มีเงาตกระดับมืออาชีพโดยไม่ต้องเปิด Word.  

คุณสามารถทดลองกับแนวคิดรองได้—*apply shadow to shape* ด้วยสีต่าง ๆ, *add shape shadow* ให้กับคอลเลกชันทั้งหมด, หรือปรับ *set shadow angle* เพื่อเอฟเฟ็กต์แสงที่ดรามาติก ขั้นตอนต่อไปที่สมเหตุสมผลคือการผสานเงาเหล่านี้กับคุณลักษณะการจัดรูปแบบอื่น ๆ เช่น เส้นขอบ, การสะท้อน, หรือแม้กระทั่งการหมุน 3‑D.  

มีคำถามเกี่ยวกับกรณีขอบ, ประสิทธิภาพ, หรือการแปลงผลลัพธ์เป็น PDF? แสดงความคิดเห็นด้านล่าง แล้วขอให้เขียนโค้ดอย่างสนุกสนาน!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}