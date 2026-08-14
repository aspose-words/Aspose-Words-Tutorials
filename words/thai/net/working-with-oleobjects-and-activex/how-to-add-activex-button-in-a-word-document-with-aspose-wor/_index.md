---
category: general
date: 2026-08-14
description: วิธีเพิ่มปุ่ม ActiveX ในเอกสาร Word ด้วย Aspose.Words – เรียนรู้การสร้างเอกสาร
  Word ว่างและแทรกปุ่ม ActiveX โดยใช้โค้ด
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: th
lastmod: 2026-08-14
og_description: วิธีเพิ่มปุ่ม ActiveX ในเอกสาร Word ด้วย Aspose.Words บทเรียนนี้จะแสดงวิธีสร้างเอกสาร
  Word ว่าง แทรกปุ่ม ActiveX และบันทึกผลลัพธ์
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: วิธีเพิ่มปุ่ม ActiveX ใน Word – คู่มือ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: วิธีเพิ่มปุ่ม ActiveX ในเอกสาร Word ด้วย Aspose.Words
url: /th/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มปุ่ม ActiveX ในเอกสาร Word ด้วย Aspose.Words

หากคุณต้องการ **วิธีเพิ่ม ActiveX** คอนโทรลในไฟล์ Word ที่สร้างขึ้น คู่มือนี้จะแสดงขั้นตอนที่แน่นอน คุณจะได้เรียนรู้การ **แทรกปุ่ม ActiveX** อย่างโปรแกรมเมติก ตั้งแต่ **สร้างเอกสาร Word ว่าง** จนถึงไฟล์ที่บันทึกแล้วซึ่งสามารถเปิดใน Microsoft Word ได้

การเพิ่มปุ่มที่เรียกใช้โค้ด VBA หรือแมโครเป็นความต้องการทั่วไปสำหรับตัวสร้างรายงานอัตโนมัติ, แม่แบบฟอร์ม, หรือสัญญาแบบโต้ตอบ การใช้ Aspose.Words for .NET ช่วยให้คุณสร้างเอกสารโดยไม่ต้องเปิด Office ทำให้กระบวนการเร็วและเป็นมิตรต่อเซิร์ฟเวอร์

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 (หรือใหม่กว่า) SDK ติดตั้งแล้ว
* Visual Studio 2022 หรือ IDE ที่รองรับ C#
* Aspose.Words for .NET NuGet package (`Aspose.Words` เวอร์ชัน 24.9 หรือใหม่กว่า)  
  ติดตั้งด้วย:
  ```bash
  dotnet add package Aspose.Words
  ```
* สภาพแวดล้อม Windows หากคุณต้องการทดสอบปุ่ม ActiveX เนื่องจากคอนโทรล ActiveX ต้องการ Microsoft Word เวอร์ชัน Windows

## ขั้นตอนที่ 1: สร้างเอกสาร Word ว่าง

งานแรกคือ **สร้างเอกสาร Word ว่าง** ในหน่วยความจำ Aspose.Words มีคลาส `Document` สำหรับวัตถุประสงค์นี้

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` แทนไฟล์ .docx ทั้งไฟล์ ในขณะนี้เอกสารยังไม่มีหน้าใด ๆ แต่คุณสามารถเริ่มเพิ่มเนื้อหาได้ทันที

## ขั้นตอนที่ 2: เริ่มต้น DocumentBuilder

`DocumentBuilder` เป็นตัวช่วยที่ให้คุณแทรกข้อความ, รูปภาพ, และออบเจ็กต์อื่น ๆ ลงในเอกสาร มันทำงานบนอินสแตนซ์ `Document` ที่คุณสร้างไว้ก่อนหน้า

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

ตัวสร้างจะรักษาตำแหน่งเคอร์เซอร์; สิ่งที่คุณแทรกหลังบรรทัดนี้จะปรากฏที่จุดเริ่มต้นของหน้าแรก

## ขั้นตอนที่ 3: แทรกคอนโทรล ActiveX CommandButton

Aspose.Words เปิดเผยเมธอด `InsertForms2OleControl` สำหรับเพิ่มคอนโทรลฟอร์มแบบเก่า รวมถึง ActiveX เมธอดนี้ต้องการประเภทคอนโทรลและขนาดเป็นจุด

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

ออบเจ็กต์ `Forms2OleControl` ที่คืนค่ามาให้คุณกำหนดคุณสมบัติต่าง ๆ เช่น ชื่อและคำบรรยายของคอนโทรล

## ขั้นตอนที่ 4: กำหนดคุณสมบัติของปุ่ม

การตั้งค่า `Name` ที่มีความหมายช่วยให้คุณอ้างอิงคอนโทรลจากโค้ด VBA ในภายหลัง `Caption` คือข้อความที่ผู้ใช้เห็นบนปุ่ม

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **เคล็ดลับ:** ให้ชื่อสั้นและเป็นอักษรและตัวเลข; Word จะปฏิเสธชื่อที่มีช่องว่างหรืออักขระพิเศษ

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้าย ให้เขียนเอกสารลงดิสก์ ใช้นามสกุล `.docx` สำหรับไฟล์ Word สมัยใหม่; ปุ่ม ActiveX ทำงานเช่นเดียวกันในไฟล์ `.doc` แต่ `.docx` เป็นรูปแบบที่แนะนำสำหรับโครงการใหม่

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

เมื่อคุณเปิด `ActiveXButton.docx` ใน Microsoft Word คุณจะเห็นปุ่ม **Submit** ที่คลิกได้ หากเปิดใช้งานแมโคร คุณสามารถแนบโค้ด VBA ไปที่ `btnSubmit_Click` เพื่อให้ทำงานเมื่อผู้ใช้คลิกปุ่ม

## ตัวอย่างเต็มที่สามารถรันได้

การรวมส่วนต่าง ๆ เข้าด้วยกันทำให้คุณได้โปรแกรมที่ทำงานอิสระซึ่งสามารถคัดลอก, วาง, และรันได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง** – หลังจากรันโปรแกรม คอนโซลจะแสดงตำแหน่งการบันทึก และการเปิดไฟล์ที่สร้างใน Word จะเห็นปุ่มที่มีข้อความ **Submit** อยู่ที่ด้านบนของหน้าแรก

## การจัดการคำถามทั่วไปและกรณีขอบ

### ปุ่มทำงานในทุกเวอร์ชันของ Word หรือไม่?

คอนโทรล ActiveX รองรับในเวอร์ชันเดสก์ท็อปของ Word บน Windows ไม่แสดงผลใน Word Online, Word for macOS, หรือไคลเอนต์มือถือ หากคุณต้องการความโต้ตอบข้ามแพลตฟอร์ม ควรพิจารณาใช้คอนเทนท์คอนโทรลหรือโซลูชันแบบ HTML แทน

### ถ้าต้องการขนาดหรือตำแหน่งที่ต่างออกไปล่ะ?

`InsertForms2OleControl` วางคอนโทรลที่ตำแหน่งเคอร์เซอร์ของ builder ปัจจุบัน เพื่อย้ายตำแหน่ง ให้ปรับเคอร์เซอร์ด้วย `builder.MoveTo` ก่อนแทรก หรือแก้ไขคุณสมบัติ `Left` และ `Top` ของคอนโทรลหลังสร้าง

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### ฉันสามารถเพิ่มประเภท ActiveX อื่นได้หรือไม่?

ได้. ค่าตัวแปร `Forms2OleControlType` มี `CheckBox`, `OptionButton`, `ListBox` และอื่น ๆ แทนที่ `CommandButton` ด้วยค่า enum ที่ต้องการและปรับคุณสมบัติตามนั้น

### จำเป็นต้องมีแมโครเพื่อให้ปุ่มทำงานหรือไม่?

ปุ่มเองจะไม่ทำอะไรจนกว่าคุณจะแนบโค้ด VBA ใน Word กด **Alt+F11** เพื่อเปิด VBA editor, ค้นหา `btnSubmit_Click` และเขียนตรรกะที่ต้องการ เอกสารที่สร้างจะเก็บโครงการ VBA ไว้หากคุณบันทึกเป็นรูปแบบ **SaveFormat.Doc** (ไฟล์ `.doc` แบบเก่า) แต่ไฟล์ `.docx` ไม่สามารถเก็บแมโคร VBA ได้ ใช้รูปแบบ `.doc` หากต้องการฝัง VBA

## สรุป

คุณได้เรียนรู้ **วิธีเพิ่ม ActiveX** คอนโทรลในไฟล์ Word ด้วย Aspose.Words โดยทำตามขั้นตอนการ **สร้างเอกสาร Word ว่าง**, เริ่มต้น `DocumentBuilder`, **แทรกปุ่ม ActiveX**, กำหนดคุณสมบัติของมัน, และบันทึกไฟล์ คุณสามารถสร้างเทมเพลต Word แบบโต้ตอบโดยตรงจากโค้ด .NET ของคุณได้

ต่อไปสำรวจหัวข้อที่เกี่ยวข้อง เช่น การจัดการเหตุการณ์ **insert ActiveX button**, การเพิ่ม **create word document aspose** สำหรับตารางหรือรูปภาพ, และการรักษาความปลอดภัยของเอกสารที่เปิดแมโครสำหรับการใช้งานระดับองค์กร ทดลองใช้คอนโทรลประเภทต่าง ๆ และตัวเลือกการจัดวางเพื่อปรับประสบการณ์ผู้ใช้ให้ตรงกับความต้องการของแอปพลิเคชันของคุณ

โค้ดดิ้งให้สนุก!

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดที่ทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณเอง

- [สร้างเอกสาร Word พร้อม Header และ Footer ด้วย Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [สร้างเอกสาร Word พร้อมตารางด้วย Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}