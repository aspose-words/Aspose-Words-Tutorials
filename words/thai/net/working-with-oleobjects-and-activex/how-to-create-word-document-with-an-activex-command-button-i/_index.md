---
category: general
date: 2026-09-05
description: สร้างเอกสาร Word ด้วย Aspose.Words C# และเรียนรู้วิธีแทรกปุ่มคำสั่ง ActiveX
  ตั้งขนาดปุ่ม และเพิ่มฟังก์ชันการทำงานแบบโต้ตอบของปุ่ม
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: th
lastmod: 2026-09-05
og_description: สร้างเอกสาร Word ด้วย C# และแทรกปุ่มคำสั่ง ActiveX บทเรียนนี้แสดงวิธีตั้งค่าขนาดปุ่มและเพิ่มคุณลักษณะปุ่มเชิงโต้ตอบ
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: สร้างเอกสาร Word ด้วยปุ่มคำสั่ง ActiveX ใน C# – คู่มือทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: วิธีสร้างเอกสาร Word พร้อมปุ่มคำสั่ง ActiveX ใน C#
url: /th/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างเอกสาร Word ด้วยปุ่มคำสั่ง ActiveX ใน C#

หากคุณต้องการ **สร้างเอกสาร Word** ด้วยโปรแกรมและฝังองค์ประกอบ UI ที่คลิกได้ คู่มือนี้จะแสดงวิธีทำอย่างละเอียด โดยใช้ Aspose.Words for .NET คุณสามารถ **สร้างเอกสาร Word**, **เพิ่มปุ่มคำสั่ง**, และควบคุมลักษณะของมัน—ทั้งหมดโดยไม่ต้องเปิด Microsoft Word.

คุณจะได้เรียนรู้ **วิธีแทรกคอนโทรล ActiveX**, **ตั้งขนาดปุ่ม**, และทำให้ปุ่มทำงานเหมือนส่วนประกอบ UI แบบโต้ตอบ ไม่จำเป็นต้องมีประสบการณ์กับ COM หรือ VBA มาก่อน; เพียงแค่สภาพแวดล้อมการพัฒนา .NET และไลบรารี Aspose.Words.

## สิ่งที่คุณจะได้ทำ

* **สร้างเอกสาร Word** ตั้งแต่ต้นด้วย C#.
* **แทรกปุ่มคำสั่ง ActiveX** (คอนโทรล “Click Me” แบบคลาสสิก).
* **ตั้งขนาดปุ่ม** และตำแหน่งอย่างแม่นยำ.
* เพิ่มตรรกะ **ปุ่มโต้ตอบ** อย่างง่าย (เช่น ตัวแทนแมโคร) ตามต้องการ.
* บันทึกไฟล์เป็น `.docx` ที่สามารถเปิดใน Microsoft Word หรือโปรแกรมดูที่เข้ากันได้อื่น ๆ.

### ข้อกำหนดเบื้องต้น

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 หรือใหม่กว่า | ให้ runtime สำหรับโค้ด C#. |
| Aspose.Words for .NET (เวอร์ชันล่าสุด) | จัดเตรียม API `Document`, `DocumentBuilder`, และ `Forms2OleControl` ที่ใช้ในตัวอย่าง. |
| Visual Studio 2022 (หรือ IDE C# ใดก็ได้) | ทำให้คอมไพล์และรันตัวอย่างได้ง่าย. |
| ความรู้พื้นฐาน C# | จำเป็นสำหรับเข้าใจการไหลของโค้ด. |

> **เคล็ดลับ:** หากคุณใช้เวอร์ชันทดลองของ Aspose.Words อย่าลืมตั้งค่าไลเซนส์ก่อนรันโค้ดเพื่อหลีกเลี่ยงลายน้ำการประเมินผล.

## วิธีสร้างเอกสาร Word – กระบวนการทำงานโดยรวม

กระบวนการประกอบด้วยสี่ขั้นตอนหลัก:

1. **เริ่มต้นเอกสารใหม่** และ `DocumentBuilder` เพื่อแก้ไขมัน.  
2. **แทรกปุ่มคำสั่ง ActiveX** ด้วย `InsertForms2OleControl`.  
3. **กำหนดค่าปุ่ม** – คำบรรยาย, ขนาด, และตำแหน่ง.  
4. **บันทึก** เอกสารลงดิสก์.

![เอกสาร Word ที่มีปุ่ม ActiveX](/images/activex-button.png "Screenshot of a Word document that contains an ActiveX command button created with C#")

## วิธีแทรกปุ่มคำสั่ง ActiveX

ส่วน **วิธีแทรก activex** เริ่มต้นด้วยเมธอด `InsertForms2OleControl` เมธอดนี้สร้างคอนโทรลแบบ COM ที่ Word ถือเป็นอ็อบเจ็กต์ ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**ทำไมวิธีนี้ถึงได้ผล:** `OleControlType.CommandButton` บอก Aspose.Words ให้สร้างปุ่มสไตล์ VB แบบคลาสสิก ขนาดและตำแหน่งระบุเป็นจุด (1 point = 1/72 นิ้ว) ซึ่งให้การควบคุมการจัดวางอย่างแม่นยำ.

## วิธีเพิ่มปุ่มคำสั่งและตั้งขนาดปุ่ม

หลังจากแทรกคอนโทรลแล้ว คุณสามารถปรับคุณสมบัติดูของมันได้ ขั้นตอน **เพิ่มปุ่มคำสั่ง** ยังครอบคลุม **การตั้งขนาดปุ่ม** ด้วย.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Explanation:**  

* `Caption` คือข้อความที่แสดงบนปุ่ม.  
* `Width` และ `Height` ให้คุณ **ตั้งขนาดปุ่ม** หลังจากแทรกครั้งแรก—มีประโยชน์เมื่อขนาดขึ้นอยู่กับข้อมูลที่รันเวลา.  
* `Left` และ `Top` ย้ายตำแหน่งคอนโทรลโดยไม่ต้องสร้างเอกสารใหม่.

> **ข้อผิดพลาดทั่วไป:** การลืมใช้หน่วยจุดแทนพิกเซลจะทำให้ปุ่มแสดงขนาดเล็กหรือใหญ่เกินไป ควรแปลงค่าพิกเซล (`px * 72 / DPI`) เสมอหากเริ่มจากการวัดบนหน้าจอ.

## วิธีเพิ่มปุ่มโต้ตอบ (ทางเลือก)

ActiveX button สามารถเรียกใช้แมโครเมื่อคลิกได้ แต่การฝังโค้ด VBA จาก C# อยู่เหนือขอบเขตของกระบวนการ Aspose.Words อย่างเดียว ดังนั้นคุณสามารถเพิ่มคุณสมบัติ placeholder ที่ Word จะรับรู้เป็นชื่อแมโครได้แทน.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

เมื่อผู้ใช้เปิดไฟล์ `.docx` ที่สร้างขึ้นใน Word การคลิกปุ่มจะพยายามรัน `MyMacroName` หากแมโครไม่มีอยู่ Word จะเสนอให้ผู้ใช้สร้างมันขึ้นมา.

**ทำไมคุณอาจใช้วิธีนี้:** สำหรับฟอร์มองค์กรที่แมโครทำการกรอกข้อมูล ฟิลด์ต่าง ๆ โค้ด C# เพียงแค่วางปุ่ม; ส่วนตรรกะของแมโครอยู่ในโปรเจกต์ VBA ของเอกสาร.

## บันทึกเอกสารและตรวจสอบผลลัพธ์

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**ผลลัพธ์ที่คาดหวัง:** การเปิด `CommandButton.docx` ใน Microsoft Word จะเห็นปุ่มที่มีข้อความ **Click Me** อยู่ห่างจากขอบซ้าย 100 pts และจากขอบบน 120 pts ขนาดของปุ่มคือ **200 pts × 80 pts** การคลิกปุ่มจะเรียกใช้ placeholder ของแมโคร (ถ้ามี).

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่ทำงานได้ครบถ้วนซึ่งรวมทุกขั้นตอนเข้าด้วยกัน คัดลอกไปยังโครงการ Console App ใหม่, เพิ่มแพคเกจ NuGet ของ Aspose.Words, แล้วรัน.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

รันโปรแกรมแล้วเปิดไฟล์ที่สร้างขึ้น คุณจะเห็น **ปุ่มโต้ตอบ** พร้อมสำหรับการปรับแต่งต่อไป.

## คำถามที่พบบ่อย

| Question | Answer |
|----------|--------|
| **Does this work with .NET Core?** | Yes. Aspose.Words supports .NET Standard, so the same code runs on .NET 5/6/7. |
| **Can I use other ActiveX controls (e.g., CheckBox)?** | Absolutely. Replace `OleControlType.CommandButton` with `OleControlType.CheckBox`, `OleControlType.OptionButton`, etc. |
| **What if I need a larger button on a landscape page?** | Adjust the `Width`, `Height`, `Left`, and `Top` properties proportionally. Remember that points remain the same regardless of page orientation. |
| **Is a macro required for the button to be clickable?** | No. The button is fully functional as a UI element; a macro only adds custom behavior when clicked. |

## สรุป

ตอนนี้คุณรู้วิธี **สร้างเอกสาร Word** ด้วย Aspose.Words, **เพิ่มปุ่มคำสั่ง**, **ตั้งขนาดปุ่ม**, และตามต้องการเชื่อมปุ่มกับแมโครเพื่อพฤติกรรม **เพิ่มปุ่มโต้ตอบ** วิธีนี้ช่วยให้คุณอัตโนมัติการสร้างฟอร์ม, สร้างรายงานไดนามิก, หรือสร้างต้นแบบ UI บน Word โดยตรงจาก C#.

ต่อไปคุณอาจสำรวจ:

* **วิธีแทรกกล่องเลือก ActiveX** สำหรับแบบสำรวจ.  
* **วิธีเพิ่มเนื้อหา Rich Text** รอบปุ่มโดยใช้ `DocumentBuilder`.  
* **วิธีป้องกันเอกสาร** พร้อมให้ปุ่มทำงานได้.  

อย่าลังเลที่จะทดลองใช้คอนโทรลประเภทต่าง ๆ, ขนาดต่าง ๆ, และชื่อแมโครที่แตกต่างกันเพื่อให้ตรงกับสถานการณ์ของคุณ. Happy coding!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบต่าง ๆ ในโครงการของคุณเอง.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}