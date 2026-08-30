---
category: general
date: 2026-08-04
description: สร้างเอกสาร Word เปล่าและแทรกปุ่มคำสั่งโดยใช้ Aspose.Words เรียนรู้การตั้งขนาดปุ่มและเพิ่มปุ่มที่คลิกได้ใน
  C#
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: th
lastmod: 2026-08-04
og_description: สร้างเอกสาร Word ว่างด้วย Aspose.Words และแทรกปุ่มคำสั่ง คู่มือนี้แสดงวิธีตั้งขนาดปุ่ม,
  เพิ่มปุ่มที่คลิกได้, และบันทึกไฟล์
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: สร้างเอกสาร Word เปล่าและเพิ่มปุ่มคำสั่ง – บทเรียน C# ฉบับเต็ม
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: สร้างเอกสาร Word ว่างด้วยปุ่มคำสั่ง – คู่มือขั้นตอนโดยละเอียด
url: /th/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word เปล่าพร้อมปุ่มคำสั่ง – คู่มือขั้นตอนโดยละเอียด

หากคุณต้องการ **สร้างเอกสาร Word เปล่า** ที่มีปุ่มโต้ตอบอยู่ คู่มือนี้จะแสดงวิธีทำอย่างละเอียดด้วย Aspose.Words for .NET คุณจะได้เรียนรู้วิธี **แทรกปุ่มคำสั่ง**, ปรับลักษณะของมัน, และทำให้สามารถคลิกได้—ทั้งหมดในไม่กี่บรรทัดของ C#.

คู่มือครอบคลุมทุกขั้นตอนตั้งแต่การตั้งค่าโปรเจกต์จนถึงการบันทึกไฟล์ขั้นสุดท้าย เพื่อให้คุณสามารถคัดลอก‑วางโซลูชันเต็มรูปแบบไปใช้ในแอปพลิเคชันของคุณได้ ตลอดทางเราจะอธิบายวิธี **เพิ่มปุ่มที่คลิกได้**, **ตั้งขนาดปุ่ม**, และ **สร้างปุ่มคำสั่ง** ด้วยโปรแกรม

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือใหม่กว่า
* Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ .NET)
* NuGet package ของ Aspose.Words for .NET (`Aspose.Words` เวอร์ชัน 23.12 หรือใหม่กว่า)
* ความคุ้นเคยพื้นฐานกับ C# และการเขียนโปรแกรมเชิงวัตถุ

ไม่จำเป็นต้องใช้ Assembly ของ Office Interop เพิ่มเติม เนื่องจาก Aspose.Words ทำงานอย่างอิสระจาก Microsoft Word อย่างเต็มที่

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์ .NET

สร้างแอปพลิเคชันคอนโซลที่จะเป็นโฮสต์ให้กับโค้ดอัตโนมัติของ Word

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

คำสั่งนี้จะสร้างโฟลเดอร์ใหม่ชื่อ `WordButtonDemo` พร้อมไฟล์ `Program.cs` ที่พร้อมรันและเพิ่มไลบรารี Aspose.Words เข้าไป

## ขั้นตอนที่ 2: สร้างเอกสาร Word เปล่า

การดำเนินการแรกคือ **สร้างเอกสาร Word เปล่า** Aspose.Words มีคลาส `Document` ที่เป็นตัวแทนของไฟล์ Word ว่างเปล่าโดยอัตโนมัติ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

การสร้างเอกสารเปล่าจะให้คุณมี “ผ้าใบ” ที่สะอาดสำหรับใส่ย่อหน้า ตาราง หรือในกรณีนี้คือปุ่มคำสั่ง OLE

## ขั้นตอนที่ 3: เริ่มต้น DocumentBuilder

`DocumentBuilder` เป็นตัวช่วยที่ให้คุณแทรกเนื้อหาเข้าไปในเอกสาร คุณต้องเชื่อมต่อมันกับเอกสารที่เพิ่งสร้าง

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder จะคงตำแหน่งเคอร์เซอร์ปัจจุบันไว้ ดังนั้นการแทรกต่อไปจะเกิดขึ้นที่ตำแหน่งที่คุณต้องการอย่างแม่นยำ

## ขั้นตอนที่ 4: แทรกปุ่มคำสั่ง

ตอนนี้เราจะ **แทรกปุ่มคำสั่ง** (OLE `Forms2OleControl`) ลงในเอกสาร วิธี `InsertForms2OleControl` ต้องการอาร์กิวเมนต์สามค่า:

1. ProgID ของคอนโทรล OLE – `"CommandButton"` สำหรับปุ่มมาตรฐาน
2. `Rectangle` ที่กำหนด **ตั้งขนาดปุ่ม** และตำแหน่ง
3. คำบรรยายที่จะแสดงบนปุ่ม

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

เมื่อเปิดเอกสารใน Word ปุ่มจะทำงานเหมือนคอนโทรลฟอร์มพื้นเมือง—คุณสามารถคลิกได้และ Word จะเรียกแมโครที่เชื่อมโยง (หากมี) ซึ่งตอบสนองต่อความต้องการ **เพิ่มปุ่มที่คลิกได้** ของเรา

### ทำไมต้องใช้ Forms2OleControl?

`Forms2OleControl` ฝังอ็อบเจ็กต์ OLE ลงในไฟล์ DOCX โดยตรง ทำให้คุณสมบัติของคอนโทรลคงอยู่โดยไม่ต้องอาศัย Assembly ของ Word Interop นี่เป็นวิธีที่เชื่อถือได้ที่สุดสำหรับการ **สร้างปุ่มคำสั่ง** ที่ทำงานได้บนหลายเวอร์ชันของ Word

## ขั้นตอนที่ 5: ปรับแต่งปุ่ม (ไม่บังคับ)

คุณอาจต้องการ **ตั้งขนาดปุ่ม** อย่างแม่นยำยิ่งขึ้นหรือเปลี่ยนคุณสมบัติเพิ่มเติม เช่น ฟอนต์หรือสีพื้นหลัง Aspose.Words เปิดเผยอ็อบเจ็กต์ OLE ด้านล่าง ทำให้คุณสามารถปรับแต่งต่อได้

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

หากต้องการขนาดอื่น เพียงปรับค่า `Rectangle` ในขั้นตอนที่ 4 พิกัดวัดเป็นจุด (1 pt = 1/72 inch) ดังนั้นค่า `120` จะเท่ากับประมาณ 1.67 นิ้วในแนวกว้าง

## ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้ายให้เขียนเอกสารลงดิสก์ ไฟล์ที่ได้จะเป็น **เอกสาร Word เปล่า** พร้อมปุ่มคำสั่งที่ทำงานเต็มรูปแบบ

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

เมื่อคุณเปิด `CommandButtonDemo.docx` ใน Microsoft Word คุณจะเห็นปุ่มที่มีข้อความ “Click Me” การคลิกปุ่มจะเปิดกล่องโต้ตอบแมโครเริ่มต้น เว้นแต่คุณจะเชื่อมแมโครของคุณเอง

## โค้ดต้นฉบับเต็ม

ด้านล่างเป็นโปรแกรมทั้งหมดที่คุณสามารถคัดลอกไปวางใน `Program.cs` รวมทุกขั้นตอนที่อธิบายไว้และคอมไพล์ได้โดยไม่ต้องแก้ไข

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

การรันโปรแกรมจะสร้างไฟล์ `CommandButtonDemo.docx` เมื่อเปิดไฟล์ใน Word จะเห็น:

* หน้าหนึ่งหน้าที่มีปุ่มชื่อ **Click Me**
* ปุ่มมี **ตั้งขนาดปุ่ม** (120 × 30 จุด) ตามที่กำหนด
* การคลิกปุ่มทำให้ Word แสดงพฤติกรรมปุ่มคำสั่งเริ่มต้น ยืนยันว่าการ **เพิ่มปุ่มที่คลิกได้** ทำงานสำเร็จ

## คำถามที่พบบ่อยและกรณีขอบ

| Question | Answer |
|----------|--------|
| **Does this work with .doc files?** | ใช่. เพียงเปลี่ยนนามสกุลไฟล์ใน `doc.Save("file.doc")`. คอนโทรล OLE จะถูกเก็บในรูปแบบไบนารีแบบเก่าเช่นกัน |
| **What if I need multiple buttons?** | เรียก `InsertForms2OleControl` ซ้ำหลายครั้ง ปรับค่า `Rectangle` ของแต่ละปุ่มเพื่อหลีกเลี่ยงการทับซ้อน |
| **Can I attach a macro to the button?** | ปุ่มเองไม่ได้บรรจุโค้ดแมโคร คุณต้องเพิ่มแมโคร VBA ลงในเอกสารด้วยตนเองหรือผ่านคอลเลกชัน `Modules` ของอ็อบเจ็กต์ `Document` |
| **Is the button visible in PDF export?** | เมื่อส่งออก DOCX เป็น PDF ด้วย Aspose.Words ปุ่มจะถูกแสดงเป็นภาพคงที่ ไม่ใช่คอนโทรลโต้ตอบ |
| **What versions of Word are supported?** | ปุ่มคำสั่ง OLE ทำงานใน Word 2007 ขึ้นไป เนื่องจากสอดคล้องกับสเปค Forms2.0 มาตรฐาน |

## สรุป

คุณได้เรียนรู้วิธี **สร้างเอกสาร Word เปล่า**, **แทรกปุ่มคำสั่ง**, **เพิ่มปุ่มที่คลิกได้**, และ **ตั้งขนาดปุ่ม** ด้วย Aspose.Words for .NET ตัวอย่างเต็มแสดงกระบวนการ **สร้างปุ่มคำสั่ง** ตั้งแต่เริ่มต้นจนจบ ให้คุณมีพื้นฐานที่มั่นคงสำหรับงานอัตโนมัติของ Word ที่ซับซ้อนยิ่งขึ้น

## ขั้นตอนต่อไป

* สำรวจคอนโทรล OLE อื่น ๆ (เช่น `CheckBox`, `ListBox`) โดยเปลี่ยน ProgID ใน `InsertForms2OleControl`
* ผสานปุ่มกับแมโคร VBA เพื่อทำงานตามที่ผู้ใช้คลิก
* ใช้ `DocumentBuilder` ของ Aspose.Words เพื่อเพิ่มเนื้อหาอื่น ๆ เช่น ตาราง, รูปภาพ หรือเชิงอรรถ ก่อนแทรกปุ่ม
* ทดลองปรับค่า **ตั้งขนาดปุ่ม** ให้ตรงกับการจัดวางเอกสารของคุณ

ขอให้เขียนโค้ดสนุกและสร้างเอกสาร Word ที่มีคอนโทรลโต้ตอบได้อย่างเต็มที่!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}