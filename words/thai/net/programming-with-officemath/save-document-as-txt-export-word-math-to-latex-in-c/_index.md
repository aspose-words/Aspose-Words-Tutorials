---
category: general
date: 2026-04-24
description: บันทึกเอกสารเป็นไฟล์ txt และแปลง Word เป็น LaTeX ด้วย Aspose.Words เรียนรู้วิธีส่งออกสมการคณิตศาสตร์ใน
  Word ไปยัง LaTeX อย่างรวดเร็ว
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: th
og_description: บันทึกเอกสารเป็น txt และแปลงสมการ Word เป็น LaTeX ด้วย C# คู่มือขั้นตอนเต็มพร้อมโค้ด
og_title: บันทึกเอกสารเป็น TXT – ส่งออกสูตร Word ไปยัง LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: บันทึกเอกสารเป็น TXT – ส่งออก Math ของ Word ไปเป็น LaTeX ด้วย C#
url: /th/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# บันทึกเอกสารเป็น TXT – ส่งออกสมการ Word เป็น LaTeX ใน C#

เคยต้อง **save document as txt** พร้อมกับรักษาสมการสวย ๆ ของคุณไว้หรือไม่? คุณไม่ได้เป็นคนเดียวที่เจอปัญหานี้ คำสั่ง “Save as plain text” ของ Word จะทิ้ง Office Math ไปเลย ทำให้เหลือแค่ข้อความที่อ่านไม่ออก ถ้าคุณสามารถเก็บสมการเหล่านั้นไว้ได้ แต่ในรูปแบบ LaTeX ที่สะอาดตา จะเป็นอย่างไร?

ในบทแนะนำนี้เราจะพาคุณผ่านขั้นตอนที่แม่นยำเพื่อ **convert Word to LaTeX**‑ready text ด้วย Aspose.Words for .NET. เมื่อเสร็จสิ้นคุณจะได้ไฟล์ `.txt` ที่ทุกสมการถูกแทนด้วย markup LaTeX ที่ถูกต้อง พร้อมนำไปวางในเอกสารหรือไฟล์ markdown ได้ทันที ไม่ต้องใช้ตัวแปลงภายนอก ไม่ต้องคัดลอก‑วางด้วยตนเอง—แค่ไม่กี่บรรทัดของ C# เท่านั้น

## สิ่งที่คุณจะได้เรียนรู้

- วิธีโหลดไฟล์ `.docx` ด้วย Aspose.Words
- การกำหนดค่า `TxtSaveOptions` เพื่อให้ Office Math ถูกส่งออกเป็น LaTeX
- การบันทึกผลลัพธ์เป็นไฟล์ข้อความธรรมดาที่คุณสามารถเปิดในโปรแกรมแก้ไขใดก็ได้
- การจัดการกรณีขอบสำหรับสมการแบบในบรรทัดและแบบแสดงผล, พร้อมเคล็ดลับสั้น ๆ สำหรับการประมวลผลหลายเอกสารเป็นชุด

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ทำงานกับ .NET Framework 4.6+ ด้วย)
- แพคเกจ NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- เอกสาร Word ที่มีสมการอย่างน้อยหนึ่งสมการ (อ็อบเจ็กต์ Office Math)

---

## Step 1: Install Aspose.Words and Set Up the Project

ก่อนอื่นให้เพิ่มไลบรารีนี้เข้าไปในโปรเจกต์ของคุณ เปิดเทอร์มินัลในโฟลเดอร์โซลูชันและรันคำสั่ง:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** หากคุณใช้ Visual Studio, UI ของ NuGet Package Manager ทำงานได้เช่นกัน—ค้นหา “Aspose.Words” แล้วคลิก Install

ต่อไปสร้างแอปคอนโซลใหม่ (หรือวางโค้ดนี้ลงในแอปที่มีอยู่แล้ว) `using` directives ที่คุณต้องการมีดังนี้:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

ส่วนนี้ทำให้คลาส `Document` และชนิด `TxtSaveOptions` อยู่ในสโคปของคุณ

## Step 2: Load the Source Document

เราต้องชี้ให้ Aspose.Words รู้ตำแหน่งไฟล์ Word ที่มีสมการ แทนที่ `YOUR_DIRECTORY/input.docx` ด้วยพาธจริงบนเครื่องของคุณ

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Why this matters:** การโหลดเอกสารทำให้ Aspose.Words เข้าถึงอ็อบเจ็กต์ Office Math ภายในได้เต็มที่ ซึ่งโดยปกติจะมองไม่เห็นจากตัวส่งออกข้อความธรรมดา

## Step 3: Configure TxtSaveOptions for LaTeX Export

ความมหัศจรรย์เกิดขึ้นในอ็อบเจ็กต์ `TxtSaveOptions` โดยการตั้งค่า `OfficeMathExportMode` เป็น `LaTeX` ทุกสมการจะถูกแปลงเป็นรูปแบบ LaTeX ของมัน

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **What if you need MathML instead?** เปลี่ยน `OfficeMathExportMode` เป็น `MathML` API เดียวกันนี้รองรับหลายรูปแบบการส่งออก

## Step 4: Save the Document as Plain‑Text

ตอนนี้เราจะเขียนไฟล์ออกมา ไฟล์ `Math.txt` ที่ได้จะมีข้อความธรรมดาพร้อมส่วน LaTeX ของแต่ละสมการ

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

การรันโปรแกรมจะสร้างไฟล์ที่มีลักษณะประมาณนี้:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

สังเกตว่าการใช้สมการในบรรทัดใช้ `$…$` ส่วนสมการแสดงผลจะอยู่ใน `\[` และ `\]` นี่คือมาตรฐานของ LaTeX และ Aspose.Words ทำให้โดยอัตโนมัติ

## Step 5: Verify the Output (Optional)

หากต้องการตรวจสอบว่า LaTeX ถูกต้องหรือไม่ คุณสามารถส่งไฟล์ `.txt` ไปยังคอมไพเลอร์ LaTeX เช่น `pdflatex` หรือเรนเดอร์ออนไลน์อย่าง Overleaf ข้อความควรคอมไพล์โดยไม่มีข้อผิดพลาดและสมการจะแสดงผลเหมือนใน Word

```bash
pdflatex Math.txt
```

ถ้าคุณเจอ “Undefined control sequence” ให้ตรวจสอบว่ามีแพคเกจ LaTeX ที่ต้องการ (เช่น `amsmath`) ถูกใส่ไว้ใน preamble เมื่อคุณฝังข้อความนี้ลงในเอกสาร LaTeX ขนาดใหญ่

## Handling Common Variations

### Converting Multiple Files in a Folder

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Dealing with Inline vs. Display Equations

Aspose.Words จะตรวจจับประเภทสมการโดยอัตโนมัติตามการจัดวางใน Word หากคุณต้องการบังคับสไตล์เฉพาะ คุณสามารถทำการ post‑process ผลลัพธ์ได้ดังนี้:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Exporting to Other Formats

หาก LaTeX ไม่ใช่เป้าหมายของคุณ เพียงสลับโหมดการส่งออก:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

หรือใช้ `HtmlSaveOptions` หากคุณต้องการ MathML ฝังอยู่ใน HTML

---

## Full Working Example

ด้านล่างเป็นโปรแกรมที่สมบูรณ์พร้อมรัน คัดลอก‑วางลงใน `Program.cs` ของโปรเจกต์คอนโซล .NET

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

รันโปรแกรม (`dotnet run`), เปิด `Math.txt` แล้วคุณจะเห็นเนื้อหา Word ของคุณพร้อมสมการ LaTeX ที่คงอยู่อย่างครบถ้วน

---

## Frequently Asked Questions

**Q: Does this work with older .doc files?**  
A: ใช่—Aspose.Words สามารถเปิดไฟล์ `.doc` เก่าได้ แต่สมการที่ซับซ้อนอาจถูกเก็บเป็นรูปภาพ ในกรณีนั้นตัวส่งออกจะเปลี่ยนเป็นคอมเมนต์ placeholder

**Q: What if an equation contains custom symbols?**  
A: Aspose.Words จะแมปสัญลักษณ์ Office Math ส่วนใหญ่เป็นคำสั่ง LaTeX มาตรฐาน สำหรับสัญลักษณ์ที่กำหนดเองอย่างแท้จริงคุณอาจต้องแก้ไข LaTeX ที่สร้างขึ้นด้วยตนเอง

**Q: Is the output UTF‑8 encoded?**  
A: โดยค่าเริ่มต้น `TxtSaveOptions` จะเขียนเป็น UTF‑8 ซึ่งปลอดภัยสำหรับหลายภาษาและสัญลักษณ์

---

## Conclusion

ตอนนี้คุณรู้วิธี **save document as txt** พร้อมรักษาสมการทุกสมการเป็น LaTeX ที่สะอาดตา วิธีนี้ทำให้คุณ **convert Word to LaTeX** ได้โดยไม่ต้องพึ่งเครื่องมือของบุคคลที่สาม และสามารถขยายจากไฟล์เดียวไปจนถึงโฟลเดอร์ทั้งหมดได้ ต่อไปคุณอาจสำรวจ **convert word equations to LaTeX** สำหรับการประมวลผลเป็นชุด, หรือเจาะลึก **export word math latex** สำหรับ pipeline HTML หรือ Markdown

ลองทดลองเปลี่ยน `OfficeMathExportMode` เป็น MathML, ปรับการจัดการ line‑break, หรือรวมสคริปต์นี้เข้าใน workflow การสร้างเอกสารที่ใหญ่ขึ้นได้เลย Happy coding, และขอให้สมการของคุณแสดงผลอย่างสมบูรณ์เสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}