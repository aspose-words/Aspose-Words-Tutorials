---
category: general
date: 2026-02-12
description: สร้างตัวจัดการการเตือนฟอนต์เพื่อตรวจจับฟอนต์ที่หายไปและติดตามฟอนต์ที่หายไปใน
  Aspose.Words. เรียนรู้วิธีบันทึกการเตือนอย่างมีประสิทธิภาพ.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: th
og_description: สร้างตัวจัดการคำเตือนฟอนต์ใน C# เพื่อตรวจจับฟอนต์ที่หายไปและเรียนรู้วิธีบันทึกคำเตือนเมื่อ
  Aspose.Words แทนที่ฟอนต์
og_title: สร้างตัวจัดการคำเตือนฟอนต์ – ตรวจจับฟอนต์ที่หายไป
tags:
- Aspose.Words
- C#
- Document Processing
title: สร้างตัวจัดการคำเตือนฟอนต์ – ตรวจจับฟอนต์ที่หายไปใน C#
url: /th/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้าง Font Warning Handler – ตรวจจับฟอนต์ที่หายไปใน C#

เคยต้องการ **create font warning handler** เพราะเอกสาร Word แทนที่ฟอนต์โดยไม่แจ้งเตือนหรือไม่? คุณไม่ได้เป็นคนเดียว เมื่อ Aspose.Words โหลด DOCX ที่อ้างอิงฟอนต์ที่ไม่มีบนเซิร์ฟเวอร์ มันจะเปลี่ยนไปใช้ฟอนต์เริ่มต้นโดยเงียบ ๆ — ทำให้การจัดหน้าเสียหายเล็กน้อย  

ในบทเรียนนี้เราจะสาธิตให้คุณเห็นอย่างชัดเจนว่า **detect missing fonts**, **track missing fonts**, และ **how to log warnings** ทำอย่างไร เพื่อให้คุณสามารถจับการแทนที่ฟอนต์ก่อนที่มันจะทำให้เกิดปัญหาได้ เมื่อจบคุณจะมี warning handler ที่สามารถนำกลับมาใช้ใหม่ได้ ซึ่งพิมพ์เหตุการณ์การแทนที่ฟอนต์ทุกครั้งลงคอนโซล (หรือ logger ใด ๆ ที่คุณต้องการ) ไม่มีความลับ เพียงโค้ดที่ชัดเจนและทำได้จริง

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (API จะเหมือนกันสำหรับ .NET Framework 4.6+)
- ติดตั้ง Aspose.Words for .NET (`dotnet add package Aspose.Words`)
- ไฟล์ Word ที่อ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของคุณ (เช่น `MissingFont.docx`)

ถ้าคุณมีทั้งหมดนี้แล้ว เยี่ยม—มาเริ่มกันเลย

## ขั้นตอนที่ 1: ตั้งค่า LoadOptions พร้อม Warning Callback  

สิ่งแรกที่คุณทำเมื่ออยาก **create font warning handler** คือบอก Aspose.Words ให้เรียก callback ทุกครั้งที่พบปัญหา `LoadOptions` คือคอนเทนเนอร์สำหรับการตั้งค่านี้

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**ทำไมสิ่งนี้ถึงสำคัญ:**  
`LoadOptions` เป็นที่เดียวที่คุณสามารถต่อ `IWarningCallback` ได้ หากไม่มี Aspose.Words จะบันทึกคำเตือนภายในแต่คุณจะไม่เห็นเลย โดยการกำหนด `FontWarningHandler` เราจะได้การควบคุมเต็มที่เมื่อฟอนต์ที่หายไปถูกแทนที่

## ขั้นตอนที่ 2: สร้างคลาส FontWarningHandler  

ตอนนี้เราจะ **create font warning handler** จริง ๆ โค้ดคลาสนี้ implements `IWarningCallback` และรับอ็อบเจ็กต์ `WarningInfo` สำหรับทุกคำเตือนที่ Aspose.Words ส่งออกมา

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**คำอธิบาย:**  
- `info.Type` บอกประเภทของคำเตือน เราสนใจ `WarningType.FontSubstitution` เพราะมันบ่งบอกว่าฟอนต์หายไป  
- `info.Description` มีข้อความที่คนอ่านเข้าใจได้ เช่น *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- การเขียนลง `Console.WriteLine` ทำให้เรา **log warnings** ทันที ในแอปจริงคุณอาจเปลี่ยนเป็น `ILogger` ตัวเขียนไฟล์ หรือบริการ telemetry

> **Pro tip:** หากต้องการเก็บฟอนต์ที่หายไปทั้งหมดเพื่อรายงานภายหลัง ให้เก็บ `info.Description` ลงใน `List<string>` แทนการพิมพ์ออก

## ขั้นตอนที่ 3: โหลดเอกสารโดยใช้ LoadOptions ที่กำหนดค่าแล้ว  

เมื่อ callback ถูกตั้งค่าไว้ การโหลดเอกสารจะทำให้ handler ของเราถูกเรียกอัตโนมัติทุกครั้งที่ฟอนต์หายไป

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**สิ่งที่คุณจะเห็น:**  
การรันโปรแกรมจะแสดงผลคล้ายกับนี้:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

บรรทัดนั้นยืนยันว่าคุณ **detected missing fonts** สำเร็จและกำลัง **track missing fonts** แบบเรียลไทม์

## ขั้นตอนที่ 4: ตรวจสอบว่า Handler ทำงานกับสถานการณ์ต่าง ๆ  

ง่ายที่จะคิดว่า handler ทำงานเฉพาะไฟล์ DOCX เท่านั้น แต่ Aspose.Words รองรับหลายรูปแบบ ลองโหลด PDF ที่อ้างอิงฟอนต์ฝังอยู่ หรือไฟล์ `.doc` เก่า ๆ Callback เดียวกันจะทำงานสำหรับรูปแบบใดก็ได้ที่ผ่าน pipeline การแก้ไขฟอนต์

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

หาก PDF อ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง คุณจะได้รับข้อความคอนโซลเดียวกัน นี้แสดงให้เห็นว่าโซลูชัน **create font warning handler** ของคุณเป็นอิสระต่อรูปแบบไฟล์

## ขั้นตอนที่ 5: ขยาย Handler – บันทึกลงไฟล์  

การแสดงผลบนคอนโซลสะดวกสำหรับสาธิต แต่โค้ดในผลิตจริงมักจะบันทึกลงไฟล์ log นี่คือตัวอย่างการปรับเล็กน้อย

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

ตอนนี้ทุกครั้งที่ฟอนต์ถูกแทนที่ ข้อความจะถูกเพิ่มลงใน `font-warnings.log` ซึ่งตอบโจทย์ส่วน **how to log warnings** ของโจทย์และให้คุณมีบันทึกตรวจสอบที่คงอยู่

## ขั้นตอนที่ 6: รวมทุกอย่างเข้าด้วยกัน – ตัวอย่างเต็มที่สามารถรันได้  

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถ copy‑paste ไปยังแอปคอนโซลได้ ไม่มีส่วนใดหายไป เพียงเปลี่ยนเส้นทางไฟล์ให้เป็นเอกสารของคุณเอง

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:**  

- คอนโซลพิมพ์แต่ละบรรทัดของการแทนที่ฟอนต์  
- `font-warnings.log` มีบันทึกพร้อมเวลาของเหตุการณ์ฟอนต์ที่หายไปทุกครั้ง  
- ไฟล์ `output.pdf` ถูกสร้างด้วยฟอนต์ที่แทนที่แล้ว ทำให้การแปลงสำเร็จแม้ฟอนต์ต้นฉบับจะไม่มีอยู่

## คำถามทั่วไปและกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| *What if I want to ignore certain fonts?* | ภายใน `Warning` ตรวจสอบ `info.Description` เพื่อหาชื่อฟอนต์และ `return;` ทันทีสำหรับฟอนต์ที่คุณพิจารณาให้ยอมรับ |
| *Will the handler fire for embedded fonts?* | ไม่—ฟอนต์ที่ฝังอยู่ในเอกสารจะพร้อมใช้งานเสมอ ดังนั้นจะไม่มีคำเตือนการแทนที่ |
| *Can I capture other warning types (e.g., image‑resolution issues)?* | แน่นอน ลบเงื่อนไข `if (info.Type == WarningType.FontSubstitution)` หรือเพิ่มบล็อก `if` สำหรับ `WarningType.ImageResolution` |
| *Is the handler thread‑safe?* | การทำงานตัวอย่างที่ให้มาจะเขียนไฟล์โดยไม่มีการซิงโครไนซ์ สำหรับสถานการณ์หลายเธรด ควรห่อการเขียนไฟล์ด้วย lock หรือใช้ logger ที่รองรับ concurrent |

## ขั้นตอนต่อไป  

ตอนนี้คุณรู้แล้วว่า **how to log warnings** สำหรับฟอนต์ที่หายไปแล้ว คุณอาจต้องการ:

- **Detect missing fonts** ระหว่างกระบวนการนำเข้าจำนวนมากและสร้างรายงานสรุป  
- **Track missing fonts** ข้ามหลายเอกสารและส่งอีเมลแจ้งเตือนเมื่อฟอนต์ใดฟอนต์หนึ่งปรากฏบ่อย  
- **Integrate with a monitoring system** (เช่น Azure Application Insights) เพื่อแสดงแนวโน้มการแทนที่ฟอนต์ตามเวลา  

ส่วนขยายทั้งหมดนี้สร้างบนพื้นฐาน `IWarningCallback` ที่เราได้สร้างไว้

---

*Happy coding! หากคุณเจอปัญหา—เช่นโฟลเดอร์ฟอนต์แบบกำหนดเองหรือแชร์บนเครือข่าย—ฝากคอมเมนต์ไว้ด้านล่าง ชุมชน (และผม) ยินดีช่วยคุณปรับแต่งกลยุทธ์การแจ้งเตือนฟอนต์ของคุณ* 

![create font warning handler example](image-placeholder.png "create font warning handler example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}