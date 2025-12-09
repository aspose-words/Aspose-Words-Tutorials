---
language: th
url: /thai/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# ตรวจจับฟอนต์ที่หายไปในเอกสาร Aspose.Words – คู่มือ C# ฉบับสมบูรณ์

เคยสงสัยไหมว่า **ตรวจจับฟอนต์ที่หายไป** อย่างไรเมื่อคุณโหลดไฟล์ Word ด้วย Aspose.Words? ในงานประจำวันของฉัน ฉันเคยเจอ PDF บางไฟล์ที่ดูแปลกเพราะเอกสารต้นฉบับใช้ฟอนต์ที่ฉันไม่ได้ติดตั้ง ข่าวดีคือ Aspose.Words สามารถบอกคุณได้อย่างแม่นยำเมื่อมันทำการแทนที่ฟอนต์ และคุณสามารถจับข้อมูลนั้นด้วย callback คำเตือนแบบง่าย  

ในบทแนะนำนี้เราจะพาคุณผ่าน **ตัวอย่างที่สมบูรณ์และสามารถรันได้** ที่แสดงวิธีบันทึกการแทนที่ฟอนต์ทุกครั้ง เหตุผลที่ callback มีความสำคัญ และเทคนิคเพิ่มเติมสองสามอย่างสำหรับการตรวจจับฟอนต์ที่หายไปอย่างมั่นคง ไม่ได้มีเนื้อหาเกินความจำเป็น เพียงโค้ดและเหตุผลที่คุณต้องการเพื่อให้ทำงานได้ทันที

---

## สิ่งที่คุณจะได้เรียนรู้

- วิธีการทำ **Aspose.Words warning callback** เพื่อดักจับเหตุการณ์การแทนที่ฟอนต์  
- วิธีการกำหนดค่า **LoadOptions C#** เพื่อให้ callback ถูกเรียกขณะโหลดเอกสาร  
- วิธีตรวจสอบว่าการตรวจจับฟอนต์ที่หายไปทำงานจริงหรือไม่ และผลลัพธ์ที่แสดงในคอนโซลเป็นอย่างไร  
- การปรับแต่งเพิ่มเติมสำหรับการประมวลผลเป็นกลุ่มใหญ่หรือสภาพแวดล้อมแบบ headless  

**ข้อกำหนดเบื้องต้น** – คุณต้องมี Aspose.Words for .NET รุ่นล่าสุด (โค้ดทดสอบกับเวอร์ชัน 23.12) , .NET 6 หรือใหม่กว่า และความเข้าใจพื้นฐานเกี่ยวกับ C# หากคุณมีทั้งหมดนี้ คุณก็พร้อมเริ่มใช้งานแล้ว

---

## ตรวจจับฟอนต์ที่หายไปด้วย Warning Callback

หัวใจของวิธีแก้คือการทำงานของ `IWarningCallback` Aspose.Words จะส่งอ็อบเจ็กต์ `WarningInfo` สำหรับหลายสถานการณ์ แต่เราสนใจเฉพาะ `WarningType.FontSubstitution` เท่านั้น มาดูกันว่าจะเชื่อมต่ออย่างไร

### ขั้นตอน 1: สร้าง Font‑Warning Collector

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*เหตุผล*: การกรองด้วย `WarningType.FontSubstitution` จะช่วยหลีกเลี่ยงคำเตือนที่ไม่เกี่ยวข้อง (เช่นฟีเจอร์ที่เลิกใช้) `info.Description` มีชื่อฟอนต์ต้นฉบับและฟอนต์สำรองที่ใช้แล้ว ทำให้คุณได้บันทึกข้อมูลที่ชัดเจน

---

## กำหนดค่า LoadOptions เพื่อใช้ Callback

ต่อไปเราจะบอก Aspose.Words ให้ใช้ collector ของเราขณะโหลดไฟล์

### ขั้นตอน 2: ตั้งค่า LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*เหตุผล*: `LoadOptions` เป็นจุดเดียวที่คุณสามารถต่อ callback, รหัสผ่านการเข้ารหัส, และพฤติกรรมการโหลดอื่น ๆ การแยกออกจากคอนสตรัคเตอร์ `Document` ทำให้โค้ดสามารถนำไปใช้ซ้ำได้หลายไฟล์

---

## โหลดเอกสารและจับฟอนต์ที่หายไป

เมื่อเชื่อมต่อ callback แล้ว ขั้นตอนต่อไปคือการโหลดเอกสาร

### ขั้นตอน 3: โหลดไฟล์ DOCX (หรือรูปแบบที่สนับสนุนอื่น)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

ขณะคอนสตรัคเตอร์ `Document` วิเคราะห์ไฟล์ ฟอนต์ที่หายไปใด ๆ จะทำให้ `FontWarningCollector` ของเราถูกเรียก คอนโซลจะแสดงบรรทัดเช่น:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

บรรทัดนั้นเป็นหลักฐานที่ชัดเจนว่า **การตรวจจับฟอนต์ที่หายไป** ทำงานสำเร็จ

---

## ตรวจสอบผลลัพธ์ – สิ่งที่ควรคาดหวัง

เรียกโปรแกรมจากเทอร์มินัลหรือ Visual Studio หากเอกสารต้นทางมีฟอนต์ที่คุณไม่ได้ติดตั้ง คุณจะเห็นอย่างน้อยหนึ่งบรรทัด “Font substituted” หากเอกสารใช้ฟอนต์ที่ติดตั้งอยู่แล้ว callback จะเงียบและคุณจะเห็นข้อความ “Document loaded successfully.” เท่านั้น

**เคล็ดลับ**: เพื่อตรวจสอบอีกครั้ง ให้เปิดไฟล์ Word ด้วย Microsoft Word แล้วดูรายการฟอนต์ ฟอนต์ใดที่ปรากฏใน *Replace Fonts* ภายใต้กลุ่ม *Home → Font* จะเป็นผู้สมัครสำหรับการแทนที่

---

## ขั้นสูง: ตรวจจับฟอนต์ที่หายไปเป็นกลุ่มใหญ่

บ่อยครั้งที่คุณต้องสแกนหลายสิบไฟล์ รูปแบบเดียวกันสามารถขยายได้อย่างราบรื่น:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

เพราะ `FontWarningCollector` เขียนผลลัพธ์ลงคอนโซลทุกครั้งที่ถูกเรียก คุณจะได้รายงานต่อไฟล์โดยไม่ต้องเขียนโค้ดเพิ่มเติม สำหรับสถานการณ์การผลิตคุณอาจต้องการบันทึกลงไฟล์หรือฐานข้อมูล – เพียงเปลี่ยน `Console.WriteLine` เป็น logger ที่คุณต้องการ

---

## ข้อผิดพลาดทั่วไป & เคล็ดลับระดับมืออาชีพ

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|--------|
| **ไม่มีคำเตือนใดปรากฏ** | เอกสารจริง ๆ มีเพียงฟอนต์ที่ติดตั้งอยู่ | ตรวจสอบโดยเปิดไฟล์ใน Word หรือโดยการลบฟอนต์ออกจากระบบโดยเจตนา |
| **Callback ไม่ถูกเรียก** | `LoadOptions.WarningCallback` ไม่ได้ถูกกำหนดหรือมีการใช้ `LoadOptions` ตัวใหม่หลังจากนั้น | ใช้วัตถุ `LoadOptions` ตัวเดียวและนำไปใช้ซ้ำทุกครั้งที่โหลด |
| **คำเตือนที่ไม่เกี่ยวข้องมากเกินไป** | คุณไม่ได้กรองด้วย `WarningType.FontSubstitution` | เพิ่มเงื่อนไข `if (info.Type == WarningType.FontSubstitution)` ตามที่แสดง |
| **ประสิทธิภาพช้าบนไฟล์ขนาดใหญ่** | Callback ทำงานกับทุกคำเตือน ซึ่งอาจมีจำนวนมากในเอกสารใหญ่ | ปิดคำเตือนประเภทอื่นผ่าน `LoadOptions.WarningCallback` หรือกำหนด `LoadOptions.LoadFormat` ให้เป็นประเภทที่คุณรู้ล่วงหน้า |

---

## ตัวอย่างทำงานเต็มรูปแบบ (พร้อมคัดลอก‑วาง)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**ผลลัพธ์คอนโซลที่คาดหวัง** (เมื่อพบฟอนต์ที่หายไป):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

หากไม่มีการแทนที่ใดเกิดขึ้น คุณจะเห็นเพียงบรรทัดแสดงความสำเร็จเท่านั้น

---

## สรุป

คุณมี **วิธีตรวจจับฟอนต์ที่หายไปในเอกสารใด ๆ ที่ประมวลผลด้วย Aspose.Words** อย่างครบถ้วนและพร้อมใช้งานในระดับการผลิตแล้ว โดยใช้ **Aspose.Words warning callback** และกำหนด **LoadOptions C#** คุณสามารถบันทึกการแทนที่ฟอนต์ทุกครั้ง แก้ไขปัญหาเลย์เอาต์ และทำให้ PDF ของคุณคงรูปลักษณ์ตามที่ต้องการ  

ไม่ว่าจะเป็นไฟล์เดียวหรือหลายร้อยไฟล์ รูปแบบก็เหมือนเดิม – implement `IWarningCallback`, plug it into `LoadOptions`, แล้วให้ Aspose.Words จัดการส่วนที่เหลือ  

พร้อมก้าวต่อไปหรือยัง? ลองผสานวิธีนี้กับ **font embedding** หรือ **fallback font families** เพื่อแก้ปัญหาโดยอัตโนมัติ หรือสำรวจ API **DocumentVisitor** เพื่อวิเคราะห์เนื้อหาอย่างละเอียด ขอให้เขียนโค้ดสนุกและฟอนต์ของคุณอยู่ในที่ที่คาดหวัง!  

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}