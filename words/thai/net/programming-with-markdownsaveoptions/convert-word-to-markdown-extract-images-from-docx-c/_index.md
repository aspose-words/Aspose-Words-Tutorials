---
category: general
date: 2026-03-17
description: แปลง Word เป็น Markdown ด้วย C# พร้อมการดึงรูปภาพจาก DOCX เรียนรู้วิธีดึงรูปภาพ
  ตั้งค่า callbacks และบันทึก markdown พร้อมโฟลเดอร์ assets.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- how to convert docx
language: th
og_description: แปลง Word เป็น Markdown ด้วย C# และเรียนรู้วิธีดึงรูปภาพจาก DOCX โค้ดทีละขั้นตอน
  คำอธิบาย และเคล็ดลับเพื่อการแปลงที่ราบรื่น
og_title: แปลง Word เป็น Markdown และดึงรูปภาพจาก DOCX (C#) – คู่มือเต็ม
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: แปลง Word เป็น Markdown และดึงรูปภาพจาก DOCX (C#)
url: /th/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-from-docx-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แปลง Word เป็น Markdown และแยกรูปภาพจาก DOCX (C#)

เคยต้องการ **แปลง Word เป็น Markdown** แต่เจอปัญหารูปภาพที่หายไปอย่างลึกลับหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายโครงการจริง—เช่น static site generators, documentation pipelines, หรือ headless CMS—คุณต้องการข้อความ markdown **และ** รูปภาพต้นฉบับที่จัดเก็บอย่างเป็นระเบียบในโฟลเดอร์ *assets*.

ในบทแนะนำนี้คุณจะได้เห็น **วิธีแปลง docx** เป็น markdown **พร้อมกับการแยกรูปภาพ** โดยใช้ Aspose.Words for .NET เราจะอธิบายการตั้งค่า resource‑saving callback, การจัดการกรณีพิเศษเช่นชื่อไฟล์ซ้ำ, และสร้างโครงสร้างโฟลเดอร์ที่สะอาดพร้อมสำหรับ static site builder ของคุณ.

## สิ่งที่คุณจะได้เรียนรู้

- โหลดไฟล์ `.docx` และเตรียมพร้อมสำหรับการแปลง  
- ทำการ Implement `IResourceSavingCallback` เพื่อ **แยกรูปภาพจาก DOCX**  
- กำหนดค่า `MarkdownSaveOptions` เพื่อให้ markdown อ้างอิง assets อย่างถูกต้อง  
- รันโค้ดและตรวจสอบว่าไฟล์ `.md` และโฟลเดอร์รูปภาพถูกสร้างตามที่คาดหวัง  

**Prerequisites** – คุณต้องมี .NET 6+ (หรือ .NET Framework 4.7.2+) และไลเซนส์ Aspose.Words (เวอร์ชันทดลองฟรีใช้ได้สำหรับการสาธิตนี้) ความเข้าใจพื้นฐานของ C# และการทำงานกับไฟล์ I/O จะช่วยให้ขั้นตอนราบรื่นขึ้น แต่คู่มือเต็มรูปแบบและไม่ต้องพึ่งแหล่งอื่น

![Convert Word to Markdown folder layout](https://example.com/convert-word-to-markdown.png "Convert Word to Markdown folder layout")

*โครงสร้างโฟลเดอร์หลังการแปลง – ไฟล์ markdown อยู่ข้างๆ โฟลเดอร์ `assets` ที่เก็บรูปภาพที่แยกออกทั้งหมด*

---

## ขั้นตอนที่ 1: โหลดเอกสารต้นฉบับ (แปลง word เป็น markdown)

สิ่งแรกที่เราทำคืออ่านไฟล์ `.docx` ที่คุณต้องการแปลงเป็น markdown Aspose.Words แยกความซับซ้อนของรูปแบบ OPC ระดับต่ำออกไป ดังนั้นบรรทัดเดียวก็ทำงานได้

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// Adjust these paths to match your environment.
string inputPath  = Path.Combine("YOUR_DIRECTORY", "input.docx");
string outputDir  = Path.Combine("YOUR_DIRECTORY", "output");

// Ensure the output folder exists.
Directory.CreateDirectory(outputDir);

// Load the DOCX file.
Document document = new Document(inputPath);
```

*ทำไมเรื่องนี้สำคัญ:* การโหลดเอกสารตั้งแต่ต้นทำให้เราได้อ็อบเจ็กต์ `Document` ที่เก็บทั้งเนื้อหาข้อความ **และ** ทรัพยากรที่ฝังอยู่ (รูปภาพ, แผนภูมิ ฯลฯ) หากข้ามขั้นตอนนี้คุณจะไม่สามารถ **แยกรูปภาพ** ในภายหลังได้

## ขั้นตอนที่ 2: สร้าง Callback เพื่อ **แยกรูปภาพ** จาก DOCX

Aspose.Words จะเรียก `IResourceSavingCallback` ของคุณทุกครั้งที่ต้องเขียนทรัพยากร (เช่นรูปภาพ) โดยการให้การทำงานของเราเอง เราตัดสินใจว่าไฟล์จะถูกบันทึก **ที่ไหน** และ markdown จะอ้างอิงไฟล์นั้น **อย่างไร**

```csharp
/// <summary>
/// Saves each extracted resource (image, video, etc.) into an "assets" sub‑folder
/// and rewrites the markdown reference to point at that relative path.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _outputDirectory;

    public MyMarkdownResourceCallback(string outputDirectory)
    {
        _outputDirectory = outputDirectory;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the assets folder path.
        string assetsFolder = Path.Combine(_outputDirectory, "assets");
        Directory.CreateDirectory(assetsFolder);

        // 2️⃣ Resolve potential filename collisions.
        string safeFileName = GetUniqueFileName(assetsFolder, args.ResourceFileName);

        // 3️⃣ Write the resource stream to disk.
        string assetPath = Path.Combine(assetsFolder, safeFileName);
        using (FileStream fs = new FileStream(assetPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // 4️⃣ Tell the markdown writer the *relative* path it should embed.
        args.ResourceFileName = Path.Combine("assets", safeFileName);
        args.KeepResourceStreamOpen = false; // we already closed it
    }

    // Helper: ensure we don't overwrite an existing file.
    private string GetUniqueFileName(string folder, string originalName)
    {
        string filePath = Path.Combine(folder, originalName);
        if (!File.Exists(filePath))
            return originalName;

        string nameWithoutExt = Path.GetFileNameWithoutExtension(originalName);
        string ext = Path.GetExtension(originalName);
        int counter = 1;

        while (File.Exists(filePath))
        {
            string candidate = $"{nameWithoutExt}_{counter}{ext}";
            filePath = Path.Combine(folder, candidate);
            counter++;
        }

        return Path.GetFileName(filePath);
    }
}
```

**Key points**  

- **ทำไมต้องใช้โฟลเดอร์ assets ย่อย?** การแยกรูปภาพออกจากไฟล์ `.md` ทำให้โครงสร้างตรงกับที่ static site generators ส่วนใหญ่คาดหวัง  
- **การจัดการการชนกัน** ป้องกันข้อยกเว้น “ไฟล์มีอยู่แล้ว” ที่น่ากลัวเมื่อรูปภาพเดียวกันปรากฏหลายครั้ง  
- การตั้งค่า `args.KeepResourceStreamOpen = false` แจ้งให้ Aspose ทราบว่าเราได้จัดการสตรีมแล้ว เพื่อหลีกเลี่ยงการรั่วไหลของหน่วยความจำ  

## ขั้นตอนที่ 3: เชื่อม Callback เข้ากับ **MarkdownSaveOptions**

ตอนนี้เราบอก Aspose.Words ให้ใช้ callback ของเราเมื่อใดก็ตามที่เขียนทรัพยากร นี่คือหัวใจของ **วิธีแปลง docx** พร้อมกับการรักษาสื่อเดิมไว้

```csharp
// Instantiate the callback with the output directory.
var resourceCallback = new MyMarkdownResourceCallback(outputDir);

// Configure markdown options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // The callback does the heavy lifting for image extraction.
    ResourceSavingCallback = resourceCallback,

    // Optional: make the markdown more GitHub‑friendly.
    ExportImagesAsBase64 = false, // we want separate files, not embedded data URIs.
    ExportHeadersFooters = true,
    ExportDocumentProperties = false
};
```

*ทำไมเราตั้งค่า `ExportImagesAsBase64 = false`*: รูปภาพที่เข้ารหัสเป็น Base64 ทำให้ไฟล์ markdown ใหญ่ขึ้นและทำลายจุดประสงค์ของการมีโฟลเดอร์ `assets` ที่สะอาด การปิดใช้งานนี้ทำให้ markdown มีเพียงการอ้างอิงแบบง่าย `![](assets/image.png)`

## ขั้นตอนที่ 4: บันทึกเอกสารเป็น Markdown

เมื่อทุกอย่างพร้อมแล้ว ขั้นตอนสุดท้ายคือบรรทัดเดียวที่สร้างไฟล์ `.md` และรูปภาพพร้อมกัน

```csharp
string markdownPath = Path.Combine(outputDir, "output.md");

// Save the document.
document.Save(markdownPath, markdownOptions);
Console.WriteLine($"✅ Conversion complete! Markdown saved to: {markdownPath}");
Console.WriteLine($"📁 Extracted images are in: {Path.Combine(outputDir, "assets")}");
```

**What you should see**  

- `output.md` ที่มีข้อความ markdown โดยแท็กรูปภาพแต่ละอันชี้ไปที่ `assets/<image_name>`  
- โฟลเดอร์ `assets` ที่เต็มไปด้วยไฟล์ PNG, JPEG หรือ GIF ที่ฝังอยู่ใน `input.docx` เดิม  

เปิด `output.md` ด้วยโปรแกรมดู markdown ใดก็ได้ (VS Code, GitHub, MkDocs) แล้วคุณจะเห็นรูปภาพแสดงผลเหมือนกับที่ปรากฏในเอกสาร Word

## การจัดการกับปัญหาที่พบบ่อย (FAQ)

### ถ้า DOCX มีชื่อรูปภาพซ้ำจะทำอย่างไร?

ฟังก์ชันช่วยเหลือ `GetUniqueFileName` ของเราจะต่อท้ายด้วยตัวเลขเพิ่ม (`image_1.png`, `image_2.png`, …) เพื่อป้องกันไม่ให้ไฟล์ถูกเขียนทับ

### ฉันต้องการไลเซนส์สำหรับ Aspose.Words หรือไม่?

เวอร์ชันทดลองใช้ได้สำหรับการทดลอง แต่สำหรับการใช้งานจริงควรซื้อไลเซนส์เพื่อเอาน้ำหนักประเมินผลออกและรับประสิทธิภาพเต็มรูปแบบ

### ฉันสามารถแปลงไฟล์ Word หลายไฟล์พร้อมกันได้หรือไม่?

ได้เลย. ใส่โค้ดการโหลดและบันทึกไว้ในลูป `foreach (var file in Directory.GetFiles(sourceFolder, "*.docx"))` ใช้ instance ของ `MyMarkdownResourceCallback` เดียวกัน (หรือสร้างใหม่ต่อไฟล์หากต้องการโฟลเดอร์ assets แยกกัน)

### แล้วทรัพยากรที่ไม่ใช่รูปภาพ (เช่น PDF ที่ฝังอยู่) จะทำอย่างไร?

Callback จะรับ **ทรัพยากรใดก็ได้** คุณสามารถตรวจสอบ `args.ResourceType` แล้วตัดสินใจว่าจะเก็บ, เพิกเฉย, หรือเปลี่ยนชื่อ

### วิธีนี้เข้ากันได้กับ .NET Core หรือไม่?

ใช่. โค้ดด้านบนตั้งเป้าหมายที่ .NET 6 แต่คุณสามารถดาวน์เกรดเป็น .NET Framework 4.7.2 โดยปรับไฟล์โครงการ Aspose.Words รองรับทั้งสอง runtime

## เคล็ดลับระดับมืออาชีพและแนวทางปฏิบัติที่ดีที่สุด

- **ทำให้โฟลเดอร์ assets สะอาด** – หลังจากแปลงเป็นชุด ให้รันสคริปต์สั้น ๆ เพื่อลบไฟล์ขนาด 0 ไบต์ที่อาจถูกสร้างจาก placeholder ว่าง  
- **ใช้ชื่อไฟล์ที่มีความหมาย** – หากต้องการชื่อรูปภาพที่มนุษย์อ่านได้ ให้ดึง `AltText` ดั้งเดิม (ถ้ามี) จาก `args.ResourceFileName` แล้วนำมาใช้  
- **การควบคุมเวอร์ชัน** – เก็บเฉพาะ markdown ใน repository; โฟลเดอร์ assets สามารถสร้างได้ในขั้นตอน CI ทำให้ repository มีขนาดเบา  
- **ประสิทธิภาพ** – สำหรับเอกสารขนาดใหญ่ ควรพิจารณา stream ผลลัพธ์โดยตั้งค่า `markdownOptions.SaveFormat = SaveFormat.Markdown;` แล้วเขียนไปยัง `MemoryStream` ก่อน  

## ตัวอย่างทำงานเต็มรูปแบบ (พร้อมคัดลอก‑วาง)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

/// <summary>
/// แสดงวิธีแปลง DOCX เป็น Markdown พร้อมแยกรูปภาพไปยังโฟลเดอร์ assets
/// </summary>
class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1️⃣ Paths – ปรับให้ตรงกับสภาพแวดล้อมของคุณ.
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        string outputDir = Path.Combine("YOUR_DIRECTORY", "output");
        Directory.CreateDirectory(outputDir);

        // -----------------------------------------------------------------
        // 2️⃣ Load the source document.
        // -----------------------------------------------------------------
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // 3️⃣ Set up the resource‑saving callback.
        // -----------------------------------------------------------------
        var callback = new MyMarkdownResourceCallback(outputDir);

        // -----------------------------------------------------------------
        // 4️⃣ Configure Markdown options.
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = callback,
            ExportImagesAsBase64 = false,
            ExportHeadersFooters = true,
            ExportDocumentProperties = false
        };

        // -----------------------------------------------------------------
        // 5️⃣ Save as Markdown.
        // -----------------------------------------------------------------
        string markdownFile = Path

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}