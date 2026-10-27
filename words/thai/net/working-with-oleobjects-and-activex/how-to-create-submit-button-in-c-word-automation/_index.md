---
category: general
date: 2026-08-23
description: สร้างปุ่มส่งใน C# Word automation. เรียนรู้วิธีเพิ่มปุ่ม ActiveX, ตั้งชื่อปุ่ม,
  คำบรรยาย และข้อความโดยโปรแกรม.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: th
lastmod: 2026-08-23
og_description: สร้างปุ่มส่งในการทำงานอัตโนมัติของ Word ด้วย C# คู่มือนี้แสดงวิธีเพิ่มปุ่ม
  ActiveX ตั้งชื่อ ป้ายกำกับ และข้อความโดยใช้ Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: สร้างปุ่มส่งใน C# การทำงานอัตโนมัติของ Word
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: วิธีสร้างปุ่มส่งใน C# Word automation
url: /th/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างปุ่ม Submit ในการทำงานอัตโนมัติของ Word ด้วย C#

หากคุณต้องการ **สร้างปุ่ม Submit** ภายในเอกสาร Word ด้วย C# คู่มือนี้จะพาคุณผ่านกระบวนการทั้งหมด คุณจะได้เรียนรู้วิธีเพิ่มปุ่ม ActiveX กำหนดชื่อโปรแกรมเมติก และตั้งค่า caption ของปุ่มให้ดูเหมือนคอนโทรล *Submit* ปกติ

การทำอัตโนมัติของคอนโทรลฟอร์มใน Word สามารถแทนที่งานจัดวางด้วยมือและรับประกันความสอดคล้องในเอกสารหลายร้อยฉบับได้ ในขั้นตอนต่อไปคุณจะได้เรียนรู้วิธี **ตั้งค่าข้อความปุ่ม**, **ตั้งค่าชื่อปุ่ม**, และ **ตั้งค่า caption ปุ่ม** — ทั้งหมดนี้เป็นสิ่งสำคัญเมื่อปุ่มทำงานร่วมกับ workflow ที่ขับเคลื่อนด้วย macro

## ข้อกำหนดเบื้องต้น

* ติดตั้ง .NET 6.0 (หรือรุ่นที่ใหม่กว่า)
* อ้างอิงถึง **Aspose.Words for .NET** (ไลบรารีที่ให้ `DocumentBuilder.InsertForms2OleControl`)
* มีความคุ้นเคยพื้นฐานกับ C# และคอนโทรลฟอร์ม ActiveX ของ Word

คุณสามารถติดตั้ง Aspose.Words ผ่าน NuGet:

```bash
dotnet add package Aspose.Words
```

> **เคล็ดลับ:** ใช้เวอร์ชันเสถียรล่าสุดของ Aspose.Words เพื่อรับประโยชน์จากการแก้ไขบั๊กและฟีเจอร์ใหม่ที่เกี่ยวกับคอนโทรล ActiveX

## ภาพรวมของโซลูชัน

บทเรียนนี้จัดเป็นสามขั้นตอนที่ชัดเจน:

1. **Add ActiveX button** – ใช้เมธอด `InsertForms2OleControl` เพื่อวางปุ่มคำสั่งในเอกสาร  
2. **Set button name** – กำหนดตัวระบุโปรแกรมเมติกที่ไม่ซ้ำกันด้วย property `Name`  
3. **Set button caption** – กำหนดข้อความที่มองเห็นบนปุ่มผ่าน property `Caption` (ซึ่งยังควบคุม **set button text** ที่คุณเห็นใน UI)

เมื่อจบคู่มือคุณจะมีรูทีน **create submit button** ที่ทำงานเต็มรูปแบบซึ่งสามารถนำกลับมาใช้ใหม่ในโครงการอัตโนมัติของ Word ใดก็ได้

## ขั้นตอนที่ 1: เพิ่มปุ่ม ActiveX ลงในเอกสาร

งานแรกคือการ **add activex button** ลงในไฟล์ Word Aspose.Words เปิดเผย enum `Forms2OleControlType.CommandButton` เพื่อใช้ในกรณีนี้

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**ทำไมขั้นตอนนี้สำคัญ:**  
คอนโทรล ActiveX เป็นองค์ประกอบฟอร์มของ Word เพียงอย่างเดียวที่สามารถเรียกใช้ VBA macro หรือโต้ตอบกับโค้ดภายนอกได้ การเพิ่มคอนโทรลนี้จะสร้างตัวแทนที่ขั้นตอนต่อไปสามารถกำหนดค่าได้

> **กรณีขอบ:** หากเอกสารมีคอนโทรลที่ใช้ชื่อเดียวกันอยู่แล้ว Word จะทำการเปลี่ยนชื่ออัตโนมัติให้กับอันใหม่ (เช่น `CommandButton1`). การตั้งชื่ออย่างชัดเจนในขั้นตอนถัดไปจะช่วยหลีกเลี่ยงการชนกันของชื่อ

## ขั้นตอนที่ 2: ตั้งค่าชื่อปุ่ม

การ **set button name** ที่เชื่อถือได้เป็นสิ่งสำคัญเมื่อคุณต้องอ้างอิงคอนโทรลจาก VBA หรือจากส่วนอื่นของโค้ด C# ของคุณ Property `Name` จะให้ตัวระบุโปรแกรมเมติกกับปุ่ม

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**ทำไมคุณควรตั้งชื่อ:**  
เมื่อเปิดเอกสาร VBA สามารถดึงปุ่มได้ผ่าน `ActiveDocument.InlineShapes("btnSubmit")`. ชื่อที่มีความหมายเช่น `btnSubmit` ยังช่วยให้เข้าใจเจตนาเมื่อคุณตรวจสอบ XML ของเอกสาร

> **เคล็ดลับ:** ใช้ชื่อสั้น, ประกอบด้วยตัวอักษรและตัวเลข, และเริ่มด้วยตัวอักษร เพื่อให้สอดคล้องกับกฎการตั้งชื่อของ VBA

## ขั้นตอนที่ 3: ตั้งค่า caption ปุ่ม (ข้อความที่มองเห็นได้)

ข้อความที่ผู้ใช้เห็นบนปุ่มถูกควบคุมโดย property **set button caption** ใน UI ของ Word นี้จะแสดงเป็นป้ายกำกับของปุ่ม ซึ่งก็เป็น **set button text** ที่คุณต้องการแสดง

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**ทำไม caption ถึงสำคัญ:**  
caption คือป้ายกำกับที่ผู้ใช้มองเห็น การเปลี่ยนแปลงภายหลังจะไม่กระทบต่อชื่อของปุ่ม ดังนั้นคุณสามารถทำ localization ของ UI ได้โดยไม่ทำให้โค้ดที่พึ่งพา `btnSubmit` แตกหัก

> **คำถามทั่วไป:** *ฉันสามารถตั้งค่า Caption และ Value พร้อมกันได้หรือไม่?*  
> สำหรับ `CommandButton` `Caption` ควบคุมป้ายกำกับ ส่วน `Value` ไม่ได้ใช้ หากคุณต้องการค่าที่ซ่อนอยู่ ให้เก็บไว้ในคุณสมบัติเ�เอกสารแบบกำหนดเองแทน

## ตัวอย่างการทำงานเต็มรูปแบบ

การรวมสามขั้นตอนเข้าด้วยกันจะให้รูทีนที่สมบูรณ์ซึ่งคุณสามารถนำไปใช้ในแอปคอนโซลหรือ Windows ใดก็ได้:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

การรันโปรแกรมจะสร้างไฟล์ `SubmitButton.docx`. เมื่อคุณเปิดไฟล์ใน Microsoft Word:

* ปุ่ม **Submit** ปรากฏที่ตำแหน่งที่กำหนด
* ชื่อของปุ่มคือ `btnSubmit` (ตรวจสอบได้จาก *Developer → Design Mode → Properties*)
* การคลิกปุ่มในโหมดออกแบบจะแสดง caption *Submit*

ตอนนี้คุณมีบล็อกที่นำกลับมาใช้ใหม่สำหรับโซลูชัน Word ที่ขับเคลื่อนด้วยฟอร์มใดก็ได้

## ข้อควรพิจารณาเพิ่มเติม

### การจัดการการชนกันของชื่อ

หากคุณรันรูทีนหลายครั้งบนเอกสารเดียวกัน Word อาจทำการเปลี่ยนชื่อคอนโทรลที่ซ้ำโดยอัตโนมัติ เพื่อรับประกันความไม่ซ้ำกัน คุณสามารถใส่ GUID ข้างหน้าได้:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### การทำ Localization ให้กับ caption ของปุ่ม

สำหรับเอกสารหลายภาษา ให้เก็บ caption ไว้ในไฟล์ resource แล้วกำหนดค่าใน runtime:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### การตอบสนองต่อการคลิกปุ่ม

ปุ่มเองไม่มีตรรกะการคลิกใน C# คุณมักจะเชื่อมต่อกับ VBA macro:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

เนื่องจากคุณได้ **set button name** เป็น `btnSubmit` ชื่อ macro จะตามรูปแบบ `<Name>_Click` โดยอัตโนมัติ

## คำถามที่พบบ่อย (FAQ) การแก้ไขปัญหา

| คำถาม | คำตอบ |
|----------|--------|
| **ทำไมปุ่มถึงแสดงเป็นค่าว่าง?** | ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่า property `Caption`; หากไม่ได้ตั้งค่า ปุ่มจะไม่มีข้อความแสดง |
| **ฉันสามารถใช้คอนโทรล ActiveX ตัวอื่นได้หรือไม่?** | ได้. แทนที่ `Forms2OleControlType.CommandButton` ด้วย `CheckBox`, `OptionButton` ฯลฯ แต่ property จะต่างกัน |
| **โค้ดนี้เข้ากันได้กับ .NET Core หรือไม่?** | Aspose.Words for .NET รองรับ .NET 6+ ดังนั้นโค้ดเดียวกันทำงานได้บน .NET Core และ .NET Framework |
| **ถ้าเอกสารมีปุ่มอยู่แล้วจะทำอย่างไร?** | ใช้ `Name` ที่ไม่ซ้ำกัน (เช่น เพิ่ม GUID) เพื่อหลีกเลี่ยงการชนกัน |

## สรุป

ตอนนี้คุณรู้วิธี **create submit button** อย่างโปรแกรมเมติกในเอกสาร Word ด้วย C# โดยทำตามสามขั้นตอน—**add activex button**, **set button name**, และ **set button caption**—คุณสามารถ **set button text**, **set button name**, และ **set button caption** อย่างเชื่อถือได้สำหรับโซลูชันฟอร์มอัตโนมัติใด ๆ

ต่อจากนี้คุณอาจสำรวจ:

* เพิ่ม VBA macro ที่ตอบสนองต่อการคลิก **submit button**
* ปรับสไตล์ปุ่มด้วยฟอนต์หรือสีที่กำหนดเองผ่าน XML ที่อยู่ด้านล่าง
* สร้างหลายปุ่มในลูปสำหรับฟอร์มแบบไดนามิก

อย่าลังเลที่จะทดลองกับ caption, ชื่อ, และตำแหน่งที่ต่างกันเพื่อให้เหมาะกับ workflow ของคุณเอง ขอให้สนุกกับการทำอัตโนมัติ!

## สิ่งที่คุณควรเรียนต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโครงการของคุณ

- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [สร้าง Line Chart ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [สร้างเอกสาร Word พร้อม Header และ Footer ด้วย Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}