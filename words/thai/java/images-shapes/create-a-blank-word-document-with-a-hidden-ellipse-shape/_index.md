---
category: general
date: 2026-09-18
description: สร้างเอกสาร Word ว่างและซ่อนรูปวงรีโดยใช้ Aspose.Words. เรียนรู้วิธีซ่อนรูปใน
  Word, วิธีแทรกรูปวงรี, และสร้างรูปที่ซ่อนอย่างรวดเร็ว.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: th
lastmod: 2026-09-18
og_description: สร้างเอกสาร Word ว่างและซ่อนรูปวงรีใน Word คู่มือนี้จะแสดงขั้นตอนแบบทีละขั้นตอนว่าต้องแทรกรูปวงรี,
  ซ่อนรูปใน Word, และสร้างรูปที่ซ่อนด้วย Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: สร้างเอกสาร Word ว่างพร้อมรูปวงรีที่ซ่อนอยู่
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: สร้างเอกสาร Word ว่างพร้อมรูปวงรีที่ซ่อนอยู่
url: /th/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word ว่างพร้อมรูปวงรีที่ซ่อนอยู่

หากคุณต้องการ **สร้างเอกสาร Word ว่าง** ที่มีรูปทรงที่คุณไม่ต้องการให้ปรากฏในเลเอาต์ คู่มือนี้จะแสดงวิธีทำอย่างละเอียด โดยใช้ Aspose.Words for .NET คุณสามารถแทรกรูปวงรีด้วยโปรแกรมและจากนั้นซ่อนรูปทรงนั้นเพื่อให้เอกสารดูว่างเปล่าในเชิงภาพ แต่ยังคงเก็บข้อมูลรูปทรงไว้

ในบทเรียนนี้คุณจะได้เรียนรู้:

* วิธี **สร้างเอกสาร Word ว่าง** objects,
* วิธี **แทรกรูปวงรี** using `DocumentBuilder`,
* วิธี **ซ่อนรูปทรงใน Word** เพื่อไม่ให้ส่งผลต่อหน้า,
* วิธี **สร้างรูปทรงที่ซ่อนอยู่** objects สำหรับการประมวลผลในภายหลัง

ขั้นตอนเหล่านี้ทำงานกับ .NET 6+ และเวอร์ชันล่าสุดของ Aspose.Words (23.9 ณ เวลาที่เขียน) ไม่จำเป็นต้องติดตั้ง Office เพิ่มเติม

## ข้อกำหนดเบื้องต้น

* Visual Studio 2022 (หรือ IDE C# ใดก็ได้)
* .NET 6 SDK หรือใหม่กว่า
* Aspose.Words for .NET NuGet package  
  ```bash
  dotnet add package Aspose.Words
  ```
* ความรู้พื้นฐานเกี่ยวกับ C# และแนวคิดเอกสาร Word

## ขั้นตอนที่ 1: สร้างเอกสาร Word ว่าง

สิ่งแรกที่คุณต้องทำคือสร้างอ็อบเจ็กต์ `Document` อ็อบเจ็กต์นี้แทนไฟล์ `.docx` ที่ว่างเปล่าและเป็นพื้นฐานสำหรับการดำเนินการต่อไปทั้งหมด

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

การ **สร้างเอกสาร Word ว่าง** ให้คุณมีผืนผ้าใบที่สะอาด – ไม่มีย่อหน้า ไม่มีส่วน เพียงโครงสร้างแพ็กเกจพื้นฐาน นี่เป็นจุดเริ่มต้นที่เหมาะสมเมื่อคุณต้องการเพียงรูปทรงที่ซ่อนอยู่และไม่มีสิ่งอื่นใด

## ขั้นตอนที่ 2: เริ่มต้น DocumentBuilder

`DocumentBuilder` ให้ API ที่สะดวกสำหรับการเพิ่มเนื้อหาไปยัง `Document` มันทำงานเหมือนเคอร์เซอร์ที่คุณเคลื่อนผ่านเอกสาร

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder จะสร้างส่วนแรกและย่อหน้าเริ่มต้นโดยอัตโนมัติ ดังนั้นคุณสามารถเริ่มแทรกรูปทรงได้โดยไม่ต้องเพิ่มส่วนด้วยตนเอง

## ขั้นตอนที่ 3: แทรกรูปวงรี

ตอนนี้เราจะ **แทรกรูปวงรี** ด้วยเมธอด `InsertShape` เมธอดนี้รับพารามิเตอร์ `ShapeType` enumeration, ความกว้าง และความสูง (หน่วยเป็นพอยต์)

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

ทำไมต้องเป็นวงรี? วงรีเป็นรูปเวกเตอร์ที่สามารถซ่อนได้โดยไม่กระทบต่อการไหลของข้อความรอบข้าง ความกว้าง 100 pt และความสูง 50 pt เป็นค่าที่กำหนดขึ้นเอง; คุณสามารถปรับให้เหมาะกับความต้องการการประมวลผลในภายหลังได้

## ขั้นตอนที่ 4: ซ่อนรูปทรงเพื่อไม่ให้ปรากฏในเลเอาต์

เพื่อ **ซ่อนรูปทรงใน Word** ให้ตั้งค่า `Hidden` property ของอ็อบเจ็กต์ `Shape` เป็น `true` เมื่อเปิดเอกสารใน Microsoft Word รูปทรงจะไม่มองเห็นและจะไม่ใช้พื้นที่ในเลเอาต์

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

แฟล็ก `Hidden` จะถูกเก็บใน XML ของรูปทรง (`<w:hidden/>`) Word จะเคารพแอตทริบิวต์นี้ระหว่างการเรนเดอร์ ซึ่งเป็นเหตุผลที่เอกสารดูว่างเปล่าอย่างสมบูรณ์แม้ว่ารูปทรงยังคงอยู่

### เคล็ดลับพิเศษ

หากคุณต้องการทำให้รูปทรงปรากฏอีกครั้งในภายหลัง เพียงตั้งค่า `ellipse.Hidden = false;` แล้วบันทึกเอกสาร

## ขั้นตอนที่ 5: บันทึกเอกสารพร้อมรูปทรงที่ซ่อนอยู่

สุดท้าย ให้บันทึกเอกสารลงดิสก์ ไฟล์จะเป็น `.docx` ปกติที่โปรแกรมประมวลผล Word ใดก็เปิดได้

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

ไฟล์ที่บันทึกไว้ `HiddenEllipse.docx` เป็น **create blank word document** ที่มีรูปวงรีที่ซ่อนอยู่ การเปิดไฟล์นี้ใน Microsoft Word จะเห็นหน้าว่างเปล่า แต่รูปทรงยังคงอยู่ในโครงสร้าง Open XML

## ตัวอย่างการทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่สมบูรณ์และเป็นอิสระที่คุณสามารถคัดลอก วาง และรันได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output**

* ไฟล์ชื่อ `HiddenEllipse.docx` ปรากฏใน `C:\Temp`
* การเปิดไฟล์ใน Microsoft Word จะแสดงหน้าว่างเปล่าอย่างสมบูรณ์
* หากคุณตรวจสอบเอกสารด้วย Open XML SDK หรือโปรแกรมดูไฟล์ zip คุณจะพบองค์ประกอบ `<w:shape>` ที่มี `<w:hidden/>` อยู่ในส่วนของเอกสาร

## คำถามทั่วไปและกรณีขอบ

### ถ้ารูปทรงยังคงปรากฏอยู่?

* ตรวจสอบว่าคุณใช้ Aspose.Words 23.9 หรือใหม่กว่า – เวอร์ชันเก่ามีบั๊กที่ทำให้ `Hidden` ถูกละเลยสำหรับบางประเภทของรูปทรง
* ยืนยันว่าคุณไม่ได้ใช้การจัดรูปแบบเพิ่มเติม (เช่น `WrapType`) ที่บังคับให้รูปทรงใช้พื้นที่ในเลเอาต์

### ฉันสามารถซ่อนรูปทรงประเภทอื่นได้หรือไม่?

ใช่. แอตทริบิวต์ `Hidden` เดียวกันทำงานกับ `ShapeType.Rectangle`, `ShapeType.Picture` เป็นต้น เพียงเปลี่ยน `ShapeType.Ellipse` เป็นประเภทที่ต้องการ

### วิธีการแสดงรายการรูปทรงที่ซ่อนอยู่ในภายหลัง?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

โค้ดสแนปนี้วนลูปผ่านรูปทรงทั้งหมดและพิมพ์รูปทรงที่ถูกซ่อน ซึ่งมีประโยชน์สำหรับ workflow **create hidden shape** ที่คุณต้องการประมวลผลหรือยกเลิกการซ่อนในภายหลัง

## สรุป

คุณได้เรียนรู้วิธี **สร้างเอกสาร Word ว่าง**, **แทรกรูปวงรี**, และ **ซ่อนรูปทรงใน Word** เพื่อสร้าง **create hidden shape** ที่มองไม่เห็นต่อผู้อ่าน เทคนิคนี้เป็นประโยชน์สำหรับการเก็บเมตาดาต้า, บุ๊กมาร์ก, หรือ XML แบบกำหนดเองภายในเอกสารโดยไม่เปลี่ยนแปลงลักษณะการแสดงผล

### ขั้นตอนต่อไป

* สำรวจ **วิธีซ่อนรูปทรง** อย่างมีเงื่อนไขตามเนื้อหาเอกสาร
* เรียนรู้ **วิธียกเลิกการซ่อนรูปทรง** เมื่อสร้างเวอร์ชันสุดท้ายของเอกสาร
* ผสานรูปทรงที่ซ่อนกับ **คุณสมบัติเ�เอกสารแบบกำหนดเอง** เพื่อฝังข้อมูลที่เครื่องอ่านได้

Feel free to experiment with different shape types, sizes, and hidden‑state logic to fit your automation scenario. Happy coding!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบต่าง ๆ ในโครงการของคุณ

- [สร้างเอกสาร Word ว่างพร้อมรูปสี่เหลี่ยมเงา – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [สร้าง Group Shape ในเอกสาร Word โดยใช้ Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}