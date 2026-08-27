---
category: general
date: 2026-01-11
description: เปิดการแจ้งเตือนการแทนที่ฟอนต์เพื่อตรวจจับฟอนต์ที่หายไปในเอกสาร .NET
  ของคุณ เรียนรู้วิธีดึงชื่อฟอนต์ที่หายไปและแสดงรายการฟอนต์ที่หายไปด้วย Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: th
og_description: เปิดการแจ้งเตือนการแทนที่ฟอนต์ใน Aspose.Words เพื่อค้นหาแบบอักษรที่หายไป,
  รับชื่อฟอนต์ที่หายไป, และแสดงรายการฟอนต์ที่หายไปในเอกสารของคุณ.
og_title: เปิดการแจ้งเตือนการแทนที่ฟอนต์ – การสอน C# ทีละขั้นตอน
tags:
- Aspose.Words
- C#
- Document Processing
title: เปิดการเตือนการแทนที่ฟอนต์ใน Aspose.Words – คู่มือฉบับสมบูรณ์
url: /th/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปิดการแจ้งเตือนการแทนที่ฟอนต์ – คู่มือฉบับสมบูรณ์

เคยสงสัยไหมว่า ทำไมเอกสาร Word ถึงดูแปลกเล็กน้อยหลังจากที่คุณอัปโหลดไปที่เซิร์ฟเวอร์? มีโอกาสสูงที่ฟอนต์ที่ผู้เขียนต้นฉบับใช้ไม่ได้ติดตั้งบนเครื่องของคุณ และ Aspose.Words จะสลับฟอนต์โดยอัตโนมัติเป็นฟอนต์ที่ใกล้เคียงที่สุด **เปิดการแจ้งเตือนการแทนที่ฟอนต์** แล้วคุณจะทราบทันทีว่าฟอนต์ใดหายไป, ถูกแทนที่ด้วยอะไร, และต้องทำอย่างไรกับข้อมูลนั้น

ในบทแนะนำนี้เราจะเดินผ่านตัวอย่างเชิงปฏิบัติแบบครบวงจรที่แสดงให้คุณเห็นวิธี **ตรวจจับฟอนต์ที่หายไป**, ดึง **ชื่อฟอนต์ที่หายไป**, และแม้กระทั่ง **รายการฟอนต์ที่หายไป** เพื่อทำรายงาน ไม่อ้อมค้อม เพียงโซลูชันที่ชัดเจนซึ่งคุณสามารถนำไปใช้ในโปรเจค .NET ใดก็ได้ทันที

---

## สิ่งที่คุณจะได้เรียนรู้

- วิธีกำหนดค่า `LoadOptions` เพื่อให้ Aspose.Words ส่งคำเตือนอย่างละเอียด
- โค้ดที่จำเป็นในการโหลดเอกสารและวนลูปคำเตือนที่เกี่ยวกับฟอนต์
- วิธีสกัดชื่อฟอนต์ที่หายไปและการแทนที่ของมัน แล้วแสดงผลเป็นรายงานที่เรียบร้อย
- เคล็ดลับการจัดการกับกรณีขอบเขต เช่น เอกสารที่มีฟอนต์หายหลายสิบตัวหรือโฟลเดอร์ฟอนต์แบบกำหนดเอง

### ข้อกำหนดเบื้องต้น

- .NET 6+ (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+ ด้วย)
- Aspose.Words for .NET 23.10 หรือใหม่กว่า (คุณสามารถดาวน์โหลดจาก NuGet)
- ตัวอย่างไฟล์ DOCX ที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้ง (เราจะเรียกมันว่า `MissingFont.docx`)

ถ้าคุณมีสิ่งเหล่านี้แล้ว ไปต่อกันเลย

---

## ขั้นตอนที่ 1: ตั้งค่า LoadOptions เพื่อเปิดการแจ้งเตือนการแทนที่ฟอนต์  

สิ่งแรกที่คุณต้องทำคือบอก Aspose.Words ว่าคุณสนใจฟอนต์ที่หายไป โดยค่าเริ่มต้นไลบรารีจะบันทึกคำเตือนไว้ภายในเท่านั้น การตั้งค่า `SubstitutionWarningLevel` เป็น `Typical` (หรือ `All` สำหรับเอาต์พุตที่ละเอียดที่สุด) จะเปิดสวิตช์นี้

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
เมื่อกำหนด `SubstitutionWarningLevel` แล้ว ทุกครั้งที่ Aspose.Words ไม่พบฟอนต์ที่อ้างอิง มันจะเพิ่ม `FontSubstitutionWarning` ลงในคอลเลกชัน `Warnings` ของเอกสาร คอลเลกชันนี้เป็นวิธีที่เชื่อถือได้เดียวในการ **ตรวจจับฟอนต์ที่หายไป** โดยไม่ต้องพาร์สเอกสารด้วยตนเอง

> **เคล็ดลับ:** หากคุณต้องจัดการกับชุดเอกสารจำนวนมากและต้องการมั่นใจว่าจะจับการแทนที่ทุกกรณี ใช้ `FontSubstitutionWarningLevel.All` แม้จะค่อนข้างรบกวนมากขึ้น แต่รับประกันว่าจะไม่มีคำเตือนใดหลุดรอด

---

## ขั้นตอนที่ 2: โหลดเอกสารด้วยตัวเลือกที่กำหนดไว้  

เมื่อระบบคำเตือนพร้อมแล้ว ให้โหลดไฟล์ DOCX ของคุณด้วย `LoadOptions` ที่เพิ่งเตรียมไว้ เส้นทางไฟล์สามารถเป็นแบบเต็มหรือแบบสัมพันธ์ได้ เพียงแค่แน่ใจว่าไฟล์มีอยู่จริง

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**อะไรที่เกิดขึ้นเบื้องหลัง?**  
Aspose.Words จะพาร์ส XML ของเอกสาร, แกะ `<w:font>` แต่ละตัว, แล้วตรวจสอบแคตาล็อกฟอนต์ของระบบ (รวมถึงโฟลเดอร์ฟอนต์ที่คุณอาจเพิ่มเข้าไปใน `FontSettings`) หากไม่พบฟอนต์ มันจะบันทึกคำเตือน — นี่คือสิ่งที่เราต้องการเพื่อ **รายการฟอนต์ที่หายไป** ในขั้นตอนต่อไป

---

## ขั้นตอนที่ 3: วนลูปคำเตือนและสกัดรายละเอียดฟอนต์ที่หายไป  

เมื่อเอกสารถูกโหลดเข้าสหน่วยความจำแล้ว คอลเลกชัน `Warnings` จะเก็บ `FontSubstitutionWarning` ทุกรายการ เราจะวนลูป, กรองประเภทที่ต้องการ, แล้วพิมพ์รายงานที่อ่านง่าย

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (สมมติว่าเอกสารต้นฉบับอ้างอิง `MyCustomFont` ซึ่งไม่ได้ติดตั้ง):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

สังเกตว่าทุกรายการให้ทั้ง **ชื่อฟอนต์ที่หายไป** (`MyCustomFont`) และฟอนต์สำรอง (`Arial`) นี่คือข้อมูลที่คุณต้องใช้เพื่อพิจารณาว่าจะฝังฟอนต์ต้นฉบับ, ขอผู้เขียนเปลี่ยนฟอนต์, หรือยอมรับการแทนที่นั้น

---

## ขั้นตอนที่ 4: ทางเลือก – เก็บข้อมูลลงใน List เพื่อประมวลผลต่อ  

หากคุณต้องการส่งออกรายงานเป็น CSV, ส่งผ่าน API, หรือเก็บไว้ในหน่วยความจำเพื่อใช้งานต่อไป คุณสามารถบันทึกคำเตือนลงใน List ที่มีชนิดข้อมูลชัดเจน

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

ตอนนี้คุณมี **รายการฟอนต์ที่หายไป** ในรูปแบบที่ระบบ downstream ใดก็สามารถนำไปใช้ ไม่ว่าจะเป็นการป้อนข้อมูลให้แดชบอร์ดหรือสร้างบันทึกการตรวจสอบ ข้อมูลพร้อมใช้งานแล้ว

---

## ขั้นตอนที่ 5: การจัดการกรณีขอบเขตและข้อผิดพลาดทั่วไป  

### ฟอนต์หลายตัวหายในรอบเดียว  

เทมเพลตองค์กรขนาดใหญ่มักอ้างอิงฟอนต์กำหนดเองหลายสิบตัว คอลเลกชันคำเตือนอาจค่อนข้างใหญ่ แต่รูปแบบการวนลูปที่แสดงด้านบนขยายตามจำนวนเชิงเส้น ดังนั้นประสิทธิภาพจึงไม่เป็นปัญหา เพียงจำไว้ว่าให้ทำให้ผลลัพธ์อ่านง่าย — การจัดกลุ่มตามหน้า หรือสไตล์อาจช่วยเมื่อคุณต้องการวิเคราะห์เชิงลึก

### โฟลเดอร์ฟอนต์กำหนดเอง  

หากคุณเก็บฟอนต์ในไดเรกทอรีที่ไม่เป็นมาตรฐาน (เช่นแชร์บนเครือข่าย) ให้บอก Aspose.Words ให้มองหา:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

การตั้งค่านี้ *ก่อน* โหลดเอกสารจะทำให้ไลบรารีมีโอกาสค้นพบฟอนต์ ซึ่งอาจทำให้คำเตือนบางรายการหายไปทั้งหมด

### การกรองคำเตือนเฉพาะ  

บางครั้งคุณอาจรู้ว่าการแทนที่บางอย่างยอมรับได้ (เช่นฟอนต์ตกแต่งที่คุณไม่สนใจเปลี่ยน) คุณสามารถกรองออกหลังจากได้รายการแล้ว:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### ความเข้ากันได้ของเวอร์ชัน  

Enum `FontSubstitutionWarningLevel` มีความเสถียรตั้งแต่ Aspose.Words 20.12 หากคุณใช้เวอร์ชันเก่ากว่า อาจต้องอัปเกรดเพื่อใช้คุณสมบัติระดับคำเตือนนี้

---

## ตัวอย่างทำงานเต็มรูปแบบ  

ด้านล่างเป็นโปรแกรมที่พร้อมรันครบทุกขั้นตอน คัดลอกไปวางในโปรเจคคอนโซลใหม่, เพิ่มแพคเกจ NuGet ของ Aspose.Words, แล้วตั้งค่า `docPath` ให้ชี้ไปที่เอกสารที่อ้างอิงฟอนต์หาย

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

การรันโปรแกรมนี้จะ **เปิดการแจ้งเตือนการแทนที่ฟอนต์**, **ตรวจจับฟอนต์ที่หายไป**, **ดึงชื่อฟอนต์ที่หายไป**, และ **รายการฟอนต์ที่หายไป** ทั้งในคอนโซลและไฟล์ CSV

---

## สรุป  

เราได้ครอบคลุมทุกอย่างที่คุณต้องการเพื่อ **เปิดการแจ้งเตือนการแทนที่ฟอนต์** ใน Aspose.Words ตั้งแต่การกำหนดค่าเบื้องต้นจนถึงการสกัดรายการฟอนต์ที่หายไป ด้วยการทำตามขั้นตอนนี้ คุณจะสามารถตรวจสอบเอกสารของคุณ, รักษาความเที่ยงตรงของการแสดงผล, และหลีกเลี่ยงความประหลาดใจเมื่อเรนเดอร์บนเซิร์ฟเวอร์

ต่อไปคุณอาจอยากสำรวจ:

- **ฝังฟอนต์ที่หายไป** ลงใน PDF หรือ DOCX ที่ส่งออก (ใช้ `FontSettings.EmbeddedFonts`)
- **อัตโนมัติการติดตั้งฟอนต์** บนเอเจนต์การสร้างตามรายงานที่สร้างขึ้น
- **ผสานรวมกับ pipeline CI** เพื่อให้การสร้างล้มเหลวเมื่อฟอนต์สำคัญหายไป

ลองทำตามดู แล้วคุณจะเปลี่ยนระบบแจ้งเตือนง่าย ๆ ให้กลายเป็นเวิร์กโฟลว์การจัดการฟอนต์เต็มรูปแบบ

ขอให้เขียนโค้ดสนุกและฟอนต์ของคุณทั้งหมดถูกพบเจอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}