---
category: general
date: 2026-03-01
description: สร้าง FontSettings ใน C# เพื่อตรวจจับฟอนต์ที่หายไป, บันทึกข้อความฟอนต์,
  และจัดการฟอนต์ที่หายไปด้วย Aspose.Words. คู่มือขั้นตอนต่อขั้นตอนสำหรับนักพัฒนา.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: th
og_description: สร้าง FontSettings ใน C# เพื่อตรวจจับฟอนต์ที่หายไป, จับข้อความฟอนต์,
  และจัดการฟอนต์ที่หายไปโดยใช้ Aspose.Words. บทเรียนเต็มพร้อมโค้ด.
og_title: สร้าง FontSettings ใน C# – ตรวจจับฟอนต์ที่หายไปและบันทึกข้อความฟอนต์
tags:
- Aspose.Words
- C#
- Font Management
title: สร้าง FontSettings ใน C# – ตรวจจับฟอนต์ที่หายไปและบันทึกข้อความฟอนต์
url: /th/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้าง FontSettings ใน C# – ตรวจจับฟอนต์ที่หายไปและบันทึกข้อความฟอนต์

เคยต้อง **create FontSettings** ในโครงการ .NET แต่ไม่แน่ใจว่าจะตรวจจับฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องเป้าหมายได้อย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว ในแอปพลิเคชันจริงหลาย ๆ ตัว—เช่น ตัวสร้างรายงานอัตโนมัติหรือเครื่องแปลงเอกสาร—ฟอนต์ที่หายไปอาจทำให้การจัดวางเสียหายโดยไม่แจ้งเตือน และคุณจะไม่รู้จนกว่า PDF จะดูผิดรูป  

ถ้าคุณสามารถ **detect missing fonts**, **capture font messages**, และ **handle missing fonts** ก่อนที่มันจะทำลายผลลัพธ์ของคุณได้ล่ะ? ข่าวดีคือ Aspose.Words ทำให้เรื่องนี้ง่ายเหมือนเค้ก ในบทแนะนำนี้เราจะพาคุณผ่านกระบวนการทั้งหมด ตั้งแต่การตั้งค่าอ็อบเจกต์ `FontSettings` ไปจนถึงการเชื่อมต่อ callback คำเตือนที่บอกคุณว่า glyph ใดถูกแทนที่

> **TL;DR:** เมื่อเสร็จคุณจะมีแอปคอนโซล C# ที่พร้อมรันซึ่งบันทึกการแทนที่ฟอนต์ทุกครั้ง ให้คุณตัดสินใจว่าจะฝังฟอนต์ทดแทนหรือแจ้งผู้ใช้หรือไม่.

## ข้อกำหนดเบื้องต้น

- .NET 6 SDK (หรือเวอร์ชัน .NET ล่าสุดใดก็ได้)  
- Visual Studio 2022 หรือ VS Code พร้อมส่วนขยาย C#  
- ใบอนุญาต Aspose.Words สำหรับ .NET (รุ่นทดลองฟรีใช้ได้สำหรับสาธิตนี้)  
- ตัวอย่างไฟล์ DOCX ที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้ง (เช่น *Comic Sans MS* บนเครื่อง Linux)  

ไม่จำเป็นต้องใช้แพ็กเกจ NuGet พิเศษใด ๆ นอกจาก `Aspose.Words`

## ขั้นตอนที่ 1 – ติดตั้ง Aspose.Words และตั้งค่าโปรเจกต์

เริ่มต้นด้วยการสร้างโปรเจกต์คอนโซลใหม่และเพิ่มไลบรารี Aspose.Words เข้าไป

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **เคล็ดลับ:** หากคุณมีโซลูชันอยู่แล้ว เพียงเพิ่มแพ็กเกจผ่าน UI ของ NuGet Package Manager—ทำให้การติดตามเวอร์ชันง่ายขึ้น.

## ขั้นตอนที่ 2 – สร้าง FontSettings (คีย์เวิร์ดหลักปรากฏที่นี่)

ขั้นตอน **create FontSettings** เป็นหัวใจของกระบวนการทำงานที่เกี่ยวกับฟอนต์ทุกประเภท `FontSettings` บอก Aspose.Words ว่าจะค้นหาฟอนต์ที่ไหน ใช้โฟลเดอร์ระบบหรือไม่ และจะทำอย่างไรเมื่อบางอย่างหายไป

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

ทำไมจึงสำคัญ? หากไม่มีการกำหนดค่า `FontSettings` อย่างเหมาะสม เอนจินจะทำการแทนที่ glyph ที่หายไปด้วยฟอนต์ระบบโดยไม่แจ้งเตือน และคุณจะไม่เคยเห็นคำเตือน

## ขั้นตอนที่ 3 – เชื่อมต่อ LoadOptions กับ FontSettings

`LoadOptions` ให้คุณส่ง `FontSettings` เข้าไปในตัวโหลดเอกสาร นี่คือสะพานที่ทำให้เอนจิน **detect missing fonts** ระหว่างขั้นตอนการสร้าง `Document`

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

ตอนนี้ทุกครั้งที่คุณโหลดไฟล์ DOCX ด้วย `loadOptions` Aspose.Words จะอ้างอิง `FontSettings` ที่เราตั้งค่าไว้ก่อนหน้า

## ขั้นตอนที่ 4 – แนบ Warning Callback เพื่อ **Capture Font Messages**

Aspose.Words ส่งคำเตือนสำหรับเงื่อนไขหลายอย่าง—การแทนที่ฟอนต์เป็นหนึ่งในที่พบบ่อย โดยการให้การทำงานของ `IWarningCallback` คุณสามารถ **capture font messages** ได้แบบเรียลไทม์

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### คลาส Warning Handler

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

ฟิลด์ `info.Description` มีข้อความที่มนุษย์อ่านได้ เช่น *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* นี่คือประเภทของผลลัพธ์ที่คุณต้องการเพื่อ **handle missing fonts** อย่างราบรื่น

## ขั้นตอนที่ 5 – โหลดเอกสารและให้ Callback ทำงานของมัน

เมื่อทุกอย่างเชื่อมต่อแล้ว การโหลดเอกสารก็ง่ายดาย หากไฟล์ต้นทางอ้างอิงฟอนต์ที่ไม่มีในระบบ ตัวจัดการคำเตือนของเราจะทำงาน

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

เมื่อคุณรันโปรแกรม คุณจะเห็นผลลัพธ์บนคอนโซลคล้ายกับ:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

ผลลัพธ์นั้นเป็นส่วนของ **capture font messages** ในกระบวนการทำงานของเรา คุณสามารถขยายตัวจัดการเพื่อบันทึกลงไฟล์ ส่ง telemetry หรือแม้แต่ยกเลิกการแปลงหากฟอนต์สำคัญหายไป

## ขั้นตอนที่ 6 – ตัวอย่างทำงานเต็มรูปแบบ (รวมทุกส่วนเข้าด้วยกัน)

ด้านล่างเป็นโปรแกรมที่สมบูรณ์พร้อมคัดลอกและวาง เพียงวางลงใน `Program.cs` ปรับเส้นทางไฟล์ แล้วรันด้วย `dotnet run`

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

การรันโปรแกรมบนเครื่องที่ไม่มี *Comic Sans MS* จะพิมพ์ข้อความคล้ายกับ:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

คุณจะได้ไฟล์ `Result.pdf` ที่ใช้ฟอนต์ที่ถูกแทนที่ ทำให้การแปลงไม่เกิดการล่ม

## คำถามทั่วไปและกรณีขอบ

| Question | Answer |
|----------|--------|
| **ถ้าฉันต้องการให้การแปลงล้มเหลวแทนการแทนที่?** | ใน `FontSubstitutionWarningHandler` ให้โยนข้อยกเว้นเมื่อ `info.Description` มีชื่อฟอนต์สำคัญ |
| **ฉันสามารถฝังฟอนต์ทดแทนโดยอัตโนมัติได้หรือไม่?** | ได้. หลังจากตรวจจับฟอนต์ที่หายไป คุณสามารถโหลด `FontInfo` สำรองจากเส้นทางที่รู้จักและเพิ่มเข้าไปใน `fontSettings` ผ่าน `fontSettings.SetFontsFolder` |
| **วิธีนี้ทำงานบน Linux/macOS หรือไม่?** | แน่นอน. `FontSettings` ทำงานข้ามแพลตฟอร์ม; เพียงตรวจสอบให้โฟลเดอร์สำรองมีไฟล์ `.ttf` หรือ `.otf` ที่เหมาะสม |
| **Callback คำเตือนนี้ปลอดภัยต่อการทำงานหลายเธรดหรือไม่?** | Callback ทำงานบนเธรดเดียวกับที่โหลดเอกสาร ดังนั้นคุณไม่จำเป็นต้องซิงโครไนซ์เพิ่มเติมสำหรับการบันทึกบนคอนโซล สำหรับสถานการณ์หลายเธรด ให้ปกป้องทรัพยากรที่ใช้ร่วมกัน |
| **ฉันจะบันทึกคำเตือนลงไฟล์อย่างไร?** | แทนที่ `Console.WriteLine` ด้วย `File.AppendAllText("font_warnings.log", ...)` หรือใช้เฟรมเวิร์กการบันทึกใด ๆ (Serilog, NLog). |

## เคล็ดลับระดับมืออาชีพสำหรับการจัดการฟอนต์ในสภาพแวดล้อมการผลิต

1. **Cache Font Lookups** – การใช้ `FontSettings` ตัวเดียวกันซ้ำหลายครั้งในการโหลดเอกสารช่วยหลีกเลี่ยงการสแกนไฟล์ระบบหลายครั้ง.  
2. **Whitelist Critical Fonts** – หากแบรนด์ของคุณต้องการฟอนต์เฉพาะ ตรวจสอบการมีอยู่ของฟอนต์ตั้งแต่ต้นและยกเลิกการทำงานพร้อมข้อความแสดงข้อผิดพลาดที่ชัดเจน.  
3. **Use `SetFontFolder` Recursively** – การตั้งค่า `recursive: true` ทำให้สแกนโฟลเดอร์ย่อยทั้งหมด ซึ่งสะดวกเมื่อคุณจัดส่งคอลเลกชันฟอนต์ทั้งหมด.  
4. **Combine with `FontSubstitutionSettings`** – คุณสามารถปรับแต่งกฎการแทนที่ได้ละเอียด (เช่น ให้ความสำคัญกับฟอนต์ที่มีชื่อครอบครัวเดียวกัน).  

## สรุป

เราเพิ่ง **สร้าง FontSettings**, ตั้งค่า `LoadOptions` เพื่อ **detect missing fonts**, แนบ callback ที่ **captures font messages**, และแสดงวิธี **handle missing fonts** อย่างเป็นระบบและพร้อมใช้งานในสภาพแวดล้อมการผลิต ทั้งกระบวนการทั้งหมดใช้เพียงไม่กี่สิบบรรทัดของ C# แต่ให้คุณมองเห็นภาพรวมของฟอนต์ใน DOCX ใด ๆ ที่คุณประมวลผลได้อย่างครบถ้วน

ต่อไปคุณอาจสำรวจ:

- **Embedding fallback fonts** โดยตรงลงใน PDF ผลลัพธ์ (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programmatically substituting fonts** ตามกฎการแบรนด์ขององค์กร.  
- **Integrating with a CI pipeline** เพื่อทำเครื่องหมายเอกสารที่ใช้ฟอนต์ไม่ได้รับอนุญาตโดยอัตโนมัติ.

ลองใช้งาน ปรับแต่ง warning handler ให้ตรงกับความต้องการของคุณ และให้ไพพ์ไลน์เอกสารของคุณทำงานอย่างมั่นใจ—ไม่มีปัญหาเลย์เอาต์ลึกลับที่เกิดจากการสลับฟอนต์ที่มองไม่เห็นอีกต่อไป

เขียนโค้ดให้สนุก! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}