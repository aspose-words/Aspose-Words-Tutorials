---
category: general
date: 2026-06-08
description: เปิดไฟล์ Word ที่เสียหายใน C# ด้วย Aspose.Words. เรียนรู้วิธีตั้งค่าโหมดการกู้คืนและกู้คืนเอกสารที่เสียหายอย่างมีประสิทธิภาพ.
draft: false
keywords:
- open corrupted word file
- set recovery mode
- recover corrupted document
- Aspose.Words recovery
- handling damaged docx
language: th
og_description: เปิดไฟล์ Word ที่เสียหายใน C# ด้วย Aspose.Words คู่มือนี้แสดงวิธีตั้งค่าโหมดการกู้คืนและกู้คืนเอกสารที่เสียหายอย่างปลอดภัย
og_title: เปิดไฟล์ Word ที่เสียหายใน C# – คู่มือขั้นตอนต่อขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  headline: Open Corrupted Word File in C# – Complete Guide
  type: TechArticle
- description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  name: Open Corrupted Word File in C# – Complete Guide
  steps:
  - name: '**Create `LoadOptions`** – decide how strict the loader should be.'
    text: '**Create `LoadOptions`** – decide how strict the loader should be.'
  - name: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
    text: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
  - name: '**Load the document** – give the path and the options you just built.'
    text: '**Load the document** – give the path and the options you just built.'
  - name: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
    text: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
  type: HowTo
tags:
- C#
- Aspose.Words
- Document Recovery
title: เปิดไฟล์ Word ที่เสียหายใน C# – คู่มือฉบับสมบูรณ์
url: /th/net/programming-with-loadoptions/open-corrupted-word-file-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปิดไฟล์ Word ที่เสียหายใน C# – คู่มือฉบับสมบูรณ์

เคยต้องการ **เปิดไฟล์ Word ที่เสียหาย** ในโครงการ .NET และสงสัยว่าไฟล์นั้นเกินกว่าจะซ่อมได้หรือไม่? คุณไม่ได้เป็นคนแรก—การเสียหายของเอกสารเกิดบ่อยกว่าที่คุณคิด, โดยเฉพาะเมื่อไฟล์เดินทางผ่านเครือข่ายที่ไม่เสถียรหรือถูกแก้ไขโดยเวอร์ชัน Office เก่า.  

ข่าวดี? ด้วย Aspose.Words คุณสามารถ **set recovery mode** เพื่อบอกไลบรารีว่าต้องทำงานอย่างไร, และคุณยังสามารถ **recover corrupted document** เนื้อหาโดยไม่ต้องเขียนพาร์เซอร์แบบกำหนดเองได้อีกด้วย ในบทแนะนำนี้เราจะเดินผ่านทุกขั้นตอน, ตั้งแต่การกำหนดค่าตัวเลือกจนถึงการตรวจสอบว่าไฟล์เปิดสำเร็จหรือไม่.

> **สิ่งที่คุณจะได้เรียนรู้**  
> • ตัวอย่างโค้ด C# ที่ทำงานได้ซึ่งเปิดไฟล์ .docx ใดก็ได้, แม้จะเป็นไฟล์ที่เสียหาย  
> • ความเข้าใจเกี่ยวกับค่า `RecoveryMode` ทั้งสามค่าและเมื่อควรใช้แต่ละค่า  
> • เคล็ดลับในการจัดการข้อยกเว้น, ทดสอบผลลัพธ์, และบันทึกสำเนาที่สะอาดเป็นตัวเลือก

## วิธีเปิดไฟล์ Word ที่เสียหายด้วย Aspose.Words

ด้านล่างเป็นภาพระดับสูงของกระบวนการ.  
![แผนภาพแสดงกระบวนการเปิดไฟล์ Word ที่เสียหาย](/images/open-corrupted-word-file-flow.png){: .center alt="แผนภาพแสดงกระบวนการเปิดไฟล์ Word ที่เสียหาย"}

1. **สร้าง `LoadOptions`** – กำหนดความเข้มงวดของตัวโหลด.  
2. **เลือก `RecoveryMode`** – *Passthrough* สำหรับการโหลดแบบดิบ, *Recover* สำหรับการแก้อัตโนมัติ, หรือ *Throw* เพื่อดักจับปัญหาแต่เนิ่นๆ.  
3. **โหลดเอกสาร** – ระบุพาธและตัวเลือกที่คุณสร้างไว้.  
4. **ตรวจสอบ** – ตรวจสอบว่าโครงสร้างเอกสารไม่ว่างเปล่า, และอาจบันทึกสำเนาที่ซ่อมแล้ว.

มาดูรายละเอียดแต่ละส่วนกัน

## ทำความเข้าใจโหมด Recovery

Aspose.Words กำหนดพฤติกรรมที่แตกต่างกันสามแบบ:

| โหมด | ทำอะไร | เมื่อใดควรใช้ |
|------|--------|----------------|
| `RecoveryMode.Recover` | พยายามแก้ไขปัญหาโครงสร้าง, ส่วนที่หายไป, หรือ XML ที่ผิดรูปแบบ. นี่เป็น **default** และทำงานได้กับการเสียหายเล็กน้อยส่วนใหญ่. | คุณต้องการการซ่อมแซมแบบพยายามเต็มที่โดยไม่ต้องแทรกแซงด้วยตนเอง. |
| `RecoveryMode.Passthrough` | โหลดไฟล์ **อย่างตรงตามที่มี** แม้ว่าจะมีส่วนที่เสียหาย. ไม่ได้ทำการแก้อัตโนมัติ. | คุณต้องการตรวจสอบเนื้อหาดิบ, หรือคุณวางแผนจะใช้ตรรกะการกู้คืนแบบกำหนดเองในภายหลัง. |
| `RecoveryMode.Throw` | ทันทีโยนข้อยกเว้นหากพบปัญหาใดๆ. | คุณต้องการวิธีการล้มเหลวเร็วเพื่อปฏิเสธไฟล์ที่เสียหายโดยตรง. |

การเลือกโหมดที่ถูกต้องคือหัวใจของการ **set recovery mode** อย่างถูกต้อง. นักพัฒนาส่วนใหญ่เริ่มด้วย `Recover`, แต่หากคุณกำลังดีบักไฟล์ที่ยากต่อการแก้, `Passthrough` สามารถให้คุณมองเห็นว่ามีอะไรผิดพลาด.

## ขั้นตอน‑ต่อ‑ขั้นตอน: ตั้งค่า Recovery Mode

ด้านล่างเป็นบล็อกโค้ดแรกที่คุณจะวางในแอปคอนโซลใหม่หรือโครงการ C# ใดๆ ที่อ้างอิง `Aspose.Words` อยู่แล้ว.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 1: Create LoadOptions and choose a recovery behavior
LoadOptions loadOptions = new LoadOptions
{
    // Choose the desired recovery behavior:
    //   RecoveryMode.Recover      – attempt to fix the file (default)
    //   RecoveryMode.Passthrough – load the file exactly as it is
    //   RecoveryMode.Throw       – throw an exception if the file is damaged
    RecoveryMode = RecoveryMode.Passthrough   // <-- we are explicitly setting it
};
```

**ทำไมเรื่องนี้ถึงสำคัญ:** ด้วยการกำหนดค่า `RecoveryMode.Passthrough` อย่างชัดเจน, เรากำลังบอก Aspose.Words ให้ **set recovery mode** เป็นค่าที่ไม่ใช่ค่าเริ่มต้น. สิ่งนี้ขจัดการคาดเดาและทำให้เจตนาชัดเจนสำหรับผู้ดูแลในอนาคต.

> **เคล็ดลับ:** หากคุณต้องการสลับกลับไปยังเส้นทางการซ่อมอัตโนมัติ, เพียงเปลี่ยน enum เป็น `RecoveryMode.Recover` แล้วรันใหม่—ไม่ต้องเปลี่ยนโค้ดอื่นใด

## โหลดเอกสารอย่างปลอดภัย

เมื่อกำหนดตัวเลือกเรียบร้อยแล้ว, ขั้นตอนต่อไปคือการ **เปิดไฟล์ Word ที่เสียหาย** จริงๆ. ตัวอย่างโค้ดต่อไปนี้แสดงกระบวนการโหลดและรวมการตรวจสอบความสมเหตุสมผลเล็กน้อย.

```csharp
// Step 2: Load the possibly‑corrupted document using the configured options
try
{
    // Replace the path with the location of your damaged DOCX
    Document doc = new Document(@"C:\Temp\Corrupted.docx", loadOptions);

    // Quick validation – make sure the document contains at least one section
    if (doc.Sections.Count == 0)
    {
        Console.WriteLine("The document appears empty after loading. It may be severely corrupted.");
    }
    else
    {
        Console.WriteLine($"Successfully opened the file. Sections found: {doc.Sections.Count}");
    }
}
catch (Exception ex)
{
    // If you used RecoveryMode.Throw, you'll land here for any problem.
    Console.WriteLine($"Failed to open the file: {ex.Message}");
}
```

**คำอธิบาย:**  
* บล็อก `try/catch` ปกป้องเราจากโหมด `Throw`, แต่ยังเป็นเครือข่ายความปลอดภัยสำหรับข้อผิดพลาด I/O ที่ไม่คาดคิด.  
* หลังจากโหลด, เราตรวจสอบ `doc.Sections.Count`. จำนวนศูนย์เป็นสัญญาณชัดว่ไฟล์ไม่สามารถกู้คืนเนื้อหาที่มีความหมายใดๆ—เหมาะสำหรับยืนยันว่า **recover corrupted document** สำเร็จหรือไม่.

## การจัดการข้อยกเว้นและการตรวจสอบการกู้คืน

แม้จะใช้ `Passthrough`, ไลบรารีอาจยังโยนข้อยกเว้นหากแพ็กเกจ ZIP พื้นฐานไม่สามารถอ่านได้. นี่คือวิธีแยกแยะระหว่างปัญหา *recoverable* กับ *fatal*:

```csharp
catch (CorruptedFileException cfe)
{
    // This exception means the file's internal structure is broken.
    Console.WriteLine("CorruptedFileException caught – the file cannot be read at all.");
}
catch (Exception ex)
{
    // Any other exception (e.g., FileNotFound, UnauthorizedAccess)
    Console.WriteLine($"General error: {ex.GetType().Name} – {ex.Message}");
}
```

หากคุณเห็น `CorruptedFileException`, คุณอาจต้องกลับไปใช้กลยุทธ์การกู้คืนอื่น, เช่น:

* ลองใช้ `RecoveryMode.Recover` แทน `Passthrough`.  
* ใช้เครื่องมือซ่อม ZIP ของบุคคลที่สามก่อนส่งไฟล์ให้ Aspose.Words.  
* แจ้งผู้ใช้ให้อัปโหลดไฟล์ใหม่.

## โบนัส: การบันทึกเอกสารที่ซ่อมแล้ว

เมื่อคุณได้ **recover corrupted document** เนื้อหาแล้ว, คุณมักต้องการบันทึกเวอร์ชันที่สะอาด. โค้ดต่อไปนี้จะเขียนไฟล์ที่ซ่อมแล้วไปยังตำแหน่งใหม่:

```csharp
// Assuming 'doc' was loaded successfully
string outputPath = @"C:\Temp\Repaired.docx";

doc.Save(outputPath, SaveFormat.Docx);
Console.WriteLine($"Repaired document saved to: {outputPath}");
```

การบันทึกยังทำหน้าที่เป็นขั้นตอนการตรวจสอบโดยอ้อม—หาก `doc.Save` โยนข้อยกเว้น, แสดงว่ามีบางอย่างยังไม่ถูกต้องในโครงสร้างภายในของโหนด.

## เคล็ดลับสำหรับสถานการณ์การกู้คืนเอกสารที่เสียหาย

| สถานการณ์ | การกระทำที่แนะนำ |
|-----------|--------------------|
| ข้อผิดพลาด XML เล็กน้อย (เช่น แท็กปิดหายไป) | ใช้ `RecoveryMode.Recover` ต่อ; Aspose.Words จะทำการแก้อัตโนมัติ. |
| ไฟล์ ZIP เสียหายอย่างสมบูรณ์ | ใช้การซ่อม ZIP ภายนอก, แล้วโหลดด้วย `Passthrough`. |
| โหมดผสม (บางส่วนปกติ, บางส่วนเสียหาย) | โหลดด้วย `Passthrough`, ตรวจสอบโหนดที่มีปัญหา, แล้วลบหรือแทนที่ด้วยตนเอง. |
| การเสียหายบ่อยจากแหล่งที่มาหนึ่ง | ทำการตรวจสอบล่วงหน้าอัตโนมัติที่รัน `RecoveryMode.Recover` และบันทึก `CorruptedFileException` ใดๆ |

จำไว้ว่า, **set recovery mode** ไม่ใช่ไม้วิเศษ—การเข้าใจลักษณะของการเสียหายช่วยให้คุณเลือกกลยุทธ์ที่เหมาะสม.

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน, นี่คือแอปคอนโซลที่สมบูรณ์ซึ่งคุณสามารถวางลงใน `Program.cs` และรันได้ทันที (หลังจากเพิ่มแพคเกจ NuGet ของ Aspose.Words).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace OpenCorruptedWordFileDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure load options – we explicitly set the recovery mode.
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Passthrough // change to Recover if you prefer auto‑fix
            };

            // 2️⃣ Attempt to load the possibly damaged DOCX.
            string sourcePath = @"C:\Temp\Corrupted.docx";
            Document doc = null;

            try
            {
                doc = new Document(sourcePath, loadOptions);
                Console.WriteLine($"File loaded. Sections: {doc.Sections.Count}");
            }
            catch (CorruptedFileException)
            {
                Console.WriteLine("The file is too damaged to be opened even in Passthrough mode.");
                return;
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.Message}");
                return;
            }

            // 3️⃣ Simple verification – ensure we have at least one paragraph.
            if (doc.GetChildNodes(NodeType.Paragraph, true).Count == 0)
            {
                Console.WriteLine("No paragraphs were recovered – the document may be empty.");
            }
            else
            {
                Console.WriteLine("Paragraphs recovered – the document appears usable.");
            }

            // 4️⃣ Optionally save a clean copy.
            string cleanPath = @"C:\Temp\Repaired.docx";
            doc.Save(cleanPath, SaveFormat.Docx);
            Console.WriteLine($"Clean copy saved to: {cleanPath}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง (เมื่อไฟล์สามารถเปิดได้):**



## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบอื่นในโครงการของคุณ.

- [วิธีกู้คืน docx – set recovery mode & เปิดไฟล์ Word ที่เสียหาย](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [กู้คืนไฟล์ Word ที่เสียหาย – คู่มือฉบับสมบูรณ์เพื่อเปิด DOCX ที่เสียหาย & รับหน้า](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)
- [กู้คืนเอกสาร Word ด้วย Aspose.Words ใน C#](/words/english/net/programming-with-loadoptions/recover-word-document-with-aspose-words-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}