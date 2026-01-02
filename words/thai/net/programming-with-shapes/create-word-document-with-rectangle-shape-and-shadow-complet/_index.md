---
category: general
date: 2026-01-02
description: สร้างเอกสาร Word พร้อมรูปสี่เหลี่ยม ตั้งค่าสีเติมของรูป และบันทึกไฟล์
  docx ด้วย Aspose.Words เรียนรู้วิธีสร้างสี่เหลี่ยมพร้อมเงาในไม่กี่นาที.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: th
og_description: สร้างเอกสาร Word พร้อมสี่เหลี่ยมกำหนดเอง ตั้งค่าสีเติม เพิ่มเงา และบันทึกเป็น
  DOCX. โค้ดเต็มและคำอธิบาย.
og_title: สร้างเอกสาร Word ด้วยรูปสี่เหลี่ยม – ทีละขั้นตอน
tags:
- Aspose.Words
- C#
- Document Generation
title: สร้างเอกสาร Word พร้อมรูปสี่เหลี่ยมและเงา – คู่มือฉบับสมบูรณ์
url: /th/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word พร้อมรูปสี่เหลี่ยมและเงา – คู่มือฉบับสมบูรณ์

เคยสงสัยไหมว่าจะ **สร้างเอกสาร word** ที่มีสี่เหลี่ยมสไตล์สวยงามได้อย่างไร? บางทีคุณอาจต้องการพื้นที่วางโลโก้ แบนเนอร์สี หรือเพียงแค่สัญญาณภาพในรายงาน ในบทแนะนำนี้เราจะ **เพิ่มรูปสี่เหลี่ยม**, ตั้งค่าสีเติม, ใส่เงาแบบอ่อนโยน, และสุดท้าย **บันทึกไฟล์ docx** – ทั้งหมดด้วย Aspose.Words for .NET

คุณจะได้โค้ด C# ที่พร้อมรัน, คำอธิบายแต่ละบรรทัดอย่างชัดเจน, และเคล็ดลับหลายอย่างที่คุณสามารถนำกลับไปใช้ในโปรเจกต์ของคุณเอง ไม่มีเนื้อหาเกินความจำเป็น เพียงวิธีแก้ปัญหาที่คุณสามารถคัดลอก‑วางได้

## สิ่งที่คุณต้องมี

- .NET 6 หรือใหม่กว่า (โค้ดนี้ทำงานบน .NET Framework ด้วย)  
- Visual Studio 2022 (หรือเครื่องมือแก้ไขใด ๆ ที่คุณชอบ)  
- **Aspose.Words** NuGet package (`Install-Package Aspose.Words`)  

ถ้าคุณมีทั้งหมดแล้ว เยี่ยม – มาเริ่มกันเลย

## ขั้นตอนที่ 1 – เริ่มต้นสร้างเอกสารใหม่ (How to create word document)

สิ่งแรกที่ต้องทำคือ **สร้างเอกสาร word** ในหน่วยความจำ คิดว่าเป็นการเปิดผืนผ้าใบเปล่าที่คุณจะวาดสี่เหลี่ยมลงไป

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **ทำไมจึงสำคัญ:** `Document` แทนไฟล์ DOCX ทั้งไฟล์, ส่วน `DocumentBuilder` เป็นตัวช่วยที่สะดวกให้คุณแทรกข้อความ, ตาราง, รูปภาพ, และรูปทรงโดยไม่ต้องจัดการกับโครงสร้างโหนดพื้นฐานด้วยตนเอง

## ขั้นตอนที่ 2 – แทรกรูปสี่เหลี่ยม (Add rectangle shape)

ต่อไปเราจะ **เพิ่มรูปสี่เหลี่ยม** ลงในเอกสาร วิธี `InsertShape` รับประเภทของรูปทรงและขนาดเป็นหน่วยพอยต์ (1 พอยต์ = 1/72 นิ้ว)

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **เคล็ดลับมืออาชีพ:** หากต้องการสร้างรูปทรงอื่น (วงรี, สามเหลี่ยม ฯลฯ) เพียงเปลี่ยน `ShapeType.Rectangle` เป็นค่า enum ที่ต้องการ

## ขั้นตอนที่ 3 – ตั้งค่าเงา (Set shape fill color & shadow)

เงาช่วยให้รูปทรงแบนดูมีมิติสามมิติมากขึ้น ที่นี่เราเปิดใช้งานเงาและปรับลักษณะของมัน

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **ทำไมต้องใช้ค่าดังกล่าว?** รัศมีเบลอร์ที่พอเหมาะและระยะห่าง 5 พอยต์ทำให้เงาไม่บดบังรูปทรง, ส่วนมุม 45° จำลองแหล่งแสงมาจากด้านบน‑ซ้าย – เป็นแนวทาง UI ที่พบได้บ่อย

## ขั้นตอนที่ 4 – บันทึกเอกสาร (Save docx file)

สุดท้ายเราจะ **บันทึกไฟล์ docx** ลงดิสก์ ปรับเส้นทางให้เหมาะกับสภาพแวดล้อมของคุณ

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

เมื่อคุณเปิด `ShadowDemo.docx` ใน Word คุณควรเห็นสี่เหลี่ยมสีฟ้าอ่อนพร้อมเงาสีเทานุ่ม ๆ เหมือนภาพหน้าจอด้านล่าง

![สร้างเอกสาร Word พร้อมรูปสี่เหลี่ยมและเงา](https://example.com/images/rectangle-shadow.png "สร้างเอกสาร Word พร้อมรูปสี่เหลี่ยมและเงา")

*ข้อความแทนภาพ:* **สร้างเอกสาร Word** แสดงรูปสี่เหลี่ยมพร้อมเงา

## ตัวอย่างเต็มพร้อมรัน (How to create rectangle and save)

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมเต็มที่คุณสามารถคัดลอกไปใส่ในแอปคอนโซลได้

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

- จะมีไฟล์ชื่อ **ShadowDemo.docx** ปรากฏในโฟลเดอร์เป้าหมาย  
- เปิดไฟล์ใน Microsoft Word จะเห็นหน้าเดียวที่มีข้อความ “Shadow Demo” ตามด้วยสี่เหลี่ยมสีฟ้าอ่อน  
- สี่เหลี่ยมจะมีเงาสีเทานุ่มที่มุม 45°, ให้ความรู้สึก 3‑D เล็กน้อย

## คำถามทั่วไป & กรณีขอบ

### ถ้าต้องการขนาดอื่น?

เพียงเปลี่ยนค่า `200, 100` ใน `InsertShape` ตัวเลขเหล่านี้คือความกว้างและความสูงเป็นพอยต์ สำหรับสี่เหลี่ยมจัตุรัสให้ใช้ค่าเดียวกัน

### ต้องการให้เงาเด่นขึ้น?

เพิ่ม `BlurRadius` เพื่อให้ขอบนุ่มขึ้น, เพิ่ม `Distance` เพื่อขยับเงาออกไกลขึ้น, หรือ ลด `Transparency` (เช่น `0.1`) เพื่อทำให้เงาเข้มขึ้น

### จะเพิ่มขอบให้สี่เหลี่ยมได้อย่างไร?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### รองรับเวอร์ชันเก่าของ Aspose.Words หรือไม่?

ใช่. คลาส `ShadowFormat` มีตั้งแต่รุ่นปล่อยในปี 2020 หากคุณใช้เวอร์ชันเก่าเกินไปอาจต้องอัปเกรดเพื่อใช้คุณสมบัติต่าง ๆ

## เคล็ดลับ & สิ่งที่ควรระวัง

- **เคล็ดลับมืออาชีพ:** ควรทำการ `Dispose()` เอกสารขนาดใหญ่ (`doc.Dispose()`) เมื่อเสร็จ, โดยเฉพาะในแอปเว็บ, เพื่อปลดปล่อยทรัพยากรเนทีฟ  
- **ระวัง:** การใช้เส้นทางสัมพันธ์โดยไม่มีสิทธิ์ที่เหมาะสมอาจทำให้เกิด `UnauthorizedAccessException` ควรใช้เส้นทางเต็มหรือให้แอปพลิเคชันมีสิทธิ์เขียน  
- **จำไว้:** คุณสมบัติ `FillColor` รับค่า `System.Drawing.Color` ใดก็ได้ ใช้ `Color.FromArgb(255, 173, 216, 230)` เพื่อกำหนดสีพาสเทลตามต้องการ

## ขั้นตอนต่อไป

ตอนนี้คุณรู้วิธี **สร้างเอกสาร word**, **เพิ่มรูปสี่เหลี่ยม**, **ตั้งค่าสีเติม**, และ **บันทึกไฟล์ docx** แล้ว คุณสามารถทดลองต่อได้:

- แทรกรูปหลายรูปและจัดตำแหน่งด้วย `RelativeHorizontalPosition` และ `RelativeVerticalPosition`  
- ผสานสี่เหลี่ยมกับข้อความโดยใช้ `Shape.TextBox` สำหรับคำอธิบาย  
- ส่งออกเอกสารเดียวกันเป็น PDF (`doc.Save("output.pdf")`) เพื่อการแจกจ่าย

หากคุณสนใจกราฟิกขั้นสูงเพิ่มเติม ตรวจสอบการสนับสนุนของ Aspose.Words สำหรับ **WordArt**, **charts**, และ **inline images** ทุกอย่างทำตามรูปแบบเดียวกัน: สร้างโหนด, ตั้งค่าคุณสมบัติ, แล้วบันทึก

---

### TL;DR

- ใช้ `Document` และ `DocumentBuilder` เพื่อ **สร้างเอกสาร word**  
- เรียก `InsertShape(ShapeType.Rectangle, …)` เพื่อ **เพิ่มรูปสี่เหลี่ยม**  
- ตั้งค่า `FillColor` เพื่อกำหนดพื้นหลังที่ต้องการ  
- เปิดใช้งาน `ShadowFormat` และปรับคุณสมบัติเพื่อให้ดูเป็นมืออาชีพ  
- ปิดท้ายด้วย `document.Save("yourPath.docx")` เพื่อ **บันทึกไฟล์ docx**

ขอให้เขียนโค้ดสนุกและทำให้ไฟล์ Word ของคุณดูสวยงามยิ่งขึ้น!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}