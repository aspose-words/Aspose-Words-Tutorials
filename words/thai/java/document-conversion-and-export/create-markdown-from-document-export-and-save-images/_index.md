---
category: general
date: 2026-02-18
description: สร้าง markdown จากเอกสารด้วยขั้นตอนง่าย ๆ เพื่อส่งออกเอกสารเป็น markdown
  และบันทึกรูปภาพลงในโฟลเดอร์ย่อย เรียนรู้วิธีบันทึกเอกสารเป็น markdown ด้วย C#
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: th
og_description: สร้าง markdown จากเอกสารด้วย C# และเรียนรู้วิธีส่งออกเอกสารเป็น markdown
  พร้อมบันทึกรูปภาพลงในโฟลเดอร์ย่อย ทำตามคู่มือขั้นตอนต่อขั้นตอน.
og_title: สร้าง Markdown จากเอกสาร – ส่งออกและบันทึกรูปภาพ
tags:
- C#
- Aspose.Words
- Markdown export
title: สร้างมาร์กดาวน์จากเอกสาร – ส่งออกและบันทึกภาพ
url: /th/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้าง markdown จากเอกสาร – ส่งออกและบันทึกรูปภาพ

เคยต้อง **สร้าง markdown จากเอกสาร** แล้วไม่แน่ใจว่าจะจัดการรูปภาพที่ฝังอยู่ให้เป็นระเบียบอย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายโครงการเราต้องสร้างรายงาน คู่มือ หรือร่างบล็อกโดยอัตโนมัติ และสิ่งที่เราไม่ต้องการคือไฟล์รูปภาพกระจัดกระจายอยู่ทั่วโฟลเดอร์ผลลัพธ์  

ในบทแนะนำนี้เราจะเดินผ่านโซลูชันที่พร้อม‑run อย่างครบถ้วนซึ่ง **ส่งออกเอกสารเป็น markdown**, เก็บรูปภาพทุกไฟล์ไว้ในโฟลเดอร์ย่อย *md‑resources* เฉพาะ, และสุดท้าย **บันทึกเอกสารเป็น markdown** ด้วย Aspose.Words for .NET API เมื่อจบคุณจะได้เมธอดเดียวที่สามารถนำไปใส่ในโค้ด C# ใดก็ได้ พร้อมกับเคล็ดลับเล็กน้อยสำหรับจัดการกรณีขอบ

> **ภาพรวมอย่างรวดเร็ว:**  
> • ตั้งค่า `MarkdownSaveOptions`  
> • ให้ `IResourceSavingCallback` ที่เปลี่ยนเส้นทางรูปภาพไปยังโฟลเดอร์ย่อย  
> • เรียก `Document.Save` พร้อมตัวเลือกที่กำหนดค่าไว้  

หากคุณอยากรู้ว่าทำไมเราถึงเลือกใช้ callback แทนการประมวลผลหลังจากส่งออกต่อไป อ่านต่อ – เหตุผลจะอธิบายทีละขั้นตอน

---

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+ ด้วย)  
- Aspose.Words for .NET (แพ็กเกจ NuGet `Aspose.Words`)  
- วัตถุ `Document` แหล่งที่มา (อาจเป็น .docx, .pdf, .rtf ฯลฯ)  

ไม่ต้องใช้ไลบรารีเพิ่มเติม; API ของ callback ถูกสร้างไว้ใน Aspose.Words แล้ว

---

## ขั้นตอนที่ 1: สร้าง markdown จากเอกสาร – กำหนดตัวเลือกการบันทึก

สิ่งแรกที่เราทำคือสร้างอินสแตนซ์ของ `MarkdownSaveOptions` วัตถุนี้บอก Aspose.Words ว่าการแปลงควรทำงานอย่างไร เช่น ใช้รูปแบบ Markdown ใด, จะฝังรูปภาพเป็น Base64 หรือไม่, และจะวางไฟล์ที่สร้างขึ้นที่ไหน

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **ทำไมเรื่องนี้ถึงสำคัญ:**  
> หากไม่ได้สร้าง `MarkdownSaveOptions` อย่างชัดเจน ไลบรารีจะใช้ค่าตั้งต้นที่ฝังรูปภาพลงในไฟล์ Markdown เป็นสตริง Base64 ทำให้ไฟล์ใหญ่โตและทำลายจุดประสงค์ของการมีโฟลเดอร์ *images* ที่แยกออกมาอย่างสะอาด

---

## ขั้นตอนที่ 2: ส่งออกเอกสารเป็น markdown และกำหนดการจัดการทรัพยากร

ต่อไปเราบอกตัวบันทึกว่า **จะวางรูปภาพแต่ละไฟล์ไว้ที่ไหน** อินเทอร์เฟซ `IResourceSavingCallback` ให้จุดเชื่อมต่อที่ทำงานสำหรับทุกทรัพยากร (รูปภาพ, SVG ฯลฯ) ที่พบระหว่างการส่งออก ภายใน callback เราจะทำ:

1. ตรวจสอบให้แน่ใจว่าโฟลเดอร์เป้าหมายมีอยู่ (`md-resources/`)  
2. ตั้งค่า `OutputFileName` ให้เป็นโฟลเดอร์บวกกับชื่อทรัพยากรเดิม  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **คำถามทั่วไป:** *ถ้าฉันต้องการฝังรูปภาพแทนการบันทึกล่ะ?*  
> เพียงข้าม callback หรือกำหนด `args.OutputFileName = null;` – ตัวบันทึกจะฝังรูปภาพเป็นสตริง Base64 โดยอัตโนมัติ

> **กรณีขอบ:** เอกสารบางฉบับเก่าอาจมีชื่อรูปภาพซ้ำกัน Callback ด้านบนจะเขียนทับไฟล์เดิม เพื่อหลีกเลี่ยงนั้นคุณสามารถต่อท้ายด้วย GUID ได้:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## ขั้นตอนที่ 3: บันทึกเอกสารเป็น markdown และตรวจสอบรูปภาพที่บันทึกไว้

เมื่อกำหนดตัวเลือกครบถ้วนแล้ว คำสั่งสุดท้ายเป็นบรรทัดเดียวที่เขียนไฟล์ Markdown และรูปภาพที่เกี่ยวข้องลงดิสก์

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

หากทุกอย่างทำงานได้ดี คุณจะเห็น:

- `MyReport.md` – ตัวแทน Markdown ของเอกสารต้นฉบับของคุณ  
- `md-resources/` – โฟลเดอร์ข้างไฟล์ .md ที่บรรจุรูปภาพที่แยกออกมาทั้งหมด (เช่น `image001.png`, `image002.jpg`)  

**ตัวอย่างส่วนของ Markdown** (สร้างโดยอัตโนมัติจาก Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **เคล็ดลับระดับมืออาชีพ:** เปิดไฟล์ `.md` ที่สร้างขึ้นใน VS Code หรือโปรแกรมดูตัวอย่าง Markdown ใดก็ได้; รูปภาพควรแสดงทันทีเพราะเส้นทางสัมพันธ์ตรงกับโครงสร้างโฟลเดอร์

---

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมคอนโซลแบบ self‑contained ที่คุณสามารถคัดลอกไปวางในโปรเจกต์ .NET ใหม่และรันได้ มันสร้างเอกสาร Word ง่าย ๆ เพิ่มรูปภาพหนึ่งรูป แล้ว **สร้าง markdown จากเอกสาร** พร้อมเก็บรูปภาพในโฟลเดอร์ย่อย

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**สิ่งที่คุณควรเห็น** หลังจากรัน:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

เปิด `ExportedDoc.md` – การอ้างอิงรูปภาพจะชี้ไปที่ `md-resources/sample-image.png` และรูปภาพจะปรากฏอย่างถูกต้องในตัวดู Markdown ใดก็ได้

---

## ความหลากหลายที่พบบ่อย

| สถานการณ์ | วิธีปรับโค้ด |
|----------|----------------------|
| **ข้ามการส่งออกรูปภาพ** (ฝังเป็น Base64) | ไม่ต้องใส่ `ResourceSavingCallback` เลย, หรือกำหนด `args.OutputFileName = null;` ภายใน callback |
| **เปลี่ยนรูปแบบรูปภาพ** (เช่น ทั้งหมดเป็น PNG) | ภายใน callback, แก้ไข `args.ResourceFileName` และอาจแปลงสตรีมก่อนเขียน |
| **เปลี่ยนชื่อโฟลเดอร์** | แทนที่ `"md-resources/"` ด้วยเส้นทางสัมพันธ์หรือเต็มที่คุณต้องการ |
| **หลายเอกสารในชุด** | วนลูปผ่านคอลเลกชันของวัตถุ `Document`, ใช้ `MarkdownSaveOptions` ตัวเดียวกัน (แค่ต้องแน่ใจว่าโฟลเดอร์ถูกล้างหรือมีชื่อเฉพาะต่อการรัน) |

---

## สรุป

เราได้แสดงให้คุณ **สร้าง markdown จากเอกสาร**, **ส่งออกเอกสารเป็น markdown**, และ **บันทึกรูปภาพลงโฟลเดอร์ย่อย** ด้วยวิธีที่สะอาดและขับเคลื่อนด้วย callback ประเด็นสำคัญคือ:

- ใช้ `MarkdownSaveOptions` เพื่อควบคุมการส่งออกอย่างละเอียด  
- Implement `IResourceSavingCallback` เพื่อชี้รูปภาพไปยังโฟลเดอร์เฉพาะ ทำให้ Markdown ของคุณเป็นระเบียบ  
- แพทเทิร์นเดียวกันนี้ทำงานกับประเภททรัพยากรอื่น (SVG, audio) – เพียงตรวจสอบ `args.ResourceType`  

ต่อไปคุณอาจสำรวจ **การบันทึกเอกสารเป็น markdown** พร้อมสไตล์หัวข้อที่กำหนดเอง, หรือรวมขั้นตอนนี้เข้าใน ASP.NET Web API ที่คืน ZIP ประกอบไฟล์ `.md` และทรัพยากรของมัน ไม่ว่าคุณจะเลือกทางไหน บล็อกการสร้างนี้ก็พร้อมให้คุณใช้แล้ว

มีคำถามหรือเจอกรณีที่เราไม่ได้ครอบคลุม? แสดงความคิดเห็นด้านล่าง แล้วขอให้สนุกกับการเขียนโค้ด!

---

![สร้าง markdown จากเอกสารตัวอย่าง](placeholder.png "สร้าง markdown จากเอกสารตัวอย่าง")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}