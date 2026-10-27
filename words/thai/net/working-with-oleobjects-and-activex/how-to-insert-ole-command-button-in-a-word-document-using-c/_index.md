---
category: general
date: 2026-10-07
description: เรียนรู้วิธีแทรกปุ่มคำสั่ง OLE ในเอกสาร Word ด้วย Aspose.Words C# คู่มือทีละขั้นตอนที่ครอบคลุม
  DocumentBuilder, คุณสมบัติ และการบันทึกไฟล์
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: th
lastmod: 2026-10-07
og_description: แทรกปุ่มคำสั่ง OLE ในเอกสาร Word ด้วย C# ทำตามบทแนะนำสั้น ๆ นี้เพื่อเพิ่ม,
  กำหนดค่า และบันทึกปุ่ม CommandButton ที่ทำงานได้ด้วย Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: แทรกปุ่มคำสั่ง OLE ใน Word ด้วย C# – คู่มือ Aspose.Words ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: วิธีแทรกปุ่มคำสั่ง OLE ในเอกสาร Word ด้วย C#
url: /th/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทรกปุ่มคำสั่ง OLE ในเอกสาร Word ด้วย C#

หากคุณต้องการ **แทรกปุ่มคำสั่ง OLE** ลงในไฟล์ Word ด้วยโปรแกรม, คู่มือนี้จะแสดงให้คุณทราบอย่างละเอียดว่าทำอย่างไรด้วย Aspose.Words for .NET ไม่ว่าคุณจะสร้างรายงานที่มีแบบฟอร์มกรอกหรือทำอัตโนมัติเทมเพลตที่ต้องการการโต้ตอบจากผู้ใช้ ขั้นตอนต่อไปนี้จะให้โซลูชันที่สมบูรณ์และสามารถรันได้

คุณจะได้เรียนรู้วิธีสร้างเอกสารเปล่า, ใช้ `DocumentBuilder` เพื่อวาง `Forms2OleControl`, ตั้งค่าคำบรรยายและชื่อของปุ่ม, และสุดท้ายบันทึกเป็นไฟล์ `.docx` ไม่จำเป็นต้องใช้เครื่องมือภายนอกใด ๆ นอกจากไลบรารี Aspose.Words

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน, โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานได้กับ .NET Framework 4.7+)
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้องหรือคีย์ทดลองฟรี
* Visual Studio 2022 (หรือ IDE C# ใด ๆ ที่คุณชอบ)
* ความคุ้นเคยพื้นฐานกับไวยากรณ์ C# และแนวคิด OLE ของ Word

> **เคล็ดลับ:** หากคุณใช้รุ่นทดลองฟรี, เอกสารที่สร้างจะมีลายน้ำขนาดเล็ก ปลั๊กอินที่มีใบอนุญาตจะลบลายน้ำโดยอัตโนมัติ

## ขั้นตอนที่ 1: ติดตั้ง Aspose.Words

เพิ่มแพคเกจ Aspose.Words ไปยังโปรเจกต์ของคุณผ่าน NuGet:

```bash
dotnet add package Aspose.Words
```

แพคเกจนี้รวมเนมสเปซ `Aspose.Words.Drawing` และ `Aspose.Words.Drawing.Ole` ที่จำเป็นสำหรับคอนโทรล OLE

## ขั้นตอนที่ 2: แทรกปุ่มคำสั่ง OLE ด้วย DocumentBuilder

หัวใจของบทเรียนคือเมธอด `InsertForms2OleControl` ซึ่งจะสร้าง **Forms2 OLE CommandButton** ที่ตำแหน่งและขนาดที่กำหนด

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### ทำไมวิธีนี้ถึงได้ผล

* `DocumentBuilder` เป็น API หลักสำหรับสร้างเอกสาร Word ด้วยโปรแกรม  
* `InsertForms2OleControl` บอก Aspose.Words ให้ฝัง **Forms2 OLE control** ซึ่งเป็นเทคโนโลยีฟอร์มของ Word รุ่นเก่าที่รองรับปุ่มคำสั่ง, ช่องทำเครื่องหมาย ฯลฯ  
* ค่า enum `OleControlType.CommandButton` ระบุว่าคอนโทรลที่แทรกเป็น **ปุ่มคำสั่ง** — ประเภทที่คุณต้องการเมื่อ **แทรกปุ่มคำสั่ง OLE**  
* `Rectangle` กำหนดตำแหน่งการแสดงผล ปรับพิกัด X/Y หรือความกว้าง/ความสูงให้ตรงกับการจัดวางของคุณ

## ขั้นตอนที่ 3: บันทึกเอกสาร

หลังจากตั้งค่าปุ่มแล้ว, เขียนเอกสารลงดิสก์ คุณสามารถเลือกฟอร์แมตใดก็ได้ที่ Aspose.Words รองรับ (`.docx`, `.pdf`, `.odt`, …) สำหรับบทเรียนนี้เราจะบันทึกเป็นเอกสาร Word

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

เมื่อคุณเปิด `CommandButton.docx` ใน Microsoft Word, คุณจะเห็นปุ่มที่คลิกได้ที่มีข้อความ **Click Me** การกดปุ่มใน Word จะเปิดกล่องโต้ตอบ “Run Macro” เริ่มต้น เนื่องจากปุ่มเป็นคอนโทรลฟอร์ม OLE; คุณสามารถผูกแมโครหรือโค้ด VBA ต่อไปได้หากต้องการ

## ขั้นตอนที่ 4: ตรวจสอบผลลัพธ์ (ผลลัพธ์ที่คาดหวัง)

เปิดไฟล์ที่สร้างขึ้น:

1. ปุ่มปรากฏที่พิกัดที่คุณระบุ (ประมาณ 1.4 in จากซ้ายและบนของหน้า)  
2. ข้อความบนปุ่มเป็น **Click Me**  
3. คุณสมบัติ Name (`cmdSubmit`) ปรากฏในแผง **Developer → Properties** ของ Word ซึ่งมีประโยชน์เมื่อคุณต้องอ้างอิงคอนโทรลจาก VBA  

![ตัวอย่างการแทรกปุ่มคำสั่ง OLE ในเอกสาร Word](insert-ole-button.png)

*ข้อความแทนภาพ*: **ตัวอย่างการแทรกปุ่มคำสั่ง OLE ในเอกสาร Word** (รวมคีย์เวิร์ดหลักสำหรับการเข้าถึงและ SEO)

## กรณีขอบและคำถามทั่วไป

### 1. ถ้าปุ่มไม่ปรากฏตรงที่คาดหวัง?

* Word ใช้หน่วย point ไม่ใช่พิกเซล แปลงพิกเซลของหน้าจอเป็น point (`points = pixels * 72 / DPI`).  
* ตรวจสอบให้แน่ใจว่า Rectangle ไม่ตัดกับขอบกระดาษ มิฉะนั้น Word อาจย้ายคอนโทรล

### 2. ฉันสามารถแทรกปุ่มลงในเอกสารที่มีอยู่ได้หรือไม่?

ได้. โหลดเอกสารด้วย `new Document("Existing.docx")` และใช้ workflow ของ `DocumentBuilder` เดียวกัน เพียงจำไว้ว่าให้ย้ายเคอร์เซอร์ของ builder (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")` ฯลฯ) ก่อนเรียก `InsertForms2OleControl`.

### 3. ฉันจะผูกแมโครกับปุ่มได้อย่างไร?

Aspose.Words ไม่สร้างโค้ด VBA, แต่คุณสามารถฝังแมโครหลังจากที่เอกสารถูกสร้างแล้ว:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. วิธีนี้ทำงานกับ .NET Core บน Linux หรือไม่?

คอนโทรล OLE เป็นฟีเจอร์เฉพาะ Windows เนื่องจากพึ่งพา COM บน Linux ปุ่มจะถูกแทรกแต่จะแสดงเป็นภาพคงที่โดยไม่มีพฤติกรรมเชิงโต้ตอบ สำหรับฟอร์มเชิงโต้ตอบข้ามแพลตฟอร์ม, พิจารณาใช้คอนเทนท์คอนโทรล (`StructuredDocumentTag`) แทน

### 5. ถ้าฉันต้องการขนาดอื่นหรือหลายปุ่มล่ะ?

สร้างอ็อบเจกต์ `Rectangle` เพิ่มเติมด้วยพิกัดที่ไม่ซ้ำกันและเรียก `InsertForms2OleControl` ซ้ำแต่ละครั้ง ปุ่มแต่ละปุ่มสามารถมี `Caption` และ `Name` ของตนเองได้

## ตัวอย่างการทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปพลิเคชันคอนโซล มันรวม `using` directive ที่จำเป็น, การจัดการข้อผิดพลาด, และคอมเมนต์

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

เรียกใช้โปรแกรม, เปิด `CommandButton.docx` ที่สร้างขึ้น, คุณจะเห็นปุ่ม **Click Me** พร้อมใช้งานสำหรับการปรับแต่งต่อไป

## สรุป

คุณได้เรียนรู้วิธี **แทรกปุ่มคำสั่ง OLE** ลงในเอกสาร Word ด้วย C# และ Aspose.Words บทเรียนนี้ครอบคลุม:

* การติดตั้งแพคเกจ Aspose.Words  
* การใช้ `DocumentBuilder.InsertForms2OleControl` กับ `OleControlType.CommandButton`  
* การตั้งค่าคุณสมบัติของปุ่ม (`Caption`, `Name`)  
* การบันทึกและตรวจสอบผลลัพธ์  

จากนี้คุณสามารถสำรวจหัวข้อที่เกี่ยวข้องเช่น **Aspose.Words OLE control** สำหรับช่องทำเครื่องหมาย, คอมโบบ็อกซ์, หรือการฝังเวิร์กชีต Excel ทั้งหมด คุณอาจทดลองทำอัตโนมัติ **Word OLE command button** ในเทมเพลตขนาดใหญ่, หรือเปลี่ยนคอนโทรล OLE เป็น **content controls** สมัยใหม่เพื่อรองรับข้ามแพลตฟอร์มได้ดียิ่งขึ้น

อย่าลังเลที่จะปรับค่า rectangle, เพิ่มหลายปุ่ม, หรือผูกแมโคร VBA เพื่อให้ตรงกับความต้องการของแอปพลิเคชันของคุณ. Happy coding!

## สิ่งที่คุณควรเรียนต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ

- [แทรกวัตถุ Ole ในเอกสาร Word](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [แทรกวัตถุ Ole ในเอกสาร Word เป็นไอคอน](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [แทรกวัตถุ Ole ใน Word ด้วย Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}