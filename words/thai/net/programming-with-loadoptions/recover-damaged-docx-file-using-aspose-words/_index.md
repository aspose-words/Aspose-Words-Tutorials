---
category: general
date: 2026-02-15
description: กู้คืนไฟล์ DOCX ที่เสียหายอย่างรวดเร็วด้วย Aspose.Words. เรียนรู้วิธีซ่อมไฟล์
  DOCX ที่เสียและเปิดไฟล์ DOCX ที่เสียใน C# ด้วย LoadOptions และ RecoveryMode.
draft: false
keywords:
- recover damaged docx file
- repair broken docx
- open corrupt docx
- Aspose.Words recovery
- C# document loading
language: th
og_description: กู้คืนไฟล์ DOCX ที่เสียหายแบบทีละขั้นตอน คู่มือนี้แสดงวิธีซ่อมไฟล์
  DOCX ที่เสียและเปิดไฟล์ DOCX ที่เสียหายด้วย Aspose.Words ใน C#
og_title: กู้ไฟล์ DOCX ที่เสียหายด้วย Aspose.Words – คู่มือเต็ม
tags:
- Aspose.Words
- C#
- Document Processing
title: กู้ไฟล์ DOCX ที่เสียหายโดยใช้ Aspose.Words
url: /th/net/programming-with-loadoptions/recover-damaged-docx-file-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# กู้ไฟล์ DOCX ที่เสียหายด้วย Aspose.Words

เคยพยายาม **กู้ไฟล์ DOCX ที่เสียหาย** แล้วเจออุปสรรคบ้างไหม? บางทีไฟล์อาจถูกส่งผ่านเครือข่ายที่ไม่เสถียร หรือฮาร์ดไดรฟ์ขัดข้องทำให้ไฟล์ถูกเขียนครึ่งหนึ่ง ในช่วงเวลานั้นคุณอาจสงสัย: *ฉันยังสามารถเปิดเอกสารนั้นได้โดยไม่สูญเสียทุกอย่างหรือไม่?* ข่าวดีคือใช่—Aspose.Words มีวิธีในตัวเพื่อ **repair broken DOCX** files และแม้กระทั่ง **open corrupt DOCX** streams ด้วยโค้ดเพียงเล็กน้อย.

ในบทแนะนำนี้ เราจะเดินผ่านตัวอย่างที่สมบูรณ์พร้อมรันที่แสดงวิธีการกำหนดค่า `LoadOptions` ตั้งค่า `RecoveryMode` เป็น lenient แล้วอ่านจำนวนหน้าของไฟล์ Word ที่อาจเสียหายอย่างปลอดภัย เมื่อจบคุณจะได้โค้ดสั้นที่สามารถนำไปใช้ในโปรเจกต์ .NET ใดก็ได้

> **TL;DR:** ใช้ `LoadOptions.RecoveryMode = RecoveryMode.Lenient` เพื่อ **recover damaged DOCX file** โดยอัตโนมัติ.

---

## สิ่งที่คุณต้องการ

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้บนเครื่องของคุณ:

| Prerequisite | Why it matters |
|--------------|----------------|
| .NET 6.0 or later (or .NET Framework 4.6+) | Aspose.Words รองรับทั้งสอง; เวอร์ชันรันไทม์ที่ใหม่กว่าจะให้ประสิทธิภาพที่ดีกว่า. |
| Visual Studio 2022 (or any C# editor) | มีประโยชน์สำหรับการดีบักอย่างรวดเร็ว แต่ไม่จำเป็น. |
| Aspose.Words for .NET NuGet package | ไลบรารีที่ทำงานหนัก. |
| A sample DOCX that is known to be corrupted (optional) | เพื่อดูการกู้คืนทำงานจริง. |

You can install the library with a single command:

```bash
dotnet add package Aspose.Words
```

เท่านี้—ไม่มี DLL เพิ่มเติม, ไม่มี COM interop, เพียงอ้างอิง NuGet ที่สะอาด.

---

## ขั้นตอนที่ 1: ติดตั้ง Aspose.Words และตั้งค่าโปรเจกต์ของคุณ

แรก, สร้างโปรเจกต์คอนโซล (หรือเปิดโปรเจกต์ที่มีอยู่). หากคุณเริ่มจากศูนย์:

```bash
dotnet new console -n DocxRecoveryDemo
cd DocxRecoveryDemo
dotnet add package Aspose.Words
```

ตอนนี้เปิด `Program.cs`. คุณจะเห็นเมธอด `Main` เริ่มต้น—นี่คือที่ที่เราจะใส่ตรรกะการกู้คืน.

> **เคล็ดลับ:** รักษาโฟลเดอร์โปรเจกต์ให้เป็นระเบียบ; ใส่ไฟล์ DOCX ทดสอบใด ๆ ลงในโฟลเดอร์ย่อยเช่น `Samples/` เพื่อให้เส้นทางคงที่ในทุกเครื่อง.

---

## ขั้นตอนที่ 2: กำหนดค่า LoadOptions เพื่อ **Recover Damaged DOCX File**

ความมหัศจรรย์อยู่ใน `LoadOptions`. โดยค่าเริ่มต้น Aspose.Words จะโยนข้อยกเว้นเมื่อพบความเสียหาย. การเปลี่ยน `RecoveryMode` เป็น **Lenient** จะบอกไลบรารีให้ *พยายาม* แก้ไขปัญหาโดยเงียบ.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 2: Prepare LoadOptions for lenient recovery
LoadOptions loadOptions = new LoadOptions
{
    // Lenient – attempt to repair and continue.
    // Use Strict if you want an exception on any problem.
    RecoveryMode = RecoveryMode.Lenient
};
```

ทำไมต้องเลือก **Lenient**? ลองนึกว่าคุณมีชุดของเรซูเม่ที่ผู้ใช้อัปโหลด—บางไฟล์อาจมีความเสียหายเล็กน้อย. คุณไม่ต้องการให้ชุดทั้งหมดล้มเหลวเพราะไฟล์เดียวที่เสีย. โหมด Lenient ให้การอ่านแบบพยายามเต็มที่ ซึ่งเหมาะอย่างยิ่งสำหรับสถานการณ์ **repair broken docx**.

---

## ขั้นตอนที่ 3: **Open Corrupt DOCX** ด้วยตัวเลือกที่กำหนด

ตอนนี้เราจะโหลดไฟล์จริง ๆ. คอนสตรัคเตอร์ `Document` รับพาธและ `LoadOptions` ที่เราสร้างไว้.

```csharp
// Step 3: Load the (potentially) corrupted document
string filePath = Path.Combine("Samples", "maybeCorrupt.docx");
Document doc = new Document(filePath, loadOptions);
```

หากไฟล์อ่านไม่ได้จริง ๆ, Aspose.Words ยังจะคืนอ็อบเจกต์ `Document` แม้ว่าจะมีส่วนที่หายไปที่ไม่สามารถสร้างใหม่ได้. คุณสามารถตรวจสอบคุณสมบัติ `IsEncrypted` หรือ `HasDigitalSignature` ต่อมาได้หากต้องการการตรวจสอบเพิ่มเติม.

---

## ขั้นตอนที่ 4: ทำงานกับเอกสารที่กู้คืน (ตัวอย่าง: จำนวนหน้า)

การตรวจสอบอย่างรวดเร็วคือการขอจำนวนหน้าจากไลบรารี. หากเอกสารโหลดได้ จำนวนหน้าจะเป็นตัวบ่งชี้ที่เชื่อถือได้ว่าการกู้คืนสำเร็จ.

```csharp
// Step 4: Verify the load by getting the page count
int pageCount = doc.GetPageCount();
Console.WriteLine($"Document loaded successfully. Page count: {pageCount}");
```

การรันโปรแกรมควรพิมพ์ผลลัพธ์ประมาณ:

```
Document loaded successfully. Page count: 12
```

แม้ว่าไฟล์ต้นฉบับจะขาดรูปภาพบางส่วนหรือมีส่วนท้ายที่เสีย, เนื้อหาข้อความและส่วนใหญ่ของข้อมูลการจัดรูปแบบยังคงอยู่.

![ตัวอย่างการกู้ไฟล์ DOCX ที่เสียหาย](recover-damaged-docx.png)

*ข้อความแทนภาพ:* **Recover damaged DOCX file example** – แสดงผลลัพธ์คอนโซลหลังจากโหลดไฟล์ที่เสียหาย.

---

## กรณีขอบและเคล็ดลับปฏิบัติ

### 1. เมื่อ Lenient ไม่พอ
หาก `RecoveryMode.Lenient` ยังโยนข้อยกเว้น (เช่น ไฟล์ถูกตัดจนซ่อมไม่ได้), คุณสามารถย้อนกลับไปใช้วิธี **stream‑based**:

```csharp
using (FileStream fs = new FileStream(filePath, FileMode.Open, FileAccess.Read))
{
    Document fallbackDoc = new Document(fs, loadOptions);
    // Continue with fallbackDoc…
}
```

การอ่านจาก `FileStream` บางครั้งจะข้ามการตรวจสอบภายในที่ทำให้หยุดก่อนเวลา.

### 2. บันทึกรายละเอียดการกู้คืน
Aspose.Words สามารถส่งบันทึกรายละเอียดผ่าน `LoadOptions` `WarningCallback`. สร้าง `IWarningCallback` เพื่อจับสิ่งที่ถูกแก้ไข:

```csharp
class RecoveryLogger : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        Console.WriteLine($"[Recovery] {info.WarningType}: {info.Description}");
    }
}

// Attach logger
loadOptions.WarningCallback = new RecoveryLogger();
```

คุณจะเห็นข้อความเช่น *“Missing part /word/footer1.xml was skipped.”* ซึ่งเป็นประโยชน์อย่างยิ่งเมื่อคุณต้อง **repair broken docx** ในสายการผลิต.

### 3. บันทึกสำเนาที่สะอาด
หลังการกู้คืน, คุณอาจต้องการบันทึกเวอร์ชันที่สะอาดลงดิสก์:

```csharp
string cleanPath = Path.Combine("Samples", "recovered.docx");
doc.Save(cleanPath);
Console.WriteLine($"Clean copy saved to {cleanPath}");
```

ไฟล์ที่บันทึกแล้วจะไม่มีส่วน XML ที่เสียหาย ทำให้การเปิดในอนาคตเร็วและปลอดภัยยิ่งขึ้น.

### 4. จัดการไฟล์ที่ป้องกันด้วยรหัสผ่าน
หากไฟล์ที่เสียหายยังถูกเข้ารหัส, ตั้งรหัสผ่านบน `LoadOptions` ก่อนโหลด:

```csharp
loadOptions.Password = "mySecretPassword";
Document protectedDoc = new Document(filePath, loadOptions);
```

วิธีนี้คุณสามารถ **open corrupt docx** ที่ยังถูกป้องกันด้วยรหัสผ่านได้.

---

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงใน `Program.cs`. มันรวมทุกส่วนที่เราได้พูดถึง—การนำเข้า, ตัวเลือก, การบันทึก, และขั้นตอนการบันทึกที่สะอาด.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class RecoveryLogger : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Log each recovery action for audit purposes
        Console.WriteLine($"[Recovery] {info.WarningType}: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Step 1: Prepare LoadOptions with Lenient recovery and logger
        // -------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Lenient,
            WarningCallback = new RecoveryLogger()
        };

        // -------------------------------------------------------------
        // Step 2: Load the potentially corrupted DOCX file
        // -------------------------------------------------------------
        string filePath = Path.Combine("Samples", "maybeCorrupt.docx");
        if (!File.Exists(filePath))
        {
            Console.WriteLine($"File not found: {filePath}");
            return;
        }

        Document doc = new Document(filePath, loadOptions);

        // -------------------------------------------------------------
        // Step 3: Verify by retrieving page count
        // -------------------------------------------------------------
        int pageCount = doc.GetPageCount();
        Console.WriteLine($"Document loaded successfully. Page count: {pageCount}");

        // -------------------------------------------------------------
        // Step 4: Save a clean copy for future use
        // -------------------------------------------------------------
        string cleanPath = Path.Combine("Samples", "recovered.docx");
        doc.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to {cleanPath}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (สมมติว่าไฟล์ตัวอย่างมี 12 หน้าและมีความเสียหายเล็กน้อย):

```
[Recovery] MissingPart: Part /word/footer1.xml was missing and was ignored.
Document loaded successfully. Page count: 12
Clean copy saved to Samples\recovered.docx
```

หากไฟล์อ่านไม่ได้อย่างสมบูรณ์, ตัวบันทึกจะโชว์คำเตือนร้ายแรง, และโปรแกรมจะออกอย่างราบรื่นด้วยโหมด Lenient.

---

## สรุป

ตอนนี้คุณรู้วิธี **recover damaged DOCX file** ด้วย Aspose.Words, วิธี **repair broken docx** อัตโนมัติด้วย `RecoveryMode.Lenient`, และวิธี **open corrupt docx** อย่างปลอดภัยโดยไม่ทำให้แอปพลิเคชันของคุณพัง. วิธีนี้เบา, ต้องการเพียงไม่กี่บรรทัดของโค้ด, และทำงานได้ทั้งบน .NET Core และ .NET Framework.

ขั้นตอนต่อไป? ลองผสานตรรกะนี้เข้าไปใน API การอัปโหลดไฟล์, ประมวลผลเป็นชุดโฟลเดอร์เรซูเม่, หรือรวมกับ OCR เพื่อดึงข้อความจากเอกสารที่เสียหายบางส่วน. คุณอาจสำรวจฟีเจอร์อื่นของ Aspose.Words เช่น การแปลงเอกสารที่กู้คืนเป็น PDF หรือการดึงเมทาดาต้า.

มีคำถามเกี่ยวกับกรณีขอบ, ประสิทธิภาพ, หรือการให้สิทธิ์? แสดงความคิดเห็นด้านล่าง—ขอให้เขียนโค้ดอย่างสนุกสนาน

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}