---
category: general
date: 2026-08-20
description: เรียนรู้วิธีสร้างคอนโทรล ActiveX ตั้งค่าขนาดปุ่ม และเพิ่มปุ่มลงใน Word
  ด้วยตัวอย่าง C# ที่สมบูรณ์
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: th
lastmod: 2026-08-20
og_description: สร้างคอนโทรล ActiveX ในไฟล์ Word ด้วย C# บทเรียนนี้แสดงวิธีตั้งขนาดปุ่ม,
  เพิ่มปุ่มลงใน Word, และทำให้ปุ่มสามารถคลิกได้.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: สร้างคอนโทรล ActiveX ใน Word – คู่มือ C# ทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: วิธีสร้างคอนโทรล ActiveX ในเอกสาร Word ด้วย C#
url: /th/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้าง ActiveX control ในเอกสาร Word ด้วย C#

หากคุณต้องการ **สร้าง ActiveX control** ภายในไฟล์ Microsoft Word คำแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนอย่างละเอียด คุณจะได้เรียนรู้วิธี **เพิ่มปุ่มลงใน Word**, ตั้งค่าขนาดของปุ่ม, และทำให้คอนโทรลสามารถคลิกได้—ทั้งหมดด้วยโปรแกรม C# สั้น ๆ ที่ทำงานอิสระ

ในบทเรียนนี้คุณจะได้:

* เข้าใจว่าทำไม ActiveX control ถึงมีประโยชน์สำหรับเอกสาร Word ที่โต้ตอบได้  
* เรียนรู้โค้ดที่จำเป็นเพื่อ **ตั้งค่าขนาดปุ่ม** และกำหนดคำบรรยาย  
* ดูวิธี **สร้างปุ่มที่คลิกได้** ซึ่งสามารถเชื่อมต่อกับมาโครหรือโลจิกภายนอกในภายหลัง  

ขั้นตอนเหล่านี้ทำงานร่วมกับ Aspose.Words .NET 23.12 หรือเวอร์ชันใหม่กว่าและต้องการสภาพแวดล้อมการพัฒนา .NET เท่านั้น

> **Prerequisite** – คุณมีลิขสิทธิ์ Aspose.Words ที่ถูกต้อง (หรือกำลังใช้รุ่นทดลอง) และ Visual Studio 2022 หรือ IDE สำหรับ C# ใด ๆ

---

## วิธีสร้าง ActiveX control ในเอกสาร Word

ขั้นตอนแรกคือการสร้างอ็อบเจ็กต์ `Document` ว่างเปล่าและ `DocumentBuilder` ตัวสร้างนี้ให้ API ระดับสูงสำหรับการแทรกอ็อบเจ็กต์ เช่น ActiveX control

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

เมธอด `InsertActiveXButton` (กำหนดต่อไป) มีตรรกะสำหรับ **วิธีแทรกปุ่ม** และการตั้งค่าต่าง ๆ

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

เมื่อรันโปรแกรมจะสร้างไฟล์ **ActiveXButton.docx** การเปิดไฟล์ใน Word จะเห็นปุ่มที่มีข้อความ **Submit** คอนโทรลทำงานเต็มรูปแบบ—การคลิกจะทำให้เกิดเหตุการณ์มาตรฐาน `CommandButton_Click` ซึ่งคุณสามารถผูกกับมาโคร VBA ต่อไปได้

### ทำไมวิธีนี้ถึงได้ผล

* `InsertForms2OleControl` บอก Word ให้ฝังอ็อบเจ็กต์ OLE ชนิด **CommandButton** ซึ่งเป็นคลาสปุ่ม ActiveX ดั้งเดิม  
* พารามิเตอร์ความกว้างและความสูงจะ **ตั้งค่าขนาดปุ่ม** โดยตรง; Word จะเปลี่ยนค่าจากจุด (1 pt ≈ 1/72 in)  
* การตั้งชื่อคอนโทรล (`Name = "btnSubmit"`) ทำให้ค้นหาได้ง่ายจาก VBA (`ActiveDocument.InlineShapes("btnSubmit")`)  

---

## ตั้งค่าขนาดและคำบรรยายของปุ่ม

หากต้องการลักษณะที่แตกต่าง ให้ปรับค่าตัวเลขในคำเรียก `InsertForms2OleControl` ลายเซ็นของเมธอดคือ:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – ตัวระบุโปรแกรมของคลาส ActiveX (`"CommandButton"` สำหรับปุ่มมาตรฐาน)  
* **width / height** – ขนาดเป็นจุด สำหรับปุ่มกว้าง 2 cm ให้ใช้ `width = 56.7` (2 cm ≈ 56.7 pt)  

คุณยังสามารถแก้ไขคำบรรยายหลังจากแทรกได้:

```csharp
commandButton.Caption = "Send Request";
```

การเปลี่ยนคำบรรยายจะไม่กระทบต่อขนาด แต่จะส่งผลต่อการตอบสนองต่อผู้ใช้

### เคล็ดลับพิเศษ

หากต้องการปุ่มสี่เหลี่ยมจัตุรัส ให้ตั้งค่าทั้งสองมิติให้เท่ากัน:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## เพิ่มปุ่มลงใน Word และทำให้คลิกได้

โค้ดข้างต้นได้ **เพิ่มปุ่มลงใน Word** แล้ว หากต้องการให้ปุ่มทำงานบางอย่าง คุณต้องเขียนมาโคร VBA ที่จัดการเหตุการณ์ `Click` ตัวอย่างมาโครขั้นต่ำที่คุณสามารถวางในตัวแก้ไข VBA ของ Word (`Alt+F11` → Insert → Module) มีดังนี้:

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

เนื่องจากคอนโทรลถูกตั้งชื่อเป็น `btnSubmit` Word จะแมปเหตุการณ์ `Click` ไปยัง `btnSubmit_Click` โดยอัตโนมัติ นี่เป็นวิธีมาตรฐานในการ **สร้างปุ่มที่คลิกได้** โดยไม่ต้องพึ่งไลบรารีภายนอก

> **Note:** การตั้งค่าความปลอดภัยของมาโครใน Word อาจบล็อก ActiveX control ตรวจสอบให้แน่ใจว่าได้เลือก “Enable all macros” หรือ “Enable VBA macros” สำหรับเอกสารนี้ หรือเซ็นดิจิทัลให้กับมาโครสำหรับการใช้งานในสภาพแวดล้อมการผลิต

---

## คำถามที่พบบ่อย: วิธีแทรกปุ่มและการแก้ไขปัญหา

### 1. ปุ่มไม่ปรากฏหลังบันทึกทำอย่างไร?

* ตรวจสอบว่าเวอร์ชัน Aspose.Words รองรับ `InsertForms2OleControl` เวอร์ชันก่อน 22.5 ยังไม่มีฟีเจอร์นี้  
* ตรวจสอบให้แน่ใจว่าไฟล์เป้าหมายเป็นรูปแบบ `.docx` หรือ `.doc` รูปแบบเก่าเช่น `.rtf` ไม่สามารถเก็บอ็อบเจ็กต์ ActiveX ได้

### 2. สามารถแทรกปุ่มที่ตำแหน่ง bookmark เฉพาะได้หรือไม่?

ได้ เพียงย้าย builder ไปยัง bookmark ก่อนเรียก `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. วิธี **ตั้งค่าขนาดปุ่ม** อย่างไดนามิกตามความยาวข้อความ?

คำนวณความกว้างที่ต้องการโดยใช้เมธอด `Graphics.MeasureString` (จาก `System.Drawing`) แล้วแปลงพิกเซลเป็นจุด (`points = pixels * 72 / DPI`) จากนั้นส่งค่าความกว้างที่คำนวณได้ไปยัง `InsertForms2OleControl`

### 4. มีวิธีเพิ่มหลายปุ่มในลูปหรือไม่?

มีแน่นอน ให้วางตรรกะการแทรกไว้ในลูป `for` และปรับคุณสมบัติ `Left` และ `Top` สำหรับแต่ละรอบ:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## ผลลัพธ์ที่คาดหวัง

เมื่อคุณรันโปรแกรมและเปิด **ActiveXButton.docx**:

* จะเห็นปุ่ม **Submit** เพียงปุ่มเดียวที่ตำแหน่งบน‑ซ้ายของหน้าแรก  
* ขนาดของปุ่มตรงกับค่าที่คุณกำหนด (`100 pt × 30 pt`)  
* หากคุณเพิ่มมาโคร VBA แล้ว การคลิกปุ่มจะแสดงกล่องข้อความ: “You clicked the Submit button!”

คุณได้ **สร้าง ActiveX control**, **ตั้งค่าขนาดปุ่ม**, และ **เพิ่มปุ่มลงใน Word** สำเร็จแล้ว พร้อมกับเรียนรู้ **วิธีแทรกปุ่ม** และ **สร้างปุ่มที่คลิกได้** สำหรับงานอัตโนมัติในอนาคต

---

## สรุป

ในบทเรียนนี้คุณได้เรียนรู้วิธี **สร้าง ActiveX control** ภายในเอกสาร Word ด้วย C# โดยทำตามขั้นตอนคุณสามารถ **ตั้งค่าขนาดปุ่ม**, ตั้งชื่อคอนโทรลให้มีความหมาย, และ **เพิ่มปุ่มลงใน Word** เพื่อให้กลายเป็น **ปุ่มที่คลิกได้** ที่เชื่อมต่อกับมาโคร VBA  

ต่อไปคุณอาจสำรวจ:

* การผูกปุ่มกับ .NET COM add‑in แทน VBA  
* การใช้คลาส ActiveX อื่น ๆ เช่น `CheckBox` หรือ `ComboBox`  
* การอัตโนมัติการสร้างฟอร์มเต็มรูปแบบที่มีหลายคอนโทรล

ลองทดลองกับขนาดต่าง ๆ ได้ตามต้องการ

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบต่าง ๆ ในโปรเจกต์ของคุณ

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}