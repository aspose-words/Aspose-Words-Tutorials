---
category: general
date: 2026-04-21
description: เรียนรู้วิธีตรวจจับฟอนต์, บันทึกคำเตือน, ตั้งค่าการเรียกกลับ, และแสดงรายการคำเตือนด้วย
  Aspose.Words ใน C#. คู่มือขั้นตอนต่อขั้นตอนสำหรับการจัดการฟอนต์ที่เชื่อถือได้.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: th
og_description: วิธีตรวจจับฟอนต์ใน Aspose.Words? บทเรียนนี้จะแสดงวิธีดักจับคำเตือน,
  กำหนดค่า callback, และแสดงรายการคำเตือนใน C#
og_title: วิธีตรวจจับฟอนต์ใน Aspose.Words – คู่มือฉบับสมบูรณ์
tags:
- Aspose.Words
- C#
- Document Processing
title: วิธีตรวจจับแบบอักษรใน Aspose.Words – คู่มือฉบับสมบูรณ์
url: /th/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตรวจจับฟอนต์ใน Aspose.Words – คู่มือฉบับสมบูรณ์

เคยสงสัย **วิธีตรวจจับฟอนต์** ที่หายไปเมื่อคุณโหลดเอกสาร Word หรือไม่? นี่เป็นสถานการณ์ที่เกิดบ่อยกว่าที่คุณคิด โดยเฉพาะเมื่อต้องทำงานกับไฟล์เก่าหรือการปรับใช้ข้ามแพลตฟอร์ม ในบทแนะนำนี้เราจะเดินผ่านตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่ง **จับคำเตือน**, **ตั้งค่าคอลแบ็ก**, และ **แสดงรายการคำเตือน** เพื่อให้คุณรู้เสมอว่าฟอนต์ใดถูกแทนที่

เราจะใช้ Aspose.Words for .NET (เวอร์ชัน 24.9 ณ เวลาที่เขียน) และ C# ธรรมดา ไม่ใช้บริการภายนอก ไม่ต้องใช้เวทมนตร์—เพียง API และไม่กี่บรรทัดโค้ดเท่านั้น เมื่อเสร็จคุณจะสามารถตรวจจับการแทนที่ฟอนต์ทุกครั้ง บันทึกลงล็อก และแม้แต่ตัดสินใจยกเลิกการโหลดหากฟอนต์สำคัญหายไป  

### สิ่งที่คุณต้องมี
- **Aspose.Words for .NET** (ติดตั้งผ่าน NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ทำงานบน .NET Framework ด้วย)
- ตัวอย่างไฟล์ DOCX ที่อ้างอิงฟอนต์ที่ไม่มีในเครื่อง (เช่น “MyCustomFont.ttf”)
- Visual Studio, Rider หรือเครื่องมือแก้ไข C# ใด ๆ ที่คุณชอบ

> **เคล็ดลับ:** หากคุณไม่มีเอกสารที่มีฟอนต์หายไป เพียงเปลี่ยนชื่อไฟล์ฟอนต์บนระบบของคุณหรือแก้ไข XML ของ DOCX ให้อ้างอิงฟอนต์ที่ไม่มีอยู่จริง

---

## วิธีตรวจจับฟอนต์ด้วย Aspose.Words

แนวคิดหลักคือการเชื่อมต่อกับระบบคำเตือนของ Aspose.Words เมื่อไลบรารีไม่พบฟอนต์ที่ร้องขอ มันจะส่งคำเตือน `WarningType.FontSubstitution` โดยการให้การทำงานของ `IWarningCallback` ของคุณเอง คุณจึง **ตรวจจับฟอนต์** ที่ถูกสลับระหว่างกระบวนการโหลดได้

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **ทำไมวิธีนี้ถึงได้ผล:** Aspose.Words จะเรียกเมธอด `Warning` สำหรับทุกปัญหาที่ไม่เป็นวิกฤติ การเก็บอ็อบเจ็กต์ `WarningInfo` ทำให้คุณเข้าถึงประเภท, ข้อความ, และบริบทได้ครบถ้วน ซึ่งเป็นสิ่งที่คุณต้องการเพื่อ **ตรวจจับฟอนต์** ที่ถูกแทนที่

---

## วิธีจับคำเตือนขณะโหลดเอกสาร

เมื่อเรามีตัวเก็บแล้ว เราต้องบอก `LoadOptions` ให้ใช้มัน นี่คือส่วน **วิธีจับคำเตือน** ของปริศนา

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **กรณีขอบ:** หากคุณโหลดเอกสารจากสตรีม (`new Document(stream, loadOptions)`), คอลแบ็กเดียวกันก็ทำงาน—เพียงส่งสตรีมแทนพาธไฟล์

ในขณะนี้เอกสารถูกโหลดเต็มที่แล้ว แต่คำเตือนการแทนที่ฟอนต์ใด ๆ จะถูกเก็บไว้ใน `warningCollector.Warnings` อย่างปลอดภัย

---

## วิธีแสดงรายการคำเตือนและรายงานการแทนที่ฟอนต์

สุดท้าย เราจะคัดกรองคำเตือนที่เก็บมาและ **แสดงรายการคำเตือน** ที่เกี่ยวกับการแทนที่ฟอนต์ ขั้นตอนนี้จะแปลงข้อมูลดิบให้เป็นรายงานที่อ่านง่าย

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (ตัวอย่าง):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

หากเอกสารไม่มีฟอนต์หายไป ลูปจะไม่แสดงผลใด ๆ—ไม่มีอะไรต้องกังวล

---

## ตัวอย่างทำงานเต็มรูปแบบ (ทุกขั้นตอนในไฟล์เดียว)

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในโปรเจกต์คอนโซล มันเชื่อมต่อ **วิธีตรวจจับฟอนต์**, **วิธีจับคำเตือน**, **วิธีตั้งค่าคอลแบ็ก**, และ **วิธีแสดงรายการคำเตือน** ไว้ในกระบวนการเดียวที่ต่อเนื่อง

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**การรันโปรแกรมนี้** จะพิมพ์ฟอนต์ทุกตัวที่ Aspose.Words ต้องเปลี่ยน คุณสามารถส่งออกผลลัพธ์ไปยังไฟล์ล็อก, ส่งสัญญาณเตือน, หรือแม้แต่ยกเลิกการโหลดหากฟอนต์สำคัญหายไป

---

## คำถามที่พบบ่อย & จุดต้องระวัง

### จะหยุดการโหลดเมื่อฟอนต์ที่ต้องการหายไปได้อย่างไร?
คุณสามารถตรวจสอบอ็อบเจ็กต์ `WarningInfo` ภายในคอลแบ็กและโยนข้อยกเว้นเมื่อพบชื่อฟอนต์ที่กำหนด ข้อยกเว้นจะทำให้การโหลดหยุดลง ให้คุณควบคุมได้เต็มที่

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### วิธีนี้ทำงานกับ PDF หรือฟอร์แมตอื่นได้หรือไม่?
ได้ Aspose.Words ใช้โครงสร้างคำเตือนเดียวกันสำหรับ PDF, RTF, และ HTML เพียงเปลี่ยนนามสกุลไฟล์ ส่วนโค้ดที่เหลือยังคงเหมือนเดิม

### จะบันทึกคำเตือนลงไฟล์แทนคอนโซลได้อย่างไร?
แทนที่ `Console.WriteLine` ด้วยเฟรมเวิร์กล็อกที่คุณชอบ (`Serilog`, `NLog` เป็นต้น) คลาส `WarningInfo` มี `Message`, `Source` และ `Exception` ให้ใช้สำหรับบันทึกรายละเอียด

### จะส่งผลต่อประสิทธิภาพหรือไม่?
ค่าโอเวอร์เฮดน้อยมาก—Aspose.Words สร้างคำเตือนอยู่แล้ว การเพิ่มคอลแบ็กเพียงเก็บไว้ในลิสต์ซึ่งเป็น O(n) ตามจำนวนคำเตือน สำหรับเอกสารทั่วไป ผลกระทบต่ำกว่า 1 % ของเวลาโหลดทั้งหมด

---

## สรุปภาพรวม

![วิธีตรวจจับฟอนต์ใน Aspose.Words – แผนภาพการไหลของการเตือน](https://example.com/images/font-detection-diagram.png "วิธีตรวจจับฟอนต์")

*ข้อความแทนภาพ:* **วิธีตรวจจับฟอนต์** – แผนภาพแสดงขั้นตอนคอลแบ็กการเตือน, การเก็บ, และการแสดงรายการ

---

## สรุป

เราได้ครอบคลุม **วิธีตรวจจับฟอนต์** ใน Aspose.Words โดย **จับคำเตือน**, **ตั้งค่าคอลแบ็ก**, และ **แสดงรายการคำเตือน** ตัวอย่างโค้ดเต็มแสดงรูปแบบที่พร้อมใช้งานในโปรเจกต์ .NET ใด ๆ  

ต่อไปคุณอาจอยากสำรวจ:

- **วิธีจับคำเตือน** สำหรับปัญหาอื่น ๆ (เช่น ปัญหาการแปลงรูปภาพ)
- **วิธีตั้งค่าคอลแบ็ก** สำหรับเฟรมเวิร์กล็อกแบบกำหนดเอง
- **วิธีแสดงรายการคำเตือน** ข้ามหลายเอกสารในงานแบตช์
- การใช้ **Aspose.Words.Fonts.FontSettings** เพื่อกำหนดโฟลเดอร์ฟอนต์สำรอง ซึ่งสามารถลดจำนวนการแทนที่ได้ตั้งแต่แรก

ลองใช้ ปรับตัวเก็บข้อมูลให้เข้ากับสไตล์การล็อกของคุณ แล้วคุณจะไม่ต้องกังวลกับการสลับฟอนต์โดยไม่คาดคิดอีกต่อไป หากเจอข้อผิดพลาดใด ๆ แสดงความคิดเห็นด้านล่าง—ขอให้เขียนโค้ดสนุก!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}