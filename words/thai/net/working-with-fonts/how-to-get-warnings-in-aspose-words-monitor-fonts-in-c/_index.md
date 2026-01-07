---
category: general
date: 2026-01-06
description: เรียนรู้วิธีรับคำเตือนขณะโหลดเอกสารและวิธีตรวจสอบแบบอักษรโดยใช้ Aspose.Words
  คู่มือนี้ครอบคลุมการเรียกคืนคำเตือนและการติดตามการแทนที่แบบอักษร
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: th
og_description: วิธีรับคำเตือนใน Aspose.Words? ทำตามบทแนะนำขั้นตอนต่อขั้นตอนนี้เพื่อเฝ้าติดตามฟอนต์และจับข้อความการแทนที่ขณะโหลดเอกสาร.
og_title: วิธีรับคำเตือนใน Aspose.Words – ตรวจสอบฟอนต์
tags:
- Aspose.Words
- C#
- Font Monitoring
title: วิธีรับคำเตือนใน Aspose.Words – ตรวจสอบฟอนต์ใน C#
url: /th/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีรับคำเตือนใน Aspose.Words – ตรวจสอบฟอนต์ใน C#

เคยสงสัย **วิธีรับคำเตือน** เมื่อเอกสาร Word มีฟอนต์ที่คุณไม่ได้ติดตั้งหรือไม่? นี่เป็นปัญหาที่พบบ่อย—แอปของคุณจะเปลี่ยนฟอนต์ที่หายไปโดยเงียบ ๆ และคุณไม่รู้ว่ามีอะไรเปลี่ยนแปลง ข่าวดีคือคุณสามารถเชื่อมต่อกับระบบคำเตือนของ Aspose.Words และ **ตรวจสอบฟอนต์** แบบเรียลไทม์ได้

> **เคล็ดลับ:** หากคุณกำลังสร้าง pipeline การแปลงเอกสาร การบันทึกฟอนต์ที่หายไปตั้งแต่แรกจะช่วยคุณหลีกเลี่ยงความประหลาดใจด้านการจัดรูปแบบที่ไม่ดีในภายหลัง.

---

## สิ่งที่คุณต้องการ

- **Aspose.Words for .NET** (เวอร์ชันล่าสุด; API ยังไม่เปลี่ยนแปลงตั้งแต่ v23.10)
- สภาพแวดล้อมการพัฒนา .NET (Visual Studio, Rider, หรือ VS Code พร้อมส่วนขยาย C#)
- ตัวอย่างไฟล์ `.docx` ที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้ง (เช่น **“NonExistentFont”**)

เท่านี้—ไม่มีแพ็กเกจ NuGet เพิ่มเติมนอกจาก Aspose.Words.

---

## ขั้นตอนที่ 1 – ตั้งค่า Warning Collector (คีย์เวิร์ดหลักในหัวข้อ)

สิ่งแรกที่คุณต้องการคือที่เก็บคำเตือนเมื่อเกิดขึ้น Aspose.Words มี property `WarningCallback` บน `LoadOptions` เพื่อวัตถุประสงค์นี้โดยเฉพาะ

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
เมื่อไลบรารีพบฟอนต์ที่หายไป มันจะไม่โยน exception; แต่จะส่งออกอ็อบเจ็กต์ `WarningInfo` การเชื่อมต่อ collector จะทำให้คุณมองเห็นทุกเหตุการณ์การแทนที่อย่างเต็มที่ ทำให้คุณสามารถ **ตรวจสอบฟอนต์** ได้โดยไม่ทำให้คอนโซลของคุณเต็มไปด้วยข้อความที่ไม่เกี่ยวข้อง.

---

## ขั้นตอนที่ 2 – โหลดเอกสารด้วยตัวเลือกที่เปิดใช้งาน Warning

ตอนนี้เราจะอ่านไฟล์จริง ๆ `LoadOptions` ที่เราจัดเตรียมในขั้นตอนก่อนหน้าจะทำให้แน่ใจว่าคำเตือนที่เกี่ยวกับฟอนต์ทั้งหมดจะถูกจับไว้

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**อะไรที่เกิดขึ้นเบื้องหลัง?**  
Aspose.Words จะทำการพาร์สไฟล์ Word, แก้ไขฟอนต์, และเมื่อไม่พบฟอนต์ที่ร้องขอ มันจะใช้ฟอนต์สำรอง (โดยปกติคือ Arial) การสำรองนี้จะทำให้เกิดคำเตือน `WarningType.FontSubstitution` ซึ่งจะถูกบันทึกใน `warningCollector`.

---

## ขั้นตอนที่ 3 – ตรวจสอบคำเตือนที่เก็บไว้ (คีย์เวิร์ดหลักปรากฏอีกครั้ง)

หลังจากโหลดเอกสารแล้ว เราจะวนลูปผ่าน `warningCollector` และพิมพ์ข้อความการแทนที่ฟอนต์ใด ๆ ที่พบ

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (สมมติว่าฟอนต์ที่หายไปคือ *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

หากเอกสารมีฟอนต์ที่ไม่รู้จักหลายตัว คุณจะเห็นหนึ่งบรรทัดต่อการแทนที่—เหมาะสำหรับการบันทึกหรือแจ้งเตือน.

---

## ขั้นตอนที่ 4 – ทางเลือก: บันทึกหรือเก็บข้อมูลคำเตือน

ในสภาพแวดล้อมการผลิต คุณอาจต้องการมากกว่าการใช้ `Console.WriteLine` ตัวอย่างสั้น ๆ นี้จะเขียนคำเตือนลงไฟล์ JSON เพื่อการวิเคราะห์ในภายหลัง

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

ตอนนี้คุณมีบันทึกถาวรที่สามารถส่งต่อไปยังแดชบอร์ดการตรวจสอบ หรือแม้กระทั่งเรียกใช้การร้องขออัตโนมัติสำหรับไฟล์ฟอนต์ที่หายไป

---

## ขั้นตอนที่ 5 – ตรวจสอบผลลัพธ์และทำความสะอาด

เรียกใช้โปรแกรม หากคุณเห็นข้อความการแทนที่ คุณได้ **รับคำเตือน** สำเร็จและกำลัง **ตรวจสอบฟอนต์** อย่างต่อเนื่อง หากไม่มีอะไรแสดง ตรวจสอบอีกครั้งว่าเอกสารทดสอบจริง ๆ มีการอ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเครื่อง

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

จำนวนศูนย์มักหมายความว่าอย่างใดอย่างหนึ่ง:

1. ฟอนต์ทั้งหมดถูกแก้ไข (อาจฟอนต์ *มี* ติดตั้งในเครื่อง), หรือ
2. เอกสารไม่มีการอ้างอิงฟอนต์ที่ต้องการการแทนที่.

---

## ข้อผิดพลาดทั่วไป & วิธีหลีกเลี่ยง

| ปัญหา | สาเหตุ | วิธีแก้ |
|---------|----------------|-----|
| **ไม่มีคำเตือนปรากฏ** | ฟอนต์จริง ๆ มีอยู่ในระบบ หรือเอกสารใช้เฉพาะฟอนต์ที่มาพร้อมในตัว | เปลี่ยนชื่อฟอนต์ในไฟล์ต้นฉบับให้เป็นชื่อที่เป็นไปไม่ได้ (เช่น `XYZ123`) แล้วลองใหม่ |
| **คำเตือนมากเกินไป (เสียงรบกวน)** | คุณกำลังโหลดเอกสารหลายไฟล์ในลูปโดยไม่ได้ล้าง collector | สร้าง `WarningInfoCollection` ใหม่สำหรับแต่ละเอกสาร หรือเรียก `warningCollector.Clear()` หลังการประมวลผล |
| **ผลกระทบต่อประสิทธิภาพ** | การบันทึกลงดิสก์อย่างมากอาจทำให้การประมวลผลเป็นชุดช้าลง | เก็บคำเตือนในหน่วยความจำแล้วเขียนเป็นชุด, หรือใช้ I/O แบบอะซิงโครนัส |
| **ขาด `using Aspose.Words.Loading;`** | คลาส `LoadOptions` อยู่ใน namespace นี้ | เพิ่มคำสั่ง `using` ที่ขาดหายไปตามที่แสดงในขั้นตอน 1 |

---

## การขยายโซลูชัน – ตรวจสอบประเภทคำเตือนอื่น

แม้ว่าการแทนที่ฟอนต์จะเป็นที่เห็นชัดที่สุด Aspose.Words สามารถส่งคำเตือนสำหรับ:
- **ฟีเจอร์ที่เลิกใช้** (`WarningType.Deprecated`),
- **ความเสี่ยงการสูญเสียข้อมูล** (`WarningType.DataLoss`),
- **รูปแบบไฟล์ที่ไม่รองรับ** (`WarningType.UnsupportedFileFormat`).

คุณสามารถขยายตัวกรองในขั้นตอน 3 เพื่อจับคำเตือนเหล่านี้ได้เช่นกัน:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

ด้วยวิธีนี้คุณไม่เพียงแค่ **ตรวจสอบฟอนต์** แต่ยัง **รับคำเตือน** สำหรับสถานการณ์ใด ๆ ที่แอปพลิเคชันของคุณอาจเจอ

---

## ตัวอย่างทำงานเต็ม (พร้อมคัดลอก‑วาง)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**เรียกใช้:** สร้างโปรเจกต์, รัน, และคุณจะเห็นคำเตือนที่พิมพ์และบันทึกไว้ นี่คือคำตอบครบถ้วนสำหรับ **รับคำเตือน** และ **ตรวจสอบฟอนต์** ด้วย Aspose.Words.

---

## สรุป

ตอนนี้คุณรู้แล้วว่า **รับคำเตือน** จาก Aspose.Words อย่างไร โดยเฉพาะในสถานการณ์การแทนที่ฟอนต์ และคุณได้เรียนรู้ **ตรวจสอบฟอนต์** ตลอดกระบวนการโหลดเอกสาร ด้วยการแนบ `WarningCallback` การวนลูปอ็อบเจ็กต์ `WarningInfo` ที่เก็บไว้และอาจบันทึกข้อมูล คุณจะได้ความโปร่งใสเต็มที่ต่อเหตุการณ์ฟอนต์ที่หายไป—ความสามารถสำคัญสำหรับ pipeline การประมวลผลเอกสารใด ๆ

ขั้นตอนต่อไป? ลองขยายตัวกรองคำเตือนเพื่อครอบคลุมการสูญเสียข้อมูลหรือคำเตือนฟีเจอร์ที่เลิกใช้, หรือผสานบันทึก JSON เข้ากับแดชบอร์ดการตรวจสอบเช่น Grafana รูปแบบเดียวกันทำงานกับทุกประเภทของคำเตือน ดังนั้นคุณจะพร้อมอย่างดีในการเฝ้าระวังปัญหาใด ๆ ที่ Aspose.Words ส่งมา

ขอให้เขียนโค้ดอย่างสนุกสนาน และขอให้เอกสารของคุณแสดงผลตามที่คุณคาดหวังเสมอ!

<img src="font-warnings.png" alt="วิธีรับคำเตือนใน Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}