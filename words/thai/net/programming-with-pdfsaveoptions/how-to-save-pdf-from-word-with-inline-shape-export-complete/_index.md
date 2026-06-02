---
category: general
date: 2026-06-02
description: วิธีบันทึก PDF จากไฟล์ DOCX ด้วย Aspose.Words, ส่งออกรูปทรงเป็นแท็ก span
  แบบอินไลน์, และแปลง Word เป็น PDF เพียงไม่กี่ขั้นตอน.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: th
og_description: วิธีบันทึก PDF จากเอกสาร Word ด้วย Aspose.Words โดยส่งออกรูปทรงลอยเป็นแท็ก
  span แบบอินไลน์เพื่อให้ได้ผลลัพธ์การแปลง Word เป็น PDF ที่สะอาดและแม่นยำ
og_title: วิธีบันทึก PDF จาก Word – การสอนส่งออก Inline Shape
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: วิธีบันทึก PDF จาก Word ด้วยการส่งออกรูปแบบในบรรทัด – คู่มือฉบับสมบูรณ์
url: /th/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีบันทึก PDF จาก Word พร้อมการส่งออก Inline Shape – คู่มือฉบับสมบูรณ์

เคยสงสัย **วิธีบันทึก PDF** จากไฟล์ Word พร้อมให้รูปทรงที่ลอยอยู่ทั้งหมดจัดเรียงอย่างเป็นระเบียบในข้อความหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายแอปพลิเคชันระดับองค์กรเราต้อง *แปลง Word เป็น PDF* โดยไม่ให้ภาพหรือวัตถุวาดที่ลอยอยู่กระจัดกระจาย ข่าวดีคือ Aspose.Words ทำให้กระบวนการนี้ง่ายดาย และคุณยังสามารถบอกไลบรารีให้ **ส่งออกรูปทรงเป็นแท็ก `<span>` แบบอินไลน์** เพื่อให้ PDF ดูเหมือนกับ DOCX ดั้งเดิม

ในบทแนะนำนี้เราจะเดินผ่านกระบวนการทั้งหมด—โหลด DOCX ปรับแต่ง `PdfSaveOptions` และสุดท้ายบันทึกเป็น PDF ที่สะอาดตา เมื่อจบคุณจะรู้ **วิธีบันทึก PDF**, **บันทึก docx เป็น pdf**, และแม้กระทั่ง **วิธีส่งออกรูปทรง** ด้วย *แท็ก span แบบอินไลน์* 

## สิ่งที่คุณต้องมี

- **Aspose.Words for .NET** (เวอร์ชันล่าสุด 24.x ณ เวลาที่เขียน)  
- **.NET 6.0** หรือใหม่กว่า – โค้ดนี้ยังทำงานบน .NET Framework 4.7.2 ได้เช่นกัน แต่ .NET 6 เป็นจุดที่เหมาะที่สุด  
- เอกสาร Word ง่าย ๆ ที่มีอย่างน้อยหนึ่งรูปทรงที่ลอยอยู่ (รูปภาพ, กล่องข้อความ, หรือการวาด)  
- IDE ใดก็ได้ที่คุณชอบ (Visual Studio, Rider, VS Code + ส่วนขยาย C#)  

แค่นี้—ไม่มีแพ็กเกจ NuGet เพิ่มเติม ไม่มีการทำ COM interop ที่ซับซ้อน พร้อมหรือยัง? ไปกันเลย  

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และเพิ่ม Aspose.Words

เริ่มต้นด้วยการสร้างแอปคอนโซล (หรือผสานโค้ดนี้เข้าไปในบริการที่มีอยู่ของคุณ)

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **เคล็ดลับ:** หากคุณใช้ Visual Studio สามารถเพิ่มแพ็กเกจผ่าน UI ของ NuGet Package Manager—แค่ค้นหา *Aspose.Words*  

## ขั้นตอนที่ 2: โหลดเอกสารต้นฉบับ

เมื่อไลบรารีถูกอ้างอิงแล้ว เราก็สามารถโหลด DOCX ได้ นี่คือขั้นตอนแรกของ **วิธีบันทึก pdf** ที่ทำให้ไฟล์ต้นฉบับเข้าสู่หน่วยความจำ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**ทำไมขั้นตอนนี้สำคัญ:** การโหลดไฟล์จะตรวจสอบว่าเส้นทางถูกต้องและ Aspose สามารถพาร์สโครงสร้างของ Word ได้ หากไฟล์มีรูปทรงที่ลอยอยู่ พวกมันจะเป็นส่วนหนึ่งของโครงสร้าง `Document`  

## ขั้นตอนที่ 3: ตั้งค่า PDF Save Options – ส่งออกรูปทรงเป็นแท็กอินไลน์

นี่คือหัวใจของ **วิธีส่งออกรูปทรง** โดยค่าเริ่มต้น Aspose.Words จะเรนเดอร์รูปทรงที่ลอยเป็นวัตถุแยกใน PDF ซึ่งอาจทำให้เลย์เอาต์เปลี่ยนแปลง การตั้งค่า `ExportFloatingShapesAsInlineTag` เป็น `true` จะบอกเอนจินให้ห่อแต่ละรูปทรงด้วยแท็ก `<span>` แบบอินไลน์ เพื่อรักษาการไหลของข้อความ

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**ทำไมต้องเปิดฟลักนี้?** ลองนึกถึงสัญญาที่มีกล่องลายเซ็นลอยอยู่เหนือข้อความ หากแปลงเป็น PDF โดยไม่มีการตั้งค่านี้ กล่องอาจปรากฏบนหน้าที่ต่างกัน แท็ก `<span>` แบบอินไลน์ทำให้รูปทรงถูกยึดกับย่อหน้าที่อยู่รอบ ๆ สร้างสำเนาภาพที่ตรงกับต้นฉบับ  

## ขั้นตอนที่ 4: บันทึกเอกสารเป็น PDF

สุดท้าย เราเรียก `doc.Save` พร้อมตัวเลือกที่เราตั้งค่าไว้ นี่คือช่วงเวลาที่คุณ **บันทึก docx เป็น pdf** จริง ๆ

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

เรียกโปรแกรม (`dotnet run`) แล้วตรวจสอบ `output.pdf` คุณควรเห็นรูปทรงที่ลอยถูกเรนเดอร์แบบอินไลน์ เหมือนเดิมใน Word  

## ขั้นตอนที่ 5: ตรวจสอบผลลัพธ์ – เช็คลิสต์สั้น ๆ

1. **ข้อความทั้งหมดปรากฏ** – ไม่มีย่อหน้าที่หายไป  
2. **รูปทรงที่ลอยอยู่ปรากฏตรงที่ควร** – ตอนนี้เป็นส่วนหนึ่งของการไหลของข้อความ  
3. **ขนาด PDF อยู่ในระดับที่สมเหตุสมผล** – การส่งออกเป็นแท็กอินไลน์มักลดขนาดไฟล์เมื่อเทียบกับสตรีมภาพแยก  

หากพบอะไรผิดพลาด ให้ตรวจสอบว่า DOCX ต้นฉบับจริง ๆ ใช้รูปทรง *ลอยอยู่* หรือไม่ (คลิกขวา → Layout → “In line with text” vs “Square/Behind text”) การเปลี่ยนรูปทรงเป็น “In line” ก่อนแปลงก็ใช้ได้เช่นกัน แต่ตัวเลือกแท็กอินไลน์ให้คุณควบคุมได้โดยไม่ต้องแก้ไฟล์ต้นฉบับ  

## กรณีขอบและคำถามที่พบบ่อย

### ถ้าเอกสารของฉันมี **SmartArt** หรือ **Charts** จะทำอย่างไร?

SmartArt และแผนภูมิจัดเป็นวัตถุการวาด `ExportFloatingShapesAsInlineTag` ยังห่อพวกมันด้วยแท็ก `<span>` แต่กราฟิกที่ซับซ้อนอาจสูญเสียความคมชัดบางส่วน ในกรณีนั้นให้พิจารณาแปลงแผนภูมิเป็นภาพก่อน (`Chart.ToImage()`) แล้วแทรกเป็นอินไลน์  

### ฉันสามารถ **รักษาลิงก์** และ **บุ๊กมาร์ก** ไว้ได้หรือไม่?

ทำได้แน่นอน ส่วนเหล่านี้ไม่ได้รับผลกระทบจากการตั้งค่า `ExportFloatingShapesAsInlineTag` Aspose.Words จะเก็บข้อมูลลิงก์และบุ๊กมาร์กทั้งหมดโดยอัตโนมัติ  

### ฉันจะ **เปลี่ยนการบีบอัด PDF** หรือ **ฝังฟอนต์** อย่างไร?

`PdfSaveOptions` มีคุณสมบัติเพิ่มเติมหลายอย่าง:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

ปรับแต่งค่าต่าง ๆ ตามความต้องการของระบบ downstream ของคุณ (เช่น การทำให้เป็น PDF/A)  

## ตัวอย่างทำงานเต็มรูปแบบ (พร้อมคัดลอก‑วาง)

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอกไปใส่ใน `Program.cs` แทนที่ `YOUR_DIRECTORY` ด้วยเส้นทางโฟลเดอร์จริง

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

เปิด `output.pdf`—คุณจะเห็นเลย์เอาต์เดิม พร้อมรูปทรงที่ลอยทุกอันถูกวางอย่างกระชับภายในข้อความ  

## สรุป

เราได้อธิบาย **วิธีบันทึก PDF** จากเอกสาร Word พร้อมให้รูปทรงที่ลอยกลายเป็นแท็ก `<span>` แบบอินไลน์ โดยการโหลด DOCX ตั้งค่า `PdfSaveOptions` แล้วเรียก `doc.Save` คุณสามารถ **บันทึก docx เป็น pdf** และ **แปลง word to pdf** อย่างมั่นใจโดยไม่มีปัญหาเลย์เอาต์  

ขั้นตอนต่อไป? ลองผสานวิธีนี้กับการทำให้เป็น **PDF/A** เพื่อการเก็บรักษาในระยะยาว หรือประมวลผลหลายไฟล์ DOCX ในโฟลเดอร์ด้วยลูป `foreach` ง่าย ๆ คุณอาจสนใจ **การเรนเดอร์แบบกำหนดเอง** (เช่น การเพิ่มลายน้ำ) โดยใช้ API `DocumentVisitor` ของ Aspose.Words  

มีคำถามเพิ่มเติมเกี่ยวกับการจัดการรูปทรง การฝังฟอนต์ หรือการปรับประสิทธิภาพ? แสดงความคิดเห็นด้านล่าง แล้วขอให้เขียนโค้ดอย่างสนุกสนาน!  

## สิ่งที่คุณควรเรียนต่อ

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโปรเจกต์ของคุณ

- [วิธีบันทึกเอกสารเป็น pdf ด้วย Aspose.Words สำหรับ Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [แปลง Word เป็น PDF ด้วย Aspose.Words สำหรับ Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – แปลง DOCX เป็น PDF ใน Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}