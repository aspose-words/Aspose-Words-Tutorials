---
category: general
date: 2026-05-04
description: เรียนรู้วิธีใช้การแทนที่ฟอนต์ของ Aspose เพื่อตรวจจับฟอนต์ที่หายไปเมื่อคุณโหลดเอกสาร
  Word และดึงรายละเอียดฟอนต์ที่หายไป—คู่มือขั้นตอนโดยละเอียด
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: th
og_description: เชี่ยวชาญการแทนที่ฟอนต์ของ Aspose เพื่อตรวจจับฟอนต์ที่หายไปเมื่อโหลดเอกสาร
  Word และดึงข้อมูลฟอนต์ที่หายไปพร้อมโค้ด C# อย่างครบถ้วน
og_title: การแทนที่ฟอนต์ของ Aspose – ตรวจจับฟอนต์ที่หายไปในเอกสาร Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'การแทนที่ฟอนต์ของ Aspose: ตรวจจับฟอนต์ที่หายไปในเอกสาร Word'
url: /th/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – ตรวจจับฟอนต์ที่หายไปในเอกสาร Word

เคยสงสัยไหมว่าทำไมเอกสาร Word ถึงดูผิดพลาดบนเครื่องอื่น? บ่อยครั้งสาเหตุคือฟอนต์ที่หายไป, และ **Aspose font substitution** คือเครื่องมือที่ช่วยให้คุณตรวจพบช่องโหว่เหล่านั้นก่อนที่มันจะกลายเป็นความหายนะด้านภาพ. ในบทแนะนำนี้เราจะอธิบายวิธี **detect missing fonts** ทันทีที่คุณ **load a Word document**, แล้ว **retrieve missing font** รายละเอียดเพื่อให้คุณแก้ไขหรือเปลี่ยนแทนได้.

เราจะครอบคลุมทุกอย่างตั้งแต่การตั้งค่า warning callback ไปจนถึงการดึงรายการฟอนต์ที่หายไปที่สะอาด. เมื่อจบคุณจะมี snippet C# ที่พร้อมใช้งานซึ่งบอกคุณอย่างชัดเจนว่าฟอนต์ใดบ้างที่ไม่ถูกพบ, และคุณจะเข้าใจว่าทำไมเรื่องนี้ถึงสำคัญต่อความเที่ยงตรงของเอกสาร.

---

## ข้อกำหนดเบื้องต้น – สิ่งที่คุณต้องมีก่อนเริ่ม

- **Aspose.Words for .NET** (แนะนำเวอร์ชัน v23.12 หรือใหม่กว่า).  
- สภาพแวดล้อมการพัฒนา .NET (Visual Studio, Rider, หรือ `dotnet` CLI).  
- ตัวอย่างไฟล์ DOCX ที่ตั้งใจใช้ฟอนต์ที่คุณไม่ได้ติดตั้ง—ชื่อว่า `DocumentWithMissingFont.docx`.  
- ความรู้พื้นฐาน C#—ไม่ต้องซับซ้อน, เพียงความสามารถในการรันแอปคอนโซล.

หากสิ่งใดข้างต้นไม่คุ้นเคย, ให้หยุดและติดตั้งแพคเกจ NuGet:

```bash
dotnet add package Aspose.Words
```

เท่านี้แค่นั้น. ไม่ต้องฟอนต์เพิ่มเติม, ไม่ต้องบริการภายนอก.

## ขั้นตอนที่ 1: โหลดเอกสาร Word (และเรียกการตรวจสอบฟอนต์)

สิ่งแรกที่คุณทำคือ **load a Word document**. Aspose.Words จะทำการแยกไฟล์และหากไม่สามารถหาไฟต์ฟอนต์ที่อ้างอิงได้, มันจะเพิ่มคำเตือน *FontSubstitution*. นี่คือโค้ดที่ทำการโหลด:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **ทำไมเรื่องนี้ถึงสำคัญ:** การโหลดเอกสารตั้งแต่แรกทำให้ Aspose มีโอกาสสแกนทุกส่วนของข้อความ, สไตล์, และออบเจ็กต์ที่ฝังอยู่. หากฟอนต์ไม่พบในระบบหรือในโฟลเดอร์ฟอนต์ที่กำหนดเอง, คุณจะได้รับคำเตือนในภายหลัง.

## ขั้นตอนที่ 2: แนบ Warning Callback เพื่อจับเหตุการณ์ Substitution

Aspose.Words ใช้กลไก callback เพื่อแจ้งคุณเกี่ยวกับปัญหาเช่นฟอนต์ที่หายไป. โดยการกำหนดการทำงานของ `IWarningCallback` ให้กับ `doc.WarningCallback`, คุณสามารถดักจับคำเตือนแต่ละรายการเมื่อเกิดขึ้น.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **เคล็ดลับ:** คุณสามารถแนบหลาย callback (เช่น logging, UI updates) โดยการห่อหุ้มในรูปแบบ composite, แต่สำหรับบทแนะนำนี้การใช้ callback เดียวทำให้เรื่องชัดเจน.

## ขั้นตอนที่ 3: Implement the Font Substitution Warning Callback

ตอนนี้เราจะกำหนดคลาสที่ทำงานจริง. Callback จะรับอ็อบเจ็กต์ `WarningInfo`; เราจะกรองสำหรับ `WarningType.FontSubstitution` และเก็บคำอธิบายไว้ใช้ภายหลัง.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **กำลังเกิดอะไรขึ้น:** เมื่อ Aspose พบฟอนต์ที่หายไป, มันจะสร้างคำเตือนเช่น “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Callback ของเราจะพิมพ์บรรทัดนั้นและบันทึกไว้.

## ขั้นตอนที่ 4: ประมวลผลเอกสาร (ทางเลือก) และรวบรวมฟอนต์ที่หายไป

หากคุณต้องการเพียง **detect missing fonts**, ขั้นตอนการโหลดก็เพียงพอ—คำเตือนจะถูกส่งโดยอัตโนมัติ. อย่างไรก็ตาม, นักพัฒนาจำนวนมากยังต้อง **retrieve missing font** หลังจากทำบางการดำเนินการ (เช่น การบันทึก, การแปลง). ด้านล่างเราบังคับให้ทำการดำเนินการเล็กน้อย—บันทึกเป็น PDF—เพื่อให้แน่ใจว่าคำเตือนทั้งหมดถูกส่ง, แล้วเราจะดึงข้อความที่เก็บไว้.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **ผลลัพธ์คอนโซลที่คาดหวัง** (ตัวอย่าง):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

สังเกตว่าทุกบรรทัดบอกอย่างชัดเจนถึงฟอนต์ต้นฉบับและฟอนต์สำรองที่ Aspose เลือก. นั่นคือแก่นของการรายงาน **aspose font substitution**.

## ขั้นตอนที่ 5: ขั้นสูง – ใช้แหล่งฟอนต์แบบกำหนดเองเพื่อลดการแทนที่

บางครั้งคุณ *มี* ฟอนต์ที่หายไป, แต่ไม่ได้อยู่ในโฟลเดอร์ระบบเริ่มต้น. Aspose.Words ให้คุณชี้ไปยังไดเรกทอรีกำหนดเองผ่าน `FontSettings`. การเพิ่มขั้นตอนนี้สามารถลดจำนวนคำเตือนการแทนที่ได้อย่างมาก.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **ทำไมต้องเพิ่มขั้นตอนนี้?** หากคุณแจกจ่ายเอกสารข้ามเครื่อง, การบรรจุฟอนต์ที่ต้องการในโฟลเดอร์ที่รู้จักทำให้ลักษณะภาพเหมือนกันทุกที่. มันยังทำให้ขั้นตอน **detect missing fonts** ของคุณแม่นยำขึ้นเพราะ Aspose ตรวจสอบโฟลเดอร์นั้นก่อนที่จะใช้ฟอนต์สำรอง.

## ตัวอย่างการทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน, นี่คือโปรแกรมคอนโซลที่พร้อมคัดลอกและวาง. บันทึกเป็น `Program.cs` แล้วรันด้วย `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**สิ่งที่คุณควรเห็น:** หาก DOCX ต้นทางอ้างอิงฟอนต์ที่คุณไม่มี, คอนโซลจะพิมพ์แต่ละบรรทัดการแทนที่ตามด้วยสรุปสั้น. หากฟอนต์ทั้งหมดมีอยู่, คุณจะได้รับข้อความ “No missing fonts were detected.”

## ข้อผิดพลาดทั่วไป & วิธีหลีกเลี่ยง

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **ไม่มีคำเตือนปรากฏ** | เอกสารใช้เฉพาะฟอนต์ระบบ, หรือคุณได้เพิ่มโฟลเดอร์กำหนดเองที่มีฟอนต์ที่หายไปแล้ว. | ตรวจสอบว่า DOCX จริง ๆ แล้วอ้างอิงฟอนต์ที่ไม่มีอยู่. คุณสามารถเปิดใน Word แล้วเปลี่ยนย่อหน้าหนึ่งเป็นฟอนต์หายาก (เช่น “Papyrus”). |
| **ข้อความซ้ำ** | ฟอนต์เดียวกันถูกใช้หลายรัน, ทำให้เกิดคำเตือนหลายครั้ง. | ทำการลบรายการซ้ำด้วย `Distinct()` หากคุณต้องการชุดที่ไม่ซ้ำ. |
| **ประสิทธิภาพลดลงในเอกสารขนาดใหญ่** | แต่ละคำเตือนถูกประมวลผลบน UI thread. | รันการโหลดในงานเบื้องหลังหรือใช้ `Parallel.ForEach` สำหรับการประมวลผลต่อ. |
| **ฟอนต์สำรองไม่ถูกต้อง** | ฟอนต์สำรองเริ่มต้นของ Aspose อาจไม่ตรงกับแบรนด์ของคุณ. | ตั้งค่า `FontSettings.SubstitutionSettings.DefaultFontName` เป็นฟอนต์สำรองที่ต้องการ (เช่น “Calibri”). |

## การขยายโซลูชัน – ส่งออกฟอนต์ที่หายไปเป็น JSON

หากคุณกำลังสร้างเว็บเซอร์วิสที่ต้องรายงานฟอนต์ที่หายไปกลับไปยังไคลเอนต์, การแปลงรายการเป็น JSON ทำได้ง่าย:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

## สรุป

ในคู่มือนี้เราได้สาธิต **Aspose font substitution** ตั้งแต่ต้นจนจบ: การโหลดเอกสาร Word, การแนบ warning callback, การจับเหตุการณ์ *detect missing fonts* แต่ละรายการ, และสุดท้าย **retrieve missing font** เพื่อการรายงานหรือแก้ไข. ด้วยการเพิ่มโฟลเดอร์ฟอนต์กำหนดเองแบบเลือกใช้ คุณสามารถลดรายการการแทนที่, และด้วยบรรทัดเพิ่มเล็กน้อยคุณยังสามารถส่งออกผลลัพธ์เป็น JSON ได้.

จำไว้ว่า ความสมบูรณ์ของภาพในเอกสารของคุณขึ้นอยู่กับฟอนต์ที่ใช้. ด้วยเทคนิคที่แสดงในนี้, คุณจะไม่ต้องประหลาดใจกับฟอนต์สำรองที่ไม่คาดคิดอีกต่อไป.  

พร้อมก้าวต่อไปหรือยัง? ลองผสานตรรกะนี้เข้าไปใน pipeline การประมวลผลเอกสารที่ใหญ่ขึ้น, หรือสำรวจคุณสมบัติอื่นของ Aspose.Words เช่นการฝังฟอนต์ (`doc.FontSettings.EmbeddedFonts`). ความเป็นไปได้ไม่มีที่สิ้นสุด, และผู้ใช้ของคุณจะขอบคุณคุณสำหรับผลลัพธ์ที่เรียบหรู.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}