---
category: general
date: 2026-04-24
description: วิธีตรวจจับการแทนที่ฟอนต์ที่หายไปใน Aspose.Words ด้วย C# คู่มือนี้จะแสดงวิธีจัดการกับฟอนต์ที่หายไปอย่างเชื่อถือได้ด้วยคำเตือนจาก
  FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: th
og_description: วิธีตรวจจับการแทนที่ฟอนต์ที่หายไปใน Aspose.Words ด้วย C#. เรียนรู้การจัดการฟอนต์ที่หายไปโดยใช้คำเตือนจาก
  FontSettings.
og_title: วิธีตรวจจับการแทนที่ใน Aspose.Words – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: วิธีตรวจจับการแทนที่ใน Aspose.Words – จัดการกับฟอนต์ที่หายไป
url: /th/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตรวจจับการแทนที่ใน Aspose.Words – จัดการฟอนต์ที่หายไป

เคยสงสัย **วิธีตรวจจับการแทนที่** เมื่อเอกสารพยายามใช้ฟอนต์ที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์ของคุณหรือไม่? นี่เป็นปัญหาที่พบบ่อย โดยเฉพาะเมื่อคุณสร้าง PDF หรือไฟล์ Word ในกระบวนการอัตโนมัติ ข่าวดีคือ Aspose.Words มีฮุคในตัวที่ช่วยให้คุณตรวจจับสถานการณ์นี้ได้อย่างแม่นยำ และคุณยังสามารถ **จัดการฟอนต์ที่หายไป** อย่างราบรื่นได้อีกด้วย

ในบทเรียนนี้เราจะเดินผ่านตัวอย่างจริงที่แสดง **วิธีตรวจจับการแทนที่** ผ่านเหตุการณ์ `FontSettings.Warning` และอธิบายวิธี **จัดการฟอนต์ที่หายไป** โดยไม่ทำให้กระบวนการของคุณหยุดชะงัก สุดท้ายคุณจะได้โค้ดสคริปต์พร้อมใช้งาน ความเข้าใจที่ชัดเจนว่าทำไมแต่ละบรรทัดถึงสำคัญ และเคล็ดลับเล็ก ๆ เพื่อหลีกเลี่ยงปัญหาที่มักพบ

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ทำงานบน .NET Framework ด้วย)
- Aspose.Words for .NET (แพคเกจ NuGet `Aspose.Words`) – เวอร์ชัน 23.11 หรือใหม่กว่า
- ตัวอย่างเอกสารที่อ้างอิงฟอนต์ที่คุณไม่มีติดตั้ง (เช่น `MissingFont.docx`)
- Visual Studio, VS Code หรือ IDE C# ใด ๆ ที่คุณชื่นชอบ  

ไม่ต้องตั้งค่าพิเศษใด ๆ นอกจากการเพิ่มแพคเกจ NuGet

---

## วิธีตรวจจับการแทนที่ด้วย FontSettings

แกนหลักของ **วิธีตรวจจับการแทนที่** อยู่ที่เหตุการณ์ `FontSettings.Warning` เมื่อ Aspose.Words ไม่สามารถหาไฟล์ฟอนต์ที่ร้องขอได้ มันจะส่งคำเตือน `WarningType.FontSubstitution` โดยการสมัครรับเหตุการณ์นี้คุณจะได้รับการแจ้งเตือนแบบเรียลไทม์ พร้อมชื่อฟอนต์ต้นฉบับและฟอนต์ที่ใช้แทน

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**ทำไมวิธีนี้ถึงได้ผล:**  
- `LoadOptions.FontSettings` บอก Aspose.Words ให้ใช้วัตถุ `FontSettings` ที่คุณสร้างขึ้น  
- การสมัครรับ `Warning` ทำให้คุณมีจุดเดียวในการตรวจสอบ *ปัญหาที่เกี่ยวกับฟอนต์ทั้งหมด* ไม่ใช่แค่ฟอนต์ที่หายไปเท่านั้น  
- ตัวกรอง `WarningType.FontSubstitution` ทำให้คุณตอบสนองต่อสถานการณ์ที่ต้องการเท่านั้น – สรุปคือ **วิธีตรวจจับการแทนที่** อย่างแท้จริง

### ผลลัพธ์ที่คาดหวัง

การรันโค้ดด้านบนกับเอกสารที่อ้างอิงฟอนต์ที่ไม่มีอยู่จะพิมพ์ข้อความประมาณนี้:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

หากเอกสารใช้เฉพาะฟอนต์ที่ติดตั้งอยู่แล้ว คอนโซลจะเงียบ – สัญญาณชัดเจนว่า **วิธีตรวจจับการแทนที่** ทำงานสำเร็จโดยไม่มีการเตือนเท็จ

---

## การจัดการฟอนต์ที่หายไปอย่างราบรื่น

การตรวจจับการแทนที่เป็นเพียงครึ่งหนึ่งของการแก้ปัญหา; คุณยังต้องมีกลยุทธ์เพื่อ **จัดการฟอนต์ที่หายไป** เพื่อให้ผลลัพธ์สุดท้ายดูตามที่ต้องการ ด้านล่างนี้คือสามวิธีปฏิบัติที่คุณสามารถผสมผสานใช้ได้

### 1. ระบุโฟลเดอร์ฟอนต์สำรอง

Aspose.Words สามารถค้นหาโฟลเดอร์เพิ่มเติมเพื่อหาไฟล์ฟอนต์ได้ โดยการชี้ไปที่โฟลเดอร์ที่มีฟอนต์ที่พบบ่อยที่สุด คุณจะลดโอกาสการแทนที่ลงอย่างมาก

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**ทำไม:** เมื่อฟอนต์ต้นฉบับหายไป Aspose.Words จะมีชุดฟอนต์สำรองที่รู้จัก ซึ่งมักให้ผลลัพธ์ที่คาดเดาได้มากขึ้น

### 2. แทนที่ฟอนต์ที่หายไปด้วยโค้ด

หากต้องการควบคุมเต็มรูปแบบ คุณสามารถแทนที่ฟอนต์ที่หายไปด้วยฟอนต์เฉพาะหลังจากตรวจพบได้

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**ทำไม:** วิธีนี้บอกเอนจินอย่างชัดเจนว่าควรลองใช้ฟอนต์ใดบ้าง ทำให้คุณสามารถบังคับใช้แบรนด์ของบริษัทหรือมาตรฐานการเข้าถึงได้

### 3. บันทึกและยกเลิก (เมื่อการแทนที่ไม่ยอมรับได้)

บางครั้งฟอนต์ที่หายไปหมายความว่าเอกสารไม่เหมาะกับกรณีการใช้งานของคุณ (เช่น แบบฟอร์มทางกฎหมาย) ในสถานการณ์นั้นคุณสามารถโยนข้อยกเว้นทันทีเมื่อเกิดการแทนที่

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**ทำไม:** การล้มเหลวทันทีช่วยป้องกันข้อผิดพลาดต่อเนื่อง เช่น ตารางที่จัดตำแหน่งผิดหรือลายเซ็นที่เสียหาย

---

## ตัวอย่างทำงานเต็มรูปแบบ – รวมทุกขั้นตอนไว้ในหนึ่งไฟล์

ด้านล่างเป็นโปรแกรมพร้อมคัดลอก‑วางที่แสดง **วิธีตรวจจับการแทนที่** *และ* วิธีต่าง ๆ เพื่อ **จัดการฟอนต์ที่หายไป** คุณสามารถคอมเมนต์ส่วนที่ไม่ต้องการได้ตามสะดวก

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**สิ่งที่คาดว่าจะเกิดขึ้น:**  
- หาก `MissingFont.docx` อ้างอิงฟอนต์ที่ไม่มีบนเครื่อง คอนโซลจะพิมพ์คำเตือนการแทนที่  
- ไฟล์ `Processed.docx` ที่บันทึกไว้จะใช้ฟอนต์สำรองที่คุณกำหนด (หรือฟอนต์เริ่มต้นของไลบรารี)  
- จะไม่มีข้อยกเว้นที่ไม่ได้จัดการ ยกเว้นคุณตั้งใจให้หยุดทำงานเมื่อมีการแทนที่

---

## คำถามทั่วไป & กรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| *ถ้าเอกสารมีฟอนต์ที่หายไปหลายตัวจะเป็นอย่างไร?* | เหตุการณ์เตือนจะเกิดขึ้น **สำหรับแต่ละ** การแทนที่ ดังนั้นคุณจะเห็นหลายบรรทัด คุณสามารถรวบรวมเป็นรายการเพื่อสรุปรายงานได้ |
| *วิธีนี้ทำงานกับการแปลงเป็น PDF หรือไม่?* | ทำได้แน่นอน `FontSettings` เดียวกันจะถูกนำไปใช้เมื่อคุณเรียก `doc.Save("out.pdf")` คำเตือนการแทนที่จะยังคงเกิดขึ้น ทำให้คุณตรวจสอบความตรงของภาพใน PDF ได้ |
| *สามารถตรวจจับการแทนที่หลังจากโหลดเอกสารแล้วได้หรือไม่?* | ไม่ได้โดยตรง คำเตือนจะถูกส่ง **ระหว่าง** การโหลดหรือการบันทึก หากต้องการวิเคราะห์หลังโหลด ให้เก็บคำเตือนไว้ในคอลเลกชันระหว่างขั้นตอนโหลด |
| *ฟอนต์ที่ฝังไว้ใน DOCX จะเป็นอย่างไร?* | ฟอนต์ที่ฝังไว้ถือว่ามีอยู่แล้ว จึงไม่มีการแทนที่ หากฟอนต์ที่ฝังเสียหาย Aspose.Words ยังจะส่งคำเตือน ซึ่งคุณสามารถดักจับได้เช่นกัน |
| *มีผลกระทบต่อประสิทธิภาพหรือไม่?* | น้อยมาก การตรวจสอบคำเตือนเป็นกระบวนการเบา ๆ; ค่าที่ใช้จริงคือการโหลดเอกสารเอง การเพิ่มโฟลเดอร์ฟอนต์อาจทำให้เวลาค้นเพิ่มขึ้นเล็กน้อย แต่เฉพาะการโหลดครั้งแรกเท่านั้น |

---

## เคล็ดลับระดับมืออาชีพ & สิ่งที่ควรหลีกเลี่ยง

- **เคล็ดลับ:** ตั้งค่า `recursive: true` เสมอเมื่อชี้ไปยังโฟลเดอร์ที่มีฟอนต์หลาย ๆ แบบ; มิฉะนั้นโฟลเดอร์ย่อยจะถูกละเลย  
- **ระวัง:** ความแตกต่างของตัวพิมพ์ใหญ่‑เล็กบน Linux ฟอนต์บน Windows ไม่แยกแยะตัวพิมพ์ แต่บน Linux แยกแยะ จึงใช้ชื่อที่ตรงกันหรือเพิ่มทั้งสองรูปแบบ  
- **จำไว้:** หากคุณรันในสภาพแวดล้อมคอนเทนเนอร์ ตรวจสอบให้แน่ใจว่าโฟลเดอร์ฟอนต์เป็นส่วนหนึ่งของอิมเมจหรือถูกเมานท์ในเวลารัน  
- **เคล็ดลับเพิ่มเติม:** เก็บคำเตือนใน `List<string>` หากต้องการสรุปให้ผู้ใช้สุดท้ายหรือบันทึกลงระบบมอนิเตอร์  

---

## สรุป

เราได้ครอบคลุม **วิธีตรวจจับการแทนที่** ของฟอนต์ที่หายไปใน Aspose.Words แสดงวิธีต่าง ๆ เพื่อ **จัดการฟอนต์ที่หายไป** และให้ตัวอย่างครบถ้วนที่คุณสามารถนำไปใช้ในโปรเจกต์ .NET ใดก็ได้ โดยการใช้เหตุการณ์ `FontSettings.Warning` คุณจะได้มองเห็นปัญหาฟอนต์แบบเรียลไทม์ และด้วยโฟลเดอร์สำรองหรือกฎการแทนที่ที่กำหนดเอง คุณจะทำให้ผลลัพธ์ออกมาตรงตามที่คาดหวัง

พร้อมก้าวต่อไปหรือยัง? ลองขยายโซลูชันให้ฝังฟอนต์สำรองลงใน PDF ที่สร้างขึ้นโดยอัตโนมัติ หรือเชื่อมต่อตัวจัดการคำเตือนกับระบบบันทึกศูนย์กลางสำหรับสายงานเอกสารขนาดใหญ่ รูปแบบที่เราได้พูดถึงวันนี้—การตรวจจับแบบอีเวนท์, การสำรองแบบราบรื่น, และการจัดการข้อผิดพลาดอย่างชัดเจน—สามารถนำไปใช้กับ API ของ Aspose อื่น ๆ ได้เช่นกัน ทำให้คุณพร้อมรับมือกับความท้าทายด้านฟอนต์ในทุกกรณี

มีคำถามเพิ่มเติมเกี่ยวกับการจัดการฟอนต์, การแปลง PDF, หรือเทคนิค Aspose.Words อื่น ๆ? แสดงความคิดเห็นด้านล่าง แล้วขอให้สนุกกับการเขียนโค้ด!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}