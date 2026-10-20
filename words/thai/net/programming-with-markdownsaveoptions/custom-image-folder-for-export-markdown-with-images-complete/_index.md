---
category: general
date: 2026-06-20
description: โฟลเดอร์รูปภาพแบบกำหนดเองช่วยให้คุณส่งออก Markdown พร้อมรูปภาพได้อย่างง่ายดาย
  เรียนรู้วิธีบันทึกรูปภาพในไดเรกทอรีเฉพาะและบันทึกรูปภาพใน Markdown ด้วย .NET.
draft: false
keywords:
- custom image folder
- export markdown with images
- save images specific directory
- save markdown images
language: th
og_description: โฟลเดอร์รูปภาพที่กำหนดเองทำให้การส่งออก markdown พร้อมรูปภาพเป็นเรื่องง่าย
  ทำตามคำแนะนำขั้นตอนต่อขั้นตอนนี้เพื่อบันทึกรูปภาพในไดเรกทอรีเฉพาะและบันทึกรูปภาพใน
  markdown.
og_title: โฟลเดอร์รูปภาพกำหนดเอง – ส่งออก Markdown พร้อมรูปภาพ
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  headline: custom image folder for export markdown with images – Complete Guide
  type: TechArticle
- description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  name: custom image folder for export markdown with images – Complete Guide
  steps:
  - name: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
    text: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
  - name: Eliminates a second file‑system scan, which can be costly for large docs.
    text: Eliminates a second file‑system scan, which can be costly for large docs.
  - name: Gives you the flexibility to rename or compress images on the fly.
    text: Gives you the flexibility to rename or compress images on the fly.
  type: HowTo
tags:
- Aspose.Words
- Markdown
- .NET
title: โฟลเดอร์รูปภาพแบบกำหนดเองสำหรับการส่งออก Markdown พร้อมรูปภาพ – คู่มือเต็ม
url: /th/net/programming-with-markdownsaveoptions/custom-image-folder-for-export-markdown-with-images-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# โฟลเดอร์รูปภาพแบบกำหนดเอง – ส่งออก Markdown พร้อมรูปภาพใน .NET

เคยต้องการ **โฟลเดอร์รูปภาพแบบกำหนดเอง** เมื่อต้องส่งออก markdown พร้อมรูปภาพหรือไม่? คุณไม่ได้เป็นคนเดียวที่เจอปัญหานี้ ไม่ว่าคุณจะสร้างเอกสาร, บล็อกโพสต์, หรือคู่มือ API การจัดเก็บรูปภาพไว้ในไดเรกทอรีเฉพาะช่วยให้คุณหลีกเลี่ยงโครงสร้างไฟล์ที่ยุ่งเหยิงในภายหลัง

ในบทแนะนำนี้เราจะพาคุณผ่านโซลูชันที่พร้อมรันเต็มรูปแบบ ซึ่งจะแสดง **วิธีบันทึกรูปภาพในไดเรกทอรีที่กำหนด** ขณะสร้างไฟล์ markdown คุณจะเห็นว่าการใช้ callback เป็นวิธีที่สะอาดที่สุด และคุณจะจบคู่มือด้วยตัวอย่างโค้ดเต็มที่สามารถนำไปวางในโปรเจกต์ .NET ใดก็ได้

## สิ่งที่คุณจะได้เรียนรู้

- ตั้งค่า Aspose.Words (หรือไลบรารีที่คล้ายกัน) เพื่อเปลี่ยนเส้นทางการบันทึกรูปภาพ
- Implement callback ที่เขียนแต่ละรูปภาพลงใน **โฟลเดอร์รูปภาพแบบกำหนดเอง**
- ใช้ `MarkdownSaveOptions` เพื่อเชื่อมต่อทุกอย่างและ **บันทึกรูปภาพใน markdown** อย่างถูกต้อง
- เคล็ดลับการจัดการกรณีขอบเช่น ชื่อซ้ำหรือไฟล์ขนาดใหญ่

### ข้อกำหนดเบื้องต้น

| ข้อกำหนด | เหตุผลที่สำคัญ |
|-------------|----------------|
| .NET 6+ (หรือ .NET Framework 4.7+) | โค้ดใช้ `FileStream` และ `Guid` |
| Aspose.Words for .NET (หรือ markdown exporter ที่เทียบเคียง) | มี `MarkdownSaveOptions` และอินเทอร์เฟซ callback |
| ความรู้พื้นฐาน C# | คุณต้องเข้าใจคลาสและสตรีม |
| วัตถุ `Document` ที่มีอยู่ (`doc`) | บทแนะนำสมมติว่าคุณมีเอกสารที่เติมข้อมูลแล้ว |

ไม่ต้องใช้เครื่องมือภายนอกเพิ่มเติม—ทุกอย่างทำงานแบบโลคัล

## ขั้นตอนที่ 1: สร้าง Callback ที่บันทึกรูปภาพแต่ละไฟล์ในโฟลเดอร์รูปภาพแบบกำหนดเอง

หัวใจของโซลูชันคือคลาสที่ implements `IResourceSavingCallback` ภายใน `ResourceSaving` เราจะสร้างชื่อไฟล์ที่ไม่ซ้ำกัน, สร้างพาธเต็มภายในโฟลเดอร์ที่คุณเลือก, แล้วบอกไลบรารีให้เขียนรูปภาพที่นั่น

```csharp
// Step 1: Define a callback that stores each image in a custom folder
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique file name for the image
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Build the full path inside the desired resources directory
        var fullPath = Path.Combine("YOUR_DIRECTORY", fileName);

        // Redirect the saving stream to the new location
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;   // close after save

        // Update the markdown reference to point to the new file name
        args.ResourceFileName = fileName;
    }
}
```

**ทำไมวิธีนี้ถึงได้ผล:**  
- `Guid.NewGuid()` รับประกันชื่อที่ไม่ซ้ำกัน, ป้องกันการชนเมื่อเอกสารต้นทางมีรูปหลายรูปที่มีชื่อไฟล์เดิม  
- การสลับ `args.Stream` ทำให้ exporter เขียนข้อมูลไบนารีไปยังที่ที่เรากำหนด  
- การอัปเดต `args.ResourceFileName` ทำให้ markdown reference (`![](img_…​)`) ชี้ไปยังไฟล์ที่อยู่ใน **โฟลเดอร์รูปภาพแบบกำหนดเอง** ของคุณ

> **เคล็ดลับ:** แทนที่ `"YOUR_DIRECTORY"` ด้วยพาธที่สร้างจาก `Path.Combine(Environment.CurrentDirectory, "Images")` หากคุณต้องการให้โฟลเดอร์อยู่ข้างไฟล์ markdown โดยอัตโนมัติ

## ขั้นตอนที่ 2: เชื่อม Callback เข้ากับ Markdown Save Options

ต่อไปเราจะสร้างอินสแตนซ์ `MarkdownSaveOptions` และกำหนด callback ของเราให้กับมัน ซึ่งบอก exporter ให้เรียก `ImageSavingCallback` สำหรับทุก resource ที่ฝังอยู่

```csharp
// Step 2: Configure Markdown save options to use the callback
var markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ImageSavingCallback()
};
```

**อะไรกำลังเกิดขึ้นเบื้องหลัง?**  
เมื่อ `doc.Save` ทำงาน, Aspose.Words จะเดินผ่านโครงสร้าง node ของเอกสาร ทุกครั้งที่เจอรูปภาพ มันจะเรียก `ResourceSaving` Callback ของเราจะดักจับเหตุการณ์นี้, เปลี่ยนเส้นทางสตรีมของรูปภาพ, และอัปเดตลิงก์ markdown ผลลัพธ์คือ รูปภาพทั้งหมดจะถูกเก็บในโฟลเดอร์ที่คุณระบุและไฟล์ markdown จะอ้างอิงพวกมันอย่างถูกต้อง

## ขั้นตอนที่ 3: บันทึกเอกสารเป็น Markdown – รูปภาพจะถูกบันทึกผ่าน Callback

สุดท้ายเราจะเรียก `Save` พร้อมกับอ็อบเจ็กต์ options ไลบรารีจะทำงานหนักส่วนของเราแค่จัดตำแหน่งไฟล์

```csharp
// Step 3: Save the document as Markdown; images are saved via the callback
doc.Save("YOUR_DIRECTORY/DocWithImages.md", markdownOptions);
```

หาก `"YOUR_DIRECTORY"` เป็น `C:\Docs\MyProject` คุณจะเห็น:

```
C:\Docs\MyProject\DocWithImages.md
C:\Docs\MyProject\img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png
C:\Docs\MyProject\img_7e8f9a0b‑c1d2‑3e4f‑5g6h‑7i8j9k0l1m2n.jpg
```

ไฟล์ markdown จะมีบรรทัดเช่น:

```markdown
![Image](img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png)
```

นี่คือสิ่งที่คุณต้องการเพื่อ **บันทึกรูปภาพใน markdown** ไปยังตำแหน่งที่คาดเดาได้

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นแอปคอนโซลที่พร้อมคัดลอก‑วางลง Visual Studio มันสร้างเอกสารง่าย ๆ พร้อมรูปภาพ แล้วส่งออกโดยใช้วิธีโฟลเดอร์แบบกำหนดเอง

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, markdown with images!");
        builder.InsertImage("sample.jpg"); // Ensure sample.jpg exists next to the exe

        // 2️⃣ Define the callback (same as earlier)
        var options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback()
        };

        // 3️⃣ Choose output folder (feel free to change)
        string outputDir = Path.Combine(Environment.CurrentDirectory, "Exported");
        Directory.CreateDirectory(outputDir); // creates if missing

        // 4️⃣ Save markdown and images
        string mdPath = Path.Combine(outputDir, "Document.md");
        doc.Save(mdPath, options);

        Console.WriteLine($"Markdown saved to: {mdPath}");
        Console.WriteLine("Images stored in the same folder.");
    }
}

// Callback class – identical to the earlier snippet
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
        var fullPath = Path.Combine("Exported", fileName);
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;
        args.ResourceFileName = fileName;
    }
}
```

**ผลลัพธ์ที่คาดหวัง**

เมื่อรันโปรแกรมจะพิมพ์บางอย่างเช่น:

```
Markdown saved to: C:\MyApp\Exported\Document.md
Images stored in the same folder.
```

เปิด `Document.md` แล้วคุณจะเห็น markdown image reference ที่ชี้ไปยัง `img_…​` ไฟล์รูปภาพจะอยู่ข้างไฟล์ markdown อย่างตรงตามที่ **โฟลเดอร์รูปภาพแบบกำหนดเอง** กำหนดไว้

## การจัดการกรณีขอบทั่วไป

| สถานการณ์ | วิธีแก้ |
|-----------|----------|
| **ชื่อไฟล์ซ้ำ** | การใช้ `Guid` ป้องกันการซ้ำอยู่แล้ว; หากต้องการชื่อที่อ่านง่าย สามารถต่อเลขลำดับ (`img_001.png`, `img_002.png`) |
| **ชุดรูปภาพขนาดใหญ่** | สตรีมโดยตรงไปยังดิสก์ตามที่แสดง; หลีกเลี่ยงการโหลดรูปทั้งหมดเข้าสู่หน่วยความจำ |
| **ไดเรกทอรีผลลัพธ์ต่างกันในแต่ละครั้ง** | ส่งโฟลเดอร์เป้าหมายเป็นพารามิเตอร์ใน constructor ของ `ImageSavingCallback` แทนการ hard‑code `"Exported"` |
| **ไม่มีสิทธิ์เขียน** | ตรวจสอบให้แอปทำงานด้วยสิทธิ์ที่เพียงพอหรือเลือกโฟลเดอร์ที่ผู้ใช้เขียนได้ เช่น `%TEMP%` |
| **resource ที่ไม่ใช่รูปภาพ (เช่น CSS)** | Callback จะถูกเรียกสำหรับทุก resource; คุณสามารถตรวจสอบ `args.ResourceType` แล้วจัดการเฉพาะรูปภาพได้ |

## ทำไมต้องใช้ Callback แทนการประมวลผลหลังจากบันทึก?

คุณอาจสงสัยว่า “ทำไมไม่สร้าง markdown ก่อนแล้วค่อยย้ายรูปภาพหลังจากนั้น?” วิธี callback มีข้อดี:

1. รับประกัน **ความเป็นอะตอม** – รูปภาพและ markdown ถูกเขียนพร้อมกัน ป้องกันลิงก์เสีย  
2. ลดการสแกนไฟล์ระบบครั้งที่สอง ซึ่งอาจใช้เวลามากสำหรับเอกสารขนาดใหญ่  
3. ให้ความยืดหยุ่นในการเปลี่ยนชื่อหรือบีบอัดรูปภาพขณะทำงาน

สรุปคือ นี่คือ **วิธีที่มั่นคงที่สุดในการส่งออก markdown พร้อมรูปภาพ** พร้อมการจัดเก็บใน **โฟลเดอร์รูปภาพแบบกำหนดเอง**

## สรุป

เราได้ครอบคลุมทุกอย่างที่คุณต้องการเพื่อ **บันทึกรูปภาพในไดเรกทอรีที่กำหนด** และ **บันทึกรูปภาพใน markdown** ด้วยกลยุทธ์ **โฟลเดอร์รูปภาพแบบกำหนดเอง** โดยการ implement `IResourceSavingCallback`, ตั้งค่า `MarkdownSaveOptions`, และเรียก `doc.Save` คุณจะได้โครงสร้างโฟลเดอร์ที่เรียบร้อยและ markdown reference ที่เชื่อถือได้—ทั้งหมดในไม่กี่สิบบรรทัดของโค้ด

ต่อไปคุณอาจสำรวจ:

- เพิ่มการบีบอัดรูปภาพภายใน callback  
- สร้าง `README.md` ที่ลิงก์ไปยังโฟลเดอร์โดยอัตโนมัติ  
- ขยาย callback เพื่อจัดการ resource ประเภทอื่น เช่น CSS หรือสคริปต์

ลองใช้ใน pipeline การสร้างเอกสารครั้งต่อไป—ตัวคุณในอนาคตจะขอบคุณสำหรับโครงสร้างโฟลเดอร์ที่เป็นระเบียบ

Happy coding!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}