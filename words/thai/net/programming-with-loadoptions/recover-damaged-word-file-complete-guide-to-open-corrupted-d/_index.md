---
category: general
date: 2026-01-03
description: กู้ไฟล์ Word ที่เสียหายอย่างรวดเร็วด้วย Aspose.Words LoadOptions. เรียนรู้วิธีเปิดไฟล์
  DOCX ที่เสียหายและวิธีนับจำนวนหน้าใน C#
draft: false
keywords:
- recover damaged word file
- how to get page count
- open corrupted docx
- aspose words load options
language: th
og_description: กู้คืนไฟล์ Word ที่เสียหายด้วย Aspose.Words LoadOptions คู่มือนี้แสดงวิธีเปิดไฟล์
  DOCX ที่เสียหายและวิธีนับจำนวนหน้าใน C#
og_title: กู้ไฟล์ Word ที่เสีย – เปิดไฟล์ DOCX ที่เสียและดึงจำนวนหน้า
tags:
- Aspose.Words
- C#
- Document Recovery
title: กู้คืนไฟล์ Word ที่เสีย – คู่มือเต็มสำหรับเปิดไฟล์ DOCX ที่เสียและนับจำนวนหน้า
url: /th/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# กู้คืนไฟล์ Word ที่เสีย – คู่มือเต็ม

เคยลอง **กู้คืนไฟล์ Word ที่เสีย** แล้วเจออุปสรรคเพราะเอกสารไม่เปิดหรือไม่? นั่นเป็นช่วงเวลาที่น่าหงุดหงิด โดยเฉพาะเมื่อไฟล์นั้นมีเนื้อหาที่สำคัญ ในบทเรียนนี้เราจะสาธิตอย่างละเอียดว่า **เปิดไฟล์ DOCX ที่เสีย** อย่างไรโดยใช้ Aspose.Words LoadOptions และจากนั้นจะแสดง **วิธีดึงจำนวนหน้า** หลังจากไฟล์โหลดสำเร็จ ไม่ต้องเดา หรือทำการลอง‑และ‑ผิดอีกต่อไป—เพียงโซลูชันที่ชัดเจนและสามารถรันได้

เราจะครอบคลุมทุกอย่างตั้งแต่การตั้งค่าไลบรารี Aspose.Words, การกำหนด LoadOptions ที่เหมาะสม, การจัดการกรณีขอบ, และสุดท้ายการดึงจำนวนหน้า เมื่อเสร็จสิ้นคุณจะได้สคริปต์ที่พร้อมใช้งานในโปรเจกต์ .NET ใดก็ได้

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบว่าคุณมี:

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ทำงานกับ .NET Core ด้วย)
- ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคุณสามารถเริ่มด้วยรุ่นทดลองฟรี)
- Visual Studio 2022 หรือ IDE ที่รองรับ C#
- ไฟล์ `Corrupted.docx` ที่เสียและต้องการกู้คืน

ถ้าคุณมีทั้งหมดนี้แล้ว—ดีมาก—มาเริ่มกันเลย

## ขั้นตอนที่ 1: ติดตั้ง Aspose.Words และเพิ่ม Using Directives

อันดับแรกคุณต้องติดตั้งแพ็กเกจ NuGet เปิดเทอร์มินัลในโฟลเดอร์โปรเจกต์แล้วรัน:

```bash
dotnet add package Aspose.Words
```

เมื่อติดตั้งเสร็จ ให้เพิ่ม namespace ที่จำเป็นที่ส่วนหัวของไฟล์ C# ของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **เคล็ดลับ:** หากคุณใช้ไลเซนส์รุ่นทดลอง ให้เรียก `License license = new License(); license.SetLicense("Aspose.Total.lic");` ตั้งแต่ต้นใน `Main` เพื่อหลีกเลี่ยงข้อความลายน้ำ

## ขั้นตอนที่ 2: กำหนดค่า LoadOptions เพื่อกู้คืนไฟล์ Word ที่เสีย

หัวใจของ **การกู้คืนไฟล์ Word ที่เสีย** อยู่ที่อ็อบเจกต์ `LoadOptions` โดยตั้งค่า `RecoveryMode` เป็น `Lenient` Aspose.Words จะพยายามโหลดข้อมูลที่สามารถอ่านได้และข้ามส่วนที่อ่านไม่ได้แทนที่จะโยนข้อยกเว้น

```csharp
// Step 2: Prepare load options for lenient recovery
LoadOptions loadOptions = new LoadOptions
{
    // Lenient mode tells Aspose to salvage what it can.
    RecoveryMode = RecoveryMode.Lenient
};
```

ทำไมต้องใช้ `Lenient`? ในโหมด *strict* ไลบรารีจะหยุดทำงานเมื่อเจอความเสียหายแรก ซึ่งหมายความว่าคุณจะสูญเสียทุกอย่าง `Lenient` ทำหน้าที่เป็นเครือข่ายความปลอดภัยที่มักจะกู้คืนข้อความ ตาราง และแม้กระทั่งรูปภาพส่วนใหญ่กลับมา

## ขั้นตอนที่ 3: เปิดไฟล์ DOCX ที่เสียโดยใช้ตัวเลือกที่กำหนดไว้

ตอนนี้เราจะโหลดไฟล์จริง ๆ แทนที่ `YOUR_DIRECTORY` ด้วยพาธที่ไฟล์เสียของคุณอยู่

```csharp
// Step 3: Load the corrupted document with our recovery settings
string filePath = @"YOUR_DIRECTORY\Corrupted.docx";

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
```

หากไฟล์เสียอย่างรุนแรง คุณยังคงจะได้อ็อบเจกต์ `Document` แต่บางส่วนอาจหายไป นั่นคือเหตุผลที่เราห่อการโหลดด้วย `try/catch` เพื่อให้แอปไม่หยุดทำงานและคุณสามารถบันทึกปัญหาได้อย่างแม่นยำ

## ขั้นตอนที่ 4: วิธีดึงจำนวนหน้าจากเอกสารที่กู้คืนแล้ว

เมื่อเอกสารถูกโหลดเข้าสู่หน่วยความจำ การดึงจำนวนหน้ากลายเป็นเรื่องง่าย Aspose.Words คำนวณการแบ่งหน้าแบบตามความต้องการ ดังนั้นการเรียกจึงใช้ทรัพยากรน้อย

```csharp
// Step 4: Retrieve the page count
int pageCount = document.PageCount;
Console.WriteLine($"Recovered document contains {pageCount} page(s).");
```

บรรทัดเดียวนี้ตอบคำถาม **วิธีดึงจำนวนหน้า** แม้สำหรับไฟล์ที่เคยเสีย `PageCount` จะสะท้อนการจัดหน้า หลังจากไลบรารีได้ทำการพาร์สเนื้อหาที่มีอยู่ทั้งหมดแล้ว

## ขั้นตอนที่ 5: บันทึกเอกสารที่ซ่อมแล้ว (ไม่บังคับ)

หากต้องการเก็บเวอร์ชันที่กู้คืนไว้ เพียงบันทึกไปยังตำแหน่งใหม่ Aspose.Words รองรับหลายรูปแบบ แต่เราจะใช้ DOCX เพื่อความคุ้นเคย

```csharp
// Step 5: Save the cleaned-up document
string outputPath = @"YOUR_DIRECTORY\Recovered.docx";
document.Save(outputPath);
Console.WriteLine($"Recovered document saved to {outputPath}");
```

การบันทึกยังทำให้มีการประมวลผลการจัดหน้าอีกครั้ง ซึ่งบางครั้งอาจเปิดเผยปัญหาเพิ่มเติมที่ไม่เห็นในระหว่างการตรวจสอบในหน่วยความจำ

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมทั้งหมดที่เชื่อมโยงทุกขั้นตอนเข้าด้วยกัน คัดลอก‑วางลงในแอปคอนโซลใหม่แล้วรัน

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose license here
        // var license = new License();
        // license.SetLicense("Aspose.Total.lic");

        // 1️⃣ Set up load options for lenient recovery
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Lenient
        };

        // 2️⃣ Path to the corrupted DOCX
        string inputPath = @"YOUR_DIRECTORY\Corrupted.docx";

        // 3️⃣ Attempt to load the document
        Document doc;
        try
        {
            doc = new Document(inputPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to open file: {ex.Message}");
            return;
        }

        // 4️⃣ Get the page count (how to get page count)
        int pages = doc.PageCount;
        Console.WriteLine($"✅ Recovered document has {pages} page(s).");

        // 5️⃣ Save the repaired version (optional)
        string outputPath = @"YOUR_DIRECTORY\Recovered.docx";
        doc.Save(outputPath);
        Console.WriteLine($"💾 Recovered file saved at {outputPath}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (สมมติว่าไฟล์มีเนื้อหา):

```
✅ Recovered document has 12 page(s).
💾 Recovered file saved at C:\Docs\Recovered.docx
```

หากไฟล์อ่านไม่ได้เลย คุณจะเห็นข้อความข้อผิดพลาดจากบล็อก `catch` แทน

## กรณีขอบทั่วไป & วิธีจัดการ

| สถานการณ์ | สาเหตุ | วิธีแก้แนะนำ |
|-----------|--------|---------------|
| **ไฟล์โยน `BadImageFormatException`** | ไฟล์ไม่ได้เป็น DOCX จริง (อาจเป็น `.doc` เก่า หรือไฟล์ zip ที่เปลี่ยนชื่อ) | ตรวจสอบนามสกุลไฟล์ หรือใช้ `LoadOptions.LoadFormat = LoadFormat.Doc` สำหรับไฟล์ Word รุ่นเก่า |
| **โหลดได้เพียงบางส่วนของเอกสาร** | บางส่วนของ XML เสียหายจนไม่สามารถกู้คืน | หลังโหลด ตรวจสอบ `doc.GetChildNodes(NodeType.Any, true).Count` เพื่อดูว่าโหนดใดเหลืออยู่ คุณยังสามารถดึงข้อความด้วย `doc.GetText()` เพื่อตรวจสอบความสมบูรณ์อย่างรวดเร็ว |
| **จำนวนหน้าเป็นศูนย์** | เอกสารถูกโหลดแต่ไม่มีข้อมูลการจัดหน้า (เช่น มีเฉพาะข้อความดิบ) | เรียก `doc.UpdatePageLayout();` ก่อนอ่าน `PageCount` เพื่อบังคับให้ทำการจัดหน้า |
| **ประสิทธิภาพช้ากับไฟล์ขนาดใหญ่** | การกู้คืนแบบ Lenient อาจใช้ CPU มากสำหรับเอกสารใหญ่ | พิจารณาโหลดเฉพาะส่วนที่ต้องการโดยใช้ `LoadOptions.LoadFormat` และ `LoadOptions.Password` หากจำเป็น |

## เคล็ดลับการใช้ Aspose.Words LoadOptions

- **RecoveryMode.Lenient** เป็นตัวเลือกหลักสำหรับไฟล์เสีย; **RecoveryMode.Strict** มีประโยชน์เมื่อคุณต้องการบังคับให้ไฟล์มีความสมบูรณ์
- สามารถผสาน `LoadOptions` กับ **Password** ได้หากไฟล์เสียยังถูกป้องกันด้วยรหัสผ่าน
- ใช้ `Document.UpdatePageLayout()` เมื่อคุณแก้ไขเอกสารหลังการโหลด (เช่น เพิ่ม/ลบโหนด) ก่อนตรวจสอบจำนวนหน้าอีกครั้ง

## คำถามที่พบบ่อย

**ถาม: วิธีนี้ทำงานกับไฟล์ .doc (binary) ได้หรือไม่?**  
ตอบ: ได้ แต่ต้องตั้งค่า `LoadOptions.LoadFormat = LoadFormat.Doc` ก่อนเรียกคอนสตรัคเตอร์

**ถาม: สามารถกู้รูปภาพที่ฝังอยู่ในไฟล์เสียได้หรือไม่?**  
ตอบ: ส่วนใหญ่โหมด Lenient จะรักษารูปภาพไว้ หลังโหลด คุณสามารถวนลูป `doc.GetChildNodes(NodeType.Shape, true)` เพื่อดึงรูปภาพออกมา

**ถาม: มีวิธีบันทึกว่ามีส่วนใดบ้างที่ถูกข้ามหรือไม่?**  
ตอบ: Aspose.Words จะโยน `DocumentLoadingException` พร้อมรายละเอียด คุณสามารถสมัครรับเหตุการณ์ `Document.Loading` เพื่อเก็บข้อความเหล่านั้นได้

## สรุป

เราได้อธิบายวิธีแก้ปัญหาแบบครบวงจรสำหรับ **การกู้คืนไฟล์ Word ที่เสีย**, **การเปิด DOCX ที่เสีย**, และ **วิธีดึงจำนวนหน้า** ด้วย Aspose.Words LoadOptions ใน C# โดยการตั้งค่า `RecoveryMode.Lenient` ให้ไลบรารีทำงานหนักส่วนใหญ่ ส่วนโค้ดรอบข้างจะช่วยให้คุณควบคุมการจัดการข้อผิดพลาดและบันทึกไฟล์ได้ตามต้องการ

ลองทดลองเพิ่มเติม: เปิดไฟล์ `.doc` รุ่นเก่า, ปรับโหมดการกู้คืน, หรือทำการประมวลผลแบบแบตช์ของไฟล์เสียหลายไฟล์ แนวคิดที่คุณเรียนรู้—การโหลดด้วยตัวเลือก, การจัดการข้อยกเว้น, การดึงข้อมูลการแบ่งหน้า—สามารถนำไปใช้ซ้ำได้ในงานประมวลผลเอกสารหลากหลายประเภท

มีคำถามเพิ่มเติมเกี่ยวกับ Aspose.Words, การกู้คืนเอกสาร, หรือการดึงจำนวนหน้า? แสดงความคิดเห็นด้านล่างหรือเยี่ยมชมเอกสารอย่างเป็นทางการของ Aspose เพื่อศึกษาเชิงลึกเพิ่มเติม ขอให้สนุกกับการเขียนโค้ดและไฟล์ของคุณคงอยู่ในสภาพดี! 

---

![Screenshot of a recovered Word document showing page numbers – recover damaged word file example](https://example.com/images/recover-damaged-word-file.png "recover damaged word file")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}