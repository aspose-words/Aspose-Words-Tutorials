---
category: general
date: 2026-03-17
description: วิธีตรวจจับฟอนต์ใน C# ด้วย Aspose.Words และการเรียกกลับคำเตือน เรียนรู้วิธีใช้
  callback เพื่อจับการแทนที่ฟอนต์ที่หายไปขณะโหลดเอกสาร.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: th
og_description: วิธีตรวจจับฟอนต์ใน C# ด้วย Aspose.Words คู่มือนี้แสดงวิธีใช้คอลแบ็กเพื่อจับคำเตือนฟอนต์ที่หายไปขณะโหลดเอกสาร
og_title: วิธีตรวจจับฟอนต์ใน C# – ใช้ Callback กับ Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: วิธีตรวจจับฟอนต์ใน C# – ใช้ Callback กับ Aspose.Words
url: /th/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตรวจจับฟอนต์ใน C# – ใช้ Callback กับ Aspose.Words

เคยต้องการ **วิธีตรวจจับฟอนต์** ในเอกสาร Word อย่างโปรแกรมเมติกและสงสัยว่าทำไมบางอักขระถึงดูแปลกหลังการแปลงหรือไม่? คุณไม่ได้อยู่คนเดียว ในหลายโครงการจริง—เช่น ตัวสร้างใบแจ้งหนี้, ตัวส่งออกรายงาน, หรือไพป์ไลน์การประมวลผลแบบแบตช์—ฟอนต์ที่หายไปทำให้เกิดข้อบกพร่องของเลย์เอาต์แบบเงียบที่ยากต่อการดีบัก  

ข่าวดีคือ Aspose.Words มีวิธีที่สะอาดในการเปิดเผยปัญหาเหล่านั้นผ่าน warning callback ในบทเรียนนี้คุณจะได้เห็น **วิธีใช้ callback** เพื่อจับการแทนที่ฟอนต์ทุกครั้งที่ Aspose ทำขณะโหลดเอกสาร และคุณจะได้ตัวอย่างที่พร้อมรันซึ่งพิมพ์รายงานชัดเจนของฟอนต์ที่หายไป

เราจะครอบคลุม:

* ความต้องการขั้นต่ำ (โครงการ .NET และแพคเกจ NuGet ของ Aspose.Words)  
* วิธีการทำ `IWarningCallback` เพื่อฟัง `WarningType.FontSubstitution`  
* วิธีเชื่อม callback เข้ากับ `LoadOptions` แล้วโหลดเอกสาร  
* ตัวอย่างผลลัพธ์ที่ได้ พร้อมเคล็ดลับการใช้งานจริงสำหรับโค้ดในโปรดักชัน

เมื่อเสร็จสิ้น คุณจะสามารถ **ตรวจจับฟอนต์** ในไฟล์ DOCX, DOC หรือ RTF ใดก็ได้โดยอัตโนมัติและทำสิ่งที่ต้องการกับข้อมูลฟอนต์ที่หายไป—ไม่ว่าจะเป็นการบันทึก, แจ้งผู้ใช้, หรือแทนที่ด้วยฟอนต์สำรอง

---

![วิธีตรวจจับฟอนต์ในเอกสาร Word ด้วย Aspose.Words warning callback](https://example.com/images/detect-fonts.png "วิธีตรวจจับฟอนต์ในเอกสาร Word")

## สิ่งที่คุณต้องการ

* **.NET 6.0** หรือใหม่กว่า (ตัวอย่างนี้ยังคอมไพล์ได้กับ .NET Framework 4.6+)  
* **Aspose.Words for .NET** – ติดตั้งผ่าน NuGet: `Install-Package Aspose.Words`  
* ไฟล์ Word ตัวอย่างที่อ้างอิงฟอนต์ที่คุณไม่มีติดตั้ง (เช่น `MissingFont.docx`)  

ไม่ต้องใช้ไลบรารีเพิ่มเติม; ทุกอย่างอยู่ใน namespace ของ Aspose

---

## วิธีตรวจจับฟอนต์ด้วย Warning Callback

### ขั้นตอนที่ 1: สร้างคลาส warning‑callback

คลาสนี้ทำการ implement `IWarningCallback` เมื่อ Aspose.Words พบฟอนต์ที่ไม่พบ มันจะปล่อย `WarningInfo` พร้อม `WarningType.FontSubstitution` คลาสของเราจะเขียนข้อความที่เป็นมิตรลงคอนโซล

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**ทำไมเรื่องนี้สำคัญ:** การกรองด้วย `WarningType.FontSubstitution` จะช่วยหลีกเลี่ยง warning ที่ไม่เกี่ยวข้อง (เช่น ฟีเจอร์ที่ล้าสมัย) ทำให้บันทึกโฟกัสที่ปัญหาที่คุณต้องการแก้—**การตรวจจับฟอนต์** ที่ไม่มีอยู่บนเครื่อง

---

### ขั้นตอนที่ 2: เชื่อม callback เข้ากับ `LoadOptions`

`LoadOptions` ให้คุณปรับแต่งวิธีการพาร์สเอกสาร การกำหนด `FontWarningCollector` ของเราให้กับ property `WarningCallback` จะบอก Aspose ให้เรียกใช้เมื่อพบฟอนต์ที่หายไป

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**เคล็ดลับ:** คุณยังสามารถตั้งค่า `LoadOptions.FontSettings` ที่นี่เพื่อระบุฟอนต์สำรองโดยโปรแกรม นี่เป็นสถานการณ์ขั้นสูงที่เราจะพูดถึงต่อไป

---

### ขั้นตอนที่ 3: โหลดเอกสารและดูผลลัพธ์

ตอนนี้เราจะโหลดไฟล์จริง เมื่อ Aspose พาร์สเอกสาร ฟอนต์ที่ไม่พบใด ๆ จะทำให้ callback ของเราถูกเรียก

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล** (สมมติว่าเอกสารอ้างอิง *Comic Sans MS* ซึ่งไม่ได้ติดตั้ง):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

หากเอกสารมีฟอนต์ที่หายไปหลายตัว คุณจะเห็นบรรทัดหนึ่งต่อฟอนต์—ข้อมูล **วิธีตรวจจับฟอนต์** ที่คุณต้องการอย่างแม่นยำ

---

## วิธีใช้ Callback สำหรับสถานการณ์ที่ซับซ้อนกว่า

### บันทึกลงไฟล์แทนคอนโซล

ในโปรดักชันคุณอาจต้องการบันทึกแบบถาวร แทนที่ `Console.WriteLine` ด้วย `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### เก็บ warning เพื่อนำไปวิเคราะห์ภายหลัง

บางครั้งคุณต้องการรายการฟอนต์ที่หายไปหลังจากโหลดเอกสารแล้ว เพื่อนำไปแสดงใน UI เก็บ warning ไว้ใน `List<string>` แล้วเปิดให้เข้าถึง:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### ให้ฟอนต์สำรองโดยโปรแกรม

ถ้าคุณมีฟอนต์ของบริษัทที่ต้องการบังคับใช้ สามารถเพิ่มเข้าไปใน `FontSettings` ก่อนโหลด:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

ตอนนี้ Aspose จะแทนที่ฟอนต์ที่หายไปด้วย *Arial Unicode MS* พร้อมยังคงรายงานการแทนที่ผ่าน callback วิธีนี้เป็นวิธีที่ดีในการ **ใช้ callback** ทั้งสำหรับการตรวจจับและการแก้ไขอัตโนมัติ

---

## ข้อผิดพลาดทั่วไปและเคล็ดลับระดับมืออาชีพ

| ข้อผิดพลาด | สาเหตุ | วิธีหลีกเลี่ยง |
|------------|--------|----------------|
| **ลืมอ้างอิง `Aspose.Words.Warnings`** | อินเทอร์เฟซ `IWarningCallback` อยู่ในนั้น | เพิ่ม `using Aspose.Words.Warnings;` ที่ส่วนหัว |
| **โหลดเอกสารโดยไม่ใช้ `LoadOptions`** | ตัวโหลดเริ่มต้นแทนที่ฟอนต์โดยเงียบโดยไม่มีการแจ้งเตือน | สร้างอินสแตนซ์ `LoadOptions` เสมอและกำหนด callback ของคุณ |
| **รันบนเซิร์ฟเวอร์ที่มีสิทธิ์จำกัด** | การเขียนไฟล์ล็อกอาจทำให้เกิด `UnauthorizedAccessException` | ใช้โฟลเดอร์ที่เขียนได้ (เช่น โฟลเดอร์ข้อมูลของแอป) หรือใช้คอลเลกชันในหน่วยความจำ |
| **หลายเธรดแชร์ collector เดียว** | `FontWarningCollector` ไม่ได้ออกแบบให้ thread‑safe | สร้าง collector แยกสำหรับแต่ละเธรดหรือปกป้องรายการด้วย lock |
| **สมมติว่า callback ทำงานกับฟอนต์ที่ฝังอยู่** | ฟอนต์ที่ฝังอยู่แล้วอยู่ในเอกสาร จึงไม่มี warning | หากต้องการตรวจสอบความสมบูรณ์ของฟอนต์ที่ฝัง ให้ตรวจสอบ `FontInfo` ผ่าน `FontSettings` |

---

## ตัวอย่างทำงานเต็มรูปแบบ (คัดลอก‑วางได้)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**สิ่งที่คุณควรเห็น** (สมมติว่าไฟล์อ้างอิงฟอนต์ที่หายไปสองตัว):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

หากไฟล์ใช้ฟอนต์ที่ติดตั้งแล้ว คอนโซลจะพิมพ์เพียง:

```
Document loaded successfully.

No missing fonts detected.
```

---

## สรุป

เราได้อธิบาย **วิธีตรวจจับฟอนต์** ในเอกสาร Word โดยการเชื่อมต่อ warning callback แบบกำหนดเองเข้ากับ Aspose.Words วิธีนี้เบา, ต้องการเพียง

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}