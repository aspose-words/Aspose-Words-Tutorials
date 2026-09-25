---
category: general
date: 2026-02-26
description: สร้างโฟลเดอร์บทเรียน C# ที่แสดงวิธีแปลง Word เป็น markdown, ดึงรูปภาพจากไฟล์
  docx, และคัดลอกสตรีมไปยังไฟล์—ทั้งหมดในขั้นตอนเดียว
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: th
og_description: บทเรียน C# สร้างโฟลเดอร์พาคุณผ่านขั้นตอนการแปลง Word เป็น markdown,
  การดึงภาพจากไฟล์ docx, และการคัดลอกสตรีมไปยังไฟล์ พร้อมตัวอย่างโค้ดที่ชัดเจน
og_title: สร้างโฟลเดอร์ C# – แปลง Word เป็น Markdown และดึงรูปภาพ
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: สร้างโฟลเดอร์ C# – แปลง Word เป็น Markdown และดึงรูปภาพ
url: /th/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างโฟลเดอร์ C# – แปลง Word เป็น Markdown และดึงรูปภาพ

เคยต้อง **สร้างโฟลเดอร์ C#** พร้อมกับแปลงเอกสาร Word เป็น markdown และดึงรูปภาพทั้งหมดออกมาหรือไม่? คุณไม่ได้เป็นคนเดียวที่สับสนกับเรื่องนี้ ในหลาย ๆ pipeline ของการอัตโนมัติ คุณต้องจัดการกับงานระบบไฟล์ การแปลงรูปแบบ และการจัดการข้อมูลไบนารี—ทั้งหมดในครั้งเดียว  

ในคู่มือนี้ เราจะพาไปผ่านโซลูชันที่สมบูรณ์และสามารถรันได้ ซึ่งทำสิ่งนั้นโดยตรง: สร้างไดเรกทอรีเป้าหมาย, แปลงไฟล์ `.docx` เป็น markdown, ดึงรูปภาพที่ฝังอยู่แต่ละรูป, และใช้ตรรกะ **copy stream to file** เพื่อให้รูปภาพถูกบันทึกลงที่คุณต้องการ ไม่มีสคริปต์ภายนอก ไม่มีขั้นตอนด้วยมือ เพียงแค่ C# แท้ ๆ และไลบรารี Aspose.Words

> **สิ่งที่คุณจะได้**  
> * โครงสร้างโฟลเดอร์ที่ชัดเจนพร้อมสำหรับ markdown และ assets  
> * ไฟล์ markdown ที่อ้างอิงรูปภาพที่ดึงออกมาอย่างถูกต้อง  
> * โค้ดต้นฉบับเต็มที่คุณสามารถใส่ลงในโปรเจกต์ .NET ใดก็ได้  

ก่อนที่เราจะเริ่ม, โปรดตรวจสอบว่าคุณมี:

* SDK .NET 6.0 (หรือใหม่กว่า) ติดตั้งแล้ว – โค้ดใช้ฟีเจอร์ภาษาแบบสมัยใหม่  
* ไลเซนส์สำหรับ **Aspose.Words for .NET** (เวอร์ชันทดลองฟรีใช้สำหรับทดสอบ)  
* Visual Studio 2022 หรือโปรแกรมแก้ไขที่คุณชื่นชอบ  

หากคุณสงสัย *ทำไม* คุณถึงต้องการดึงรูปภาพแทนการฝังไว้, คิดถึง static site generators: พวกเขาชอบ markdown ที่มีพาธรูปภาพแบบ relative, และการเก็บ assets ไว้ในโฟลเดอร์เฉพาะทำให้จัดการง่ายและเป็นมิตรกับแคช.

---

## สร้างโฟลเดอร์ C# และเตรียมโครงสร้างเอาต์พุต

สิ่งแรกที่เราต้องการคือที่เก็บบนดิสก์ที่ทุกอย่างจะอยู่ ขั้นตอนนี้คือการทำงานของ **create folder C#** และมันง่ายกว่าที่คิดด้วย `Directory.CreateDirectory` เมธอดนี้เป็น idempotent—จะไม่โยนข้อผิดพลาดหากโฟลเดอร์มีอยู่แล้ว ซึ่งช่วยให้เราไม่ต้องตรวจสอบเพิ่มเติม.

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**ทำไมสิ่งนี้ถึงสำคัญ:**  
การสร้างโฟลเดอร์ล่วงหน้าช่วยรับประกันว่าขั้นตอนการบันทึกต่อมาจะไม่ล้มเหลวด้วย `DirectoryNotFoundException`. นอกจากนี้ยังให้โครงสร้างที่คาดเดาได้: `output/markdown` สำหรับไฟล์ `.md` และ `output/MyImages` สำหรับรูปภาพทุกรูปที่เราดึงออก

> **เคล็ดลับมืออาชีพ:** หากคุณรันโปรแกรมหลายครั้ง, คุณอาจต้องการทำความสะอาดโฟลเดอร์รูปภาพก่อน (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`) เพื่อหลีกเลี่ยงไฟล์เก่า

## แปลง Word เป็น Markdown ด้วย Aspose.Words

เมื่อโครงสร้างไดเรกทอรีพร้อมแล้ว, มาแปลงเอกสาร Word เป็น markdown กัน. Aspose.Words ทำงานหนักให้—ไม่ต้องยุ่งกับ OpenXML หรือคอนเวอร์เตอร์ของบุคคลที่สาม.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**อะไรที่เกิดขึ้นภายใน?**  
`MarkdownSaveOptions` บอก Aspose ให้สร้างไวยากรณ์ markdown. โดยค่าเริ่มต้น, ไลบรารีจะวางรูปภาพในโฟลเดอร์เดียวกับไฟล์ markdown พร้อมชื่อที่สร้างอัตโนมัติ. โดยการให้ `ResourceSavingCallback`, เราจับพฤติกรรมนั้นและ **copy stream to file** ไปยังตำแหน่งที่เราต้องการ

## ดึงรูปภาพจาก DOCX และบันทึก

คลาส callback implements `IResourceSavingCallback`. ภายในเราจะได้รับอ็อบเจ็กต์ `ResourceSavingArgs` ที่มีสตรีมรูปภาพต้นฉบับและชื่อไฟล์ที่แนะนำ. จากนั้นเราจะเขียนสตรีมนั้นลงดิสก์, เปลี่ยนชื่อไฟล์ตามต้องการ, และบอก Aspose ว่าเราได้จัดการแล้ว.

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### รูปแบบ markdown ที่จะได้

หลังจากการแปลง, `output.md` ที่สร้างขึ้นจะมีบรรทัดเช่น:

```markdown
![Image 1](MyImages/img_picture1.png)
```

เนื่องจากเราเปลี่ยน `args.ResourceFileName` ให้เป็นพาธ relative, markdown จะชี้ตรงไปยังโฟลเดอร์ที่เราสร้าง นี่คือสิ่งที่ static site generators คาดหวัง

**การจัดการกรณีขอบ:**  
*หากเอกสารมีชื่อรูปภาพซ้ำ*, การใส่คำนำหน้า `img_` กับชื่อเดิมมักจะหลีกเลี่ยงการชนกัน, แต่คุณก็สามารถเพิ่ม GUID (`Guid.NewGuid()`) เพื่อความเป็นเอกลักษณ์อย่างสมบูรณ์

## คัดลอกสตรีมไปยังไฟล์ – จัดการข้อมูลรูปภาพ

คุณอาจสงสัยว่าทำไมเราไม่เรียก `File.WriteAllBytes` ตรง ๆ คำตอบอยู่ที่ **stream flexibility**. `args.Stream` อาจเป็น memory stream, network stream, หรือการทำงานอื่นใด. ด้วยการใช้ `CopyTo`, เราไม่ผูกมัดและให้ .NET จัดการขนาดบัฟเฟอร์อย่างมีประสิทธิภาพ

นี่คือเมธอดยูทิลิตี้แบบกะทัดรัด หากคุณต้องการคัดลอกสตรีมทั่วไปไปที่อื่น:

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

คุณสามารถแทนที่การคัดลอกในบรรทัดเดียวใน `ImageSavingCallback` ด้วยการเรียก `CopyStreamToFile` หากคุณต้องการแนวทาง single‑responsibility

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

การรวมส่วนต่าง ๆ เข้าด้วยกันจะให้โปรแกรมอิสระที่คุณสามารถรันจากบรรทัดคำสั่ง:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**ผลลัพธ์ที่คาดหวัง**

* `output/markdown/output.md` – ไฟล์ markdown ที่อ้างอิงรูปภาพเป็น `![Alt text](MyImages/img_picture1.png)`.  
* `output/MyImages/` – ไฟล์ PNG/JPEG หนึ่งไฟล์ต่อรูปภาพที่เคยอยู่ใน `input.docx`.  

เปิด markdown ในโปรแกรมดูใดก็ได้ (VS Code, GitHub, หรือ static‑site generator) แล้วคุณจะเห็นรูปภาพแสดงผลตรงตำแหน่งที่เคยอยู่ในไฟล์ Word ดั้งเดิม.

## คำถามที่พบบ่อย & การแก้ไขปัญหา

| Question | Answer |
|----------|--------|
| **ถ้าโฟลเดอร์เป้าหมายมีไฟล์อยู่แล้วจะทำอย่างไร?** | `Directory.CreateDirectory` จะไม่เขียนทับ. หากต้องการการรันที่สะอาด, ลบ |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}