---
category: general
date: 2026-03-19
description: เรียนรู้วิธีดักจับคำเตือนใน Aspose.Words, ตั้งค่าฟอนต์เริ่มต้น, และตรวจจับฟอนต์ที่หายไปเมื่อโหลดเอกสาร
  Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: th
og_description: วิธีดักจับคำเตือนใน Aspose.Words, ตั้งค่าฟอนต์เริ่มต้น, และตรวจจับฟอนต์ที่หายไปเมื่อโหลดเอกสาร
  Word.
og_title: วิธีจับคำเตือน – ตั้งค่าฟอนต์เริ่มต้น
tags:
- Aspose.Words
- C#
- Document Processing
title: วิธีดักจับคำเตือน – ตั้งค่าฟอนต์เริ่มต้น
url: /th/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีจับคำเตือน – ตั้งค่าฟอนต์เริ่มต้น

**How to capture warnings** เป็นความต้องการทั่วไปเมื่อคุณทำงานกับ Aspose.Words, โดยเฉพาะอย่างยิ่งหากเอกสารของคุณพึ่งพาฟอนต์เฉพาะที่อาจไม่มีบนเครื่องเป้าหมาย. เคยเปิดไฟล์ DOCX แล้วสงสัยว่าทำไมการจัดวางถึงดูผิดปกติไหม? คำตอบมักซ่อนอยู่ในคำเตือนเกี่ยวกับฟอนต์ที่หายไป.  

ในคู่มือนี้เราจะอธิบาย **how to capture warnings** ขณะ **load word document**, ตั้งค่า **set default font settings**, และสุดท้าย **detect missing fonts** เพื่อให้คุณสามารถตอบสนองโดยอัตโนมัติ. ไม่มีส่วนเกิน—เพียงตัวอย่างที่ทำงานได้เต็มรูปแบบและเหตุผลเบื้องหลังแต่ละบรรทัด.

> *Pro tip:* การจับคำเตือนตั้งแต่ต้นจะช่วยคุณหลีกเลี่ยงการดีบักปัญหาการจัดวางที่ลึกลับในภายหลัง.

---

## สิ่งที่คุณต้องการ

- **Aspose.Words for .NET** (เวอร์ชันล่าสุด ณ ปี 2026).  
- สภาพแวดล้อมการพัฒนา .NET (Visual Studio, Rider, หรือ VS Code).  
- ตัวอย่างไฟล์ DOCX ที่อ้างอิงฟอนต์ที่คุณ *ไม่ได้* ติดตั้ง (เช่น *Comic Sans MS* บนเครื่อง Linux).  

เท่านี้เอง ไม่ต้องใช้ NuGet แพคเกจเพิ่มเติมนอกจาก Aspose.Words.

---

## ขั้นตอนที่ 1 – ทำความเข้าใจว่าทำไมคุณต้องจับคำเตือน

เมื่อ Aspose.Words วิเคราะห์เอกสาร มันอาจเจอฟอนต์ที่ไม่มีบนเครื่องโฮสต์. โดยค่าเริ่มต้นไลบรารีจะทำการแทนที่ฟอนต์ด้วยฟอนต์สำรองโดยเงียบ ๆ ซึ่งอาจทำให้การตัดบรรทัด, ระยะห่าง, หรือแม้กระทั่งข้อความหายไป.  

การใช้ **WarningCallback** ร่วมกับอ็อบเจกต์ **FontSettings** ให้คุณได้สองอย่าง:

1. **Visibility** – คุณจะได้รับรายการ `WarningInfo` สำหรับการแทนที่แต่ละครั้ง.  
2. **Control** – คุณสามารถกำหนดฟอนต์เริ่มต้นล่วงหน้าเพื่อ ลดความประหลาดใจด้านการแสดงผล.

คิดว่าเป็นการติดตั้ง “watchdog” ที่จะส่งเสียงเตือนทุกครั้งที่เครื่องยนต์สลับชิ้นส่วนภายใต้ฝากระโปรง.

---

## ขั้นตอนที่ 2 – ตั้งค่าฟอนต์เริ่มต้น

คีย์เวิร์ดรองแรก, **set default font settings**, ปรากฏที่นี่. คุณสร้างอินสแตนซ์ `FontSettings` และอาจระบุโฟลเดอร์ที่มีฟอนต์สำรองของคุณ.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Why?**  
> หากคุณไม่ได้กำหนดฟอนต์สำรอง, Aspose.Words จะเลือกฟอนต์ระบบแรกที่ตรงกับสไตล์, ซึ่งอาจแตกต่างอย่างมาก. การตั้งค่าฟอนต์เริ่มต้นที่รู้จักทำให้การเรนเดอร์คงที่ข้ามเครื่องต่าง ๆ.

---

## ขั้นตอนที่ 3 – เตรียม Warning Callback เพื่อจับคำเตือน

ต่อไปเราจะ **how to capture warnings** โดยเชื่อม `WarningInfoCollection` กับตัวเลือกการโหลด. คอลเลกชันนี้จะเก็บคำเตือนทุกข้อความที่เกิดขึ้นระหว่างกระบวนการโหลด.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` implements `IWarningCallback`, ดังนั้น Aspose.Words จะส่งคำเตือนแต่ละรายการอัตโนมัติไปยัง `warningInfos`. ไม่ต้องทำการ polling.

---

## ขั้นตอนที่ 4 – โหลดเอกสาร Word ด้วยตัวเลือกที่กำหนดค่าไว้

นี่คือจุดที่คีย์เวิร์ดรองที่สอง, **load word document**, ส่องแสง. เราจะส่งทั้ง `FontSettings` และ `WarningCallback` ผ่านอินสแตนซ์ `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

หากเอกสารอ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง, callback จะจับรายการ `WarningType.FontSubstitution`.

---

## ขั้นตอนที่ 5 – ตรวจจับฟอนต์ที่หายไปจากคำเตือนที่เก็บรวบรวม

สุดท้าย เราตอบคีย์เวิร์ดรองที่สาม, **detect missing fonts**, โดยวนลูปผ่านคำเตือนที่เก็บไว้.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

ผลลัพธ์ที่พบบ่อยจะมีลักษณะเช่นนี้:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

บรรทัดนั้นบอกคุณอย่างชัดเจนว่าฟอนต์ใดหายไปและฟอนต์สำรองใดถูกใช้—ข้อมูลที่คุณสามารถบันทึก, แสดงให้ผู้ใช้เห็น, หรือแม้กระทั่งเรียกใช้ขั้นตอนติดตั้งฟอนต์แบบกำหนดเอง.

---

## ตัวอย่างที่สามารถรันได้ครบถ้วน

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถ copy‑paste ไปยังแอปพลิเคชันคอนโซล. มันสาธิต **how to capture warnings**, **set default font settings**, **load word document**, และ **detect missing fonts** ในกระบวนการเดียวกัน.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Expected result:** เมื่อ DOCX ที่ระบุอ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง, คอนโซลจะแสดงคำเตือนสำหรับแต่ละการแทนที่. หากฟอนต์ทั้งหมดมีอยู่, ลูปจะไม่มีการแสดงผลใด ๆ.

---

## ข้อผิดพลาดทั่วไปและกรณีขอบเขต

| Situation | Why it Happens | How to Handle It |
|-----------|----------------|------------------|
| **ไม่มีคำเตือนปรากฏ** แม้ว่าการจัดวางจะแสดงผลผิด | เอกสารอาจใช้ฟอนต์ *embedded* ซึ่ง Aspose.Words จะเรนเดอร์โดยไม่ต้องทำการแทนที่. | ตรวจสอบ `Document.HasEmbeddedFonts` และพิจารณาดึงฟอนต์ที่ฝังไว้ออกมา หากคุณต้องการใช้บนเครื่องอื่น. |
| **หลายคำเตือนสำหรับ** |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}