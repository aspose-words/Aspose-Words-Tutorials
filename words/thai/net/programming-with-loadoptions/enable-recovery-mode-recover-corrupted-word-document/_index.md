---
category: general
date: 2026-07-06
description: เปิดใช้งานโหมดการกู้คืนเพื่อเปิดไฟล์ docx ที่เสียหายด้วย Aspose.Words.
  เรียนรู้วิธีกู้คืนเอกสาร Word ที่เสียหายอย่างรวดเร็ว.
draft: false
keywords:
- enable recovery mode
- recover corrupted word document
- recover damaged docx file
- how to open corrupted docx
language: th
og_description: การเปิดใช้งานโหมดการกู้คืนทำให้คุณสามารถเปิดไฟล์ docx ที่เสียหายและพยายามกู้คืนเอกสาร
  Word ที่เสียได้
og_title: เปิดใช้งานโหมดกู้คืน – กู้คืนเอกสาร Word ที่เสียหาย
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Enable recovery mode to open a corrupted docx file with Aspose.Words.
    Learn how to recover corrupted Word document quickly.
  headline: Enable recovery mode – Recover corrupted Word document
  type: TechArticle
- questions:
  - answer: No. It only affects how the library reads the file in memory. The source
      remains untouched unless you explicitly call `Save`.
    question: Does enabling recovery mode modify the original file?
  - answer: Usually yes, as long as the underlying ZIP entry isn’t broken. If an image
      stream is missing, Aspose.Words will skip it and continue.
    question: Can I recover images that were embedded in the corrupted docx?
  - answer: Slightly, because the parser performs additional checks. The overhead
      is negligible for typical documents (<10 MB).
    question: Is recovery mode slower?
  - answer: '`RecoveryMode.Auto` (default) tries to recover only when an error occurs.
      `RecoveryMode.None` disables any recovery attempts. `RecoveryMode.Recover` forces
      the attempt every time. ## Full Working Example Below is a self‑contained console
      app you can copy‑paste into a new .NET project. It demonstrate'
    question: What other recovery options exist?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Document Recovery
- Word
title: เปิดใช้งานโหมดการกู้คืน – กู้คืนเอกสาร Word ที่เสียหาย
url: /th/net/programming-with-loadoptions/enable-recovery-mode-recover-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปิดโหมดการกู้คืน – กู้ไฟล์ Word ที่เสียหาย

เคยลองเปิด **docx ที่เสียหาย** แล้วเจอกับกล่องโต้ตอบแสดงข้อผิดพลาดที่มองกลับมาหรือไม่? มันทำให้หงุดหงิด โดยเฉพาะเมื่อไฟล์นั้นมีงานหลายสัปดาห์อยู่ในนั้น โชคดีที่ Aspose.Words มีวิธีให้คุณ *เปิดโหมดการกู้คืน* เพื่อพยายามกู้เนื้อหาโดยไม่ต้องคัดลอก‑วางด้วยตนเอง

ในคู่มือนี้ เราจะพาคุณผ่านขั้นตอนที่แน่นอนเพื่อ **เปิดโหมดการกู้คืน**, โหลดไฟล์ที่เสียและบันทึกสำเนาที่ใช้งานได้ เมื่อจบคุณจะรู้วิธี *กู้ไฟล์ Word ที่เสียหาย* อย่างโปรแกรมเมติกและแม้กระทั่งจัดการกับสถานการณ์ *กู้ไฟล์ docx ที่เสีย* อย่างราบรื่น

## สิ่งที่คุณต้องมี

- .NET 6 (หรือ .NET runtime ล่าสุดใดก็ได้) – ไลบรารีทำงานบน .NET Framework ด้วย
- Visual Studio 2022 หรือ VS Code – IDE ที่คุณชื่นชอบก็ใช้ได้
- **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`) – นี่คือการพึ่งพาภายนอกเพียงอย่างเดียว
- ไฟล์ `docx` ที่เสียตัวอย่าง (เราจะเรียกว่า `corrupted.docx`)

แค่นั้นเอง ไม่ต้องเครื่องมือเพิ่มเติม ไม่ต้องแก้ไข XML ด้วยตนเอง เพียงไม่กี่บรรทัดของ C#

![เปิดโหมดการกู้คืนใน Aspose.Words](image-url-placeholder.png)

*ข้อความอธิบายภาพ: เปิดโหมดการกู้คืนใน Aspose.Words*

## ขั้นตอนที่ 1: ติดตั้ง Aspose.Words และตั้งค่าโปรเจกต์

เปิดเทอร์มินัลของคุณ (หรือ Package Manager Console) แล้วรัน:

```bash
dotnet add package Aspose.Words
```

หรืออีกทางหนึ่ง ใน Visual Studio เปิด **Tools → NuGet Package Manager → Manage NuGet Packages** แล้วค้นหา *Aspose.Words* หลังจากติดตั้งแล้ว ให้เพิ่ม namespace ที่ส่วนบนของไฟล์ของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **เคล็ดลับ:** คอยอัปเดตแพคเกจของคุณให้เป็นเวอร์ชันล่าสุด การทำงานของโหมดการกู้คืนจะดีขึ้นในแต่ละรุ่น

## ขั้นตอนที่ 2: เปิดโหมดการกู้คืนโดยใช้ `LoadOptions`

หัวใจของวิธีแก้คือคลาส `LoadOptions` โดยการตั้งค่า property `RecoveryMode` ให้เป็น `RecoveryMode.Recover` คุณบอก Aspose.Words ให้ *เปิดโหมดการกู้คืน* ขณะทำการพาร์สเอกสาร

```csharp
// Step 2: Create LoadOptions and enable recovery mode
LoadOptions loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover   // <-- this line turns on recovery
};
```

ทำไมเรื่องนี้ถึงสำคัญ? หากไม่มีโหมดการกู้คืน Aspose.Words จะหยุดทำงานเมื่อเจอสัญญาณแรกของความเสียหาย แต่เมื่อเปิดใช้งาน ไลบรารีจะพยายามข้ามส่วนที่เสียและยังคงสร้างอ็อบเจกต์ `Document` ที่ใช้งานได้

## ขั้นตอนที่ 3: โหลดไฟล์ที่อาจเสีย

ตอนนี้เราจะทำการโหลดไฟล์จริง หากเอกสารอยู่ในสภาพที่ซ่อมไม่ได้ Aspose.Words ยังจะคืนค่าอ็อบเจกต์ `Document` แต่บางองค์ประกอบอาจหายไป

```csharp
// Step 3: Load the potentially corrupted document using the recovery options
Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
```

สังเกตว่าพาธเป็นสตริงแบบเต็ม; ปรับให้ตรงกับตำแหน่งที่ไฟล์ทดสอบของคุณอยู่ ตัวสร้าง `Document` จะอ่านไฟล์ **โดยเปิดโหมดการกู้คืน** ซึ่งให้โอกาสคุณ *กู้เนื้อหา Word ที่เสียหาย*

## ขั้นตอนที่ 4: ตรวจสอบสิ่งที่กู้ได้ (ไม่บังคับแต่เป็นประโยชน์)

เป็นการปฏิบัติที่ดีที่จะตรวจสอบเอกสารที่โหลดก่อนที่คุณจะตัดสินใจเขียนทับอะไร ๆ สำหรับการตรวจสอบอย่างรวดเร็ว คุณสามารถพิมพ์ย่อหน้าตัวแรกไม่กี่บรรทัดลงคอนโซล:

```csharp
// Optional: Print first 3 paragraphs to verify recovery
for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
{
    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
}
```

หากคุณเห็นข้อความเป็นอักขระผสมหรือสตริงว่างจำนวนมาก ไฟล์อาจ **เสียหายเกินไป** อย่างไรก็ตาม คุณยังคงมีอ็อบเจกต์ `Document` ที่สามารถจัดการได้—เช่น เพิ่มหัวเรื่อง, แทนที่รูปภาพที่หายไป ฯลฯ

## ขั้นตอนที่ 5: บันทึกเอกสารที่กู้คืน

สมมติว่าการตรวจสอบความสมเหตุสมผลดูโอเค ให้บันทึกเวอร์ชันที่กู้คืนลงไฟล์ใหม่ ขั้นตอนนี้ทำให้ *กู้ไฟล์ docx ที่เสีย* อย่างมีประสิทธิภาพและให้คุณได้สำเนาที่สะอาดซึ่งสามารถเปิดใน Word ได้

```csharp
// Step 5: Save the recovered document
string outputPath = @"C:\Temp\recovered.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Recovered document saved to: {outputPath}");
```

หากไฟล์ต้นฉบับเป็น `.doc` หรือรูปแบบอื่น คุณสามารถเปลี่ยน `SaveFormat` ให้เหมาะสม (เช่น `SaveFormat.Pdf` สำหรับส่งออกเป็น PDF)

## ขั้นตอนที่ 6: จัดการข้อยกเว้นและกรณีขอบ

แม้จะเปิดโหมดการกู้คืน บางเหตุการณ์ร้ายแรงก็ยังไม่สามารถกู้คืนได้ (เช่น โครงสร้าง zip ที่ถูกตัดขาดอย่างสมบูรณ์) ให้ห่อการโหลดด้วยบล็อก try‑catch เพื่อแสดงปัญหาเหล่านั้น:

```csharp
try
{
    Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
    // proceed with saving...
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to recover the document: {ex.Message}");
    // You might log the stack trace or notify the user.
}
```

คำถามที่พบบ่อยคือ **“วิธีเปิด docx ที่เสีย”** เมื่อไฟล์ถูกป้องกันด้วยรหัสผ่าน โหมดการกู้คืน **ไม่** ข้ามการเข้ารหัส; คุณยังต้องใช้รหัสผ่าน ในกรณีนั้น ให้ตั้งค่า `LoadOptions.Password` ก่อนทำการโหลด

## คำถามที่พบบ่อย (FAQ)

**Q: การเปิดโหมดการกู้คืนทำให้ไฟล์ต้นฉบับเปลี่ยนแปลงหรือไม่?**  
A: ไม่ใช่ มันส่งผลต่อวิธีที่ไลบรารีอ่านไฟล์ในหน่วยความจำเท่านั้น แหล่งไฟล์จะไม่ถูกแก้ไข เว้นแต่คุณจะเรียก `Save` อย่างชัดเจน

**Q: ฉันสามารถกู้รูปภาพที่ฝังอยู่ใน docx ที่เสียได้หรือไม่?**  
A: ส่วนใหญ่ทำได้ ตราบใดที่รายการ ZIP พื้นฐานไม่ได้เสีย หากสตรีมรูปภาพหายไป Aspose.Words จะข้ามและดำเนินการต่อ

**Q: โหมดการกู้คืนทำให้ช้าลงหรือไม่?**  
A: ค่อนข้างช้าเล็กน้อย เนื่องจากตัวพาร์สทำการตรวจสอบเพิ่มเติม ภาระเพิ่มขึ้นนั้นไม่มีนัยสำคัญสำหรับเอกสารทั่วไป (<10 MB)

**Q: มีตัวเลือกการกู้คืนอื่น ๆ อีกบ้าง?**  
A: `RecoveryMode.Auto` (ค่าเริ่มต้น) จะพยายามกู้คืนเมื่อเกิดข้อผิดพลาดเท่านั้น `RecoveryMode.None` ปิดการพยายามกู้คืนทั้งหมด `RecoveryMode.Recover` บังคับให้พยายามกู้คืนทุกครั้ง

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นแอปคอนโซลที่ทำงานอิสระซึ่งคุณสามารถคัดลอก‑วางลงในโปรเจกต์ .NET ใหม่ได้ มันแสดงกระบวนการทั้งหมด—ตั้งแต่การติดตั้งแพคเกจจนถึงการบันทึกไฟล์ที่กู้คืน

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace RecoverCorruptedDocx
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the corrupted document
            string inputPath = @"C:\Temp\corrupted.docx";
            // Where the recovered file will be written
            string outputPath = @"C:\Temp\recovered.docx";

            // Step 1: Create LoadOptions and enable recovery mode
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Recover
            };

            try
            {
                // Step 2: Load the document with recovery enabled
                Document doc = new Document(inputPath, loadOptions);

                // Optional sanity check – print first three paragraphs
                Console.WriteLine("=== First three paragraphs after recovery ===");
                for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
                {
                    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
                }

                // Step 3: Save the recovered document
                doc.Save(outputPath, SaveFormat.Docx);
                Console.WriteLine($"\nRecovered document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to open or recover the document: {ex.Message}");
            }
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง (สมมติว่าการกู้คืนสำเร็จ):**

```
=== First three paragraphs after recovery ===
Paragraph 1: Project Overview
Paragraph 2: This document outlines...
Paragraph 3: ...

Recovered document saved to: C:\Temp\recovered.docx
```

หากไฟล์อยู่ในสภาพที่ช่วยไม่ได้ คุณจะเห็นข้อความข้อผิดพลาดแทนการพิมพ์ย่อหน้า

## สรุป

เราได้แสดงวิธี **เปิดโหมดการกู้คืน** ใน Aspose.Words, โหลด `docx` ที่เสีย, และ **กู้ข้อมูล Word ที่เสียหาย** ไปยังไฟล์ใหม่แบบสะอาด รูปแบบเดียวกันนี้ทำให้คุณ *กู้ไฟล์ docx ที่เสีย* ในงานแบบแบตช์, การแนบอีเมลอัตโนมัติ, หรือ

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการนำไปใช้แบบอื่นในโครงการของคุณ

- [วิธีกู้คืน docx – ตั้งค่าโหมดการกู้คืน & เปิดไฟล์ Word ที่เสีย]( /words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/ )
- [วิธีกู้คืน docx ด้วย Aspose.Words – ทีละขั้นตอน](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [กู้ไฟล์ Word ที่เสีย – คู่มือฉบับสมบูรณ์เพื่อเปิด DOCX ที่เสียและรับหน้า](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}