---
category: general
date: 2026-08-04
description: สร้างเอกสาร Word อย่างอัตโนมัติด้วย C#. เรียนรู้วิธีเพิ่มปุ่มคำสั่งด้วย
  Aspose.Words อย่างเป็นโปรแกรมในไม่กี่ขั้นตอน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: th
lastmod: 2026-08-04
og_description: สร้างเอกสาร Word อย่างอัตโนมัติด้วย Aspose.Words คู่มือนี้แสดงวิธีการเพิ่มปุ่มคำสั่งอย่างอัตโนมัติ
  ตั้งค่าและบันทึกไฟล์
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: สร้างเอกสาร Word ด้วยโปรแกรม – บทเรียน C# ฉบับเต็ม
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: สร้างเอกสาร Word อย่างอัตโนมัติ – คู่มือขั้นตอนต่อขั้นตอน
url: /th/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word ด้วยโปรแกรม – คำแนะนำเต็ม C#

หากคุณต้องการ **สร้างเอกสาร Word ด้วยโปรแกรม**, คู่มือนี้จะแสดงวิธีทำอย่างละเอียดด้วย Aspose.Words for .NET เพียงไม่กี่บรรทัดของ C# คุณก็สามารถสร้างไฟล์ `.docx` เปล่า, **เพิ่มปุ่มคำสั่ง** (command button) อย่างโปรแกรมเมติก, ตั้งค่าคุณสมบัติต่าง ๆ และบันทึกผลลัพธ์ได้  

ขั้นตอนต่อไปนี้ครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโปรเจกต์จนถึงการจัดการกรณีขอบ, เพื่อให้คุณคัดลอกโค้ดไปใช้ในแอปพลิเคชันของคุณและรันได้โดยไม่ต้องแก้ไขใด ๆ

## สิ่งที่คุณจะได้เรียนรู้

เมื่อจบบทเรียนนี้คุณจะสามารถ:

* สร้างเอกสาร Word ใหม่โดยทำงานทั้งหมดในหน่วยความจำ  
* **เพิ่มปุ่มคำสั่ง** OLE อย่างโปรแกรมเมติกในตำแหน่งและขนาดใดก็ได้  
* ตั้งค่าคำบรรยายของปุ่ม, ชื่อภายใน, และคุณสมบัติ OLE อื่น ๆ  
* บันทึกเอกสารที่สร้างขึ้นไปยังดิสก์หรือสตรีมเพื่อการประมวลผลต่อไป

### ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+)  
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือเวอร์ชันทดลองฟรี)  
* ความคุ้นเคยพื้นฐานกับ C# และ Visual Studio (หรือ IDE ที่คุณเลือก)  

> **เคล็ดลับ:** หากคุณรันตัวอย่างโดยไม่มีใบอนุญาต, Aspose.Words จะใส่น้ำหนักประเมินผลขนาดเล็กบนหน้าแรก

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า namespace ที่จำเป็น

สร้าง Console App ใหม่ (หรือผสานเข้ากับบริการที่มีอยู่) และเพิ่มแพคเกจ NuGet ของ Aspose.Words:

```bash
dotnet add package Aspose.Words
```

จากนั้นใส่ namespace ที่จำเป็นไว้ด้านบนของไฟล์ `.cs` ของคุณ:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

การนำเข้าตรงนี้ทำให้คุณเข้าถึง `Document`, `DocumentBuilder`, `Forms2OleControl` และโครงสร้าง `RectangleF` ที่ใช้สำหรับกำหนดตำแหน่ง

## ขั้นตอนที่ 2: เริ่มต้นเอกสาร Word ใหม่

การดำเนินการแรกในกระบวนการ **สร้างเอกสาร Word ด้วยโปรแกรม** คือการสร้างอ็อบเจกต์ `Document`. อ็อบเจกต์นี้อยู่ในหน่วยความจำจนกว่าคุณจะบันทึกอย่างชัดเจน

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` ทำหน้าที่เหมือนเคอร์เซอร์ที่ติดตามตำแหน่งขององค์ประกอบถัดไป การใช้มันช่วยให้โค้ดกระชับและทำงานคล้ายกับการพิมพ์โดยตรงใน Word

## ขั้นตอนที่ 3: แทรกปุ่มคำสั่ง OLE

Aspose.Words มีเมธอด `InsertForms2OleControl` เพื่อฝังอ็อบเจกต์ OLE เช่น ปุ่มคำสั่ง, กล่องตรวจสอบ, หรือคอมโบบ็อกซ์ เมธอดนี้ต้องการอาร์กิวเมนต์สามค่า:

1. ค่า enum `ControlType` (ที่นี่ใช้ `CommandButton`)  
2. `RectangleF` ที่กำหนดตำแหน่ง X‑Y และความกว้าง‑สูงของคอนโทรล (หน่วยเป็นพอยต์, 72 pt = 1 inch)  
3. (ไม่บังคับ) คุณสมบัติ OLE เพิ่มเติม (ไม่จำเป็นสำหรับปุ่มพื้นฐาน)

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **ทำไมวิธีนี้ถึงใช้ได้:** `InsertForms2OleControl` สร้างคอนเทนเนอร์ OLE ในเอกสารและคืนค่าอ็อบเจกต์ `Forms2OleControl`. อ็อบเจกต์นี้ให้คุณจัดการกับอ็อบเจกต์ OLE ด้านล่าง (ปุ่มจริง) โดยไม่ต้องทำงานกับ COM ระดับต่ำ

## ขั้นตอนที่ 4: ตั้งค่าคำบรรยายและชื่อภายในของปุ่ม

หลังจากแทรกแล้ว, คุณมักต้องการกำหนดข้อความที่ผู้ใช้เห็นบนปุ่มและตัวระบุภายในที่แมโครหรือแอด‑อินของคุณจะอ้างอิงต่อไป

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` คือข้อความที่แสดงบนปุ่มใน UI ของ Word  
* `Name` คือชื่อโปรแกรมเมติกที่ใช้โดย VBA หรือสคริปต์อัตโนมัติภายนอก

### ตัวเลือก: ผูกแมโครกับปุ่ม

หากคุณต้องการให้แมโคร VBA ทำงานเมื่อคลิกปุ่ม, สามารถแนบชื่อแมโครได้ดังนี้:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **กรณีขอบ:** หากเอกสารเป้าหมายเปิดบนเครื่องที่ไม่มีแมโคร, Word จะแสดงคำเตือนด้านความปลอดภัย. ควรเซ็นชื่อแมโครหรือแจ้งผู้ใช้เกี่ยวกับการตั้งค่าที่จำเป็น

## ขั้นตอนที่ 5: บันทึกเอกสาร

คุณสามารถบันทึกไฟล์ลงดิสก์, `MemoryStream`, หรือส่งโดยตรงเป็น response ใน Web API วิธีที่ง่ายที่สุดสำหรับการสาธิตในคอนโซลคือบันทึกลงโฟลเดอร์ท้องถิ่น:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

ไฟล์ `.docx` ที่ได้จะเปิดใน Microsoft Word พร้อมปุ่มคำสั่งที่ทำงานและแสดงข้อความ “Click Me”. การคลิกปุ่มจะเรียกแมโครที่แนบ (ถ้ามี) หรือแสดงข้อความเริ่มต้นตามค่าเริ่มต้น

## ตัวอย่างทำงานเต็มรูปแบบ

คัดลอกโปรแกรมต่อไปนี้ไปยัง `Program.cs` แล้วรัน มันจะแสดงกระบวนการ **สร้างเอกสาร Word ด้วยโปรแกรม** ทั้งหมดรวมถึงการจัดการข้อผิดพลาด

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิด `CommandButton.docx` ใน Word จะเห็นปุ่มที่มีข้อความ “Click Me”. การวางเมาส์เหนือปุ่มจะแสดงชื่อ `cmdClickMe` ในแผงคุณสมบัติ

## คำถามที่พบบ่อยและการแก้ไขปัญหา

| Question | Answer |
|----------|--------|
| *Can I add the button to an existing document?* | Yes. Load the file with `new Document("Existing.docx")`, then use the same `InsertForms2OleControl` call. |
| *What units does `RectangleF` use?* | Points (1 inch = 72 pt). Adjust values to position the button precisely. |
| *Will the button work on Word for Mac?* | OLE controls are supported on Windows Word only. On Mac the button appears as a static image. |
| *Do I need a license for production use?* | A commercial license removes evaluation watermarks and unlocks full functionality. |
| *How do I change the button’s size after insertion?* | Modify `commandButton.Width` and `commandButton.Height` or re‑insert with a new `RectangleF`. |

## ขยายการใช้งาน

ตอนนี้คุณรู้วิธี **เพิ่มปุ่มคำสั่ง** อย่างโปรแกรมเมติกแล้ว, คุณสามารถสำรวจหัวข้อที่เกี่ยวข้องต่อไปนี้:

* **แทรกคอนโทรลฟอร์มอื่น** – ใช้ `ControlType.CheckBox`, `ControlType.OptionButton` ฯลฯ (ครอบคลุมคีย์เวิร์ดรอง *Aspose.Words InsertForms2OleControl*)  
* **เติมข้อมูลแบบไดนามิกลงในเอกสาร** – ผสานข้อมูลจากฐานข้อมูลเข้าสู่ตารางหรือฟิลด์เมล‑เมิร์จ  
* **ส่งออกเป็น PDF** – หลังจากเพิ่มปุ่มแล้ว, เรียก `doc.Save("output.pdf", SaveFormat.Pdf)` เพื่อสร้างไฟล์ PDF (เกี่ยวข้องกับ *C# Word automation*)  

## สรุป

คุณมีรูปแบบครบถ้วนและพร้อมใช้งานสำหรับ **สร้างเอกสาร Word ด้วยโปรแกรม** และ **เพิ่มปุ่มคำสั่ง** อย่างโปรแกรมเมติกโดยใช้ Aspose.Words for .NET บทเรียนนี้ครอบคลุมการตั้งค่าโปรเจกต์, การเริ่มต้นเอกสาร, การแทรกปุ่ม OLE, การกำหนดคุณสมบัติ, และการบันทึกไฟล์ คุณสามารถปรับโค้ดเพื่อแทรกคอนโทรลฟอร์มอื่น, แนบแมโคร, หรือรวมโลจิกนี้เข้าในเว็บเซอร์วิสหรืองานแบ็กกราวด์ได้ตามต้องการ  

ขอให้สนุกกับการเขียนโค้ดและการอัตโนมัติเอกสาร Word!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}