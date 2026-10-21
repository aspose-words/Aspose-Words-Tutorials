---
category: general
date: 2026-06-24
description: วิธีใช้ IWarningCallback เพื่อตรวจจับฟอนต์ที่หายไปในเอกสาร Aspose.Words
  เรียนรู้ตัวอย่างที่ทำงานได้เต็มรูปแบบและแนวปฏิบัติที่ดีที่สุด
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: th
og_description: วิธีใช้ IWarningCallback เพื่อตรวจจับฟอนต์ที่หายไปใน Aspose.Words.
  ปฏิบัติตามคู่มือขั้นตอนต่อขั้นตอนเพื่อรับโซลูชันที่ครบถ้วนและพร้อมใช้งานในสภาพแวดล้อมการผลิต.
og_title: วิธีใช้ IWarningCallback – ตรวจจับฟอนต์ที่หายไป
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: วิธีใช้ IWarningCallback – ตรวจจับฟอนต์ที่หายไปด้วย Aspose.Words
url: /th/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีใช้ IWarningCallback – ตรวจจับฟอนต์ที่หายไปด้วย Aspose.Words

การใช้ **IWarningCallback** มีความสำคัญเมื่อคุณทำงานกับ Aspose.Words และต้องการ **ตรวจจับฟอนต์ที่หายไป** ในไฟล์ DOCX ในคู่มือนี้เราจะพาคุณผ่านตัวอย่างเต็มรูปแบบที่สามารถคัดลอก‑วางได้ ซึ่งจะแสดงให้เห็นอย่างชัดเจนว่าต้องใช้ IWarningCallback อย่างไรเพื่อดักจับคำเตือนการแทนที่ฟอนต์ ทำไมจึงสำคัญ และต้องทำอย่างไรหลังจากที่คุณจับได้แล้ว

หากคุณเคยเปิดเอกสารแล้วเจอข้อความเป็นอักขระแปลก ๆ เพราะฟอนต์ที่กำหนดเองไม่ได้ติดตั้ง คุณคงรู้สึกหงุดหงิด เมื่อจบบทเรียนนี้คุณจะมีวิธีที่เชื่อถือได้ในการตรวจพบปัญหาเหล่านี้โดยอัตโนมัติ บันทึกลงล็อก หรือแม้แต่กำหนดฟอนต์สำรองโดยอัตโนมัติ

## สิ่งที่คุณจะได้เรียนรู้

- จุดประสงค์ของ **IWarningCallback** และเมื่อใดควรใช้  
- วิธีสร้างคอลเลกเตอร์คำเตือนแบบกำหนดเองที่แยกเหตุการณ์ **detect missing fonts** ออกมา  
- การเชื่อมคอลเลกเตอร์เข้ากับ **LoadOptions** เพื่อให้การโหลดเอกสารทุกครั้งถูกตรวจสอบ  
- วิธีตรวจสอบผลลัพธ์และจัดการกรณีขอบ (ฟอนต์หายหลายตัว, คำเตือนเงียบ, ฯลฯ)  

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานบน .NET Framework 4.6+ ด้วย)  
- Aspose.Words for .NET ติดตั้งผ่าน NuGet (`Install-Package Aspose.Words`)  
- ไฟล์ DOCX ที่อ้างอิงฟอนต์ที่ไม่มีในเครื่อง (เช่น `DocumentWithMissingFont.docx`)  

ไม่ต้องใช้ไลบรารีเพิ่มเติม — ทุกอย่างอยู่ใน Aspose.Words

---

## วิธีใช้ IWarningCallback เพื่อตรวจจับฟอนต์ที่หายไปใน Aspose.Words

ด้านล่างเป็น **โปรแกรมเต็มรูปแบบที่สามารถรันได้** คัดลอกไปยังโปรเจกต์คอนโซลใหม่ ปรับเส้นทางไฟล์ แล้วรัน คุณจะเห็นผลลัพธ์ในคอนโซลสำหรับทุกคำเตือนฟอนต์ที่หายไป

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

หาก `DocumentWithMissingFont.docx` อ้างอิงฟอนต์ชื่อ *“MyFancyFont”* ที่ไม่ได้ติดตั้ง คุณจะเห็นข้อความประมาณนี้:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

แต่ละบรรทัดที่ขึ้นต้นด้วย **[Missing Font]** ถูกสร้างโดยการทำงานของ **IWarningCallback** ของเรา แสดงว่าเราสามารถ **detect missing fonts** ได้สำเร็จ

---

## ขั้นตอนที่ 1: Implement the IWarningCallback Interface

ทำไมต้องสร้างคลาสกำหนดเอง? Aspose.Words จะส่ง **warnings** ด้วยเหตุผลหลายอย่าง — ปัญหาไฟล์ฟอร์แมต, ฟีเจอร์ที่เลิกใช้, และที่สำคัญที่สุดสำหรับเรา คือการแทนที่ฟอนต์ โดยการ implement `IWarningCallback` เราจะได้ hook ที่รับทุกคำเตือนเมื่อมันเกิดขึ้น การกรองด้วย `WarningType.FontSubstitution` จะทำให้เราแยกสถานการณ์ที่ฟอนต์หายไปออกมาได้อย่างชัดเจน

**เคล็ดลับ:** หากต้องการดักจับ *ทุก* คำเตือนเพื่อการวินิจฉัย เพียงลบเงื่อนไข `if` แล้วบันทึก `info.Type` ทุกค่า

---

## ขั้นตอนที่ 2: Wire the Callback into LoadOptions

`LoadOptions` คือประตูที่บอก Aspose.Words ว่าจะจัดการกับเอกสารเข้ามาอย่างไร การตั้งค่า `WarningCallback` ให้เป็นอินสแตนซ์ของคอลเลกเตอร์ของเราจะทำให้ callback ทำงานตลอดการโหลด คุณสามารถใช้วัตถุ `LoadOptions` เดียวกันสำหรับหลายเอกสารได้ ซึ่งสะดวกใน pipeline การประมวลผลแบบ batch

**คำถามที่พบบ่อย:** *ถ้าฉันโหลดเอกสารโดยไม่ระบุ LoadOptions จะเกิดอะไรขึ้น?*  
คำตอบ: Aspose.Words จะยังคงส่งคำเตือนภายในระบบอยู่ แต่หากไม่มี callback คำเตือนเหล่านั้นจะถูกละทิ้งโดยเงียบ ๆ ทำให้คุณพลาดโอกาส **detect missing fonts** ไป

---

## ขั้นตอนที่ 3: Load a Document and Capture Missing Font Warnings

คอนสตรัคเตอร์ `Document` ที่รับพาธไฟล์และ `LoadOptions` จะทำงานหนักส่วนนี้ เมื่อไฟล์ถูกพาร์ส ฟอนต์ที่หายไปใด ๆ จะเรียกเมธอด `FontWarningCollector.Warning` ของเรา ผลลัพธ์ในคอนโซลยืนยันว่าเมคานิซึมทำงาน

**กรณีขอบ:** เอกสารหนึ่งไฟล์อาจอ้างอิงฟอนต์ที่ไม่มีหลายตัว Callback จะถูกเรียกหนึ่งครั้งต่อฟอนต์ที่หายไป ทำให้คุณเห็นหลายบรรทัด — เหมาะสำหรับสร้างรายงานที่ครอบคลุม

---

## ทำไมต้องใช้ IWarningCallback แทนการตรวจสอบฟอนต์ด้วยตนเอง?

คุณอาจสแกนคุณสมบัติ `Run.Font` ของเอกสารหลังจากโหลดแล้ว แต่การทำเช่นนั้นต้องให้เอกสารโหลดสำเร็จก่อน — ซึ่งอาจล้มเหลวหากฟอนต์ไม่มีอยู่เลย ระบบคำเตือนทำงาน **ก่อน** การแทนที่ฟอนต์ใด ๆ ทำให้คุณเห็นภาพที่แท้จริงของสิ่งที่หายไป

นอกจากนี้ callback ทำงาน **เป็นส่วนหนึ่งของ pipeline การโหลด** หมายความว่าคุณสามารถยกเลิกการทำงานล่วงหน้า, แทนที่ฟอนต์แบบไดนามิก, หรือบันทึกข้อมูลวินิจฉัยโดยไม่ต้องสแกนต้นไม้เอกสารเพิ่มเติม

---

## การจัดการฟอนต์ที่หายไปหลายตัวอย่างมีประสิทธิภาพ

หากคาดว่าจะมีฟอนต์หายหลายตัว ควรรวบรวมไว้ในคอลเลกชัน:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

หลังจากโหลดเสร็จ คุณสามารถวนลูป `MissingFonts` และเช่น เขียนลงไฟล์ CSV เพื่อส่งให้ทีมออกแบบได้

---

## โบนัส: บันทึกคำเตือนลงไฟล์

การแสดงผลบนคอนโซลเหมาะสำหรับสาธิต แต่โค้ดจริงมักบันทึกลงที่จัดเก็บถาวร แทน `Console.WriteLine` ด้วยโค้ดเช่น:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

ตอนนี้คุณมี audit trail ที่สามารถตรวจสอบได้ในภายหลัง ตรงตามข้อกำหนด compliance

---

## สรุป

เราได้อธิบาย **วิธีใช้ IWarningCallback** เพื่อ **detect missing fonts** ใน Aspose.Words ตั้งแต่การสร้าง callback, การเชื่อมต่อกับ `LoadOptions` จนถึงการจัดการคำเตือนที่เกิดขึ้น วิธีนี้ให้ข้อมูลเชิงเวลาจริงเกี่ยวกับปัญหาฟอนต์ ช่วยให้คุณบันทึก, แทนที่, หรือแจ้งเตือนผู้ใช้ก่อนที่เอกสารจะถูกแสดงผล

ขั้นตอนต่อไปที่คุณอาจสนใจ:

- **Fallback fonts:** กำหนดฟอนต์เริ่มต้นโดยโปรแกรมเมื่อตรวจพบการแทนที่  
- **Batch processing:** วนลูปโฟลเดอร์เอกสารหลายไฟล์โดยใช้ `AggregatingFontCollector` เดียวกัน  
- **User feedback:** แสดงคำเตือนฟอนต์ที่หายไปใน UI แทนคอนโซล  

ลองนำไปใช้ในโปรเจกต์ของคุณ — ไม่ต้องเจอข้อความแปลก ๆ อีกต่อไป มีแต่การวินิจฉัยที่ชัดเจนและทำได้จริง Happy coding!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่อธิบายในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอน‑ต่อ‑ขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}