---
category: general
date: 2026-10-23
description: สร้างเอกสาร Word ว่างด้วย C# และเรียนรู้วิธีแทรกคอนโทรล ActiveX รวมถึงปุ่มโดยใช้
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: th
lastmod: 2026-10-23
og_description: สร้างเอกสาร Word เปล่าด้วย C# และเรียนรู้วิธีแทรกคอนโทรล ActiveX รวมถึงปุ่มโดยใช้
  Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: สร้างเอกสาร Word ว่างและเพิ่มปุ่ม ActiveX ด้วย C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: สร้างเอกสาร Word ว่างและเพิ่มปุ่ม ActiveX ด้วย C#
url: /th/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word เปล่าและเพิ่มปุ่ม ActiveX ใน C#

หากคุณต้องการ **create blank Word document** อย่างอัตโนมัติ คู่มือนี้จะแสดงให้คุณเห็นอย่างละเอียด คุณจะได้เห็นตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่งสร้างเอกสารใหม่ แทรก ActiveX CommandButton และบันทึกไฟล์—ทั้งหมดด้วย Aspose.Words for .NET.

การทำงานกับไฟล์ Word มักต้องการมากกว่าข้อความธรรมดา การเพิ่ม **ActiveX button** ช่วยให้คุณฝังฟังก์ชันเชิงโต้ตอบที่สามารถใช้ในเทมเพลตที่เปิดใช้งานมาโครหรือโซลูชันเฉพาะ Windows ได้ ในตอนท้ายของบทแนะนำนี้คุณจะสามารถแทรก ActiveX control ใดก็ได้ แต่เราจะเน้นสถานการณ์ที่พบบ่อยที่สุด: **word document activex button** ที่ส่งฟอร์ม

## ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+ ด้วย)
* Visual Studio 2022 (หรือ IDE C# ใดก็ได้)
* **Aspose.Words for .NET** NuGet package  
  ```bash
  dotnet add package Aspose.Words
  ```
* ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#

> **เคล็ดลับ:** Aspose.Words เป็นไลบรารีเชิงพาณิชย์ แต่ให้ใบอนุญาตชั่วคราวฟรีสำหรับการทดสอบ ติดตั้งใบอนุญาตตั้งแต่ต้นเพื่อหลีกเลี่ยงลายน้ำการประเมินผล

## ขั้นตอนที่ 1: สร้างเอกสาร Word เปล่าด้วย Aspose.Words

ขั้นตอนแรกคือการสร้างอ็อบเจ็กต์ `Document` ซึ่งเป็นตัวแทนของไฟล์ `.docx` ว่างในหน่วยความจำ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` เริ่มต้นโดยไม่มีส่วน, หน้า หรือเนื้อหาใดๆ มันเป็นแผ่นเปล่าที่คุณต้องการสำหรับสถานการณ์ **create blank word document** เช่นการสร้างรายงานจากศูนย์

## ขั้นตอนที่ 2: รับ DocumentBuilder เพื่อแก้ไขเอกสาร

`DocumentBuilder` ให้ API ที่สะดวกสำหรับการเพิ่มข้อความ, รูปภาพ, และคอนโทรล เราจะใช้มันเพื่อกำหนดตำแหน่งของ ActiveX control

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

DocumentBuilder จะเพิ่มส่วนเริ่มต้นและหน้าที่หนึ่งโดยอัตโนมัติ ดังนั้นคุณสามารถเริ่มแทรกอ็อบเจ็กต์ได้ทันที

## ขั้นตอนที่ 3: วิธีแทรก ActiveX control ลงในเอกสาร

Aspose.Words มีเมธอด `InsertForms2OleControl` สำหรับฝังอ็อบเจ็กต์ OLE/ActiveX เมธอดนี้ต้องการประเภทของคอนโทรล, ความกว้าง, และความสูง (เป็นหน่วย points) ด้านล่างเราจะแทรก **CommandButton**—ปุ่มฟอร์มคลาสสิกที่คุณเห็นในเทมเพลต Word รุ่นเก่า

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **ทำไมวิธีนี้ถึงทำงาน:** `Forms2OleControlType.COMMANDBUTTON` บอก Word ให้สร้างปุ่มที่สามารถตอบสนองต่อเหตุการณ์คลิกเมื่อเอกสารถูกเปิดในสภาพแวดล้อม Windows ที่รองรับ ActiveX

## ขั้นตอนที่ 4: สร้าง ActiveX control – ตั้งค่าคุณสมบัติ

ตอนนี้เราจะกำหนดชื่อโปรแกรมและคำบรรยายที่มองเห็นได้ให้กับปุ่ม นี่คือส่วนของ **create activex control** ที่นักพัฒนามักมองข้าม

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` คือชื่อระบุที่คุณจะอ้างอิงจากมาโคร VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` คือข้อความที่แสดงบนปุ่มเอง

## ขั้นตอนที่ 5: บันทึกเอกสาร Word พร้อมปุ่ม ActiveX

สุดท้ายให้เขียนเอกสารลงดิสก์ ส่วนขยายไฟล์ต้องเป็น `.docx` (หรือ `.docm` หากคุณวางแผนจะเพิ่มมาโครในภายหลัง) ตัวอย่างนี้บันทึกลงโฟลเดอร์ชั่วคราว—ให้เปลี่ยนเป็นเส้นทางของคุณเอง

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

เมื่อคุณเปิดไฟล์ที่ได้ใน Microsoft Word (เฉพาะ Windows) คุณจะเห็น **word document activex button** ที่ทำงานได้ซึ่งสามารถเชื่อมต่อกับโค้ด VBA

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอกและวางลงในโปรเจกต์คอนโซลใหม่

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวังเมื่อคุณรันโปรแกรม**

```
Document saved to C:\Temp\ActiveXButton.docx
```

เปิดไฟล์ `ActiveXButton.docx` ที่สร้างขึ้นใน Word แล้วคุณจะเห็นปุ่มที่มีป้าย **Submit** อยู่ที่ด้านบนของหน้าที่หนึ่ง

## กรณีขอบและข้อผิดพลาดทั่วไป

| สถานการณ์ | สิ่งที่ควรระวัง | คำแนะนำ |
|-----------|-------------------|----------------|
| ทำงานบน macOS หรือ Linux | ActiveX เป็นเทคโนโลยีเฉพาะ Windows ดังนั้นปุ่มจะปรากฏเป็นตัวแทน | ใช้บทแนะนำนี้เฉพาะกับเทมเพลตที่มุ่งเป้า Windows เท่านั้น |
| เปิดเอกสารใน Word Online | คอนโทรล ActiveX ไม่รองรับในมุมมองเบราว์เซอร์ | ให้ UI สำรองหรือแนะนำผู้ใช้ให้เปิดไฟล์ในไคลเอนต์เดสก์ท็อป |
| ต้องการไฟล์ที่เปิดใช้งานมาโคร | ไฟล์ `.docx` ไม่สามารถเก็บโค้ด VBA ได้ | บันทึกเป็น `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) แล้วเพิ่มมาโครแยกต่างหาก |
| ขนาดคอนโทรลไม่ตรงกัน | ค่าความกว้าง/ความสูงเป็นหน่วย points (1 pt ≈ 1/72 in) | ปรับค่าตัวเลขเพื่อให้ได้ขนาดที่ต้องการ |

## คำถามที่พบบ่อย

**วิธีแทรก ActiveX control ที่ไม่ใช่ปุ่ม?**  
ใช้เมธอด `InsertForms2OleControl` เดียวกันแต่ส่งค่า enum `Forms2OleControlType` ที่แตกต่าง เช่น `COMBOBOX` หรือ `LISTBOX`.

**ฉันสามารถเปลี่ยนฟอนต์หรือสีของปุ่มได้หรือไม่?**  
ลักษณะของปุ่ม ActiveX ถูกกำหนดโดยแอปพลิเคชันโฮสต์ (Word) และธีม Windows ที่อยู่เบื้องหลัง คุณสามารถแก้ไขคุณสมบัติเช่น `ForeColor` และ `BackColor` ผ่าน VBA หลังจากเปิดเอกสารได้

**มีวิธีเพิ่มตัวจัดการคลิกโดยตรงจาก C# หรือไม่?**  
ไม่มี เหตุการณ์คลิกต้องถูกจัดการโดย VBA หรือ Word add‑in เนื่องจากปุ่มทำงานภายในกระบวนการของ Word ไม่ใช่แอปพลิเคชัน .NET ของคุณ

## สรุป

ตอนนี้คุณรู้วิธี **create blank Word document** อย่างอัตโนมัติและฝัง **ActiveX button** ด้วย Aspose.Words for .NET ขั้นตอนที่ครอบคลุม:

1. สร้างอ็อบเจ็กต์ `Document`.
2. ใช้ `DocumentBuilder` เพื่อทำงานกับไฟล์.
3. เรียก `InsertForms2OleControl` เพื่อ **how to insert activex** control.
4. ตั้งค่าคุณสมบัติของคอนโทรล (**create activex control**).
5. บันทึกไฟล์ ซึ่งจะได้ **word document activex button** พร้อมสำหรับการรวมกับ VBA

จากนี้คุณสามารถสำรวจการเพิ่มประเภทคอนโทรลอื่นๆ, เชื่อมโยงมาโคร VBA, หรือแปลงเอกสารเป็น PDF พร้อมคงปุ่มไว้ (เป็นภาพคงที่) ทดลองกับขนาด, คำบรรยาย, และชื่อที่แตกต่างกัน

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการใช้งานแบบอื่นในโครงการของคุณ

- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}