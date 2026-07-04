---
category: general
date: 2026-04-21
description: บันทึก LaTeX คณิตศาสตร์ของ Office อย่างรวดเร็วด้วย Aspose.Words – เรียนรู้วิธีบันทึกข้อความธรรมดาของ
  Word และส่งออกสมการ Word เป็น LaTeX ในครั้งเดียว.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: th
og_description: บันทึก LaTeX คณิตศาสตร์ของ Office ทันที; เรียนรู้การส่งออกสมการ Word
  เป็น LaTeX และแปลง LaTeX คณิตศาสตร์ของ Word ด้วย Aspose.Words ใน C#
og_title: บันทึก Office Math LaTeX – ส่งออกสมการ Word ไปยัง LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: บันทึก Office Math LaTeX – ส่งออกสมการ Word เป็น LaTeX ใน C#
url: /th/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# บันทึก Office Math LaTeX – ส่งออกสมการ Word ไปเป็น LaTeX ด้วย Aspose.Words

เคยต้องการ **save office math latex** จากไฟล์ `.docx` แต่ไม่แน่ใจว่าจะเริ่มอย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว และข่าวดีคือวิธีแก้ง่ายมาก ในคู่มือนี้เราจะอธิบายขั้นตอนที่แน่นอนเพื่อส่งออกสมการ Word เป็น latex (และแม้กระทั่ง MathML) โดยใช้ Aspose.Words สำหรับ .NET พร้อมกับแสดงวิธี **save word plain text** ควบคู่กับสมการ

เราจะครอบคลุมทุกสิ่งที่คุณอาจสงสัย: ทำไมคุณจึงเลือก LaTeX แทนรูปแบบอื่น ๆ, วิธีกำหนดค่า `TxtSaveOptions`, และวิธีทำเมื่อคุณต้องการ **convert word math latex** ไปเป็นรูปแบบอื่น ๆ เมื่อเสร็จสิ้นคุณจะมีโค้ดสั้นที่สามารถรันได้ซึ่งรับไฟล์ Word ที่มีวัตถุ Office Math แล้วสร้างไฟล์ `.txt` สะอาดที่มีสมการ LaTeX (หรือ MathML) ไม่มีเครื่องมือภายนอก ไม่มีการคัดลอก‑วางด้วยมือ—เพียงโค้ด C# สะอาดที่คุณสามารถใส่ลงในโปรเจกต์ใดก็ได้

## Prerequisites

- **Aspose.Words for .NET** (v23.10 หรือใหม่กว่า) แพ็คเกจ NuGet คือ `Aspose.Words`
- สภาพแวดล้อมการพัฒนา .NET (Visual Studio, Rider หรือ VS Code พร้อมส่วนขยาย C#)
- ไฟล์ Word (`.docx`) ที่มีอย่างน้อยหนึ่งสมการที่สร้างด้วย Office Math editor
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#—ไม่ต้องซับซ้อน เพียงแค่ `using` statements ปกติ

ถ้าคุณมีทั้งหมดข้างต้นแล้ว เยี่ยม—มาเริ่มกันเลย

## Step 1 – Set up **save office math latex** options

สิ่งแรกที่คุณต้องทำคือบอก Aspose.Words ว่าต้องการให้เนื้อหาคณิตศาสตร์แสดงผลอย่างไร คลาส `TxtSaveOptions` มีคุณสมบัติ `OfficeMathExportMode` ที่รับค่าได้สามค่า: `LaTeX`, `MathML`, หรือ `Text` สำหรับเป้าหมายหลักของเราเราจะเลือก `LaTeX`

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**ทำไมเรื่องนี้ถึงสำคัญ:** เมื่อคุณตั้งค่า `OfficeMathExportMode` เป็น `LaTeX` แต่ละสมการจะถูกแปลงเป็นซอร์ส LaTeX ดิบ ซึ่งซอร์สนี้สามารถคอมไพล์ด้วยเครื่องมือ LaTeX ใดก็ได้ ให้ผลลัพธ์การจัดรูปแบบที่สมบูรณ์แบบโดยไม่ต้องพิมพ์สูตรใหม่

> **Pro tip:** หากคุณต้องการ **convert word equations mathml** เพียงสลับค่า enum เป็น `OfficeMathExportMode.MathML` โค้ดส่วนอื่นยังคงเหมือนเดิม

## Step 2 – Load the Word document (the **save word plain text** scenario)

ต่อไปเราจะโหลดไฟล์ `.docx` ต้นฉบับ ขั้นตอนนี้เหมือนกันไม่ว่าคุณจะสนใจแค่การสกัดข้อความธรรมดาหรือยังต้องการสมการในรูป LaTeX ด้วย

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**เกิดอะไรขึ้นที่นี่?** ตัวสร้าง `Document` จะอ่านไฟล์เข้าสู่หน่วยความจำ การตรวจสอบอย่างรวดเร็วด้วย `GetChildNodes` ช่วยให้คุณจับกรณีขอบที่พบบ่อย—การพยายามส่งออก LaTeX จากไฟล์ที่ไม่มีสมการเลย เป็นการป้องกันเล็ก ๆ ที่ช่วยหลีกเลี่ยงผลลัพธ์ว่างเปล่าที่ทำให้สับสนในภายหลัง

## Step 3 – **save office math latex** to a plain‑text file

ตอนนี้เราจะเขียนไฟล์จริง `Save` จะเคารพ `TxtSaveOptions` ที่กำหนดไว้ก่อนหน้า ดังนั้นไฟล์ `.txt` ที่ได้จะมีทั้งข้อความปกติและส่วน LaTeX ของแต่ละสมการ

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

เมื่อคุณเปิด `Equations.txt` คุณจะเห็นประมาณนี้:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

บล็อก LaTeX จะถูกห่อด้วย `\begin{equation}` … `\end{equation}` อัตโนมัติ ทำให้พร้อมนำไปใส่ในเอกสาร LaTeX ใดก็ได้

## Step 4 – Alternative: **convert word equations mathml** instead of LaTeX

หากสายงานต่อไปของคุณต้องการ MathML (เช่น หน้าเว็บที่เรนเดอร์สมการด้วย MathJax) เพียงเปลี่ยนโหมดการส่งออก:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

ผลลัพธ์จะมีแท็ก XML‑style MathML เช่น:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

นี่คือวิธีเร็ว ๆ ที่จะ **convert word equations mathml** โดยไม่ต้องเขียนพาร์เซอร์ของคุณเอง

## Step 5 – Bonus: **save word plain text** while keeping equations separate

บางครั้งคุณต้องการเวอร์ชันข้อความสะอาดของเอกสาร *โดยไม่มี* LaTeX หรือ MathML ฝังอยู่ คุณทำได้โดยสลับโหมดการส่งออกเป็น `Text` แล้วทำการบันทึกครั้งที่สอง:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

ตอนนี้คุณจะมีไฟล์สามไฟล์อยู่เคียงข้างกัน:

| File                         | Contents                               |
|------------------------------|----------------------------------------|
| `Equations.txt`              | Plain text **+** LaTeX equations       |
| `EquationsMathML.txt`        | Plain text **+** MathML equations       |
| `PlainDocument.txt`          | Pure text, equations stripped out      |

รูปแบบนี้มีประโยชน์เมื่อคุณต้องการป้อนข้อความธรรมดาเข้าสู่ดัชนีการค้นหา แต่ยังคงรักษาสมการต้นฉบับไว้สำหรับการตีพิมพ์ทางวิชาการ

## Full Working Example (Copy‑Paste Ready)

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคอมไพล์และรันได้ทันที แสดงการทำ **save office math latex**, **export word equations latex**, **convert word math latex**, และ **save word plain text**—ทั้งหมดในสคริปต์เดียวที่เรียบร้อย

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** หลังจากรัน คุณจะพบไฟล์ข้อความสามไฟล์ใน `C:\MyDocs` เปิด `Equations.txt` จะเห็นบล็อก LaTeX; `EquationsMathML.txt` จะมี MathML; `PlainDocument.txt` จะไม่มีเครื่องหมายสมการใด ๆ

## Common Questions & Edge Cases

- **What if I only need LaTeX for a subset of equations?**  
  Use the `OfficeMath` node API to iterate over each equation, export it manually with `MathConverter`, and replace the placeholder text where you want. That approach gives you fine‑grained control but adds a few extra lines of code.

- **Does this work with .NET Core / .NET 5+?**  
  Absolutely. Aspose.Words is cross‑platform, so the same code runs on Windows, Linux, and macOS as long as the runtime version matches the library’s requirements.

- **Can I change the LaTeX wrapper (`\begin{equation}`) to something else?**  
  Yes. Set `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` and then modify `txtOptions.MathExportSettings` (available in newer releases) to customize delimiters.

- **Performance concerns for huge documents?**  
  The library streams the output, so memory usage stays modest. However

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}