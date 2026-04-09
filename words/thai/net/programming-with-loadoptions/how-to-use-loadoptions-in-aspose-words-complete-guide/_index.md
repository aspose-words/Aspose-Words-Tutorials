---
category: general
date: 2026-01-10
description: เรียนรู้วิธีใช้ LoadOptions เพื่อจัดการกับฟอนต์ที่หายไปใน Aspose.Words
  โค้ดทีละขั้นตอน เคล็ดลับ และแนวปฏิบัติที่ดีที่สุดสำหรับการโหลดเอกสารที่มั่นคง
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: th
og_description: วิธีใช้ LoadOptions เพื่อจัดการกับฟอนต์ที่หายไปใน Aspose.Words รับตัวอย่างที่ทำงานได้เต็มรูปแบบพร้อมคำอธิบายและเคล็ดลับเชิงปฏิบัติ
og_title: วิธีใช้ LoadOptions ใน Aspose.Words – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- .NET
title: วิธีใช้ LoadOptions ใน Aspose.Words – คู่มือเต็ม
url: /th/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีใช้ LoadOptions ใน Aspose.Words – คู่มือฉบับสมบูรณ์

เคยสงสัย **วิธีใช้ LoadOptions** เมื่อต้องโหลดเอกสาร Word ที่อาจขาดฟอนต์บางตัวหรือไม่? คุณไม่ได้เป็นคนเดียวที่กังวลเรื่องนี้ ในหลายโครงการจริง ๆ เอกสารจะถูกย้ายข้ามเครื่อง และระบบเป้าหมายมักไม่มีแบบอักษรที่ผู้เขียนใช้ ผลลัพธ์คือการแทนที่ฟอนต์ที่ไม่คาดคิด ซึ่งอาจทำให้รูปแบบพัง ตัวอักษรสำคัญหายไป หรือดูไม่ตรงกับแบรนด์  

โชคดีที่ Aspose.Words มีวิธีที่สะอาดในการ *จัดการฟอนต์ที่ขาดหาย* โดยเปิดเผยอ็อบเจ็กต์ `LoadOptions` พร้อมคอลแบ็กเตือนภัย ในบทเรียนนี้คุณจะได้เรียนรู้ **วิธีใช้ LoadOptions** เพื่อดักจับคำเตือนการแทนที่ฟอนต์ บันทึกลงไฟล์ และทำให้กระบวนการของคุณแข็งแรงยิ่งขึ้น

เราจะครอบคลุม:

* การตั้งค่าคลาสคอลแบ็กเตือนภัย  
* การกำหนดค่า `LoadOptions` พร้อมคอลแบ็กนั้น  
* การโหลดเอกสารพร้อมติดตามฟอนต์ที่ขาดหาย  
* เคล็ดลับการแก้ปัญหาและขยายโซลูชัน  

ไม่ต้องอ้างอิงเอกสารภายนอก—ทุกอย่างที่คุณต้องการอยู่ที่นี่

---

## สิ่งที่คุณต้องมี

ก่อนที่เราจะลงลึก โปรดตรวจสอบว่าคุณมี:

* **Aspose.Words for .NET** (เวอร์ชันล่าสุด ณ ปี 2026) ติดตั้งผ่าน NuGet  
* สภาพแวดล้อมการพัฒนา .NET (Visual Studio, Rider หรือ VS Code)  
* ตัวอย่างไฟล์ DOCX ที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้ง (เราจะเรียกมันว่า `input.docx`)  

แค่นั้น—ไม่ต้องใช้ไลบรารีเพิ่มเติม

---

## ขั้นตอนที่ 1 – สร้างคอลแบ็กเตือนภัยเพื่อดักจับการแทนที่ฟอนต์

ชิ้นแรกของปริศนาคือคลาสที่ implements `IWarningCallback` Aspose.Words จะเรียกเมธอด `Warning` ของมันทุกครั้งที่เจอสิ่งที่ควรเตือน—เช่นฟอนต์ที่หายไป

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**ทำไมจึงสำคัญ:**  
โดยกรองด้วย `WarningType.FontSubstitution` เราจะหลีกเลี่ยงคำเตือนที่ไม่เกี่ยวข้อง (เช่นฟีเจอร์ที่เลิกใช้) คอลแบ็กให้คุณควบคุมเต็มที่—คุณอาจบันทึกลงไฟล์, โยนข้อยกเว้น, หรือแม้แต่พยายามฝังฟอนต์สำรองโดยอัตโนมัติ

---

## ขั้นตอนที่ 2 – กำหนดค่า LoadOptions ด้วยคอลแบ็ก

เมื่อเรามีตัวจัดการแล้ว เราต้องบอก Aspose.Words ให้ใช้มัน นี่คือที่ที่ **วิธีใช้ LoadOptions** ปรากฏขึ้นในทางปฏิบัติ

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**เคล็ดลับ:** `LoadOptions` มีสวิตช์อื่น ๆ อีกมาก (เช่น `Password`, `LoadFormat`, `Encoding`) คุณสามารถเชื่อมต่อกันได้ แต่สำหรับการจัดการฟอนต์ที่หายไป `WarningCallback` คือดาวเด่นของเรื่อง

---

## ขั้นตอนที่ 3 – โหลดเอกสารด้วยตัวเลือกที่กำหนดไว้

เมื่อ `LoadOptions` พร้อม การโหลดเอกสารก็ง่ายดาย Aspose.Words จะเรียกคอลแบ็กโดยอัตโนมัติสำหรับฟอนต์ใดที่ไม่พบ

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**ผลลัพธ์ที่คาดหวัง:**  

ถ้า `input.docx` ใช้ฟอนต์ชื่อ *“GothicBold”* ที่ไม่ได้ติดตั้ง คุณจะเห็นข้อความประมาณนี้:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

บรรทัดเตือนจะแสดง **พอดีที่ฟอนต์ที่หายไปถูกพบ** ให้คุณได้รับฟีดแบ็กทันที

---

## ขั้นตอนที่ 4 – (ทางเลือก) ดำเนินการต่อกับเอกสาร

โดยปกติคุณมักจะทำมากกว่าการโหลดไฟล์เท่านั้น ด้านล่างเป็นการกระทำหลังโหลดที่พบบ่อยและทำงานร่วมกับคอลแบ็กของเราได้อย่างราบรื่น

### 4.1 บันทึกเอกสารเป็น PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรองที่รู้จัก

หากคุณต้องการสำรองเฉพาะ (เช่น *“Calibri”*) คุณสามารถปรับ `FontSettings` ก่อนบันทึกได้:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 บันทึกคำเตือนทั้งหมดลงไฟล์

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

โค้ดเหล่านี้แสดง **วิธีใช้ LoadOptions** นอกเหนือจากกรณีพื้นฐาน ให้คุณมีความยืดหยุ่นสำหรับโซลูชันระดับผลิตภัณฑ์

---

## ข้อผิดพลาดทั่วไป & วิธี **จัดการฟอนต์ที่หายไป** อย่างมืออาชีพ

| ข้อผิดพลาด | สาเหตุ | วิธีแก้ / ลดผล |
|------------|--------|----------------|
| **ไม่ได้แนบคอลแบ็ก** | ลืมตั้งค่า `WarningCallback` | สร้างอินสแตนซ์ `LoadOptions` แล้วกำหนดตัวจัดการของคุณก่อนโหลด |
| **คอลแบ็กพิมพ์เท่านั้น ไม่เก็บ** | ในเว็บเซอร์วิส คอนโซลอาจหายไป | แทนที่ `Console.WriteLine` ด้วย logger (Serilog, NLog) หรือเขียนลงที่จัดเก็บถาวร |
| **หลายฟอนต์หาย แต่รายงานแค่แรก** | คอลแบ็กโยนข้อยกเว้นที่คำเตือนแรก | ทำคอลแบ็กให้เบา ๆ; อย่าโยนข้อยกเว้นเว้นแต่คุณต้องการยกเลิกจริง |
| **ฟอนต์สำรองดูแปลก** | การแทนที่เริ่มต้นอาจเลือกฟอนต์ที่ไม่เหมือนกัน | ใช้ `FontSettings.SubstitutionSettings.FontSubstitutionRules` เพื่อกำหนดลำดับสำรองที่คุณต้องการ |
| **ประสิทธิภาพลดลงกับไฟล์ขนาดใหญ่** | คอลแบ็กถูกเรียกหลายพันครั้ง | เก็บคำเตือนในรายการแล้วประมวลผลหลังโหลด, หรือกรองเฉพาะชื่อฟอนต์ที่ไม่ซ้ำกัน |

การรับรู้สถานการณ์เหล่านี้จะช่วยให้คุณ **จัดการฟอนต์ที่หายไป** ได้โดยไม่มีเซอร์ไพรส์

---

## ตัวอย่างทำงานเต็มรูปแบบ – รวมทุกส่วนเข้าด้วยกัน

ด้านล่างเป็นโปรแกรมพร้อมรันที่แสดงกระบวนการทั้งหมด คัดลอก‑วางลงในโปรเจกต์คอนโซล, เพิ่มแพคเกจ NuGet ของ Aspose.Words, แล้วมันจะทำงานทันที

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**การรันโปรแกรมนี้** จะ:

1. พิมพ์คำเตือนการแทนที่ฟอนต์ใด ๆ ลงคอนโซล  
2. บันทึกเลย์เอาต์เดิมเป็น `output.pdf`  
3. บันทึก PDF ที่สอง (`output-with-fallback.pdf`) ที่บังคับให้ใช้สำรองเป็น *Calibri* หรือ *Arial*

---

## คำถามที่พบบ่อย (FAQs)

**ถาม: วิธีนี้ทำงานกับไฟล์ DOC, RTF หรือ HTML ได้หรือไม่?**  
ตอบ: ได้ `LoadOptions` ไม่ขึ้นกับรูปแบบ; เพียงส่งพาธไฟล์ที่ถูกต้อง คอลแบ็กจะทำงานกับฟอนต์ที่หายไปในทุกฟอร์แมตที่สนับสนุน

**ถาม: สามารถปิดการแสดงคำเตือนทั้งหมดได้หรือไม่?**  
ตอบ: คุณสามารถกำหนดคอลแบ็กที่ทำอะไรไม่ทำ (`new IWarningCallback { Warning = _ => {} }`) หรือตั้ง `LoadOptions.WarningCallback = null` อย่างไรก็ตาม การสูญเสียการมองเห็นอาจทำให้พลาดปัญหาฟอนต์สำคัญ

**ถาม: ถ้าต้องการแทนที่ฟอนต์ที่หายไปด้วยฟอนต์ฝังไว้ทำอย่างไร?**  
ตอบ: ใช้ `FontSettings` เพื่อฝังไฟล์ฟอนต์สำรอง (`AddFontSource`) แล้วผสานกับกฎการแทนที่เพื่อประสบการณ์ที่ไร้รอยต่อ

**ถาม: คอลแบ็กปลอดภัยต่อหลายเธรดหรือไม่?**  
ตอบ: คอลแบ็กอาจถูกเรียกจากหลายเธรดเมื่อโหลดไฟล์ขนาดใหญ่แบบขนาน ควรทำให้ทรัพยากรที่ใช้ร่วมกัน (เช่นไฟล์ล็อก) มีการซิงโครไนซ์

---

## สรุป

เราได้อธิบาย **วิธีใช้ LoadOptions** ใน Aspose.Words เพื่อ **จัดการฟอนต์ที่หายไป** อย่างมีประสิทธิภาพ โดยการสร้าง `IWarningCallback` แบบกำหนดเอง, ผูกเข้ากับ `LoadOptions`, แล้วโหลดเอกสารด้วยการตั้งค่านั้น คุณจะได้รับข้อมูลแบบเรียลไทม์เกี่ยวกับเหตุการณ์การแทนที่ฟอนต์ จากนั้นคุณสามารถบันทึก, แทนที่, หรือฝังฟอนต์สำรองเพื่อให้ผลลัพธ์ออกมาตรงตามที่ต้องการ

ขั้นตอนสำคัญคือ:

1. Implement คอลแบ็กเตือนที่โฟกัสที่ `WarningType.FontSubstitution`  
2. เชื่อมคอลแบ็กเข้ากับอ็อบเจ็กต์ `LoadOptions`  
3. โหลดเอกสารด้วยตัวเลือกเหล่านั้น  
4. (ทางเลือก) ปรับกฎการแทนที่ฟอนต์หรือการบันทึกตามต้องการ  

ลองปรับเปลี่ยนตามสไตล์ของคุณ—สลับคอนโซลโลเกอร์เป็นโครงสร้างล็อกที่เป็นระบบ, เพิ่มการแจ้งเตือนอีเมลสำหรับฟอนต์สำคัญที่หาย, หรือผสานแนวคิดนี้เข้าไปในไพพ์ไลน์การประมวลผลเอกสารขนาดใหญ่ โซลูชันนี้ขยายได้ดีไม่ว่าจะเป็นไฟล์เดียวหรือหลายพันไฟล์ในงานแบตช์

ขอให้เขียนโค้ดสนุกและเอกสารของคุณแสดงผลด้วยฟอนต์ที่ถูกต้องเสมอ!  

---

![วิธีใช้ loadoptions ตัวอย่าง]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}