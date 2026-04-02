---
category: general
date: 2026-04-02
description: วิธีตรวจจับฟอนต์ในเอกสาร C# ด้วย Aspose.Words เรียนรู้การกำหนดค่าฟอนต์และจัดการฟอนต์ที่หายไปอย่างมีประสิทธิภาพ
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: th
og_description: วิธีตรวจจับฟอนต์ในเอกสาร C# ด้วย Aspose.Words คู่มือนี้จะแสดงวิธีตั้งค่าฟอนต์และจัดการกับฟอนต์ที่หายไป
og_title: วิธีตรวจจับฟอนต์ใน C# – คู่มือฉบับสมบูรณ์
tags:
- C#
- Aspose.Words
- Document Processing
title: วิธีตรวจจับฟอนต์ใน C# – คู่มือฉบับเต็ม
url: /th/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตรวจจับฟอนต์ใน C# – คู่มือฉบับสมบูรณ์

เคยสงสัย **วิธีตรวจจับฟอนต์** ที่หายไปหรือถูกแทนที่เมื่อคุณโหลดเอกสาร Word ใน .NET หรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนามักเจอปัญหาเมื่อเอกสารอ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์ ข่าวดีคือ Aspose.Words มีวิธีที่สะอาดและเป็นโปรแกรมเมติกเพื่อค้นหาช่องว่างเหล่านั้น

ในบทเรียนนี้เราจะเดินผ่านตัวอย่างเชิงปฏิบัติที่ไม่เพียงแสดง **วิธีตรวจจับฟอนต์** เท่านั้น แต่ยังสาธิต **การตั้งค่า font settings** และ **การจัดการฟอนต์ที่หายไป** อย่างราบรื่น เมื่อเสร็จคุณจะได้สคริปต์พร้อมรันที่พิมพ์คำเตือนการแทนที่ฟอนต์ทุกรายการ เพื่อให้คุณสามารถบันทึก, แจ้งเตือน หรือแทนที่ฟอนต์ตามต้องการ

---

## สิ่งที่คุณต้องเตรียม

- **Aspose.Words for .NET** (เวอร์ชันล่าสุดทำงานดีที่สุด; โค้ดด้านล่างตั้งเป้าหมายที่ .NET 6+)
- สภาพแวดล้อมการพัฒนา .NET (Visual Studio, Rider, หรือ VS Code)
- ตัวอย่างไฟล์ `.docx` ที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้ง (เหมาะสำหรับการทดสอบ)

ไม่ต้องใช้แพ็กเกจ NuGet เพิ่มเติมนอกจาก Aspose.Words และโซลูชันทำงานได้บน Windows, Linux, และ macOS

---

## ขั้นตอนที่ 1: ติดตั้งและอ้างอิง Aspose.Words

แรกเริ่มให้เพิ่มไลบรารีลงในโปรเจกต์ของคุณ คำสั่ง NuGet ง่าย ๆ ดังนี้

```bash
dotnet add package Aspose.Words
```

> **เคล็ดลับ:** หากคุณทำงานบนเซิร์ฟเวอร์ CI ให้ระบุเวอร์ชันของแพ็กเกจเพื่อหลีกเลี่ยงการเปลี่ยนแปลงที่ไม่คาดคิด

---

## ขั้นตอนที่ 2: ตั้งค่า Font Settings (และเตรียม Load Options)

ก่อนที่คุณจะเปิดเอกสาร คุณสามารถบอก Aspose.Words ให้มองหาฟอนต์สำรองได้ นี่คือส่วน **configure font settings** ที่ช่วยป้องกันเอนจินจากการสลับฟอนต์โดยอัตโนมัติที่คุณอาจไม่ต้องการ

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

ทำไมต้องทำ? หากเอกสารอ้างอิง *Comic Sans* แต่เซิร์ฟเวอร์ของคุณมีแค่ *Calibri* เท่านั้น Aspose.Words จะสลับเป็น *Calibri* และแจ้งคำเตือน การกำหนดเส้นทางค้นหาจะช่วยลดความประหลาดใจที่ไม่ต้องการ

---

## ขั้นตอนที่ 3: โหลดเอกสารด้วย Options ที่เตรียมไว้

ต่อไปเราจะเปิดไฟล์จริง `LoadOptions` ที่สร้างในขั้นตอนก่อนหน้าจะถูกส่งตรงไปยังคอนสตรัคเตอร์ของ `Document`

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

หากไฟล์ไม่พบหรือเสียหาย จะเกิดข้อยกเว้น—ดังนั้นคุณอาจต้องห่อโค้ดนี้ด้วย try/catch ในโค้ดผลิตจริง

---

## ขั้นตอนที่ 4: สแกนคำเตือนของเอกสารเพื่อหาการแทนที่ฟอนต์

Aspose.Words จะเก็บรายการคำเตือนขณะทำการพาร์ส ในบรรดาคำเตือนเหล่านั้น `FontSubstitutionWarning` จะบอกคุณว่า ฟอนต์ใดถูกสลับ

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

คอลเลกชัน `Warnings` อาจมีรายการอื่น ๆ ด้วย (เช่น `DocumentStructureWarning`) การกรองเฉพาะ `FontSubstitutionWarning` จะทำให้เรารายงานเฉพาะสถานการณ์ **handle missing fonts** ที่ต้องการเท่านั้น

---

## ขั้นตอนที่ 5: รวมทั้งหมด – ตัวอย่างเต็มที่รันได้

ด้านล่างเป็นโปรแกรมเต็มคัดลอก‑วางลงในแอปคอนโซลใหม่แล้วรัน; คุณจะเห็นฟอนต์ที่หายไปแต่ละรายการแสดงบนคอนโซล

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (ตัวอย่าง):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

หากเอกสารใช้ฟอนต์ที่มีอยู่บนเครื่องทั้งหมด คุณจะเห็นบรรทัด “No font substitutions detected” แทน

---

## กรณีขอบและคำถามที่พบบ่อย

### ถ้าเอกสารไม่มี **คำเตือน** ใดเลยล่ะ?

หมายความว่าฟอนต์ทั้งหมดที่อ้างอิงถูกพบในโฟลเดอร์ค้นหาที่คุณตั้งค่า `anySubstitutions` ในตัวอย่างจะครอบคลุมกรณีนี้

### ฉันสามารถ **บันทึก** คำเตือนลงไฟล์แทนคอนโซลได้หรือไม่?

ได้เลย แทนที่การเรียก `Console.WriteLine` ด้วยโล거ที่คุณเลือก (Serilog, NLog ฯลฯ) วัตถุ `WarningInfo` ยังให้ `WarningType` และ `WarningMessage` หากต้องการรายละเอียดเพิ่มเติม

### จะ **ละเว้น**ฟอนต์บางตัวอย่างฟอนต์แบรนด์ของบริษัทที่ไม่ควรสลับได้อย่างไร?

คุณสามารถเพิ่มกฎการแทนที่แบบกำหนดเอง:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

ตอนนี้ Aspose.Words จะสลับ *MyBrandFont* ด้วยทางเลือกที่ระบุเท่านั้น และคุณยังคงได้รับคำเตือนเพื่อดำเนินการต่อ

### ทำงานบนคอนเทนเนอร์ **Linux** ได้หรือไม่?

ทำได้—แค่ตรวจสอบให้แน่ใจว่าคุณเมานท์โฟลเดอร์ที่มีไฟล์ `.ttf`/`.otf` ที่ต้องการและชี้ `SetFontsFolder` ไปที่นั้น Aspose.Words ไม่พึ่งพาฟอนต์ที่ติดตั้งใน OS

---

## ภาพรวมเชิงภาพ

![how to detect fonts flowchart](detect-fonts.png "Diagram showing the steps to detect fonts in a document")

*ข้อความแทนภาพ:* **how to detect fonts** flowchart แสดงการกำหนดค่า, การโหลด, และการตรวจสอบคำเตือน

---

## สรุป – สิ่งที่เราได้เรียนรู้

- **วิธีตรวจจับฟอนต์** ที่หายไปหรือถูกแทนที่โดยใช้คำเตือนของ Aspose.Words  
- วิธี **ตั้งค่า font settings** เพื่อชี้ไปยังโฟลเดอร์ฟอนต์แบบกำหนดเองและกำหนด fallback เริ่มต้น  
- กลยุทธ์ **การจัดการฟอนต์ที่หายไป** ตั้งแต่การบันทึกจนถึงกฎการแทนที่แบบกำหนดเอง

ทั้งหมดนี้อยู่ในแอปคอนโซลขนาดกะทัดรัดที่คุณสามารถนำไปใส่ในโซลูชัน .NET ใดก็ได้

---

## ขั้นตอนต่อไปและหัวข้อที่เกี่ยวข้อง

- **การฝังฟอนต์** ลงในเอกสารผลลัพธ์เพื่อหลีกเลี่ยงการแทนที่ในอนาคต (`SaveOptions` กับ `EmbedFullFonts`)  
- **การแทนที่ฟอนต์โดยโปรแกรม** – แทนที่ฟอนต์ที่หายไปด้วยทางเลือกเฉพาะก่อนบันทึก  
- **การปรับประสิทธิภาพ** – แคช `FontSettings` เมื่อต้องประมวลผลเอกสารหลายไฟล์เป็นชุด  

หากคุณสนใจหัวข้อเหล่านี้ ให้ค้นหา *configure font settings* และ *handle missing fonts* จะพาคุณไปสู่การเจาะลึกการจัดการฟอนต์ด้วย Aspose.Words

---

Happy coding! มีกรณีฟอนต์แปลก ๆ ไหม? ฝากคอมเมนต์มา เราจะช่วยกันแก้ไข

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}