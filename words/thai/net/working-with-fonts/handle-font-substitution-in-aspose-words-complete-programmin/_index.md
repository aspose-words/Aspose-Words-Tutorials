---
category: general
date: 2026-06-17
description: จัดการการแทนที่ฟอนต์ใน Aspose.Words และตรวจจับฟอนต์ที่หายไปอย่างรวดเร็วด้วยบทแนะนำแบบขั้นตอนต่อขั้นตอนสำหรับนักพัฒนา
  .NET
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: th
og_description: จัดการการแทนที่ฟอนต์ใน Aspose.Words และเรียนรู้วิธีตรวจจับฟอนต์ที่หายไปในเอกสารของคุณด้วยตัวอย่างโค้ดที่ชัดเจน
og_title: จัดการการแทนที่ฟอนต์ใน Aspose.Words – คู่มือเต็ม
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: จัดการการแทนที่ฟอนต์ใน Aspose.Words – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์
url: /th/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# จัดการการแทนที่ฟอนต์ใน Aspose.Words – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์

เคยสงสัยไหมว่า **จะจัดการการแทนที่ฟอนต์** อย่างไรเมื่อเอกสาร Word อ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์? คุณไม่ได้อยู่คนเดียว ในแอปพลิเคชันจริงหลาย ๆ ตัว—เช่น ตัวสร้างใบแจ้งหนี้หรือบริการรายงานอัตโนมัติ—ฟอนต์ที่หายไปทำให้เกิดการเปลี่ยนฟอนต์โดยอัตโนมัติที่ทำลายการจัดวาง  

ข่าวดีคือ Aspose.Words มีระบบเตือนในตัวที่ช่วยให้คุณ **ตรวจจับฟอนต์ที่หายไป** และตอบสนองตามที่ต้องการ ในบทแนะนำนี้เราจะเดินผ่านการลงทะเบียนตัวจัดการการเตือน, การโหลดเอกสาร, และการดึงเหตุการณ์การแทนที่ฟอนต์ที่คุณต้องการทราบ สุดท้ายคุณจะเห็นวิธีตอบคำถามคลาสสิก “**วิธีตรวจจับฟอนต์ที่หายไป**?” ด้วยโค้ดที่สะอาดและพร้อมใช้งานในสภาพแวดล้อมการผลิต

## สิ่งที่บทแนะนำนี้ครอบคลุม

* ตั้งค่า Aspose.Words ให้ส่งการเตือนสำหรับทุกการแทนที่ฟอนต์
* ดักจับการเตือนเหล่านั้นด้วยตัวจัดการแบบกำหนดเองเพื่อบันทึก, แทนที่, หรือยกเลิกกระบวนการ
* ใช้ข้อมูลที่ดักจับได้เพื่อ **ตรวจจับฟอนต์ที่หายไป** ก่อนบันทึกหรือแสดงผลเอกสาร
* เคล็ดลับการแก้ไขปัญหาในกรณีขอบ—เช่น เมื่อฟอนต์สำรองถูกเลือกโดยเงียบ ๆ
* ตัวอย่างที่สมบูรณ์และสามารถรันได้ซึ่งคุณสามารถนำไปใส่ในแอปคอนโซล .NET ใดก็ได้

> **Prerequisites** – คุณจะต้องมี .NET SDK เวอร์ชันล่าสุด (6.0 ขึ้นไป), ไลเซนส์ Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ประเมินผลชั่วคราว), และไฟล์ DOCX ตัวอย่างที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้งไว้โดยเจตนา ไม่ต้องใช้ไลบรารีของบุคคลที่สามอื่นใด

---

## ## จัดการการแทนที่ฟอนต์ด้วยตัวจัดการการเตือนแบบกำหนดเอง

Aspose.Words จะสร้างอ็อบเจ็กต์ `WarningInfo` ทุกครั้งที่ไม่พบฟอนต์ที่ร้องขอ โดยค่าเริ่มต้นการเตือนเหล่านี้จะถูกละเลย ซึ่งเป็นเหตุผลที่คุณมักไม่สังเกตเห็นการแทนที่ เพื่อ **จัดการการแทนที่ฟอนต์** คุณต้องแทนที่ตัวจัดการการเตือนเริ่มต้นด้วยตัวที่ทำอะไรสักอย่างจริง ๆ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### ทำไมวิธีนี้ถึงได้ผล

* `FontSettings.DefaultWarningHandler` เป็นคุณสมบัติสแตติกระดับทั่วโลก—เมื่อคุณตั้งค่าแล้ว **ทุก** การดำเนินการของ Aspose.Words ใน AppDomain ปัจจุบันจะใช้ delegate ของคุณ
* `WarningInfoCollectionHandler` จะรับอ็อบเจ็กต์ `WarningInfo` ที่มี `WarningType` และ `Description` ที่อ่านได้โดยมนุษย์ การกรองด้วย `WarningType.FontSubstitution` ทำให้คุณเห็นเฉพาะเหตุการณ์ที่สนใจเท่านั้น
* การเรียก `doc.Save` จะบังคับให้ไลบรารีแก้ไขฟอนต์ทั้งหมด ซึ่งเป็นจังหวะที่การเตือนจะถูกส่ง หากคุณต้องการตรวจสอบเอกสารโดยไม่บันทึก สามารถเรียก `doc.UpdatePageLayout()` แทนได้

**ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล** (สมมติว่าฟอนต์ที่หายไปคือ “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

บรรทัดนั้นเป็นหลักฐานว่าห้องสมุด **ตรวจจับฟอนต์ที่หายไป** และเลือกฟอนต์สำรองแล้ว

---

## ## ตรวจจับฟอนต์ที่หายไปก่อนการแสดงผล

บางครั้งคุณอาจต้องหยุดกระบวนการทั้งหมดหากฟอนต์ที่จำเป็นหายไป—เช่น เมื่อแนวทางแบรนด์กำหนดให้ต้องใช้ตัวอักษรที่แน่นอน ตัวจัดการการเตือนสามารถขยายให้เก็บข้อความฟอนต์ที่หายไปทั้งหมดไว้ในรายการ แล้วคุณจึงตัดสินใจได้

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### วิธีที่ตอบคำถาม “วิธีตรวจจับฟอนต์ที่หายไป”

* รายการ `missingFonts` ทำหน้าที่เป็นบันทึกของทุกเหตุการณ์การแทนที่
* หลังจาก `UpdatePageLayout` คุณสามารถตรวจสอบรายการนี้และตัดสินใจว่าจะดำเนินต่อ, บันทึก, หรือโยนข้อยกเว้น
* รูปแบบนี้ทำงานกับรูปแบบผลลัพธ์ใด ๆ (PDF, HTML, ภาพ) เพราะระบบการเตือนเป็นอิสระต่อรูปแบบ

---

## ## เคล็ดลับขั้นสูง: แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรองที่กำหนด

หากองค์กรของคุณมีฟอนต์เฉพาะที่ต้องใช้ คุณสามารถบอก Aspose.Words ให้แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรองของคุณโดยอัตโนมัติ วิธีนี้มีประโยชน์เมื่อคุณต้องการให้เอกสารยังคงดูดีโดยไม่ต้องทำการประมวลผลหลังจากสร้าง

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

วางโค้ดส่วนนี้ **ก่อน** โหลดเอกสาร จากนี้ไปฟอนต์ที่หายไป—ไม่ว่าจะชื่ออะไร—จะถูกสลับเป็น “Calibri” (หรือ “Arial” หากไม่มี Calibri) คุณยังคงได้รับการเตือน แต่เอกสารจะถูกแสดงผลด้วยฟอนต์ที่คุณกำหนด

---

## ## ข้อผิดพลาดทั่วไป & วิธีหลีกเลี่ยง

| ข้อผิดพลาด | สาเหตุ | วิธีแก้ |
|------------|--------|--------|
| **การเตือนหายไปหลังจากเรียกครั้งแรก** | `DefaultWarningHandler` สแตติกถูกเขียนทับภายหลังในแอป | ตั้งค่าตัวจัดการ **ครั้งเดียว** ตอนเริ่มแอป หรือเก็บอ้างอิงแล้วกำหนดใหม่เมื่อจำเป็น |
| **รายงานฟอนต์ที่หายไปเพียงฟอนต์แรก** | บาง API ทำการแบตช์การเตือน; คุณต้องเรียก `UpdatePageLayout` หรือ `Save` เพื่อปล่อยคิว | บังคับอัปเดตเลย์เอาต์หรือบันทึกในรูปแบบที่ต้องการสร้าง |
| **การแทนที่ยังคงเกิดขึ้นแม้ยกเลิก** | ตัวจัดการการเตือนทำงาน *หลัง* การแทนที่เกิดขึ้นแล้ว | ใช้ตัวจัดการเพื่อ **บันทึก** แล้วโยนข้อยกเว้นเพื่อหยุดการประมวลผลต่อ |
| **ฟอนต์หายไปในคอนเทนเนอร์ Linux** | Linux มักไม่มีแคตาล็อกฟอนต์ของ Windows ทำให้เกิดการแทนที่หลายครั้ง | เมานท์ฟอนต์ที่ต้องการเข้าในคอนเทนเนอร์หรือใช้ `FontSettings.SetFontsFolder` ชี้ไปยังไดเรกทอรีฟอนต์ของคุณเอง |

---

## ## ตรวจจับการแทนที่ฟอนต์ในสถานการณ์ Web API

หากคุณให้บริการเอกสารผ่าน ASP.NET Core คุณอาจไม่ต้องการให้มีการเขียนลงคอนโซล แทนที่จะนั้นให้เก็บการเตือนและส่งกลับเป็นส่วนหนึ่งของ HTTP response

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

ตอนนี้ API **ตรวจจับฟอนต์ที่หายไป** และส่งคืน payload JSON ที่ชัดเจนก่อนที่ PDF จะถูกสร้าง นี่คือตัวอย่างการประยุกต์ “วิธีตรวจจับฟอนต์ที่หายไป” ในบริการระดับผลิต

---

## ## ทดสอบการทำงานของคุณ

1. **สร้างไฟล์ DOCX ทดสอบ** ที่อ้างอิงฟอนต์ที่คุณรู้ว่าไม่มีในเครื่อง (เช่น “Comic Sans MS” บน Docker image ที่มีขนาดเล็ก)  
2. รันแอปคอนโซลหรือ endpoint ของ API  
3. ยืนยันว่าคอนโซล (หรือ HTTP response) แสดงการเตือนการแทนที่ฟอนต์  
4. ทางเลือก: เปิด PDF ที่ได้และตรวจสอบคุณสมบัติฟอนต์—Aspose.Words ควรแสดงฟอนต์สำรองที่คุณกำหนดไว้

หากคุณเห็นการเตือนแต่ PDF ยังคงใช้ฟอนต์ที่ไม่คาดคิด ให้ตรวจสอบลำดับของ `SubstitutionSettings` อีกครั้ง; การจับคู่แรกจะชนะ

---

## ## สรุป

เราได้ครอบคลุมทุกอย่างที่คุณต้องการ **จัดการการแทนที่ฟอนต์** ใน Aspose.Words ตั้งแต่การลงทะเบียนตัวจัดการการเตือนจนถึงการตรวจจับฟอนต์ที่หายไปแบบโปรแกรมและแม้กระทั่งการแทนที่ด้วยฟอนต์ขององค์กร การใช้ระบบการเตือนในตัวทำให้คุณมองเห็นทุกเหตุการณ์ “ฟอนต์ไม่พบ” ซึ่งตอบคำถาม “**วิธีตรวจจับฟอนต์ที่หายไป**?” ที่นักพัฒนามักถามเมื่อทำอัตโนมัติการสร้างเอกสาร

ต่อไปคุณอาจลองผสานตรรกะนี้กับ **การโหลดฟอนต์แบบไดนามิก** (`FontSettings.SetFontsFolder`) เพื่อรองรับฟอนต์ที่ผู้ใช้อัปโหลดแบบเรียลไทม์ หรือขยายตัวจัดการการเตือนให้เขียนบันทึกลงบริการ logging กลางอย่าง Serilog ยิ่งคุณทำเครื่องมือเฝ้าติดตามฟอนต์มากเท่าไหร่ กระบวนการเอกสารของคุณก็ยิ่งเชื่อถือได้มากขึ้น

มีสถานการณ์การแทนที่ฟอนต์ที่คุณกำลังต่อสู้อยู่ไหม? แสดงความคิดเห็นด้านล่าง แล้วมาช่วยกันแก้ไขกันเถอะ Happy coding!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้เกี่ยวกับหัวข้อที่ใกล้เคียงและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ ทุกแหล่งข้อมูลมีโค้ดตัวอย่างทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [วิธีตรวจจับฟอนต์ใน Aspose.Words – จัดการการเตือนและการตั้งค่า](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [เปิดใช้งานการเตือนการแทนที่ฟอนต์ใน Aspose.Words – คู่มือฉบับสมบูรณ์](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [วิธีโหลด DOCX และตรวจจับฟอนต์ที่หายไป – คู่มือ C# ฉบับสมบูรณ์](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}