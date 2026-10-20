---
category: general
date: 2026-04-28
description: เรียนรู้วิธีตั้งเส้นทางภาพแบบสัมพัทธ์ใน Markdown เมื่อคุณแปลง Word เป็น
  Markdown, ดึงภาพจาก Word และสร้างโฟลเดอร์ resources สำหรับภาพที่ส่งออก
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: th
og_description: กำหนดเส้นทางภาพแบบสัมพันธ์ใน Markdown ขณะแปลงไฟล์ Word เป็น Markdown,
  ดึงภาพจาก Word, และสร้างโฟลเดอร์ resources สำหรับภาพที่ส่งออก
og_title: เส้นทางสัมพัทธ์ของรูปภาพ markdown – แปลง Word เป็น Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: เส้นทางสัมพัทธ์ของรูปภาพใน Markdown – แปลง Word เป็น Markdown
url: /th/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown image relative path – แปลง Word เป็น Markdown

เคยต้องการ **markdown image relative path** ขณะ **convert Word to markdown** หรือไม่? คุณไม่ได้เป็นคนเดียว นักพัฒนาส่วนใหญ่เจอปัญหาเมื่อ Markdown ที่สร้างขึ้นชี้ไปที่ภาพในโฟลเดอร์แบน ทำให้โครงสร้างลิงก์สัมพัทธ์ที่คุณคาดหวังในเว็บไซต์สถิตหรือรีโป GitHub แตกหัก

ในบทแนะนำนี้เราจะพาคุณผ่านโซลูชันครบวงจรแบบ end‑to‑end ที่ **extracts images from Word**, **creates a resources folder**, และเขียนทับการอ้างอิงภาพเพื่อให้ใช้ *markdown image relative path* ที่สะอาดตา เมื่อเสร็จคุณจะได้ไฟล์ `.md` พร้อมเผยแพร่และไดเรกทอรี `Resources` ที่จัดระเบียบอย่างเป็นระเบียบซึ่งบรรจุภาพทั้งหมดที่ดึงจากไฟล์ `.docx` ดั้งเดิม

> **What you’ll get:** โปรแกรม C# เดียว (ไม่มีสคริปต์ภายนอก) คำอธิบายที่ชัดเจนเกี่ยวกับ *why* แต่ละส่วนสำคัญ, และเคล็ดลับเชิงปฏิบัติที่คุณสามารถคัดลอก‑วางไปใช้ในโปรเจกต์ของคุณเอง.

---

## ข้อกำหนดเบื้องต้น

- **.NET 6.0** หรือใหม่กว่า (คุณสามารถกำหนดเป้าหมายเป็น .NET Framework 4.7+ ได้เช่นกัน, แต่ .NET 6 เป็นจุดที่เหมาะสมสำหรับโปรเจกต์ใหม่).
- **Aspose.Words for .NET** (แพคเกจ NuGet ล่าสุด ณ เวลาที่เขียน, เวอร์ชัน 23.12). ติดตั้งด้วย:
  ```bash
  dotnet add package Aspose.Words
  ```
- เอกสาร Word ที่มีภาพจริง ๆ — สมมติว่าไฟล์ชื่อ `WithImages.docx`.
- โฟลเดอร์ที่คุณต้องการให้ markdown ผลลัพธ์และภาพอยู่, เช่น `C:\Projects\MarkdownExport`.

ไม่ต้องการไลบรารีเพิ่มเติม; ส่วนอื่นทั้งหมดจัดการโดย Aspose.Words.

## ขั้นตอนที่ 1: โหลดเอกสาร Word ต้นฉบับ (จุดเริ่มต้นสำหรับ convert word to markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Why this matters:* การโหลดเอกสารทำให้เราสามารถเข้าถึงโครงสร้าง node ภายใน, ซึ่งรวมถึงส่วนของภาพที่เราต้อง **export images from docx** ในภายหลัง หากการโหลดล้มเหลว ขั้นตอนต่อ ๆ ไปจะไม่ทำงาน ดังนั้นตรวจสอบเส้นทางและสิทธิ์ไฟล์อีกครั้ง.

## ขั้นตอนที่ 2: กำหนดค่า `MarkdownSaveOptions` ด้วย callback แบบกำหนดเอง (หัวใจของ create resources folder)

`ResourceSavingCallback` ช่วยให้เราสามารถแทรกแซงทุกครั้งที่ Aspose.Words ต้องการเขียนไฟล์ภาพ ภายใน callback เราจะ **create a Resources sub‑folder** และปรับการอ้างอิงเพื่อให้ markdown ที่สร้างใช้ *markdown image relative path*.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

สังเกตว่าเราได้ส่ง `resourcesFolder` เข้าไปในคอนสตรัคเตอร์ของ callback—ทำให้เส้นทางโฟลเดอร์ยืดหยุ่นและหลีกเลี่ยงการ hard‑coding สตริงทั่วทั้งโค้ด.

## ขั้นตอนที่ 3: Implement the callback that **creates resources folder** and rewrites the path

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Why this works:* `args.Stream` มีไบต์ของภาพดิบ. โดยคัดลอกไปยังไฟล์ในโฟลเดอร์ `Resources` ของเรา เรา **export images from docx** อย่างปลอดภัย จากนั้นเราจะแทนที่ `args.ResourceFileName` ด้วย URL สัมพัทธ์ (`Resources/image.png`). เมื่อ Aspose.Words เขียน markdown ต่อไป มันจะใส่สตริงนั้นลงไป ทำให้เราได้ *markdown image relative path* ที่ต้องการ.

## ขั้นตอนที่ 4: ตรวจสอบ Markdown ที่สร้างขึ้น (รูปแบบผลลัพธ์สุดท้าย)

เปิด `Doc.md` ด้วยโปรแกรมแก้ไขข้อความใดก็ได้ คุณควรเห็นสิ่งที่คล้ายกับ:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

ส่วนสำคัญคือการอ้างอิงภาพแต่ละรายการชี้ไปที่ `Resources/...` – นั่นคือ **markdown image relative path** ที่เราต้องการ.

![ตัวอย่าง markdown image relative path](example.png "ตัวอย่าง markdown image relative path")

*Tip:* หากคุณเปิด markdown ด้วยตัวดูที่เคารพลิงก์สัมพัทธ์ (preview ของ VS Code, GitHub, หรือ static site generator), ภาพจะถูกแสดงอย่างถูกต้องโดยไม่ต้องตั้งค่าเพิ่มเติม.

## ขั้นตอนที่ 5: ข้อผิดพลาดทั่วไปและ pro‑tips

| ปัญหา | สาเหตุ | วิธีแก้ไข |
|-------|--------|-----------|
| ภาพถูกเก็บไว้ในโฟลเดอร์รากแทน `Resources` | Callback ไม่ได้ถูกแนบหรือ `args.ResourceFileName` ไม่ได้ถูกเขียนทับ | ตรวจสอบให้แน่ใจว่าได้ตั้งค่า `ResourceSavingCallback` **ก่อน** เรียก `doc.Save` |
| ชื่อไฟล์มีอักขระที่ไม่ถูกต้อง | Word บางครั้งตั้งชื่อภาพด้วยช่องว่างหรือสัญลักษณ์ Unicode | ใช้ `Path.GetInvalidFileNameChars()` เพื่อลบอักขระที่ไม่ถูกต้องจาก `args.ResourceFileName` ภายใน callback |
| เอกสารขนาดใหญ่ใช้เวลาประมวลผลนาน | แต่ละภาพถูกเขียนแบบ synchronous | เปลี่ยนเป็น I/O แบบ asynchronous (`await args.Stream.CopyToAsync(fileStream)`) หากคุณใช้ .NET 6+ และต้องการประสิทธิภาพ |
| เส้นทางสัมพัทธ์เสียหายเมื่อย้าย markdown | เส้นทางเป็นสัมพัทธ์ต่อที่ตั้งไฟล์ markdown | เก็บ `Doc.md` และโฟลเดอร์ `Resources` ไว้ด้วยกัน, หรือปรับ callback ให้ใช้ prefix สัมพัทธ์อื่น (เช่น `../assets`) |

## ขั้นตอนที่ 6: ขยายโซลูชัน (ถ้าต้องการการควบคุมเพิ่มเติม?)

- **Multiple output formats:** แทนที่ `MarkdownSaveOptions` ด้วย `HtmlSaveOptions` หรือ `PdfSaveOptions` ขณะยังคงใช้ callback เดียว—Aspose.Words จะเรียกใช้มันสำหรับทุกภาพโดยไม่คำนึงถึงรูปแบบ.
- **Custom image naming:** หากต้องการเปลี่ยนชื่อภาพ (เช่น `figure-01.png`), แก้ไข `args.ResourceFileName` ภายใน callback ก่อนเขียนไฟล์.
- **Embedding images as Base64:** ตั้งค่า `args.ResourceFileName` เป็น data URI (`data:image/png;base64,...`) และข้ามการเขียนไฟล์. วิธีนี้สะดวกสำหรับการส่งออก markdown เป็นไฟล์เดียว.

## สรุป

คุณมีโปรแกรม C# ที่ทำงานเต็มรูปแบบที่ **converts Word to markdown**, **extracts images from word**, **creates a resources folder**, และรับประกัน **markdown image relative path** ที่สะอาดสำหรับทุกภาพ โค้ดเป็นอิสระ, ทำงานกับเวอร์ชันล่าสุดของ Aspose.Words, และสามารถนำไปใส่ในโปรเจกต์ .NET ใดก็ได้ด้วยความพยายามน้อย.

ขั้นตอนต่อไป? ลองนำ markdown ที่สร้างไปใช้กับ static site generator เช่น Hugo หรือ Jekyll, หรือทดลองปรับ callback เพื่อฝังภาพโดยตรงเป็นสตริง Base64. หากเจอกรณีขอบเช่น ภาพ SVG หรือไฟล์ขนาดใหญ่มาก ให้กลับไปดูตาราง “ข้อผิดพลาดทั่วไป”; การปรับเล็กน้อยมักแก้ปัญหาได้.

ขอให้เขียนโค้ดอย่างสนุกสนาน, และขอให้ markdown ของคุณชี้ไปยังโฟลเดอร์ที่ถูกต้องเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}