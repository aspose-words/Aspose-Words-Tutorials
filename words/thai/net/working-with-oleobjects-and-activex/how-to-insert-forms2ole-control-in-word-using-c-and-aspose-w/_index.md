---
category: general
date: 2026-11-22
description: เรียนรู้วิธีแทรกควบคุม Forms2Ole ใน Word ด้วย C# คู่มือขั้นตอนนี้ครอบคลุม
  DocumentBuilder การวางปุ่มคำสั่ง และการบันทึกไฟล์ .docx
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: th
lastmod: 2026-11-22
og_description: แทรกคอนโทรล Forms2Ole ใน Word ด้วย C#. ทำตามคำแนะนำนี้เพื่อเพิ่มปุ่มคำสั่งโดยใช้
  Aspose.Words และ DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: แทรกคอนโทรล Forms2Ole ใน Word ด้วย C# – คู่มือครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีแทรกควบคุม Forms2Ole ใน Word ด้วย C# และ Aspose.Words
url: /th/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทรก Forms2Ole control ใน Word ด้วย C# และ Aspose.Words

หากคุณต้องการ **แทรก Forms2Ole control ใน Word** นี้เป็นบทแนะนำที่แสดงให้คุณเห็นอย่างชัดเจนว่าจะทำอย่างไรด้วย C#. ไม่ว่าคุณจะกำลังสร้างเทมเพลตที่สามารถกรอกข้อมูลได้หรืออัตโนมัติการสร้างฟอร์ม โซลูชันด้านล่างนี้จะทำให้คุณสามารถเพิ่มปุ่มคำสั่ง (command button) ผ่านโปรแกรมได้

คุณจะได้เรียนรู้วิธีสร้างเอกสารเปล่า, ใช้ `DocumentBuilder` เพื่อวาง control, และบันทึกผลลัพธ์เป็นไฟล์ `.docx`. คู่มือนี้ยังครอบคลุมข้อผิดพลาดทั่วไป เช่น ระบบพิกัดและความเข้ากันได้กับเวอร์ชัน Word เก่า

## ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+)
* Aspose.Words for .NET (แพ็กเกจ NuGet `Aspose.Words`)
* ความเข้าใจพื้นฐานเกี่ยวกับ C# และ Word object model
* IDE เช่น Visual Studio หรือ VS Code

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า namespaces

สร้างแอปพลิเคชันคอนโซลใหม่และเพิ่มแพ็กเกจ Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

ในไฟล์ `Program.cs` ให้นำเข้า namespaces ที่จำเป็น:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **เคล็ดลับ:** ใช้เวอร์ชันล่าสุดของ Aspose.Words เพื่อรับการสนับสนุนเต็มรูปแบบสำหรับ API `Forms2OleControl`.

## ขั้นตอนที่ 2: สร้างเอกสารเปล่าและเริ่มต้น DocumentBuilder

คลาส `Document` แทนไฟล์ Word, ส่วน `DocumentBuilder` ให้เมธอดสำหรับแทรกเนื้อหา.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` ทำงานคล้ายเคอร์เซอร์; หลังจากบรรทัดนี้คุณสามารถเริ่มวางองค์ประกอบได้ทุกที่ในเอกสาร.

## ขั้นตอนที่ 3: กำหนดตำแหน่งและขนาดของปุ่ม

Word วัดพิกัดเป็นหน่วย points (1 pt ≈ 1/72 in). โครงสร้าง `Rectangle` จาก `System.Drawing` บรรยายขอบเขตของ control.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` จะวาง control ที่มุมบน‑ซ้ายของหน้าปัจจุบัน.
* ปรับค่า `x` และ `y` เพื่อย้ายปุ่มไปตำแหน่งอื่น (เช่น `new Rectangle(150, 200, 100, 30)`).

## ขั้นตอนที่ 4: แทรกปุ่มคำสั่ง Forms2Ole

ตอนนี้ใช้ `InsertForms2OleControl` เพื่อเพิ่ม control. เมธอดนี้ต้องการประเภทของ control, ชื่อ, และขอบเขตที่กำหนดไว้ข้างต้น.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

อ็อบเจ็กต์ `Forms2OleControl` ที่คืนค่ามาให้คุณสามารถแก้ไขคุณสมบัติต่าง ๆ เช่น `Enabled`, `Visible` หรือแม้แต่แนบชื่อแมโครในภายหลัง.

### ทำไมต้องใช้ Forms2Ole?

* **ความเข้ากันได้กับระบบเก่า** – Controls ของ Forms2Ole ทำงานใน Word 97‑2003 (`.doc`) และไฟล์ `.docx` รุ่นใหม่.
* **รองรับแมโคร** – สามารถเรียกใช้แมโคร VBA ทำให้เหมาะกับเทมเพลตแบบโต้ตอบ.
* **การวางตำแหน่งที่แม่นยำ** – แตกต่างจาก content controls, คุณสามารถควบคุมพิกัดได้อย่างแน่นอน.

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายให้เขียนไฟล์ลงดิสก์. เลือกโฟลเดอร์ที่คุณมีสิทธิ์เขียน.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

เปิด `output.docx` ด้วย Microsoft Word. คุณจะเห็นปุ่มที่มีป้าย **ClickMe** ที่มุมบน‑ซ้ายของหน้าแรก. การคลิกใน Word จะไม่มีผลจนกว่าคุณจะกำหนดแมโคร, แต่ control ทำงานได้เต็มที่.

## การจัดการกับกรณีขอบที่พบบ่อย

| Situation | How to address it |
|-----------|-------------------|
| **ปุ่มปรากฏนอกหน้า** | ตรวจสอบให้แน่ใจว่าพิกัด `Rectangle` อยู่ภายในขอบเขตของหน้ากระดาษ. ใช้ `builder.PageSetup.PageWidth` และ `PageHeight` เพื่อคำนวณขอบเขตที่ปลอดภัย. |
| **Control ไม่แสดงใน Word เวอร์ชันเก่า** | บันทึกเอกสารเป็น `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) เพื่อรับประกันความเข้ากันได้ของ Forms2Ole กับ Word 97‑2003. |
| **ต้องการเปลี่ยนข้อความบนปุ่ม** | หลังจากแทรกแล้ว, ตั้งค่า `commandButton.Caption = "Submit";`. |
| **กำหนดแมโคร** | ตั้งค่า `commandButton.MacroName = "MyMacro"`; แมโครต้องมีอยู่ในโครงการ VBA ของเอกสาร. |
| **หลายปุ่ม** | ทำซ้ำขั้นตอน 4 ด้วยค่า `Rectangle` ที่แตกต่างและชื่อที่ไม่ซ้ำกัน. |

## ตัวอย่างที่สมบูรณ์และสามารถรันได้

เมื่อนำทุกอย่างมารวมกัน นี่คือโปรแกรมที่สมบูรณ์แบบที่คุณสามารถคัดลอก, วาง, และรันได้:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** หลังจากรันโปรแกรม, `output.docx` จะเปิดใน Word พร้อมปุ่มที่คลิกได้ที่มีข้อความ *Click Me!* อยู่ที่มุมบน‑ซ้ายของหน้าแรก.

## สรุป

ตอนนี้คุณรู้วิธี **แทรก Forms2Ole control ใน Word** ด้วย C# และ Aspose.Words แล้ว. กระบวนการนี้รวมถึงการสร้าง `Document`, การกำหนดตำแหน่ง `Rectangle`, และการเรียก `InsertForms2OleControl` ผ่าน `DocumentBuilder`. ด้วยตัวอย่างโค้ดเต็มและคำแนะนำสำหรับกรณีขอบ, คุณสามารถรวมปุ่มคำสั่งเข้าไปในกระบวนการทำงานอัตโนมัติของ Word ใด ๆ ได้.

### ขั้นตอนต่อไป

* สำรวจค่า `ControlType` อื่น ๆ เช่น `CheckBox` หรือ `OptionButton`.
* ผสานรวม Forms2Ole controls กับแมโคร VBA เพื่อสร้างฟอร์มแบบโต้ตอบ.
* ใช้ `DocumentBuilder.MoveTo` เพื่อวางปุ่มบนย่อหน้า หรือ ตาราง ที่ระบุ.
* ตรวจสอบเอกสาร **Forms2Ole** ของ Aspose.Words สำหรับการตั้งค่าคุณสมบัติขั้นสูง.

ขอให้สนุกกับการเขียนโค้ด, และเพลิดเพลินกับการสร้างเอกสาร Word ที่สมบูรณ์ยิ่งขึ้นด้วย C# และ Aspose.Words!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลรวมตัวอย่างโค้ดที่ทำงานได้เต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการนำไปใช้แบบต่าง ๆ ในโครงการของคุณ.

- [วิธีแทรกปุ่มคำสั่ง OLE ในเอกสาร Word ด้วย C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [วิธีเพิ่ม ActiveX control ใน Word ด้วย Aspose.Words – คู่มือขั้นตอนต่อขั้นตอน](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [เพิ่มปุ่มคำสั่งลงในเอกสาร Word ด้วย Aspose.Words – คู่มือเต็ม](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}