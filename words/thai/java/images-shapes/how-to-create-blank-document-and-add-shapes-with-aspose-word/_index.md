---
category: general
date: 2026-09-30
description: สร้างเอกสารเปล่าและแทรกรูปสี่เหลี่ยม, รูปวงรี, และจัดกลุ่มหลายรูปใน C#
  โดยใช้ Aspose.Words. เรียนรู้วิธีแทรกรูปและวิธีสร้างกลุ่ม.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: th
lastmod: 2026-09-30
og_description: สร้างเอกสารเปล่าใน C# และเรียนรู้วิธีแทรกรูปทรงและจัดกลุ่มรูปทรงหลายรูปด้วย
  Aspose.Words ทำตามบทแนะนำขั้นตอนโดยละเอียด.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: สร้างเอกสารเปล่าและจัดกลุ่มรูปร่างใน C# – คู่มือ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: วิธีสร้างเอกสารเปล่าและเพิ่มรูปทรงด้วย Aspose.Words ใน C#
url: /th/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างเอกสารเปล่าและเพิ่มรูปทรงด้วย Aspose.Words ใน C#

หากคุณต้องการ **สร้างเอกสารเปล่า** และเติมกราฟิกลงไป คู่มือนี้จะแสดงวิธีทำอย่างละเอียด คุณจะได้เห็นวิธี **แทรกรูปสี่เหลี่ยม** เพิ่มวัตถุวาดอื่น ๆ และ **จัดกลุ่มหลายรูปทรง** ให้ทำงานเป็นหน่วยเดียว

การทำงานกับรูปทรงเป็นความต้องการทั่วไปเมื่อสร้างสัญญา ใบรับรอง หรือรายงานแบบกำหนดเอง ในบทเรียนนี้คุณจะได้เรียนรู้ขั้นตอนทั้งหมด ตั้งแต่การเริ่มต้นเอกสารจนถึงการบันทึกไฟล์สุดท้าย โดยใช้ Aspose.Words API สำหรับ .NET

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 (หรือใหม่กว่า) SDK ติดตั้งแล้ว  
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (รุ่นทดลองฟรีใช้ได้กับตัวอย่างนี้)  
* IDE เช่น Visual Studio 2022 หรือ Visual Studio Code  

ไม่จำเป็นต้องติดตั้งแพ็กเกจ NuGet เพิ่มเติมนอกจาก `Aspose.Words`

## วิธีสร้างเอกสารเปล่าและทำงานกับรูปทรง

ขั้นตอนแรกคือการสร้างอ็อบเจกต์ `Document` ซึ่งอ็อบเจกต์นี้แทนไฟล์ Word ในหน่วยความจำและให้คุณเข้าถึง `DocumentBuilder` ซึ่งเป็นเครื่องมือหลักสำหรับแทรกเนื้อหา

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**ทำไมจึงสำคัญ:** เอกสารเปล่าให้พื้นที่ว่างสะอาด `DocumentBuilder` จะรักษาตำแหน่งแทรกปัจจุบันไว้ ดังนั้นทุกรูปทรงที่คุณเพิ่มจะถูกวางอัตโนมัติบนหน้าที่เหมาะสม

## แทรกรูปสี่เหลี่ยมและรูปทรงอื่น ๆ

ต่อไปเราจะเพิ่มรูปสี่เหลี่ยมและรูปวงรี ทั้งสองการเรียกใช้ใช้เมธอด `InsertShape` เดียวกัน ซึ่งเป็นวิธีที่แนะนำ **วิธีแทรกรูปทรง** ใน Aspose.Words

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*เมธอด `InsertShape` จะวางรูปทรงโดยอัตโนมัติที่ตำแหน่งเคอร์เซอร์ปัจจุบัน* หากต้องการตำแหน่งที่แม่นยำ คุณสามารถปรับ `Shape.Left` และ `Shape.Top` หลังจากแทรกได้

## จัดกลุ่มหลายรูปทรงเป็นอ็อบเจกต์เดียว

ต่อไปเราจะรวมรูปสี่เหลี่ยมและรูปวงรีให้เป็นเอนทิตี้เดียว การจัดกลุ่มเป็นประโยชน์เมื่อคุณต้องการย้ายหรือปรับขนาดหลายรูปพร้อมกัน

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**วิธีการทำงาน:** `InsertGroupShape` สร้างคอนเทนเนอร์ที่ทำงานเหมือน `Shape` ใด ๆ การเรียก `AppendChild` จะย้ายรูปที่มีอยู่เข้าไปในคอนเทนเนอร์ ซึ่งจะอัปเดตพิกัดสัมพันธ์โดยอัตโนมัติ

### เคล็ดลับปฏิบัติ

หากคุณต้องการ **วิธีสร้างกลุ่ม** โปรแกรมmatically สำหรับรูปมากกว่าสองรูป เพียงทำซ้ำ `AppendChild` สำหรับแต่ละอินสแตนซ์ `Shape` ที่เพิ่มเข้ามา กลุ่มสามารถบรรจุวัตถุวาดได้จำนวนไม่จำกัด รวมถึงรูปภาพ, กล่องข้อความ, หรือแม้แต่กลุ่มอื่น ๆ

## ตัวอย่างเต็ม – วิธีแทรกรูปทรงและบันทึกเอกสาร

ด้านล่างเป็นโปรแกรมที่ทำงานได้เต็มรูปแบบซึ่งสาธิตทุกขั้นตอนที่กล่าวถึง การรันโค้ดจะสร้างไฟล์ `ShapesDemo.docx` ที่มีรูปสี่เหลี่ยม, รูปวงรี, และรูปที่จัดกลุ่มไว้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** การเปิด `ShapesDemo.docx` ใน Microsoft Word จะเห็นหน้าเดียวที่มีสี่เหลี่ยมสีน้ำเงิน, วงรีสีเขียว, และกรอบสีเทาที่ล้อมรอบซึ่งเป็นตัวแทนของกลุ่ม การย้ายกลุ่มจะทำให้ทั้งสองรูปเคลื่อนที่พร้อมกัน ยืนยันว่าการ **จัดกลุ่มหลายรูปทรง** ทำงานสำเร็จ

## คำถามที่พบบ่อยและการจัดการกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| *ถ้าต้องการให้รูปอยู่ในหน้าที่กำหนดต้องทำอย่างไร?* | เรียก `builder.MoveToDocumentEnd();` ก่อนแทรกรูป หรือใช้ `builder.MoveToSection(sectionIndex);` เพื่อกำหนดส่วนเฉพาะ |
| *สามารถเพิ่มข้อความภายในรูปที่จัดกลุ่มได้หรือไม่?* | ได้ สร้าง `Shape` ชนิด `ShapeType.TextBox` ตั้งค่าข้อความ แล้ว `AppendChild` เข้าไปใน `GroupShape` |
| *มิติของรูปใช้หน่วยเป็นจุดหรือพิกเซล?* | Aspose.Words ใช้ **points** (1 pt = 1/72 inch) เพื่อให้ขนาดสอดคล้องกันบนเครื่องพิมพ์และจอแสดงผล |
| *จะเปลี่ยนการหมุนของกลุ่มอย่างไร?* | ตั้งค่า `groupShape.RotationAngle = 45;` (หน่วยเป็นองศา) รูปทั้งหมดในกลุ่มจะหมุนรอบจุดศูนย์กลางของกลุ่ม |

## สรุป

คุณได้เรียนรู้วิธี **สร้างเอกสารเปล่า**, **แทรกรูปสี่เหลี่ยม**, **วิธีแทรกรูปทรง** เช่น วงรี, และ **จัดกลุ่มหลายรูปทรง** ให้เป็นอ็อบเจกต์เดียวโดยใช้ Aspose.Words สำหรับ .NET ตัวอย่างโค้ดเต็มแสดงแนวทางที่แนะนำ และเคล็ดลับข้างต้นช่วยให้คุณปรับใช้กับสถานการณ์ที่ซับซ้อนกว่า เช่น การเพิ่มกล่องข้อความหรือการหมุนกลุ่ม

พร้อมสำรวจต่อหรือยัง? ลองเพิ่มรูปภาพเข้าไปในกลุ่ม, ทดลองเปลี่ยนสีเติม, หรือสร้างรายงานหลายหน้าโดยแต่ละหน้ามีแผนภูมิที่จัดกลุ่มเอง หลักการเดียวกันสามารถขยายไปยังโครงการอัตโนมัติเอกสารใด ๆ ได้

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}