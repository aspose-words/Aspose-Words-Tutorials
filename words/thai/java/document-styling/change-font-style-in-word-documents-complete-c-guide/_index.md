---
category: general
date: 2026-06-27
description: เปลี่ยนสไตล์ฟอนต์ในเอกสาร Word ด้วย C# เรียนรู้วิธีตั้งน้ำหนักฟอนต์,
  ตั้งน้ำหนักตัวหนา, และปรับความกว้างของฟอนต์เพื่อการพิมพ์ที่แม่นยำ.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: th
og_description: เปลี่ยนสไตล์ฟอนต์ในเอกสาร Word ด้วย C# ค้นพบวิธีตั้งน้ำหนักฟอนต์ ตั้งน้ำหนักตัวหนา
  และปรับความกว้างของฟอนต์ในไม่กี่ขั้นตอนง่าย ๆ
og_title: เปลี่ยนสไตล์ฟอนต์ในเอกสาร Word – คู่มือ C# ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: เปลี่ยนสไตล์ฟอนต์ในเอกสาร Word – คู่มือ C# ฉบับสมบูรณ์
url: /th/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปลี่ยนสไตล์ฟอนต์ในเอกสาร Word – คู่มือ C# ฉบับสมบูรณ์

เคยต้อง **เปลี่ยนสไตล์ฟอนต์** ในไฟล์ Word แต่ไม่แน่ใจว่า API ใดทำหน้าที่นั้นจริง ๆ หรือไม่? คุณไม่ได้อยู่คนเดียว—นักพัฒนาส่วนใหญ่มักเจออุปสรรคนี้เมื่อลองปรับแต่งการพิมพ์แบบโปรแกรมเป็นครั้งแรก  

ข่าวดีคือด้วยไม่กี่บรรทัดของ C# คุณก็สามารถ **ตั้งค่าน้ำหนักฟอนต์** ได้ แม้จะเพิ่มเป็นน้ำหนักหนา (bold) และปรับความกว้างของ glyph แต่ละตัวได้อย่างละเอียด ในบทเรียนนี้เราจะเดินผ่านตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่งแก้ไขไฟล์ `.docx` ตั้งแต่ต้นจนจบ

## สิ่งที่คู่มือนี้ครอบคลุม

เราจะเริ่มด้วยการโหลดเอกสารที่มีอยู่แล้ว จากนั้นสร้างอ็อบเจ็กต์ `FontSettings` ที่บรรจุ `FontVariation` จากนั้นเราจะ **ตั้งค่าน้ำหนักฟอนต์**, **ตั้งค่าน้ำหนักหนา**, และ **ปรับความกว้างของฟอนต์** ก่อนสุดท้ายนำการเปลี่ยนแปลงไปใช้และบันทึกผลลัพธ์ ไม่ต้องใช้ไฟล์กำหนดค่าภายนอก ไม่ต้องใช้สตริงวิเศษ—แค่ C# ธรรมดาและไลบรารี Aspose.Words เท่านั้น เมื่อจบคุณจะสามารถ **แก้ไขฟอนต์ใน Word** ได้อย่างมั่นใจ ไม่ว่าจะสร้างเอนจินรายงานหรือเครื่องมือจัดรูปแบบแบบกลุ่ม

### ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดยังคอมไพล์บน .NET Core ได้เช่นกัน)  
- NuGet package Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- ตัวอย่างไฟล์ `input.docx` ที่วางไว้ในโฟลเดอร์ที่คุณอ้างอิง (เราจะเรียกมันว่า `YOUR_DIRECTORY`)  

ถ้าคุณพร้อมกับพื้นฐานเหล่านี้แล้ว ไปต่อกันเลย

---

## ขั้นตอนที่ 1: เปลี่ยนสไตล์ฟอนต์ – โหลดเอกสาร Word

สิ่งแรกที่ต้องทำคือดึงไฟล์เป้าหมายเข้ามาในหน่วยความจำ คิดว่าเป็นการเปิดผ้าใบเปล่าที่คุณจะวาดการพิมพ์ใหม่บนมัน

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **เคล็ดลับ:** หากคุณรันโค้ดบนเซิร์ฟเวอร์ที่ไม่มี UI อย่าลืมตั้งค่าไลเซนส์ Aspose.Words ให้เป็นแบบทดลองหรือใส่ไฟล์ไลเซนส์ที่ถูกต้องเพื่อหลีกเลี่ยงข้อความลายน้ำ

---

## ขั้นตอนที่ 2: ตั้งค่าน้ำหนักฟอนต์และตั้งค่าน้ำหนักหนา

เมื่อเอกสารถูกโหลดเข้าสู่หน่วยความจำแล้ว เราจะสร้างคอนเทนเนอร์ `FontSettings` อ็อบเจ็กต์นี้เป็นประตูสู่การปรับแต่งระดับฟอนต์ทุกอย่างที่คุณทำได้  

คลาส `FontVariation` ให้คุณระบุคุณสมบัติหลักสามอย่าง:

| Property | สิ่งที่ทำ | ช่วงค่าที่ทั่วไป |
|----------|-----------|-----------------|
| `Weight` | ควบคุมความหนาของ glyph ที่แสดงผล ค่า **700** คือ “bold” มาตรฐาน | 100‑900 |
| `Width`  | ยืดหรือบีบ glyph แนวนอน ค่า **100** หมายถึงความกว้างปกติ | 50‑200 |
| `Slant`  | เพิ่มการเอียงคล้ายอิตาลิก ตัวเลขบวกเอียงขวา | -90‑90 |

ด้านล่างเราจะ **ตั้งค่าน้ำหนักฟอนต์** เป็น 700 (bold) และยังแสดงวิธีเพิ่มค่าน้ำหนักให้สูงกว่านั้นหากฟอนต์ของคุณรองรับสไตล์ “extra‑bold”

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **ทำไมถึงสำคัญ:** การตั้งค่า **set bold weight** โดยตรงผ่าน `SetWeight` ทำให้ไม่ต้องสร้างอ็อบเจ็กต์สไตล์ “Bold” แยกต่างหาก ให้คุณควบคุมความหนาของเส้นได้อย่างพิกเซล‑เพอร์เฟ็คท์

---

## ขั้นตอนที่ 3: ปรับความกว้างของฟอนต์

หากคุณเคยต้องการทำให้ฟอนต์ดูกระชับสำหรับหัวข้อหรือกว้างขึ้นสำหรับย่อหน้า คุณจะยินดีที่มาถึงขั้นตอนนี้ คุณสมบัติ `Width` ทำหน้าที่นั้นโดยตรง

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **ข้อผิดพลาดทั่วไป:** ไม่ใช่ทุกฟอนต์จะรองรับการปรับความกว้าง หากคุณไม่เห็นการเปลี่ยนแปลง ให้ตรวจสอบว่าครอบครัวฟอนต์ที่ใช้สนับสนุน glyph แบบบีบ/ขยายหรือไม่

---

## ขั้นตอนที่ 4: นำการตั้งค่าไปใช้ – แก้ไขฟอนต์ใน Word

เมื่อ `FontSettings` ของเราถูกกำหนดค่าเต็มที่แล้ว ขั้นตอนสุดท้ายคือบอกเอกสารให้ใช้ค่าเหล่านั้น นี่คือจุดที่เราจะ **แก้ไขฟอนต์ใน Word** ระดับเอกสาร ส่งผลต่อทุก run ของข้อความที่สืบทอดสไตล์เริ่มต้น

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

หากคุณต้องการกำหนดเป้าหมายเฉพาะย่อหน้าหรือ run เพียงบางส่วน คุณสามารถดึงโหนดนั้นออกมาและตั้งค่า `FontSettings` แยกต่างหาก ตัวอย่างข้างต้นแสดงวิธีการแบบกว้าง ซึ่งเหมาะกับสถานการณ์จัดรูปแบบแบบกลุ่ม

---

## ขั้นตอนที่ 5: บันทึกและตรวจสอบการเปลี่ยนแปลง

การบันทึกเป็นขั้นตอนสุดท้าย (แต่ไม่ใช่ขั้นตอนที่สำคัญน้อย) หลังจากบันทึกไฟล์แล้ว คุณสามารถเปิดไฟล์ใน Microsoft Word เพื่อตรวจสอบสไตล์ใหม่ที่ทำงาน

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

- ข้อความหลักทั้งหมดที่เคยใช้ฟอนต์เริ่มต้นจะปรากฏเป็น **หนา** (weight 700)  
- หากคุณทดลอง `SetWidth(80)` ตัวอักษรจะดูกระชับขึ้น; `SetWidth(120)` จะทำให้กระจายออก  
- เนื้อหาอื่น ๆ (รูปภาพ, ตาราง ฯลฯ) ไม่ได้รับการเปลี่ยนแปลง—มีเพียงคุณลักษณะฟอนต์ของ run ข้อความเท่านั้นที่ถูกปรับ

เปิด `output.docx` ใน Word, เลือกย่อหน้า แล้วเปิดกล่องโต้ตอบ **Font** คุณจะเห็นช่อง **Bold** ถูกทำเครื่องหมายและค่า **Scale** (width) แสดงตามที่คุณตั้งไว้

---

## คำถามที่พบบ่อย & กรณีขอบ

### สามารถเปลี่ยนครอบครัวฟอนต์พร้อมกันได้หรือไม่?

ทำได้แน่นอน หลังจากตั้งค่า `FontVariation` แล้ว คุณยังสามารถกำหนด `FontInfo` ใหม่ให้กับ `FontSettings` ได้อีกด้วย:

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### ถ้าต้องการ **ตั้งค่าน้ำหนักหนา** เฉพาะหัวข้อจะทำอย่างไร?

ดึงโหนดสไตล์หัวข้อออกมาและใช้ `FontSettings` แยกต่างหาก:

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### ทำงานบน .NET Core บน Linux ได้หรือไม่?

ได้—Aspose.Words รองรับหลายแพลตฟอร์ม เพียงตรวจสอบว่าคุณได้ติดตั้งไลบรารีรันไทม์ที่จำเป็น (`libgdiplus` บนบางดิสทริบิวชัน) หากต้องการแปลงเอกสารเป็น PDF ต่อไป

---

## สรุป

เราได้ **เปลี่ยนสไตล์ฟอนต์** ในเอกสาร Word ตั้งแต่ต้นจนจบ ครอบคลุมการ **ตั้งค่าน้ำหนักฟอนต์**, **ตั้งค่าน้ำหนักหนา**, และ **ปรับความกว้างของฟอนต์** ด้วย C# ตัวอย่างที่ทำงานได้เต็มรูปแบบแสดงการนำเข้า, การสร้างอ็อบเจ็กต์, และการเรียกเมธอดที่จำเป็นทั้งหมด เพื่อให้คุณคัดลอก‑วางลงในโปรเจกต์ของตนเองและเห็นการเปลี่ยนแปลงของการพิมพ์ทันที  

เมื่อคุณรู้วิธี **แก้ไขฟอนต์ใน Word** แล้ว คุณอาจสนใจหัวข้อที่เกี่ยวข้องเช่น **การฝังฟอนต์แบบกำหนดเอง**, **การใช้สีไล่ระดับบนฟอนต์**, หรือ **การสร้างตารางแบบไดนามิก** ทุกหัวข้อเหล่านี้ต่อยอดจากพื้นฐาน `FontSettings` ที่เราใช้ในที่นี้ ทำให้คุณก้าวหน้าไปอีกขั้นหนึ่ง  

มีสถานการณ์ที่ไม่ได้กล่าวถึง? แสดงความคิดเห็นมาได้ เราจะสำรวจร่วมกัน ขอให้เขียนโค้ดอย่างสนุกและให้เอกสารของคุณดูสมบูรณ์แบบตามที่คุณต้องการ!  

![change font style example](placeholder.png){alt="ตัวอย่างการเปลี่ยนสไตล์ฟอนต์"}

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [ตั้งค่าเครื่องหมายเน้นฟอนต์](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [ตั้งค่าการสำรองฟอนต์](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [ตั้งค่าการจัดรูปแบบฟอนต์](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}