---
category: general
date: 2026-08-14
description: วิธีเพิ่ม SDT อย่างรวดเร็วด้วย Aspose.Words เรียนรู้การสร้างตัวแทนคำและแทรกการควบคุมข้อความธรรมดาในไฟล์
  .docx
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: th
lastmod: 2026-08-14
og_description: วิธีเพิ่ม SDT ใน C# ด้วย Aspose.Words. ทำตามบทแนะนำนี้เพื่อสร้างตัวแทนคำใน
  Word และแทรกการควบคุมข้อความธรรมดาสำหรับเอกสารแบบไดนามิก.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: วิธีเพิ่ม SDT ใน C# – คู่มือ Word placeholder แบบทำตามขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: วิธีเพิ่ม SDT ใน C# – คู่มือฉบับสมบูรณ์สำหรับตัวแทนใน Word
url: /th/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่ม SDT ใน C# – คู่มือเต็มสำหรับตัวแทน Word

หากคุณต้องการ **how to add sdt** ในไฟล์ Word, บทแนะนำนี้จะแสดงขั้นตอนที่แน่นอนโดยใช้ Aspose.Words for .NET. เมื่อจบคู่มือคุณจะสามารถ **create word placeholder** แท็กที่ให้ผู้ใช้พิมพ์โดยตรงในเอกสาร, และคุณจะเข้าใจวิธี **insert plain text control** อย่างเชื่อถือได้.

การทำงานกับ Structured Document Tags (SDTs) ช่วยขจัดความจำเป็นของฟิลด์ฟอร์มแบบแมนนวลและให้วิธีที่เป็นระเบียบและโปรแกรมเมติกในการสร้างสัญญา, รายงาน หรือจดหมายแบบไดนามิก ตัวอย่างด้านล่างครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโครงการจนถึงการบันทึกไฟล์ .docx สุดท้าย, เพื่อให้คุณสามารถคัดลอก‑วางโค้ดไปยังโซลูชันของคุณเองโดยไม่พลาดการพึ่งพาใดๆ.

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+)
- Visual Studio 2022 หรือ IDE C# ใดๆ ที่คุณชอบ
- ไลเซนส์ Aspose.Words for .NET (ไลเซนส์ชั่วคราวฟรีใช้สำหรับการทดสอบได้)
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C# และแนวคิดของ SDTs

> **เคล็ดลับ:** หากคุณวางแผนจะแจกจ่ายเอกสารที่สร้างขึ้น, ให้ฝังไฟล์ไลเซนส์เพื่อหลีกเลี่ยงลายน้ำการประเมินผล.

## ขั้นตอนที่ 1: ตั้งค่าโครงการและนำเข้า Aspose.Words

สร้างแอปพลิเคชันคอนโซลใหม่และเพิ่มแพคเกจ NuGet ของ Aspose.Words:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

คำสั่ง `using` เหล่านี้ให้คุณเข้าถึงคลาส `Document`, `DocumentBuilder`, และ `StructuredDocumentTag` ที่จำเป็นสำหรับการทำงาน **insert plain text control**.

## ขั้นตอนที่ 2: เริ่มต้นเอกสารและ Builder

บล็อกโค้ดแรกสร้างเอกสาร Word ว่างเปล่าและ `DocumentBuilder` ที่ให้คุณเขียนเนื้อหาเข้าไปในเอกสาร

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` ทำงานเหมือนเคอร์เซอร์; การเรียกต่อไปทุกครั้งจะเพิ่มเนื้อหาที่ตำแหน่งปัจจุบัน การเริ่มต้นเอกสารเป็นพื้นฐานสำหรับทุกสถานการณ์ **how to add sdt** เนื่องจาก SDT ต้องเป็นส่วนหนึ่งของอินสแตนซ์ `Document` ที่ใช้งานอยู่.

## ขั้นตอนที่ 3: แทรก Structured Document Tag (SDT) แบบข้อความธรรมดา

ตอนนี้เราจะ **insert plain text control** ซึ่งทำหน้าที่เป็นตัวแทนที่ผู้ใช้สามารถพิมพ์ชื่อ, วันที่, หรือค่าที่กำหนดเองได้.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` บอก Aspose.Words ให้สร้างฟิลด์ข้อความแบบง่าย.
- `SdtAppearanceTags.Default` ให้แท็กมีสไตล์การแสดงผลมาตรฐานของ Word (กล่องสีเทาเมื่อเปิดเอกสารใน Word).

## ขั้นตอนที่ 4: กำหนดค่า SDT ด้วยชื่อและข้อความตัวแทน

SDT ที่ตั้งชื่ออย่างเหมาะสมทำให้เอกสารอธิบายตัวเองได้สำหรับผู้ใช้ปลายทาง ที่นี่เราจะ **create word placeholder** เมทาดาต้าและตั้งค่าคำแนะนำที่ปรากฏภายในฟิลด์.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` คือรหัสภายในที่คุณสามารถใช้ในภายหลังเมื่อดึงหรืออัปเดตค่าผ่านโปรแกรม.
- `PlaceholderName` คือคำแนะนำสีเทาที่แสดงใน Word, บอกผู้ใช้ว่าต้องพิมพ์อะไร.

## ขั้นตอนที่ 5: เพิ่มเนื้อหารอบข้าง

เอกสารมักไม่ใช่แค่ SDT เดียว คุณมักต้องการย่อหน้าปกติก่อนและหลังตัวแทน ใช้วิธี `WriteLine` ของ builder เพื่อเพิ่มข้อความคงที่.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

การเรียก `InsertNode` จะวาง SDT ที่สร้างไว้ก่อนหน้านี้ตรงตำแหน่งที่ต้องการ, รักษาการไหลของข้อความรอบข้าง.

## ขั้นตอนที่ 6: บันทึกเอกสารเป็นไฟล์ .docx

สุดท้าย, บันทึกเอกสารลงดิสก์. เส้นทางอาจเป็นแบบเต็มหรือสัมพันธ์กับโฟลเดอร์โครงการ.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

การเปิด `SDT.docx` ใน Microsoft Word จะแสดงตัวแทนสีเทาที่มีข้อความ **Enter name here**. ผู้ใช้สามารถคลิกฟิลด์, พิมพ์ค่า, และเอกสารจะเก็บค่าดังกล่าวเมื่อบันทึกอีกครั้ง.

## ตัวอย่างเต็มที่สามารถรันได้

การรวมส่วนต่างๆ เข้าด้วยกันให้คุณได้โปรแกรมที่เป็นอิสระและสามารถรันได้ทันที:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง** เมื่อคุณรันโปรแกรม:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

การเปิด `SDT.docx` ที่สร้างขึ้นจะแสดง:

```
Dear [Enter name here],
After the SDT
```

ข้อความในวงเล็บเป็นตัวแทน **insert plain text control** ที่ผู้ใช้สามารถแทนที่ได้.

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | วิธีปรับโค้ด |
|-----------|-----------------------|
| **Multiple placeholders** | เรียก `InsertStructuredDocumentTag` ซ้ำหลายครั้งและให้แต่ละแท็กมี `Title` ที่ไม่ซ้ำกัน. |
| **Rich‑text SDT** | ใช้ `StructuredDocumentTagType.RichText` แทน `PlainText`. |
| **Lock the placeholder** | ตั้งค่า `plainTextTag.LockContentControl = true;` เพื่อป้องกันผู้ใช้ลบฟิลด์. |
| **Pre‑populate with a value** | กำหนด `plainTextTag.Text = "John Doe";` ก่อนบันทึก. |
| **Conditional appearance** | ใช้ `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` สำหรับควบคุมแบบกล่องกาเครื่องหมาย. |

การแปรผันเหล่านี้ทำให้คุณสามารถ **create word placeholder** โครงสร้างที่ตรงกับสถานการณ์แบบฟอร์มใดๆ เกือบทั้งหมด.

## เคล็ดลับการแก้ไขปัญหา

- **Placeholder not visible** – ตรวจสอบว่าคุณเปิดไฟล์ใน Microsoft Word (หรือโปรแกรมดูที่รองรับ). บางโปรแกรมแก้ไขที่เบาอาจซ่อน SDTs.
- **License warning** – หากคุณเห็นลายน้ำการประเมินผล, ตรวจสอบว่าไฟล์ไลเซนส์ของคุณโหลดอย่างถูกต้อง (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – หลังจากแทรก SDT, เคอร์เซอร์ของ builder จะอยู่ *หลัง* แท็ก. หากต้องการเพิ่มข้อความ *ภายใน* แท็ก, ใช้ `builder.MoveTo(plainTextTag);` ก่อนเขียน.

## สรุป

ตอนนี้คุณรู้แล้วว่า **how to add sdt** ในเอกสาร Word ด้วย Aspose.Words for .NET, วิธี **create word placeholder** แท็ก, และวิธี **insert plain text control** ที่ผู้ใช้สามารถแก้ไขโดยตรงใน Word ตัวอย่างเต็มแสดงการเริ่มต้น, การแทรกแท็ก, การกำหนดค่า, เนื้อหารอบข้าง, และการบันทึก—ทั้งหมดในโปรแกรมเดียวที่สามารถรันได้.

ต่อไป, สำรวจหัวข้อที่เกี่ยวข้องเช่น **insert rich text control**, **populate SDTs from a database**, หรือ **convert the final document to PDF**. ทั้งหมดนี้อิงจากพื้นฐานเดียวกันที่อธิบายไว้ที่นี่, ทำให้คุณสามารถขยายสายงานอัตโนมัติของคุณได้อย่างมั่นใจ.

ขอให้สนุกกับการเขียนโค้ด, และอย่าลังเลที่จะทดลองใช้ประเภท SDT ต่างๆ เพื่อให้ตรงกับความต้องการการอัตโนมัติเอกสารของคุณ!

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แหล่งข้อมูลแต่ละรายการรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโครงการของคุณ.

- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [วิธีสร้าง Editable Ranges ในเอกสารแบบอ่านอย่างเดียวโดยใช้ Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [เพิ่ม Bookmarks Word ด้วย Aspose.Words for Java – แทรก, อัปเดต, ลบ](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}