---
category: general
date: 2026-02-18
description: เรียนรู้วิธีจับคำเตือนฟอนต์และตรวจจับฟอนต์ที่หายไปใน C# ด้วย Aspose.Words.
  ปฏิบัติตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อจัดการฟอนต์ที่หายไปอย่างมีประสิทธิภาพ.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: th
og_description: บันทึกคำเตือนฟอนต์ใน C# และเรียนรู้วิธีตรวจจับฟอนต์ที่หายไป, จัดการฟอนต์ที่หายไป,
  และแสดงรายการฟอนต์ที่หายไปพร้อมตัวอย่างโค้ดเต็ม
og_title: จับคำเตือนฟอนต์ใน C# – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Font Management
title: จับคำเตือนฟอนต์ใน C# – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์
url: /th/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

produce final output with translated content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การจับคำเตือนฟอนต์ใน C# – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์

เคยสงสัยไหมว่า **การจับคำเตือนฟอนต์** ทำอย่างไรเมื่อเอกสารอ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์? คุณไม่ได้เป็นคนเดียวที่สงสัย ในแอปพลิเคชันระดับองค์กรหลายแห่ง ฟอนต์ที่หายไปทำให้การจัดวางหน้าตาเสียหาย และวิธีที่เชื่อถือได้ที่สุดในการตรวจจับคือการฟังคำเตือนที่ไลบรารีส่งออก  

ในบทเรียนนี้เราจะสาธิตวิธีแก้ที่พร้อมรันที่ไม่เพียงแต่ **จับคำเตือนฟอนต์** แต่ยัง **ตรวจจับฟอนต์ที่หายไป**, **จัดการฟอนต์ที่หายไป**, และแม้กระทั่ง **แสดงรายการฟอนต์ที่หายไป** เพื่อให้คุณตัดสินใจว่าจะใช้ฟอนต์สำรอง ฝังฟอนต์ หรือแจ้งผู้ใช้ ไม่ต้องอ้างอิงเอกสารภายนอก—แค่คัดลอก วาง แล้วรัน

## สิ่งที่คุณจะได้เรียนรู้

- วิธีกำหนดค่า `LoadOptions` เพื่อเปิดการเตือนการแทนที่ฟอนต์  
- โค้ดที่จำเป็นเพื่อโหลดไฟล์ DOCX และดึงคำเตือนทั้งหมด  
- เหตุผลว่าทำไมแต่ละขั้นตอนจึงสำคัญ รวมถึงการพิจารณาประสิทธิภาพ  
- การจัดการกรณีขอบเช่นเอกสารที่มีฟอนต์หลายสคริปต์หรือโฟลเดอร์ฟอนต์แบบกำหนดเอง  

**Prerequisites**: .NET 6+ (หรือ .NET Framework 4.6+), การอ้างอิงไปยังแพคเกจ **Aspose.Words** NuGet, และความเข้าใจพื้นฐานของ C#. หากคุณไม่เคยใช้ Aspose.Words มาก่อน ไม่ต้องกังวล—คู่มือนี้จะพาคุณผ่านทุกขั้นตอน

![Diagram showing capture font warnings flow](image.png){alt="แผนภาพการจับคำเตือนฟอนต์"}

## การจับคำเตือนฟอนต์ – ทำไมจึงสำคัญ

เมื่อ Aspose.Words โหลดเอกสาร มันจะสลับฟอนต์ที่ไม่มีอยู่ด้วยฟอนต์สำรองโดยอัตโนมัติ ฟอนต์สำรองนี้ทำให้การโหลดดำเนินต่อไปได้ แต่ผลลัพธ์ที่แสดงอาจผิดตำแหน่งอย่างสิ้นเชิง โดยการเปิดแฟล็ก **SubstitutionWarningLevel.All** ไลบรารีจะเพิ่มรายการ `WarningInfo` สำหรับฟอนต์ที่หายไปแต่ละตัว ทำให้คุณ **ตรวจจับฟอนต์ที่หายไป** ก่อนที่เอกสารจะถูกเรนเดอร์หรือบันทึก

> **Pro tip:** หากคุณประมวลผลไฟล์หลายร้อยไฟล์ในงานแบตช์ การบันทึกคำเตือนเหล่านี้ลงในที่เก็บศูนย์กลางสามารถประหยัดเวลาการตรวจสอบด้วยตนเองหลายชั่วโมงในภายหลังได้

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์ของคุณ

1. เปิด IDE ที่คุณชื่นชอบ (Visual Studio, Rider, VS Code).  
2. สร้างโปรเจกต์คอนโซลใหม่:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. เพิ่มแพคเกจ Aspose.Words:

```bash
dotnet add package Aspose.Words
```

แค่นั้น—ไม่ต้องเพิ่ม DLL พิเศษ ไม่ต้องใช้ COM interop ไลบรารีมาพร้อมทุกอย่างที่คุณต้องการเพื่อ **จัดการฟอนต์ที่หายไป**  

## ขั้นตอนที่ 2: เตรียม Load Options เพื่อจับคำเตือนการแทนที่ฟอนต์ทั้งหมด

เพื่อให้เอนจิน **จับคำเตือนฟอนต์**, คุณต้องบอกให้มันบันทึกการแทนที่ทุกครั้ง โค้ดต่อไปนี้สร้างอินสแตนซ์ `LoadOptions`, เปิดระดับคำเตือน, และ (ตามต้องการ) ชี้ไปยังโฟลเดอร์ที่มีฟอนต์กำหนดเองที่คุณอาจต้องการใช้

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**ทำไมเรื่องนี้สำคัญ:**  
- `SubstitutionWarningLevel.All` ทำให้ **ทุก** เหตุการณ์ฟอนต์ที่หายไปถูกบันทึก ไม่ใช่แค่เหตุการณ์แรกเท่านั้น  
- หากไม่ตั้งแฟล็กนี้ Aspose.Words จะสลับฟอนต์โดยเงียบ ๆ และคุณจะไม่รู้ว่ามีปัญหาเกิดขึ้น  

## ขั้นตอนที่ 3: โหลดเอกสารโดยใช้ตัวเลือกที่กำหนดค่า

ตอนนี้เราจะเปิดไฟล์จริง ๆ แทนที่ `DocumentWithMissingFonts.docx` ด้วยพาธของไฟล์ทดสอบของคุณ

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

หากไฟล์มีการอ้างอิงฟอนต์ที่ไม่มีบนเครื่อง (หรือในโฟลเดอร์เพิ่มเติมที่คุณระบุ) `document.WarningInfoCollection` จะถูกเติมข้อมูล

## ขั้นตอนที่ 4: ค้นหาและแสดงคำเตือนการแทนที่ฟอนต์ใด ๆ

นี่คือหัวใจของบทเรียน: การวนลูป `WarningInfoCollection` เพื่อ **แสดงรายการฟอนต์ที่หายไป** เราจะกรองโดย `WarningType.FontSubstitution` และพิมพ์ข้อความที่เป็นมิตร

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

หากเอกสารใช้ฟอนต์ที่ติดตั้งอยู่แล้ว คุณจะเห็นบรรทัด “✅ No missing fonts detected”

## ขั้นตอนที่ 5: ขั้นสูง – วิธี **จัดการฟอนต์ที่หายไป** อย่างโปรแกรมเมติก

การพิมพ์รายการอาจเพียงพอสำหรับเครื่องมือวินิจฉัย แต่ระบบการผลิตหลายระบบต้อง **จัดการฟอนต์ที่หายไป** โดยอัตโนมัติ ด้านล่างเป็นสองกลยุทธ์ที่พบบ่อย:

### 5.1 แทนที่ด้วยฟอนต์สำรองที่รู้จัก

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 ฝังฟอนต์กำหนดเองแบบทันที

หากคุณมีไฟล์ฟอนต์ขององค์กร (`MyBrand.ttf`) คุณสามารถฝังมันเมื่อพบฟอนต์ที่หายไป:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Note:** การฝังฟอนต์อาจทำให้ขนาดไฟล์ผลลัพธ์เพิ่มขึ้น ดังนั้นควรพิจารณาความสมดุลระหว่างความแม่นยำและแบนด์วิธ  

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| ไม่มีคำเตือนปรากฏแม้เอกสารดูผิดพลาด | `SubstitutionWarningLevel` ไม่ได้ตั้งค่าเป็น `All` | ตรวจสอบให้ขั้นตอนที่ 2 ตั้งค่าสถานะตามที่แสดง |
| คำเตือนแสดงฟอนต์เดียวกันหลายครั้ง | เอกสารมีฟอนต์นี้ในหลายสไตล์ | ทำการลบซ้ำหากต้องการรายการที่ไม่ซ้ำ: `fontWarnings.Select(w => w.Description).Distinct()` |
| แอปพลิเคชันหยุดทำงานกับไฟล์ DOCX ขนาดใหญ่ | โหลดด้วยการตั้งค่าหน่วยความจำเริ่มต้น | ใช้ `LoadOptions.LoadFormat` หรือสตรีมไฟล์เพื่อลดความกดดันของหน่วยความจำ |

## ตัวอย่างทำงานเต็ม (พร้อมคัดลอก‑วาง)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

เรียกใช้โปรแกรมด้วย `dotnet run`. คุณควรเห็นรายการฟอนต์ที่หายไปพิมพ์บนคอนโซล ยืนยันว่าคุณได้ **จับคำเตือนฟอนต์** สำเร็จแล้ว

## สรุป

ตอนนี้คุณมีรูปแบบที่ครบถ้วนและพร้อมใช้งานในระดับการผลิตเพื่อ **จับคำเตือนฟอนต์**, **ตรวจจับฟอนต์ที่หายไป**, **จัดการฟอนต์ที่หายไป**, และ **แสดงรายการฟอนต์ที่หายไป** ด้วย Aspose.Words ใน C#. วิธีนี้เบา ใช้แค่ไม่กี่บรรทัดโค้ด และสามารถนำไปใส่ใน pipeline ที่มีอยู่ได้ทุกที่—ไม่ว่าจะเป็น

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}