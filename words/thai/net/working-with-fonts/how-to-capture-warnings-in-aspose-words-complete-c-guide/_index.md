---
category: general
date: 2026-03-28
description: วิธีดักจับคำเตือนเมื่อโหลดไฟล์ DOCX ด้วย Aspose.Words และรับข้อความคำเตือนสำหรับฟอนต์ที่หายไป
  เรียนรู้การจัดการฟอนต์ที่หายไปอย่างมีประสิทธิภาพ
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: th
og_description: วิธีดักจับคำเตือนเมื่อโหลดไฟล์ DOCX ด้วย Aspose.Words, รับข้อความคำเตือน,
  และจัดการฟอนต์ที่หายไปด้วยตัวอย่างโค้ดที่ใช้งานได้จริง.
og_title: วิธีดักจับคำเตือนใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Processing
title: วิธีดักจับคำเตือนใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
url: /th/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีจับคำเตือนใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์

เคยสงสัย **วิธีจับคำเตือน** ที่ปรากฏขึ้นเมื่อคุณโหลดเอกสาร Word ด้วย Aspose.Words หรือไม่? บางทีคุณอาจเห็นการเปลี่ยนแปลงฟอนต์ที่แปลก ๆ และต้องการรู้เหตุผลที่แน่ชัด สั้น ๆ คือคุณสามารถเชื่อมต่อกับระบบคำเตือนของไลบรารี, **รับข้อความคำเตือน**, และแม้กระทั่ง **จัดการฟอนต์ที่หายไป** ก่อนที่มันจะทำลายเลย์เอาต์ของคุณ  

ในบทแนะนำนี้เราจะเดินผ่านสถานการณ์จริง: โหลดไฟล์ DOCX, รวบรวมคำเตือนทุกข้อความที่เอนจินส่งออก, และพิมพ์รายละเอียดเกี่ยวกับการแทนที่ฟอนต์ที่เกิดขึ้น เมื่อจบคุณจะได้ตัวอย่างโค้ดที่พร้อมรัน, เข้าใจ “ทำไม” ของแต่ละขั้นตอน, และรู้วิธีขยายวิธีการนี้สำหรับโปรเจกต์ของคุณเอง

## สิ่งที่คุณจะได้เรียนรู้

- วิธีกำหนดค่า `LoadOptions` เพื่อให้จับคำเตือนโดยอัตโนมัติ  
- วิธีที่แม่นยำในการ **รับข้อความคำเตือน** จาก `WarningInfoCollection`  
- วิธีระบุและตอบสนองต่อ **ฟอนต์ที่หายไป** ผ่านแฟล็ก `WarningType.FontSubstitution`  
- เคล็ดลับการแก้ปัญหาในกรณีขอบ เช่น เอกสารที่ฝังฟอนต์หรือโฟลเดอร์ฟอนต์แบบกำหนดเอง  

ไม่มีการอ้างอิงภายนอกที่จำเป็น – ทุกอย่างที่คุณต้องการอยู่ที่นี่

---

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานบน .NET Framework 4.7+ ด้วย)  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
- ตัวอย่างไฟล์ DOCX (`input.docx`) ที่อาจขาดฟอนต์บางตัวหรือใช้ฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของคุณ  

แค่นั้นเอง หากคุณคุ้นเคยกับ C# และ Visual Studio อยู่แล้ว คุณสามารถคัดลอก‑วางโค้ดและรันได้ทันที

---

## ขั้นตอนที่ 1: เตรียม Load Options และ Warning Callback

สิ่งแรกที่ Aspose.Words ทำเมื่อคุณเรียก `new Document(path, loadOptions)` คือการพาร์สไฟล์ ระหว่างการพาร์สอาจเจอฟอนต์ที่หายไป, ฟีเจอร์ที่ไม่รองรับ, หรือมาร์กอัปที่ล้าสมัย เพื่อดักจับเหตุการณ์เหล่านั้นคุณต้องมีอ็อบเจ็กต์ **warning callback**  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**ทำไมเรื่องนี้ถึงสำคัญ:** หากไม่มี callback, Aspose.Words จะบันทึกคำเตือนไปที่คอนโซลโดยเงียบ (หรือทิ้งไว้) ทำให้คุณไม่เห็นการแทนที่ฟอนต์ที่อาจส่งผลต่อเลย์เอาต์ โดยการให้ `WarningInfoCollection` เฉพาะคุณจะได้มองเห็นทั้งหมดอย่างเต็มที่

> **Pro tip:** หากคุณสนใจเฉพาะคำเตือนที่เกี่ยวกับฟอนต์, คุณสามารถกรองภายหลัง – แต่การเก็บ **ทุก** คำเตือนจะให้คุณมีเครือข่ายความปลอดภัยสำหรับปัญหาในอนาคต

---

## ขั้นตอนที่ 2: โหลดเอกสารด้วยตัวเลือกที่กำหนดไว้

เมื่อ callback พร้อมแล้ว, โหลดไฟล์ ตัวสร้าง `Document` จะเรียก callback อัตโนมัติสำหรับปัญหาใด ๆ ที่พบ  

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**เกิดอะไรขึ้นเบื้องหลัง?** Aspose.Words พาร์ส Open XML, แก้ไขสไตล์, และพยายามแมปแต่ละการอ้างอิงฟอนต์ไปยังฟอนต์ที่ติดตั้งในระบบ หากไม่พบการจับคู่, มันจะสร้างรายการ `WarningInfo` ชนิด `FontSubstitution`

---

## ขั้นตอนที่ 3: ดึงและตรวจสอบคำเตือนที่เก็บรวบรวมไว้

หลังจากการโหลดเสร็จ, `warningCollector` ของคุณจะมีคำเตือนทุกข้อความที่เกิดขึ้น ให้เรานำออกมาและโฟกัสที่ข้อความการแทนที่ฟอนต์  

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**ตัวอย่างผลลัพธ์** (คอนโซลของคุณอาจแสดงประมาณนี้):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

หากต้องการ *ทุก* คำเตือน, เพียงลบเงื่อนไข `if` หรือบันทึก `warning.Type` สำหรับแต่ละรายการ

---

## ขั้นตอนที่ 4: การจัดการฟอนต์ที่หายไป – มากกว่าการบันทึกลงล็อก

การจับคำเตือนเป็นประโยชน์, แต่บ่อยครั้งคุณต้อง **จัดการฟอนต์ที่หายไป** ด้วยโปรแกรม นี่คือสองกลยุทธ์ที่พบบ่อย:

### 4.1 แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรองที่กำหนด

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

ตอนนี้ฟอนต์ที่หายไปใด ๆ จะถูกสลับเป็น *Calibri* แทนฟอนต์สำรองเริ่มต้นของไลบรารี

### 4.2 ฝังฟอนต์สำรองแบบไดนามิก

หากคุณมีไฟล์ฟอนต์แบบกำหนดเอง (เช่น `MyFallback.ttf`) คุณสามารถลงทะเบียนได้ในขณะรัน:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

วิธีนี้เหมาะเมื่อคุณต้องแจกจ่ายฟอนต์ของบริษัทพร้อมกับแอปพลิเคชันของคุณ

> **Edge case:** เอกสารที่ฝังฟอนต์ที่ต้องการแล้วจะละเว้นกฎการแทนที่ของระบบ ในกรณีนั้น, คอลเลกชันคำเตือนจะว่างเปล่าสำหรับฟอนต์นั้น ซึ่งเป็นสิ่งที่คุณต้องการ

---

## ขั้นตอนที่ 5: ตัวอย่างทำงานเต็มรูปแบบ (พร้อมคัดลอก‑วาง)

ด้านล่างเป็นโปรแกรมอิสระที่สาธิตทุกอย่างตั้งแต่ต้นจนจบ เพียงเปลี่ยน `YOUR_DIRECTORY/input.docx` ให้เป็นพาธของไฟล์ทดสอบของคุณ  

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**สิ่งที่คาดว่าจะเกิดขึ้น**

- คอนโซลพิมพ์คำเตือนการแทนที่ฟอนต์ทุกข้อความ, โดยมีอีโมจีเตือนหน้าข้อความเพื่อความชัดเจน  
- ไฟล์ DOCX ผลลัพธ์ (`output.docx`) จะใช้ *Calibri* ทุกครั้งที่พบฟอนต์ที่หายไป  
- ไม่มีข้อยกเว้นที่ไม่ได้จัดการ – ระบบคำเตือนจัดการกับฟอนต์ที่ไม่รู้จักอย่างราบรื่น

---

## คำถามที่พบบ่อย

**ถาม: วิธีนี้จะทำงานกับ PDF ที่สร้างจาก Word หรือไม่?**  
ตอบ: ใช่ Aspose.Words ถือ PDF เป็นรูปแบบผลลัพธ์อื่น คำเตือนจะถูกจับในขั้นตอน *โหลด* ดังนั้นจึงไม่ขึ้นกับการส่งออกขั้นสุดท้าย

**ถาม: ถ้าต้องการจับคำเตือนสำหรับ **ทุก** การดำเนินการกับเอกสาร (บันทึก, แปลง, ฯลฯ) จะทำอย่างไร?**  
ตอบ: คุณสามารถใช้ `WarningInfoCollection` เดียวกันโดยกำหนดให้กับ `Document.WarningCallback` หลังจากสร้างเอกสาร ทุกการดำเนินการต่อไปจะเพิ่มรายการใหม่ลงในคอลเลกชันเดียวกัน

**ถาม: Callback นี้ส่งผลต่อประสิทธิภาพหรือไม่?**  
ตอบ: แทบไม่มี ผลของคอลเลกชันคือการเก็บอ็อบเจ็กต์; เว้นแต่คุณจะประมวลผลคำเตือนหลายพันรายการในลูปแคบ คุณก็จะไม่สังเกตความช้าฝั่งใด

**ถาม: จะทำอย่างไรให้คำเตือนที่ไม่สนใจไม่แสดง?**  
ตอบ: สร้างคลาสที่สืบทอดจาก `IWarningCallback` และกรองภายในเมธอด `Warning` เอง `WarningInfoCollection` ที่มาพร้อมจะเก็บเท่านั้น ไม่ได้กรอง

---

## เคล็ดลับระดับมืออาชีพ & สิ่งที่ต้องระวัง

- **Pro tip:** ตรวจสอบ `Warning.Description` เสมอ – จะบอกชื่อฟอนต์ที่หายไปอย่างแม่นยำ ช่วยให้คุณตัดสินใจว่าจะต้องจัดส่งฟอนต์นั้นกับแอปหรือไม่  
- **ระวังฟอนต์ที่ฝังอยู่:** หาก DOCX ต้นฉบับฝังฟอนต์ที่ต้องการแล้ว Aspose.Words จะไม่ส่งคำเตือนการแทนที่ แม้ว่าฟอนต์นั้นจะไม่ได้ติดตั้งในเครื่องของคุณ  
- **ความปลอดภัยของเธรด:** `WarningInfoCollection` ไม่ได้ออกแบบให้ใช้หลายเธรดพร้อมกัน หากคุณโหลดหลายเอกสารพร้อมกัน ให้แต่ละเธรดมีคอลเลกชันของตนเอง  
- **ตรวจสอบเวอร์ชัน:** API คำเตือนมีความเสถียรตั้งแต่ Aspose.Words 20.8 ตรวจสอบให้แน่ใจว่าคุณใช้เวอร์ชันล่าสุดเพื่อไม่พลาดประเภทคำเตือนใหม่

---

## สรุป

เราได้ครอบคลุม **วิธีจับคำเตือน** จาก Aspose.Words, แสดงวิธี **รับข้อความคำเตือน**, และเสนอวิธี **จัดการฟอนต์ที่หายไป** ผ่านฟอนต์สำรองหรือโฟลเดอร์ฟอนต์แบบกำหนดเอง ตัวอย่างเต็มพร้อมใช้งานสามารถใส่ลงในโปรเจกต์ .NET ใดก็ได้ และแนวคิดนี้สามารถขยายไปสู่ไพพ์ไลน์อัตโนมัติขนาดใหญ่

ขั้นตอนต่อไปที่คุณอาจสนใจ:

- ใช้ `Document.WarningCallback` เพื่อจับคำเตือนระหว่างการ **บันทึก**  
- บันทึกคำเตือนลงไฟล์หรือระบบ telemetry สำหรับการตรวจสอบในสภาพแวดล้อมผลิต  
- ขยาย callback เพื่อแทนที่ฟอนต์ที่หายไปด้วยแบบอักษรเฉพาะแบรนด์ของคุณโดยอัตโนมัติ  

ลองทดลองดู – สลับฟอนต์สำรอง, เพิ่มเอกสารหลายไฟล์ใน batch, หรือรวม warning collector เข้าไปใน pipeline CI ที่ตรวจจับการถดถอยของฟอนต์ Happy coding, และขอให้เอกสารของคุณแสดงผลตามที่คุณคาดหวังเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}