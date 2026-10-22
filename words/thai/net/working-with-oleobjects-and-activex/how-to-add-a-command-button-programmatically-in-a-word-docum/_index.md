---
category: general
date: 2026-10-13
description: เรียนรู้วิธีเพิ่มปุ่มคำสั่งโดยใช้โค้ดโปรแกรมด้วย Aspose.Words คู่มือนี้ยังแสดงวิธีสร้างปุ่มในเอกสาร
  Word ด้วยโค้ด C# เต็มรูปแบบ
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: th
lastmod: 2026-10-13
og_description: เพิ่มปุ่มคำสั่งโดยโปรแกรมลงในเอกสาร Word ด้วย Aspose.Words. ทำตามบทแนะนำฉบับเต็มนี้เพื่อสร้างปุ่มในเอกสาร
  Word ด้วย C#
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: เพิ่มปุ่มคำสั่งโดยโปรแกรมลงในเอกสาร Word – คู่มือทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีเพิ่มปุ่มคำสั่งโดยโปรแกรมในเอกสาร Word
url: /th/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มปุ่มคำสั่งโดยโปรแกรมในเอกสาร Word  

หากคุณต้องการ **เพิ่มปุ่มคำสั่งโดยโปรแกรม**, Aspose.Words มี API ที่สะอาดและง่ายต่อการฝังคอนโทรลฟอร์ม OLE ลงในไฟล์ .docx โดยตรง บทแนะนำนี้จะพาคุณผ่านทุกขั้นตอนที่จำเป็นเพื่อ **สร้างปุ่มในเอกสาร Word** ที่ทำงานเหมือนปุ่มฟอร์มทั่วไปเมื่อเปิดเอกสารใน Microsoft Word  

คุณจะได้เรียนรู้วิธีตั้งค่าสภาพแวดล้อมการพัฒนา, แทรกปุ่ม, กำหนดคุณสมบัติของมัน, และตรวจสอบผลลัพธ์ ไม่ต้องใช้เครื่องมือภายนอก—เพียงโครงการ .NET และไลบรารี Aspose.Words for .NET  

## Prerequisites  

ก่อนเริ่ม, ตรวจสอบว่าคุณมี:  

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า  
* Aspose.Words for .NET เวอร์ชันล่าสุด (ตัวอย่างใช้ 23.12, แต่เวอร์ชัน 22.x+ ใดก็ทำงาน)  
* IDE เช่น Visual Studio 2022 หรือ Visual Studio Code  

โค้ดนี้ทำงานได้บน Windows, macOS, และ Linux เนื่องจาก Aspose.Words ไม่ขึ้นกับแพลตฟอร์ม  

## Step 1: Set up the project and reference Aspose.Words  

1. สร้างโปรเจกต์คอนโซลใหม่:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. เพิ่มแพ็กเกจ NuGet ของ Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. เปิด **Program.cs** และแทนที่เนื้อหาเดิมด้วยโครงสร้างที่แสดงในขั้นตอนต่อไป  

การตั้งค่าโปรเจกต์แบบนี้ทำให้คอมไพเลอร์สามารถค้นหา namespace `Aspose.Words` และ `Aspose.Words.Drawing.Forms` ที่จำเป็นสำหรับคอนโทรลฟอร์มได้  

## Step 2: Initialize a blank document and a DocumentBuilder  

คลาส `Document` แทนไฟล์ Word ทั้งหมด, ส่วน `DocumentBuilder` ให้ API แบบ fluent สำหรับการเพิ่มเนื้อหา  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*ทำไมขั้นตอนนี้สำคัญ* – หากไม่มี `DocumentBuilder` คุณจะไม่สามารถกำหนดตำแหน่งของปุ่มได้อย่างแม่นยำบนหน้า Builder ยังเคารพตำแหน่งเคอร์เซอร์ปัจจุบัน ทำให้แทรกคอนโทรลหลายตัวได้ง่ายในภายหลัง  

## Step 3: Insert the command button OLE control  

Aspose.Words ถือปุ่มคำสั่งเป็นคอนโทรล OLE ชนิด `ControlType.CommandButton` คุณกำหนดตำแหน่งและขนาดด้วย `RectangleF` หน่วยเป็นพอยต์ (1 พอยต์ = 1/72 นิ้ว)  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**จุดสำคัญ**  

* จุดกำเนิดของสี่เหลี่ยม (X, Y) อ้างอิงจากมุมซ้าย‑บนของหน้า  
* การเปลี่ยนค่า `Width` หรือ `Height` จะปรับขนาดการแสดงผลของปุ่ม  
* `InsertForms2OleControl` จะคืนค่าเป็นอ็อบเจกต์ `Forms2OleControl` ที่คุณสามารถกำหนดค่าเพิ่มเติมได้  

## Step 4: Configure the button’s name and caption  

**ชื่อ** (`name`) ใช้โดยเครื่องมือตัวแมโครของ Word เพื่อระบุคอนโทรล, ส่วน **คำบรรยาย** (`caption`) คือข้อความที่ผู้ใช้เห็น  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

หากคุณวางแผนจะเพิ่มแมโคร VBA ในภายหลัง ควรใช้ชื่อที่อธิบายได้ชัดเจน เพราะเครื่องบันทึกแมโครของ Word จะอ้างอิงคุณสมบัตินี้  

## Step 5: (Optional) Save the document and verify the result  

การบันทึกไฟล์ทำให้คุณสามารถเปิดใน Microsoft Word เพื่อตรวจสอบว่าปุ่มปรากฏและทำงานตามที่คาดหวัง  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

เมื่อคุณเปิด *CommandButtonDemo.docx* ใน Word คุณควรเห็นปุ่มที่มีข้อความ **Submit** อยู่ตำแหน่งประมาณ 1.4 นิ้วจากขอบซ้ายและ 2.1 นิ้วจากด้านบนของหน้า การคลิกปุ่มจะไม่มีผลใด ๆ โดยค่าเริ่มต้นเพราะไม่มีแมโครเชื่อมต่อ, แต่คอนโทรลแสดงผลทำงานเต็มที่  

## Step 6: Edge cases and common pitfalls  

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **Button overlaps existing text** | สี่เหลี่ยมอาจตัดกับย่อหน้าที่มีอยู่ ทำให้เลย์เอาต์เสีย | แทรกปุ่มหลังจากเรียก `builder.Writeln()` เพื่อย้ายเคอร์เซอร์ไปบรรทัดใหม่, หรือปรับค่า `Y` |
| **Document opens with a warning** | เวอร์ชัน Word บางรุ่นจะเตือนคอนโทรล OLE ที่ไม่มีโปรแกรมเชื่อมโยง | ตรวจสอบให้แน่ใจว่าชนิดคอนโทรลเป็น `CommandButton`; Word จะมองว่าเป็นฟอร์มมาตรฐานและไม่ต้องการโปรแกรมภายนอก |
| **Running on Linux with headless environment** | ไม่สามารถเปิด Word เพื่อตรวจสอบ UI ได้, แต่ไฟล์ยังคงถูกต้อง | ใช้ unit test เพื่อตรวจสอบคุณสมบัติของคอนโทรล (`commandButton.Name`, `commandButton.Caption`) ว่าถูกตั้งค่าอย่างถูกต้อง |
| **Multiple buttons needed** | ใช้ `DocumentBuilder` เดียวกันโดยไม่ย้ายเคอร์เซอร์จะทำให้ปุ่มซ้อนกัน | เรียก `builder.MoveToDocumentEnd()` หรือปรับค่า `Y` ของสี่เหลี่ยมก่อนแทรกแต่ละครั้ง |

การจัดการกับกรณีเหล่านี้ตั้งแต่ต้นจะช่วยประหยัดเวลาเมื่อขยายโซลูชันเป็นฟอร์มเต็มที่มีหลายสิบคอนโทรล  

## Step 7: Full, runnable example  

ด้านล่างเป็นโปรแกรมที่สมบูรณ์และพร้อมรัน คุณสามารถคัดลอก, วาง, และรันได้โดยไม่ต้องแก้ไข (ยกเว้นการกู้คืน NuGet)  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง**  

เมื่อรันโปรแกรมจะพิมพ์เส้นทางไฟล์คล้ายกับ:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

การเปิด *CommandButtonDemo.docx* ที่สร้างขึ้นจะแสดงปุ่ม **Submit** เพียงปุ่มเดียวที่วางตามพิกัดที่กำหนดในโค้ด ไม่ปรากฏ UI อื่น ๆ ใด ๆ ยืนยันว่ากระบวนการ **add command button programmatically** ทำงานสำเร็จ  

## Conclusion  

ตอนนี้คุณรู้วิธี **add a command button programmatically** ลงในเอกสาร Word ด้วย Aspose.Words, และคุณยังเข้าใจวิธี **create a Word document button** ที่สามารถต่อเชื่อมกับแมโคร VBA หรือเครื่องมืออัตโนมัติอื่น ๆ ได้ กระบวนการประกอบด้วยการเริ่มต้นเอกสาร, แทรกคอนโทรล OLE `CommandButton`, กำหนดคุณสมบัติ, และบันทึกไฟล์  

ต่อจากนี้คุณอาจ:  

* เพิ่มคอนโทรลอื่น ๆ (checkbox, text field) โดยทำซ้ำขั้นตอน 3 พร้อมค่า `ControlType` ที่ต่างกัน  
* แนบแมโคร VBA ให้ปุ่มเพื่อทำงานเช่นบันทึกฟอร์มหรือส่งอีเมล  
* สร้างฟอร์มทั้งหมดแบบไดนามิกโดยวนลูปผ่านคอลเลกชันข้อมูลที่กำหนดฟิลด์  

ลองปรับค่าพิกัดของสี่เหลี่ยมและข้อความบนปุ่มให้สอดคล้องกับการออกแบบ UI ของคุณเอง ขอให้สนุกกับการเขียนโค้ด!  


## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}