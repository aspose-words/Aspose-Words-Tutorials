---
category: general
date: 2026-03-06
description: บันทึกคำเตือนฟอนต์ขณะโหลดเอกสาร Word ด้วย C# เรียนรู้วิธีตรวจจับฟอนต์ที่หายไป,
  ตรวจสอบฟอนต์ในเอกสาร, และจัดการฟอนต์ที่หายไปอย่างมีประสิทธิภาพ.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: th
og_description: จับคำเตือนฟอนต์ขณะโหลดเอกสาร Word ด้วย C# บทเรียนนี้แสดงวิธีตรวจจับฟอนต์ที่หายไป,
  ตรวจสอบฟอนต์ของเอกสาร, และจัดการกับฟอนต์ที่หายไป.
og_title: บันทึกคำเตือนฟอนต์ใน C# – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Font Management
title: จับคำเตือนฟอนต์ใน C# – คู่มือฉบับสมบูรณ์
url: /th/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# จับคำเตือนฟอนต์ใน C# – คู่มือฉบับสมบูรณ์

เคยต้อง **จับคำเตือนฟอนต์** ขณะประมวลผลเอกสาร Word หรือไม่? การจับคำเตือนฟอนต์เป็นสิ่งสำคัญเพื่อ **ตรวจจับฟอนต์ที่หายไป** และทำให้แน่ใจว่าผลลัพธ์สุดท้ายดูเหมือนที่คุณต้องการ  

ในบทเรียนนี้เราจะเดินผ่านตัวอย่างเชิงปฏิบัติแบบครบวงจร ที่โหลดไฟล์ `.docx` ตรวจสอบกระบวนการโหลด และรายงานการแทนที่ฟอนต์ใด ๆ ที่เกิดขึ้น เมื่อเสร็จแล้วคุณจะรู้วิธี **โหลดเอกสาร Word** อย่างปลอดภัย, **ตรวจสอบฟอนต์ของเอกสาร**, และ **จัดการกับฟอนต์ที่หายไป** โดยไม่เกิดข้อผิดพลาดขณะรัน

## สิ่งที่คุณจะได้เรียนรู้

- วิธีแนบตัวเก็บคำเตือนให้กับ `Document` ของ Aspose.Words
- ประเภทคำเตือนใดบ่งบอกถึงฟอนต์ที่หายไปหรือถูกแทนที่
- วิธีบันทึกหรือทำการตอบสนองต่อคำเตือนเหล่านั้นในแอประดับผลิตภัณฑ์
- เคล็ดลับการกำหนดแหล่งฟอนต์แบบกำหนดเอง หากคุณต้องการ **จัดการฟอนต์ที่หายไป** อย่างราบรื่น

> **ข้อกำหนดเบื้องต้น:** คุณมีไลเซนส์ Aspose.Words for .NET ที่ถูกต้อง (หรือกำลังใช้รุ่นทดลองฟรี) และมีสภาพแวดล้อมการพัฒนา .NET (Visual Studio, Rider หรือ VS Code) ไม่ต้องใช้ไลบรารีอื่นใด

---

## จับคำเตือนฟอนต์ – ขั้นตอนโดยละเอียด

ด้านล่างเป็นโค้ดเต็มที่สามารถรันได้ แต่ละส่วนถูกแยกออกเป็นขั้นตอนเพื่อให้คุณคัดลอก‑วาง, ทดลอง, และขยายตรรกะได้ง่าย

![Capture font warnings diagram](image.png "Diagram showing warning collection"){: alt="แผนภาพการจับคำเตือนฟอนต์"}

### ขั้นตอนที่ 1: โหลดเอกสาร Word

ก่อนอื่นเราต้อง **โหลดเอกสาร Word** ที่อาจมีฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องปัจจุบัน ตัวสร้าง `Document` ทำงานหนักส่วนนี้ไว้แล้ว แต่เราจะแยกการเรียกใช้ไว้เพื่อให้คุณสามารถสลับเป็นสตรีมหรืออาร์เรย์ไบต์ในภายหลังได้หากต้องการ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**ทำไมจึงสำคัญ:** การโหลดเอกสารโดยไม่มีตัวจัดการคำเตือนหมายความว่าการแทนที่ฟอนต์ใด ๆ จะถูกละเลยโดยเงียบ ๆ การตั้งค่า `WarningCallback` *ก่อน* การโหลดทำให้เรามั่นใจว่าจะเห็นคำเตือน `FontSubstitution` ทุกครั้งที่เกิดขึ้น

### ขั้นตอนที่ 2: แนบตัวเก็บคำเตือน

คลาส `WarningInfoCollector` เป็นการนำเสนอที่สร้างไว้แล้วของ `IWarningCallback` มันเพียงแค่เก็บคำเตือนแต่ละรายการในรายการที่เราสามารถตรวจสอบได้ภายหลัง

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**เคล็ดลับระดับมืออาชีพ:** หากคุณต้องการ **จัดการฟอนต์ที่หายไป** อย่างเข้มข้น (เช่น ยกเลิกการโหลดหรือแทนที่ด้วยฟอนต์สำรองเฉพาะ) คุณสามารถเปลี่ยน `Console.WriteLine` เป็นตรรกะของคุณเอง — โยนข้อยกเว้น, บันทึกลงไฟล์, หรือแม้แต่เพิ่มแหล่งฟอนต์แบบกำหนดเอง

### ขั้นตอนที่ 3: ตรวจสอบผลลัพธ์

รันโปรแกรมจากคอนโซล หาก `input.docx` ของคุณใช้ฟอนต์ที่ไม่ได้ติดตั้ง คุณจะเห็นบรรทัดเช่น

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

หากไม่มีการแสดงผลใด ๆ แสดงว่าเอกสารใช้ฟอนต์ที่มีอยู่แล้ว **หรือ** Aspose.Words พบฟอนต์ที่ตรงกันในคอลเลกชันสำรองที่สร้างไว้โดยอัตโนมัติ ไม่ว่าอย่างไรก็ตาม คุณได้ **ตรวจสอบฟอนต์ของเอกสาร** สำเร็จแล้ว

---

## ตรวจจับฟอนต์ที่หายไปโดยไม่ต้องมีไลเซนส์ (รุ่นทดลองฟรี)

แม้คุณจะใช้รุ่นทดลอง 30‑วัน กลไกการแจ้งคำเตือนทำงานเหมือนเดิม ความแตกต่างเพียงอย่างเดียวคือรุ่นทดลองจะใส่น้ำหนักบนผลลัพธ์ที่สร้างขึ้น ซึ่ง **ไม่** มีผลต่อการเก็บคำเตือน ดังนั้นคุณสามารถ **ตรวจจับฟอนต์ที่หายไป** อย่างปลอดภัยก่อนตัดสินใจซื้อไลเซนส์เต็ม

---

## จัดการฟอนต์ที่หายไป – ตัวเลือกขั้นสูง

บางครั้งคุณอาจต้องการให้ไฟล์ฟอนต์ของคุณเอง (เช่น ฟอนต์แบรนด์ของบริษัท) เพื่อให้การแทนที่ไม่เกิดขึ้น Aspose.Words ให้คุณลงทะเบียนโฟลเดอร์ฟอนต์แบบกำหนดเองได้:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

วางโค้ดข้างต้น **ก่อน** โหลดเอกสาร หากคุณต้องการให้ตัวโหลดพิจารณาฟอนต์เหล่านั้นในขั้นตอนการพาร์สเริ่มต้น นี่เป็นวิธีที่เชื่อถือได้ที่สุดในการ **จัดการฟอนต์ที่หายไป** โดยไม่ต้องพึ่งพาฟอนต์ระบบเริ่มต้น

---

## ข้อผิดพลาดทั่วไป & วิธีหลีกเลี่ยง

| ปัญหา | สาเหตุ | วิธีแก้ |
|---------|----------------|-----|
| **แนบตัวเก็บคำเตือนหลังจากโหลด** | เอกสารถูกพาร์สแล้ว จึงไม่มีการบันทึกคำเตือน | แนบ `WarningCallback` **ก่อน** เรียก `new Document(path)` |
| **เห็นคำเตือนทั่วไปเท่านั้น** | กรองด้วย `WarningType` ผิดประเภท | ใช้ `WarningType.FontSubstitution` เพื่อโฟกัสที่ปัญหาฟอนต์ |
| **ไม่มีผลลัพธ์แม้ฟอนต์หายไป** | Aspose.Words พบฟอนต์สำรองในตัว (เช่น Arial) | ปิดฟอนต์สำรองในตัวโดย `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **ประสิทธิภาพลดลงเมื่อสแกนเอกสารขนาดใหญ่** | การเก็บทุกคำเตือนอาจใช้ทรัพยากรมาก | จำกัดการเก็บไว้เฉพาะ `FontSubstitution` เท่านั้น หรือประมวลผลคำเตือนเป็นชุด |

---

## ตัวอย่างทำงานเต็มรูปแบบ (พร้อมคัดลอก‑วาง)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**ผลลัพธ์คอนโซลที่คาดหวัง** (สมมติว่ามีฟอนต์หายไปสองตัว):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

หากคอนโซลเงียบยกเว้นข้อความ “Document loaded successfully” แสดงว่าคุณได้ **ตรวจสอบฟอนต์ของเอกสาร** แล้วและไม่พบฟอนต์ที่หายไป

---

## สรุป

เราได้แสดงวิธี **จับคำเตือนฟอนต์** ใน C# ด้วย Aspose.Words ซึ่งเป็นวิธีที่เชื่อถือได้ในการ **ตรวจจับฟอนต์ที่หายไป**, **โหลดเอกสาร Word** อย่างปลอดภัย, **ตรวจสอบฟอนต์ของเอกสาร**, และ **จัดการฟอนต์ที่หายไป** ผ่านแหล่งฟอนต์แบบกำหนดเอง  

ด้วยรูปแบบนี้คุณสามารถผสานการตรวจสอบฟอนต์เข้าไปในไพพ์ไลน์อัตโนมัติใด ๆ — ไม่ว่าจะเป็นการสร้าง PDF, แปลงเป็น HTML, หรือเพียงเก็บสำเนาเอกสาร Word

### ขั้นตอนต่อไปคืออะไร?

- สำรวจ API **FontSettings.SubstitutionSettings** เพื่อกำหนดกฎสำรองของคุณเอง
- ผสานการเก็บคำเตือนกับเฟรมเวิร์กบันทึก (Serilog, NLog) เพื่อการเฝ้าระวังในระดับผลิตภัณฑ์
- ใช้แนวทางเดียวกันเพื่อจับประเภทคำเตือนอื่น ๆ เช่น ความละเอียดภาพหรือฟีเจอร์ที่ไม่รองรับ

มีคำถามเพิ่มเติมเกี่ยวกับการจัดการฟอนต์หรือ Aspose.Words โดยทั่วไป? แสดงความคิดเห็นหรือเข้าร่วมฟอรั่มชุมชนของ Aspose ได้เลย ขอให้เขียนโค้ดสนุก ๆ และขอให้เอกสารของคุณแสดงผลด้วยฟอนต์ที่คุณคาดหวังเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}