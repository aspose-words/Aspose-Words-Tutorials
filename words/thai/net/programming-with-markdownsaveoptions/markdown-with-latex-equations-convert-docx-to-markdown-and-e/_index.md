---
category: general
date: 2025-12-19
description: คู่มือการใช้ markdown กับสมการ latex – เรียนรู้วิธีแปลง docx เป็น markdown,
  ส่งออกสมการเป็น latex, และบันทึกรูปภาพลงโฟลเดอร์ด้วยชื่อที่ไม่ซ้ำกันโดยใช้ Aspose.Words
  ใน C#
draft: false
keywords:
- markdown with latex equations
- convert docx to markdown
- save images to folder
- export equations to latex
- generate unique image names
language: th
og_description: บทแนะนำการใช้ markdown พร้อมสมการ latex แสดงวิธีแปลง docx เป็น markdown,
  ส่งออกสมการเป็น latex, และสร้างชื่อไฟล์รูปภาพที่ไม่ซ้ำกันสำหรับรูปภาพที่บันทึกไว้
og_title: มาร์กดาวน์พร้อมสมการ LaTeX – คู่มือการแปลงเป็น C# อย่างเต็มรูปแบบ
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: 'มาร์กดาวน์พร้อมสมการ LaTeX: แปลง DOCX เป็นมาร์กดาวน์และส่งออกรูปภาพ'
url: /th/net/programming-with-markdownsaveoptions/markdown-with-latex-equations-convert-docx-to-markdown-and-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown พร้อมสมการ LaTeX: แปลง DOCX เป็น Markdown และส่งออกรูปภาพ

เคยต้องการ **markdown with latex equations** แต่ไม่แน่ใจว่าจะดึงออกจากไฟล์ Word อย่างไร? คุณไม่ได้เป็นคนเดียว—นักพัฒนาหลายคนเจออุปสรรคนี้เมื่อนำเอกสารจาก Office ไปยัง static site generators.  

ในบทแนะนำนี้ เราจะพาไปผ่านโซลูชันแบบครบวงจรที่ **converts docx to markdown**, **exports equations to latex**, และ **saves images to folder** พร้อมตรรกะ **generate unique image names**, ทั้งหมดใช้ Aspose.Words for .NET.  

เมื่อจบคุณจะได้โปรแกรม C# ที่พร้อมรันซึ่งสร้างไฟล์ Markdown ที่สะอาด, คณิตศาสตร์พร้อม LaTeX, และไดเรกทอรีรูปภาพที่เป็นระเบียบ—ไม่ต้องคัดลอก‑วางด้วยตนเอง.

## สิ่งที่คุณต้องการ

- .NET 6 (หรือ .NET runtime ล่าสุดใดก็ได้)  
- Aspose.Words for .NET 23.10 หรือใหม่กว่า (แพคเกจ NuGet `Aspose.Words`)  
- ตัวอย่าง `input.docx` ที่มีข้อความทั่วไป, วัตถุ Office Math, และรูปภาพไม่กี่รูป  
- IDE ที่คุณชอบ (Visual Studio, Rider, หรือ VS Code)  

เท่านี้แหละ. ไม่มีไลบรารีเพิ่มเติม, ไม่มีเครื่องมือ command‑line ที่ยุ่งยาก—แค่ C# ธรรมดา.

## ขั้นตอนที่ 1: โหลดเอกสารอย่างปลอดภัย (Recovery Mode)

เมื่อคุณทำงานกับไฟล์ที่อาจถูกแก้ไขโดยหลายคน ความเสียหายเป็นความเสี่ยงจริง Aspose.Words ให้คุณเปิด *RecoveryMode* เพื่อให้ตัวโหลดพยายามซ่อมส่วนที่เสียหายแทนที่จะโยนข้อยกเว้น.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // Load the document with recovery mode – this handles possible corruption.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
หากไฟล์ต้นทางมีโหนด XML แปลกปลอมหรือสตรีมรูปภาพที่เสีย, โหมด recovery จะยังคงให้ `Document` ที่ใช้งานได้ การข้ามขั้นตอนนี้อาจทำให้โปรแกรมหยุดทำงานอย่างรุนแรง, โดยเฉพาะใน pipeline CI ที่คุณไม่ได้ควบคุมการอัปโหลดทุกครั้ง

> **เคล็ดลับ:** เมื่อประมวลผลเป็นชุด, ให้ห่อการโหลดด้วย `try/catch` และบันทึก `DocumentCorruptedException` ใด ๆ เพื่อการตรวจสอบภายหลัง.

## ขั้นตอนที่ 2: แปลง DOCX เป็น Markdown พร้อมสมการ LaTeX

ตอนนี้มาถึงหัวใจของบทแนะนำ: เราต้องการ **markdown with latex equations**. `MarkdownSaveOptions` ของ Aspose.Words ให้คุณกำหนด `OfficeMathExportMode.LaTeX`, ซึ่งจะแปลงวัตถุ Office Math แต่ละอันเป็นสตริง LaTeX ที่ล้อมด้วย `$…$` หรือ `$$…$$`.

```csharp
        // Export Office Math equations to LaTeX while saving as Markdown.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);
```

ไฟล์ `output_math.md` ที่ได้จะมีลักษณะประมาณนี้:

```markdown
Here is an inline equation $E = mc^2$ inside a sentence.

And a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

**ทำไมคุณถึงต้องการแบบนี้:**  
Static site generator ส่วนใหญ่ (Hugo, Jekyll, MkDocs) เข้าใจตัวแบ่ง LaTeX อยู่แล้วเมื่อคุณเปิดปลั๊กอิน MathJax หรือ KaTeX การส่งออกโดยตรงเป็น LaTeX จะช่วยหลีกเลี่ยงขั้นตอนหลังการประมวลผลที่ต้องใช้ regex hack

### กรณีขอบ

- **สมการซับซ้อน:** โครงสร้างที่ซ้อนลึกมากยังคงแสดงผลได้ถูกต้อง, แต่คุณอาจต้องเพิ่มขีดจำกัดหน่วยความจำของ `MathRenderer` หากเจอ `OutOfMemoryException`.  
- **เนื้อหาผสม:** หากย่อหน้าผสมข้อความทั่วไปและสมการ, Aspose.Words จะทำการแยกโดยอัตโนมัติ, รักษา markdown รอบ ๆ ไว้

## ขั้นตอนที่ 3: บันทึกรูปภาพลงโฟลเดอร์พร้อมชื่อที่ไม่ซ้ำกัน

หากเอกสาร Word ของคุณมีรูปภาพ, คุณอาจต้องการให้เป็นไฟล์รูปภาพแยกที่ markdown สามารถอ้างอิงได้ `ResourceSavingCallback` บน `MarkdownSaveOptions` ให้คุณควบคุมการเขียนรูปภาพแต่ละไฟล์อย่างเต็มที่

```csharp
        // Customize image handling during Markdown export.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                // Generate a unique file name for each image.
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);

                // Ensure the Images folder exists.
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);

                // Save the image to the file system.
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);
```

**รูปแบบ markdown ตอนนี้เป็นแบบนี้:**  

```markdown
![Image description](Images/img_3f9c2a1e-7b5d-4c8f-9d6e-2b5c7a9e1f0a.png)
```

**ทำไมต้องสร้างชื่อที่ไม่ซ้ำกัน?**  
หากรูปเดียวกันปรากฏหลายครั้ง, การใช้ชื่อเดิมจะทำให้ไฟล์ถูกเขียนทับ. ชื่อที่สร้างจาก GUID จะรับประกันว่าไฟล์แต่ละไฟล์เป็นเอกลักษณ์, ซึ่งมีประโยชน์มากเมื่อคุณทำการแปลงในงานแบบขนาน

### เคล็ดลับและข้อควรระวัง

- **ประสิทธิภาพ:** การสร้าง GUID สำหรับรูปภาพแต่ละรูปเพิ่มภาระที่น้อยมาก, แต่หากคุณประมวลผลรูปภาพหลายพันรูป คุณสามารถเปลี่ยนเป็นแฮชที่กำหนดได้ (เช่น SHA‑256 ของไบต์รูปภาพ).  
- **รูปแบบไฟล์:** `resource.Save` จะบันทึกรูปภาพในรูปแบบเดิมของมัน. หากคุณต้องการ PNG ทั้งหมด, ให้แทนที่ `resource.Save(imageFile);` ด้วย `resource.Save(imageFile, ImageSaveOptions.CreateSaveOptions(SaveFormat.Png));`.

## ขั้นตอนที่ 4: ส่งออก PDF พร้อม Inline Shapes (ตัวเลือก)

บางครั้งคุณอาจยังต้องการเวอร์ชัน PDF ของเอกสารเดียวกัน, บางครั้งเพื่อการตรวจสอบทางกฎหมาย. การตั้งค่า `ExportFloatingShapesAsInlineTag` จะทำให้วัตถุลอย (เช่น กล่องข้อความ) อยู่ใน PDF เป็นแท็กอินไลน์, รักษาความแม่นยำของการจัดวาง

```csharp
        // Save the document as PDF, exporting floating shapes as inline tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

คุณสามารถข้ามขั้นตอนนี้ได้หากการส่งออก PDF ไม่ใช่ส่วนหนึ่งของ workflow ของคุณ—ไม่มีอะไรเสียหายหากละเว้นขั้นตอนนี้.

## ตัวอย่างการทำงานเต็มรูปแบบ (รวมทุกขั้นตอน)

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปคอนโซล. อย่าลืมแทนที่ `YOUR_DIRECTORY` ด้วยพาธจริงที่เป็นแบบ absolute หรือ relative

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // 1️⃣ Load with recovery mode.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Export markdown with LaTeX equations.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);

        // 3️⃣ Save images to a folder, using unique GUID names.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);

        // 4️⃣ (Optional) Export PDF with inline shape tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

การรันโปรแกรมนี้จะสร้างไฟล์สามไฟล์:

| File | วัตถุประสงค์ |
|------|----------------|
| `output_math.md` | Markdown ที่มีสมการพร้อม LaTeX |
| `output_images.md` | Markdown ที่มีลิงก์รูปภาพชี้ไปยัง PNG ที่มีชื่อไม่ซ้ำกัน |
| `output_shapes.pdf` | เวอร์ชัน PDF ที่รักษา floating shapes เป็นแท็กอินไลน์ (ตัวเลือก) |

## สรุป

ตอนนี้คุณมี pipeline **markdown with latex equations** ที่ **convert docx to markdown**, **export equations to latex และ **save images to folder** พร้อม **generate unique image names** สำหรับแต่ละรูปภาพ วิธีการนี้เป็นอิสระเต็มรูปแบบ, ทำงานกับโปรเจกต์ .NET สมัยใหม่ใดก็ได้, และต้องการเพียงแพคเกจ NuGet ของ Aspose.Words เท่านั้น

ต่อไปคุณจะทำอะไร? ลองนำ markdown ที่สร้างขึ้นไปใส่ใน static‑site generator อย่าง Hugo, เปิดใช้งาน MathJax, แล้วดูเอกสารของคุณเปลี่ยนจากรูปแบบ Office ปิดเป็นเว็บไซต์ที่สวยงามและพร้อมใช้งานบนเว็บ. ต้องการตาราง? Aspose.Words ยังรองรับ `MarkdownSaveOptions.ExportTableAsHtml` อีกด้วย, ทำให้คุณสามารถรักษาเลย์เอาต์ที่ซับซ้อนได้

If

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}