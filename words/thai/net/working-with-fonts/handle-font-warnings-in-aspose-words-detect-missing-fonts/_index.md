---
category: general
date: 2026-02-28
description: เรียนรู้วิธีจัดการคำเตือนฟอนต์และตรวจจับฟอนต์ที่หายไปใน Aspose.Words
  ด้วย C# คู่มือแบบขั้นตอน‑ต่อ‑ขั้นตอนพร้อมโค้ดเต็ม.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: th
og_description: จัดการคำเตือนฟอนต์ใน Aspose.Words และตรวจจับฟอนต์ที่หายไปด้วยตัวอย่าง
  C# ที่พร้อมใช้งาน ทำตามขั้นตอนและดูผลลัพธ์
og_title: จัดการคำเตือนฟอนต์ใน Aspose.Words – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Loading
title: จัดการคำเตือนฟอนต์ใน Aspose.Words – ตรวจจับฟอนต์ที่หายไป
url: /th/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# จัดการคำเตือนฟอนต์ใน Aspose.Words – ตรวจจับฟอนต์ที่หายไป

เคยต้อง **จัดการคำเตือนฟอนต์** ขณะโหลดเอกสาร Word แล้วสงสัยว่าทำไมข้อความบางส่วนดูแปลกหรือไม่? คุณไม่ได้เป็นคนเดียว ฟอนต์ที่หายไปจะทำให้เกิดคำเตือนการแทนที่ซึ่งอาจทำให้รูปแบบการแสดงผลเสียหายโดยไม่รู้สึก และหากคุณไม่ **ตรวจจับฟอนต์ที่หายไป** คุณจะไม่มีทางรู้ว่าอะไรผิดพลาด

ในบทแนะนำนี้เราจะสาธิตวิธีที่เป็นประโยชน์ในการ **จัดการคำเตือนฟอนต์** ด้วย `IWarningCallback` ของ Aspose.Words. เมื่อจบคู่มือคุณจะสามารถตรวจจับเหตุการณ์การแทนที่ฟอนต์ทุกครั้ง, บันทึกมัน, และแม้กระทั่งตัดสินใจว่าจะยกเลิกการโหลดหรือไม่. ไม่ต้องอ้างอิงเอกสารภายนอก, มีตัวอย่างเดียวที่พร้อมคัดลอกและวาง

## สิ่งที่คุณจะได้เรียนรู้

- ตั้งค่าตัวจัดการคำเตือนแบบกำหนดเองที่ตอบสนองเฉพาะการแจ้งเตือนการแทนที่ฟอนต์เท่านั้น  
- แนบตัวจัดการเข้ากับ `LoadOptions` เพื่อให้การโหลดเอกสารทุกครั้งผ่านมัน  
- ตรวจสอบผลลัพธ์ในคอนโซลและเข้าใจความหมายของแต่ละคำเตือน  

**Prerequisites**

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+ ด้วย)  
- Aspose.Words for .NET ที่ติดตั้งผ่าน NuGet (`Install-Package Aspose.Words`)  
- ไฟล์ Word ที่อ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของคุณ (เช่น ฟอนต์องค์กรแบบกำหนดเอง)  

หากคุณยังไม่มีส่วนใดส่วนหนึ่งเหล่านี้, ให้ดาวน์โหลดตอนนี้—ถ้าไม่มี, เรามาเริ่มกันเลย

## วิธีจัดการคำเตือนฟอนต์ใน Aspose.Words

ด้านล่างเป็นโปรแกรมเต็มที่สามารถรันได้ รวมทุกอย่างตั้งแต่ `using` จนถึงเมธอด `Main` เพื่อให้คุณสามารถวางลงในแอปคอนโซลและกด **F5** ได้ทันที

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Expected console output** (assuming the document uses a font you don’t have installed):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

หากเอกสารไม่มี **ฟอนต์ที่หายไป**, บรรทัดคำเตือนจะไม่ปรากฏ—ดังนั้นคุณจึง **ตรวจจับฟอนต์ที่หายไป** ได้เฉพาะเมื่อจำเป็น

### ทำไมวิธีนี้ถึงได้ผล

Aspose.Words จะโยน `WarningInfo` สำหรับทุกปัญหาที่ไม่สำคัญที่พบขณะพาร์สไฟล์. โดยการทำ `IWarningCallback` คุณจะได้ hook เข้าไปใน pipeline นั้น. ธง `WarningType.FontSubstitution` บอกคุณอย่างชัดเจนเมื่อไลบรารีต้องแทนที่ฟอนต์ที่ร้องขอด้วยฟอนต์สำรอง. นี่เป็นวิธีที่เชื่อถือได้ที่สุดในการ **จัดการคำเตือนฟอนต์** เพราะทำงาน *ระหว่าง* การโหลด, ก่อนที่คุณจะสัมผัสกับ Document Object Model

## ตรวจจับฟอนต์ที่หายไปโดยไม่ทำให้แอปพัง

บางครั้งคุณอาจต้องการถือว่าฟอนต์ที่หายไปเป็นข้อผิดพลาดร้ายแรง—อาจเป็นเพราะแนวทางแบรนด์ของคุณห้ามการแทนที่ใด ๆ. คุณสามารถแก้ไขตัวจัดการให้โยนข้อยกเว้นแทนการบันทึกได้:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

ตอนนี้บล็อก `try…catch` รอบ `new Document(...)` จะจับปัญหา, ให้คุณตัดสินใจว่าจะยกเลิก, ใช้ฟอนต์สำรอง, หรือแสดงข้อความให้ผู้ใช้ทราบ

## โบนัส: แสดงคำเตือนในแอป UI

หากคุณกำลังสร้างแอป WinForms หรือ WPF, ให้แทนที่ `Console.WriteLine` ด้วยการเรียกที่เป็นมิตรกับ UI:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

วิธีนี้ผู้ใช้ปลายทางจะเห็นคำเตือนทันที, และคุณยังคง **จัดการคำเตือนฟอนต์** อย่างสม่ำเสมอในทุกแพลตฟอร์ม

## ข้อผิดพลาดทั่วไป & เคล็ดลับระดับมืออาชีพ

- **Pitfall:** ลืมตั้งค่า `WarningCallback`. พฤติกรรมเริ่มต้นคือการละเลยคำเตือนฟอนต์, ดังนั้นคุณจะไม่เห็นมันเลย  
  **Pro tip:** ควรสร้างอินสแตนซ์ `LoadOptions` เสมอแม้ว่าคุณจะต้องการเพียงตัวจัดการคำเตือนเท่านั้น. มันมีค่าใช้จ่ายต่ำและชัดเจน  

- **Pitfall:** ใช้ตัวคั่นเส้นทางที่ไม่ถูกต้องบนระบบปฏิบัติการที่ไม่ใช่ Windows  
  **Pro tip:** ใช้ `Path.Combine` หรือ raw string literal (`@"C:\Docs\MissingFont.docx"` ทำงานบน Windows; บน Linux ใช้ `"/home/user/docs/MissingFont.docx"`)  

- **Pitfall:** สมมติว่าคำเตือนจะเกิดขึ้นสำหรับฟอนต์ที่ฝังอยู่  
  **Pro tip:** ฟอนต์ที่ฝังอยู่ถือว่าเป็นฟอนต์ที่มีอยู่, ดังนั้นจะไม่มีคำเตือนการแทนที่. ทดสอบด้วยฟอนต์ที่ *หายจริงๆ* เพื่อดูการทำงานของตัวจัดการ  

- **Pitfall:** บันทึกคำเตือนทุกประเภทเกินความจำเป็น  
  **Pro tip:** กรองด้วย `WarningType.FontSubstitution` ตามที่แสดง—วิธีนี้ทำให้คอนโซลสะอาดและเน้นไปที่สถานการณ์ **ตรวจจับฟอนต์ที่หายไป**  

## สรุปตัวอย่างทำงานเต็ม

นี่คือโปรแกรมทั้งหมดอีกครั้ง, ครั้งนี้ไม่มีคอมเมนต์สำหรับผู้ที่ต้องการมุมมองที่สะอาด:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

คัดลอก, วาง, รัน—คอนโซลของคุณจะ **จัดการคำเตือนฟอนต์** และ **ตรวจจับฟอนต์ที่หายไป** โดยอัตโนมัติ

## ขั้นตอนต่อไป

- **Log to a file:** แทนที่ `Console.WriteLine` ด้วย logger (เช่น NLog) เพื่อการติดตามระดับการผลิต  
- **Batch processing:** วนลูปผ่านโฟลเดอร์ของเอกสาร, รวบรวมเหตุการณ์การแทนที่ฟอนต์ทั้งหมดในรายงาน CSV  
- **Automatic font installation:** เชื่อมต่อกับตัวจัดการคำเตือนเพื่อดาวน์โหลดฟอนต์ที่หายไปจากคลังของบริษัทก่อนการโหลดดำเนินต่อ  

แต่ละส่วนขยายเหล่านี้สร้างบนแนวคิดหลักของการ **จัดการคำเตือนฟอนต์** อย่างสะอาดและนำกลับมาใช้ใหม่ได้

---

*ขอให้สนุกกับการเขียนโค้ด! หากคุณเจอปัญหาใด ๆ ขณะพยายาม **ตรวจจับฟอนต์ที่หายไป**, ฝากคอมเมนต์ไว้ด้านล่างได้เลย. ฉันยินดีช่วยแก้ไขปัญหา*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}