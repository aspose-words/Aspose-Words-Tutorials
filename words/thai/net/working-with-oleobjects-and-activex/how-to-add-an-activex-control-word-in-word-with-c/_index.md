---
category: general
date: 2026-09-30
description: เพิ่มคอนโทรล ActiveX ลงในเอกสาร Word ด้วย C# เรียนรู้วิธีแทรกปุ่ม ActiveX,
  เพิ่มปุ่มคำสั่ง, และทำให้สามารถคลิกได้.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: th
lastmod: 2026-09-30
og_description: เพิ่มคำควบคุม ActiveX ลงในเอกสาร Word ด้วย C# ทำตามคู่มือฉบับเต็มนี้เพื่อแทรกปุ่ม
  ActiveX, เพิ่มปุ่มคำสั่ง, และทำให้สามารถคลิกได้.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: เพิ่มคอนโทรล ActiveX ลงในเอกสาร Word – คู่มือ C# ทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: วิธีเพิ่ม ActiveX Control ใน Word ด้วย C#
url: /th/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มคำควบคุม ActiveX ใน Word ด้วย C#

หากคุณต้องการฝัง **คำควบคุม ActiveX** ไว้ในไฟล์ Microsoft Word คำแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนทั้งหมดอย่างละเอียด คุณจะได้เห็นตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่งแทรกปุ่มที่คลิกได้ บันทึกเอกสาร และทำงานร่วมกับ Aspose.Words for .NET เวอร์ชันล่าสุด

การเพิ่มคำควบคุม ActiveX ช่วยให้คุณสร้างแบบฟอร์มเชิงโต้ตอบ กล่องโต้ตอบแบบกำหนดเอง หรือองค์ประกอบ UI ง่าย ๆ ที่ทำงานเหมือนกับควบคุมของ Word ไม่ว่าจะเป็นการสร้างเทมเพลตสัญญาที่ต้องการการโต้ตอบของผู้ใช้ หรือรายงานที่ต้องการปุ่ม “Run” ขั้นตอนต่อไปนี้ครอบคลุมทุกอย่างที่คุณต้องการ

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือใหม่กว่า (โค้ดนี้ยังทำงานได้กับ .NET Framework 4.8)
* Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ C#)
* Aspose.Words for .NET ติดตั้งแล้ว (`dotnet add package Aspose.Words`)
* ความเข้าใจพื้นฐานเกี่ยวกับ C# และโครงสร้างเอกสาร Word

> **เคล็ดลับ:** เมธอด `InsertForms2OleControl` ทำงานได้เฉพาะกับควบคุม “Forms 2.0” แบบดั้งเดิม ซึ่งเป็น ActiveX control ที่ Word ใช้สำหรับฟิลด์ฟอร์ม หากคุณกำหนดเป้าหมายเป็น Office เวอร์ชันใหม่ ควบคุมนี้ยังคงแสดงผลอย่างถูกต้องในไคลเอนต์เดสก์ท็อป

## ขั้นตอนที่ 1: ตั้งค่าโครงการและนำเข้า namespace

สร้างโปรเจกต์คอนโซลใหม่และเพิ่มคำสั่ง `using` ที่จำเป็น ซึ่งจะทำให้คอมไพเลอร์ค้นหาคลาส `Document`, `DocumentBuilder` และ `OleControlType` ได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Namespace `Aspose.Words` ให้ API ระดับสูงสำหรับการประมวลผล Word ส่วน `Aspose.Words.Drawing` มี enumeration `OleControlType` ที่ใช้ระบุประเภทของ ActiveX control

## ขั้นตอนที่ 2: โหลดเอกสาร Word ต้นฉบับ

คุณต้องเริ่มจากไฟล์ Word ที่ต้องการแก้ไข โค้ดต่อไปนี้จะโหลด `input.docx` จากโฟลเดอร์ที่คุณระบุ

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

หากไฟล์ไม่พบ Aspose.Words จะโยน `FileNotFoundException` ให้ใส่โค้ดในบล็อก `try/catch` หากต้องการจัดการข้อผิดพลาดอย่างสุภาพ

## ขั้นตอนที่ 3: สร้าง DocumentBuilder เพื่อแก้ไขเอกสาร

`DocumentBuilder` เป็นเครื่องมือหลักสำหรับแทรกข้อความ รูปภาพ และควบคุมต่าง ๆ มันจะรักษาตำแหน่งเคอร์เซอร์ที่บ่งบอกตำแหน่งที่องค์ประกอบถัดไปจะถูกวาง

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

โดยค่าเริ่มต้น เคอร์เซอร์ของ builder จะอยู่ที่จุดเริ่มต้นของเซคชันแรก คุณสามารถย้ายตำแหน่งด้วยเมธอดเช่น `MoveToDocumentEnd()` หรือ `MoveToParagraph(index)` หากต้องการให้ปุ่มอยู่ที่อื่น

## ขั้นตอนที่ 4: แทรกควบคุม ActiveX CommandButton

ตอนนี้มาถึงหัวใจของบทเรียน: การแทรก **คำควบคุม ActiveX** ที่ปรากฏเป็นปุ่มที่คลิกได้ เมธอด `InsertForms2OleControl` รับอาร์กิวเมนต์สองค่า คือ ประเภทของควบคุมและคำบรรยาย (หรือชื่อ) ของควบคุม

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **ทำไมต้องใช้ `OleControlType.CommandButton`?**  
  มันบอก Word ให้สร้างปุ่ม Forms 2.0 แบบคลาสสิก ซึ่งจะแสดงคำบรรยายและสามารถเชื่อมต่อกับมาโครหรือสคริปต์ VBA ได้ในภายหลัง

* **คำบรรยายทำหน้าที่อะไร?**  
  สตริง `"ClickMe"` จะกลายเป็นข้อความที่แสดงบนปุ่ม คุณสามารถเปลี่ยนเป็นข้อความใดก็ได้ที่เหมาะกับ UI ของคุณ

### แทรกปุ่มในตำแหน่งเฉพาะ

หากต้องการให้ปุ่มอยู่หลังย่อหน้าที่กำหนด ให้ย้าย builder ก่อน:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## ขั้นตอนที่ 5: บันทึกเอกสารที่แก้ไขแล้ว

หลังจากแทรกควบคุมแล้ว ให้บันทึกการเปลี่ยนแปลงลงไฟล์ใหม่ (หรือเขียนทับไฟล์เดิม)

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

เมื่อคุณเปิด `output.docx` ใน Word เวอร์ชันเดสก์ท็อป คุณจะเห็นปุ่มที่มีข้อความ **ClickMe** (หรือ **Submit** ขึ้นอยู่กับคำบรรยายที่คุณตั้ง) การคลิกปุ่มในโหมดออกแบบจะไม่มีผลใด ๆ โดยค่าเริ่มต้น; คุณสามารถกำหนดมาโครให้ภายหลังผ่านแท็บ “Developer” ของ Word

## ตัวอย่างเต็มที่ทำงานได้

ด้านล่างเป็นโปรแกรมที่รวมทุกขั้นตอนไว้ในไฟล์เดียว คัดลอกไปวางใน `Program.cs` ของแอปคอนโซลใหม่แล้วรัน

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

* คอนโซลจะแสดงข้อความสำเร็จพร้อมเส้นทางของไฟล์ผลลัพธ์
* การเปิด `output.docx` จะเห็นปุ่ม **ClickMe** ปรากฏในตำแหน่งที่ builder แทรกไว้
* สามารถเลือก ปรับขนาด หรือกำหนดมาโครให้ปุ่มผ่าน **Developer → Design Mode** ของ Word ได้

## คำถามที่พบบ่อยและการจัดการกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **จะใส่ปุ่ม ActiveX ในส่วนหัว/ส่วนท้ายอย่างไร?** | ย้าย builder ไปที่ส่วนหัว/ส่วนท้ายด้วย `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` ก่อนเรียก `InsertForms2OleControl`. |
| **ถ้าต้องการเช็คบ็อกซ์แทนปุ่มทำอย่างไร?** | ใช้ `OleControlType.CheckBox` และกำหนดคำบรรยายเช่น `"Agree"`. |
| **ปุ่มจะทำงานใน Word Online หรือไม่?** | ไม่ทำงาน Word Online ไม่รองรับ ActiveX Forms 2.0 ควบคุมนี้จะแสดงผลเฉพาะในไคลเอนต์เดสก์ท็อปเท่านั้น. |
| **สามารถกำหนดขนาดของปุ่มผ่านโค้ดได้หรือไม่?** | หลังแทรกแล้ว ให้ดึงอ็อบเจกต์ `Shape` ผ่าน `builder.CurrentParagraph.Runs[0].GetShape()` แล้วปรับ `Width`/`Height`. |
| **มีวิธีกำหนดมาโครให้ปุ่มจากโค้ดหรือไม่?** | Aspose.Words ไม่เปิดเผยการแก้ไขมาโคร คุณต้องเปิดเอกสารใน Word แล้วแนบมาโครด้วยตนเอง หรือใช้ Office Interop API. |

## เคล็ดลับสำหรับการใช้งานในสภาพแวดล้อมจริง

* **หลีกเลี่ยงการใช้เส้นทางแบบฮาร์ดโค้ด** – ใช้ `Path.Combine` และไฟล์กำหนดค่า
* **Dispose `Document`** – ห่อไว้ใน `using` หากทำงานกับไฟล์ขนาดใหญ่เพื่อคืนหน่วยความจำทันที
* **ตรวจสอบผลลัพธ์** – ตรวจสอบโปรแกรมmatically ว่าเอกสารมี shape ประเภท `OleControl` โดยวน `doc.GetChildNodes(NodeType.Shape, true)`
* **หมายเหตุด้านความปลอดภัย** – ควบคุม ActiveX สามารถรันโค้ดบนเครื่องลูกค้าได้ จัดจำหน่ายเอกสารให้กับผู้ใช้ที่เชื่อถือได้เท่านั้นและพิจารณาใช้ลายเซ็นดิจิทัล

## สรุป

คุณได้เรียนรู้วิธีเพิ่ม **คำควบคุม ActiveX** ลงในเอกสาร Word ด้วย C# โดยการโหลดเอกสาร สร้าง `DocumentBuilder` แทรกปุ่มคำสั่งด้วย `InsertForms2OleControl` และบันทึกไฟล์ คุณสามารถอัตโนมัติการสร้างฟอร์ม Word เชิงโต้ตอบได้ ทดลองใช้ค่า `OleControlType` อื่น ๆ วางควบคุมในส่วนหัวหรือในตาราง และผสานกับมาโครเพื่อประสบการณ์ผู้ใช้ที่สมบูรณ์ยิ่งขึ้น

---

*ขั้นตอนต่อไป*: สำรวจ **วิธีแทรก ActiveX** ควบคุมประเภทอื่น ๆ เรียนรู้ **วิธีเพิ่มตัวจัดการเหตุการณ์ปุ่มคำสั่ง** ผ่าน VBA และอ่านเกี่ยวกับ **แนวทางปฏิบัติที่ดีที่สุดสำหรับการแทรกปุ่ม ActiveX** เพื่อความเข้ากันได้ข้ามแพลตฟอร์ม


## สิ่งที่คุณควรเรียนต่อไป


บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบทางเลือกในโปรเจกต์ของคุณ

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}