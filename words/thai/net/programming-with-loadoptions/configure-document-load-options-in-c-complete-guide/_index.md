---
category: general
date: 2026-06-05
description: กำหนดค่าตัวเลือกการโหลดเอกสารใน C# เพื่อจัดการคำเตือนการแทนที่ฟอนต์และปรับแต่งพฤติกรรมการโหลดโดยใช้คอลแบ็กคำเตือน.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: th
og_description: กำหนดค่าตัวเลือกการโหลดเอกสารใน C# เพื่อจัดการคำเตือนการแทนที่ฟอนต์และปรับแต่งการโหลดเอกสารอย่างละเอียดด้วยคอลแบ็กคำเตือน
og_title: กำหนดค่าตัวเลือกการโหลดเอกสารใน C# – คู่มือครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: กำหนดค่าตัวเลือกการโหลดเอกสารใน C# – คู่มือฉบับสมบูรณ์
url: /th/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# กำหนดค่าตัวเลือกการโหลดเอกสารใน C# – คู่มือฉบับสมบูรณ์

เคยต้องการ **configure document load options** ใน C# เพราะพฤติกรรมการโหลดเริ่มต้นไม่ตอบโจทย์หรือไม่? บางทีคุณอาจเห็นการแทนที่ฟอนต์ที่ไม่คาดคิดหรือคุณต้องการบันทึกคำเตือนทุกข้อความที่ปรากฏระหว่างการนำเข้าไฟล์ ในบทเรียนนี้เราจะพาคุณผ่านโซลูชันเชิงปฏิบัติแบบครบวงจรที่ไม่เพียงตั้งค่าตัวเลือกเหล่านั้นเท่านั้น แต่ยังสาธิต **warning callback** สำหรับคำเตือนการแทนที่ฟอนต์

เราจะครอบคลุมทุกอย่างตั้งแต่โค้ดสั้น ๆ ที่สร้าง callback จนถึงช่วงที่คุณเปิดเอกสารด้วยการตั้งค่าที่กำหนดเองของคุณ ในตอนท้ายคุณจะได้รูปแบบที่นำกลับมาใช้ใหม่ได้ซึ่งสามารถใส่ลงในโปรเจกต์ Aspose.Words ใดก็ได้ ไม่ว่าจะเป็นการประมวลผลใบแจ้งหนี้ สัญญากฎหมาย หรือรายงานง่าย ๆ

## สิ่งที่คุณจะได้เรียนรู้

- วิธี **configure document load options** ด้วย `LoadOptions`.
- วิธีการทำ **warning callback** ที่จับการแจ้งเตือน `FontSubstitution`.
- ทำไมการจัดการ **font substitution warning** ตั้งแต่ต้นจึงช่วยป้องกันความประหลาดใจด้านการจัดหน้า.
- การจัดการกรณีขอบสำหรับฟอนต์ที่หายไปและวิธี fallback อย่างราบรื่น.
- ตัวอย่างโค้ดที่สมบูรณ์พร้อมคัดลอก‑วางที่คุณสามารถรันได้ทันที

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ทำงานกับ .NET Framework 4.6+ ด้วย)
- ติดตั้ง Aspose.Words for .NET (`dotnet add package Aspose.Words`)
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#

ถ้าคุณมีทั้งหมดนี้แล้ว ไปเริ่มกันเลย

## กำหนดค่าตัวเลือกการโหลดเอกสาร – ขั้นตอนโดยละเอียด

ด้านล่างเป็นขั้นตอนการทำงานเต็มรูปแบบที่แบ่งเป็นสี่ขั้นตอนชัดเจน แต่ละขั้นจะอธิบายแล้วตามด้วยบล็อกโค้ดสั้น ๆ ที่คุณสามารถวางลงใน Visual Studio ได้ทันที

### ขั้นตอนที่ 1: สร้าง Warning Callback สำหรับการแทนที่ฟอนต์

เริ่มกันเลย—**warning callback** คืออะไร? ใน Aspose.Words นั้นเป็น delegate ที่ถูกเรียกใช้ทุกครั้งที่ไลบรารีพบสิ่งที่ควรแจ้งเตือน เช่น ฟอนต์ที่หายไป โดยการจับ `WarningType.FontSubstitution` เราสามารถบันทึกฟอนต์ที่เครื่องยนต์ได้สลับออกมาได้อย่างแม่นยำ

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**ทำไมเรื่องนี้ถึงสำคัญ:** หากไม่มี callback ไลบรารีจะทำการแทนที่ฟอนต์ที่หายไปโดยเงียบ ๆ ซึ่งอาจทำให้ข้อความเสียรูปใน PDF หรือ DOCX สุดท้าย การแสดงคำเตือนทำให้คุณมองเห็นและสามารถตัดสินใจว่าจะฝังฟอนต์ที่หายไป, สลับไปใช้ fallback, หรือแจ้งผู้ใช้

> **เคล็ดลับ:** หากคุณต้องการจับ *ทุก* คำเตือน ให้ลบเงื่อนไข `if` ออก เพียงบันทึก `warningInfo.Description` สำหรับทุกเหตุการณ์

### ขั้นตอนที่ 2: ตั้งค่า LoadOptions พร้อม Callback

ตอนนี้เรามี callback แล้ว เราต้อง **configure document load options** เพื่อให้ใช้งานจริง `LoadOptions` เป็นคอนเทนเนอร์ขนาดเล็กที่บอก Aspose.Words ว่าจะทำงานอย่างไรในระหว่างการเรียกคอนสตรัคเตอร์ `Document`

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**ทำไมเรื่องนี้ถึงสำคัญ:** การกำหนด `WarningCallback` ทำให้คำเตือนทุกข้อความที่เกิดขึ้นในช่วงการโหลดถูกส่งผ่าน delegate ของเรา คุณยังสามารถปรับคุณสมบัติอื่นของ `LoadOptions` ได้ที่นี่—เช่น `LoadFormat` หากคุณรู้ประเภทไฟล์ที่แน่นอน หรือ `Password` สำหรับเอกสารที่เข้ารหัส

### ขั้นตอนที่ 3: โหลดเอกสารโดยใช้ตัวเลือกที่กำหนดไว้

เมื่อเชื่อมต่อ callback แล้ว ขั้นตอนสุดท้ายคือการ **load the document** จริง ๆ คอนสตรัคเตอร์ `Document` รับพาธไฟล์และ `LoadOptions` ที่เราตั้งค่าไว้

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

หากไฟล์ต้นทางอ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเครื่อง คุณจะเห็นบรรทัดเช่น:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

ในคอนโซล การตอบสนองทันทีนี้ทำให้คุณตัดสินใจได้ว่าจะจัดส่งฟอนต์ที่หายไปพร้อมกับแอปของคุณหรือแทนที่โดยโปรแกรม

### ขั้นตอนที่ 4: ตัวเลือก – ตรวจสอบฟอนต์ที่โหลด (การจัดการกรณีขอบ)

บางครั้งคุณอาจต้องการ *pre‑validate* เอกสารก่อนโหลดเต็มที่ โดยเฉพาะในสถานการณ์การประมวลผลเป็นชุด Aspose.Words มีคลาส `FontSettings` ที่สามารถแสดงฟอนต์ที่ต้องการได้

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**เมื่อใดควรใช้:** หากคุณดูแลคลังฟอนต์ส่วนตัว (เช่น ฟอนต์แบรนด์ขององค์กร) การชี้ `FontSettings` ไปยังโฟลเดอร์นั้นทำให้เครื่องยนต์พบแบบอักษรที่ถูกต้องโดยไม่ต้อง fallback ไปยังฟอนต์ทั่วไป

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมทั้งหมด—คัดลอก วาง และรันได้เลย มันสาธิตทุกอย่างตั้งแต่การสร้าง callback จนถึงการโหลดเอกสารขั้นสุดท้าย

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

หากไม่มีฟอนต์ที่หายไป callback จะเงียบอย่างเดียว—ไม่มีอะไรต้องกังวล

## คำถามทั่วไป & กรณีขอบ

### ถ้า warning callback โยนข้อยกเว้นจะเป็นอย่างไร?

callback ทำงานบนเธรดเดียวกับที่โหลดเอกสาร การโยนข้อยกเว้นภายใน delegate จะทำให้การโหลดหยุดและส่งต่อข้อยกเว้นนั้น ให้ห่อหุ้มตรรกะของคุณด้วย `try/catch` หากต้องการความทนทาน

### ฉันสามารถปิด *ทุก* คำเตือนแทนการจัดการได้หรือไม่?

ได้—ตั้งค่า `loadOptions.WarningCallback = null;` หรือให้ callback ที่ไม่ทำอะไรเลย ระวังว่าคุณจะสูญเสียการมองเห็นปัญหาที่อาจเกิดขึ้น

### วิธีนี้ทำงานกับไฟล์ DOCX ที่เข้ารหัสหรือไม่?

แน่นอน เพียงเพิ่ม `Password = "yourPassword"` ไปยัง `LoadOptions` ก่อนสร้าง `Document` warning callback ยังจะทำงานสำหรับปัญหาฟอนต์

### วิธีนี้แตกต่างจากการใช้ `DocumentBuilder` อย่างไร?

`DocumentBuilder` ใช้สำหรับ *สร้าง* หรือ *แก้ไข* เอกสารหลังจากโหลดแล้ว **Configure document load options** มีผลต่อขั้นตอนการพาร์เซิง *เริ่มต้น* ซึ่งเป็นจุดที่ตัดสินใจการแทนที่ฟอนต์

## ภาพรวมเชิงภาพ

![แผนภาพแสดงกระบวนการกำหนดค่าตัวเลือกการโหลดเอกสาร](https://example.com/images/load-options-flow.png "แผนภาพแสดงกระบวนการกำหนดค่าตัวเลือกการโหลดเอกสาร")

*ภาพนี้แสดงกระบวนการ: callback → LoadOptions → คอนสตรัคเตอร์ Document → การจัดการคำเตือน*

## สรุป

ตอนนี้คุณรู้วิธี **configure document load options** ใน C# เพื่อจับคำเตือนการแทนที่ฟอนต์, แทรกโฟลเดอร์ฟอนต์แบบกำหนดเอง, และควบคุมกระบวนการโหลดอย่างเต็มที่ รูปแบบนี้ทำให้คุณมั่นใจว่าฟอนต์ที่หายไปทุกตัวจะถูกรายงาน ช่วยให้คุณรักษาความสมบูรณ์ของเอกสารในทุกสภาพแวดล้อม

ขั้นตอนต่อไป? ลองเปลี่ยนการบันทึกในคอนโซลเป็นระบบ telemetry ที่แข็งแกร่งขึ้น หรือรวมวิธีนี้กับ `DocumentBuilder` เพื่อแทนที่ฟอนต์ที่หายไปโดยอัตโนมัติด้วยฟอนต์เริ่มต้นขององค์กร คุณอาจสำรวจค่า `WarningType` อื่น ๆ เช่น `DocumentStructure` เพื่อรับข้อมูลเชิงลึกที่ลึกขึ้น

ขอให้เขียนโค้ดอย่างสนุกสนาน และขอให้เอกสารของคุณแสดงผลตรงตามที่คุณต้องการเสมอ!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการนำไปใช้แบบอื่นในโปรเจกต์ของคุณ

- [เชี่ยวชาญ Aspose.Words Markdown Load Options ใน Python เพื่อการประมวลผลเอกสารที่ดียิ่งขึ้น](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [เพิ่มประสิทธิภาพการโหลดเอกสารด้วยตัวเลือก HTML, RTF, และ TXT](/words/english/java/word-processing/optimizing-document-loading-options/)
- [การใช้ Document Options และ Settings ใน Aspose.Words สำหรับ Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}