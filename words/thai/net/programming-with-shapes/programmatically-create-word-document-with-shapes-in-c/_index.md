---
category: general
date: 2026-11-22
description: สร้างเอกสาร Word ด้วยโปรแกรมใน C# แล้วแทรกรูปสี่เหลี่ยม, แทรกรูปหลายรูป,
  และเขียนรูปลงใน Word โดยใช้ Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: th
lastmod: 2026-11-22
og_description: สร้างเอกสาร Word อย่างโปรแกรมเมติกใน C# โดยแทรกรูปสี่เหลี่ยม, แทรกรูปหลายรูป,
  และเขียนรูปลงใน Word ด้วย Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: สร้างเอกสาร Word พร้อมรูปทรงโดยใช้ C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: สร้างเอกสาร Word พร้อมรูปทรงโดยเขียนโปรแกรมใน C#
url: /th/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word พร้อมรูปทรงโดยอัตโนมัติด้วย C#

หากคุณต้องการ **สร้างเอกสาร Word โดยอัตโนมัติ** ที่มีกราฟิกแบบกำหนดเอง คำแนะนำนี้จะแสดงวิธีทำด้วย Aspose.Words for .NET คุณจะได้เรียนรู้การแทรกรูปสี่เหลี่ยม, เพิ่มรูปทรงอื่น ๆ, จัดกลุ่มรูปทรงเหล่านั้น, และสุดท้ายบันทึกรูปทรงลงใน Word—ทั้งหมดในไม่กี่บรรทัดของ C#.

การสร้างไฟล์ Word ที่มีกราฟิกไม่ต้องอาศัยการแก้ไขด้วยมือหรือสคริปต์แมโครอีกต่อไป เมื่อจบบทเรียนนี้คุณจะมีเมธอดที่ใช้ซ้ำได้ซึ่งสร้างไฟล์ `.docx` ที่มีสี่เหลี่ยมและวงรีจัดกลุ่มพร้อมใช้งานสำหรับการประมวลผลต่อหรือการรายงานผล.

## สิ่งที่คุณต้องเตรียม

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+)
- Aspose.Words for .NET (แพคเกจ NuGet `Aspose.Words`)
- IDE เช่น Visual Studio 2022 (หรือโปรแกรมแก้ไขใด ๆ ที่สามารถคอมไพล์ C# ได้)

> **เคล็ดลับ:** ติดตั้งแพคเกจด้วยคำสั่ง CLI `dotnet add package Aspose.Words` ก่อนเริ่มเขียนโค้ด.

## ภาพรวมการสร้างเอกสาร Word โดยอัตโนมัติ

กระบวนการโดยรวมประกอบด้วยสามขั้นตอนหลัก:

1. **เริ่มต้น** `Document` ใหม่และ `DocumentBuilder`  
2. **แทรกรูปทรงหลายรูป** (สี่เหลี่ยมและวงรี) แล้วใส่ไว้ใน `GroupShape`  
3. **บันทึกรูปทรงลง Word** โดยบันทึก `Document` เป็นไฟล์ `.docx`

แต่ละขั้นตอนถูกแยกเป็นส่วนย่อยด้านล่าง เพื่อให้คุณสามารถคัดลอก‑วางโค้ดลงในโปรเจกต์ของคุณได้โดยตรง.

![สร้างเอกสาร Word ด้วยรูปทรงที่จัดกลุ่ม](grouped-shapes.png){: .align-center alt="สร้างเอกสาร Word ด้วยรูปทรงที่จัดกลุ่ม"}

## ขั้นตอนที่ 1: เริ่มต้นเอกสารและตัวสร้าง

คลาส `Document` แทนไฟล์ Word ทั้งหมด, ส่วน `DocumentBuilder` ให้ API แบบ fluent เพื่อเพิ่มเนื้อหา

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*เหตุผลที่สำคัญ:* การสร้าง `Document` ก่อนทำให้คุณได้ “ผ้าใบ” ที่สะอาด `DocumentBuilder` จะติดตามตำแหน่งแทรกปัจจุบัน ซึ่งจำเป็นเมื่อคุณต่อมาจะใส่รูปทรงลงในโครงสร้างย่อหน้า.

## ขั้นตอนที่ 2: แทรกคอนเทนเนอร์ GroupShape

`GroupShape` ทำให้คุณจัดการรูปทรงหลายรูปเป็นหน่วยเดียว ซึ่งสะดวกเมื่อคุณต้องการย้ายหรือปรับขนาดพร้อมกัน

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*คำอธิบาย:* `InsertGroupShape` แทรกคอนเทนเนอร์เปล่าและทำให้มันเป็นรูปทรงปัจจุบัน รูปทรงที่แทรกต่อมาจะถูกเพิ่มเข้าไปในคอนเทนเนอร์นี้จนกว่าจะปิดกลุ่ม.

### แทรกรูปสี่เหลี่ยม

ต่อไปเราจะเพิ่มกราฟิกแรก—สี่เหลี่ยม ซึ่งสอดคล้องกับความต้องการ **insert rectangle shape**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

สี่เหลี่ยมสืบทอดบริบทการจัดรูปแบบจากกลุ่ม, ดังนั้นจะแสดงอยู่ภายใน `GroupShape`. คุณยังสามารถตั้งค่าสีเส้น, การเติมสี, หรือข้อความได้ในภายหลังหากต้องการ.

### แทรกรูปทรงหลายรูป

เพื่อสาธิตความสามารถ **insert multiple shapes**, เราจะเพิ่มวงรีหลังสี่เหลี่ยม คุณสามารถเพิ่มรูปทรงใด ๆ จำนวนเท่าใดก็ได้ (เช่น สามเหลี่ยม, ดาว) ก่อนปิดกลุ่ม

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

ตอนนี้กลุ่มมีสองรูปทรงที่แตกต่างกัน: สี่เหลี่ยมและวงรี เนื่องจากพวกมันมีพาเรนต์เดียวกัน คุณจึงสามารถย้ายพวกมันเป็นหน่วยเดียวได้.

## ขั้นตอนที่ 3: แนบ GroupShape ไปยังโครงสร้างย่อหน้า

เอกสาร Word เก็บเนื้อหาในต้นไม้ของย่อหน้า เพื่อให้กลุ่มปรากฏในไฟล์สุดท้าย เราต้องแนบมันไปยังย่อหน้าปัจจุบัน

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*เหตุผลที่ต้องทำขั้นตอนนี้:* หากไม่แนบกลุ่มไปยังย่อหน้า รูปทรงจะอยู่แค่ในหน่วยความจำและจะไม่ถูกบันทึกเมื่อบันทึกเอกสาร.

## ขั้นตอนที่ 4: บันทึกเอกสาร – เขียนรูปทรงลง Word

สุดท้าย เราจะบันทึก `Document` ที่อยู่ในหน่วยความจำลงดิสก์ นี่คือการบรรลุเป้าหมาย **write shapes to word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

เมื่อคุณเปิด `GroupShape.docx` ด้วย Microsoft Word คุณจะเห็นสี่เหลี่ยมและวงรีที่จัดกลุ่มอยู่ด้วยกัน ตามที่โค้ดได้แทรกไว้.

### ผลลัพธ์ที่คาดหวัง

- ไฟล์ชื่อ **GroupShape.docx** อยู่ในโฟลเดอร์ output ของโปรเจกต์  
- ภายในไฟล์ Word: ย่อหน้าเดียวที่มีสี่เหลี่ยมจัดกลุ่ม (100 pt × 50 pt) และวงรี (80 pt × 40 pt) การเลือกรูปใดรูปหนึ่งจะเลือกทั้งกลุ่ม

## การจัดการกรณีขอบทั่วไป

| สถานการณ์ | คำแนะนำ |
|-----------|----------|
| **DPI หรือขนาดหน้ากระดาษต่างกัน** | ตั้งค่า `builder.PageSetup.PaperSize` อย่างชัดเจนก่อนแทรกรูปทรงเพื่อหลีกเลี่ยงการสเกลที่ไม่คาดคิด |
| **ต้องการกำหนดตำแหน่งรูปทรงอย่างแม่นยำ** | ใช้ `builder.MoveTo` เพื่อย้ายตำแหน่งแทรก, จากนั้นตั้งค่า `groupShape.Left` และ `groupShape.Top` (ค่าหน่วยเป็น point) |

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจกต์ของคุณ

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}