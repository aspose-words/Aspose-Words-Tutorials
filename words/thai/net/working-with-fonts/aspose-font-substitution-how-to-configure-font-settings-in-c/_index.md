---
category: general
date: 2026-03-27
description: 'Aspose Font Substitution ง่ายดาย: เรียนรู้การตั้งค่าฟอนต์, จับคำเตือน,
  และจัดการฟอนต์ที่หายไปในแอป .NET ของคุณ.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: th
og_description: เชี่ยวชาญการแทนที่ฟอนต์ของ Aspose ด้วยการกำหนดค่าฟอนต์และจัดการฟอนต์ที่หายไปด้วยการแจ้งเตือนแบบคอลแบ็ก
  คู่มือ C# ฉบับสมบูรณ์.
og_title: การแทนที่ฟอนต์ของ Aspose – กำหนดค่าการตั้งค่าฟอนต์ใน C#
tags:
- Aspose.Words
- C#
- Font Management
title: การแทนที่ฟอนต์ของ Aspose – วิธีตั้งค่าฟอนต์ใน C#
url: /th/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – คู่มือเต็มสำหรับการกำหนดค่า Font Settings

เคยเจอเอกสารที่ทันใดนั้นสลับฟอนต์ที่คุณกำหนดเองเป็นฟอนต์ทั่วไปหรือไม่? นั่นคือ **aspose font substitution** ทำหน้าที่ของมัน—แทนที่ฟอนต์ที่หายไปด้วยฟอนต์ที่ใกล้เคียงที่สุดที่มันหาได้ มันสะดวก แต่ถ้าคุณต้องการรู้ *อย่างแม่นยำ* ว่าฟอนต์ใดถูกสลับ คุณต้องเข้าถึงระบบคำเตือนของไลบรารีและกำหนดค่า font settings ด้วยตนเอง

ในบทแนะนำนี้เราจะเดินผ่านสถานการณ์จริง: โหลดไฟล์ DOCX ที่อ้างอิงฟอนต์ที่คุณไม่มี, จับเหตุการณ์การสลับฟอนต์, และพิมพ์ข้อความที่เป็นมิตรไปยังคอนโซล. เมื่อจบคุณจะคุ้นเคยกับ **configure font settings**, การเชื่อมต่อ **Aspose.Words warning callback**, และการขยายตัวอย่างให้เข้ากับกระบวนการทำงานใด ๆ

> **สิ่งที่คุณต้องมี**  
> • .NET 6+ (หรือ .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (เวอร์ชันล่าสุดจาก NuGet)  
> • DOCX ที่อ้างอิงฟอนต์ที่หายไป (เราจะเรียกมันว่า `MissingFont.docx`)  

มาเริ่มกันเลย

---

## Step 1: Install Aspose.Words and Prepare the Project

ก่อนที่เราจะเขียนโค้ดใด ๆ ตรวจสอบให้แน่ใจว่าได้อ้างอิงแพคเกจ Aspose.Words แล้ว:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** ใช้เวอร์ชันเสถียรล่าสุด; ณ เดือนมีนาคม 2026 คือ 23.11.0. เวอร์ชันใหม่ ๆ ปรับปรุงอัลกอริทึมการจับคู่ฟอนต์และเพิ่มประเภทคำเตือนเพิ่มเติม

สร้างแอปคอนโซลใหม่ (หรือวางโค้ดลงในโปรเจกต์ที่มีอยู่) แล้วเพิ่ม `using` directives ตามปกติ:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

เนมสเปซเหล่านี้ให้เราเข้าถึง `Document`, `LoadOptions`, และคลาสที่เกี่ยวกับฟอนต์ที่เราต้องการใช้

---

## Step 2: Configure Font Settings with LoadOptions

หัวใจของการควบคุม **aspose font substitution** อยู่ที่ `LoadOptions.FontSettings`. การส่งออบเจกต์ `FontSettings` ว่าง ๆ ให้ Aspose ใช้เส้นทางค้นหาเริ่มต้น *และ* รายงานการสลับใด ๆ ผ่าน callback คำเตือน

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

ทำไมไม่ใช้ค่าเริ่มต้นเลย? เพราะการแนบ callback คำเตือน (ขั้นตอนต่อไป) จะทำงานได้เฉพาะเมื่อคุณสมบัติ `FontSettings` ไม่เป็น null. บรรทัดเล็ก ๆ นี้ให้จุดเชื่อมต่อเข้าสู่กระบวนการสลับโดยไม่เปลี่ยนแปลงพฤติกรรมการค้นหาฟอนต์จริง ๆ

---

## Step 3: Attach a Warning Callback to Capture Substitutions

Aspose.Words ใช้ interface `IWarningCallback`. ทุกครั้งที่มีเหตุการณ์สำคัญ—เช่นฟอนต์หาย—มันจะเรียกเมธอด `Warning` ของเรา. เราจะสร้าง handler เล็ก ๆ ที่กรอง `WarningType.FontSubstitution` แล้วพิมพ์คำอธิบาย

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

และนี่คือ handler เอง:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **ทำไมเรื่องนี้ถึงสำคัญ** – หากไม่มี callback, Aspose จะสลับฟอนต์โดยเงียบ ๆ ทำให้คุณไม่รู้ว่าฟอนต์ใดถูกใช้. Callback ทำให้กระบวนการโปร่งใส ซึ่งจำเป็นสำหรับการรายงานการปฏิบัติตามหรือการดีบักปัญหาเลย์เอาต์

---

## Step 4: Load the Document Using the Configured Options

ตอนนี้เราจะโหลดเอกสารโดยส่ง `loadOptions` ที่เตรียมไว้. หากไฟล์ต้นทางอ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง, handler ของเราจะทำงาน

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

แทนที่ `YOUR_DIRECTORY` ด้วยพาธจริงที่เก็บ `MissingFont.docx`. เมื่อรันโปรแกรม คุณควรเห็นผลลัพธ์คล้ายกับ:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

บรรทัดนั้นบอกคุณอย่างชัดเจนว่าฟอนต์ใดหายไปและฟอนต์สำรองที่ Aspose เลือกใช้คืออะไร

---

## Step 5: (Optional) Fine‑Tune Font Search Paths

หากคุณมีโฟลเดอร์ส่วนตัวที่เก็บฟอนต์ขององค์กร, คุณสามารถบอก Aspose ให้ค้นหาที่นั่นก่อนที่จะย้อนกลับไปใช้ฟอนต์ระบบ. นี่คือการใช้ **configure font settings** ขั้นสูง:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

การตั้งค่า `recursive: true` ทำให้ Aspose สแกนโฟลเดอร์ย่อยด้วย. ตอนนี้ไลบรารีจะลองใช้ฟอนต์ส่วนตัวของคุณก่อน ลดโอกาสการสลับฟอนต์ที่ไม่ต้องการ

---

## Full Working Example

รวมทุกอย่างเข้าด้วยกัน นี่คือตัวอย่างโปรแกรมที่พร้อมรัน:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (เมื่อพบฟอนต์ที่หายไป):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

หากฟอนต์ทั้งหมดมีอยู่ โปรแกรมจะทำงานแบบเงียบ (ไม่มีคำเตือน) และยังคงสร้าง PDF ได้ตามปกติ

---

## Common Questions & Edge Cases

### What if I need to *prevent* substitution altogether?

ตั้งค่า `FontSettings.SubstitutionSettings` เป็น `null` หรือใช้ `FontSettings.FontSubstitutionSettings` เพื่อควบคุมพฤติกรรม. ตัวอย่าง:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

ตอนนี้ Aspose จะโยนข้อยกเว้นแทนการสลับโดยเงียบ ๆ ซึ่งคุณสามารถจับและจัดการได้

### Does this work with other file formats (e.g., .doc, .rtf)?

แน่นอน. ออบเจกต์ `LoadOptions` เดียวกันสามารถส่งให้คอนสตรัคเตอร์ `Document` ใด ๆ ที่รับพาธไฟล์ได้. Callback คำเตือนจะทำงานสำหรับทุกฟอร์แมตที่พึ่งพาฟอนต์

### Can I capture the *exact* fallback font name?

ได้. สตริง `info.Description` มีทั้งฟอนต์ที่หายและฟอนต์สำรอง. หากต้องการชื่อแบบโปรแกรมเมติก, คุณสามารถพาร์สสตริงนั้นหรือใช้ `FontInfo` (พร้อมในเวอร์ชันใหม่)

### How does this behave in a multi‑threaded environment?

`FontSettings` **ไม่**เป็น thread‑safe. สร้าง `LoadOptions` (พร้อม `FontSettings` ของมัน) แยกสำหรับแต่ละเธรด, หรือปกป้องการเข้าถึงด้วย lock

---

## Conclusion

เราได้ครอบคลุมทุกอย่างที่คุณต้องการเพื่อเชี่ยวชาญ **aspose font substitution** และ **configure font settings** ในแอป C#:

1. ติดตั้ง Aspose.Words และเพิ่ม `using` ที่จำเป็น  
2. สร้างออบเจกต์ `LoadOptions` พร้อม `FontSettings` ใหม่  
3. แนบ `IWarningCallback` ที่กำหนดเองเพื่อแสดงเหตุการณ์สลับฟอนต์  
4. โหลดเอกสารและให้ callback รายงานฟอนต์ที่หายไป  
5. (เลือก) ขยายเส้นทางค้นหาหรือปิดการสลับฟอนต์ทั้งหมด

ด้วยรูปแบบนี้คุณสามารถบันทึกฟอนต์ที่หายไปเพื่อการปฏิบัติตาม, แจ้งผู้ใช้ใน UI, หรือฝังฟอนต์สำรองโดยอัตโนมัติก่อนเผยแพร่. ขั้นต่อไปอาจเป็นการสำรวจ **Aspose.Words font substitution policies** หรือผสานกระบวนการนี้เข้าสู่ pipeline การประมวลผลเอกสารขนาดใหญ่

Happy coding, and may your documents always render with the right typeface!  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}