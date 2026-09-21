---
category: general
date: 2026-09-21
description: เรียนรู้วิธีสร้างปุ่มคำสั่ง ActiveX ในเอกสาร Word ด้วย Aspose.Words และ
  C# คู่มือแบบขั้นตอน‑ต่อ‑ขั้นตอนครอบคลุมการแทรก การจัดตำแหน่ง และการบันทึก
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: th
lastmod: 2026-09-21
og_description: สร้างปุ่มคำสั่ง ActiveX ในเอกสาร Word ด้วย C# และ Aspose.Words. ทำตามบทเรียนฉบับสมบูรณ์นี้เพื่อแทรก,
  กำหนดตำแหน่งและบันทึกปุ่มโดยอัตโนมัติ.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: สร้างปุ่มคำสั่ง ActiveX ใน Word ด้วย C# – คู่มือเต็ม
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: วิธีสร้างปุ่มคำสั่ง ActiveX ใน Word ด้วย C#
url: /th/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างปุ่มคำสั่ง ActiveX ใน Word ด้วย C#

หากคุณต้องการ **สร้างปุ่มคำสั่ง ActiveX** ภายในไฟล์ Word คำแนะนำนี้จะแสดงขั้นตอนที่แน่นอน โดยใช้ Aspose.Words for .NET คุณสามารถเพิ่ม, กำหนดตำแหน่ง, และตั้งค่าปุ่มได้ทั้งหมดจากโค้ด C#

การแทรกปุ่ม ActiveX ด้วยโปรแกรมช่วยลดงาน UI แบบแมนนวลและทำให้การสร้างเอกสารอัตโนมัติสำหรับแบบฟอร์ม, รายงาน, หรือเทมเพลตแบบโต้ตอบเป็นไปได้ ในบทเรียนนี้คุณจะได้เรียนรู้วิธีใช้ **DocumentBuilder**, วิธี **InsertForms2OleControl**, และคุณสมบัติเกี่ยวข้องเพื่อสร้างปุ่มที่ทำงานเต็มรูปแบบ

## สิ่งที่คุณต้องการ

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+)
* Aspose.Words for .NET (แพ็กเกจ NuGet `Aspose.Words`)
* IDE เช่น Visual Studio 2022 หรือ VS Code
* ความรู้พื้นฐานเกี่ยวกับ C# และแนวคิดเอกสาร Word

ไม่จำเป็นต้องติดตั้ง Office เพิ่มเติม เพราะ Aspose.Words ทำงานอิสระจาก Microsoft Word

## ขั้นตอน 1: ตั้งค่าโครงการ C#

สร้างโปรเจกต์คอนโซลใหม่และเพิ่มแพ็กเกจ Aspose.Words

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

ไลบรารี `Aspose.Words` มีคลาส **DocumentBuilder** ที่เราจะใช้เพื่อจัดการเอกสาร

## ขั้นตอน 2: เริ่มต้นเอกสารและ builder

บล็อกโค้ดแรกสร้างเอกสารเปล่าและอินสแตนซ์ของ `DocumentBuilder` วัตถุนี้เป็นจุดเริ่มต้นสำหรับการทำงานทั้งหมดกับ Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**ทำไมเรื่องนี้ถึงสำคัญ:** `DocumentBuilder` รักษาตำแหน่งเคอร์เซอร์ปัจจุบันไว้ ดังนั้นการแทรกใด ๆ ที่ตามมาจะปรากฏตรงตำแหน่งที่คุณวางเคอร์เซอร์

## ขั้นตอน 3: แทรกปุ่มคำสั่ง ActiveX

วิธี **InsertForms2OleControl** สร้างคอนโทรล ActiveX ตามประเภทที่ระบุ ที่นี่เราขอ `CommandButton` และกำหนดขนาดเป็นจุด (200 × 30 pt)

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**คำอธิบาย:**  
* `OleControlType.CommandButton` บอก Aspose.Words ให้สร้างปุ่มแทนคอนโทรลประเภทอื่น  
* วิธีนี้คืนค่าออบเจ็กต์ `Forms2OleControl` ซึ่งเปิดเผยฟิลด์การกำหนดตำแหน่งและคุณสมบัติต่าง ๆ

## ขั้นตอน 4: กำหนดตำแหน่งปุ่มและตั้งค่าคุณสมบัติ

หลังจากแทรกแล้ว คุณสามารถย้ายปุ่มไปยังตำแหน่งใดก็ได้บนหน้าและตั้งชื่อโปรแกรมและคำอธิบายที่มองเห็นได้

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**เคล็ดลับ:** ระบบพิกัดเริ่มจากมุมซ้าย‑บนของหน้า ปรับค่า `Left` และ `Top` เพื่อให้ปุ่มจัดแนวกับฟิลด์ฟอร์มอื่น ๆ

## ขั้นตอน 5: บันทึกเอกสาร

สุดท้าย เขียนเอกสารลงดิสก์ ไฟล์จะมีปุ่ม ActiveX พร้อมใช้งานใน Microsoft Word ซึ่งปุ่มจะทำงานแบบโต้ตอบ

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

เมื่อคุณเปิด `ActiveXCommandButton.docx` ใน Word คุณจะเห็นปุ่มที่มีข้อความ **Submit** อยู่ในตำแหน่งที่กำหนด การคลิกปุ่มใน Word จะเรียกพฤติกรรมปุ่มคำสั่งเริ่มต้น (คุณสามารถปรับแต่งต่อด้วย VBA หรือ Add‑ins ของ Word)

## ตัวอย่างสมบูรณ์ที่สามารถรันได้

รวมทุกส่วนเข้าด้วยกันจะได้โปรแกรมอิสระที่คุณสามารถคัดลอก, วาง, และรันได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** คอนโซลจะแสดงข้อความ *“Document created successfully.”* และโฟลเดอร์จะมีไฟล์ `ActiveXCommandButton.docx` เปิดไฟล์ใน Microsoft Word จะเห็นปุ่ม **Submit** ที่คลิกได้ อยู่ห่างจากขอบซ้าย 100 pt และจากขอบบน 150 pt

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|---------|
| ปุ่มปรากฏนอกหน้า | ค่า `Left`/`Top` เกินขนาดหน้ากระดาษ | ใช้ `doc.FirstSection.PageSetup.PageWidth` และ `PageHeight` เพื่อคำนวณพิกัดที่ปลอดภัย |
| ปุ่มไม่แสดงใน Word | เอกสารบันทึกในรูปแบบที่ลบคอนโทรล ActiveX (เช่น `.txt`) | บันทึกเสมอเป็น `.docx` หรือ `.doc` |
| Runtime error `ArgumentOutOfRangeException` | ความกว้างหรือความสูงตั้งเป็นศูนย์หรือค่าลบ | ตรวจสอบให้แน่ใจว่าขนาดที่ส่งให้ `InsertForms2OleControl` เป็นจำนวนบวก |

## ขยายการใช้งาน

คุณสามารถปรับแต่งปุ่มเพิ่มเติมโดยตั้งค่าคุณสมบัติเช่น `Enabled`, `Visible` หรือผูกแมโครผ่าน VBA คลาส **Forms2OleControl** ยังให้คุณแทรกคอนโทรล ActiveX อื่น ๆ เช่น กล่องกาเครื่องหมาย (`OleControlType.CheckBox`) หรือคอมโบบ็อกซ์ (`OleControlType.ComboBox`)

หากต้องการสร้างหลายปุ่มในลูป ให้ห่อหุ้มตรรกะการแทรกในเมธอดช่วยเหลือ:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## สรุป

คุณได้เรียนรู้วิธี **สร้างปุ่มคำสั่ง ActiveX** ในเอกสาร Word ด้วย C# และ Aspose.Words บทเรียนครอบคลุมการตั้งค่าโครงการ, การแทรกปุ่มด้วย `InsertForms2OleControl`, การกำหนดตำแหน่ง, และการบันทึกไฟล์สุดท้าย ด้วยพื้นฐานนี้คุณสามารถทำอัตโนมัติแบบฟอร์มที่ซับซ้อน, ฝังคอนโทรลโต้ตอบ, และผสานเอกสาร Word เข้ากับโซลูชัน .NET ขนาดใหญ่ได้

ต่อไปสำรวจหัวข้อที่เกี่ยวข้อง เช่น ฟิลด์ฟอร์ม **Aspose.Words ActiveX**, การจัดรูปแบบขั้นสูงด้วย **C# DocumentBuilder**, หรือการเพิ่ม **ActiveX control in Word** แบบโปรแกรมเมติกสำหรับกล่องกาเครื่องหมายและรายการดรอป‑ดาวน์ ทดลองปรับพิกัดและขนาดต่าง ๆ เพื่อให้เข้ากับการออกแบบของคุณเอง ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณเอง

- [สร้างเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [สร้างเอกสาร Word พร้อมตารางโดยใช้ Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}