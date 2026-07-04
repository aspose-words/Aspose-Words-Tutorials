---
category: general
date: 2026-06-08
description: เรียนรู้วิธีใช้ LoadOptions ใน Aspose.Words เพื่อตรวจจับฟอนต์ที่หายไประหว่างการนำเข้าเอกสาร
  คู่มือทีละขั้นตอนพร้อมโค้ด คำอธิบาย และแนวปฏิบัติที่ดีที่สุด
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: th
og_description: วิธีใช้ LoadOptions ใน Aspose.Words และตรวจจับฟอนต์ที่หายไปขณะโหลดเอกสาร
  คู่มือเต็มพร้อมโค้ดและเคล็ดลับเชิงปฏิบัติ
og_title: วิธีใช้ LoadOptions เพื่อตรวจจับฟอนต์ที่หายไป
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: วิธีใช้ LoadOptions เพื่อตรวจจับฟอนต์ที่หายไป
url: /th/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีใช้ LoadOptions เพื่อตรวจจับฟอนต์ที่หายไป

เคยสงสัย **วิธีใช้ LoadOptions** เมื่อโหลดไฟล์ Word ด้วย Aspose.Words หรือไม่? ในบทแนะนำนี้เราจะสาธิต **วิธีใช้ LoadOptions** เพื่อ **ตรวจจับฟอนต์ที่หายไป** และจัดการกับมันอย่างเหมาะสม ไม่ว่าคุณจะกำลังสร้างบริการแปลงเอกสารหรือเครื่องมือสร้างรายงาน ฟอนต์ที่หายไปอาจทำให้รูปแบบหน้าตาแปลกประหลาด ดังนั้นการตรวจจับตั้งแต่แรกเป็นสิ่งจำเป็น

เราจะเดินผ่านทุกขั้นตอน—ตั้งแต่การเชื่อมต่อ callback คำเตือนจนถึงการตีความผลลัพธ์—เพื่อให้คุณได้ตัวอย่าง C# ที่ทำงานเต็มรูปแบบและสามารถนำไปใช้ในโปรเจกต์ .NET ใดก็ได้ ไม่ต้องอ้างอิงเอกสารภายนอก เพียงโซลูชันครบวงจรเท่านั้น เมื่อจบคุณจะเข้าใจว่าทำไมระบบคำเตือนถึงมีอยู่ วิธีเปิดใช้งาน และต้องทำอย่างไรเมื่อ callback ถูกเรียก

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงลึก โปรดตรวจสอบว่าคุณมี:

- **Aspose.Words for .NET** (เวอร์ชันล่าสุดใดก็ได้; API ที่เราใช้มีความเสถียรตั้งแต่ปี 2022)
- สภาพแวดล้อมการพัฒนา .NET (Visual Studio, Rider หรือ VS Code พร้อมส่วนขยาย C#)
- ตัวอย่างไฟล์ Word (`input.docx`) ที่อ้างอิงฟอนต์ที่คุณ *ไม่ได้* ติดตั้งบนเครื่อง

แค่นั้นเอง—ไม่ต้องเพิ่มแพ็กเกจ NuGet ใด ๆ นอกจาก Aspose.Words

## วิธีใช้ LoadOptions กับ Aspose.Words

คลาส **LoadOptions** เป็นประตูสู่การปรับแต่งวิธีการอ่านเอกสาร โดยการเชื่อม callback คำเตือนเข้าไป คุณสามารถ **ตรวจจับฟอนต์ที่หายไป** ได้ทันทีที่ Aspose.Words ทำการพาร์สไฟล์ มาแยกย่อยกันดู

### ขั้นตอนที่ 1: สร้าง Warning Handler

Aspose.Words ใช้อินเทอร์เฟซ `IWarningCallback` เพื่อแจ้งเตือนคุณเกี่ยวกับปัญหาไม่สำคัญ เช่น การแทนที่ฟอนต์ ให้ทำการ implement อินเทอร์เฟซนี้และกำหนดว่าต้องทำอะไรเมื่อได้รับคำเตือน

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
หากไม่มี callback, Aspose.Words จะสลับฟอนต์ที่หายไปด้วยฟอนต์เริ่มต้น (โดยส่วนใหญ่คือ Arial) อย่างเงียบ ๆ การดักจับคำเตือน `FontSubstitution` ทำให้คุณสามารถบันทึกปัญหา แจ้งผู้ใช้ หรือแม้แต่แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรองที่กำหนดเองได้

### ขั้นตอนที่ 2: เชื่อม Handler กับ LoadOptions

ต่อไปเราจะสร้างอินสแตนซ์ `LoadOptions` และบอกให้ใช้ `FontWarningHandler` ของเรา นี่คือจุดที่ **วิธีใช้ LoadOptions** แสดงศักยภาพอย่างเต็มที่

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
`LoadOptions` เป็นศูนย์รวมการตั้งค่าต่าง ๆ ในขั้นตอนการนำเข้า (เช่น encoding, password ฯลฯ) การกำหนด `WarningCallback` ทำให้คุณเปิดกลไกแบบ event‑driven ที่เบาและทำงานกับเอกสารใด ๆ ที่โหลดด้วยตัวเลือกเหล่านี้

### ขั้นตอนที่ 3: โหลดเอกสารด้วย Options ที่กำหนดไว้

สุดท้าย เรานำ `LoadOptions` ไปใส่ในคอนสตรัคเตอร์ของ `Document` หากไฟล์ต้นทางอ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง Aspose.Words จะส่งคำเตือนและ handler ของคุณจะพิมพ์ข้อความออกมา

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**สิ่งที่คุณจะเห็น:**  
สมมติว่า `input.docx` ใช้ฟอนต์ชื่อ *“MyCustomFont”* ที่ไม่มีบนเครื่อง ผลลัพธ์ในคอนโซลจะเป็นดังนี้:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

หากฟอนต์ทั้งหมดมีอยู่ คำเตือนจะเงียบ—ไม่มีเอาต์พุตและไม่มีผลกระทบต่อประสิทธิภาพ

## ตรวจจับฟอนต์ที่หายไปด้วย Warning Callback (คีย์เวิร์ดรองในแอคชัน)

วลี **detect missing fonts** ปรากฏอย่างเป็นธรรมชาติในหัวข้อข้างต้น เพื่อเสริมความสำคัญของคีย์เวิร์ดรอง เรามาดูตัวอย่างการใช้งานหลายรูปแบบที่อาจเจอในโครงการจริง

### การประมวลผลหลายไฟล์ในลูป

บ่อยครั้งที่คุณต้องจัดการไฟล์หลายไฟล์ ชุด `LoadOptions` เดียวสามารถใช้ซ้ำได้ แต่ต้องจำว่า `WarningCallback` จะคงอยู่ระหว่างการโหลด หากต้องการแยกการแจ้งเตือนต่อเอกสารแต่ละไฟล์ ควรสร้าง `LoadOptions` ใหม่สำหรับแต่ละรอบ

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### โลจิกการแทนที่ฟอนต์แบบกำหนดเอง

แทนที่จะบันทึกเพียงอย่างเดียว คุณอาจต้องการแทนที่ฟอนต์ที่หายไปด้วยฟอนต์ที่ได้รับการอนุมัติจากองค์กร ขยาย handler ดังนี้:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

ตอนนี้คุณไม่เพียงแต่ **detect missing fonts** เท่านั้น แต่ยังสามารถกำหนดวิธีการแทนที่ได้ด้วย

### ปิดการแสดงคำเตือนที่ไม่ต้องการ

หากคุณสนใจเฉพาะปัญหาฟอนต์และต้องการละเว้นคำเตือนอื่น ๆ ให้กรองตาม `WarningType` ตามตัวอย่าง หากต้องการบันทึก *ทุก* คำเตือน เพียงลบเงื่อนไข `if` และพิมพ์ `info.WarningType` พร้อม `info.Description`

## ตัวอย่างเต็มที่สามารถรันได้

รวมทุกส่วนเข้าด้วยกัน นี่คือโปรแกรมสมบูรณ์ที่คุณสามารถคอมไพล์และรันได้ แทนที่ `"YOUR_DIRECTORY/input.docx"` ด้วยพาธของไฟล์ทดสอบของคุณ

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล (เมื่อฟอนต์หายไป):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

หากไม่มีฟอนต์ใดหายไป คุณจะเห็นเพียง:

```
Document loaded successfully.
```

## ข้อผิดพลาดทั่วไป & เคล็ดลับระดับมืออาชีพ

- **ข้อผิดพลาด:** ลืมตั้งค่า `WarningCallback` API จะยังคงแทนที่ฟอนต์ แต่คุณจะไม่รู้ว่ามันเกิดขึ้น  
  **เคล็ดลับระดับมืออาชีพ:** ควรเชื่อม handler เสมอเมื่อคุณต้องการความแม่นยำของฟอนต์; ค่าใช้จ่ายแทบไม่มี

- **ข้อผิดพลาด:** 

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้เกี่ยวข้องอย่างใกล้ชิดกับหัวข้อที่เราได้อธิบายไว้ในคู่มือนี้ โดยแต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [วิธีตรวจจับฟอนต์ใน Aspose.Words – จัดการคำเตือนและการตั้งค่า](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [วิธีจับฟอนต์ใน Aspose.Words – คู่มือฉบับสมบูรณ์](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [วิธีโหลด DOCX และตรวจจับฟอนต์ที่หายไป – คู่มือ C# ฉบับสมบูรณ์](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}