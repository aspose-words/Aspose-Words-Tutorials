---
category: general
date: 2026-11-18
description: สร้างเอกสาร Word เปล่าและแทรกปุ่ม ActiveX ด้วย C# เรียนรู้วิธีเพิ่มคอนโทรล
  ตั้งค่าคำบรรยายของปุ่ม และบันทึกไฟล์
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: th
lastmod: 2026-11-18
og_description: สร้างเอกสาร Word เปล่าและแทรกปุ่ม ActiveX ด้วย C# ทำตามบทเรียนฉบับเต็มนี้เพื่อเพิ่มคอนโทรล
  ตั้งค่าข้อความบนปุ่ม และบันทึกผลลัพธ์.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: สร้างเอกสาร Word ว่างและแทรกปุ่ม ActiveX – คู่มือแบบทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: สร้างเอกสาร Word ว่างและแทรกปุ่ม ActiveX
url: /th/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word เปล่าและแทรกปุ่ม ActiveX

หากคุณต้องการ **สร้างเอกสาร Word เปล่า** และวางปุ่ม ActiveX ที่โต้ตอบได้ภายในเอกสารนี้ คู่มือนี้จะแสดงให้คุณเห็นอย่างละเอียดว่าทำอย่างไรด้วย Aspose.Words for .NET คุณจะได้เห็นโค้ดทั้งหมด เข้าใจว่าทำไมแต่ละบรรทัดจึงสำคัญ และเรียนรู้วิธี **ตั้งค่าคำบรรยายของปุ่ม** เพื่อให้คอนโทรลดูพร้อมสำหรับการโต้ตอบของผู้ใช้

นอกจากเป้าหมายหลักแล้ว เราจะครอบคลุม **วิธีแทรก ActiveX** ขั้นตอน **วิธีเพิ่มคอนโทรล** ไปยังไฟล์ Word และรายละเอียดของ **การแทรกปุ่ม ActiveX** พร้อมคำบรรยายที่กำหนดเอง สุดท้ายคุณจะได้รูปแบบที่นำกลับมาใช้ใหม่ได้สำหรับสถานการณ์อัตโนมัติของเอกสารใด ๆ ที่ต้องการองค์ประกอบ UI ฝังอยู่

## สิ่งที่คุณจะได้เรียนรู้

* วิธี **สร้างเอกสาร Word เปล่า** ด้วยโปรแกรม.  
* การเรียก API ที่จำเป็นเพื่อ **แทรกปุ่ม ActiveX** และกำหนดคุณสมบัติต่าง ๆ.  
* วิธี **ตั้งค่าคำบรรยายของปุ่ม** เพื่อให้คอนโทรลแสดงข้อความที่ต้องการ.  
* เคล็ดลับในการบันทึกไฟล์ในตำแหน่งที่คุณเลือกและจัดการกับข้อผิดพลาดทั่วไป.

### ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานได้กับ .NET Framework 4.6+)  
* Aspose.Words for .NET ติดตั้งแล้ว (`Install-Package Aspose.Words`).  
* ความคุ้นเคยพื้นฐานกับ C# และ Visual Studio หรือ IDE ที่รองรับ .NET ใด ๆ  

---

## สร้างเอกสาร Word เปล่าด้วย Aspose.Words

ขั้นตอนแรกคือการสร้างอ็อบเจกต์ `Document` ที่ว่างเปล่า อ็อบเจกต์นี้แทนไฟล์ Word ที่ไม่มีเนื้อหาใด ๆ จนกว่าเราจะเพิ่มบางอย่างเข้าไป

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*ทำไมเรื่องนี้ถึงสำคัญ*: `Document` ที่ว่างเปล่าให้คุณมีผืนผ้าใบที่สะอาด คุณสามารถเพิ่มย่อหน้า ตาราง หรือคอนโทรลในภายหลังโดยไม่ต้องกังวลเกี่ยวกับการจัดรูปแบบที่มีอยู่

## เริ่มต้น DocumentBuilder เพื่อทำงานกับเอกสาร

`DocumentBuilder` เป็นคลาสช่วยเหลือที่ให้คุณแทรกเนื้อหาได้ที่ตำแหน่งเคอร์เซอร์ปัจจุบัน มันจะติดตามตำแหน่งของคุณในเอกสารโดยอัตโนมัติ

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*ทำไมเรื่องนี้ถึงสำคัญ*: หากไม่มี `DocumentBuilder` คุณจะต้องจัดการโครงสร้างโหนดระดับต่ำด้วยตนเอง Builder ทำให้การแทรกข้อความ ภาพ และคอนโทรล ActiveX ง่ายขึ้น

## วิธีแทรกปุ่ม ActiveX (insert activex button)

ตอนนี้เราจะใช้ `InsertForms2OleControl` เพื่อฝังคอนโทรล ActiveX วิธีนี้ต้องการอาร์กิวเมนต์สามค่า:

1. ประเภทของคอนโทรล (`OleControlType.CommandButton`).  
2. ชื่อภายในของคอนโทรล (ใช้โดย VBA หรือโค้ดแมโคร).  
3. `RectangleF` ที่กำหนดตำแหน่งและขนาดบนหน้า.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*ทำไมเรื่องนี้ถึงสำคัญ*: นี่คือหัวใจของ **วิธีแทรก activex** ลงในเอกสาร Word พิกัดของสี่เหลี่ยมถูกระบุเป็นจุด (1 point = 1/72 นิ้ว) ปรับค่าเหล่านี้เพื่อวางปุ่มในตำแหน่งที่ต้องการ

### เคล็ดลับ

หากคุณต้องการให้ปุ่มปรากฏบนหน้าที่กำหนด ให้ย้ายเคอร์เซอร์ของ builder ก่อน:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

## วิธีตั้งค่าคำบรรยายของปุ่ม (set button caption)

หลังจากวางคอนโทรลแล้ว คุณสามารถแก้ไขคุณสมบัติต่าง ๆ ของมันได้ คุณสมบัติที่มองเห็นได้ชัดที่สุดคือ `Caption` ซึ่งกำหนดข้อความที่แสดงบนปุ่ม

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*ทำไมเรื่องนี้ถึงสำคัญ*: ผู้ใช้เห็นคำบรรยาย ไม่ใช่ชื่อภายใน การเปลี่ยนแปลงนี้ทำให้ปุ่มมีความหมายในเอกสารสุดท้าย

## บันทึกเอกสารที่มีปุ่ม

สุดท้าย ให้เขียนเอกสารลงดิสก์ คุณสามารถเลือกฟอร์แมตที่รองรับใดก็ได้ (`.docx`, `.pdf` เป็นต้น) ที่นี่เราบันทึกเป็นเอกสาร Word

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*ทำไมเรื่องนี้ถึงสำคัญ*: การบันทึกไฟล์ทำให้คุณสามารถเปิดใน Microsoft Word และทดสอบปุ่มได้ เมื่อเปิดเอกสาร ปุ่มจะปรากฏพร้อมคำบรรยาย “Press”.

### ผลลัพธ์ที่คาดหวัง

การเปิด `with_button.docx` ใน Word จะเห็นหน้าว่างพร้อมปุ่มสี่เหลี่ยมที่มีป้าย **Press** การคลิกปุ่มจะไม่ทำอะไรโดยค่าเริ่มต้นเนื่องจากไม่มีแมโคร VBA แนบอยู่ แต่คอนโทรลทำงานได้เต็มที่และสามารถเชื่อมต่อกับโค้ดในภายหลังได้

## วิธีเพิ่มคอนโทรลในย่อหน้าที่กำหนด (how to add control)

บางครั้งคุณอาจต้องการให้ปุ่มอยู่ภายในย่อหน้าที่กำหนด เช่น หลังข้อความสอน ใช้ `MoveTo` เพื่อวางตำแหน่ง builder ก่อนแทรกคอนโทรล

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*ทำไมเรื่องนี้ถึงสำคัญ*: รูปแบบนี้แสดง **วิธีเพิ่มคอนโทรล** ในบริบท เพื่อให้การจัดวางเอกสารยังคงเป็นตรรกะ

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| ปุ่มปรากฏนอกหน้า | พิกัดสี่เหลี่ยมอยู่นอกขอบกระดาษ | ใช้ `builder.PageSetup` เพื่อรับขนาดหน้าและคำนวณ `RectangleF` ที่ปลอดภัย |
| คำบรรยายไม่แสดง | ตั้งค่า `Caption` ก่อนที่คอนโทรลจะถูกกำหนดค่าเต็ม | ตั้งค่า `Caption` **หลัง** การเรียก `InsertForms2OleControl` ตามที่แสดงในขั้นตอน 4 |
| เอกสารบันทึกโดยไม่มีปุ่ม | เคอร์เซอร์ของ Builder ถูกย้ายหลังการแทรกโดยไม่ได้บันทึกการเปลี่ยนแปลง | รักษา Builder ไว้บนหน้าเดียวกันหรือเรียก `builder.Document.UpdatePageLayout()` ก่อนบันทึก |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก วาง และรันได้ มันสร้างไฟล์ Word เปล่า แทรกปุ่ม ActiveX ตั้งค่าคำบรรยาย และบันทึกผลลัพธ์

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**ผลลัพธ์**: หลังจากรันโปรแกรม เปิด `C:\Temp\with_button.docx` ใน Microsoft Word คุณจะเห็นหน้าเดียวที่มีข้อความ “Below is an ActiveX button created programmatically:” ตามด้วยปุ่มที่มีป้าย **Press**.

## สรุป

ตอนนี้คุณรู้วิธี **สร้างเอกสาร Word เปล่า**, **แทรกปุ่ม ActiveX**, **ตั้งค่าคำบรรยายของปุ่ม**, และ **บันทึก** ผลลัพธ์โดยใช้ Aspose.Words for .NET รูปแบบเดียวกันนี้สามารถขยายไปยังคอนโทรล ActiveX อื่น ๆ (เช่น checkbox, list box ฯลฯ) โดยการเปลี่ยน `OleControlType`.

ต่อไป คุณอาจสำรวจ **วิธีแทรกเหตุการณ์ปุ่ม ActiveX** ด้วย VBA หรือ **วิธีเพิ่มคอนโทรล** ไปยังเอกสารที่มีอยู่แล้วซึ่งมีเนื้อหาอยู่แล้ว ทั้งสองหัวข้อนี้ต่อเนื่องจากแนวคิดที่อธิบายไว้ที่นี่

ขอให้สนุกกับการเขียนโค้ด และอย่าลังเลที่จะทดลองขนาด ตำแหน่ง และคำบรรยายต่าง ๆ เพื่อให้ตรงกับความต้องการ UI ของแอปพลิเคชันของคุณ!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญคุณลักษณะ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโครงการของคุณ

- [วิธีสร้างเอกสาร Word ด้วย C# พร้อมปุ่มคำสั่ง ActiveX](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [วิธีเพิ่มปุ่ม ActiveX ในเอกสาร Word ด้วย Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}