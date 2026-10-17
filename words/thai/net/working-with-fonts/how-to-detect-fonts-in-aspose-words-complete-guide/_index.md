---
category: general
date: 2026-04-07
description: เรียนรู้วิธีตรวจจับฟอนต์และวิธีดักจับคำเตือนขณะจัดการฟอนต์ที่หายไปใน
  C# ด้วย Aspose.Words พร้อมโค้ดแบบขั้นตอนต่อขั้นตอน.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: th
og_description: วิธีตรวจจับฟอนต์ใน Aspose.Words? ทำตามบทแนะนำนี้เพื่อบันทึกคำเตือนและจัดการกับฟอนต์ที่หายไปได้อย่างง่ายดาย.
og_title: วิธีตรวจจับแบบอักษรใน Aspose.Words – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Font handling
title: วิธีตรวจจับแบบอักษรใน Aspose.Words – คู่มือฉบับสมบูรณ์
url: /th/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตรวจจับฟอนต์ใน Aspose.Words – คู่มือฉบับสมบูรณ์

เคยสงสัย **วิธีตรวจจับฟอนต์** ที่หายไปจากเอกสาร Word ก่อนนำไปใช้งานจริงหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายกรณีขององค์กร ฟอนต์ที่หายไปอาจทำให้กระบวนการแปลงเป็น PDF ล้มเหลวหรือทำให้เลย์เอาต์ผิดพลาดดูไม่เป็นมืออาชีพ ข่าวดีคือ Aspose.Words มีวิธีในตัวที่ช่วยให้คุณค้นพบฟอนต์ที่ไม่มีและแสดงคำเตือนอย่างชัดเจน

ในบทเรียนนี้เราจะอธิบาย **วิธีตรวจจับฟอนต์** อย่างละเอียด **วิธีเก็บคำเตือน** และแนวทางปฏิบัติที่ดีที่สุดในการ **จัดการกับฟอนต์ที่หายไป** เพื่อให้แอปพลิเคชันของคุณทำงานได้อย่างมั่นคง ไม่ต้องใช้เครื่องมือภายนอก ไม่ต้องคาดเดา—เพียงโค้ด C# ธรรมดาที่คุณสามารถนำไปใช้ในโปรเจกต์ได้ทันที

> **แสดงตัวอย่างอย่างเร็ว:** เมื่อจบคุณจะมี `FontSubstitutionWarningCollector` ที่สามารถนำกลับมาใช้ใหม่ได้ ซึ่งจะรวบรวมข้อความการแทนที่ฟอนต์ทุกข้อความระหว่างการโหลดเอกสาร และคุณจะรู้วิธีตอบสนองเมื่อไม่พบฟอนต์

---

## สิ่งที่คุณจะได้เรียนรู้

- วิธีกำหนดค่า `LoadOptions` เพื่อรับฟังคำเตือนการแทนที่ฟอนต์  
- วิธีเก็บคำเตือนเหล่านั้นในคลาสคอลเลกเตอร์ที่กำหนดเอง  
- วิธีประมวลผลคำเตือนที่เก็บไว้และตัดสินใจว่าจะยกเลิก, บันทึก, หรือแทนที่ฟอนต์หรือไม่  
- การจัดการกรณีพิเศษสำหรับเอกสารที่อ้างอิงฟอนต์จากระยะไกลหรือฟอนต์ที่ฝังอยู่ในไฟล์  

**ข้อกำหนดเบื้องต้น:** .NET 6+ (หรือ .NET Framework 4.6+), Aspose.Words for .NET (เวอร์ชันล่าสุด) และความคุ้นเคยพื้นฐานกับ C# หากคุณยังไม่เคยใช้ Aspose.Words ไม่ต้องกังวล—คู่มือนี้สมมุติว่าคุณใช้เวลาเตรียมแค่ไม่กี่นาทีเท่านั้น

---

## วิธีตรวจจับฟอนต์ด้วย Aspose.Words LoadOptions

ขั้นตอนแรกในการตรวจจับฟอนต์ที่หายไปคือบอกให้ Aspose.Words รายงานฟอนต์เหล่านั้น ทำได้โดยใช้คุณสมบัติ `LoadOptions.WarningCallback` ซึ่งรับคลาสใดก็ได้ที่ implements `IWarningCallback` ด้านล่างเราจะสร้างคอลเลกเตอร์ขนาดเล็กที่เก็บคำเตือนทุกข้อความไว้สำหรับตรวจสอบภายหลัง

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**ทำไมจึงสำคัญ:** หากไม่มีการตั้งค่า callback คำเตือน Aspose.Words จะทำการแทนที่ฟอนต์ที่หายไปด้วยฟอนต์เริ่มต้นโดยอัตโนมัติและคุณจะไม่รู้ว่ามีปัญหาเกิดขึ้น การจับ `WarningType.FontSubstitution` ทำให้คุณมองเห็นข้อมูลทั้งหมด—ข้อมูลที่จำเป็นสำหรับการ **ตรวจจับฟอนต์** ที่ไม่มีบนเครื่องโฮสต์

ต่อไปเราจะเชื่อมคอลเลกเตอร์เข้ากับ `LoadOptions` แล้วโหลดเอกสาร:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **เคล็ดลับ:** หากคุณต้องประมวลผลเอกสารหลายไฟล์เป็นชุด ให้ใช้ `FontSubstitutionWarningCollector` ตัวเดียวกันซ้ำได้ แต่ต้องจำเรียก `Clear()` ระหว่างการโหลดแต่ละครั้งเพื่อหลีกเลี่ยงการผสานคำเตือนจากไฟล์ต่างกัน

---

## เก็บคำเตือนระหว่างการโหลดเอกสาร

หลังจากเอกสารถูกโหลด คอลเลกเตอร์จะมีคำเตือนที่เกี่ยวกับฟอนต์ทั้งหมดแล้ว คำถามต่อไปคือ: *ฉันจะเก็บคำเตือนอย่างไร* ให้สามารถบันทึกหรือแสดงผลได้ง่าย?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

ผลลัพธ์ที่พบบ่อยจะมีลักษณะเช่นนี้:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**สิ่งที่บอกคุณ:** แต่ละบรรทัดจะแสดงชื่อฟอนต์ต้นฉบับและฟอนต์สำรองที่ Aspose.Words เลือกใช้ ด้วยข้อมูลนี้คุณสามารถตัดสินใจได้ว่าการสำรองนั้นยอมรับได้หรือคุณต้องฝังฟอนต์ที่หายไปด้วยตนเอง

---

## จัดการฟอนต์ที่หายไปอย่างราบรื่น

การตรวจจับและเก็บคำเตือนเป็นเพียงครึ่งหนึ่งของการแก้ปัญหา คุณค่าที่แท้จริงคือการ **จัดการฟอนต์ที่หายไป** อย่างพร้อมใช้งานในสภาพแวดล้อมการผลิต ด้านล่างนี้คือสามกลยุทธ์ที่พบบ่อย:

1. **บันทึกและดำเนินต่อ** – เหมาะกับการประมวลผลเป็นชุดที่คุณแค่ต้องการบันทึกประวัติ  
2. **ยกเลิกเมื่อพบฟอนต์สำคัญ** – โยนข้อยกเว้นหากฟอนต์เฉพาะ (เช่น ฟอนต์แบรนด์) หายไป  
3. **ฝังฟอนต์แบบอัตโนมัติ** – โหลดฟอนต์ที่หายไปจากโฟลเดอร์ที่กำหนดและลงทะเบียนกับ Aspose.Words ก่อนโหลดเอกสารใหม่

### ตัวอย่าง: ยกเลิกเมื่อพบฟอนต์สำคัญ

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### ตัวอย่าง: ฝังฟอนต์ที่หายไปอัตโนมัติ

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**ทำไมรูปแบบเหล่านี้ถึงช่วยได้:** การกำหนดแนวทางอย่างชัดเจนเมื่อฟอนต์หายไป ช่วยขจัดการแทนที่โดยเงียบที่อาจทำให้แบรนด์หรือความอ่านง่ายเสียหาย นี่คือหัวใจของ **การจัดการฟอนต์ที่หายไป** อย่างมีการควบคุม

---

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมเดียวที่พร้อมรันซึ่งสาธิต **วิธีตรวจจับฟอนต์**, **วิธีเก็บคำเตือน**, และนโยบายง่าย ๆ เพื่อ **จัดการฟอนต์ที่หายไป** โดยบันทึกลงคอนโซล

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เมื่อคุณรันโปรแกรมกับเอกสารที่อ้างอิงฟอนต์ที่ไม่มีบนเครื่อง คอนโซลจะรายการคำเตือนการแทนที่แต่ละรายการ หากมีคำเตือนใดเกี่ยวกับฟอนต์จากชุด `critical` โปรแกรมจะหยุดทำงานก่อนสร้าง PDF ที่อาจมีข้อบกพร่อง

---

## คำถามที่พบบ่อย (FAQs)

| Question | Answer |
|----------|--------|
| *Do I need a license for Aspose.Words to use this code?* | Yes, a valid Aspose.Words license removes evaluation watermarks and unlocks full functionality. |
| *Can this approach detect embedded fonts?* | Embedded fonts are already part of the file, so Aspose.Words won’t raise a substitution warning. You can check `Document.FontInfos` to enumerate embedded fonts if needed. |
| *What if the missing font is a system font on Windows but not on Linux?* | The same warning will fire on Linux because the font isn’t installed there. Use the “handle missing fonts” strategy to ship the required `.ttf` files with your app. |
| *Is the warning collector thread | 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}