---
category: general
date: 2026-02-10
description: ตั้งค่า warning callback เพื่อตรวจสอบการเปลี่ยนแปลงฟอนต์ขณะกำหนดฟอนต์เริ่มต้นและตั้งค่าฟอนต์นำเข้าเริ่มต้นใน
  Aspose.Words เรียนรู้วิธีแก้ปัญหาแบบขั้นตอนเต็ม.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: th
og_description: ตั้งค่าการเรียกคืนคำเตือนเพื่อเฝ้าติดตามการเปลี่ยนแปลงฟอนต์ขณะกำหนดฟอนต์เริ่มต้นและตั้งค่าฟอนต์นำเข้าเริ่มต้น.
  ทำตามบทเรียนเต็มสำหรับ Aspose.Words.
og_title: ตั้งค่า callback คำเตือนใน C# – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Import
title: ตั้งค่าการเรียกกลับคำเตือนใน C# – คู่มือฉบับสมบูรณ์การจัดการฟอนต์
url: /th/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set warning callback in C# – คู่มือฉบับสมบูรณ์การจัดการฟอนต์

เคยต้องการ **set warning callback** ขณะโหลดเอกสาร Word และสงสัยว่าจะ *configure default font* พร้อมกันได้อย่างไรหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายโครงการจริง—เช่น ตัวสร้างรายงานอัตโนมัติหรือ pipeline การแปลงเอกสาร—ฟอนต์ที่หายไปอาจทำให้เลย์เอาต์พังโดยไม่แจ้ง และวิธีเดียวที่จะจับปัญหานี้คือ **monitor font changes** ผ่าน warning callback.

ในบทเรียนนี้เราจะพาคุณผ่านตัวอย่างเชิงปฏิบัติที่แสดงให้เห็นวิธี **set warning callback**, **configure default font**, และแม้กระทั่ง **set default import font** ด้วย Aspose.Words for .NET. เมื่อจบคุณจะได้โค้ดสั้น ๆ ที่พร้อมรัน, เข้าใจว่าทำไมแต่ละส่วนจึงสำคัญ, และรู้วิธีปรับให้เข้ากับกรณีขอบเช่นโฟลเดอร์ฟอนต์แบบกำหนดเองหรือการแทนที่แบบเงียบ ๆ

---

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ทำงานบน .NET Framework 4.6+ ด้วย)  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
- โฟลเดอร์ที่มีฟอนต์ fallback ที่คุณต้องการใช้ (เช่น `fonts/Arial.ttf`)  
- ความคุ้นเคยพื้นฐานกับแอปพลิเคชันคอนโซล C#  

ไม่จำเป็นต้องใช้ไลบรารีเพิ่มเติม

---

## ขั้นตอนที่ 1: สร้าง LoadOptions และ **configure default font**

สิ่งแรกที่คุณทำเมื่ออยากควบคุมการจัดการฟอนต์คือการสร้างอินสแตนซ์ของ `LoadOptions`. อ็อบเจกต์นี้บอก Aspose.Words ว่าจะจัดการกับฟอนต์ที่หายไปอย่างไรระหว่างการนำเข้า

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
หากเอกสารต้นทางอ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์, Aspose.Words จะมองหาในโฟลเดอร์ที่คุณระบุ นี่คือแก่นของ **set default import font**—คุณบอกไลบรารีอย่างชัดเจนว่าต้องหาแทนที่ที่ไหนก่อนที่คำเตือนใด ๆ จะถูกส่งออก

---

## ขั้นตอนที่ 2: **Set warning callback** เพื่อ **monitor font changes**

Aspose.Words จะปล่อย `WarningInfoCollection` ทุกครั้งที่ต้องแทนที่ฟอนต์, รวมถึงเหตุการณ์อื่น ๆ ด้วย การแนบ handler จะทำให้คุณบันทึกหรือทำการตอบสนองต่อการแทนที่แต่ละครั้ง

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
การ **configure default font** เพียงอย่างเดียวไม่พอหากคุณต้องการตรวจสอบว่าฟอนต์ใดบ้างที่ถูกสลับจริง ๆ callback จะให้บันทึกแบบเรียลไทม์, ตอบสนองต่อความต้องการ **monitor font changes** และช่วยให้คุณจับการ fallback ที่ไม่คาดคิดได้ตั้งแต่ต้นใน pipeline CI

---

## ขั้นตอนที่ 3: โหลดเอกสารด้วยตัวเลือกที่เตรียมไว้

เมื่อ `LoadOptions` พร้อมแล้ว, คุณสามารถโหลดไฟล์ `.docx` ใดก็ได้อย่างปลอดภัย Callback จะทำงานอัตโนมัติหากมีการแทนที่เกิดขึ้น

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**สิ่งที่คุณจะเห็น:**  
หากต้นทางใช้ฟอนต์ที่ไม่มีอยู่, คอนโซลจะพิมพ์ข้อความประมาณนี้:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

ผลลัพธ์นี้ยืนยันว่าคุณได้ **set warning callback** สำเร็จและ **default import font** ทำงานตามที่คาดหวัง

---

## ขั้นตอนที่ 4: (Optional) ปรับแต่งพฤติกรรมการแทนที่ฟอนต์ให้ละเอียดขึ้น

บางครั้งคุณอาจต้องการแทนที่ *ฟอนต์ที่หายไปทั้งหมด* ด้วยตระกูลเดียว, ไม่คำนึงถึงคำขอเดิม Aspose.Words ให้คุณตั้งค่า *fallback font* ทั้งระบบ

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**เมื่อใดควรใช้:**  
หากคุณกำลังสร้าง PDF สำหรับแบรนด์ที่อนุญาตให้ใช้ฟอนต์ชุดจำกัด, วิธีนี้จะทำให้ทุกเอกสารมีความสอดคล้องกัน แม้แหล่งข้อมูลจะพยายามใช้ฟอนต์ที่แปลกใหม่

---

## ขั้นตอนที่ 5: บันทึกหรือประมวลผลเอกสารต่อ

หลังจากโหลดแล้ว, คุณสามารถทำการประมวลผลต่อได้ตามต้องการ—แก้ไข, แปลงเป็น PDF, ดึงข้อความ ฯลฯ ตัวอย่างสั้น ๆ ด้านล่างแสดงการบันทึกเป็น PDF พร้อมคงฟอนต์ที่ถูกแทนที่ไว้

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

PDF ที่ได้จะแสดงฟอนต์ fallback ทุกจุดที่มีการแทนที่, ให้คุณเห็นภาพยืนยันว่า **set warning callback** ทำงานตามที่คาด

---

## ข้อผิดพลาดทั่วไป & เคล็ดลับระดับมืออาชีพ

| ข้อผิดพลาด | สาเหตุ | วิธีแก้ |
|------------|--------|----------|
| **Callback never fires** | `LoadOptions.WarningCallback` ไม่ได้ถูกกำหนด *ก่อน* โหลดเอกสาร | อย่าลืมแนบ callback **ก่อน** เรียก `new Document(...)` |
| **Wrong font folder** | พิมพ์ผิดพลาดในพาธหรือไม่มีสิทธิ์อ่าน | ตรวจสอบว่าโฟลเดอร์มีอยู่และแอปมีสิทธิ์ `Read` ใช้พาธแบบ absolute เพื่อความเชื่อถือ |
| **Multiple substitutions, noisy output** | เอกสารขนาดใหญ่มีฟอนต์หายหลายตัว | กรอง warning ด้วย `WarningType.FontSubstitution` (ตามตัวอย่าง) หรือบันทึกลงไฟล์ log แทนคอนโซล |
| **Fallback font not applied** | ฟอนต์ fallback ไม่ได้ติดตั้งบนเครื่อง | ใส่ไฟล์ `.ttf`/`.otf` ลงในโฟลเดอร์ที่ส่งให้ `SetFontsFolder` Aspose.Words จะโหลดโดยตรง ไม่ต้องติดตั้งบน OS |

**Pro tip:** เมื่อรันใน pipeline CI/CD, ให้ redirect ผลลัพธ์คอนโซลไปยัง artifact ของการ build. วิธีนี้จะทำให้คุณมี audit trail ของการแทนที่ฟอนต์ทุกครั้งที่เกิดขึ้นระหว่างการ build

---

## ตัวอย่างทำงานเต็มรูปแบบ (Copy‑Paste Ready)

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถวางลงในโปรเจค Console App ใหม่ได้เลย มีทุกขั้นตอน, using statements, และคอมเมนต์ที่จำเป็น

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**ผลลัพธ์คอนโซลที่คาดหวัง** (สมมติว่า `Times New Roman` หายไป):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

รันโปรแกรม, เปิด `output.pdf`, คุณจะเห็นเอกสารแสดงด้วยฟอนต์ fallback ตามที่ต้องการ

---

## สรุป

ตอนนี้คุณมีรูปแบบที่มั่นคงและพร้อมใช้งานในระดับ production สำหรับการ **set warning callback** ใน C#, **configure default font**, **monitor font changes**, และ **set default import font** เมื่อทำงานกับ Aspose.Words. ด้วยการแนบ warning collector ก่อนโหลด, ชี้ `FontSettings` ไปยังโฟลเดอร์ฟอนต์ที่เชื่อถือได้, และหากต้องการบังคับ fallback ทั่วโลก, คุณจะได้มองเห็นและควบคุมการแทนที่ฟอนต์อย่างเต็มที่—สิ่งที่ pipeline การประมวลผลเอกสารที่แข็งแรงต้องการ

พร้อมก้าวต่อไป? ลองผสานวิธีนี้กับ:

- **Dynamic font loading** จากฐานข้อมูล (ใช้ `FontSettings.SetFontsFolder` ขณะ runtime)  
- **Custom warning handlers** ที่บันทึกเป็น log โครงสร้าง (JSON หรือ CSV) เพื่อวิเคราะห์  
- **Parallel document processing** ที่แต่ละเธรดใช้ `LoadOptions` ของตนเองเพื่อหลีกเลี่ยงการสื่อสารข้ามเธรด  

อย่าลังเลที่จะทดลอง, ปรับโค้ดให้เข้ากับสถาปัตยกรรมของคุณ, และแชร์การค้นพบในคอมเมนต์. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}