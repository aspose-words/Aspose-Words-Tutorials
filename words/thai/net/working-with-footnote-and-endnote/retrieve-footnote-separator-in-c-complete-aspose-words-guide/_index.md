---
category: general
date: 2026-08-07
description: ดึงตัวคั่นเชิงอรรถโดยใช้ Aspose.Words for .NET เรียนรู้วิธีการแยกตัวคั่นเชิงอรรถและเชิงอรรถท้าย
  ตรวจสอบประเภทโหนด และแก้ไขใน C#
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: th
lastmod: 2026-08-07
og_description: ดึงตัวคั่นเชิงอรรถด้วย Aspose.Words for .NET. คู่มือนี้แสดงวิธีการสกัดตัวคั่นเชิงอรรถและเชิงอรรถท้าย
  ตรวจสอบประเภทโหนดของพวกมัน และบันทึกการเปลี่ยนแปลง.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: ดึงตัวคั่นเชิงอรรถใน C# – บทแนะนำ Aspose.Words ทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: ดึงตัวคั่นเชิงอรรถใน C# – คู่มือ Aspose.Words ฉบับสมบูรณ์
url: /th/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ดึงตัวคั่นเชิงอรรถใน C# – คู่มือ Aspose.Words ฉบับสมบูรณ์

หากคุณต้องการ **ดึงตัวคั่นเชิงอรรถ** จากเอกสาร Word คำแนะนำนี้จะแสดงวิธีทำอย่างละเอียดด้วย Aspose.Words for .NET ไม่ว่าคุณจะกำลังสร้างบริการประมวลผลเอกสารหรือทำความสะอาดรูปแบบเชิงอรรถ คุณจะได้เห็นตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่งสกัดตัวคั่นเชิงอรรถและตัวคั่นอ้างอิงท้ายเอกสารออกมา

ในคู่มือนี้คุณจะได้เรียนรู้วิธีโหลดไฟล์ `.docx` เรียกใช้คุณสมบัติ `FootnoteSeparator` และ `EndnoteSeparator` ตรวจสอบอ็อบเจ็กต์ `Node` ที่คืนค่า และหากต้องการก็สามารถแทนที่เส้นตัวคั่นได้ ไม่ต้องอ้างอิงเอกสารภายนอก—ทุกอย่างที่คุณต้องการรวมอยู่ด้านล่างนี้

## ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานบน .NET Framework 4.7.2 ด้วย)
* Aspose.Words for .NET NuGet package (เวอร์ชัน 24.9 หรือใหม่กว่า)
* เอกสาร Word ที่มีเชิงอรรถและ/หรืออ้างอิงท้ายเอกสาร (เช่น `Footnotes.docx`)

คุณสามารถเพิ่มแพคเกจ Aspose.Words ด้วยคำสั่ง CLI ดังต่อไปนี้:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## ขั้นตอนที่ 1: ตั้งค่าโครงการและนำเข้า namespace

สร้างโปรเจกต์คอนโซลใหม่หรือเพิ่มโค้ดนี้ลงในโปรเจกต์ที่มีอยู่แล้ว คำสั่ง `using` ที่จำเป็นมีดังนี้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Namespace เหล่านี้ทำให้คุณเข้าถึงคลาส `Document` โครงสร้าง `Node` และ enumeration `NodeType` ที่จำเป็นสำหรับการ **ดึงตัวคั่นเชิงอรรถ**  

## ขั้นตอนที่ 2: โหลดเอกสารที่มีเชิงอรรถและอ้างอิงท้ายเอกสาร

การดำเนินการแรกในทุก workflow ของ Aspose.Words คือการโหลดไฟล์ต้นฉบับ แทนที่พาธตัวอย่างด้วยตำแหน่งที่ตั้งจริงของไฟล์ `.docx` ของคุณ

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

การโหลดไฟล์จะเตรียมต้นไม้โหนดภายใน ซึ่งเป็นสิ่งสำคัญสำหรับการ **ดึงตัวคั่นเชิงอรรถ** เนื่องจากโหนดตัวคั่นอยู่ภายในต้นไม้ดังกล่าว

## ขั้นตอนที่ 3: ดึงโหนดตัวคั่นเชิงอรรถ

ตอนนี้คุณสามารถ **ดึงตัวคั่นเชิงอรรถ** ได้โดยเข้าถึงคุณสมบัติ `FootnoteSeparator` ของอ็อบเจ็กต์ `Document` โหนดนี้เป็นเส้นที่แยกเชิงอรรถออกจากข้อความหลัก

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

`NodeType` จะเป็น `Paragraph` สำหรับเส้นตัวคั่นมาตรฐาน การรู้ประเภทของโหนดช่วยให้คุณตัดสินใจได้ว่าจะปรับเปลี่ยนตัวคั่นหรือแทนที่ทั้งหมดหรือไม่

## ขั้นตอนที่ 4: ดึงโหนดตัวคั่นอ้างอิงท้ายเอกสาร

ในทำนองเดียวกัน คุณสามารถ **ดึงตัวคั่นอ้างอิงท้ายเอกสาร** ได้โดยใช้คุณสมบัติ `EndnoteSeparator` โหนดนี้แยกอ้างอิงท้ายเอกสารออกจากเนื้อหาหลัก

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

โหนดตัวคั่นทั้งสองมักจะมี `NodeType` เท่ากัน (`Paragraph`) ในเอกสารส่วนใหญ่ แต่คุณสามารถปรับแต่งได้อย่างอิสระ

## ขั้นตอนที่ 5: ตรวจสอบหรือแก้ไขเนื้อหาตัวคั่น (ทางเลือก)

หากคุณต้องการเปลี่ยนลักษณะการแสดงผลของตัวคั่น—เช่นแทนที่เส้นขีดด้วยกฎบางเส้น—คุณสามารถแก้ไขโหนด `Paragraph` โดยตรง ตัวอย่างต่อไปนี้จะแทนที่ข้อความตัวคั่นเริ่มต้นด้วยสตริงที่กำหนดเอง

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

หลังจากแก้ไขโหนดแล้ว คุณสามารถบันทึกเอกสารเพื่อดูการเปลี่ยนแปลงใน Word

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล

เมื่อคุณรันโปรแกรมด้วยไฟล์ `Footnotes.docx` ดั้งเดิม ควรเห็นผลลัพธ์คล้ายกับนี้

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

หากคุณเปิด `Footnotes_Updated.docx` ใน Microsoft Word ตัวคั่นเชิงอรรถและอ้างอิงท้ายเอกสารจะปรากฏข้อความที่คุณใส่ไว้

## คำถามที่พบบ่อยและกรณีขอบ

**เอกสารไม่มีเชิงอรรถจะทำอย่างไร?**  
คุณสมบัติ `FootnoteSeparator` ยังคงคืนค่าโหนด `Paragraph` เนื่องจาก Word จะมีตัวคั่นสำรองอยู่เสมอ โหนดจะว่างเปล่า ดังนั้นคุณจึงสามารถเพิ่มเนื้อหาได้หรือปล่อยไว้ตามเดิมได้อย่างปลอดภัย

**สามารถดึงตัวคั่นสำหรับส่วน (section) เฉพาะได้หรือไม่?**  
ตัวคั่นเชิงอรรถและอ้างอิงท้ายเอกสารเป็นระดับเอกสารทั้งหมด ไม่ใช่ระดับส่วน หากต้องการควบคุมระดับส่วน คุณต้องทำงานกับ `Section.FootnoteOptions` และ `Section.EndnoteOptions` แทนโหนดตัวคั่นทั่วโลก

**ทำงานกับ .NET Core ได้หรือไม่?**  
ได้ Aspose.Words for .NET รองรับหลายแพลตฟอร์ม และโค้ดเดียวกันทำงานบน Windows, Linux และ macOS ด้วย .NET 6+

**คาดว่าจะได้ประเภทโหนดอะไร?**  
ทั้ง `FootnoteSeparator` และ `EndnoteSeparator` จะคืนค่าโหนด `Paragraph` (`NodeType.Paragraph`) หากคุณพบประเภทอื่น แสดงว่าเอกสารอาจเสียหายและควรโหลดใหม่หรือทำการตรวจสอบไฟล์ต้นฉบับ

## โค้ดเต็มสำหรับคัดลอก‑วางอย่างรวดเร็ว

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

คัดลอกโค้ดนี้ไปยังไฟล์ `Program.cs` ปรับพาธไฟล์ตามความต้องการ แล้วรัน `dotnet run` โปรแกรมจะแสดง workflow **ดึงตัวคั่นเชิงอรรถ** อย่างครบถ้วน ตั้งแต่การโหลดเอกสารจนถึงการบันทึกการเปลี่ยนแปลง

## สรุป

คุณได้เรียนรู้วิธี **ดึงตัวคั่นเชิงอรรถ** และ **ดึงตัวคั่นอ้างอิงท้ายเอกสาร** ด้วย Aspose.Words for .NET ตรวจสอบ `document node type` ของพวกมัน และหากต้องการก็สามารถแทนที่เนื้อหาได้ เทคนิคนี้ช่วยให้คุณอัตโนมัติรูปแบบเชิงอรรถ สร้างเส้นตัวคั่นแบบกำหนดเอง หรือทำการตรวจสอบโครงสร้างเอกสารในแอปพลิเคชัน C# ใด ๆ

ต่อไปคุณอาจสำรวจหัวข้อที่เกี่ยวข้อง เช่น **การสกัดเชิงอรรถใน C#** เพื่อดึงข้อความเชิงอรรถแต่ละรายการ หรือเรียนรู้วิธี **แก้ไขเครื่องหมายอ้างอิงเชิงอรรถ** ด้วย `FootnoteOptions` ทั้งสองแนวคิดต่อยอดจากพื้นฐานโหนด‑ทรีที่อธิบายไว้ที่นี่

ขอให้เขียนโค้ดสนุกสนานและอย่ากลัวที่จะทดลองสไตล์ตัวคั่นต่าง ๆ เพื่อให้สอดคล้องกับแบรนด์ของโครงการคุณ!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอน‑ต่อ‑ขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Working With Footnote And Endnote](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}