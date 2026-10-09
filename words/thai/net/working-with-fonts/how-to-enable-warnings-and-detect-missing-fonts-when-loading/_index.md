---
category: general
date: 2026-02-21
description: เรียนรู้วิธีเปิดการแจ้งเตือน, ตรวจจับฟอนต์ที่หายไป, และวิธีโหลดไฟล์ docx
  อย่างปลอดภัยโดยใช้ Aspose.Words ใน C#. ทำตามคู่มือขั้นตอนต่อขั้นตอน.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: th
og_description: วิธีเปิดการแจ้งเตือน, ตรวจจับฟอนต์ที่หายไป, และโหลดไฟล์ docx อย่างถูกต้องด้วย
  Aspose.Words พร้อมตัวอย่างโค้ดเต็ม
og_title: วิธีเปิดการแจ้งเตือนและตรวจจับฟอนต์ที่หายไปเมื่อโหลดไฟล์ DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: วิธีเปิดการแจ้งเตือนและตรวจจับฟอนต์ที่หายไปเมื่อโหลดไฟล์ DOCX
url: /th/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเปิดการแจ้งเตือนและตรวจจับฟอนต์ที่หายไปเมื่อโหลดไฟล์ DOCX

เคยสงสัยไหมว่า **how to enable warnings** สำหรับฟอนต์ที่หายไปก่อนที่มันจะทำให้การแสดงผลเอกสารของคุณเสียหายโดยเงียบ ๆ? คุณไม่ได้เป็นคนเดียว—นักพัฒนาส่วนใหญ่สมมติว่าห้องสมุดจะ “ทำในสิ่งที่ถูกต้อง” เพียงอย่างเดียว แล้วจึงพบภายหลังว่าฟอนต์ถูกเปลี่ยนโดยไม่มีสัญญาณใดเลย.

ในบทแนะนำนี้เราจะสาธิตให้คุณเห็นอย่างชัดเจนว่า **how to enable warnings**, วิธี **detect missing fonts**, และวิธีที่ถูกต้อง **how to load docx** ด้วย Aspose.Words for .NET. เมื่อจบคุณจะได้ตัวอย่างที่พร้อมรันซึ่งพิมพ์คำเตือนการแทนที่ฟอนต์ทุกรายการไปยังคอนโซล, เพื่อให้คุณไม่ต้องเดาว่าเกิดอะไรขึ้นภายในไฟล์.

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดทำงานบน .NET Framework 4.7+ ด้วย)  
- Visual Studio 2022 หรือ IDE C# ใด ๆ ที่คุณชอบ  
- แพ็กเกจ NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  
- ไฟล์ DOCX ที่อาจมีฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของคุณ (เราจะเรียกมันว่า `input.docx`)

> **Pro tip:** หากคุณไม่มีไฟล์ทดสอบ, เพียงเปิดเอกสาร Word ที่ใช้ฟอนต์องค์กรแบบกำหนดเองและบันทึกเป็น `input.docx`. สิ่งนั้นจะทำให้เกิดคำเตือนที่เราต้องการจับ.

## ภาพรวมของโซลูชัน

1. **Create** อ็อบเจ็กต์ `LoadOptions` พร้อมเปิด `FontSubstitutionWarnings`.  
2. **Load** ไฟล์ DOCX ด้วยตัวเลือกเหล่านั้น.  
3. **Inspect** คอลเลกชัน `WarningCallback` เพื่อหาข้อมูล `FontSubstitution` ใด ๆ.  
4. **React** – คุณอาจบันทึก, แสดงผล, หรือแม้แต่แทนที่ฟอนต์ที่หายไปโดยโปรแกรม.

ด้านล่างเราจะแบ่งขั้นตอนแต่ละขั้นเป็นส่วนย่อย, อธิบายว่า *ทำไม* จึงสำคัญ, และให้โค้ดตัวอย่างที่สมบูรณ์และรันได้.

---

## ขั้นตอนที่ 1: ติดตั้ง Aspose.Words และตั้งค่าโปรเจกต์

ก่อนที่เราจะสามารถ **how to enable warnings** ได้, เราต้องการไลบรารีที่สนับสนุนฟีเจอร์นี้จริง ๆ.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

หรือ, ใน Visual Studio Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Why this step?**  
> หากไม่มีแพ็กเกจ, คลาส `LoadOptions`, `Document`, และโครงสร้างการแจ้งเตือนจะไม่มีอยู่เลย. การเพิ่มการอ้างอิง NuGet ทำให้คุณได้เวอร์ชันเสถียรล่าสุด (ณ เวลาที่เขียนนี้, 24.5).

---

## ขั้นตอนที่ 2: สร้าง LoadOptions ที่เปิดการแจ้งเตือนการแทนที่ฟอนต์

หัวใจของ **how to enable warnings** อยู่ในคลาส `LoadOptions`. การตั้งค่า `FontSubstitutionWarnings` เป็น `true` จะบอกเอนจินให้บันทึกทุกครั้งที่ต้องแทนที่ฟอนต์ที่หายไป.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Why enable this flag?**  
> โดยค่าเริ่มต้น Aspose.Words จะเปลี่ยนฟอนต์ที่หายไปโดยเงียบ ๆ ด้วยฟอนต์สำรอง (มักเป็น Arial). สิ่งนี้อาจทำให้เลย์เอาต์เปลี่ยนแปลง, ตัวอักษรหายไป, หรือการละเมิดแบรนด์. การเปิดฟลักนี้ทำให้คุณเห็นภาพทั้งหมด.

---

## ขั้นตอนที่ 3: โหลดไฟล์ DOCX ด้วยตัวเลือกที่กำหนดไว้

ตอนนี้เรารู้ว่า **how to load docx** พร้อมเปิดการแจ้งเตือนแล้ว, เราจะทำการโหลดจริง.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **What happens under the hood?**  
> ระหว่างการพาร์ส DOCX, Aspose.Words จะตรวจสอบทุกองค์ประกอบ `<w:rFonts>`. หากฟอนต์ที่ระบุไม่ได้ติดตั้ง, มันจะบันทึกคำเตือน `FontSubstitution` และใช้ฟอนต์เริ่มต้นแทน. เนื่องจากเราเปิดการแจ้งเตือน, รายการเหล่านั้นจะอยู่ใน `document.WarningCallback.Warnings`.

---

## ขั้นตอนที่ 4: ดึงและแสดงคำเตือนการแทนที่ฟอนต์

คุณสมบัติ `WarningCallback` เก็บ `WarningInfoCollection`. ทำการวนลูป, กรองโดย `WarningType.FontSubstitution`, และแสดงข้อความ.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (ตัวอย่าง):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **What to do with these messages?**  
> คุณอาจบันทึกลงไฟล์, แสดงใน UI, หรือแม้กระทั่งเรียกใช้ขั้นตอนฟอนต์สำรองแบบกำหนดเอง. สิ่งสำคัญคือคุณตอนนี้ *detect missing fonts* แทนการเดาในภายหลัง.

---

## ขั้นตอนที่ 5: (ตัวเลือก) แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรองที่กำหนด

หากคุณมีฟอนต์องค์กรที่ต้องการบังคับใช้, คุณสามารถจัดการคำเตือนและแทนที่ฟอนต์เหล่านั้นแบบเรียลไทม์.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Why consider this?**  
> มันรับประกันความสอดคล้องของภาพในทุกเอกสารที่สร้าง, ซึ่งสำคัญต่อการปฏิบัติตามแบรนด์.

---

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นไฟล์ C# เดียวที่คุณสามารถคัดลอก‑วางลงในแอปคอนโซล. มันครอบคลุมทุกอย่าง—from การติดตั้งแพ็กเกจจนถึงการพิมพ์คำเตือน.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Run it**: `dotnet run` จากโฟลเดอร์โปรเจกต์. หากมีฟอนต์ใดหายไป, คุณจะเห็นคำเตือนที่พิมพ์ออกมา, และการแทนที่แบบเลือกจะถูกนำไปใช้ก่อนบันทึกไฟล์.

---

## คำถามที่พบบ่อย

### วิธีนี้ทำงานกับการแปลงเป็น PDF ด้วยหรือไม่?

ใช่. หลังจากที่คุณจัดการคำเตือนแล้ว, คุณสามารถเรียก `doc.Save("output.pdf")` และฟอนต์ที่แทนที่จะปรากฏใน PDF เช่นเดียวกับใน DOCX.

### ถ้าฉันต้องการยกเลิกคำเตือนสำหรับฟอนต์เฉพาะ?

คุณสามารถกรองออกในลูป—เพียงข้าม `WarningInfo` ที่ `Message` มีชื่อฟอนต์ที่คุณต้องการละเว้น.

### `FontSubstitutionWarnings` มีในเวอร์ชันเก่าของ Aspose.Words หรือไม่?

มันถูกเพิ่มเข้ามาในเวอร์ชัน 20.5. หากคุณยังใช้เวอร์ชันเก่า, ให้อัปเกรดผ่าน NuGet; การเปลี่ยนแปลง API ยังเข้ากันได้กับรุ่นก่อน.

---

## สรุป

เราได้อธิบายขั้นตอน **how to enable warnings**, แสดงให้คุณ **detect missing fonts**, และสาธิตวิธีที่ถูกต้อง **how to load docx** ด้วย Aspose.Words พร้อมให้คุณมองเห็นการแทนที่ฟอนต์อย่างเต็มที่. ด้วยการตรวจสอบ `document.WarningCallback.Warnings` คุณจะได้เส้นทางตรวจสอบที่เชื่อถือได้—ไม่มีการสำรองเงียบอีกต่อไป.

ขั้นตอนต่อไป? ลองเชื่อมตรรกะการแจ้งเตือนเข้ากับเฟรมเวิร์กการบันทึกเช่น Serilog, หรือสร้าง UI ที่ไฮไลท์ฟอนต์ที่หายไปก่อนส่งเอกสารให้ผู้ใช้. คุณอาจสำรวจคลาส `FontSettings` เพื่อควบคุมนโยบายการแทนที่ฟอนต์อย่างละเอียดมากขึ้น.

ขอให้เขียนโค้ดอย่างสนุกสนาน, และขอให้เอกสารของคุณแสดงผลตรงตามที่คุณตั้งใจเสมอ! 

![Diagram illustrating the flow from loading a DOCX file to capturing font substitution warnings – how to enable warnings in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}