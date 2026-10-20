---
category: general
date: 2026-03-25
description: สร้าง callback คำเตือนเพื่อโหลดเอกสาร Word และตรวจจับฟอนต์ที่หายไป เรียนรู้วิธีกำหนดค่าการตั้งค่าฟอนต์ใน
  Aspose.Words สำหรับ .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: th
og_description: สร้างการเรียกคืนคำเตือนเพื่อโหลดเอกสาร Word พร้อมตรวจจับฟอนต์ที่หายไป
  คู่มือนี้แสดงวิธีการกำหนดค่าการตั้งค่าแบบอักษรใน Aspose.Words.
og_title: สร้างคอลแบ็กเตือน – โหลดเอกสาร Word และตรวจจับฟอนต์ที่หายไป
tags:
- Aspose.Words
- C#
- Font handling
title: สร้างคอลแบ็กเตือนสำหรับการโหลดเอกสาร Word – คู่มือฉบับสมบูรณ์
url: /th/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างการแจ้งเตือน callback – โหลดเอกสาร Word และตรวจจับฟอนต์ที่หายไป

เคยต้อง **สร้าง warning callback** ขณะโหลดเอกสาร Word แล้วสงสัยว่าทำไมฟอนต์บางตัวถึงหายไปหรือไม่? คุณไม่ได้เป็นคนเดียว ในแอปพลิเคชันระดับองค์กรหลายแห่ง ฟอนต์ที่หายไปทำให้การจัดหน้าเสียหาย และหากไม่มี callback ที่เหมาะสม คุณอาจไม่สังเกตปัญหาเลย  

ข่าวดีคืออะไร? ด้วย Aspose.Words for .NET คุณสามารถ **โหลดเอกสาร Word**, **ตรวจจับฟอนต์ที่หายไป**, และ **กำหนดค่า font settings** ทั้งหมดในไม่กี่บรรทัดของโค้ดที่เรียบร้อย ในบทแนะนำนี้เราจะเดินผ่านตัวอย่างที่ทำงานได้เต็มรูปแบบ, อธิบายว่าทำไมแต่ละส่วนจึงสำคัญ, และแสดงวิธีตรวจสอบว่า warning callback ทำงานตามที่คาดหวังหรือไม่

> **สิ่งที่คุณจะได้เรียนรู้**  
> * โปรแกรม C# เต็มรูปแบบที่โหลดไฟล์ DOCX, รายงานการแทนที่ฟอนต์ใด ๆ, และให้คุณปรับแต่งเส้นทางการค้นหาฟอนต์  
> * ความเข้าใจเกี่ยวกับคลาส `FontSettings`, `LoadOptions`, และ `IWarningCallback`  
> * เคล็ดลับสำหรับการจัดการกรณีขอบเช่นฟอนต์ที่ฝังอยู่หรือโฟลเดอร์ฟอนต์ระดับระบบ

---

## Prerequisites

- .NET 6+ (หรือ .NET Framework 4.7.2+) พร้อมคอมไพเลอร์ C#  
- NuGet package ของ Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- ตัวอย่างไฟล์ Word (`input.docx`) ที่ใช้ฟอนต์อย่างน้อยหนึ่งตัวที่ไม่ได้ติดตั้งบนเครื่อง (เช่น *Calibri Light* บนคอนเทนเนอร์ Windows ขั้นต่ำ)  
- ความคุ้นเคยพื้นฐานกับแอปคอนโซล C#

ไม่มีไลบรารีเพิ่มเติมที่จำเป็น; ทุกอย่างอยู่ภายใน Aspose.Words

---

## Step 1: Create warning callback to detect missing fonts

ส่วน **หลัก** ของปริศนานี้คือคลาสที่ implements `IWarningCallback`. Aspose.Words จะเรียก callback นี้ทุกครั้งที่พบสถานการณ์ที่ต้องแจ้งเตือน – การแทนที่ฟอนต์เป็นกรณีที่พบบ่อยที่สุด

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**ทำไมเรื่องนี้ถึงสำคัญ** – หากไม่มี callback คุณจะต้องคัดกรองบันทึกหลังจากที่เหตุการณ์เกิดขึ้นแล้ว การจัดการคำเตือนแบบเรียลไทม์ทำให้คุณสามารถตัดสินใจได้ว่าจะยกเลิกการโหลด, แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรอง, หรือเพียงแค่บันทึกปัญหาเพื่อทบทวนในภายหลัง

---

## Step 2: Configure FontSettings for custom font handling

ก่อนที่เราจะโหลดเอกสารจริง เราอาจต้องบอก Aspose.Words ว่าจะค้นหาฟอนต์ที่ไม่มีในระบบที่ไหน `FontSettings` คือคำตอบ

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**ทำไมเรื่องนี้ถึงสำคัญ** – การชี้ Aspose.Words ไปยังโฟลเดอร์ที่มีฟอนต์ที่หายไปมักจะทำให้หลีกเลี่ยงการแทนที่ได้ทั้งหมด หากทำไม่ได้ การตั้งค่าเริ่มต้นที่เหมาะสม (เช่น *Arial*) จะทำให้เอกสารยังอ่านได้

---

## Step 3: Load Word document with the configured warning callback

ตอนนี้เราจะเชื่อมทุกอย่างเข้าด้วยกัน: สร้าง `LoadOptions`, ใส่ `FontSettings` และ `FontWarningHandler` ของเรา, แล้วโหลดเอกสาร

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**ทำไมเรื่องนี้ถึงสำคัญ** – `LoadOptions` เป็นจุดเดียวที่คุณกำหนด *วิธี* ที่เอกสารจะถูกอ่าน การให้ทั้งการตั้งค่าฟอนต์และ warning callback พร้อมกันทำให้ฟอนต์ที่หายไปถูกค้นหาในตำแหน่งที่ถูกต้อง **และ** รายงานทันที

---

## Step 4: Verify the output – what should you see?

เรียกโปรแกรมจากคอนโซล หาก `input.docx` ใช้ฟอนต์ที่ไม่ได้ติดตั้งและยังไม่ได้อยู่ใน `C:\SharedFonts` คุณจะเห็นข้อความประมาณนี้:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

หากฟอนต์ทั้งหมดพร้อมใช้งาน บรรทัดคำเตือนจะไม่ปรากฏเลย การตอบสนองแบบทันทีนี้มีคุณค่าอย่างยิ่งในสายงานประมวลผลเอกสารอัตโนมัติที่การแทนที่ฟอนต์โดยเงียบอาจทำลายแนวทางแบรนด์

---

## Step 5: Common pitfalls and best‑practice tips

| Pitfall | How to avoid it |
|---------|-----------------|
| **Forgot to reference `Aspose.Words.Fonts`** | ตรวจสอบว่ามี `using Aspose.Words.Fonts;` ที่ส่วนหัวของไฟล์; มิฉะนั้นคอมไพเลอร์จะบอกว่าไม่มีประเภทที่ต้องการ |
| **Font folder path is wrong** | ตรวจสอบเส้นทางอีกครั้งและตั้งค่า `recursive: true` หากมีโฟลเดอร์ย่อย ใช้ `Path.GetFullPath` เพื่อดีบัก |
| **Multiple warning callbacks** | Aspose.Words จะรับเฉพาะ `WarningCallback` ตัวสุดท้ายที่กำหนดไว้เท่านั้น ให้ใช้ handler ตัวเดียวที่สามารถส่งต่อ (delegate) หากต้องการตรรกะที่ซับซ้อนกว่า |
| **Running on a server without UI** | การเขียนลงคอนโซลก็พอ, แต่สำหรับเว็บแอปอาจต้องบันทึกลงไฟล์หรือระบบมอนิเตอร์แทน `Console.WriteLine` |
| **Large documents cause performance hit** | ใช้ `FontSettings` ตัวเดียวซ้ำหลายครั้ง; การสร้างใหม่ทุกครั้งอาจทำให้ประสิทธิภาพลดลง |

**Pro tip:** หากต้องการ *เก็บ* คำเตือนเพื่อนำไปวิเคราะห์ต่อ, ให้เก็บไว้ใน `List<string>` ภายใน handler แทนการพิมพ์ออกโดยตรง

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

จากนั้นคุณสามารถตรวจสอบ `handler.Messages` หลังจากโหลดเอกสารเสร็จ

---

## Step 6: Extending the solution – what if I need to embed a fallback font?

บางครั้งคุณอาจต้องการให้ฟอนต์ที่หายไปถูก *ฝัง* ลงใน PDF ผลลัพธ์เพื่อให้ผู้ดูต่อไปเห็นลักษณะเดียวกัน หลังจากโหลดเอกสารแล้ว คุณสามารถบังคับให้ฝังฟอนต์ได้:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

ส่วนโค้ดนี้แสดงให้เห็นว่าการ **กำหนดค่า font settings** สามารถต่อยอดไปไกลกว่าการโหลดเพียงอย่างเดียว

---

## Full runnable example

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในโปรเจกต์ Console App ใหม่ได้ รวมทุกส่วนที่กล่าวถึงข้างต้น

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (เมื่อมีฟอนต์ที่หายไป):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

หากไม่มีการแทนที่ ฟีดแบ็กที่แสดงจะเป็นเพียงข้อความสำเร็จเท่านั้น

---

## Conclusion

เราได้ **สร้าง warning callback** ที่ตรวจจับ **ฟอนต์ที่หายไป** อย่างเชื่อถือได้ขณะ **โหลดเอกสาร Word** ด้วย Aspose.Words, และแสดงวิธี **กำหนดค่า font settings** เพื่อควบคุมตำแหน่งที่ไลบรารีค้นหาฟอนต์และฟอนต์สำรองที่ใช้ การเชื่อม `FontSettings` กับ `LoadOptions` ทำให้คุณมองเห็นปัญหาที่เกี่ยวกับฟอนต์ได้อย่างเต็มที่—ไม่ต้องกังวลเรื่องการจัดหน้าเงียบ ๆ อีกต่อไป

ขั้นตอนต่อไป? ลองเปลี่ยน `FontWarningHandler` ให้เขียนลงฐานข้อมูล, หรือทดลอง **กฎการแทนที่ฟอนต์** เพื่อแมปฟอนต์ที่หายไปกับฟอนต์ที่ได้รับการอนุมัติจากแบรนด์ คุณอาจสำรวจ **การโหลดฟอนต์แบบไดนามิก** จากคลาวด์สตอเรจหากแอปของคุณทำงานในสภาพแวดล้อมคอนเทนเนอร์

มีคำถามเกี่ยวกับกรณีขอบเฉพาะ—เช่นการจัดการคุณลักษณะ OpenType หรือไฟล์ DOCX ที่เข้ารหัส? แสดงความคิดเห็นด้านล่าง แล้วขอให้สนุกกับการเขียนโค้ด!

---

![สร้างการแจ้งเตือน callback diagram](https://example.com/images/create-warning-callback.png "สร้างการแจ้งเตือน callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}