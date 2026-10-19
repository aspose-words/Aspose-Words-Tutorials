---
category: general
date: 2026-01-03
description: วิธีตรวจจับฟอนต์ใน Aspose.Words และจัดการคำเตือนโดยใช้การตั้งค่าแบบอักษรของ
  Aspose – คู่มือขั้นตอนต่อขั้นตอนสำหรับนักพัฒนา
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: th
og_description: วิธีตรวจจับฟอนต์ใน Aspose.Words และกำหนดค่าการเตือนด้วยการตั้งค่าแบบอักษรของ
  Aspose เรียนรู้กระบวนการทำงานทั้งหมดในไม่กี่นาที.
og_title: วิธีตรวจจับฟอนต์ใน Aspose.Words – จัดการคำเตือน
tags:
- Aspose.Words
- C#
- Document Processing
title: วิธีตรวจจับแบบอักษรใน Aspose.Words – จัดการคำเตือนและการตั้งค่า
url: /th/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตรวจจับฟอนต์ใน Aspose.Words – จัดการคำเตือนและการตั้งค่า

เคยสงสัย **วิธีตรวจจับฟอนต์** ในเอกสาร Word ก่อนที่จะนำไปใช้งานจริงหรือไม่? คุณไม่ได้เป็นคนเดียวที่เจอปัญหานี้ ฟอนต์ที่หายไปอาจทำให้รูปแบบหน้าเอกสารเสียหาย และหากไม่มีการเตือนที่เหมาะสม คุณอาจส่งออก PDF หรือ DOCX ที่มีข้อบกพร่องโดยไม่รู้ตัว  

ในบทแนะนำนี้เราจะอธิบาย **วิธีตรวจจับฟอนต์** ด้วย Aspose.Words, แสดง **วิธีจัดการคำเตือน**, และปรับ **การตั้งค่าฟอนต์ของ Aspose** เพื่อให้คุณ **กำหนดค่าคำเตือน** ตามที่ต้องการ เมื่อจบคุณจะได้โค้ดสั้น ๆ ที่พร้อมรันซึ่งจะแสดงทุกการแทนที่ฟอนต์ที่ Aspose ทำ และคุณจะรู้วิธีปรับใช้กับโปรเจกต์ของคุณเอง

## ข้อกำหนดเบื้องต้น

- .NET 6+ (หรือ .NET Framework 4.6+).  
- Aspose.Words for .NET ที่ติดตั้งผ่าน NuGet (`Install-Package Aspose.Words`).  
- ไฟล์ Word ที่ตั้งค่าให้เรียกอ้างอิงฟอนต์ที่ไม่มีอยู่ (เช่น *DocumentWithMissingFonts.docx*).  

ถ้าคุณมีทั้งหมดแล้ว เยี่ยม—มาเริ่มกันเลย

![ภาพหน้าจอการตรวจจับฟอนต์](https://example.com/detect-fonts.png "ตัวอย่างผลลัพธ์การตรวจจับฟอนต์")

## วิธีตรวจจับฟอนต์ด้วย Aspose.Words

ขั้นตอนแรกคือบอก Aspose.Words ว่าคุณต้องการรับเหตุการณ์การแทนที่ฟอนต์ ซึ่งทำได้โดยการกำหนด callback คำเตือนแบบกำหนดเองผ่าน **การตั้งค่าฟอนต์ของ Aspose** Callback จะรับอ็อบเจกต์ `WarningInfo` สำหรับแต่ละการแทนที่ ทำให้คุณ **ตรวจจับฟอนต์** ขณะทำงานได้

### ขั้นตอน 1: สร้างคลาส Callback คำเตือน

ทำการ Implement อินเทอร์เฟซ `IWarningCallback` ภายในเมธอด `Warning` ให้กรอง `WarningType.FontSubstitution` แล้วบันทึกรายละเอียด

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **เคล็ดลับ:** สตริง `info.Description` จะมีทั้งชื่อฟอนต์ที่หายไปและฟอนต์ที่ Aspose แทนที่ คุณสามารถแยกข้อมูลนี้ออกมาเพื่อสร้างรายงานที่เป็นโครงสร้างได้หากต้องการ

### ขั้นตอน 2: กำหนด LoadOptions ด้วยการตั้งค่าฟอนต์ของ Aspose

สร้างอินสแตนซ์ `LoadOptions` แนบอ็อบเจกต์ `FontSettings` ใหม่ และตั้งค่า `WarningCallback` ให้ชี้ไปที่ handler ที่สร้างไว้ นี่คือการบอก Aspose **วิธีกำหนดค่าคำเตือน**  

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

หากคุณมีโฟลเดอร์ฟอนต์ส่วนตัว สามารถเพิ่มได้ดังนี้

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

บรรทัดนี้แสดงมุมมองอีกด้านของ **การตั้งค่าฟอนต์ของ Aspose**—คุณควบคุมได้ว่า Aspose จะค้นหาฟอนต์จากที่ใดก่อนที่จะทำการแทนที่

### ขั้นตอน 3: โหลดเอกสารและเรียก Callback

ตอนนี้โหลดเอกสารเป้าหมายด้วย `loadOptions` เมื่อ Aspose ทำการพาร์สไฟล์ ฟอนต์ที่หายไปใด ๆ จะทำให้เรียก handler คำเตือนโดยอัตโนมัติ ซึ่งเป็นการ **ตรวจจับฟอนต์** แบบเรียลไทม์

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

เมื่อรันโปรแกรม คุณจะเห็นผลลัพธ์คล้ายกับนี้

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### ขั้นตอน 4: (ทางเลือก) เก็บคำเตือนเพื่อใช้ในภายหลัง

หากต้องการเก็บข้อมูลการแทนที่เพื่อทำรายงาน ให้แก้ไข handler ให้สะสมข้อความไว้ในรายการ

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

ต่อมา คุณสามารถเขียน `handler.Substitutions` ไปเป็นไฟล์ JSON ส่งไปยังบริการบันทึกล็อก หรือแสดงผลใน UI ได้ตามต้องการ

### ขั้นตอน 5: ตรวจสอบผลลัพธ์ด้วยโค้ด

บางครั้งคุณอาจต้องยืนยันว่า *ไม่มี* การแทนที่เกิดขึ้น (เช่น ในการสร้าง CI) ตัวอย่างเช็กอย่างรวดเร็วมีดังนี้

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

โค้ดสั้น ๆ นี้แสดง **วิธีจัดการคำเตือน** อย่างกำหนดได้ ทำให้คุณควบคุม pipeline การสร้างได้อย่างเต็มที่

## คำถามที่พบบ่อย (และกรณีขอบ)

**ถ้าต้องการละเว้นการแทนที่บางอย่างล่ะ?**  
คุณสามารถใส่เงื่อนไขภายใน `Warning` แล้ว `return` ทันทีโดยไม่บันทึกสำหรับฟอนต์ที่ยอมรับได้

**สามารถปิดคำเตือนทั้งหมดและรับผลลัพธ์เป็นบูลีนได้หรือไม่?**  
ทำได้—ตั้งค่า `loadOptions.WarningCallback = null` แล้วตรวจสอบ `doc.FontInfo` หลังโหลด (แต่คุณจะเสียรายละเอียดของล็อก)

**ทำงานกับการแปลงเป็น PDF ได้หรือไม่?**  
ได้แน่นอน กลไกคำเตือนเดียวกันทำงานเมื่อเรียก `doc.Save("out.pdf")` Callback จะจับการสลับฟอนต์ที่เกิดขึ้นระหว่างขั้นตอนแปลง

**มีผลต่อประสิทธิภาพหรือไม่?**  
ผลกระทบค่อนข้างน้อย—เพียงเรียกเมธอดเพิ่มเล็กน้อยต่อฟอนต์ที่หายไป สำหรับชุดข้อมูลขนาดใหญ่อาจต้องแคชผลลัพธ์

## สรุปสิ่งที่ได้เรียนรู้

- **วิธีตรวจจับฟอนต์** ด้วยการ Implement `IWarningCallback` แบบกำหนดเอง  
- **วิธีจัดการคำเตือน** ผ่าน `LoadOptions.WarningCallback`  
- ปรับ **การตั้งค่าฟอนต์ของ Aspose** (เพิ่มโฟลเดอร์ฟอนต์ส่วนตัว, เปิด/ปิดคำเตือน)  
- **วิธีกำหนดค่าคำเตือน** ทั้งสำหรับแสดงผลทันทีบนคอนโซลและสำหรับวิเคราะห์ภายหลัง  

เมื่อมีเครื่องมือเหล่านี้ คุณจะสามารถประมวลผลเอกสาร Word อย่างมั่นใจ ตรวจจับฟอนต์ที่หายไปได้ทันที และรักษาความสอดคล้องของผลลัพธ์ในทุกสภาพแวดล้อม

## ขั้นตอนต่อไป

- สำรวจ `FontSettings.SubstitutionSettings` เพื่อควบคุมการแทนที่อย่างละเอียด (เช่น แมพฟอนต์ที่หายไปกับฟอนต์แทนที่ที่ต้องการ)  
- ผสานวิธีนี้กับ Aspose.PDF เพื่อสร้าง PDF ที่คงรูปแบบตัวอักษรเดิมได้อย่างแม่นยำ  
- ทำอัตโนมัติกระบวนการตรวจสอบคำเตือนใน pipeline CI/CD เพื่อบล็อกการปล่อยเวอร์ชันที่มีปัญหาฟอนต์—เหมาะสำหรับทีมที่ **จัดการคำเตือน** เป็นส่วนหนึ่งของเกตคุณภาพ  

มีคำถามเพิ่มเติมเกี่ยวกับ **การตั้งค่าฟอนต์ของ Aspose** หรืออยากขอคำแนะนำในการผสานเข้ากับบริการขนาดใหญ่? แสดงความคิดเห็นด้านล่าง แล้วขอให้เขียนโค้ดอย่างสนุกสนาน!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}