---
category: general
date: 2026-07-19
description: สร้างเอกสาร Word ด้วย Aspose.Words C# และเรียนรู้วิธีเพิ่มปุ่มคำสั่ง
  ActiveX ตั้งขนาดปุ่ม และแทรกปุ่มโดยโปรแกรม.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: th
lastmod: 2026-07-19
og_description: สร้างเอกสาร Word ด้วย Aspose.Words C# และฝังปุ่มคำสั่ง ActiveX ได้ในไม่กี่วินาที
  ทำตามคู่มือขั้นตอนต่อขั้นตอนเพื่อกำหนดขนาดปุ่มและแทรกปุ่มได้อย่างง่ายดาย
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: สร้างเอกสาร Word ด้วยปุ่ม ActiveX – บทเรียน C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: สร้างเอกสาร Word ด้วยปุ่ม ActiveX – คู่มือ C#
url: /th/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word พร้อมปุ่ม ActiveX – คู่มือ C# ฉบับสมบูรณ์

เคยสงสัยไหมว่า **create word document** ที่มีปุ่ม ActiveX ทำงานได้จริงเป็นอย่างไร? บางทีคุณอาจกำลังทำอัตโนมัติรายงานและต้องการควบคุม “Approve” ที่คลิกได้อยู่ในไฟล์โดยตรง ในบทแนะนำนี้เราจะพาคุณผ่านขั้นตอนทั้งหมด—โดยใช้ Aspose.Words for .NET เพื่อเพิ่มปุ่มคำสั่ง ActiveX ตั้งค่าขนาดของมันและแทรกลงในตำแหน่งที่ต้องการ  

หากคุณเคยถามตัวเองว่า *how to add activex* โดยไม่ต้องเปิด Word ด้วยตนเอง คุณมาถูกที่แล้ว เมื่อจบคุณจะได้ตัวอย่างที่สามารถรันได้ คำอธิบายที่ชัดเจนของแต่ละขั้นตอน และเคล็ดลับในการจัดการกับปัญหาที่พบบ่อย

## สิ่งที่คุณจะได้เรียนรู้

- วิธีตั้งค่า Aspose.Words ในโปรเจกต์ C#  
- โค้ดที่แม่นยำเพื่อ **create word document** และฝังปุ่มคำสั่ง ActiveX  
- วิธี **set button size** และปรับแต่งคำบรรยายและชื่อของปุ่ม  
- วิธีที่ถูกต้องในการ **insert command button** และ **how to insert button** ในตำแหน่งใดก็ได้ในเอกสาร  
- การพิจารณาในกรณีขอบ (Word version, platform limits, security warnings)

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานบน .NET Framework 4.7+)  
- ไลเซนส์ Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ทดลองใช้ฟรี)  
- Visual Studio 2022 (หรือ IDE ใดก็ได้ที่คุณชอบ)  
- ความคุ้นเคยพื้นฐานกับ C# และการเขียนโปรแกรมเชิงวัตถุ  

ไม่จำเป็นต้องใช้ไลบรารีของบุคคลที่สามอื่นใด

---

## ขั้นตอนที่ 1: สร้างเอกสาร Word – การตั้งค่าโปรเจกต์

ก่อนที่เราจะ **insert command button** เราต้องมีไฟล์ Word เปล่าสำหรับทำงาน ขั้นตอนนี้ยังแสดงรูปแบบคลาสสิกของ “create word document” ด้วย Aspose.Words

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **ทำไมจึงสำคัญ:** `Document` แทนไฟล์ .docx ทั้งไฟล์ ในขณะที่ `DocumentBuilder` ติดตามตำแหน่งเคอร์เซอร์ปัจจุบัน การแทรกทั้งหมด (รวมถึงคอนโทรล ActiveX ของเรา) จะทำงานสัมพันธ์กับ builder นี้

---

## ขั้นตอนที่ 2: วิธีเพิ่ม ActiveX – สร้างคอนโทรล CommandButton

ตอนนี้เอกสารพร้อมแล้ว เรามาแก้ไขส่วน **how to add activex** กัน Aspose.Words มีคลาส `Forms2OleControl` สำหรับอ็อบเจ็กต์ ActiveX ที่นี่เราจะสร้างปุ่มคำสั่งและกำหนดคุณสมบัติต่าง ๆ รวมถึงความต้องการ **set button size**

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **เคล็ดลับ:** ขนาดวัดเป็นจุด (1 point = 1/72 นิ้ว) ปรับค่าตามการจัดวางของคุณ; สำหรับปุ่มบนแถบเครื่องมือทั่วไป 120 × 30 ทำงานได้ดี

---

## ขั้นตอนที่ 3: แทรกปุ่มคำสั่ง – แกนหลักของ **Insert Command Button**

เมื่อคอนโทรลพร้อม เราจะ **insert command button** ลงในเอกสารที่ตำแหน่งปัจจุบันของ builder คุณสามารถย้าย builder ไปที่ใดก็ได้ (เช่น หลังย่อหน้า) ก่อนเรียกเมธอดนี้

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

หากต้องการ **how to insert button** ที่บุ๊คมาร์คเฉพาะ เพียงย้าย builder ก่อน:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **เกิดอะไรขึ้นเบื้องหลัง?** Aspose.Words จะเขียนสตรีมอ็อบเจ็กต์ OLE ที่จำเป็นลงในแพ็กเกจ .docx ทำให้ Word สามารถแสดงปุ่มได้โดยไม่ต้องใช้มาโครเพิ่มเติม

---

## ขั้นตอนที่ 4: บันทึกเอกสาร – สรุปวงจร **Create Word Document**

ขั้นตอนสุดท้ายง่ายมาก: บันทึกไฟล์ลงดิสก์ นี่คือการปิดรอบของ **create word document** ฝัง ActiveX และบันทึก

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

เปิดไฟล์ที่ได้ใน Microsoft Word (เฉพาะ Windows) คุณควรเห็นปุ่มที่คลิกได้ชื่อ “Click Me” การคลิกจะเรียก Action เริ่มต้นของ CommandButton—จะไม่มีอะไรเกิดขึ้นหากคุณไม่ได้แนบโค้ด VBA, แต่คอนโทรลทำงานเต็มที่

> **ผลลัพธ์ที่คาดหวัง:** ไฟล์ .docx หนึ่งหน้า มีปุ่มอยู่กึ่งกลางตำแหน่งแทรก ขนาด 120 × 30 pt มีคำบรรยาย “Click Me”.  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *ข้อความแทนภาพ:* **ActiveX button inserted into a Word document using C#** (matches `og_image_alt`).

---

## ขั้นตอนที่ 5: กรณีขอบ, ความปลอดภัย, และแนวปฏิบัติที่ดีที่สุด

### ข้อจำกัดของแพลตฟอร์ม
- คอนโทรล ActiveX ทำงานได้เฉพาะบน Word เวอร์ชัน Windows หากผู้ใช้ของคุณใช้ macOS หรือ Word Online ปุ่มจะปรากฏเป็นภาพคงที่  
- สภาพแวดล้อมองค์กรบางแห่งอาจปิดการใช้งาน ActiveX เพื่อความปลอดภัย; คุณอาจต้องลงนามเอกสารหรือแจ้งผู้ใช้ให้เปิดใช้งานเนื้อหา

### การโต้ตอบกับ VBA (ทางเลือก)
หากต้องการให้ปุ่มเรียกแมโคร คุณต้องเพิ่มโปรเจกต์ VBA ลงในเอกสารหลังจากบันทึก Aspose.Words ไม่ได้สร้างโค้ด VBA อัตโนมัติ แต่คุณสามารถใช้ API `Document.VbaProject` เพื่อแทรกได้

### การชนชื่อ
ควรให้แต่ละคอนโทรลมี `Name` ที่ไม่ซ้ำกัน การใช้ชื่อเดียวกันหลายครั้งอาจทำให้ Word เกิดข้อผิดพลาดขณะเรียกคอนโทรล

### เคล็ดลับประสิทธิภาพ
เมื่อต้องแทรกคอนโทรลหลายตัว ให้ใช้ `DocumentBuilder` ตัวเดียวและหลีกเลี่ยงการเรียก `doc.Save` ภายในลูป ทำการแทรกเป็นชุดแล้วบันทึกครั้งเดียวตอนจบ

---

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมที่พร้อมคัดลอก‑วาง:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

รันโปรแกรม เปิดไฟล์ที่บันทึกไว้ คุณจะเห็นปุ่มอยู่ตรงตำแหน่งที่ builder ตั้งไว้

---

## สรุป

เราได้ **created word document** ตั้งแต่ต้น, เรียนรู้ **how to add activex** ด้วยการกำหนด `Forms2OleControl`, ทำความเข้าใจคุณสมบัติ **set button size**, และแสดงวิธีที่ถูกต้องในการ **insert command button** และ **how to insert button** ที่ตำแหน่งใดก็ได้ในไฟล์  

จากตัวอย่างโค้ดเดียวนี้ คุณมีพื้นฐานที่แข็งแรงสำหรับการทำอัตโนมัติ Word ที่ซับซ้อนมากขึ้น—ไม่ว่าจะเป็นการสร้างเทมเพลตฟอร์มโต้ตอบ, สร้างสัญญาที่ต้องการการยืนยันจากผู้ใช้, หรือแค่ใส่คอนโทรลเล็ก ๆ ลงในรายงาน

### สิ่งที่ควรทำต่อไป

- **Style the button** – ปรับฟอนต์, สี, หรือเพิ่มภาพพื้นหลัง  
- **Attach VBA macros** – ทำให้ปุ่มทำการคำนวณหรือเปิดโปรแกรมภายนอก  
- **Combine with other controls** – เช็คบ็อกซ์, ลิสต์บ็อกซ์, หรือแม้กระทั่งแผ่นงาน Excel ฝังในเอกสาร  

ลองทดลองดูได้เลย หากเจอปัญหาใด ๆ คอมเมนต์ด้านล่างได้เลย ขอให้สนุกกับการเขียนโค้ดและการอัตโนมัติ Word ด้วย Aspose.Words!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ ทุกแหล่งข้อมูลมาพร้อมตัวอย่างโค้ดทำงานเต็มรูปแบบและคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบต่าง ๆ ในโปรเจกต์ของคุณ

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}