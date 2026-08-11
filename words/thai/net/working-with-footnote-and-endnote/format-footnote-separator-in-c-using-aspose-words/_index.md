---
category: general
date: 2026-08-10
description: จัดรูปแบบตัวคั่นเชิงอรรถใน C# ด้วย Aspose.Words เพื่อปรับแต่งเส้นเชิงอรรถและเชิงอรรถท้าย
  เรียนรู้การจัดรูปแบบเชิงอรรถใน C# ภายในไม่กี่นาที.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: th
lastmod: 2026-08-10
og_description: จัดรูปแบบตัวคั่นเชิงอรรถใน C# ด้วย Aspose.Words. ทำตามบทแนะนำนี้เพื่อจัดสไตล์ตัวคั่นเชิงอรรถและเชิงอรรถท้ายอย่างรวดเร็วและเชื่อถือได้.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: จัดรูปแบบตัวคั่นเชิงอรรถใน C# – คู่มือ Aspose.Words ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: จัดรูปแบบตัวคั่นหมายเหตุท้ายบรรทัดใน C# ด้วย Aspose.Words
url: /th/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# จัดรูปแบบตัวคั่นเชิงอรรถใน C# ด้วย Aspose.Words

หากคุณต้องการ **จัดรูปแบบตัวคั่นเชิงอรรถ** ในเอกสาร Word คำแนะนำนี้จะแสดงวิธีทำด้วย Aspose.Words for .NET คุณจะได้เห็นตัวอย่างที่สมบูรณ์และสามารถรันได้ซึ่งเปลี่ยนการจัดแนวและสีของย่อหน้าตัวคั่น และคุณจะได้เรียนรู้วิธีใช้เทคนิคเดียวกันกับตัวคั่นของบันทึกท้าย

บทเรียนนี้ครอบคลุมทุกขั้นตอน—from การโหลดไฟล์ต้นทางจนถึงการบันทึกเอกสารที่แก้ไขแล้ว—เพื่อให้คุณสามารถคัดลอก‑วางโค้ดลงในโปรเจกต์ของคุณเองได้โดยไม่ต้องค้นคว้าเพิ่มเติม

## สิ่งที่คุณต้องมี

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+ ได้เช่นกัน)
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (รุ่นทดลองฟรีใช้สำหรับการประเมินผล)
* ไฟล์ Word ที่มีอย่างน้อยหนึ่งเชิงอรรถหรือบันทึกท้าย (เช่น `Footnotes.docx`)
* Visual Studio 2022 หรือ IDE C# ใด ๆ ที่คุณชื่นชอบ

การมีสิ่งเหล่านี้พร้อมจะทำให้คุณมุ่งเน้นที่ตรรกะ **การจัดรูปแบบเชิงอรรถใน C#** แทนการตั้งค่าสภาพแวดล้อม

## ขั้นตอนที่ 1: โหลดเอกสารที่มีเชิงอรรถและบันทึกท้าย

การดำเนินการแรกคือการสร้างอ็อบเจกต์ `Document` ที่ชี้ไปยังไฟล์ต้นทางของคุณ Aspose.Words จะอ่านแพ็กเกจ DOCX ทั้งหมดเข้าสู่หน่วยความจำ ทำให้คุณเข้าถึงโหนดเชิงอรรถและบันทึกท้ายได้อย่างเต็มที่

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*ทำไมเรื่องนี้สำคัญ*: การโหลดเอกสารเป็นเงื่อนไขเบื้องต้นสำหรับการแก้ไขใด ๆ หากเส้นทางไฟล์ไม่ถูกต้อง Aspose.Words จะโยน `FileNotFoundException` ดังนั้นให้ตรวจสอบเส้นทางก่อนดำเนินการต่อ

## ขั้นตอนที่ 2: ดึงโหนดตัวคั่นและตัวคั่นต่อเนื่อง

ตัวคั่นของเชิงอรรถและบันทึกท้ายถูกจัดเก็บเป็นโหนดพิเศษภายในคอลเลกชัน `Footnotes` และ `Endnotes` แต่ละคอลเลกชันเปิดเผยคุณสมบัติ `Separator` และ `ContinuationSeparator` ที่คืนค่าอ้างอิง `Node`

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*ทำไมเรื่องนี้สำคัญ*: โหนด `Separator` แทนบรรทัดที่แยกข้อความหลักออกจากบล็อกเชิงอรรถโดยภาพ การได้อ้างอิงนี้ทำให้คุณสามารถแก้ไขรูปแบบย่อหน้า ฟอนต์ หรือแม้แต่แทนที่โหนดทั้งหมดได้

## ขั้นตอนที่ 3: เปลี่ยนสไตล์การแสดงผลของตัวคั่นเชิงอรรถ

ในเอกสาร Word ส่วนใหญ่ ตัวคั่นเป็นย่อหน้าหนึ่งบรรทัดที่มีเครื่องหมายขีดหรือดอกจัน โค้ดด้านล่างตรวจสอบว่าตัวคั่นเป็น `Paragraph` หรือไม่ และถ้าใช่ จะจัดกึ่งกลางและเปลี่ยนสีข้อความเป็นสีเทา

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### การจัดรูปแบบตัวคั่นต่อเนื่อง (ไม่บังคับ)

ตัวคั่นต่อเนื่องปรากฏเมื่อเชิงอรรถขยายหลายหน้า คุณสามารถจัดรูปแบบได้เช่นเดียวกัน:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*ทำไมเรื่องนี้สำคัญ*: การจัดแนวตัวคั่นช่วยเพิ่มความอ่านง่าย และการเปลี่ยนสีทำให้มันแตกต่างจากข้อความย่อปกติ คุณสามารถเปลี่ยน `ParagraphAlignment.Center` เป็น `Left` หรือ `Right` เพื่อให้สอดคล้องกับแนวทางการออกแบบเอกสารของคุณ

## ขั้นตอนที่ 4: บันทึกเอกสารที่แก้ไขแล้ว

หลังจากปรับสไตล์ตามต้องการ ให้เขียนเอกสารกลับไปยังดิสก์ คุณสามารถเขียนทับไฟล์เดิมหรือสร้างเวอร์ชันใหม่ได้

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

เมื่อคุณเปิด `Footnotes_Styled.docx` ใน Microsoft Word ตัวคั่นเชิงอรรถจะปรากฏกึ่งกลางและสีเทาตามที่โค้ดกำหนด

## การปรับใช้ขั้นสูง

### การจัดรูปแบบตัวคั่นของบันทึกท้าย

หากเอกสารของคุณใช้บันทึกท้ายด้วย คุณสามารถใช้ตรรกะเดียวกันกับคอลเลกชัน `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### ใช้สตริงกำหนดเองสำหรับตัวคั่น

บางครั้งคุณอาจต้องการให้ตัวคั่นเป็นชุดดอกจัน (`***`) แทน ให้แทนที่รันที่มีอยู่ด้วยรันใหม่:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### จัดการเอกสารที่ไม่มีโหนดตัวคั่น

กรณีขอบที่หายากคือเอกสารที่ไม่มีโหนดตัวคั่น (เช่น ผู้เขียนลบออก) ในสถานการณ์นั้น `document.Footnotes.Separator` จะคืนค่า `null` ควรตรวจสอบก่อนใช้งาน:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| ข้อผิดพลาด | สาเหตุ | วิธีแก้ |
|------------|--------|----------|
| **Separator ไม่ใช่ `Paragraph`** | เทมเพลต Word บางอย่างใช้ `Table` หรือ `Shape` เป็นตัวคั่น | ตรวจสอบประเภทของโหนดด้วย `is Paragraph` ก่อนทำการแคสท์ |
| **`Runs` collection is empty** | ตัวคั่นอาจเป็นย่อหน้าว่าง | ตรวจสอบ `Runs.Count > 0` ก่อนเข้าถึง `Runs[0]` |
| **License not applied** | หากไม่มีลิขสิทธิ์ Aspose.Words จะใส่ลายน้ำและอาจจำกัดการใช้ API | เรียก `License license = new License(); license.SetLicense("Aspose.Words.lic");` ที่จุดเริ่มต้นของโปรแกรม |
| **Saving to a read‑only folder** | เมธอด `Save` จะโยน `UnauthorizedAccessException` | ตรวจสอบให้แน่ใจว่าไดเรกทอรีเป้าหมายมีสิทธิ์การเขียน |

การจัดการกับปัญหาเหล่านี้ตั้งแต่ต้นจะช่วยป้องกันข้อยกเว้นในขณะรันไทม์และทำให้ประสบการณ์ **การแก้ไขตัวคั่นเชิงอรรถ** ราบรื่นขึ้น

## ตัวอย่างสมบูรณ์ที่สามารถรันได้

ด้านล่างเป็นแอปพลิเคชันคอนโซลที่รวมทุกขั้นตอนที่อธิบายไว้ข้างต้น คัดลอกโค้ดไปยังโปรเจกต์คอนโซล .NET ใหม่ แก้ไขเส้นทางไฟล์ แล้วรันมัน

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง**  

เมื่อคุณเปิด `Footnotes_Styled.docx`:

* เส้นตัวคั่นเชิงอรรถจะอยู่กึ่งกลางใต้ข้อความหลัก
* สีของมันจะแสดงเป็นสีเทาอ่อน ทำให้แตกต่างจากข้อความปกติ
* หากเอกสารมีบันทึกท้าย ตัวคั่นของบันทึกท้ายก็จะถูกจัดกึ่งกลางและสีเทา (หรือสีเทาเข้ม)

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดที่ทำงานได้เต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบต่าง ๆ ในโปรเจกต์ของคุณเอง

- [การประมวลผลคำด้วยเชิงอรรถและบันทึกท้าย](/words/english/net/working-with-footnote-and-endnote/)
- [ตั้งตำแหน่งเชิงอรรถและบันทึกท้าย](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [ทำงานกับเชิงอรรถและบันทึกท้าย](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}