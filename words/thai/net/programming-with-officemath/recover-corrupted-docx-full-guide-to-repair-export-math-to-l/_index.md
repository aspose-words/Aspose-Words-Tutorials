---
category: general
date: 2025-12-23
description: เรียนรู้วิธีกู้ไฟล์ docx ที่เสียหาย, ใช้โหมดการกู้คืน, ส่งออกสมการเป็น LaTeX,
  และสร้างชื่อรูปภาพที่ไม่ซ้ำกันใน C# โค้ดทีละขั้นตอนพร้อมคำอธิบาย.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: th
og_description: กู้ไฟล์ docx ที่เสียหาย, ใช้โหมดการกู้คืน, ส่งออกสมการเป็น LaTeX,
  และสร้างชื่อรูปภาพที่ไม่ซ้ำกันด้วย Aspose.Words ใน C#
og_title: กู้ไฟล์ docx ที่เสียหาย – คอร์สสอน C# ฉบับเต็ม
tags:
- Aspose.Words
- C#
- Document Recovery
title: กู้ไฟล์ docx ที่เสีย – คู่มือเต็มสำหรับการซ่อมแซม, ส่งออกคณิตศาสตร์เป็น LaTeX
  และสร้างชื่อรูปภาพที่ไม่ซ้ำกัน
url: /th/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# กู้ไฟล์ docx ที่เสีย – คู่มือเต็มสำหรับการซ่อม, ส่งออก Math เป็น LaTeX และสร้างชื่อรูปภาพที่ไม่ซ้ำกัน

เคยเปิดไฟล์ **.docx** ที่ไม่สามารถโหลดได้เพราะไฟล์เสียหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายโครงการจริง ๆ ไฟล์ Word ที่เสียอาจทำให้กระบวนการทำงานทั้งหมดหยุดชะงัก แต่ข่าวดีคือคุณสามารถ **recover corrupted docx** ไฟล์ได้โดยโปรแกรม  

ในบทแนะนำนี้เราจะพาคุณผ่านขั้นตอนที่แน่นอนเพื่อ **recover corrupted docx**, แสดง **how to use recovery mode**, สาธิต **export equations to LaTeX**, และสุดท้าย **generate unique image names** เมื่อบันทึกเป็น Markdown. เมื่อเสร็จสิ้นคุณจะมีโปรแกรม C# เดียวที่ทำงานได้ครบทุกอย่างโดยไม่มีปัญหา

## ข้อกำหนดเบื้องต้น

- .NET 6 หรือใหม่กว่า (โค้ดนี้ยังทำงานได้กับ .NET Framework 4.6+)。  
- Aspose.Words for .NET (รุ่นทดลองหรือแบบมีลิขสิทธิ์). ติดตั้งผ่าน NuGet:

```bash
dotnet add package Aspose.Words
```

- ความคุ้นเคยพื้นฐานกับ C# และการทำ I/O ของไฟล์。  
- ไฟล์ `corrupt.docx` ที่เสียเพื่อทดสอบ (คุณสามารถจำลองการเสียได้โดยการตัดส่วนของไฟล์ที่ถูกต้อง)

> **Pro tip:** เก็บสำเนาสำรองของไฟล์ต้นฉบับก่อนเริ่ม—การกู้คืนจะทำลายไฟล์เฉพาะเมื่อคุณเขียนทับแหล่งที่มานั้น

## ขั้นตอนที่ 1 – กู้ไฟล์ DOCX ที่เสียโดยใช้ Recovery Mode

สิ่งแรกที่เราต้องทำคือบอก Aspose.Words ให้ถือว่าไฟล์ที่เข้ามาอาจเสียได้ นี่คือจุดที่ **how to use recovery mode** เข้ามามีบทบาท

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**Why this matters:**  
เมื่อเปิดใช้งาน `RecoveryMode.Recover` Aspose.Words จะพยายามสร้างต้นไม้เอกสารภายในใหม่โดยข้ามส่วนที่อ่านไม่ออกในขณะที่พยายามเก็บเนื้อหาให้มากที่สุด หากไม่เปิดใช้งาน ตัวสร้าง `Document` จะโยนข้อยกเว้นและคุณจะสูญเสียโอกาสในการกู้ไฟล์

> **What if the file is beyond repair?**  
> ไลบรารีจะยังคงคืนค่าออบเจ็กต์ `Document` แต่บางโหนดอาจหายไป คุณสามารถตรวจสอบ `doc.GetChildNodes(NodeType.Any, true).Count` เพื่อดูว่ามีองค์ประกอบเหลืออยู่กี่รายการ

## ขั้นตอนที่ 2 – ส่งออกสมการ Office Math เป็น LaTeX เมื่อบันทึกเป็น Markdown

เอกสารเทคนิคหลายฉบับมีสมการที่เขียนด้วย Office Math หากคุณต้องการสมการเหล่านั้นในรูปแบบ LaTeX—เช่นเพื่อเผยแพร่บนบล็อกวิชาการ—คุณสามารถให้ Aspose.Words ทำการแปลงให้คุณได้

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**How it works:**  
`OfficeMathExportMode.LaTeX` บอกตัวบันทึกให้แทนที่แต่ละโหนด `OfficeMath` ด้วยการแสดงผล LaTeX ที่ห่อด้วย `$…$` (แบบอินไลน์) หรือ `$$…$$` (แบบแสดงผล) ไฟล์ Markdown ที่ได้สามารถส่งต่อโดยตรงให้กับ static‑site generators อย่าง Hugo หรือ Jekyll

> **Edge case:** หากเอกสารต้นฉบับมีวัตถุสมการที่ซับซ้อน (เช่นเมทริกซ์) การแปลงเป็น LaTeX อาจสร้างผลลัพธ์หลายบรรทัด ตรวจสอบไฟล์ `.md` ที่สร้างขึ้นเพื่อให้แน่ใจว่าตรงกับรูปแบบที่คุณต้องการ

## ขั้นตอนที่ 3 – บันทึกเอกสารเป็น PDF พร้อมควบคุมแท็กของรูปแบบลอย

บางครั้งคุณต้องการเวอร์ชัน PDF ของเอกสารเดียวกัน แต่คุณก็สนใจว่ารูปแบบลอย (รูปภาพ, กล่องข้อความ) จะถูกแท็กอย่างไรเพื่อการเข้าถึง `ExportFloatingShapesAsInlineTag` ให้คุณควบคุมได้

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**Why toggle this flag?**  
- `true` → รูปแบบลอยจะกลายเป็นแท็ก `<Figure>` ซึ่งโปรแกรมอ่านหน้าจอหลายตัวจะถือว่าเป็นภาพแยกพร้อมคำอธิบาย  
- `false` → รูปแบบจะถูกห่อด้วยแท็ก `<Div>` ทั่วไป ซึ่งอาจถูกเทคโนโลยีช่วยเหลือมองข้าม เลือกตามความต้องการด้านการเข้าถึงของคุณ

## ขั้นตอนที่ 4 – ส่งออกเป็น Markdown พร้อมการจัดการรูปภาพแบบกำหนดเอง (generate unique image names)

เมื่อคุณบันทึกเอกสาร Word เป็น Markdown รูปภาพที่ฝังอยู่ทั้งหมดจะถูกเขียนลงดิสก์ โดยค่าเริ่มต้นจะใช้ชื่อไฟล์เดิม ซึ่งอาจทำให้เกิดการชนกันหากคุณประมวลผลหลายเอกสารในโฟลเดอร์เดียว เราจะดักจับกระบวนการบันทึกและ **generate unique image names** โดยอัตโนมัติ

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**What’s happening under the hood?**  
`ResourceSavingCallback` จะถูกเรียกสำหรับทุกทรัพยากรภายนอก (รูปภาพ, SVG ฯลฯ) ระหว่างการบันทึก โดยการคืนค่าพาธเต็มคุณกำหนดได้ว่ารูปไฟล์จะถูกบันทึกไว้ที่ไหนและชื่ออะไร GUID จะทำให้ **generate unique image names** โดยไม่ต้องจัดการด้วยตนเอง

> **Tip:** หากคุณต้องการรูปแบบการตั้งชื่อที่กำหนดได้ (เช่นอิงจากข้อความ alt ของรูป) ให้แทนที่ `Guid.NewGuid()` ด้วยแฮชของ `resourceInfo.Name`

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปคอนโซลได้

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

การรันโปรแกรมควรแสดงข้อความคอนโซลคล้ายกับนี้

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

คุณจะพบไฟล์สามไฟล์:

| ไฟล์ | จุดประสงค์ |
|------|-------------|
| `out.md` | Markdown ที่ทุกสมการ Office Math ปรากฏเป็น LaTeX (`$…$` หรือ `$$…$$`) |
| `out.pdf` | เวอร์ชัน PDF ที่รูปแบบลอยถูกแท็ก `<Figure>` เพื่อการเข้าถึงที่ดียิ่งขึ้น |
| `out2.md` + `md_images\*` | Markdown พร้อมโฟลเดอร์ของไฟล์รูปภาพที่ตั้งชื่อแบบไม่ซ้ำ (อิง GUID) |

## คำถามที่พบบ่อย & กรณีขอบเขต

| คำถาม | คำตอบ |
|----------|--------|
| **What if the corrupted file has no recoverable content?** | Aspose.Words จะยังคงคืนค่าออบเจ็กต์ `Document` แต่อาจว่างเปล่า ตรวจสอบ `doc.GetChildNodes(NodeType.Paragraph, true).Count` ก่อนดำเนินการต่อ |
| **Can I change the LaTeX delimiter?** | ได้—ตั้งค่า `markdownMathOptions.MathDelimiter = "$$"` เพื่อบังคับใช้ตัวแบ่งแบบแสดงผล |
| **Do I need to dispose of the `Document` object?** | คลาส `Document` implements `IDisposable` ใช้บล็อก `using` หากคุณประมวลผลหลายไฟล์เพื่อปล่อยทรัพยากรเนทีฟโดยเร็ว |
| **How do I keep the original image filenames?** | คืนค่า `Path.Combine(imageFolder, resourceInfo.Name)` ภายใน callback เพียงจำความเสี่ยงของการชนชื่อไฟล์ |
| **Is the GUID approach safe for version‑controlled repos?** | GUID มีความคงที่ระหว่างการรันแต่ไม่อ่านง่าย หากต้องการชื่อที่ทำซ้ำได้ ให้แฮชชื่อเดิมบวกกับ salt ระดับโปรเจค |

## สรุป

เราได้แสดงให้คุณเห็นวิธี **recover corrupted docx** ไฟล์, สาธิต **how to use 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}