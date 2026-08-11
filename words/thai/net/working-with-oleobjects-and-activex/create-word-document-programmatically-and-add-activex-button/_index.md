---
category: general
date: 2026-08-10
description: สร้างเอกสาร Word ด้วยโปรแกรมโดยใช้ Aspose.Words จากนั้นเพิ่มปุ่มควบคุม
  ActiveX ใน Word แทรกปุ่มคำสั่ง ActiveX เพียงไม่กี่นาที
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: th
lastmod: 2026-08-10
og_description: สร้างเอกสาร Word ด้วยโปรแกรมโดยใช้ Aspose.Words จากนั้นเพิ่มปุ่มควบคุม
  ActiveX ใน Word เรียนรู้วิธีแทรกปุ่มคำสั่ง ActiveX อย่างรวดเร็ว
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: สร้างเอกสาร Word ด้วยโปรแกรม – เพิ่มปุ่ม ActiveX ใน C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: สร้างเอกสาร Word อย่างอัตโนมัติและเพิ่มปุ่ม ActiveX
url: /th/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word อย่างโปรแกรมและเพิ่มปุ่ม ActiveX

หากคุณต้องการ **สร้างเอกสาร Word อย่างโปรแกรม**, คู่มือนี้จะพาคุณผ่านกระบวนการทั้งหมดด้วย Aspose.Words for .NET. คุณจะได้เรียนรู้วิธี **เพิ่มองค์ประกอบควบคุม ActiveX ใน Word** และ **แทรกวัตถุปุ่มคำสั่ง ActiveX** ในตัวอย่างเดียวที่สมบูรณ์แบบ

การสร้างไฟล์ Word จากโค้ดจะลบขั้นตอนการเปิด Microsoft Word ด้วยตนเอง, ทำให้คุณสามารถสร้างรายงาน, ใบแจ้งหนี้, หรือสัญญาที่ขับเคลื่อนด้วยข้อมูลโดยอัตโนมัติ. เมื่อจบบทเรียนนี้คุณจะมีแอปคอนโซล C# ที่พร้อมรันซึ่งสร้างไฟล์ `.docx` ที่มีปุ่ม ActiveX CommandButton แบบโต้ตอบ

## ข้อกำหนดเบื้องต้น

ก่อนเริ่ม, ตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+)
* Visual Studio 2022 หรือ IDE ใด ๆ ที่รองรับการพัฒนา .NET
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (คุณสามารถใช้คีย์ทดลองฟรีสำหรับการทดสอบ)
* ความคุ้นเคยพื้นฐานกับไวยากรณ์ C# และแนวคิดของคอมโพเนนท์ COM/ActiveX

> **เคล็ดลับ:** หากคุณวางแผนจะแจกจ่ายเอกสารที่สร้างให้กับผู้ใช้ที่ไม่มี Word ติดตั้ง, ฝังไฟล์รันไทม์ของคอนโทรล ActiveX ไว้เคียงกับไฟล์ `.docx` หรือให้เทมเพลตที่เปิดใช้งานมาโคร

## สร้างเอกสาร Word อย่างโปรแกรม – การตั้งค่าเริ่มต้น

ขั้นแรก, เพิ่มแพคเกจ Aspose.Words NuGet ไปยังโปรเจคของคุณ:

```bash
dotnet add package Aspose.Words
```

จากนั้นสร้างโปรเจคคอนโซลใหม่ (หากคุณยังไม่มี):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

เปิดไฟล์ `Program.cs` ที่สร้างขึ้น – เราจะเปลี่ยนเนื้อหาของมันด้วยโซลูชันเต็มด้านล่าง

## ขั้นตอนที่ 1: นำเข้า namespace และกำหนดค่าใบอนุญาต

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*ทำไมสิ่งนี้ถึงสำคัญ*: การนำเข้า `Aspose.Words.Drawing` จะทำให้คุณเข้าถึง `Forms2OleControl` ซึ่งเป็นคลาสที่แสดงคอนโทรล ActiveX ภายในเอกสาร Word. การตั้งค่าใบอนุญาตตั้งแต่ต้นจะป้องกันคำเตือนขณะรันในสภาพแวดล้อมการผลิต

## ขั้นตอนที่ 2: สร้างเอกสารเปล่าและ DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

อ็อบเจกต์ `Document` คือการแสดงผลของไฟล์ `.docx` ในหน่วยความจำ. `DocumentBuilder` ทำงานคล้ายเคอร์เซอร์ที่คุณย้ายไปรอบเอกสารเพื่อแทรกองค์ประกอบ

## ขั้นตอนที่ 3: แทรกคอนโทรล ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` สร้างอ็อบเจกต์ OLE ที่ Word พิจารณาเป็นคอนโทรล ActiveX. ระบบพิกัดใช้หน่วยจุด (1 point = 1/72 นิ้ว), ซึ่งสอดคล้องกับเอนจินการจัดวางของ Word

## ขั้นตอนที่ 4: ตั้งค่าคำบรรยายของปุ่มและคุณสมบัติเสริม

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

การตั้งค่า property `Caption` เป็นวิธีที่พบบ่อยที่สุดในการตั้งชื่อปุ่ม. หากคุณต้องการให้ปุ่มทำงานแมโคร VBA, กำหนดชื่อแมโครให้กับ `OnAction`. บทเรียนนี้เน้นส่วนที่เป็นภาพ; การรวมแมโครจะอธิบายในส่วน “ขั้นตอนต่อไป”

## ขั้นตอนที่ 5: บันทึกเอกสาร

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

เมื่อคุณรันโปรแกรม, คุณจะเห็นข้อความในคอนโซลยืนยันว่าไฟล์ `ActiveX_CommandButton.docx` ถูกเขียนลงดิสก์แล้ว

### โค้ดต้นฉบับเต็ม (พร้อมคัดลอก‑วาง)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

การรันสคริปต์นี้จะสร้างไฟล์ Word ที่มี **ปุ่มคำสั่ง ActiveX** ที่คลิกได้. เปิดไฟล์ใน Microsoft Word, สลับไปที่ **Design Mode** (แท็บ Developer → Design Mode), แล้วคุณจะเห็นปุ่มแสดงผลตรงตำแหน่งที่คุณวางไว้

## ขั้นตอนที่ 6: ตรวจสอบผลลัพธ์

1. เปิดไฟล์ `ActiveX_CommandButton.docx` ใน Microsoft Word.  
2. เปิดแท็บ **Developer** หากไม่ปรากฏ (`File → Options → Customize Ribbon → check Developer`).  
3. คลิก **Design Mode**. ปุ่มควรปรากฏพร้อมป้าย “Submit”.  
4. หากคุณได้เพิ่มแมโคร `OnAction`, คลิกปุ่มขณะ Design Mode ปิดอยู่เพื่อเรียกแมโคร.

หากปุ่มไม่แสดง, ตรวจสอบให้แน่ใจว่าการตั้งค่าความปลอดภัยของ Word อนุญาตคอนโทรล ActiveX (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## คำถามทั่วไปและกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ฉันสามารถแทรกประเภท ActiveX อื่นได้หรือไม่?** | ได้. enum `Forms2OleControlType` มีค่า `CheckBox`, `OptionButton`, `ComboBox` เป็นต้น. แทนที่ `CommandButton` ด้วยค่า enum ที่ต้องการ |

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการใช้งานทางเลือกในโปรเจคของคุณ.

- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [สร้างเอกสาร Word พร้อม Header และ Footer ด้วย Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [แทรกภาพ Inline ในเอกสาร Word ด้วย Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}