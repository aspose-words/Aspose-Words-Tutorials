---
category: general
date: 2026-03-30
description: ตรวจสอบจำนวนหน้าในเอกสาร Word ขณะเรียนรู้วิธีกู้ไฟล์ Word ที่เสียหายและตรวจจับไฟล์
  Word ที่เสียหายโดยใช้ Aspose.Words.
draft: false
keywords:
- check page count
- recover corrupted word file
- detect corrupted word file
- Aspose.Words
- C# document loading
language: th
og_description: ตรวจสอบจำนวนหน้าในเอกสาร Word และเรียนรู้วิธีกู้ไฟล์ Word ที่เสียหายด้วย
  Aspose.Words. คู่มือสอน C# ทีละขั้นตอน.
og_title: ตรวจสอบจำนวนหน้าในเอกสาร Word – คู่มือครบถ้วน
tags:
- Aspose.Words
- C#
- document processing
title: ตรวจสอบจำนวนหน้าในไฟล์ Word – กู้ไฟล์ที่เสียหาย
url: /th/net/programming-with-document-properties/check-page-count-in-word-docs-recover-corrupted-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตรวจสอบจำนวนหน้าในเอกสาร Word – กู้ไฟล์ที่เสียหาย

เคยต้องการ **ตรวจสอบจำนวนหน้า** ในเอกสาร Word แต่ไม่แน่ใจว่าไฟล์ยังคงสมบูรณ์หรือไม่? คุณไม่ได้เป็นคนเดียว ในหลาย ๆ pipeline ของการทำอัตโนมัติ สิ่งแรกที่เราทำคือการตรวจสอบความยาวของเอกสาร และในเวลาเดียวกันเรามักต้อง **ตรวจจับไฟล์ Word ที่เสียหาย** ก่อนที่กระบวนการทั้งหมดจะล่ม  

ในบทเรียนนี้เราจะพาคุณผ่านตัวอย่าง C# ที่สมบูรณ์และสามารถรันได้ ซึ่งจะแสดงวิธี **ตรวจสอบจำนวนหน้า** พร้อมกับสาธิตวิธีที่ดีที่สุดในการ **กู้ไฟล์ Word ที่เสียหาย** ด้วย Aspose.Words LoadOptions. เมื่อจบคุณจะเข้าใจว่าการตั้งค่าแต่ละอย่างสำคัญอย่างไร, วิธีจัดการกับกรณีขอบ, และสิ่งที่ควรสังเกตเมื่อไฟล์ไม่สามารถเปิดได้

---

## สิ่งที่คุณจะได้เรียนรู้

- วิธีกำหนดค่า `LoadOptions` เพื่อ **ตรวจจับไฟล์ Word ที่เสียหาย**  
- ความแตกต่างระหว่าง `RecoveryMode.Strict` กับ `RecoveryMode.Auto`  
- รูปแบบที่เชื่อถือได้สำหรับการโหลดเอกสารและ **ตรวจสอบจำนวนหน้า** อย่างปลอดภัย  
- ปัญหาที่พบบ่อย (ไฟล์หาย, ข้อผิดพลาดสิทธิ์, รูปแบบที่ไม่คาดคิด) และวิธีหลีกเลี่ยง  
- ตัวอย่างโค้ดเต็มที่พร้อมคัดลอก‑วางและรันได้ทันที  

> **Prerequisites**: .NET 6+ (หรือ .NET Framework 4.7+), Visual Studio 2022 (หรือ IDE สำหรับ C# ใดก็ได้), และลิขสิทธิ์ Aspose.Words for .NET (รุ่นทดลองฟรีใช้ได้สำหรับสาธิตนี้)

---

## Step 1 – Install Aspose.Words

ขั้นตอนแรกคุณต้องติดตั้งแพคเกจ NuGet ของ Aspose.Words เปิดเทอร์มินัลในโฟลเดอร์โปรเจกต์ของคุณและรัน:

```bash
dotnet add package Aspose.Words
```

คำสั่งเดียวนี้จะดึงทุกอย่างที่คุณต้องการ—ไม่ต้องค้นหา DLL เพิ่มเติม หากคุณใช้ Visual Studio คุณก็สามารถติดตั้งผ่าน UI ของ NuGet Package Manager ได้เช่นกัน

---

## Step 2 – Set Up LoadOptions to **Detect Corrupted Word File**

หัวใจของวิธีแก้คือคลาส `LoadOptions` ซึ่งให้คุณบอก Aspose.Words ว่าจะเข้มงวดแค่ไหนเมื่อเจอไฟล์ที่มีปัญหา

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Choose a recovery strategy.
// Strict → throws an exception the moment corruption is spotted.
// Auto   → tries to salvage what it can and keeps loading.
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Strict   // <‑‑ change to Auto if you prefer auto‑recovery
};
```

**Why this matters**: หากคุณปล่อยให้ไลบรารีคาดเดาโดยเงียบ ๆ คุณอาจได้เอกสารที่ขาดหน้า ทำให้การดำเนินการ **ตรวจสอบจำนวนหน้า** ต่อไปไม่เชื่อถือได้ การใช้ `Strict` จะบังคับให้คุณจัดการกับปัญหานั้นตั้งแต่ต้น ซึ่งเป็นทางเลือกที่ปลอดภัยสำหรับ pipeline การผลิต

---

## Step 3 – Load the Document and **Check Page Count**

ตอนนี้เราจะเปิดไฟล์จริง ๆ ตัวสร้าง `Document` รับพาธและ `LoadOptions` ที่เราตั้งค่าไว้

```csharp
try
{
    // Replace the placeholder with the real path to your .docx file.
    const string filePath = @"C:\Docs\maybeCorrupt.docx";

    // Load the document using the strict recovery mode we set above.
    Document doc = new Document(filePath, loadOptions);

    // If we reach this line, the file is considered healthy enough.
    Console.WriteLine($"✅ Document loaded successfully. Page count: {doc.PageCount}");

    // You can now safely use the page count for any downstream logic.
    // Example: abort processing if the document is unexpectedly short.
    if (doc.PageCount < 2)
    {
        Console.WriteLine("⚠️ Document seems too short – double‑check the source.");
    }
}
catch (Exception ex) when (ex is FileCorruptedException || ex is LoadOptionsException)
{
    // This block runs only when Strict mode catches corruption.
    Console.WriteLine($"❌ Failed to load document: {ex.Message}");
    // Optional: switch to Auto mode on the fly, then retry.
    loadOptions.RecoveryMode = RecoveryMode.Auto;
    Console.WriteLine("🔄 Retrying with Auto recovery mode…");
    // Recursive retry is omitted for brevity—see Step 5 for a reusable method.
}
```

**What you’re seeing**:

- รูปแบบ `try/catch` ให้วิธีที่สะอาดในการ **ตรวจจับไฟล์ Word ที่เสียหาย**  
- `doc.PageCount` คือคุณสมบัติที่ทำการ **ตรวจสอบจำนวนหน้า** จริง ๆ  
- เงื่อนไขหลัง `Console.WriteLine` แสดงสถานการณ์สมมติที่คุณอาจหยุดทำงานหากเอกสารสั้นกว่าที่คาดไว้อย่างไม่คาดคิด

---

## Step 4 – Handle Edge Cases Gracefully

โค้ดในโลกจริงมักไม่ทำงานแยกจากสภาพแวดล้อม ด้านล่างเป็นสามสถานการณ์ “ถ้า‑อย่าง” ที่พบบ่อยและวิธีจัดการ

### 4.1 File Not Found

```csharp
if (!File.Exists(filePath))
{
    Console.WriteLine($"❗ File not found: {filePath}");
    return; // Bail out early – nothing to load.
}
```

### 4.2 Insufficient Permissions

```csharp
try
{
    // Attempt to open with read‑only sharing.
    using var stream = new FileStream(filePath, FileMode.Open, FileAccess.Read, FileShare.Read);
    Document doc = new Document(stream, loadOptions);
    Console.WriteLine($"📄 Page count: {doc.PageCount}");
}
catch (UnauthorizedAccessException)
{
    Console.WriteLine("🔐 You don’t have permission to read this file.");
}
```

### 4.3 Auto‑Recovery Fallback

หากคุณตัดสินใจว่าการกู้ไฟล์แบบเงียบ ๆ เป็นที่ยอมรับ ให้ห่อการกู้อัตโนมัติในเมธอดช่วยเหลือ:

```csharp
static Document LoadWithFallback(string path)
{
    var options = new LoadOptions { RecoveryMode = RecoveryMode.Strict };
    try
    {
        return new Document(path, options);
    }
    catch
    {
        // Switch to Auto and try again.
        options.RecoveryMode = RecoveryMode.Auto;
        return new Document(path, options);
    }
}
```

ตอนนี้คุณมีบรรทัดเดียว `Document doc = LoadWithFallback(filePath);` ที่จะคืนค่า `Document` เสมอ—ไม่ว่าจะเป็นไฟล์ที่สมบูรณ์หรือที่กู้ด้วยความพยายามสูงสุด

---

## Step 5 – Full Working Example (Copy‑Paste Ready)

ด้านล่างเป็นโปรแกรมทั้งหมดพร้อมใส่ลงในโปรเจกต์แอปคอนโซล มันรวมเคล็ดลับทั้งหมดจากขั้นตอนก่อนหน้า

```csharp
// ------------------------------------------------------------
// Check Page Count in Word Docs – Recover Corrupted Files
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        const string filePath = @"C:\Docs\maybeCorrupt.docx";

        // 1️⃣ Verify the file exists.
        if (!File.Exists(filePath))
        {
            Console.WriteLine($"❗ File not found: {filePath}");
            return;
        }

        // 2️⃣ Try loading with strict recovery mode.
        Document doc = LoadDocument(filePath, RecoveryMode.Strict);

        // 3️⃣ If we have a document, we can safely check page count.
        Console.WriteLine($"✅ Document loaded. Page count: {doc.PageCount}");

        // 4️⃣ Example business rule – abort if too few pages.
        if (doc.PageCount < 2)
        {
            Console.WriteLine("⚠️ Document seems too short – investigate the source file.");
        }
    }

    /// <summary>
    /// Loads a Word document using the specified recovery mode.
    /// Falls back to Auto mode if Strict fails.
    /// </summary>
    static Document LoadDocument(string path, RecoveryMode mode)
    {
        var options = new LoadOptions { RecoveryMode = mode };

        try
        {
            return new Document(path, options);
        }
        catch (Exception ex) when (ex is FileCorruptedException || ex is LoadOptionsException)
        {
            Console.WriteLine($"❌ Strict mode failed: {ex.Message}");
            Console.WriteLine("🔄 Switching to Auto recovery mode…");
            options.RecoveryMode = RecoveryMode.Auto;
            return new Document(path, options); // Auto will attempt to salvage.
        }
    }
}
```

**Expected output (healthy file)**:

```
✅ Document loaded. Page count: 12
```

**Expected output (corrupted file, strict mode)**:

```
❌ Strict mode failed: The file is corrupted and cannot be opened.
🔄 Switching to Auto recovery mode…
✅ Document loaded. Page count: 8   // Might be less than original.
```

---

## Step 6 – Pro Tips & Common Pitfalls

- **Pro tip:** บันทึกค่า `RecoveryMode` ที่คุณใช้เสมอ เมื่อคุณตรวจสอบการทำงานเป็นชุดในภายหลัง คุณจะรู้ว่าไฟล์ใดบ้างที่ถูกกู้แบบอัตโนมัติ  
- **Watch out for:** เอกสารที่มีวัตถุฝังอยู่ (แผนภูมิ, SmartArt) โหมด Auto อาจตัดวัตถุเหล่านี้ออก ซึ่งอาจส่งผลต่อการจัดหน้าและผลลัพธ์ของ **ตรวจสอบจำนวนหน้า**  
- **Performance note:** `RecoveryMode.Auto` ช้ากว่าบ้าง เพราะ Aspose.Words ต้องทำการตรวจสอบเพิ่มเติม หากคุณประมวลผลไฟล์หลายพันไฟล์ ให้ใช้ `Strict` เป็นค่าเริ่มต้นและใช้ Auto‑recovery เฉพาะกรณีที่จำเป็นต่อไฟล์แต่ละไฟล์  
- **Version check:** โค้ดด้านบนทำงานกับ Aspose.Words 22.12 ขึ้นไป รุ่นก่อนหน้ามีชื่อ enum ที่แตกต่าง (`LoadOptions.RecoveryMode` ถูกแนะนำตั้งแต่เวอร์ชัน 20.10)

---

## Conclusion

คุณมีรูปแบบที่มั่นคงและพร้อมใช้งานในระดับการผลิตเพื่อ **ตรวจสอบจำนวนหน้า** ในเอกสาร Word พร้อมกับเรียนรู้วิธี **กู้ไฟล์ Word ที่เสียหาย** และ **ตรวจจับไฟล์ Word ที่เสียหาย** ด้วย Aspose.Words ประเด็นสำคัญคือ:

1. กำหนดค่า `LoadOptions` ด้วย `RecoveryMode` ที่เหมาะสม  
2. ห่อการโหลดด้วย `try/catch` เพื่อให้พบความเสียหายตั้งแต่ต้น  
3. ใช้คุณสมบัติ `PageCount` เป็นแหล่งข้อมูลที่แน่นอนสำหรับจำนวนหน้า  
4. นำการกู้แบบอ่อนโยน (auto‑recovery, การจัดการสิทธิ์, การตรวจสอบไฟล์มีอยู่) มาใช้เมื่อจำเป็น  

จากนี้คุณอาจสำรวจต่อ:

- การสกัดข้อความจากแต่ละหน้า (`doc.GetText()` พร้อมช่วงหน้า)  
- การแปลงเอกสารเป็น PDF หลังจากยืนยันจำนวนหน้าแล้ว  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}