---
category: general
date: 2026-01-14
description: บันทึกคำเตือนการแทนที่ฟอนต์ขณะโหลดเอกสาร Word ด้วย Aspose.Words. เรียนรู้วิธีตรวจจับฟอนต์ที่หายไปและวิธีจับฟอนต์ที่หายไปใน
  C#
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: th
og_description: บันทึกคำเตือนการแทนที่ฟอนต์ขณะโหลดเอกสาร Word ด้วย Aspose.Words. ค้นหาวิธีตรวจจับฟอนต์ที่หายไปและบันทึกฟอนต์ที่หายไปใน
  C#
og_title: บันทึกคำเตือนการแทนที่ฟอนต์ – คู่มือ Aspose.Words ฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Processing
title: บันทึกคำเตือนการแทนที่ฟอนต์ – คู่มือ Aspose.Words ฉบับสมบูรณ์
url: /th/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# บันทึกคำเตือนการแทนที่ฟอนต์ – คู่มือ Aspose.Words ฉบับสมบูรณ์

การบันทึกคำเตือนการแทนที่ฟอนต์เป็นสิ่งสำคัญเมื่อคุณต้องการรับประกันว่าเอกสาร Word จะดูเหมือนเดิมอย่างแน่นอนหลังจากที่โหลดโดย Aspose.Words หากคุณเคยสงสัยวิธี **detect missing fonts** หรืออยากรู้ **how to capture missing fonts** คุณมาถูกที่แล้ว  

ในบทแนะนำนี้เราจะพาคุณผ่านสถานการณ์จริง แสดงโค้ด C# ฉบับเต็ม และอธิบายว่าทำไมแต่ละบรรทัดถึงสำคัญ เมื่อจบคุณจะสามารถบันทึกเหตุการณ์การแทนที่ฟอนต์ทุกครั้งและดำเนินการต่อได้—ไม่มีคำเตือนลึกลับเหลืออยู่

![ตัวอย่างการบันทึกคำเตือนการแทนที่ฟอนต์](/images/font-warnings.png "ภาพหน้าจอแสดงผลลัพธ์คอนโซลของการบันทึกคำเตือนการแทนที่ฟอนต์")

## สิ่งที่คุณจะได้เรียนรู้

- วิธีกำหนดค่า `LoadOptions` เพื่อให้ Aspose.Words แสดงคำเตือนแบบพิมพ์สำหรับการแทนที่ฟอนต์.  
- ขั้นตอนที่แน่นอนเพื่อ **detect missing fonts** ระหว่างการโหลดเอกสาร.  
- วิธีที่สะอาดในการ **capture missing fonts** และเขียนลงในบันทึกหรือระบบการตรวจสอบของคุณเอง.  
- การจัดการกรณีขอบ (เช่น เมื่อเอกสารมีฟอนต์ที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์).  

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ทำงานกับ .NET Framework 4.6+ ด้วยเช่นกัน).  
- ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือทดลองใช้ฟรี).  
- ความคุ้นเคยพื้นฐานกับ C# และแอปพลิเคชันคอนโซล.  

หากคุณมีทั้งหมดแล้ว, ไปต่อกันเลย.

## ขั้นตอนที่ 1 – ตั้งค่า LoadOptions เพื่อให้แสดงคำเตือนแบบพิมพ์

หัวใจของวิธีแก้ปัญหาตั้งอยู่ที่ `LoadOptions.FontSubstitutionWarning`. การสลับเป็น `RaiseTypedWarnings` จะบอกให้ Aspose.Words ส่งเหตุการณ์ **every time** ที่ไม่พบฟอนต์ที่คุณระบุ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Why this matters:**  
> พฤติกรรมเริ่มต้นจะสลับฟอนต์ที่หายไปโดยเงียบ ๆ กับฟอนต์ที่ใกล้เคียงที่สุด ซึ่งอาจทำให้เกิดข้อบกพร่องการจัดวางที่คุณไม่คาดคิด การแสดงคำเตือนแบบพิมพ์ทำให้คุณมองเห็นได้อย่างเต็มที่

## ขั้นตอนที่ 2 – สมัครรับเหตุการณ์คำเตือน

ตอนนี้เราจะเชื่อมต่อกับ `loadOptions.FontSubstitutionWarning`. Lambda จะรับออบเจ็กต์ `e` ที่บอกเราว่าฟอนต์ใดหายไปและฟอนต์ใดถูกใช้แทน

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tip:** หากคุณรันบนเว็บเซิร์ฟเวอร์ ให้แทนที่ `Console.WriteLine` ด้วย logger ที่มีโครงสร้าง (เช่น Serilog, NLog ฯลฯ) เพื่อให้สามารถสืบค้นข้อมูลภายหลังได้

## ขั้นตอนที่ 3 – โหลดเอกสารโดยใช้ตัวเลือกที่กำหนด

เมื่อกลไกการเตือนพร้อมใช้งาน เพียงโหลดเอกสารตามปกติ เหตุการณ์จะเกิดขึ้นโดยอัตโนมัติสำหรับทุกฟอนต์ที่หายไป

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### ผลลัพธ์คอนโซลที่คาดหวัง

หาก `input.docx` อ้างอิงฟอนต์ชื่อ *MyFancyFont* ที่ไม่ได้ติดตั้ง คุณจะเห็น:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

แต่ละบรรทัดสอดคล้องกับเหตุการณ์ **detect missing fonts** ให้คุณมีเส้นทางตรวจสอบที่ครบถ้วน

## ขั้นตอนที่ 4 – การจัดการกรณีขอบและสถานการณ์ขั้นสูง

### 4.1 เมื่อไม่มีการแทนที่

บางครั้งเอกสารอาจใช้ฟอนต์ระบบที่มีอยู่แล้ว ในกรณีนั้นเหตุการณ์คำเตือนจะไม่เกิดขึ้นและคุณจะได้คอนโซลที่สะอาดไม่มีเอาต์พุต นั่นเป็นสัญญาณที่ดี—สภาพแวดล้อมของคุณมีฟอนต์ที่จำเป็นครบแล้ว

### 4.2 การบันทึกคำเตือนเพื่อการวิเคราะห์ในภายหลัง

หากต้องการเก็บคำเตือนเพื่อรายงานรายคืน ให้รวบรวมไว้ในรายการ:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

หลังจากโหลดเสร็จ คุณสามารถแปลง `missingFonts` เป็น JSON, บันทึกลงฐานข้อมูล หรือส่งอีเมลสรุปได้

### 4.3 การทำงานกับ PDF หรือรูปแบบอื่น

วิธีการ `LoadOptions` เดียวกันทำงานกับการเรียก `Load` สำหรับ PDF, RTF และแม้แต่ไฟล์ HTML เพียงส่งออบเจ็กต์ options เดียวกันให้ Aspose.Words จะส่งคำเตือนสำหรับฟอนต์ใดที่ไม่ตรงกัน

## ขั้นตอนที่ 5 – ตรวจสอบผลลัพธ์ด้วยโปรแกรม

หากคุณต้องการทดสอบอัตโนมัติโดยไม่ต้องมองคอนโซล ให้ตรวจสอบว่ารายการมีรายการที่คาดหวังอยู่หรือไม่:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

ส่วนนี้แสดง **how to capture missing fonts** ในโค้ด ไม่ใช่แค่ในบันทึก

## ข้อผิดพลาดทั่วไป & วิธีหลีกเลี่ยง

| ข้อผิดพลาด | สาเหตุที่เกิด | วิธีแก้ |
|------------|----------------|----------|
| ลืมตั้งค่า `RaiseTypedWarnings` | ค่าเริ่มต้นคือ `DoNotRaise` ทำให้ไม่มีเหตุการณ์เกิดขึ้น. | ตั้งค่า `FontSubstitutionWarning` อย่างชัดเจนตามที่แสดงในขั้นตอน 1. |
| ใช้ `Console.WriteLine` ในเว็บแอป | ผลลัพธ์คอนโซลหายไปใน IIS/ASP.NET Core. | เปลี่ยนไปใช้ logger ที่คงที่ (เช่น Serilog). |
| โหลดเอกสารด้วยเส้นทางสัมพัทธ์ | ไดเรกทอรีทำงานอาจแตกต่างกันในขณะรัน. | ใช้เส้นทางแบบเต็มหรือ `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| ละเลย `SubstitutedFontName` | คุณสูญเสียข้อมูลว่าฟอนต์สำรองใดถูกเลือก. | ควรบันทึกทั้ง `FontName` และ `SubstitutedFontName` เสมอ. |

## โบนัส: การอัตโนมัติการติดตั้งฟอนต์

หากคุณควบคุมสภาพแวดล้อมการปรับใช้ คุณสามารถติดตั้งฟอนต์ที่หายไปล่วงหน้าโดยใช้สคริปต์ PowerShell:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

การรันสคริปต์นี้ก่อนแอปพลิเคชันเริ่มทำงานจะขจัดคำเตือน **detect missing fonts** ส่วนใหญ่โดยสิ้นเชิง

## สรุป

เราได้ครอบคลุมทุกอย่างที่คุณต้องการ **log font substitution warnings** เมื่อโหลดเอกสาร Word ด้วย Aspose.Words โดยการกำหนด `LoadOptions` สมัครรับเหตุการณ์คำเตือน และบันทึกผลลัพธ์ตามต้องการ คุณจึงสามารถ **detect missing fonts** อย่างเชื่อถือได้และเข้าใจ **how to capture missing fonts** สำหรับโครงการ .NET ใด ๆ

นำโค้ดไปใช้ ปรับ logger ให้เข้ากับสแต็กของคุณ แล้วคุณจะไม่ต้องกังวลกับการสลับฟอนต์แบบเงียบอีกต่อไป ขั้นตอนต่อไปอาจรวมถึง:

- ผสานรายการคำเตือนเข้ากับ pipeline CI/CD ของคุณเพื่อให้การสร้างล้มเหลวเมื่อฟอนต์สำคัญหายไป.  
- ขยายวิธีการเพื่อติดตามการใช้ฟอนต์ในเอกสารหลายไฟล์.  
- สำรวจ API `FontSettings` ของ Aspose.Words เพื่อกำหนดฟอนต์สำรองแบบกำหนดเอง.

มีคำถามหรือสถานการณ์ที่ซับซ้อน? แสดงความคิดเห็นได้เลย เราจะช่วยกันแก้ไข ปรึกษาและพัฒนาไปด้วยกัน Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}