---
category: general
date: 2026-04-01
description: เปิดการแจ้งเตือนฟอนต์ขณะโหลดเอกสาร Word ด้วย Aspose.Words. เรียนรู้วิธีดักจับเหตุการณ์การแทนที่ฟอนต์โดยใช้
  C# LoadOptions และการตั้งค่าฟอนต์.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: th
og_description: เปิดใช้งานการแจ้งเตือนฟอนต์ขณะโหลดเอกสาร Word ด้วย Aspose.Words บทเรียนนี้จะแสดงวิธีการจับเหตุการณ์การแทนที่ฟอนต์ใน
  C#
og_title: เปิดการแจ้งเตือนฟอนต์ใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Font Management
title: เปิดใช้งานการแจ้งเตือนฟอนต์ใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
url: /th/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปิดใช้งานการแจ้งเตือนฟอนต์ใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์

เคยสงสัยไหมว่าเหตุใดเอกสาร Word จึงเปลี่ยนรูปลักษณ์โดยทันทีหลังจากที่คุณโหลดโดยโปรแกรม? **Enable Font Warnings** จะทำให้คุณทราบทันทีเมื่อ Aspose.Words แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรอง ในบทแนะนำนี้เราจะพาคุณผ่านตัวอย่างเชิงปฏิบัติที่ไม่เพียงจับการแทนที่เหล่านั้น แต่ยังอธิบาย *เหตุผล* ที่เกิดขึ้นด้วย

เราจะครอบคลุมทุกอย่างที่คุณต้องการเพื่อเริ่มต้นใช้งาน: แพคเกจ NuGet ที่จำเป็น การกำหนดค่า `LoadOptions` อย่างแม่นยำ และการแสดงผลบนคอนโซลที่บอกคุณว่าฟอนต์ใดบ้างที่ถูกแทนที่ เมื่อเสร็จสิ้นคุณจะมีรูปแบบการประมวลผลเอกสาร **C#** ที่แข็งแรงและนำกลับมาใช้ใหม่ได้กับ Aspose.Words ทุกเวอร์ชัน

## สิ่งที่คุณจะได้เรียนรู้

- วิธีสร้างอินสแตนซ์ `LoadOptions` ที่ติดตามการเปลี่ยนแปลงฟอนต์  
- จุดประสงค์ของเหตุการณ์ `SubstitutionWarning` และวิธีเชื่อมต่อ  
- ตัวอย่างโค้ดที่ทำงานได้เต็มรูปแบบซึ่งพิมพ์คำเตือนที่ชัดเจนบนคอนโซล  
- เคล็ดลับการจัดการกรณีขอบเช่นเอกสารที่มีเพียงฟอนต์มาตรฐานเท่านั้น  

ไม่จำเป็นต้องมีประสบการณ์กับ Aspose.Words มาก่อน—เพียงแค่คุ้นเคยกับ C# และ .NET ขั้นพื้นฐาน

---

![Enable font warnings diagram](placeholder-image.png "Enable font warnings diagram")

*ข้อความแทนภาพ: แผนภาพการเปิดใช้งานการแจ้งเตือนฟอนต์ แสดงการไหลของเหตุการณ์เมื่อฟอนต์ที่หายไปถูกแทนที่*

## ขั้นตอนที่ 1: ตั้งค่า LoadOptions และเปิดใช้งานการแจ้งเตือนฟอนต์

สิ่งแรกที่คุณต้องมีคืออ็อบเจกต์ `LoadOptions` ตัวนี้ทำหน้าที่บอก Aspose.Words ว่าจะจัดการไฟล์ที่กำลังโหลดอย่างไร โดยการกำหนดค่า `FontSettings` ใหม่ คุณจะเปิดประตูสู่เหตุการณ์ที่เกี่ยวข้องกับฟอนต์

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**ทำไมจึงสำคัญ:**  
หากคุณข้ามการกำหนดค่า `FontSettings` Aspose.Words จะยังคงแทนที่ฟอนต์ที่หายไปอยู่ดี แต่คุณจะไม่ได้รับการแจ้งเตือน กลไกการแจ้งเตือนอยู่ภายใน `FontSettings` ดังนั้นการเริ่มต้นมันจึง *จำเป็น* สำหรับเป้าหมายของเรา

> **เคล็ดลับ:** คุณสามารถชี้ `FontSettings` ไปยังโฟลเดอร์ฟอนต์ที่กำหนดเองได้ด้วย `SetFontsFolder` ซึ่งจะลดจำนวนคำเตือนที่คุณเห็น เพราะ Aspose.Words จะสามารถค้นพบฟอนต์ที่หายไปได้จริง

## ขั้นตอนที่ 2: สมัครรับเหตุการณ์ SubstitutionWarning (การแทนที่ฟอนต์)

เมื่ออ็อบเจกต์ `FontSettings` มีอยู่แล้ว เราจะเชื่อมต่อกับเหตุการณ์ `SubstitutionWarning` ของมัน เหตุการณ์นี้จะเกิด **ทุกครั้ง** ที่ Aspose.Words แทนที่ฟอนต์ที่ร้องขอด้วยฟอนต์อื่น

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**ทำไมจึงสำคัญ:**  
หากไม่มีตัวรับฟังนี้ คุณจะไม่มีมุมมองต่อกระบวนการแทนที่ บรรทัดบนคอนโซลจะให้ข้อมูลตรวจสอบอย่างรวดเร็ว ซึ่งเป็นประโยชน์อย่างยิ่งในระหว่างการสร้างอัตโนมัติหรือเมื่อสร้าง PDF สำหรับอุตสาหกรรมที่ต้องปฏิบัติตามมาตรฐานสูง

> **คำถามทั่วไป:** *ถ้าฉันต้องการปิดการแจ้งเตือนล่ะ?*  
> คุณสามารถถอดตัวจัดการออกหรือกำหนด `FontSettings.SubstitutionWarning += null;` ได้ อย่างไรก็ตาม การเก็บคำเตือนไว้มักเป็นวิธีที่ปลอดภัยที่สุด เพราะการแทนที่โดยเงียบอาจทำให้เกิดข้อบกพร่องของเลย์เอาต์

## ขั้นตอนที่ 3: โหลดเอกสารของคุณด้วยตัวเลือกที่กำหนด (การประมวลผลเอกสาร C#)

เมื่อระบบแจ้งเตรียมพร้อม การโหลดเอกสารก็ทำได้อย่างง่ายดาย เพียงส่งอินสแตนซ์ `LoadOptions` ไปยังคอนสตรัคเตอร์ `Document` แล้ว Aspose.Words จะจัดการส่วนที่เหลือให้เอง

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**ทำไมจึงสำคัญ:**  
อ็อบเจกต์ `LoadOptions` ทำหน้าที่เป็นสะพานระหว่างไฟล์ดิบและโครงสร้างการแจ้งเตือน หากคุณละเว้นมัน เอกสารจะโหลดโดยเงียบและฟอนต์ที่หายไปจะถูกแทนที่โดยไม่มีร่องรอย

> **กรณีขอบ:** บางเอกสารฝังไฟล์ฟอนต์ที่ต้องการไว้เอง ในสถานการณ์นั้นจะไม่มีการแจ้งเตือนใด ๆ เนื่องจาก Aspose.Words พบฟอนต์ที่ฝังอยู่แล้ว โค้ดข้างต้นยังทำงานได้; คุณจะเห็นเพียงคอนโซลว่างเปล่า

## ขั้นตอนที่ 4: ตรวจสอบผลลัพธ์และข้อผิดพลาดทั่วไป

เรียกโปรแกรมจาก command‑prompt หรือจากดีบักเกอร์ของ IDE หากเอกสารต้นทางมีฟอนต์ที่ไม่ได้ติดตั้งบนเครื่อง (หรือไม่ได้อยู่ในโฟลเดอร์ฟอนต์ที่กำหนดเอง) คุณจะเห็นบรรทัดเช่น:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

หากไม่มีอะไรพิมพ์ออกมา แสดงว่าอาจเป็นเพราะ:

1. ฟอนต์ทั้งหมดถูกพบ, **หรือ**  
2. ตัวจัดการ `SubstitutionWarning` ไม่ได้ถูกเชื่อมต่ออย่างถูกต้อง (ตรวจสอบขั้นตอน 2 อีกครั้ง)

### ทำไมการแทนที่ฟอนต์จึงเกิดขึ้น?

- **ฟอนต์ระบบหายไป:** ระบบปฏิบัติการไม่มีฟอนต์ที่ร้องขอ  
- **รูปแบบฟอนต์ที่ไม่รองรับ:** Aspose.Words สามารถอ่าน TrueType และ OpenType ได้ แต่ไม่รองรับรูปแบบที่เป็นกรรมสิทธิ์ทั้งหมด  
- **ข้อจำกัดของลิขสิทธิ์:** ฟอนต์เชิงพาณิชย์บางตัวบล็อกการฝัง ทำให้ต้องใช้ฟอนต์สำรอง

การเข้าใจ *เหตุผล* จะช่วยให้คุณตัดสินใจว่าจะจัดส่งฟอนต์ที่หายไปพร้อมแอปของคุณหรือปรับสไตล์ของเอกสาร

## โบนัส: ควบคุมฟอนต์สำรอง

หากคุณต้องการให้ฟอนต์ที่หายไปทั้งหมดแทนที่ด้วยตระกูลฟอนต์เฉพาะ (เช่น “Calibri”) คุณสามารถตั้งกฎการแทนที่ระดับทั่วโลกได้:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

ตอนนี้คอนโซลจะยังคงแจ้งเตือนคุณอยู่ แต่ผลลัพธ์ด้านภาพจะสอดคล้องกันสำหรับฟอนต์ที่หายไปทั้งหมด

---

## สรุป

- **เปิดใช้งานการแจ้งเตือนฟอนต์** ด้วยการสร้าง `LoadOptions` พร้อม `FontSettings` ใหม่  
- เชื่อมต่อเหตุการณ์ `SubstitutionWarning` เพื่อรับการแจ้งเตือนแบบเรียลไทม์ทุกครั้งที่ฟอนต์ถูกแทนที่  
- โหลดเอกสารของคุณโดยใช้ตัวเลือกที่กำหนดไว้ และอาจบันทึกเป็น PDF เพื่อดูผลลัพธ์เชิงภาพ  
- วิเคราะห์สาเหตุของการแทนที่และหากจำเป็นให้บังคับใช้ฟอนต์สำรองเฉพาะ

คุณเพิ่งเพิ่มเครือข่ายความปลอดภัยให้กับกระบวนการ **Aspose.Words** ของคุณเพื่อป้องกันการเปลี่ยนแปลงเลย์เอาต์โดยเงียบต่อไป ตอนต่อไปคุณอาจสำรวจ **การตั้งค่าฟอนต์** เช่น `DefaultFontName` หรือเจาะลึกตัวเลือก **การเรนเดอร์เอกสาร** เพื่อปรับแต่งผลลัพธ์ PDF ให้ละเอียดยิ่งขึ้น

---

### สิ่งที่ควรลองต่อไป

- **สำรวจคุณสมบัติอื่นของ FontSettings**: `SetFontsFolder`, `LoadFontSources`, และ `DefaultFontName`  
- **ผสานคำเตือนกับเฟรมเวิร์กการบันทึก** (Serilog, NLog) เพื่อการวินิจฉัยระดับ production  
- **ทดลองกับรูปแบบเอกสารต่าง ๆ** (`.doc`, `.rtf`, `.html`) เพื่อดูว่าตัวแต่ละรูปแบบจัดการฟอนต์ที่หายไปอย่างไร  

มีคำถามหรือสถานการณ์แปลก ๆ ไหม? แสดงความคิดเห็นด้านล่าง แล้วขอให้โค้ดของคุณสนุก!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}