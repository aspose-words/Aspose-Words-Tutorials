---
category: general
date: 2026-02-24
description: วิธีตรวจจับฟอนต์ในเอกสาร Word ด้วย Aspose.Words. เรียนรู้วิธีตั้งค่า
  callback และโหลดเอกสาร Word พร้อมตัวอย่างโค้ดเต็ม.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: th
og_description: วิธีตรวจจับฟอนต์ในเอกสาร Word ด้วยการใช้ warning callback คู่มือนี้แสดงวิธีตั้งค่า
  callback และโหลดเอกสาร Word ด้วย Aspose.Words.
og_title: วิธีตรวจจับฟอนต์ในเอกสาร Word – คำแนะนำ C# ทีละขั้นตอน
tags:
- C#
- Aspose.Words
- Document Processing
title: วิธีตรวจจับแบบอักษรในเอกสาร Word – คู่มือ C# ฉบับสมบูรณ์
url: /th/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

ค้ดอย่างสนุกสนาน และขอให้เอกสารของคุณแสดงผลด้วยฟอนต์ที่คุณคาดหวังเสมอ!"

Then closing shortcodes unchanged.

Finally backtop button shortcode unchanged.

Make sure to keep all markdown formatting.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตรวจจับฟอนต์ในเอกสาร Word – คู่มือ C# ฉบับสมบูรณ์

เคยสงสัย **วิธีตรวจจับฟอนต์** ที่หายไปเมื่อคุณโหลดไฟล์ Word หรือไม่? บางทีคุณอาจเจอเอกสารที่ดูดีในโปรแกรมแก้ไข แต่ PDF ที่คุณสร้างจะสลับฟอนต์บางตัวโดยอัตโนมัติ นั่นคืออาการคลาสสิกของการแทนที่ฟอนต์ และการจับได้ตั้งแต่ต้นจะช่วยคุณหลีกเลี่ยงปัญหาการจัดหน้าไม่คาดคิด

ในบทแนะนำนี้เราจะพาคุณผ่านโซลูชันที่ใช้งานได้จริง: ใช้ **Aspose.Words** เพื่อโหลดไฟล์ `.docx` แนบ callback คำเตือน, และ **วิธีตั้งค่า callback** ที่รายงานการแทนที่ฟอนต์ทุกครั้ง เมื่อจบคุณจะไม่เพียงรู้ **วิธีตรวจจับฟอนต์** ด้วยโปรแกรมเท่านั้น แต่ยังเข้าใจ **วิธีตั้งค่า callback** อย่างถูกต้องและ **โหลดเอกสาร word** อย่างปลอดภัย—ทั้งหมดในตัวอย่าง C# ที่สามารถรันได้ในครั้งเดียว

> **สิ่งที่คุณจะได้รับ**
> * ตัวอย่างโค้ดที่พร้อมคัดลอก‑วางครบถ้วน  
> * คำอธิบายทีละขั้นตอนของแต่ละบรรทัด  
> * เคล็ดลับการจัดการกรณีขอบเช่นฟอนต์หายหลายตัวหรือโฟลเดอร์ฟอนต์แบบกำหนดเอง  
> * ตัวอย่างผลลัพธ์ในคอนโซลเพื่อให้คุณตรวจสอบว่าทุกอย่างทำงานได้

---

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดทำงานกับ .NET Core ด้วยเช่นกัน)  
- แพคเกจ NuGet Aspose.Words สำหรับ .NET (`Install-Package Aspose.Words`)  
- ไฟล์ Word ที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้งโดยเจตนา (เช่น `MissingFont.docx`)  
- Visual Studio, Rider หรือโปรแกรมแก้ไขใด ๆ ที่คุณชอบ  

ไม่ต้องการไลบรารีอื่นใด; ส่วนที่เหลือทั้งหมดเป็นส่วนหนึ่งของ .NET runtime มาตรฐาน

---

## วิธีตรวจจับฟอนต์ในเอกสาร Word

### ขั้นตอนที่ 1: สร้าง Load Options และแนบ Warning Callback

สิ่งแรกที่เราทำคือบอก Aspose.Words ว่าเราต้องการรับการแจ้งเตือนเกี่ยวกับปัญหาใด ๆ ที่เกิดขึ้นขณะโหลดไฟล์ นี่คือจุดที่ **วิธีตั้งค่า callback** เข้ามามีบทบาท

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**ทำไมสิ่งนี้ถึงสำคัญ:**  
`LoadOptions` คือประตูสู่การปรับแต่งกระบวนการโหลด โดยการกำหนดอินสแตนซ์ของ `FontWarningCollector` ให้กับ `WarningCallback` Aspose.Words จะเรียกเมธอด `Warning` ของเราในทุกครั้งที่มันแทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรอง นี่คือหัวใจของ **วิธีตรวจจับฟอนต์** ที่ไม่มีอยู่ในเครื่อง

### ขั้นตอนที่ 2: เตรียมอินสแตนซ์ LoadOptions

ตอนนี้เราจะสร้างอินสแตนซ์ของ `LoadOptions` และเชื่อมต่อ callback ของเรา

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**เคล็ดลับพิเศษ:**  
หากคุณต้องการควบคุม *ตำแหน่ง* ที่ Aspose ค้นหาฟอนต์สำรอง คุณสามารถตั้งค่า `loadOptions.FontSettings` ที่นี่ได้ นั่นเป็นประโยชน์เมื่อคุณมีโฟลเดอร์ฟอนต์ส่วนตัวบนเซิร์ฟเวอร์

### ขั้นตอนที่ 3: โหลดเอกสาร Word

เมื่อมีตัวเลือกพร้อม เราจึง **โหลดเอกสาร word** สุดท้าย นี่คือช่วงที่ Aspose วิเคราะห์ไฟล์ DOCX และหากมีฟอนต์ใดหายไป callback ของเราจะทำงาน

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**อะไรเกิดขึ้นเบื้องหลัง?**  
Aspose.Words อ่านส่วน XML ของ DOCX, แก้ไขการอ้างอิง `<w:font>` แต่ละรายการ, และตรวจสอบคอลเลกชันฟอนต์ของระบบ ทุกครั้งที่การอ้างอิงไม่สามารถทำได้ มันจะแทนที่ด้วยฟอนต์สำรองที่ตรงกันแรกและส่งคำเตือน `FontSubstitution`

### ขั้นตอนที่ 4: ตรวจสอบผลลัพธ์

เรียกโปรแกรมและดูที่คอนโซล สำหรับฟอนต์ที่หายไปแต่ละตัวคุณจะเห็นบรรทัดเช่น:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

หากเอกสารไม่มีฟอนต์ที่หายไป คอนโซลจะเงียบ—หมายความว่า **วิธีตรวจจับฟอนต์** ไม่พบผลลัพธ์ใด

### ขั้นตอนที่ 5: ตัวอย่างทำงานเต็มรูปแบบ (แอปคอนโซล)

ด้านล่างเป็นไฟล์ `Program.cs` ที่สมบูรณ์ซึ่งคุณสามารถใส่ลงในโปรเจกต์คอนโซลใหม่ได้ มันรวมทุกส่วนที่เราอธิบายไว้พร้อมด้วยตัวช่วยเล็ก ๆ เพื่อให้หน้าต่างคอนโซลเปิดค้างเมื่อดีบัก

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**ผลลัพธ์คอนโซลที่คาดหวัง** (ตัวอย่าง):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

หากคุณแทนที่ `MissingFont.docx` ด้วยไฟล์ที่ใช้ฟอนต์ที่ติดตั้งแล้วเท่านั้น คุณจะเห็นเพียงบรรทัด “Press any key…”—ยืนยันว่าตรรกะการตรวจจับทำงานตามที่คาดหวัง

---

## คำถามทั่วไป & กรณีขอบ

### ถ้าฉันต้องการจับ *ทุก* คำเตือน ไม่ใช่แค่การแทนที่ฟอนต์?

เพียงลบเงื่อนไข `if (info.Type == WarningType.FontSubstitution)` ออก `WarningInfo` มีคุณสมบัติ `Type` ที่เป็น enum คุณสามารถสลับใช้สำหรับสถานการณ์อื่น ๆ (เช่น `DocumentStructure`, `ImageLoading`)

### ฉันสามารถบันทึกคำเตือนลงไฟล์แทนคอนโซลได้หรือไม่?

แน่นอน. แทนที่ `Console.WriteLine` ด้วยการเรียกใช้เฟรมเวิร์กการบันทึกใด ๆ (`Serilog`, `NLog` เป็นต้น) Callback ทำงานบนเธรดเดียวกับที่โหลดเอกสาร ดังนั้นต้องแน่ใจว่า logger ของคุณปลอดภัยต่อเธรด

### พฤติกรรมนี้เป็นอย่างไรในแอปพลิเคชันเว็บ?

ใน ASP.NET Core คุณมักจะฉีด `IWarningCallback` แบบ singleton แล้วส่งผ่าน `LoadOptions` จำไว้ว่าอย่าเขียนโดยตรงไปยังสตรีมการตอบกลับ—บันทึกลงฐานข้อมูลหรือคอลเลกชันในหน่วยความจำที่คุณสามารถเปิดเผยต่อภายหลังผ่าน endpoint API

### ฟอนต์แบบกำหนดเองที่เก็บในโฟลเดอร์ที่ไม่ใช่ระบบล่ะ?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

ตอนนี้ Aspose.Words จะค้นหา `C:\MyCustomFonts` ก่อนที่จะใช้ฟอนต์ของ OS เป็นสำรอง ลดจำนวนคำเตือนการแทนที่ที่คุณเห็น

---

## สรุปภาพรวม

![ตรวจจับการเตือน callback ฟอนต์ใน Aspose.Words](/images/font-warning-callback.png "วิธีตรวจจับฟอนต์โดยใช้ warning callback")

*ภาพหน้าจอแสดงผลลัพธ์ในคอนโซลเมื่อฟอนต์ที่หายไปถูกแทนที่ ข้อความ alt มีคีย์เวิร์ดหลักสำหรับ SEO*

---

## สรุป

ตอนนี้คุณมีรูปแบบที่มั่นคงและพร้อมใช้งานในผลิตภัณฑ์สำหรับ **วิธีตรวจจับฟอนต์** ในไฟล์ Word ใด ๆ ที่คุณโหลดด้วย Aspose.Words ด้วย **วิธีตั้งค่า callback** คุณจะได้รับข้อมูลแบบเรียลไทม์เกี่ยวกับฟอนต์ที่หายไปหรือถูกแทนที่ และคุณได้เรียนรู้วิธีที่ถูกต้องในการ **โหลดเอกสาร word** พร้อมกับรักษาโค้ดให้สะอาดและดูแลได้ง่าย

ขั้นตอนต่อไป? ลองขยาย callback เพื่อรวบรวมคำเตือนลงในรายการ แล้วแสดงผลใน UI หรือรายงานอัตโนมัติ คุณอาจสำรวจ `FontSettings.SubstitutionSettings` เพื่อควบคุม *ฟอนต์ใด* ที่จะถูกเลือกเป็นสำรอง

อย่าลังเลที่จะทดลอง—เปลี่ยนเอกสาร, เพิ่มฟอนต์ที่หายไปมากขึ้น, หรือรวมตรรกะนี้เข้าไปใน pipeline การประมวลผลเอกสารที่ใหญ่ขึ้น หากคุณเจอปัญหาใด ๆ แสดงความคิดเห็นด้านล่างหรือทักมาที่ GitHub

ขอให้เขียนโค้ดอย่างสนุกสนาน และขอให้เอกสารของคุณแสดงผลด้วยฟอนต์ที่คุณคาดหวังเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}