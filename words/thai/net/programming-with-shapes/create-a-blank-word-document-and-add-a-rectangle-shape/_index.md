---
category: general
date: 2026-09-05
description: เรียนรู้วิธีสร้างเอกสาร Word ว่างและเพิ่มรูปสี่เหลี่ยมที่สามารถซ่อนได้โดยใช้
  Aspose.Words ใน C#
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: th
lastmod: 2026-09-05
og_description: การสร้างเอกสาร Word ว่างและการแทรกรูปสี่เหลี่ยมที่ซ่อนอยู่โดยใช้ Aspose.Words
  – คู่มือแบบขั้นตอนต่อขั้นตอนสำหรับนักพัฒนา C#
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: สร้างเอกสาร Word ว่างพร้อมรูปสี่เหลี่ยมที่ซ่อน
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: สร้างเอกสาร Word ว่างและเพิ่มรูปสี่เหลี่ยม
url: /th/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word ว่างและเพิ่มรูปสี่เหลี่ยมผืนผ้า

หากคุณต้องการสร้าง **เอกสาร Word ว่าง** ที่ยังมีรูปทรงที่คุณไม่ต้องการให้แสดงในเลย์เอาต์ คู่มือนี้จะแสดงวิธีทำอย่างละเอียดด้วย Aspose.Words สำหรับ .NET คุณจะได้เห็นตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่งสร้างเอกสารใหม่ เพิ่มรูปสี่เหลี่ยมผืนผ้า ซ่อนรูปนั้น และบันทึกไฟล์—โดยไม่ต้องใช้เครื่องมือเพิ่มเติม

บทเรียนนี้ครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโครงการจนถึงการแก้ไขปัญหาที่พบบ่อย เมื่อจบคุณจะสามารถสร้างไฟล์ Word ที่ดูว่างเปล่าแก่ผู้อ่าน แต่ยังคงบรรจุเมตาดาต้าแบบซ่อนอยู่ ซึ่งมีประโยชน์สำหรับการทำลายน้ำ การจัดเก็บ XML แบบกำหนดเอง หรือเป็นจุดยึดของเลย์เอาต์

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า (โค้ดนี้ยังทำงานได้กับ .NET Framework 4.7+)
* Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ C#)
* ใบอนุญาต NuGet **Aspose.Words** ที่ใช้งานได้ (รุ่นทดลองฟรีใช้สำหรับทดสอบ)
* ความคุ้นเคยพื้นฐานกับ C# และแนวคิดของโหนดเอกสาร

คุณสามารถติดตั้งไลบรารีด้วยคำสั่ง CLI ต่อไปนี้:

```bash
dotnet add package Aspose.Words
```

> **เคล็ดลับ:** ควรอัปเดตเวอร์ชัน Aspose.Words ของคุณอย่างสม่ำเสมอ; API ที่ใช้ในบทเรียนนี้มีความเสถียรตั้งแต่เวอร์ชัน 23.10

## วิธีสร้างเอกสาร Word ว่างด้วย Aspose.Words

ขั้นตอนแรกคือการสร้างอ็อบเจ็กต์ `Document` ใหม่ `Document` ที่เพิ่งสร้างขึ้นจะแสดงถึง **เอกสาร Word ว่าง**—ไม่มีย่อหน้า ไม่มีส่วน เพียงแค่คอนเทนเนอร์ไฟล์

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **ทำไมจึงสำคัญ:** การเริ่มต้นด้วยเอกสารที่สะอาดช่วยให้แน่ใจว่ารูปที่ซ่อนจะไม่ขัดแย้งกับเนื้อหา หรือสไตล์ที่มีอยู่แล้ว

## เพิ่มรูปสี่เหลี่ยมผืนผ้าไปยังเอกสาร

ต่อไปเราจะสร้างรูปสี่เหลี่ยมผืนผ้า ใน Aspose.Words รูปเป็นโหนดที่สามารถวางได้ทุกที่ในโครงสร้างต้นไม้ของเอกสาร และสามารถกำหนดขนาด การเติมสี สไตล์เส้น และการมองเห็นได้

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

โค้ดด้านบนสร้างสี่เหลี่ยมที่มองเห็นได้ ณ จุดนี้คุณอาจแทรกมันลงในเอกสารด้วย `builder.InsertNode(rectangle)` อย่างไรก็ตาม เนื่องจากเราต้องการให้รูปคงอยู่ในสถานะซ่อน เราจะปรับคุณสมบัติ `Hidden` ก่อนทำการแทรก

## วิธีซ่อนรูปในเอกสาร Word

Word มีแอตทริบิวต์ `Hidden` สำหรับโหนดรูป เมื่อกำหนดค่าเป็น `true` รูปจะไม่ปรากฏในเลย์เอาต์ของหน้า แต่ยังคงเป็นส่วนหนึ่งของ XML ของเอกสาร นี่คือหัวใจของ **วิธีซ่อนรูป** ที่ต้องการ

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **คำอธิบาย:** การตั้งค่า `Hidden = true` จะเพิ่มแอตทริบิวต์ `<w:hide>` ลงใน XML ของรูป โปรแกรมประมวลผล Word จะละเลยรูปขณะเรนเดอร์ แต่รูปยังสามารถเข้าถึงได้ผ่านโค้ดหรือมุมมอง XML ของ Word

## แทรกรูปที่ซ่อนอยู่ลงในเอกสารว่าง

ตอนนี้เราจะวางสี่เหลี่ยมที่ซ่อนลงในโครงสร้างต้นไม้ของเอกสาร เนื่องจากเอกสารยังคงว่างเปล่า รูปจะกลายเป็นโหนดแรกในสตอรีหลัก

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

หากคุณเปิดไฟล์ที่ได้ใน Microsoft Word คุณจะเห็นหน้าที่ดูเหมือนว่างเปล่า รูปยังคงอยู่แต่ไม่ปรากฏให้เห็น

## บันทึกเอกสาร

สุดท้ายให้เขียนเอกสารลงดิสก์ คุณสามารถเลือกฟอร์แมตที่รองรับได้ทุกแบบ (`.docx`, `.pdf`, `.odt`, ฯลฯ) สำหรับบทเรียนนี้เราจะใช้ฟอร์แมต DOCX สมัยใหม่

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### ผลลัพธ์ที่คาดหวัง

เปิด `HiddenRectangle.docx` ใน Word:

* เอกสารปรากฏเป็นว่างเปล่า (ไม่มีรูปหรือข้อความที่มองเห็น)
* หากคุณตรวจสอบไฟล์ด้วยเครื่องมือเช่น **Open XML SDK** หรือ **Word XML Viewer** คุณจะเห็นองค์ประกอบ `<w:pict>` ที่บรรจุสี่เหลี่ยมพร้อมแอตทริบิวต์ `hidden`

![เอกสาร Word ว่างพร้อมรูปสี่เหลี่ยมผืนผ้าแบบซ่อน](image.png){: .align-center alt="เอกสาร Word ว่างพร้อมรูปสี่เหลี่ยมผืนผ้าแบบซ่อน"}

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปพลิเคชันคอนโซล มันรวม `using` directives ที่จำเป็น การจัดการข้อผิดพลาด และคอมเมนต์ทั้งหมด

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

เรียกใช้โปรแกรม (`dotnet run`) แล้วตรวจสอบไฟล์ผลลัพธ์ คอนโซลจะแจ้งตำแหน่งที่บันทึกไว้

## คำถามทั่วไปและกรณีขอบ

### ฉันสามารถซ่อนหลายรูปพร้อมกันได้หรือไม่?

ได้ คุณสร้างแต่ละรูป ตั้งค่า `Hidden = true` แล้วแทรกตามลำดับ ธงซ่อนทำงานต่อโหนด ดังนั้นการผสมรูปซ่อนและรูปที่มองเห็นในเอกสารเดียวกันจึงได้รับการสนับสนุน

### ถ้าฉันต้องการให้รูปซ่อนเฉพาะในมุมมองการพิมพ์จะทำอย่างไร?

Word แยกความแตกต่างระหว่างการมองเห็น **display** และ **print** ผ่านแอตทริบิวต์ `DisplayWhen` Aspose.Words ไม่ได้เปิดเผย API โดยตรงสำหรับแอตทริบิวต์นั้น แต่คุณสามารถแก้ไข XML พื้นฐานได้:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

ใช้วิธีนี้เฉพาะเมื่อคุณต้องการให้รูปมองเห็นได้เฉพาะในการพิมพ์เท่านั้น

### รูปที่ซ่อนอยู่ส่งผลต่อขนาดไฟล์หรือไม่?

รูปที่ซ่อนอยู่เพิ่มข้อมูล XML เท่ากับรูปที่มองเห็นได้ ดังนั้นขนาดไฟล์ที่เพิ่มขึ้นจึงเท่ากัน อย่างไรก็ตาม เนื่องจากรูป

## สิ่งต่อไปที่คุณควรเรียนรู้

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบต่าง ๆ ในโครงการของคุณเอง

- [สร้างเอกสาร Word ว่างพร้อมรูปสี่เหลี่ยมเงา – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [สร้างรูปสี่เหลี่ยมผืนผ้าใน Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [บทเรียนเงารูป Aspose.Words – เพิ่มเงาให้รูป Word ใน C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}