---
category: general
date: 2026-07-23
description: สร้างปุ่มเอกสาร Word ด้วย Aspose.Words – คู่มือขั้นตอนการแทรก ActiveX
  CommandButton ลงในไฟล์ .docx
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: th
lastmod: 2026-07-23
og_description: 'สร้างปุ่มเอกสาร Word ด้วย Aspose.Words: เรียนรู้วิธีฝัง ActiveX CommandButton
  ในไฟล์ Word ภายในไม่กี่นาที'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: ปุ่มสร้างเอกสาร Word – คู่มือเต็มของ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: สร้างปุ่มสร้างเอกสาร Word ด้วย Aspose.Words – ตัวอย่างโค้ดเต็ม
url: /th/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างปุ่มเอกสาร Word ด้วย Aspose.Words – คู่มือการเขียนโปรแกรมเต็มรูปแบบ

เคยต้องการ **สร้างปุ่มเอกสาร Word** แต่ไม่แน่ใจว่าจะใช้ API ไหนหรือไม่? คุณไม่ได้อยู่คนเดียว—นักพัฒนาส่วนใหญ่มักเจออุปสรรคเมื่อพยายามฝังคอนโทรลแบบโต้ตอบลงในไฟล์ .docx ข่าวดีคือ? ด้วย Aspose.Words for .NET คุณสามารถแทรก ActiveX CommandButton ที่ทำงานเต็มรูปแบบลงในเอกสาร Word ได้ด้วยเพียงไม่กี่บรรทัดของโค้ด.

ในบทแนะนำนี้ เราจะเดินผ่านกระบวนการทั้งหมด: ตั้งค่าโปรเจกต์, เริ่มต้น `DocumentBuilder`, แทรกปุ่มด้วย `InsertForms2OleControl`, และสุดท้ายบันทึกไฟล์เพื่อให้ Word รู้จักคอนโทรลนั้น. เมื่อเสร็จคุณจะได้ไฟล์ Word ที่พร้อมใช้งานซึ่งมีปุ่มที่คลิกได้—ไม่ต้องทำการเชื่อมต่อ COM ใดๆ

## สิ่งที่คุณต้องเตรียม

- **.NET 6.0** หรือใหม่กว่า (โค้ดนี้ทำงานกับ .NET Framework 4.6+ ด้วย)  
- **Aspose.Words for .NET** NuGet package (เวอร์ชัน 23.9 หรือใหม่กว่า)  
- ความเข้าใจพื้นฐานของ C# (เราจะทำให้ไวยากรณ์เป็นมิตรกับผู้เริ่มต้น)  
- Visual Studio 2022 หรือ IDE ใดก็ได้ที่คุณชอบ  

เท่านี้—ไม่มีการอ้างอิง COM เพิ่มเติม, ไม่มี Office interop, เพียงโค้ดที่จัดการโดย .NET เท่านั้น.

---

## ขั้นตอนที่ 1: ตั้งค่า Aspose.Words เพื่อ **สร้างปุ่มเอกสาร Word**

ก่อนอื่นสุด, เพิ่มแพคเกจ Aspose.Words ลงในโปรเจกต์ของคุณ:

```bash
dotnet add package Aspose.Words
```

หรือ, หากคุณใช้ Visual Studio NuGet UI, ค้นหา “Aspose.Words” แล้วคลิก **Install**. บรรทัดเดียวนี้จะทำให้คุณเข้าถึงคลาส `Document`, `DocumentBuilder`, และเมธอด `InsertForms2OleControl` ที่เราจะใช้ต่อไป.

> **เคล็ดลับ:** คอยอัปเดตแพคเกจ NuGet ของคุณให้เป็นเวอร์ชันล่าสุด; รุ่นใหม่มักจะรวมการแก้ไขบั๊กสำหรับการจัดการ ActiveX.

---

## ขั้นตอนที่ 2: เริ่มต้น **DocumentBuilder** สำหรับ **ActiveX CommandButton**

ตอนนี้เราจะสร้างเอกสาร Word ใหม่และสร้าง `DocumentBuilder`. คิดว่า `DocumentBuilder` เป็นแปรงสีที่ให้คุณวาดเนื้อหาไปบนผ้าใบ.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

สังเกตว่าเรานำเข้า `System.Drawing`—โครงสร้าง `Rectangle` กำหนดตำแหน่งและขนาดของปุ่ม. ที่นี่คือที่ที่ **ActiveX CommandButton** จะอยู่.

---

## ขั้นตอนที่ 3: ใช้ **InsertForms2OleControl** เพื่อ **เพิ่ม CommandButton**

นี่คือหัวใจของบทแนะนำ: การแทรกปุ่มเอง. เมธอด `InsertForms2OleControl` รับอาร์กิวเมนต์สามค่า—ประเภทของคอนโทรล, `Rectangle`, และชื่อ (เป็นออปชั่น). เราจะใช้ `OleControlType.CommandButton` เพื่อระบุคอนโทรลที่ต้องการ.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

การเรียกครั้งเดียวนี้ทำหลายอย่าง:

1. **สร้าง** วัตถุ OLE ภายในไฟล์ Word.  
2. **ลงทะเบียน** เป็น ActiveX CommandButton, ซึ่ง Word จะเรนเดอร์เป็นองค์ประกอบ UI ที่คลิกได้.  
3. **กำหนดตำแหน่ง** ตาม `Rectangle` ที่เราให้.  

หากคุณต้องการเปลี่ยนข้อความแคปชันของปุ่มหรือคุณสมบัติอื่นๆ, คุณสามารถทำได้หลังจากแทรกโดยเข้าถึง `OleFormat` ที่อยู่ภายใต้. สำหรับสถานการณ์ส่วนใหญ่, แคปชันเริ่มต้น (“CommandButton1”) เพียงพอ.

---

## ขั้นตอนที่ 4: บันทึกเอกสาร Word ที่มี **CommandButton**

การบันทึกทำได้ง่าย—แค่ระบุโฟลเดอร์ที่คุณมีสิทธิ์เขียน. ส่วนขยายไฟล์ต้องเป็น `.docx` เพื่อให้ปุ่มคงอยู่หลังการบันทึก.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

เมื่อคุณเปิด `CommandButton.docx` ใน Microsoft Word, คุณจะเห็นปุ่มเล็กๆ ที่มุมซ้ายบนของหน้าแรก. การคลิกมันจะไม่ทำอะไร (ต้องใช้ VBA), แต่คอนโทรลทำงานเต็มรูปแบบและสามารถเชื่อมต่อในภายหลังได้.

> **ทำไมวิธีนี้ถึงได้ผล:** Aspose.Words เขียนสตรีม OLE ลงในแพ็กเกจ DOCX โดยตรง, ข้ามขั้นตอนที่ Word ต้องสร้างคอนโทรลในขณะรันไทม์. สิ่งนี้ทำให้ปุ่มปรากฏตรงตำแหน่งที่คุณวางไว้.

---

## ขั้นตอนที่ 5: ตรวจสอบปุ่มใน Word

เปิดไฟล์ที่สร้างขึ้น:

1. เปิด Microsoft Word.  
2. ไปที่ **File → Open** และเลือก `CommandButton.docx`.  
3. คุณควรเห็นปุ่มสี่เหลี่ยมที่มีป้าย “CommandButton1”.  

หากคุณไม่เห็นปุ่ม, ตรวจสอบให้แน่ใจว่า **Design Mode** ถูกเปิดใช้งาน (Developer → Design Mode). โหมดนี้สลับการแสดงผลภาพของคอนโทรล ActiveX.

---

## ขั้นตอนที่ 6: ตัวเลือกขั้นสูง – ปรับแต่ง **ActiveX CommandButton**

ด้านล่างนี้เป็นการปรับแต่งเล็กน้อยที่อาจเป็นประโยชน์:

| เป้าหมาย | ตัวอย่างโค้ด |
|------|--------------|
| เปลี่ยนแคปชัน | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| ตั้งชื่อแมโคร (ต้องการการสนับสนุนแมโครของ Word) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| ปรับขนาดหลังการแทรก | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

ตัวอย่างโค้ดเหล่านี้แสดงถึงความยืดหยุ่นของ `InsertForms2OleControl`. คุณสามารถฝังคอนโทรล ActiveX อื่นๆ เช่น `CheckBox` หรือ `ListBox` ได้โดยการสลับค่า enum `OleControlType`.

---

## ตัวอย่างการทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มรูปแบบพร้อมคัดลอก‑วางที่ **สร้างปุ่มเอกสาร Word** ตั้งแต่ต้น:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**ผลลัพธ์ที่คาดหวังเมื่อคุณรันโปรแกรม:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

เปิดไฟล์ที่ได้และคุณจะเห็นปุ่มอยู่ตรงตำแหน่งที่โค้ดกำหนดไว้.

---

## ข้อผิดพลาดทั่วไป & วิธีหลีกเลี่ยง

- **Missing `System.Drawing` reference** – โครงสร้าง `Rectangle` อยู่ในนั้น; หากไม่มีคอมไพเลอร์จะแจ้งข้อผิดพลาด.  
- **Using an older Aspose.Words version** – รุ่นแรกๆ ไม่ได้รองรับ `InsertForms2OleControl` อย่างเต็มที่. ควรอัปเกรดเป็นแพคเกจที่เสถียรล่าสุด.  
- **Saving as `.doc` instead of `.docx`** – สตรีม OLE จะถูกตัดออกในรูปแบบไบนารีเก่า, ทำให้ปุ่มหายไป.  
- **Running on a headless server without Word installed** – ปุ่มยังคงอยู่ในไฟล์, แต่คุณไม่สามารถดูตัวอย่างได้หากไม่มี Word. สิ่งนี้ถือว่าปกติสำหรับ pipeline การสร้างอัตโนมัติ.

---

## ขั้นตอนต่อไป – ขยายการทำงานของ **สร้างปุ่มเอกสาร Word**

เมื่อคุณเชี่ยวชาญพื้นฐานแล้ว, พิจารณาแนวคิดระดับต่อไปเหล่านี้:

- **Attach VBA macros** to the button for custom business logic.  
- **Generate multiple buttons** in a loop for dynamic forms.  
- **Combine with Aspose.PDF** to export the same document to PDF while preserving the visual layout (the button becomes a static image in PDF).  
- **

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ.

- [สร้างเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือขั้นตอน](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [แทรกภาพ Inline ในเอกสาร Word ด้วย Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}