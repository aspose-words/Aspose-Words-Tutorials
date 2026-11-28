---
category: general
date: 2026-04-04
description: เรียนรู้วิธีจับคำเตือน, ตรวจจับฟอนต์ที่หายไป, และวิธีบันทึกเหตุการณ์การแทนที่โดยใช้
  Aspose.Words LoadOptions ใน C#
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: th
og_description: วิธีจับคำเตือน, ตรวจจับฟอนต์ที่หายไป, และวิธีบันทึกเหตุการณ์การแทนที่โดยใช้
  Aspose.Words LoadOptions ใน C#
og_title: วิธีจับคำเตือนใน C# – ตรวจจับฟอนต์ที่หายไปและบันทึกการแทนที่
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: วิธีดักจับคำเตือนใน C# – ตรวจจับฟอนต์ที่หายไปและบันทึกการแทนที่
url: /th/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีจับคำเตือนใน C# – ตรวจจับฟอนต์ที่หายไปและบันทึกการแทนที่

เคยสงสัย **วิธีจับคำเตือน** ที่ปรากฏขึ้นเมื่อคุณโหลดเอกสาร Word ที่มีฟอนต์หายไปหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายโครงการจริง ฟอนต์มักหายไประหว่างการย้ายระบบ และการใช้ฟอนต์สำรองโดยอัตโนมัติอาจทำให้การจัดวางของคุณเสียหาย ข่าวดีคือ Aspose.Words มีวิธีที่สะอาดและง่ายต่อการรับฟังคำเตือนเหล่านั้น ตรวจจับฟอนต์ที่หายไป และแม้กระทั่งบันทึกการแทนที่ทุกครั้ง เพื่อให้คุณสามารถแก้ไขแหล่งที่มาภายหลังได้

ในบทแนะนำนี้ เราจะพาคุณผ่านโซลูชันที่ครบถ้วนพร้อมใช้งานที่แสดง **วิธีจับคำเตือน**, สาธิต **การตรวจจับฟอนต์ที่หายไป**, และอธิบาย **วิธีบันทึกการแทนที่** ของเหตุการณ์ต่าง ๆ เมื่อจบคุณจะมีตัวจัดการคำเตือนที่นำกลับมาใช้ใหม่ได้, อ็อบเจ็กต์ `LoadOptions` ที่กำหนดค่าอย่างเต็มที่, และตัวอย่างผลลัพธ์คอนโซลที่คุณสามารถตรวจสอบได้

> **Prerequisite:** คุณต้องมี Aspose.Words for .NET (เวอร์ชัน 24.x หรือใหม่กว่า) ติดตั้งผ่าน NuGet และสภาพแวดล้อมการพัฒนา C# เบื้องต้น (Visual Studio 2022 หรือ VS Code ทำงานได้ดี)

## วิธีจับคำเตือนเมื่อโหลดเอกสาร

หัวใจของโซลูชันคือคลาสที่ทำการ implement `IWarningCallback`. Aspose.Words จะเรียก callback นี้โดยอัตโนมัติสำหรับคำเตือนทุกประเภทที่เกิดขึ้นระหว่างการโหลดเอกสาร รวมถึงคำเตือนการแทนที่ฟอนต์ด้วย

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Why this step?**  
> โดยการกรองด้วย `WarningType.FontSubstitution` เราจะหลีกเลี่ยงความรกจากคำเตือนที่ไม่เกี่ยวข้อง (เช่น ฟีเจอร์ที่เลิกใช้). สิ่งนี้ทำให้บันทึกมุ่งเน้นไปที่ปัญหาที่คุณสนใจโดยตรง—ฟอนต์ที่หายไป

## ตรวจจับฟอนต์ที่หายไปด้วย Aspose.Words

เมื่อเอกสารอ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเครื่อง, Aspose.Words จะทำการแทนที่ด้วยฟอนต์ที่ใกล้เคียงที่สุดและส่งคำเตือน ตัวจัดการของเราที่กล่าวถึงข้างต้นจะจับเหตุการณ์แต่ละครั้ง, ทำให้ **ตรวจจับฟอนต์ที่หายไป** อย่างมีประสิทธิภาพ

เพื่อดูการทำงานจริง เราต้องกำหนดค่า `LoadOptions` และเชื่อมต่อ handler:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tip:** หากคุณต้องการเก็บคำเตือนเพื่อประมวลผลในภายหลัง (เช่น เขียนลงไฟล์), ให้แทนที่ `Console.WriteLine` ด้วยโค้ดที่เพิ่มข้อความลงใน `List<string>`.

## วิธีบันทึกเหตุการณ์การแทนที่

การบันทึกนั้นง่ายเพียงแค่ส่งออกผลลัพธ์ของคำเตือนไปยังที่เก็บข้อมูลถาวร ตัวอย่างสั้น ๆ ด้านล่างจะเขียนคำเตือนการแทนที่แต่ละครั้งลงในไฟล์ข้อความชื่อ `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Why log to a file?**  
> บันทึกที่คงอยู่ช่วยให้คุณตรวจสอบปัญหาฟอนต์ในหลาย ๆ ครั้ง, ทำการแจ้งเตือนอัตโนมัติ, หรือส่งข้อมูลเข้าสู่การตรวจสอบของ pipeline การสร้าง

## ตัวอย่างการทำงานเต็มรูปแบบ

เมื่อรวมทุกอย่างเข้าด้วยกัน นี่คือแอปพลิเคชันคอนโซลแบบอิสระที่คุณสามารถคัดลอก, วาง, และรันได้ มันสาธิต **วิธีจับคำเตือน**, **ตรวจจับฟอนต์ที่หายไป**, และ **วิธีบันทึกการแทนที่** ทั้งหมดในขั้นตอนเดียว

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### ผลลัพธ์คอนโซลที่คาดหวัง

หาก `input.docx` อ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง, คุณจะเห็นข้อความประมาณนี้:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

หากคุณเปลี่ยนไปใช้ `FileLoggingWarningHandler`, บรรทัดเดียวกันจะปรากฏในไฟล์ `font-warnings.log` พร้อมกับเวลาที่บันทึก

![ผลลัพธ์คอนโซลของการจับคำเตือน](image-placeholder.png)

## คำถามทั่วไปและกรณีขอบ

### ถ้าฉันต้องการจับ *ทุก* คำเตือน, ไม่ใช่แค่การแทนที่ฟอนต์?

เพียงลบการตรวจสอบ `if (info.Type == WarningType.FontSubstitution)` ตัว callback จะรับคำเตือนทุกประเภท (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, เป็นต้น) จากนั้นคุณสามารถแยกกรณีตาม `info.Type` เพื่อจัดการแต่ละกรณีแตกต่างกันได้

### วิธีนี้ทำงานกับ PDF หรือเฉพาะเอกสาร Word เท่านั้น?

`LoadOptions` และ `IWarningCallback` เป็นส่วนหนึ่งของ Aspose.Words, ดังนั้นจึงใช้ได้กับรูปแบบที่เข้ากันกับ Word (`.docx`, `.doc`, `.rtf`, `.html`). สำหรับ PDF คุณจะต้องใช้กลไกคำเตือนของ Aspose.PDF เอง

### ฉันจะยกเลิกการแสดงคำเตือนแทนการบันทึกได้อย่างไร?

ตั้งค่า `LoadOptions.WarningCallback = null` หรือ implement callback แต่ปล่อยให้เมธอดว่างเปล่า ไลบรารีจะยังคงทำการแทนที่โดยเงียบ ๆ

### เรื่องความปลอดภัยของเธรดล่ะ?

อินสแตนซ์ของ callback จะถูกเรียกบนเธรดเดียวกับที่โหลดเอกสาร, ดังนั้นคุณไม่จำเป็นต้องทำการซิงโครไนซ์เพิ่มเติม เว้นแต่คุณจะใช้ handler ร่วมกันในหลายการโหลดแบบขนาน ในกรณีนั้นควรปกป้องทรัพยากรที่ใช้ร่วมกัน (เช่น ไฟล์บันทึก) ด้วย lock หรือใช้คอลเลกชันแบบ concurrent

## สรุป

เราได้อธิบาย **วิธีจับคำเตือน** จาก Aspose.Words, แสดงให้คุณเห็น **การตรวจจับฟอนต์ที่หายไป**, และอธิบาย **วิธีบันทึกเหตุการณ์การแทนที่** เพื่อการวิเคราะห์ในภายหลัง โดยการเชื่อม `IWarningCallback` แบบง่ายเข้าไปใน `LoadOptions` คุณจะได้มองเห็นปัญหาที่เกี่ยวกับฟอนต์อย่างครบถ้วนโดยไม่ทำให้โค้ดของคุณรก

ขั้นตอนต่อไป? ลองขยาย logger ให้ส่งอีเมล, ผสานรวมกับ Azure Monitor, หรือทำการติดตั้งฟอนต์ที่หายไปโดยอัตโนมัติบนเซิร์ฟเวอร์การสร้าง คุณอาจสำรวจประเภทคำเตือนอื่น ๆ — `WarningType.DegradedDocument` สามารถแจ้งเตือนคุณเกี่ยวกับฟีเจอร์ที่ไม่ผ่านการแปลงได้

มีคำถามเพิ่มเติมเกี่ยวกับการจัดการฟอนต์หรือ Aspose.Words โดยทั่วไปหรือไม่? แสดงความคิดเห็นหรือเปิดประเด็นใหม่ในฟอรั่มของ Aspose. ขอให้สนุกกับการเขียนโค้ด, และขอให้เอกสารของคุณแสดงผลด้วยแบบอักษรที่ถูกต้องเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}