---
category: general
date: 2026-04-04
description: กู้ไฟล์ Word ที่เสียหายโดยใช้ Aspose.Words ใน C#. เรียนรู้วิธีแสดงโหมดการกู้คืนและจัดการข้อผิดพลาดของไฟล์อย่างมีประสิทธิภาพ.
draft: false
keywords:
- recover corrupted word file
- display recovery mode
language: th
og_description: กู้ไฟล์ Word ที่เสียหายและแสดงโหมดการกู้คืนด้วย Aspose.Words คู่มือขั้นตอนเต็มสำหรับนักพัฒนา
  C#
og_title: กู้ไฟล์ Word ที่เสียหาย – แสดงโหมดการกู้คืนใน C#
tags:
- Aspose.Words
- C#
- Document Recovery
title: กู้ไฟล์ Word ที่เสียหายและแสดงโหมดการกู้คืนใน C#
url: /th/net/programming-with-loadoptions/recover-corrupted-word-file-and-display-recovery-mode-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# กู้ไฟล์ Word ที่เสีย – คู่มือเต็มสำหรับแสดงโหมดการกู้คืนใน C#

เคยลองเปิดไฟล์ Word ที่ดูปกติใน Explorer แต่เมื่อโหลดในโค้ดกลับเกิดข้อผิดพลาดหรือไม่? นั่นคือสถานการณ์คลาสสิกของ *recover corrupted word file* ในบทเรียนนี้เราจะสาธิตวิธีกู้ไฟล์ Word ที่เสีย **และ** แสดงโหมดการกู้คืนที่เลือกโดยใช้ Aspose.Words for .NET

เราจะเดินผ่านทุกขั้นตอนที่คุณต้องการ—การติดตั้งไลบรารี, การกำหนดค่า `LoadOptions`, การจัดการกรณีขอบ, และการพิมพ์โหมดการกู้คืนไปยังคอนโซล สุดท้ายคุณจะได้โค้ดสแนปช็อตที่พร้อมใช้งานในโปรเจกต์ของคุณ

## สิ่งที่คุณจะได้เรียนรู้

- วิธีตั้งค่า Aspose.Words `LoadOptions` เพื่อควบคุมการจัดการไฟล์เสีย  
- ทำไม `RecoveryMode.Strict` จึงเป็นค่าเริ่มต้นที่ปลอดภัยที่สุดสำหรับกรณีใช้ *recover corrupted word file*  
- โค้ดที่จำเป็นเพื่อ **แสดงโหมดการกู้คืน** หลังจากโหลดไฟล์  
- จุดบกพร่องทั่วไป (เช่น ไฟล์หาย, ความเสียหายที่ไม่รองรับ) และวิธีหลีกเลี่ยง  

**ข้อกำหนดเบื้องต้น:** .NET 6+ (หรือ .NET Framework 4.6+), สำเนา Aspose.Words ที่มีลิขสิทธิ์หรือแบบประเมิน, และความคุ้นเคยพื้นฐานกับ C# ไม่มีการพึ่งพาอื่นเพิ่มเติม

---

## ขั้นตอนที่ 1: ติดตั้ง Aspose.Words for .NET

เริ่มต้นด้วยการดึงแพ็กเกจ NuGet เปิดเทอร์มินัลในโฟลเดอร์โปรเจกต์ของคุณและรัน:

```bash
dotnet add package Aspose.Words
```

> **เคล็ดลับ:** หากคุณทำงานในโปรเจกต์เก่าที่ยังใช้ `packages.config` ให้รัน `Install-Package Aspose.Words` ใน Package Manager Console แทน

แพ็กเกจนี้มาพร้อมทุกอย่างที่คุณต้องการ: คลาส `Document`, `LoadOptions`, และ enum `RecoveryMode`

## ขั้นตอนที่ 2: กำหนดค่า LoadOptions เพื่อกู้ไฟล์ Word ที่เสีย

ตอนนี้เราจะบอก Aspose.Words ว่าจะพยายามซ่อมไฟล์ที่เสียอย่างรุนแรงแค่ไหน enum `RecoveryMode` มีสามค่า:

| ค่า | พฤติกรรม |
|-------|------------|
| **Strict** | ยกเลิกเมื่อพบความเสียหายรุนแรง |
| **Relaxed** | พยายามแก้ไขปัญหาเล็กน้อย |
| **NoRecovery** | โหลดไฟล์โดยไม่พยายามกู้คืนใดๆ |

สำหรับสถานการณ์การผลิตส่วนใหญ่คุณควรเลือก **Strict**—มันจะป้องกันการโหลดเอกสารเสียโดยไม่รู้สึก ซึ่งอาจทำให้เกิดข้อผิดพลาดต่อไป

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 2: Define recovery behaviour for a potentially damaged file.
var loadOptions = new LoadOptions
{
    // Abort loading if the corruption is severe (alternatives: Relaxed, NoRecovery).
    RecoveryMode = RecoveryMode.Strict
};
```

> **ทำไมเรื่องนี้สำคัญ:** การใช้ `Strict` ทำให้คุณ *จริงๆ* รู้ว่าไฟล์ไม่สามารถกู้คืนได้ แทนที่จะต้องเดาในภายหลังเมื่อเอกสารแสดงผลผิดพลาด

## ขั้นตอนที่ 3: โหลดเอกสารด้วยตัวเลือกที่กำหนดไว้

เมื่อ `loadOptions` พร้อมแล้ว เราสามารถพยายามเปิดไฟล์ได้ หากไฟล์สมบูรณ์ทุกอย่างจะดำเนินต่ออย่างราบรื่น; หากไฟล์เสียจะเกิดข้อยกเว้น (exception) ซึ่งเราจะจับไว้ในขั้นตอนต่อไป

```csharp
// Step 3: Load the document using the configured recovery options.
string filePath = @"C:\Docs\PotentiallyCorrupt.docx";
Document document = null;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"⚠️ Failed to load document: {ex.Message}");
    // You might log the error or attempt a fallback strategy here.
}
```

> **กรณีขอบ:** หากไฟล์ไม่มีอยู่จริง `FileNotFoundException` จะถูกโยนขึ้นมา ควรตรวจสอบเส้นทางไฟล์ก่อนเรียก `new Document`

## ขั้นตอนที่ 4: ตรวจสอบการโหลดสำเร็จและ **แสดงโหมดการกู้คืน**

สมมติว่าไม่มีข้อยกเว้นเกิดขึ้น วัตถุเอกสารถูกสร้างพร้อมใช้งาน ให้เรายืนยันว่าการโหลดสำเร็จและพิมพ์โหมดการกู้คืนที่ใช้ นี่คือการตอบสนองต่อความต้องการ *display recovery mode*

```csharp
// Step 4: Confirm that the document was loaded and show the recovery mode.
if (document != null)
{
    Console.WriteLine($"✅ Document loaded successfully.");
    Console.WriteLine($"RecoveryMode = {loadOptions.RecoveryMode}");
}
else
{
    Console.WriteLine("❌ Document could not be loaded.");
}
```

ผลลัพธ์ที่แสดงบนคอนโซลโดยทั่วไปจะเป็นเช่นนี้:

```
✅ Document loaded successfully.
RecoveryMode = Strict
```

หากคุณเปลี่ยน `RecoveryMode` เป็น `Relaxed` ผลลัพธ์จะแสดงการเปลี่ยนแปลงนั้น—มีประโยชน์สำหรับการดีบักหรือกลยุทธ์การกู้คืนที่ยืดหยุ่นกว่า

## ขั้นตอนที่ 5: ทางเลือก – จัดการกับสถานการณ์ไฟล์เสียเฉพาะ

บางครั้งคุณอาจต้องการ **recover corrupted word file** แม้ความเสียหายจะเล็กน้อยโดยไม่ยกเลิกการทำงานทั้งหมด นี่คือการปรับแต่งอย่างรวดเร็ว:

```csharp
// Switch to a more forgiving mode if you need to salvage partially damaged docs.
loadOptions.RecoveryMode = RecoveryMode.Relaxed;

try
{
    document = new Document(filePath, loadOptions);
    Console.WriteLine($"Loaded with Relaxed mode. RecoveryMode = {loadOptions.RecoveryMode}");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed even with Relaxed mode: {ex.Message}");
}
```

> **เมื่อใดใช้ Relaxed:** หากคุณประมวลผลการอัปโหลดเป็นจำนวนมากและยอมรับข้อบกพร่องการจัดรูปแบบเล็กน้อย `Relaxed` สามารถช่วยประหยัดเวลาได้ เพียงจำไว้ว่าให้ตรวจสอบเอกสารสุดท้ายก่อนเผยแพร่

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมพร้อมคัดลอก‑วางที่สาธิตวิธี **recover corrupted word file** และ **display recovery mode**:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Define recovery behaviour.
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Strict // Change to Relaxed if needed.
        };

        // 2️⃣ Path to the possibly damaged document.
        string filePath = @"C:\Docs\PotentiallyCorrupt.docx";

        // 3️⃣ Attempt to load the document.
        Document document = null;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"⚠️ Error loading document: {ex.Message}");
            // Early exit if loading fails.
            return;
        }

        // 4️⃣ Verify and **display recovery mode**.
        if (document != null)
        {
            Console.WriteLine($"✅ Document loaded with RecoveryMode = {loadOptions.RecoveryMode}");
        }
        else
        {
            Console.WriteLine("❌ Document could not be loaded.");
        }

        // 5️⃣ (Optional) Do something with the document, e.g., save as PDF.
        // document.Save("Recovered.pdf");
    }
}
```

รันโปรแกรมแล้วคุณจะเห็นว่าไฟล์ผ่านการตรวจสอบแบบ Strict หรือไม่และโหมดใดที่ถูกนำไปใช้

---

## คำถามที่พบบ่อย & เคล็ดลับ

- **ไฟล์ถูกเข้ารหัสลับจะทำอย่างไร?**  
  Aspose.Words สามารถเปิดไฟล์ที่มีรหัสผ่านได้ แต่คุณต้องส่งรหัสผ่านผ่าน `LoadOptions.Password` โหมดการกู้คืนยังคงทำงานหลังจากถอดรหัส

- **ฉันสามารถบันทึกรายละเอียดความเสียหายได้หรือไม่?**  
  ตั้งค่า `loadOptions.LoadFormat = LoadFormat.Docx` และเปิดใช้งาน `Document.CompatibilityOptions` เพื่อรับการวินิจฉัยที่ละเอียดขึ้น

- **`Strict` เป็นค่าเริ่มต้นหรือไม่?**  
  ไม่—หากคุณไม่ระบุ `RecoveryMode` Aspose.Words จะใช้ค่าเริ่มต้นเป็น `Relaxed` การตั้งค่า `Strict` อย่างชัดเจนเป็นวิธีที่ปลอดภัยที่สุดสำหรับการ *recover corrupted word file* เฉพาะเมื่อคุณมั่นใจว่าไฟล์สะอาด

- **ผลกระทบต่อประสิทธิภาพ?**  
  กระบวนการกู้คืนเพิ่มค่าโอเวอร์เฮดเล็กน้อย (โดยทั่วไป < 5 ms สำหรับ DOCX ขนาด 1 MB) สำหรับงานแบตช์ขนาดใหญ่ ควรพิจารณาการทำงานแบบขนาน

## สรุป

คุณได้เรียนรู้วิธี **recover corrupted word file** ด้วย Aspose.Words, ตั้งค่า `RecoveryMode` ที่เหมาะสม, และ **display recovery mode** เพื่อยืนยันกลยุทธ์ของคุณ วิธีนี้ให้การควบคุมเต็มที่ต่อการจัดการข้อผิดพลาด ทำให้แอปพลิเคชันของคุณได้รับเอกสารที่สะอาดหรือหยุดทำงานอย่างรวดเร็วพร้อมข้อความชัดเจน

ขั้นตอนต่อไป? ลองสลับ `RecoveryMode.Strict` เป็น `Relaxed` แล้วสังเกตว่าห้องสมุดพยายามแก้ไขปัญหาเล็กน้อยอย่างไร คุณยังสามารถสำรวจการบันทึกเอกสารที่กู้คืนในรูปแบบอื่น (PDF, HTML) เพื่อยืนยันว่าข้อมูลยังคงอยู่หลังการกู้คืน

ขอให้เขียนโค้ดสนุกและจำไว้ว่า—เมื่อจัดการกับไฟล์เสีย การระบุพฤติกรรมการกู้คืนอย่างชัดเจนจะช่วยลดบั๊กที่ซ่อนอยู่ได้มาก หากมีปัญหาหรือวิธีแก้ที่ฉลาด อย่าลังเลที่จะแสดงความคิดเห็น!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}