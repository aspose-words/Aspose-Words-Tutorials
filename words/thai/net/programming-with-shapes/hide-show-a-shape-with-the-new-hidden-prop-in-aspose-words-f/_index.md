---
category: general
date: 2026-10-20
description: ซ่อน/แสดงรูปทรงด้วยคุณสมบัติ `Hidden` ใหม่โดยใช้ Aspose.Words สำหรับ
  C#. เรียนรู้วิธีสลับการมองเห็นของรูปทรง, จัดการกรณีขอบ, และบันทึกผลลัพธ์.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: th
lastmod: 2026-10-20
og_description: ซ่อน/แสดงรูปทรงด้วยคุณสมบัติ `Hidden` ใหม่โดยใช้ Aspose.Words สำหรับ
  C#. เชี่ยวชาญการสลับการมองเห็นของรูปทรงและหลีกเลี่ยงข้อผิดพลาดทั่วไป.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: ซ่อน/แสดงรูปร่างด้วยคุณสมบัติ `Hidden` ใหม่ใน Aspose.Words (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: ซ่อน/แสดงรูปทรงด้วยคุณสมบัติ `Hidden` ใหม่ใน Aspose.Words สำหรับ C#
url: /th/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ซ่อน/แสดง Shape ด้วยคุณสมบัติ `Hidden` ใหม่ใน Aspose.Words for C#

หากคุณต้องการ **ซ่อน/แสดง Shape ด้วยคุณสมบัติ `Hidden` ใหม่** ในเอกสาร Word คำแนะนำนี้จะแสดงให้คุณเห็นอย่างละเอียดว่าทำอย่างไรด้วย Aspose.Words for .NET ไม่ว่าคุณจะสร้างรายงาน, สร้างเทมเพลต, หรือทำความสะอาดเอกสารที่นำเข้า การควบคุมการมองเห็นของ Shape ผ่านโปรแกรมจะช่วยคุณหลีกเลี่ยงการแก้ไขด้วยตนเอง

ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีโหลดเอกสาร, ค้นหา Shape, สลับค่า `Hidden` และบันทึกไฟล์ที่แก้ไข ขั้นตอนเหล่านี้ยังครอบคลุมกรณีทั่วไปเช่นการจัดการหลาย Shape และการทำงานกับกราฟิกแบบ inline และ floating

## ข้อกำหนดเบื้องต้น

* .NET 6.0 (หรือใหม่กว่า) ที่ติดตั้งแล้ว – Aspose.Words รองรับ .NET Standard 2.0 และ .NET Core.
* สำเนาแบบลิขสิทธิ์ของ **Aspose.Words for .NET** (รุ่นทดลองฟรีใช้สำหรับการสำรวจ).
* IDE เช่น Visual Studio 2022 หรือ Visual Studio Code.
* เอกสาร Word (`input.docx`) ที่มีอย่างน้อยหนึ่ง Shape (เช่น รูปภาพ, SmartArt, หรือ drawing canvas).

## ขั้นตอนที่ 1: โหลดเอกสาร Word

การดำเนินการแรกคือการสร้างอ็อบเจ็กต์ `Document` ที่แทนไฟล์ .docx บนดิสก์

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*ทำไมขั้นตอนนี้สำคัญ*: `Document` เป็นจุดเริ่มต้นสำหรับการดำเนินการทั้งหมดของ Aspose.Words การโหลดไฟล์เข้าสู่หน่วยความจำทำให้คุณเข้าถึงโครงสร้าง node ทั้งหมดรวมถึง Shape

## ขั้นตอนที่ 2: ดึง Shape เป้าหมาย

เพื่อสลับการมองเห็นคุณต้องรับอ้างอิงไปยัง node ของ Shape ตัวอย่างด้านล่างดึง Shape แรกในเอกสาร แต่คุณสามารถปรับเปลี่ยนตรรกะเพื่อค้นหา Shape ตามชื่อ, ประเภท, หรือดัชนี

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*ทำไมขั้นตอนนี้สำคัญ*: `GetChild` พร้อม `true` ทำการค้นหาแบบลึก เพื่อให้คุณพบ Shape แม้จะซ้อนอยู่ในตารางหรือส่วนหัว การตรวจสอบ `null` ป้องกัน `NullReferenceException` เมื่อเอกสารไม่มี Shape

## ขั้นตอนที่ 3: ซ่อน Shape ด้วยคุณสมบัติ `Hidden`

Aspose.Words ได้แนะนำคุณสมบัติ `Hidden` เพื่อควบคุมว่า Shape จะถูกแสดงหรือพิมพ์หรือไม่ การตั้งค่าเป็น `true` จะซ่อน Shape; การตั้งค่าเป็น `false` จะทำให้ Shape ปรากฏอีกครั้ง

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

หากคุณต้องการ **แสดง** Shape ที่เคยซ่อนไว้ เพียงกำหนดค่า `false` :

```csharp
// Show the shape again
shape.Hidden = false;
```

*ทำไมขั้นตอนนี้สำคัญ*: คุณสมบัติ `Hidden` ทำงานกับ Shape ทั้งแบบ floating และ inline และทำงานร่วมกับการจัดรูปแบบ “Hidden” ของ Word วิธีนี้เชื่อถือได้กว่าการลบ Shape เพราะ node ยังคงอยู่ในโครงสร้างเอกสาร ทำให้รักษาเลย์เอาต์และการอ้างอิง

## ขั้นตอนที่ 4: บันทึกเอกสารที่แก้ไข

หลังจากปรับการมองเห็นแล้ว ให้เขียนการเปลี่ยนแปลงกลับไปยังไฟล์ใหม่ (หรือเขียนทับไฟล์เดิมหากต้องการ)

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*ทำไมขั้นตอนนี้สำคัญ*: `Save` ทำการแปลงโครงสร้าง node ในหน่วยความจำเป็นแพคเกจ .docx ที่ Word สามารถเปิดได้ ธง `Hidden` จะถูกบันทึกไว้ ดังนั้นการเปิดไฟล์ใน Microsoft Word จะทำให้ Shape แสดงตามการตั้งค่า `Hidden`

## ตัวอย่างเต็มที่สามารถรันได้

การรวมทุกขั้นตอนเข้าด้วยกันจะได้โปรแกรมที่เป็นอิสระซึ่งคุณสามารถคัดลอก, คอมไพล์, และรันได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**ผลลัพธ์ที่คาดหวัง** เมื่อคุณรันโปรแกรม:

```
Document saved. Shape hidden = True
```

การเปิด `ShapeHidden.docx` ใน Microsoft Word จะแสดงเอกสารโดยไม่มี Shape ที่กำหนด หากคุณตั้งค่า `shape.Hidden = false;` ก่อนบันทึก Shape จะปรากฏขึ้นอีกครั้ง

## การจัดการหลาย Shape

ตัวอย่างข้างต้นทำงานกับ Shape เดียว เอกสารในโลกจริงมักมีกราฟิกหลายรายการ ใช้ลูปเพื่อซ่อนหรือแสดง Shape ทั้งหมดที่ตรงตามเงื่อนไข (เช่น ชื่อหรือประเภทเฉพาะ)

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*เคล็ดลับ*: การกรองด้วย `ShapeType` จะช่วยหลีกเลี่ยงการซ่อนองค์ประกอบตกแต่งโดยไม่ได้ตั้งใจ เช่น text box หรือ SmartArt

## กรณีขอบและแนวทางปฏิบัติที่ดีที่สุด

| Situation | Recommended handling |
|-----------|----------------------|
| **Shape อยู่ในส่วนหัว/ส่วนท้าย** | ดึง node ของส่วนหัว/ส่วนท้ายก่อน แล้วเรียก `GetChild(NodeType.Shape, …)` บน sub‑document นั้น |
| **Document ไม่มี Shape** | ตรวจสอบ `null` หลังจาก `GetChild` หรือยืนยัน `doc.GetChildNodes(NodeType.Shape, true).Count` เสมอ |
| **ต้องการเก็บค่า hidden flag ไว้ข้ามเวอร์ชัน Word** | คุณสมบัติ `Hidden` ถูกเก็บใน XML ของ shape เป็น `<w:hidden/>` ซึ่งรองรับโดย Word 2007 ขึ้นไป |
| **ประสิทธิภาพกับเอกสารขนาดใหญ่** | ใช้ `doc.GetChildNodes(NodeType.Shape, true)` ครั้งเดียวและนำคอลเลกชันนั้นมาใช้ซ้ำแทนการเรียก `GetChild` หลายครั้ง |

## เคล็ดลับระดับมืออาชีพ: ผสาน `Hidden` กับ `WrapType`

เมื่อ Shape ถูกซ่อน Word ยังสงวนพื้นที่ที่ Shape จะครอบครองไว้ เว้นแต่คุณจะเปลี่ยนพฤติกรรมการห่อข้อความด้วย การตั้งค่า `WrapType = WrapType.None` จะลบพื้นที่จองไว้

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

วิธีนี้ทำให้เลย์เอาต์ยุบลงเหมือนว่า Shape ไม่เคยมีอยู่ ซึ่งมีประโยชน์สำหรับการสร้างรายงานที่สะอาด

## สรุป

ตอนนี้คุณรู้วิธี **ซ่อน/แสดง Shape ด้วยคุณสมบัติ `Hidden` ใหม่** ด้วย Aspose.Words for C# แล้ว โซลูชันนี้ครอบคลุมการโหลดเอกสาร, การค้นหา Shape, การสลับคุณสมบัติ `Hidden` และการบันทึกการเปลี่ยนแปลง โดยปฏิบัติตามเคล็ดลับแนวทางปฏิบัติที่ดีที่สุด—การตรวจสอบ `null`, การจัดการหลาย Shape, และการปรับตั้งค่า wrap—คุณสามารถควบคุมการมองเห็นของ Shape ได้อย่างเชื่อถือในทุกสถานการณ์การอัตโนมัติของ Word

พร้อมสำรวจต่อหรือยัง? พิจารณาขั้นตอนต่อไปนี้:

* **ซ่อน/แสดงหลาย Shape** ตามเมตาดาต้ากำหนดเอง (ใช้เทคนิค “programmatically hide shape”)
* **ผสาน `Hidden` กับเนื้อหาแบบมีเงื่อนไข** โดยใช้ฟิลด์ของ Aspose.Words สำหรับการสร้างรายงานแบบไดนามิก
* **สำรวจคุณสมบัติ node อื่นๆ** เช่น `Visible` สำหรับวัตถุแผนภูมิ หรือ `IsDeleted` สำหรับการควบคุมระดับย่อหน้า

ขอให้สนุกกับการเขียนโค้ด และเพลิดเพลินกับการควบคุมระดับละเอียดที่ Aspose.Words มอบให้สำหรับการมองเห็น Shape ในเอกสาร Word!

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการใช้งานอื่นในโครงการของคุณ

- [วิธีซ่อน Shape ใน Word ด้วย C# – คู่มือขั้นตอนที่ละเอียด](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [วิธีซ่อน Shape ใน Word ด้วย C# – คู่มือขั้นตอนที่ละเอียด](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [สร้างเอกสาร Word เปล่าพร้อม Shape วงรีที่ซ่อน – คู่มือ C# ฉบับเต็ม](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}