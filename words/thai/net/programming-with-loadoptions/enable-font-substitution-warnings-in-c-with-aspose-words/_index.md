---
category: general
date: 2026-06-20
description: เปิดการแจ้งเตือนการแทนที่ฟอนต์ใน C# ด้วย Aspose.Words เรียนรู้วิธีกำหนดค่า
  LoadOptions, จับการแจ้งเตือน, และจัดการฟอนต์ที่หายไปอย่างมีประสิทธิภาพ.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: th
og_description: เปิดการแจ้งเตือนการแทนที่ฟอนต์ใน C# ด้วย Aspose.Words คู่มือนี้จะแสดงวิธีตั้งค่า
  LoadOptions, อ่าน WarningInfo, และแสดงข้อความฟอนต์ที่หายไป
og_title: เปิดการเตือนการแทนที่ฟอนต์ใน C# – คู่มือฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: เปิดการแจ้งเตือนการแทนที่ฟอนต์ใน C# ด้วย Aspose.Words
url: /th/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปิดการแจ้งเตือนการแทนที่ฟอนต์ใน C# ด้วย Aspose.Words

เคยสงสัยไหมว่า **จะเปิดการแจ้งเตือนการแทนที่ฟอนต์** อย่างไรเมื่อเอกสาร Word อ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์? คุณไม่ได้เป็นคนเดียว ฟอนต์ที่หายไปอาจทำให้การจัดหน้าใน PDF หรือภาพที่สร้างขึ้นเสียหายโดยไม่รู้ตัว และวิธีเดียวที่จะจับได้ตั้งแต่แรกคือการฟังการแจ้งเตือนที่ Aspose.Words ส่งออกมา

ในบทแนะนำนี้เราจะเดินผ่านตัวอย่างเชิงปฏิบัติที่แสดงให้คุณเห็นอย่างชัดเจนว่าจะแปลงการแจ้งเตือนเหล่านั้นให้ทำงานอย่างไร ดึงข้อมูลออกจากคอลเลกชัน `WarningInfo` และพิมพ์ข้อความที่มีความหมายไปยังคอนโซล สุดท้ายคุณจะรู้วิธีกำหนดค่า **Aspose.Words LoadOptions**, จัดการ **การแจ้งเตือนการแทนที่ฟอนต์ใน C#**, และทำให้กระบวนการประมวลผลเอกสารของคุณปลอดภัยอย่างเต็มที่

เราจะกล่าวถึงกรณีขอบบางบางอย่างด้วย — เช่น สิ่งที่เกิดขึ้นหากคุณปิดการแจ้งเตือน หรือหากคุณต้องการบันทึกแทนการพิมพ์ — พร้อมกับให้โค้ดตัวอย่างที่พร้อมคัดลอก‑วางและทำงานกับ Aspose.Words for .NET เวอร์ชันล่าสุด (เวอร์ชัน 24.10)

## สิ่งที่คุณต้องมี

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานบน .NET Framework 4.7+ ด้วย)
- การอ้างอิง NuGet ไปยัง `Aspose.Words` (ติดตั้งด้วย `dotnet add package Aspose.Words`)
- ไฟล์ Word ที่อ้างอิงฟอนต์ที่คุณ **ไม่ได้** ติดตั้ง (เช่น `DocumentWithMissingFont.docx`)
- IDE ที่ใช้งานได้ดี (Visual Studio, Rider หรือ VS Code)

เท่านี้—ไม่มีบริการเสริม ไม่มีเครื่องมือที่เป็นกรรมสิทธิ์ พร้อมหรือยัง? ไปกันเลย

## ขั้นตอนที่ 1: เปิดการแจ้งเตือนการแทนที่ฟอนต์

สิ่งแรกที่คุณต้องทำคือบอก Aspose.Words ว่าต้องการรับการแจ้งเตือนเมื่อมีการแทนที่ฟอนต์ที่หายไป วิธีทำคือผ่านคุณสมบัติ `FontSettings` ของอ็อบเจกต์ `LoadOptions` โดยค่าเริ่มต้น การแจ้งเตือนจะ **ปิด** เพื่อให้ API เงียบ เราต้องเปิดสวิตช์นี้ด้วยตนเอง

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **ทำไมวิธีนี้ถึงได้ผล:** เมื่อ `FontSettings` ไม่เป็น `null` ไลบรารีจะเติม `Document.WarningInfo` ด้วยรายการ `WarningType.FontSubstitution` ที่พบขณะโหลดเอกสาร ถือเป็นการเปิด “โหมดดีบัก” สำหรับฟอนต์

## ขั้นตอนที่ 2: โหลดเอกสารด้วยตัวเลือกที่กำหนด

เมื่อคอลเลกชันการแจ้งเตือนพร้อมใช้งานแล้ว ให้โหลดเอกสารของคุณโดยใช้ `LoadOptions` ที่เตรียมไว้ หากเอกสารมีฟอนต์ที่หายไป Aspose.Words จะทำการแทนที่ด้วยฟอนต์สำรองและผลักการแจ้งเตือนเข้าไปในรายการ `WarningInfo`

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **เคล็ดลับ:** หากคุณประมวลผลไฟล์หลายไฟล์ในลูป ให้ใช้ `LoadOptions` ตัวเดียวซ้ำหลายครั้ง — การสร้างครั้งเดียวช่วยประหยัดมิลลิวินาทีต่อการวนลูป

## ขั้นตอนที่ 3: วนลูป WarningInfo และแสดงข้อความการแทนที่ฟอนต์

หลังจากโหลดเอกสารแล้ว คอลเลกชัน `WarningInfo` จะเก็บการแจ้งเตือนทุกอย่างที่เกิดขึ้นระหว่างการโหลด เราจะกรองเฉพาะ `WarningType.FontSubstitution` เท่านั้น

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

การรันโค้ดส่วนนี้กับเอกสารที่อ้างอิงฟอนต์ “Papyrus” ที่หายไปอาจให้ผลลัพธ์เช่น:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

นี่คือ **ข้อความการแทนที่ฟอนต์** ที่คุณกำลังมองหา — ชัดเจน ใช้งานได้จริง และพร้อมจะบันทึกหรือส่งไปยังระบบแจ้งเตือน

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมคอนโซลแบบอิสระที่รวมทุกอย่างไว้ด้วยกัน คัดลอก‑วางลงในโครงการ `.csproj` ใหม่แล้วกด **Run**

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### ผลลัพธ์ที่คาดหวัง

หากเอกสารอ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง คุณจะเห็นข้อความคล้ายดังนี้:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

หากฟอนต์ทั้งหมดติดตั้งอยู่บนเครื่อง โปรแกรมจะพิมพ์เพียง:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## ข้อผิดพลาดทั่วไป & เคล็ดลับระดับมืออาชีพ

| ปัญหา | สาเหตุ | วิธีแก้ / ป้องกัน |
|-------|--------|-------------------|
| **การแจ้งเตือนหายไป** | คุณเคลียร์ `FontSettings` หรือใช้ `LoadOptions` ที่ไม่มีมัน | ต้องสร้าง `FontSettings` เสมอ แม้จะไม่ได้แก้ไขคุณสมบัติใด ๆ |
| **การแจ้งเตือนมากเกินไป** | เอกสารใช้ฟอนต์แปลกหลายตัว | พิจารณาเพิ่มโฟลเดอร์ฟอนต์แบบกำหนดเองให้กับ `FontSettings` ผ่าน `SetFontsFolder` เพื่อลดการแทนที่ |
| **การลดประสิทธิภาพในลูปแน่น** | สร้าง `LoadOptions` ใหม่ทุกครั้ง | ใช้ `LoadOptions` ตัวเดียวซ้ำหลายไฟล์ |
| **ไม่มีข้อความบนคอนโซล** | รันในแอป GUI ที่ `Console.WriteLine` ถูกละเลย | ส่งการแจ้งเตือนไปยัง logger (`ILogger`) หรือเขียนลงไฟล์ |

### การจัดการการแจ้งเตือนในบริการจริง

ใน Web API คุณอาจไม่ต้องการพิมพ์ลงคอนโซล แต่ให้ส่งการแจ้งเตือนไปยังบันทึกแบบโครงสร้าง:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

ด้วยวิธีนี้คุณยังคง **จัดการการแจ้งเตือนเอกสาร** ได้ในขณะที่บริการของคุณยังคงสะอาดตา

## การขยายตัวอย่าง

- **ดักจับประเภทการแจ้งเตือนอื่น** (เช่น `WarningType.UnknownFileFormat`) โดยลบเงื่อนไข `if` ออก
- **บันทึกรายงานการแจ้งเตือนทั้งหมดเป็น JSON** เพื่อการวิเคราะห์ต่อไป
- **บังคับใช้ฟอนต์สำรองเฉพาะ** โดยตั้งค่า `FontSettings.SubstitutionSettings.DefaultFontName`

ทั้งหมดนี้เป็นการต่อยอดที่เป็นธรรมชาติเมื่อคุณเชี่ยวชาญการ **เปิดการแจ้งเตือนการแทนที่ฟอนต์** แล้ว

## สรุป

เราได้แสดงวิธี **เปิดการแจ้งเตือนการแทนที่ฟอนต์** ใน C# ด้วย Aspose.Words ตั้งแต่การกำหนด `LoadOptions` ไปจนถึงการวนลูป `WarningInfo` และพิมพ์ข้อความที่เป็นมิตร หากทำตามขั้นตอนนี้ คุณจะปกป้องสายการประมวลผลเอกสารของคุณจากการเปลี่ยนแปลงเลย์เอาต์ที่เงียบ ๆ เนื่องจากฟอนต์ที่หายไป

ต่อไป ลองเพิ่มโฟลเดอร์ฟอนต์แบบกำหนดเอง, บันทึกการแจ้งเตือนลงไฟล์, หรือแม้กระทั่งส่งไปยังแดชบอร์ดการตรวจสอบ รูปแบบเดียวกันนี้ใช้ได้กับทุกสถานการณ์ **การจัดการการแจ้งเตือนเอกสาร** ไม่ว่าจะเป็นการแปลงเป็น PDF, การเรนเดอร์ภาพ, หรือการทำ mail‑merge

มีคำถามเกี่ยวกับ **การแจ้งเตือนการแทนที่ฟอนต์ใน C#** หรืออยากแชร์วิธีแก้ที่เจ๋ง? แสดงความคิดเห็นด้านล่าง—ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานแบบต่าง ๆ ในโครงการของคุณเอง

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}