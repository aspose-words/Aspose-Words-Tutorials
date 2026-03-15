---
category: general
date: 2026-03-14
description: จัดการฟอนต์ที่หายอย่างรวดเร็วด้วย Aspose.Words เรียนรู้วิธีจับคำเตือนการแทนที่ฟอนต์
  กำหนดค่า LoadOptions และหลีกเลี่ยงปัญหาการแสดงผล.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: th
og_description: จัดการฟอนต์ที่หายไปใน Aspose.Words ด้วยตัวเก็บคำเตือน บทเรียนนี้แสดงขั้นตอนโดยละเอียดว่าตรวจจับและบันทึกการแทนที่ฟอนต์อย่างไร
og_title: จัดการฟอนต์ที่หายไปใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: จัดการฟอนต์ที่หายไปใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
url: /th/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# จัดการฟอนต์ที่หายไปใน Aspose.Words – คำแนะนำเต็มสำหรับ C#

เคยต้อง **จัดการฟอนต์ที่หายไป** ขณะโหลดเอกสาร Word แล้วสงสัยทำไมไฟล์ PDF หรือรูปภาพที่ได้ดูแปลกไหม? คุณไม่ได้เป็นคนเดียว ฟอนต์ที่ขาดหายไปเป็นปัญหาเงียบที่สามารถทำให้รายงานที่ออกแบบอย่างดีกลายเป็นแปดเปื้อนได้  

ข่าวดีคือ Aspose.Words มีวิธีที่สะอาดตาในการดักจับเหตุการณ์การแทนที่ฟอนต์, บันทึกลงล็อก, และแม้แต่สลับไปใช้ฟอนต์สำรองได้ หากต้องการ ในบทแนะนำนี้เราจะเดินผ่านตัวอย่างที่พร้อมรันเต็มรูปแบบซึ่งแสดงให้เห็นวิธีตั้งค่า warnings collector, ผูกเข้ากับ `LoadOptions`, และโหลดเอกสารที่อาจมีฟอนต์หายไป

เมื่ออ่านจบคุณจะสามารถ:

* ตรวจจับการแทนที่ฟอนต์ทุกครั้งที่เกิดขึ้นระหว่างการโหลดเอกสาร  
* แสดงข้อความที่เป็นมิตรบนคอนโซล (หรือส่งต่อไปยัง logger) สำหรับฟอนต์ที่หายไปแต่ละตัว  
* ขยายวิธีแก้เพื่อเปลี่ยนฟอนต์ได้ หากต้องการ  

**ข้อกำหนดเบื้องต้น** – คุณจะต้องมี:

* .NET 6.0 หรือใหม่กว่า (โค้ดทำงานได้กับ .NET Core และ .NET Framework ด้วย)  
* แพคเกจ NuGet Aspose.Words for .NET (เวอร์ชันปัจจุบัน 23.11)  
* ไฟล์ Word ที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้ง – เราจะตั้งชื่อว่า `doc-with-missing-font.docx`  

ถ้าคุณคุ้นเคยกับ C# แล้วมีโปรเจกต์ตั้งไว้แล้ว สามารถข้ามไปยังโค้ดได้เลย หากยังไม่พร้อม ให้อ่านต่อไป เราจะครอบคลุมขั้นตอนการตั้งค่าเล็ก ๆ ก่อนเริ่ม

---

## ทำไมการจัดการฟอนต์ที่หายไปถึงสำคัญ

เมื่อ Aspose.Words โหลดเอกสาร มันพยายามจับคู่ glyph แต่ละตัวกับฟอนต์ที่ติดตั้งบนเครื่อง หากไม่พบฟอนต์ที่ตรงกัน มันจะทำการแทนที่ด้วยฟอนต์ที่ใกล้เคียงที่สุดโดยเงียบ ๆ การแทนที่นี้อาจทำให้ความสูงของบรรทัด, การเคอร์นิง, หรือแม้แต่ตัวอักษรหายไป การดักจับเหตุการณ์ `WarningType.FontSubstitution` จะให้มุมมองที่โปร่งใสว่า **อะไร** ถูกแทนที่และ **ทำไม** ซึ่งจำเป็นสำหรับ:

* รักษาความสอดคล้องของแบรนด์ (ฟอนต์ของบริษัทต้องแสดงตามที่ออกแบบ)  
* แก้ไขปัญหาการแปลงเป็น PDF — บ่อยครั้งสาเหตุคือฟอนต์หายไป  
* สร้าง pipeline เอกสารอัตโนมัติที่ต้องการทำเครื่องหมายไฟล์ที่มีปัญหาเพื่อการตรวจสอบด้วยมือ  

เมื่อ “ทำไม” ชัดเจนแล้ว ไปดู **วิธี** กันต่อ

---

## ขั้นตอน 1 – ตั้งค่า Warnings Collector

สิ่งแรกที่ต้องมีคืออ็อบเจ็กต์ที่สามารถฟังคำเตือนจาก Aspose.Words ได้ `DocumentWarnings` implements `IWarningCallback` ทำให้เราตอบสนองเมื่อไลบรารีส่งคำเตือน

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**กำลังเกิดอะไรขึ้น?**  
* `DocumentWarnings` เป็น wrapper ที่บางเบารอบอินเทอร์เฟซ callback  
* Lambda ตรวจสอบ `e.WarningType` เพื่อข้ามคำเตือนที่ไม่เกี่ยวข้อง (เช่นฟีเจอร์ที่เลิกใช้)  
* `e.WarningInfo` มีชื่อฟอนต์ที่หายไป เราจึงพิมพ์ลงคอนโซล  

*เคล็ดลับ*: แทนที่ `Console.WriteLine` ด้วย logger ที่มีโครงสร้าง (Serilog, NLog) ในสภาพแวดล้อมจริง — จะได้ timestamp และระดับล็อกโดยอัตโนมัติ

---

## ขั้นตอน 2 – ผูก Collector เข้ากับ LoadOptions

`LoadOptions` คือประตูสู่การเปิดเอกสารทุกไฟล์ด้วย Aspose.Words การกำหนดอินสแตนซ์ `fontWarnings` ของเราให้กับ property `WarningCallback` จะทำให้ collector ทำงานระหว่างกระบวนการโหลด

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**ทำไมต้องใช้ LoadOptions?**  
นอกจากคำเตือนแล้ว `LoadOptions` ยังให้คุณควบคุมการจัดการรหัสผ่าน, การเข้ารหัส, และแม้แต่การโหลดทรัพยากรแบบกำหนดเอง ที่นี่เรามุ่งเน้นที่ด้านคำเตือน แต่รูปแบบเดียวกันใช้ได้กับ callback อื่น ๆ ด้วย

---

## ขั้นตอน 3 – โหลดเอกสารด้วย Options ที่ตั้งค่าแล้ว

ตอนนี้เรานำเอกสารเข้าหน่วยความจำ หากมีฟอนต์ใดหายไป collector ของเราจะทำงานและคุณจะเห็นบรรทัดคอนโซลสำหรับแต่ละการแทนที่

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

หากคุณรันสคริปต์นี้กับเอกสารที่อ้างอิง *Calibri Light* แต่เครื่องทดสอบของคุณมีแค่ *Calibri* เท่านั้น คุณจะได้ผลลัพธ์คล้ายกับ:

```
Font 'Calibri Light' was substituted.
```

นี่คือวงจรการตรวจจับทั้งหมด — เรียบง่ายแต่ทรงพลัง

---

## ขั้นตอน 4 – (ทางเลือก) แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรองที่รู้จัก

บางครั้งคุณไม่ต้องการแค่บันทึกปัญหา แต่ต้องการบังคับใช้ฟอนต์สำรองเพื่อให้ผลลัพธ์ที่แสดงออกมามีความสอดคล้อง Aspose.Words ให้คุณกำหนด `FontSettings` ที่แมพฟอนต์ที่หายไปไปยังฟอนต์ทดแทน

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**คำอธิบาย**  
* วายด์การ์ด `"*"` บอก Aspose.Words ให้จัดการกับ *ฟอนต์ใด ๆ* ที่หายไปในลักษณะเดียวกัน  
* คุณยังสามารถแมพฟอนต์เฉพาะเจาะจงได้หากต้องการควบคุมระดับละเอียด  
* หลังจากตั้งค่า `document.FontSettings` การเรนเดอร์ต่อไป (PDF, image, HTML) จะเคารพการแทนที่นี้

---

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงใน console app ได้ รวม `using` ที่จำเป็น, การจัดการข้อผิดพลาด, และคอมเมนต์เพื่อความชัดเจน

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (เมื่อพบฟอนต์ที่หายไป):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

หากเอกสารต้นทางมีฟอนต์ครบทั้งหมด บรรทัดคำเตือนจะไม่ปรากฏ — ไม่มีอะไรต้องกังวล

---

## คำถามที่พบบ่อย & กรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ถ้าฉันต้องการเพียงบันทึกโดยไม่แทนที่ฟอนต์** | เพียงข้ามบล็อก `FontSettings` ไปเลย; ตัวเก็บคำเตือนอย่างเดียวก็เพียงพอ |
| **ฉันสามารถส่งคำเตือนไปยังไฟล์ได้หรือไม่?** | ได้ — แทนที่ `Console.WriteLine` ด้วย `File.AppendAllText("font-warnings.log", …)` |
| **วิธีนี้ทำงานกับ DOC, DOCX, และ ODT หรือไม่?** | ทำงานได้แน่นอน `LoadOptions` ใช้ได้กับทุกฟอร์แมตที่ Aspose.Words รองรับ |
| **ฟอนต์ที่ฝังอยู่ในเอกสารจะเป็นอย่างไร?** | ฟอนต์ที่ฝังอยู่ข้ามกลไกการแทนที่; จะใช้ตามที่ฝังไว้โดยตรง |
| **มีผลต่อประสิทธิภาพหรือไม่?** | ผลกระทบน้อยมาก — มี callback ต่อฟอนต์ที่หายไปหนึ่งครั้ง สำหรับชุดข้อมูลขนาดใหญ่ ควรรวบรวมคำเตือนแล้วบันทึกเป็นชุดแทนการเขียนต่อเหตุการณ์ |

---

## สรุป

เราได้แสดง **วิธีจัดการฟอนต์ที่หายไป** ใน Aspose.Words ด้วยการเชื่อม `DocumentWarnings` collector เข้ากับ `LoadOptions`, ตัวเลือกการสลับไปใช้ฟอนต์สำรอง, และการแสดงผลลัพธ์ วิธีนี้ให้คุณมองเห็นเหตุการณ์การแทนที่ฟอนต์ทั้งหมด ช่วยให้รักษาความคมชัดของภาพลักษณ์เมื่อต้องแปลงเป็น PDF, image, หรือ HTML  

ขั้นตอนต่อไปที่คุณอาจลองทำ:

* ผสาน collector กับเฟรมเวิร์กล็อกศูนย์กลาง  
* สร้างแดชบอร์ด UI ที่แสดงรายการเอกสารที่มีฟอนต์หายเพื่อประมวลผลเป็นชุด  
* ผสานวิธีนี้กับ Aspose.PDF เพื่อตรวจสอบว่า PDF ที่สร้างขึ้นใช้ฟอนต์สำรองจริงหรือไม่  

ลองเปลี่ยน `"Arial"` เป็น `"Tahoma"` หรือโหลดชุดเอกสารอื่น ๆ ดูได้เลย แนวคิดหลักยังคงเหมือนเดิม: ดักจับคำเตือน, ดำเนินการตาม, และทำให้เอกสารของคุณดูตรงตามที่ต้องการ  

ขอให้เขียนโค้ดสนุก! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}