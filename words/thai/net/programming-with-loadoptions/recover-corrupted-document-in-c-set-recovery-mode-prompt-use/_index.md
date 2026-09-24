---
category: general
date: 2026-01-11
description: กู้คืนเอกสารที่เสียหายใน C# ด้วย Aspose.Words เรียนรู้วิธีตั้งค่าโหมดการกู้คืน
  โหลดไฟล์ docx ด้วยการกู้คืน และแจ้งผู้ใช้เมื่อเกิดข้อผิดพลาดในไม่กี่ขั้นตอนง่าย
  ๆ.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: th
og_description: กู้คืนเอกสารที่เสียหายใน C# ด้วยการตั้งค่าโหมดการกู้คืน, โหลดไฟล์
  DOCX ด้วยการกู้คืน, และแจ้งผู้ใช้เมื่อเกิดข้อผิดพลาด. คู่มือขั้นตอนเต็มรูปแบบ.
og_title: กู้คืนเอกสารเสียหายใน C# – คู่มือด่วน
tags:
- Aspose.Words
- C#
- Document Recovery
title: กู้คืนเอกสารที่เสียหายใน C# – ตั้งค่าโหมดการกู้คืนและแจ้งผู้ใช้
url: /th/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การกู้คืนเอกสารเสียหายใน C# – คู่มือเต็ม

เคยลองเปิดไฟล์ DOCX ที่ดูปกติใน Word แต่โค้ดของคุณกลับโยนข้อยกเว้นหรือไม่? คุณอาจกำลังเจอสถานการณ์ **recover corrupted document** ข่าวดีคือ Aspose.Words ให้คุณควบคุมการจัดการไฟล์ที่แย่เหล่านั้นได้อย่างละเอียด—ไม่ว่าจะต้องการแก้ไขโดยเงียบ, โยนข้อยกเว้น, หรือถามผู้ใช้ว่าจะทำอย่างไร

ในบทเรียนนี้เราจะเดินผ่านทุกอย่างที่คุณต้องการเพื่อ **recover corrupted document** ตั้งแต่การติดตั้งไลบรารีจนถึงการเลือกตัวเลือก **set recovery mode** ที่เหมาะสม, **load docx with recovery**, และสุดท้าย **prompt user on error** เมื่อเกิดปัญหา ไม่บรรยายเกินความจำเป็น เพียงตัวอย่างที่ทำงานได้เต็มรูปแบบที่คุณสามารถคัดลอกไปใส่ในโปรเจกต์ .NET ใดก็ได้

> **ดูตัวอย่างสั้น:** เมื่อจบคุณจะมีแอปคอนโซลที่โหลดไฟล์ `corrupt.docx` ที่อาจเสีย, บันทึกคำเตือนใด ๆ, และถามผู้ใช้ว่าต้องการดำเนินการต่อเมื่อการกู้คืนล้มเหลว

---

## สิ่งที่คุณต้องมี

- **.NET 6.0** หรือใหม่กว่า (โค้ดนี้ยังทำงานบน .NET Framework 4.6+ ด้วย)  
- **Aspose.Words for .NET** – ติดตั้งผ่าน NuGet (`Install-Package Aspose.Words`)  
- ไฟล์ **corrupt DOCX** สำหรับทดสอบ (คุณสามารถทำให้ไฟล์เสียโดยเปิดใน hex editor หรือเปลี่ยนชื่อส่วนขยาย)  
- IDE ใดก็ได้ที่คุณชอบ—Visual Studio, Rider, หรือแม้แต่ VS Code ก็ใช้ได้

> *เคล็ดลับ:* เก็บสำเนาสำรองของไฟล์ต้นฉบับไว้ก่อน การกู้คืนอาจเขียนทับส่วนของเอกสารและคุณไม่อยากเสียข้อมูลที่ยังใช้งานได้

---

## ขั้นตอนที่ 1 – ติดตั้ง Aspose.Words และเพิ่ม Namespaces

เริ่มต้นด้วยการดึงไลบรารีจาก NuGet แล้วนำ namespaces ที่จำเป็นเข้ามา

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

เท่านี้ก็พร้อมสำหรับส่วนที่เหลือของคู่มือแล้ว `Aspose.Words.Loading` namespace มีคลาส `LoadOptions` ซึ่งเป็นกุญแจสำคัญในการ **set recovery mode**

---

## ขั้นตอนที่ 2 – เลือกโหมดการกู้คืน (Primary H2 with Keyword)

### Recover Corrupted Document – การตั้งค่า Recovery Mode ที่เหมาะสม

Aspose.Words มีพฤติกรรมการกู้คืน 3 แบบ:

| โหมด | สิ่งที่เกิดขึ้น | เมื่อควรใช้ |
|------|----------------|------------|
| **PromptUser** | แสดงกล่องโต้ตอบ (หรือคุณสามารถสร้างการแจ้งเตือนของคุณเอง) แล้วพยายามแก้ไฟล์ | เหมาะกับเครื่องมือแบบโต้ตอบที่ผู้ใช้สามารถตัดสินใจได้ |
| **Silent** | พยายามแก้โดยอัตโนมัติ ไม่แสดง UI | เหมาะกับงานแบบ batch หรือ service |
| **ThrowException** | หยุดการประมวลผลและโยนข้อยกเว้น | ใช้เมื่อคุณต้องการการตรวจสอบที่เข้มงวด |

ด้านล่างเป็นวิธี **set recovery mode** เป็น `PromptUser` หากคุณต้องการการจัดการแบบเงียบ เพียงสลับค่า enum

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **ทำไมเรื่องนี้ถึงสำคัญ:** การ **set recovery mode** อย่างชัดเจนบอก Aspose.Words ว่าจะทำงานอย่างรุนแรงแค่ไหน ค่าเริ่มต้นคือ `PromptUser` แต่การระบุอย่างชัดเจนทำให้เจตนาของคุณชัดเจนทั้งสำหรับผู้ดูแลในอนาคตและสำหรับเครื่องมือค้นหาที่ทำการครอว์ลโค้ด

---

## ขั้นตอนที่ 3 – โหลด DOCX ด้วยการกู้คืน

ต่อไปเราจะ **load docx with recovery** โดยใช้ `LoadOptions` ที่ตั้งค่าไว้ หากไฟล์เสีย Aspose.Words จะพยายามซ่อมหรือแจ้งคำเตือน ขึ้นอยู่กับโหมดที่เลือก

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

คอนสตรัคเตอร์ `Document` ทำงานหนักทั้งหมด ในโหมด **PromptUser** คุณจะเห็นการแจ้งเตือนบนคอนโซล (หรือ UI ที่คุณเชื่อมต่อกับเหตุการณ์ของ `LoadOptions`) ถามว่าต้องการดำเนินต่อหรือไม่ ในโหมด **Silent** วิธีจะพยายามอย่างเต็มที่แล้วดำเนินต่อไป

---

## ขั้นตอนที่ 4 – ตรวจสอบคำเตือนและแจ้งผู้ใช้

Aspose.Words จะบันทึกปัญหาที่พบในคอลเลกชัน `Warnings` เราจะวนลูปผ่านและให้ผู้ใช้ตัดสินใจว่าจะทำอย่างไรต่อ

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

โค้ดส่วนนี้ **prompt user on error** ในรูปแบบที่เหมาะกับคอนโซล หากคุณสร้างแอป Windows Forms หรือ WPF ให้เปลี่ยน `Console.ReadLine` เป็น `MessageBox` หรือไดอะล็อกที่กำหนดเอง

---

## ขั้นตอนที่ 5 – ทำงานกับเอกสารที่กู้คืนแล้ว

ตอนนี้เอกสารถูกโหลดเข้าสู่หน่วยความจำและได้รับการซ่อมแซมตามที่ Aspose.Words ทำได้ คุณสามารถอ่านเนื้อหา, บันทึกสำเนาที่สะอาด, หรือทำการปรับแต่งอื่น ๆ ได้ตามต้องการ

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

เมื่อรันโปรแกรมเต็มรูปแบบกับไฟล์ที่เสีย จะได้ผลลัพธ์บนคอนโซลประมาณนี้:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

หากไฟล์จริง ๆ แล้วไม่มีปัญหา คุณจะเห็นข้อความ “Document loaded without any warnings.” และสำเนาที่สะอาดจะเหมือนกับไฟล์ต้นฉบับ

---

## ตัวอย่างทำงานเต็มรูปแบบ

นี่คือโปรแกรมทั้งหมดในไฟล์เดียว คัดลอก‑วางลงในโปรเจกต์คอนโซลใหม่แล้วกด **F5**

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

รันมัน, ทำให้ไฟล์ทดสอบเสีย, แล้วดูการกู้คืนทำงานอย่างไร 🎉

---

## กรณีขอบและการปรับใช้ต่าง ๆ

| สถานการณ์ | สิ่งที่ต้องเปลี่ยน | เหตุผล |
|-----------|-------------------|--------|
| **การประมวลผลแบบ batch** (ไม่มีการโต้ตอบผู้ใช้) | ตั้ง `RecoveryMode = RecoveryMode.Silent` และลบการแจ้งเตือนบนคอนโซล | ทำให้ pipeline ทำงานอัตโนมัติ |
| **การตรวจสอบที่เข้มงวด** (fail fast) | ใช้ `RecoveryMode.ThrowException` ห่อการโหลดด้วย try/catch แล้วบันทึกข้อยกเว้น | รับประกันว่าจะไม่มีไฟล์ที่ซ่อมแซมบางส่วนเข้ามา |
| **UI แบบกำหนดเอง** (WinForms/WPF) | สมัครรับเหตุการณ์ `LoadOptions.LoadingProgress` หรือใช้ event ของ `Document.LoadOptions` เพื่อแสดงไดอะล็อก | ให้ประสบการณ์ผู้ใช้ที่ดีกว่าคอนโซล |
| **เอกสารขนาดใหญ่** (ข้อจำกัดหน่วยความจำ) | โหลดด้วย `LoadOptions.LoadFormat = LoadFormat.Docx` และพิจารณา `Document.SaveOptions` เพื่อสตรีมผลลัพธ์ | ป้องกันข้อผิดพลาด OutOfMemory |

---

## เคล็ดลับปฏิบัติ (สัญญาณ E‑E‑A‑T)

- **เก็บสำเนาสำรอง** ก่อนทำการกู้คืนเสมอ; กระบวนการอาจเขียนทับส่วนของไฟล์  
- **บันทึกคำเตือน** ลงไฟล์เพื่อวิเคราะห์ต่อไป; คำเตือนมักบ่งบอกสาเหตุหลัก (เช่น ส่วนหาย, XML เสีย)  
- **ทดสอบกับหลายรูปแบบของความเสียหาย** – ตัดไฟล์, ทำ XML แท็กเสีย, หรือเปลี่ยนโครงสร้าง zip เพื่อดูพฤติกรรมของแต่ละโหมด  
- **อัปเดต Aspose.Words อย่างสม่ำเสมอ**; เวอร์ชันใหม่ปรับปรุงอัลกอริทึมการกู้คืนและเพิ่มประเภทคำเตือนใหม่  
- **รวมกับการตรวจสอบ** – หลังการกู้คืนให้เรียก `document.UpdateFields()` และ `document.Save()` เพื่อยืนยันว่าเอกสารทำงานเต็มที่  

---

## สรุป

ตอนนี้คุณรู้วิธี **recover corrupted document** ใน C# ด้วยการ **set recovery mode**, **load docx with recovery**, และ **prompt user on error** เมื่อเกิดปัญหา ตัวอย่างเต็มแสดงขั้นตอนครบวงจรที่ทำงานได้ในแอปคอนโซล, เซอร์วิส, หรือโปรเจกต์ UI

ขั้นตอนต่อไป? ลองเปลี่ยนการแจ้งเตือนบนคอนโซลเป็นโมดัลไดอะล็อกในแอป WinForms, ทดลองโหมด **Silent** สำหรับงานเบื้องหลัง, หรือรวมโลจิกการกู้คืนเข้าใน endpoint ASP.NET ที่รับไฟล์อัปโหลดเพื่อให้ผู้ใช้อัปโหลด DOCX ที่เสียและรับไฟล์ที่ซ่อมแซมทันที

ขอให้เขียนโค้ดสนุกและเอกสารของคุณคงอยู่ครบถ้วน!  

---

![กู้คืนเอกสารเสียหายตัวอย่าง](/images/recover-corrupted-document.png "กู้คืนเอกสารเสียหาย")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}