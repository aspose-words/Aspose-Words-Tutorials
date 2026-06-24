---
category: general
date: 2026-05-23
description: ตั้งค่า callback คำเตือนของ Aspose เพื่อจับคำเตือนการแทนที่ฟอนต์ใน Aspose.Words.
  เรียนรู้ LoadOptions, FontSettings และการทำงานของ IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: th
og_description: ตั้งค่า callback คำเตือนของ Aspose เพื่อเฝ้าติดตามการแทนที่ฟอนต์ใน
  Aspose.Words การสอนนี้แสดงการใช้ LoadOptions, FontSettings และการทำงานของตัวจัดการคำเตือน
og_title: ตั้งค่าการแจ้งเตือน callback ของ Aspose – คู่มือทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: ตั้งค่า callback คำเตือน Aspose – คู่มือฉบับสมบูรณ์สำหรับการโหลดเอกสาร Word
url: /th/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่า warning callback aspose – คู่มือฉบับสมบูรณ์สำหรับการโหลดเอกสาร Word

Ever wondered how to **set warning callback aspose** so you never miss a font‑substitution alert again? You're not alone. When a DOCX references a font that isn’t installed, Aspose.Words silently swaps it, and without a proper callback you might never know something changed.

ในบทแนะนำนี้ เราจะพาคุณผ่านตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่งแสดงให้เห็นอย่างชัดเจนว่าจับคำเตือนเหล่านั้นอย่างไร ในตอนท้ายคุณจะเข้าใจ **Aspose.Words LoadOptions** วิธีการกำหนดค่า **FontSettings** และเหตุผลที่การทำ **IWarningCallback** เป็นวิธีที่สะอาดที่สุดเพื่อให้คุณรับทราบ ไม่ได้มีเนื้อหาเกินความจำเป็น—เพียงโค้ดที่คุณสามารถนำไปใช้ในโปรเจกต์ .NET วันนี้.

## สิ่งที่คุณจะได้เรียนรู้

- วิธี **set warning callback aspose** บนอินสแตนซ์ `LoadOptions`.  
- บทบาทของ **Aspose.Words LoadOptions** เมื่อเปิดเอกสาร.  
- การกำหนดค่า **Aspose fonts substitution** ด้วย `FontSettings`.  
- การเขียน **IWarningCallback implementation** แบบกำหนดเองเพื่อบันทึกปัญหาฟอนต์.  
- การโหลดเอกสารอย่างปลอดภัยด้วยแนวทางปฏิบัติที่ดีที่สุดของ **Aspose document loading**.

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ทำงานบน .NET Framework 4.5+ ด้วยเช่นกัน).  
- ใบอนุญาต Aspose.Words for .NET ที่ถูกต้องหรือคีย์ทดลอง.  
- Visual Studio, Rider หรือเครื่องมือแก้ไข C# ใดก็ได้ที่คุณชอบ.  
- ไฟล์ DOCX ตัวอย่าง (`fontTest.docx`) ที่อ้างอิงฟอนต์ที่หายไป (เป็นตัวเลือกแต่เป็นประโยชน์).

> **เคล็ดลับ:** หากคุณไม่มีไฟล์ DOCX ที่ฟอนต์หายไป เพียงเปลี่ยนชื่อฟอนต์ในสไตล์ของเอกสารและดูการแจ้งเตือนทำงาน.

---

## วิธีตั้งค่า warning callback aspose สำหรับการโหลดเอกสาร

ด้านล่างเป็นโปรแกรมที่สมบูรณ์และทำงานได้เอง บันทึกเป็น `Program.cs` คืนค่าแพ็กเกจ NuGet แล้วรัน คอนโซลจะพิมพ์คำเตือนการแทนที่ฟอนต์ทุกอย่างที่ Aspose.Words สร้างขึ้นขณะโหลดไฟล์.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล

หาก `fontTest.docx` อ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง คุณจะเห็นอย่างนี้:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

หากฟอนต์ทั้งหมดมีอยู่บรรทัดเดียวที่พิมพ์ออกมาจะเป็น *Document loaded successfully*—ไม่มีคำเตือน ไม่มีเสียงรบกวน.

![set warning callback aspose example](image.png "set warning callback aspose example")

---

## ทำความเข้าใจ LoadOptions ใน Aspose.Words

`LoadOptions` คือประตูสู่การปรับแต่งทุกอย่างที่คุณทำได้กับ **aspose document loading** มันให้คุณ:

1. **Specify a custom `FontSettings`** – มีประโยชน์เมื่อแอปของคุณมีฟอนต์ของตัวเอง.  
2. **Attach a warning callback** – เหมือนที่เราทำเพื่อจับการแทนที่ฟอนต์.  
3. ควบคุมการตรวจจับรูปแบบเอกสาร, การจัดการรหัสผ่าน, และอื่นๆ.

เนื่องจาก `LoadOptions` ถูกส่งไปยังคอนสตรัคเตอร์ของ `Document` การตั้งค่าจะถูกใช้ **หนึ่งครั้ง** ทันทีที่ไฟล์ถูกวิเคราะห์ นั่นคือเหตุผลที่เรามั่นใจว่าฮandler คำเตือนของเราจะเห็นการแทนที่ทุกครั้งก่อนที่เอกสารจะถูกสร้างในหน่วยความจำ.

### เมื่อควรใช้ LoadOptions แบบกำหนดเอง

- **Batch processing** ของไฟล์หลายไฟล์ที่คุณต้องการกลยุทธ์การบันทึกแบบสม่ำเสมอ.  
- **Cloud services** ที่ต้องรายงานฟอนต์ที่หายไปกลับไปยังผู้เรียก.  
- **Testing pipelines** ที่ตรวจสอบว่าเอกสารสอดคล้องกับนโยบายฟอนต์ขององค์กร.

---

## การกำหนดค่า FontSettings สำหรับ Aspose fonts substitution

อ็อบเจ็กต์ `FontSettings` ควบคุมวิธีที่ Aspose.Words แก้ไขฟอนต์ โดยค่าเริ่มต้นมันจะค้นหาโฟลเดอร์ฟอนต์ของระบบ แล้วใช้การแทนที่ในตัว หากต้องการคุณสามารถปรับจูนพฤติกรรมนี้ได้:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

บรรทัดเหล่านี้เป็นตัวเลือกสำหรับสถานการณ์ “set warning callback aspose” เบื้องต้น แต่แสดงให้เห็นว่าคุณสามารถ **ลด** จำนวนคำเตือนการแทนที่โดยการจัดเตรียมฟอนต์ที่เหมาะสมล่วงหน้า.

---

## การทำ IWarningCallback สำหรับคำเตือนการแทนที่ฟอนต์

อินเทอร์เฟซ `IWarningCallback` มีขนาดเล็ก—เพียงเมธอด `Warning` เดียว แต่ให้คุณ **ควบคุมเต็มที่** วิธีการจัดการคำเตือน:

- **บันทึกลงไฟล์** แทนคอนโซล.  
- **เก็บคำเตือน** ในรายการเพื่อวิเคราะห์ต่อในภายหลัง.  
- **โยนข้อยกเว้น** สำหรับคำเตือนสำคัญ (เช่น เมื่อฟอนต์ที่จำเป็นหายไป).

นี่คือตัวอย่างสั้นที่เก็บคำเตือนใน `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

จากนั้นคุณสามารถตรวจสอบ `handler.Messages` หลังจากโหลดเอกสารเพื่อพิจารณาว่าจะยกเลิกการประมวลผลหรือไม่.

---

## การโหลดเอกสารด้วยการจัดการคำเตือนแบบกำหนดเอง (เวิร์กโฟลว์เต็มรูปแบบ)

เมื่อรวมทุกอย่างเข้าด้วยกัน แพทเทิร์นสุดท้ายที่คุณอาจใช้ซ้ำดูเหมือนนี้:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

สแนปเพตนี้แสดงกระบวนการ **aspose document loading** ที่คุณจะใช้ในการผลิต: กำหนดค่า, โหลด, แล้วตอบสนอง แพทเทิร์นนี้ขยายได้ดีไม่ว่าจะประมวลผลไฟล์เดียวหรือวนลูปหลายพันไฟล์.

---

## คำถามทั่วไป & กรณีขอบ

**ถ้าเอกสารถูกป้องกันด้วยรหัสผ่าน?**  
เพิ่ม `Password = "secret"` ไปยังตัวเริ่มต้นของ `LoadOptions` คำเตือน callback ยังทำงานเมื่อไฟล์ถูกถอดรหัส.

**คำเตือน callback จะทำงานกับประเภทคำเตือนอื่นหรือไม่?**  
ใช่—`WarningInfo.Type` สามารถเป็น `DocumentStructure`, `UnsupportedFileFormat` เป็นต้น ในตัวอย่างของเราเราเลือกกรองเฉพาะ `FontSubstitution` แต่คุณสามารถบันทึกทั้งหมดได้โดยลบการตรวจสอบ `if`.

**นี่ส่งผลต่อประสิทธิภาพหรือไม่?**  
แทบไม่มีผล คำเตือน callback จะถูกเรียกเฉพาะเมื่อเกิดคำเตือน ซึ่งน้อยกว่าขั้นตอนการพาร์เซปกติอย่างมาก.

**ฉันสามารถปิดการแทนที่ฟอนต์ทั้งหมดได้หรือไม่?**  
คุณสามารถตั้งค่า `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` แต่ Aspose.Words จะโยนข้อยกเว้นเมื่อฟอนต์หายไปแทนการสลับ.

---

## สรุป

ตอนนี้คุณรู้วิธี **set warning callback aspose** เพื่อเฝ้าติดตามเหตุการณ์การแทนที่ฟอนต์ระหว่างการประมวลผล **Aspose.Words LoadOptions** แล้ว การกำหนดค่า `FontSettings` การทำ `IWarningCallback` แบบเบา และการโหลดเอกสารด้วยตัวเลือกเหล่านั้น ทำให้คุณมองเห็นการเปลี่ยนแปลงฟอนต์ใดๆ ที่ Aspose ทำเบื้องหลังได้อย่างเต็มที่  

จากนี้คุณอาจ:

- ขยาย warning handler เพื่อเขียนไปยังบริการบันทึกศูนย์กลาง.  
- ผสาน callback กับกลยุทธ์ fallback ฟอนต์แบบกำหนดเอง.  
- ใช้แพทเทิร์นนี้เมื่อสร้าง API คลาวด์ที่ตรวจสอบเอกสารที่ลูกค้าอัปโหลด.

ลองใช้กับไฟล์ DOCX ของคุณเอง ปรับ `FontSettings` แล้วดูคอนโซลบอกคุณว่าฟอนต์ใดบ้างที่ถูกสลับ ขอให้เขียนโค้ดสนุกและเอกสารของคุณแสดงผลตามที่ต้องการเสมอ!

## บทแนะนำที่เกี่ยวข้อง

- [จับคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [เปิดใช้งานคำเตือนการแทนที่ฟอนต์ใน Aspose.Words – คู่มือฉบับสมบูรณ์](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [วิธีตั้งค่า LoadOptions ใน Aspose.Words สำหรับ Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}