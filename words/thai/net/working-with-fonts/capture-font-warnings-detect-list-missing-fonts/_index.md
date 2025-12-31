---
category: general
date: 2025-12-31
description: บันทึกคำเตือนฟอนต์ใน Aspose.Words เพื่อค้นหาและระบุฟอนต์ที่หายไป พร้อมแสดงรายการฟอนต์ที่ขาดหายในแอป
  .NET ของคุณ เรียนรู้วิธีแก้ปัญหา C# ทีละขั้นตอน.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: th
og_description: บันทึกคำเตือนฟอนต์ใน Aspose.Words เพื่อตรวจจับฟอนต์ที่หายไปและแสดงรายการฟอนต์ที่หายไป
  คู่มือ C# ฉบับเต็มพร้อมโค้ดและเคล็ดลับ
og_title: บันทึกคำเตือนฟอนต์ – ตรวจจับและแสดงรายการฟอนต์ที่หายไป
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: บันทึกคำเตือนฟอนต์ – ตรวจจับและแสดงรายการฟอนต์ที่หายไป
url: /th/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# จับคำเตือนฟอนต์ – ตรวจจับและแสดงรายการฟอนต์ที่หายไป

เคยต้อง **จับคำเตือนฟอนต์** ขณะโหลดไฟล์ Word แต่ไม่แน่ใจว่าจะดึงรายละเอียดฟอนต์ที่หายไปอย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายโครงการจริง ๆ ฟอนต์ที่หายไปทำให้รูปแบบหน้าตาเสียหาย และหากไม่มีคำเตือนที่เหมาะสม คุณก็ต้องไล่ตามบั๊กที่มองไม่เห็น  

ในบทแนะนำนี้ เราจะสาธิตวิธี **ตรวจจับฟอนต์ที่หายไป** และ **แสดงรายการฟอนต์ที่หายไป** ด้วย Aspose.Words for .NET. เมื่อจบคุณจะได้โค้ด C# ที่พร้อมรันซึ่งพิมพ์คำเตือนการแทนที่ทุกรายการ เพื่อให้คุณสามารถบันทึก, แจ้งเตือน, หรือแม้แต่แทนที่ฟอนต์โดยอัตโนมัติได้

---

## ทำไมการจับคำเตือนฟอนต์จึงสำคัญ

เมื่อ Aspose.Words เปิดไฟล์ DOCX ที่อ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์ มันจะทำการแทนที่ด้วยฟอนต์สำรองโดยอัตโนมัติ เอกสารอาจดูเหมือนปกติ แต่ความเที่ยงตรงของการแสดงผลจะเสียหาย — เช่น โลโก้แบรนด์บริษัทที่แสดงด้วยแบบอักษรผิด  

การจับคำเตือนเหล่านี้ทำให้คุณสามารถ:

* **รักษาความสอดคล้องของแบรนด์** – รู้ได้ว่าฟอนต์ใดบ้างที่หายไป
* **อัตโนมัติการแก้ไข** – แทนที่ฟอนต์ที่หายไปด้วยโปรแกรม
* **ตรวจสอบการปฏิบัติตาม** – สร้างรายงานสำหรับการตรวจสอบด้านกฎหมายหรือการออกแบบ

สรุปแล้ว, **การจับคำเตือนฟอนต์** คือแนวป้องกันแรกต่อการแทนที่ฟอนต์โดยเงียบ ๆ

---

## ตั้งค่า LoadOptions เพื่อตรวจจับฟอนต์ที่หายไป

กุญแจสำคัญในการแสดงคำเตือนคือคุณสมบัติ `LoadOptions.FontSubstitutionWarning`. ค่าเริ่มต้นคือ `None` ซึ่งหมายความว่า Aspose.Words จะละเลยข้อความเหล่านั้น การเปลี่ยนเป็น `All` จะบอกไลบรารีให้บันทึกเหตุการณ์การแทนที่ทุกครั้ง

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **เคล็ดลับ:** หากคุณมีโฟลเดอร์ฟอนต์แบบกำหนดเอง ให้กำหนดให้กับ `FontSettings.SetFontsFolder("path")` ก่อนโหลดเอกสาร วิธีนี้จะช่วยให้คุณ **ตรวจจับฟอนต์ที่หายไป** ที่ไม่ได้อยู่ในไดเรกทอรีระบบ

---

## โหลดเอกสารและแสดงรายการฟอนต์ที่หายไป

เมื่อ `LoadOptions` พร้อมแล้ว ขั้นตอนต่อไปคือการโหลดไฟล์ Word ตัวสร้างรับอ็อบเจกต์ตัวเลือก และการแทนที่ใด ๆ จะถูกบันทึกไว้ใน `WarningInfoCollection` ของเอกสาร

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

หากไฟล์อ้างอิงฟอนต์ที่ไม่มีอยู่, ฟอนต์แต่ละตัวที่หายไปจะสร้างรายการ `WarningInfo`. คุณสามารถ **แสดงรายการฟอนต์ที่หายไป** ได้โดยวนลูปผ่านคอลเลกชันนั้น

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

ผลลัพธ์ที่คาดว่าจะเป็นเช่นนี้:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

แต่ละบรรทัดบอกคุณอย่างชัดเจนว่าฟอนต์ใดหายไป, ตรงตามความต้องการของ **แสดงรายการฟอนต์ที่หายไป**

---

## อ่านและตีความ WarningInfoCollection

`WarningInfoCollection` อาจมีประเภทคำเตือนต่าง ๆ (เช่น `DocumentStructure`, `ImageLoading`). เพื่อโฟกัสเฉพาะปัญหาฟอนต์ ให้กรองโดย `WarningType.FontSubstitution`

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

ทำไมต้องกรอง? เพราะเอกสารขนาดใหญ่บางครั้งอาจสร้างคำเตือนเกี่ยวกับรูปภาพเสียหายหรือฟีเจอร์ที่ไม่รองรับ การจำกัดคอลเลกชันช่วยลดสัญญาณรบกวนและทำให้ผลลัพธ์ของ **การจับคำเตือนฟอนต์** สะอาดขึ้น

---

## ตัวอย่างเต็มที่ทำงาน – การจับคำเตือนฟอนต์ในเชิงปฏิบัติ

ด้านล่างเป็นโปรแกรมที่สมบูรณ์และพร้อมใช้งาน ซึ่งคุณสามารถใส่ลงในโปรเจกต์คอนโซล .NET ใดก็ได้ มันสาธิตทุกขั้นตอนตั้งแต่การกำหนดค่า `LoadOptions` จนถึงการพิมพ์รายการฟอนต์ที่หายไปอย่างเป็นระเบียบ

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**ผลลัพธ์ที่คาดว่าจะเห็นบนคอนโซล**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

หากเอกสารไม่มีฟอนต์ที่หายไป คุณจะเห็น:

```
All referenced fonts are available – no warnings captured.
```

---

## กรณีขอบเขตทั่วไป & วิธีจัดการ

| สถานการณ์ | สาเหตุ | วิธีแก้แนะนำ |
|-----------|--------|--------------|
| **เอกสารใช้ฟอนต์ OpenType ที่ฝังไว้** | Aspose.Words สามารถอ่านฟอนต์ที่ฝังได้ แต่เฉพาะเมื่อไฟล์ไม่เสีย | ตรวจสอบ DOCX ด้วย Word ก่อน; ฝังฟอนต์ใหม่หากจำเป็น |
| **จำนวนคำเตือนมาก** (เช่น 200+ ฟอนต์ที่หาย) | การนำเข้าจำนวนมากจากระบบเก่ามักอ้างอิงพาเลตฟอนต์กว้าง | ประมวลผลคำเตือนเป็นชุด: เก็บลงฐานข้อมูล แล้วรันสคริปต์ติดตั้งฟอนต์ |
| **WarningInfoCollection ว่างเปล่า** | หรือเอกสารมีฟอนต์ครบ, หรือ `FontSubstitutionWarning` ตั้งเป็น `None` | ตรวจสอบการตั้งค่า `LoadOptions` อีกครั้งและยืนยันว่าโหลดไฟล์จากพาธที่ถูกต้อง |
| **ฟอนต์กำหนดเองอยู่บนแชร์เครือข่าย** | ความหน่วงของเครือข่ายอาจทำให้หมดเวลาในระหว่างการค้นหา | โหลดฟอนต์ล่วงหน้าเข้าสู่ `FontSettings` ด้วย `SetFontsFolder` และตั้งค่า `CacheFontData = true` |

เคล็ดลับเหล่านี้ช่วยให้คุณ **ตรวจจับฟอนต์ที่หายไป** อย่างเชื่อถือได้ แม้ในสภาพแวดล้อมที่ซับซ้อน

---

## ภาพประกอบ

![ตัวอย่างการจับคำเตือนฟอนต์](https://example.com/images/capture-font-warnings.png "ตัวอย่างการจับคำเตือนฟอนต์")

*ภาพหน้าจอแสดงการรันคอนโซลที่รายงานฟอนต์ที่หายไปสองตัว*

---

## ขั้นตอนต่อไป – ไปไกลกว่าแค่การรายงานง่าย ๆ

เมื่อคุณสามารถ **จับคำเตือนฟอนต์** แล้ว ลองพิจารณาการอัตโนมัติการแก้ไข:

1. **การแทนที่ฟอนต์อัตโนมัติ** – แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรองที่บริษัทอนุมัติโดยแก้ไข `FontSettings.SubstitutionSettings`
2. **บันทึกลงระบบมอนิเตอร์** – ส่งข้อความคำเตือนไปยัง Serilog, ELK, หรือ Azure Application Insights
3. **รายงานให้ผู้ใช้** – สร้างสรุปเป็น HTML หรือ PDF ให้ดีไซเนอร์ตรวจสอบว่าฟอนต์ใดต้องติดตั้ง

ส่วนขยายทั้งหมดนี้อิงจากพื้นฐานเดียวกันที่เราได้อธิบายไว้: การกำหนดค่า `LoadOptions`, การโหลดเอกสาร, และการอ่าน `WarningInfoCollection`

---

## สรุป

คุณได้เรียนรู้วิธี **จับคำเตือนฟอนต์** ใน Aspose.Words, **ตรวจจับฟอนต์ที่หายไป**, และ **แสดงรายการฟอนต์ที่หายไป** ด้วยผลลัพธ์ที่เรียบง่ายบนคอนโซล วิธีนี้ตรงไปตรงมา ใช้เพียงไม่กี่บรรทัดของ C# และทำงานกับ .NET เวอร์ชันใดก็ได้ที่รองรับ Aspose.Words 23.x หรือใหม่กว่า  

ลองใช้กับไฟล์ DOCX ตัวอย่างที่อ้างอิงฟอนต์ที่คุณลบออกโดยเจตนา – คุณจะเห็นคำเตือนปรากฏทันที จากนั้นคุณสามารถตัดสินใจว่าจะติดตั้งฟอนต์ที่หายไป, แทนที่โดยโปรแกรม, หรือเพียงบันทึกปัญหาเพื่อทบทวนในภายหลัง  

ขอให้เขียนโค้ดสนุกและเอกสารของคุณแสดงผลด้วยฟอนต์ที่ถูกต้องเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}