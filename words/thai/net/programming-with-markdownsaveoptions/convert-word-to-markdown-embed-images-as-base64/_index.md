---
category: general
date: 2026-01-03
description: แปลง Word เป็น Markdown และฝังรูปภาพเป็น base64 ในขั้นตอนเดียว เรียนรู้วิธีบันทึก
  Word เป็น Markdown, สร้าง Markdown จาก Word, และใช้ base64 image data URI.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: th
og_description: แปลง Word เป็น Markdown และฝังรูปภาพเป็น base64 data URIs บทแนะนำขั้นตอนนี้แสดงวิธีบันทึก
  Word เป็น Markdown และสร้าง Markdown จาก Word.
og_title: แปลง Word เป็น Markdown – คู่มือการฝังรูปภาพ Base64
tags:
- Aspose.Words
- C#
- Markdown
title: แปลง Word เป็น Markdown – ฝังรูปภาพเป็น Base64
url: /th/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แปลง Word เป็น Markdown – ฝังรูปภาพเป็น Base64

เคยต้องการ **convert Word to markdown** แต่เจอปัญหาเรื่องรูปภาพบ่อยไหม? คุณไม่ได้เป็นคนเดียว Word ชอบเก็บรูปภาพเป็นไฟล์แยกต่างหาก ในขณะที่ markdown ชอบใช้สตริง `data:image/...;base64,` เล็ก ๆ ที่ทำให้ทุกอย่างอยู่ในไฟล์เดียวอย่างเป็นระเบียบ.  

ในบทแนะนำนี้ เราจะพาคุณผ่านโซลูชันที่สมบูรณ์พร้อมใช้งาน ซึ่ง **saves Word as markdown**, **embeds images as base64**, และแม้กระทั่งแสดงวิธี **generate markdown from Word** ด้วย Aspose.Words for .NET. เมื่อเสร็จคุณจะได้ไฟล์ `.md` ไฟล์เดียวที่แสดงผลเหมือนกับเอกสารต้นฉบับ—โดยไม่ต้องใช้โฟลเดอร์รูปภาพแยกต่างหาก.

## สิ่งที่คุณต้องการ

- **.NET 6.0 หรือใหม่กว่า** (สิ่งใดที่สามารถอ้างอิงแพ็กเกจ NuGet)
- **Aspose.Words for .NET** (รุ่นทดลองฟรีใช้งานได้ดีสำหรับการทดสอบ)
- ไฟล์ `.docx` ง่าย ๆ ที่มีรูปภาพไม่กี่รูป (เราจะเรียกมันว่า `input.docx`)
- IDE ที่คุณชอบ (Visual Studio, Rider, VS Code—เลือกตามที่คุณต้องการ)

หากคุณมีแล้ว เยี่ยม—มาเริ่มกันเลย หากยังไม่มี การติดตั้งแพ็กเกจ NuGet ทำได้ด้วยบรรทัดเดียว:

```bash
dotnet add package Aspose.Words
```

## ขั้นตอนที่ 1: โหลดเอกสาร Word — จุดเริ่มต้นสำหรับ **convert word to markdown**

ก่อนอื่นเราต้องโหลดไฟล์ `.docx` เข้าสู่หน่วยความจำ นี่คือจุดเริ่มต้นของการแปลง.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **ทำไมเรื่องนี้สำคัญ:**  
> การโหลดเอกสารทำให้ Aspose เข้าถึงข้อความ, สไตล์, และทรัพยากรที่ฝังอยู่ทั้งหมดได้อย่างเต็มที่ หากข้ามขั้นตอนนี้ จะไม่มีอะไรให้แปลง.

## ขั้นตอนที่ 2: ตั้งค่า MarkdownSaveOptions พร้อม Callback การบันทึกทรัพยากร

Aspose ให้คุณดักจับทุกทรัพยากร (เช่นรูปภาพ) ที่โดยปกติจะถูกบันทึกลงดิสก์ โดยการให้ `IResourceSavingCallback` แบบกำหนดเอง เราสามารถแทนที่การบันทึกแบบไฟล์ด้วย **base64 image data uri**.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### ตัวจัดการแบบกำหนดเอง – แปลงรูปภาพเป็น Base64

ด้านล่างเป็นการทำงานเต็มรูปแบบ โปรดสังเกตว่าเราตรวจสอบ `args.ResourceType == ResourceType.Image` แล้วทำตามขั้นตอน:

1. เขียนรูปภาพลงใน `MemoryStream`.
2. แปลงอาร์เรย์ไบต์เป็นสตริง Base64.
3. สร้าง URI `data:image/jpeg;base64,` และกำหนดให้กับ `args.Uri`.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **เคล็ดลับระดับมืออาชีพ:** หากไฟล์ Word ของคุณใช้ PNG ให้เปลี่ยน `ImageSaveOptions.DefaultJpeg` เป็น `ImageSaveOptions.DefaultPng` และปรับ MIME type ให้ตรง (`image/png`).

## ขั้นตอนที่ 3: บันทึกเอกสารเป็น Markdown – ขั้นตอนสุดท้ายของ **save word as markdown** 

เมื่อ Callback พร้อม การบันทึกจริงเป็นบรรทัดเดียว.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

เมื่อคุณเปิด `output.md` ในโปรแกรมดู markdown ใด ๆ (เช่น VS Code preview, GitHub ฯลฯ) คุณจะเห็นข้อความตรงกับไฟล์ Word ต้นฉบับ และรูปภาพจะแสดงเป็น inline โดยไม่ต้องมีไฟล์รูปแยก.

## ผลลัพธ์ที่คาดหวัง

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

บรรทัด `![Embedded Image]` เป็น **base64 image data uri**—รูปภาพทั้งหมดถูกเข้ารหัสไว้ที่นั่น ไม่ต้องมีโฟลเดอร์เพิ่มเติม ไม่ต้องกังวลลิงก์เสีย.

## กรณีขอบเขต & วิธีจัดการ

| สถานการณ์ | วิธีทำ |
|-----------|------------|
| **Large Images** – Base64 ทำให้ขนาดเพิ่มประมาณ ~33% | พิจารณาปรับขนาดก่อนแปลง: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **Non‑JPEG Images** (PNG, GIF) | ตรวจจับรูปแบบต้นฉบับผ่าน `args.ResourceData.ImageType` แล้วตั้ง MIME type ให้ถูกต้อง (`image/png`, `image/gif`). |
| **Very Long Documents** (hundreds of images) | คอยตรวจสอบการใช้หน่วยความจำ; คุณสามารถสตรีมแต่ละรูปไปยังดิสก์ชั่วคราวหากกระบวนการหมด RAM. |
| **Need Separate Image Files** (เช่น สำหรับเว็บไซต์ static) | คืนค่า `false` จาก callback สำหรับรูปที่ต้องการเก็บเป็นไฟล์ แล้วให้ Aspose เขียนลงโฟลเดอร์. |

## คำถามทั่วไป (ตอบล่วงหน้า)

- **Does this work with .doc files?** ใช่—Aspose.Words สามารถโหลดไฟล์ `.doc` เก่าได้เช่นเดียวกับการโหลด `.docx`. เพียงระบุ `new Document("myfile.doc")`.
- **What about tables and footnotes?** พวกมันได้รับการสนับสนุนเต็มที่โดย Markdown exporter. ตารางจะกลายเป็นตาราง markdown; footnote จะเป็นการอ้างอิงแบบ inline.
- **Can I change the markdown flavor?** `MarkdownSaveOptions` มี property `MarkdownVersion` (CommonMark, GitHub, ฯลฯ). ตั้งค่าก่อนบันทึกหากต้องการไวยากรณ์เฉพาะ.

## ตัวอย่างเต็มพร้อมรัน

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปคอนโซลได้ รวมถึงคำสั่ง using ทั้งหมด, คลาส handler, และการจัดการข้อผิดพลาด.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

รันโปรแกรม เปิดไฟล์ `output.md` ที่สร้างขึ้น และคุณจะเห็นสำเนา markdown ที่สมบูรณ์ของไฟล์ Word ของคุณ—**convert word to markdown** ไม่เคยง่ายขนาดนี้.

## สรุป

เราเริ่มจากปัญหา **convert word to markdown** พร้อมการฝังรูปภาพแบบ inline. ด้วยการโหลดเอกสาร, ตั้งค่า callback ของ `MarkdownSaveOptions`, และบันทึกไฟล์ เราได้โซลูชัน **save word as markdown** ที่สะอาดซึ่งสร้างสตริง **base64 image data uri** คุณตอนนี้ยังรู้วิธี **embed images as base64**, จัดการกรณีขอบเขต, และปรับกระบวนการสำหรับประเภทรูปภาพต่าง ๆ.

## ต่อไปคืออะไร?

- **Generate HTML instead of markdown** – เปลี่ยนจาก `MarkdownSaveOptions` เป็น `HtmlSaveOptions` และใช้ callback เดิม.
- **Batch convert multiple files** – ห่อหุ้มตรรกะในลูป `foreach` ที่วนผ่านโฟลเดอร์.
- **Integrate into a CI pipeline** – ทำให้การสร้างเอกสารอัตโนมัติสำหรับเว็บไซต์ static.

คุณสามารถทดลอง ปรับคุณภาพรูปภาพ หรือแม้แต่เพิ่มการจัดการทรัพยากรแบบกำหนดเองของคุณ (เช่น อัปโหลดรูปไปยัง CDN แล้วแทรก URL). ไม่มีขีดจำกัดเมื่อคุณผสาน Aspose.Words กับความคิดสร้างสรรค์เล็ก ๆ ของ C#.

ขอให้เขียนโค้ดอย่างสนุกสนาน และขอให้ markdown ของคุณแสดงผลอย่างสมบูรณ์เสมอ! 

![แผนภาพแสดงกระบวนการ convert word to markdown – ฝังรูปภาพเป็น Base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "แผนภาพกระบวนการ convert word to markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}