---
category: general
date: 2026-10-13
description: แทนที่ตัวแปรในไฟล์ docx ด้วย Aspose.Words และเรียนรู้วิธีเติมข้อมูลลงในเทมเพลต
  Word เพียงไม่กี่นาที
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- replace placeholders in docx
- fill word template with data
language: th
lastmod: 2026-10-13
og_description: แทนที่ตัวแปรในไฟล์ docx ด้วย Aspose.Words และเติมเทมเพลต Word ด้วยข้อมูล.
  ทำตามบทแนะนำแบบขั้นตอนต่อขั้นตอนนี้เพื่ออัตโนมัติการสร้างเอกสาร.
og_image_alt: Illustration of a Word document where {{FirstName}} and {{LastName}}
  have been replaced with real values
og_title: แทนที่ตัวแสดงตำแหน่งในไฟล์ docx – คู่มือเร็วสำหรับนักพัฒนา C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: replace placeholders in docx using Aspose.Words and learn to fill word
    template with data in a few minutes
  headline: How to replace placeholders in docx files with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีแทนที่ตัวแปรในไฟล์ docx ด้วย Aspose.Words
url: /th/net/find-and-replace-text/how-to-replace-placeholders-in-docx-files-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทนที่ตัวแปรในไฟล์ docx ด้วย Aspose.Words

หากคุณต้องการ **แทนที่ตัวแปรในไฟล์ docx** นี้ คู่มือนี้จะแสดงวิธีทำด้วย Aspose.Words สำหรับ .NET คุณยังจะได้เรียนรู้วิธี **เติมเทมเพลต Word ด้วยข้อมูล** เพื่อให้คุณสามารถสร้างเอกสารส่วนบุคคลโดยอัตโนมัติ

การทำงานอัตโนมัติของเอกสารเป็นความต้องการทั่วไปในงานออกใบแจ้งหนี้, การรับเข้าพนักงาน HR, และการทำรายงาน เมื่อจบบทเรียนนี้คุณจะมีแอปพลิเคชันคอนโซลที่ทำงานได้สมบูรณ์ ซึ่งโหลดเทมเพลต Word, แทนที่โทเค็น `{{Placeholder}}` ใด ๆ, และบันทึกผลลัพธ์เป็นไฟล์ใหม่

## ข้อกำหนดเบื้องต้น

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า ติดตั้งไว้แล้ว  
* Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ .NET)  
* ใบอนุญาต Aspose.Words สำหรับ .NET หรือสำเนาประเมินผลฟรี (API ทำงานได้โดยไม่มีใบอนุญาตแต่จะมีลายน้ำ)  
* เทมเพลต Word (`Template.docx`) ที่มีตัวแปรเช่น `{{FirstName}}` และ `{{LastName}}`

รายการเหล่านี้เพียงพอที่จะรันโค้ดได้ตามที่แสดง

## ขั้นตอนที่ 1: สร้างโปรเจกต์คอนโซลใหม่

เปิดเทอร์มินัลและรันคำสั่งต่อไปนี้เพื่อสร้างแอปคอนโซลขั้นพื้นฐาน:

```bash
dotnet new console -n DocxPlaceholderReplacer
cd DocxPlaceholderReplacer
```

เพิ่มแพคเกจ NuGet ของ Aspose.Words:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.LowCode
```

โปรเจกต์ตอนนี้อ้างอิงไลบรารีที่จำเป็นสำหรับการแทนที่ตัวแปรแล้ว

## ขั้นตอนที่ 2: โหลดเทมเพลต DOCX

สร้างไฟล์ชื่อ `Program.cs` (หรือแทนที่ไฟล์ที่มีอยู่) แล้วเพิ่มคำสั่ง `using`:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.LowCode;
```

ขั้นตอนเชิงตรรกะแรกคือการโหลดเอกสารเทมเพลต การดำเนินการนี้สร้างการแสดงผลในหน่วยความจำของไฟล์ Word ซึ่งคุณสามารถจัดการได้โดยโปรแกรม

```csharp
// Step 2: Load the DOCX template
string templatePath = @"YOUR_DIRECTORY/Template.docx";
Document template = new Document(templatePath);
Console.WriteLine($"Loaded template from '{templatePath}'.");
```

**ทำไมเรื่องนี้ถึงสำคัญ:** การโหลดไฟล์เพียงครั้งเดียวช่วยลดภาระ I/O และให้คุณเข้าถึงโครงสร้างโหนดของเอกสารทั้งหมด ซึ่งคลาส `Replacer` จะเดินทางผ่านเพื่อค้นหาตัวแปร

## ขั้นตอนที่ 3: ตั้งค่า Replacer

Aspose.Words.LowCode มียูทิลิตี้ `Replacer` ที่สแกนเอกสารอัตโนมัติสำหรับเครื่องหมาย `{{…}}` แล้วแทนที่ด้วยค่าที่ให้มา

```csharp
// Step 3: Create a Replacer instance for the loaded document
Replacer replacer = new Replacer(template);
Console.WriteLine("Replacer initialized.");
```

**เคล็ดลับ:** `Replacer` ทำงานกับรูปทรงใด ๆ ที่มีข้อความ (ย่อหน้า, ตาราง, ส่วนหัว, ส่วนท้าย ฯลฯ) คุณไม่จำเป็นต้องเดินทางโหนดด้วยตนเอง

## ขั้นตอนที่ 4: กำหนดค่าตัวแปร

เตรียมพจนานุกรมที่แต่ละคีย์ตรงกับโทเค็นตัวแปรในเทมเพลตอย่างแม่นยำ และค่าของแต่ละคีย์คือข้อความที่คุณต้องการใส่

```csharp
// Step 4: Define placeholder values to insert
var placeholderValues = new Dictionary<string, string>
{
    { "{{FirstName}}", "Alice" },
    { "{{LastName}}", "Smith" },
    // Add more entries as required, e.g.:
    // { "{{Date}}", DateTime.Today.ToShortDateString() }
};

Console.WriteLine("Placeholder values prepared:");
foreach (var kvp in placeholderValues)
{
    Console.WriteLine($"  {kvp.Key} => {kvp.Value}");
}
```

**ทำไมเรื่องนี้ถึงสำคัญ:** การใช้พจนานุกรมทำให้คุณขยายโซลูชันไปยังหลายสิบฟิลด์โดยไม่ต้องเปลี่ยนตรรกะการแทนที่

## ขั้นตอนที่ 5: ทำการแทนที่

เรียกเมธอด `Replace` พร้อมพาสพจนานุกรม เมธอดจะวนผ่านทุกโหนดข้อความ ตรวจจับรูปแบบ `{{…}}` แล้วสลับด้วยค่าที่สอดคล้อง

```csharp
// Step 5: Replace placeholders with actual data
replacer.Replace(placeholderValues);
Console.WriteLine("All placeholders have been replaced.");
```

**การจัดการกรณีขอบ:** หากตัวแปรในเอกสารไม่มีในพจนานุกรม `Replacer` จะปล่อยไว้โดยไม่แก้ไข พฤติกรรมนี้ป้องกันการสูญเสียข้อมูลโดยบังเอิญและทำให้โค้ดปลอดภัยสำหรับเทมเพลตที่เติมข้อมูลบางส่วน

## ขั้นตอนที่ 6: บันทึกเอกสารที่เติมข้อมูลแล้ว

สุดท้ายให้เขียนเอกสารที่แก้ไขแล้วลงไฟล์ใหม่ การเก็บเทมเพลตต้นฉบับไว้ไม่เปลี่ยนแปลงทำให้คุณสามารถใช้ซ้ำได้ในการรันครั้งต่อไป

```csharp
// Step 6: Save the filled document
string outputPath = @"YOUR_DIRECTORY/FilledTemplate.docx";
template.Save(outputPath);
Console.WriteLine($"Filled document saved to '{outputPath}'.");
```

เมื่อคุณเปิด `FilledTemplate.docx` คุณควรเห็น:

```
Alice Smith
```

แทนที่โทเค็นต้นฉบับ `{{FirstName}} {{LastName}}`

## โค้ดต้นฉบับเต็ม

ด้านล่างเป็นโปรแกรมที่สมบูรณ์และทำงานได้ด้วยตนเอง คัดลอกไปยัง `Program.cs` แทนที่ `YOUR_DIRECTORY` ด้วยเส้นทางโฟลเดอร์จริง แล้วรัน `dotnet run`

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.LowCode;

class Program
{
    static void Main()
    {
        // Load the template
        string templatePath = @"YOUR_DIRECTORY/Template.docx";
        Document template = new Document(templatePath);
        Console.WriteLine($"Loaded template from '{templatePath}'.");

        // Initialize the replacer
        Replacer replacer = new Replacer(template);
        Console.WriteLine("Replacer initialized.");

        // Prepare placeholder values
        var placeholderValues = new Dictionary<string, string>
        {
            { "{{FirstName}}", "Alice" },
            { "{{LastName}}", "Smith" }
        };

        Console.WriteLine("Placeholder values prepared:");
        foreach (var kvp in placeholderValues)
        {
            Console.WriteLine($"  {kvp.Key} => {kvp.Value}");
        }

        // Perform replacement
        replacer.Replace(placeholderValues);
        Console.WriteLine("All placeholders have been replaced.");

        // Save the result
        string outputPath = @"YOUR_DIRECTORY/FilledTemplate.docx";
        template.Save(outputPath);
        Console.WriteLine($"Filled document saved to '{outputPath}'.");
    }
}
```

### ผลลัพธ์ที่คาดหวังในคอนโซล

```
Loaded template from 'YOUR_DIRECTORY/Template.docx'.
Replacer initialized.
Placeholder values prepared:
  {{FirstName}} => Alice
  {{LastName}} => Smith
All placeholders have been replaced.
Filled document saved to 'YOUR_DIRECTORY/FilledTemplate.docx'.
```

### เนื้อหาที่คาดหวังใน `FilledTemplate.docx`

หากเทมเพลตต้นฉบับมีบรรทัด:

```
{{FirstName}} {{LastName}}
```

ไฟล์ที่บันทึกจะแสดง:

```
Alice Smith
```

## คำถามที่พบบ่อยและรูปแบบต่าง ๆ

**Can I replace placeholders inside tables?**  
ใช่ `Replacer` จะสแกนทุกโหนดที่มีข้อความ รวมถึงเซลล์, ส่วนหัว, และส่วนท้าย ไม่ต้องเขียนโค้ดเพิ่มเติม

**What if I need conditional logic (e.g., hide a paragraph when a value is empty)?**  
คุณสามารถลบโหนดก่อนเรียก `Replace`:

```csharp
if (string.IsNullOrEmpty(placeholderValues["{{OptionalField}}"]))
{
    // Find the paragraph that contains the placeholder and remove it
    Node paragraph = template.GetChildNodes(NodeType.Paragraph, true)
                             .FirstOrDefault(p => p.GetText().Contains("{{OptionalField}}"));
    paragraph?.Remove();
}
```

**Is the replacement case‑sensitive?**  
การจับคู่ค่าโดยปริยายเป็นแบบตรงตัวรวมถึงตัวพิมพ์ใหญ่‑เล็ก ตรวจสอบให้คีย์ในพจนานุกรมตรงกับโทเค็นในเทมเพลตอย่างแม่นยำ

**How do I work with large documents without excessive memory use?**  
Aspose.Words ประมวลผลเอกสารแบบสตรีมเมิงเมื่อบันทึก สำหรับไฟล์ขนาดใหญ่มาก ให้พิจารณาใช้คลาส `LoadOptions` กับ `LoadFormat.Docx` และคุณสมบัติ `LoadFormat` เพื่อปรับการใช้หน่วยความจำให้เหมาะสม

## สรุป

คุณได้เรียนรู้วิธี **แทนที่ตัวแปรในไฟล์ docx** และ **เติมเทมเพลต Word ด้วยข้อมูล** ด้วย Aspose.Words สำหรับ .NET บทเรียนได้ครอบคลุมการโหลดเทมเพลต, การตั้งค่า `Replacer`, การจัดหาพจนานุกรมของค่า, การทำการแทนที่, และการบันทึกผลลัพธ์ รูปแบบนี้สามารถขยายไปยังจำนวนตัวแปรใด ๆ และทำงานได้กับโครงสร้างเอกสาร Word ทั้งหมด

## ขั้นตอนต่อไป

* สำรวจตัวเลือกการจัดรูปแบบ เช่น การใช้สไตล์กับข้อความที่แทรกเข้าไป  
* ผสานวิธีนี้กับข้อมูลจากฐานข้อมูลเพื่อสร้างจดหมายส่วนบุคคลเป็นจำนวนมาก  
* ศึกษาเครื่องมือ low‑code อื่น ๆ เช่น `SmartTagProcessor` สำหรับสถานการณ์เทมเพลตขั้นสูง

อย่ากลัวที่จะทดลองเพิ่มตัวแปร, ส่วนเงื่อนไข, หรือการแทรกรูปภาพเพื่อขยายความสามารถของกระบวนการอัตโนมัติ Word ของคุณ ขอให้เขียนโค้ดอย่างสนุกสนาน!

## สิ่งที่คุณควรเรียนต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานครบถ้วนพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบต่าง ๆ ในโครงการของคุณ

- [แทรกรูปภาพในบรรทัดในเอกสาร Word ด้วย Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [แทรกวันที่ไดนามิกในส่วนหัวของเอกสาร Word ด้วย Aspose.Words สำหรับ .NET](/words/english/net/working-with-headers-and-footers/insert-header-date/)
- [สร้างเอกสาร Word เปล่าด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}