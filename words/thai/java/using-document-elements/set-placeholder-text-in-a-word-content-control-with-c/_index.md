---
category: general
date: 2026-11-22
description: ตั้งค่าข้อความตัวแทนในคอนเทนต์คอนโทรลของ Word ด้วย C# เรียนรู้วิธีสร้างแท็กแบบกำหนดเอง,
  แทรกคอนโทรลข้อความธรรมดา, และเพิ่มข้อความตัวแทนให้กับแท็กโดยใช้ Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: th
lastmod: 2026-11-22
og_description: ตั้งค่าข้อความตัวแทนในคอนเทนต์คอนโทรลของ Word ด้วย C#. บทเรียนนี้จะแสดงวิธีสร้างแท็กแบบกำหนดเอง,
  แทรกคอนโทรลข้อความธรรมดา, และเพิ่มข้อความตัวแทนให้กับแท็กเพื่อเพิ่มการโต้ตอบของเอกสารให้ดียิ่งขึ้น.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: ตั้งค่าข้อความตัวแทนในคอนเทนต์คอนโทรลของ Word – คู่มือ C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: ตั้งค่าข้อความตัวอย่างในคอนเทนท์คอนโทรลของ Word ด้วย C#
url: /th/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าข้อความตัวอย่างใน Word content control ด้วย C#

หากคุณต้องการ **ตั้งค่าข้อความตัวอย่าง** ในเอกสาร Word ด้วยโปรแกรมมิ่ง คู่มือนี้จะแสดงวิธีทำอย่างละเอียด โดยใช้ Aspose.Words for .NET คุณสามารถสร้างแท็กแบบกำหนดเอง แทรก plain‑text control และเพิ่ม placeholder ให้กับแท็กเพื่อให้เอกสารพร้อมสำหรับการป้อนข้อมูลของผู้ใช้

ในบทแนะนำนี้คุณจะได้เรียนรู้วิธี **สร้างแท็กแบบกำหนดเอง**, **วิธีแทรก content control**, และ **เพิ่ม placeholder ให้กับแท็ก** พร้อมกับทำให้โค้ดกระชับและพร้อมใช้งานในสภาพแวดล้อมการผลิต ไม่จำเป็นต้องใช้เครื่องมือภายนอก—เพียงโครงการ .NET และไลบรารี Aspose.Words

## ข้อกำหนดเบื้องต้น

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า ติดตั้งแล้ว  
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ทดลองฟรี)  
* ความคุ้นเคยพื้นฐานกับ C# และ Visual Studio (หรือ IDE ใดก็ได้ที่คุณชอบ)

ส่วนต่อไปนี้สมมติว่าคุณได้สร้างโปรเจกต์คอนโซลชื่อ `WordPlaceholderDemo`.

## ขั้นตอนที่ 1: ติดตั้ง Aspose.Words

เพิ่มแพ็กเกจ NuGet ลงในโปรเจกต์ของคุณ:

```bash
dotnet add package Aspose.Words
```

> **เคล็ดลับ:** ใช้ flag `--version` เพื่อระบุเวอร์ชันของแพ็กเกจให้คงที่กับรุ่นเสถียรล่าสุด (เช่น `Aspose.Words.NET 24.9`).

## ขั้นตอนที่ 2: โหลดเอกสารต้นฉบับและสร้าง `DocumentBuilder`

สิ่งแรกที่คุณทำคือโหลดไฟล์ `.docx` ที่มีอยู่ (หรือสร้างเอกสารเปล่าใหม่) และสร้างอินสแตนซ์ของ `DocumentBuilder` ตัวสร้างนี้ให้ API แบบ fluent เพื่อแทรกคอนโทรลและข้อความ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

โค้ดนี้ **เตรียมพื้นฐาน** สำหรับการแทรก content control `DocumentBuilder` ทำงานโดยตรงกับอ็อบเจ็กต์ `doc` ดังนั้นการเปลี่ยนแปลงใด ๆ ที่คุณทำจะสะท้อนโดยอัตโนมัติ

## ขั้นตอนที่ 3: สร้างแท็กแบบกำหนดเอง (StructuredDocumentTag)

ใน Word *custom tag* จะเรียกว่า **StructuredDocumentTag (SDT)** คุณสามารถมองว่าเป็น content control ที่มีตัวระบุเฉพาะ การสร้างมันเป็นหัวใจของขั้นตอน **สร้างแท็กแบบกำหนดเอง**

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

เมธอด `InsertStructuredDocumentTag` รับอาร์กิวเมนต์สองค่า:

1. ประเภทของคอนโทรล (`PlainText` ในกรณีนี้)  
2. สตริงที่ระบุแท็กอย่างเฉพาะ (`"MyTag"`)

โดยใช้ **custom tag** คุณสามารถค้นหา หรือจัดการคอนโทรลนั้นได้ในภายหลังโดยโปรแกรม

## ขั้นตอนที่ 4: ตั้งค่าชื่อเรื่องสำหรับการเข้าถึง

ชื่อเรื่องช่วยเพิ่มการเข้าถึงและทำให้คอนโทรลค้นหาได้ง่ายขึ้นใน UI ของ Word

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

คุณสมบัติ `Title` เป็นตัวเลือก แต่การเพิ่มมันเป็นแนวปฏิบัติที่ดีเมื่อคุณ **เพิ่ม placeholder ให้กับแท็ก** เพื่อประสบการณ์ผู้ใช้ที่ดียิ่งขึ้น

## ขั้นตอนที่ 5: เพิ่มข้อความ placeholder ให้กับแท็ก

ตอนนี้มาถึงเป้าหมายหลัก: **ตั้งค่าข้อความ placeholder** ข้อความนี้จะแสดงเมื่อคอนโทรลว่างเปล่า เพื่อแนะนำผู้ใช้ว่าต้องพิมพ์อะไร

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

คุณสมบัติ `PlaceholderText` คือสิ่งที่คุณต้องการเพื่อ **เพิ่ม placeholder ให้กับแท็ก** มันทำงานเหมือนคำแนะนำสีเทาที่คุณเห็นในฟิลด์ฟอร์มสมัยใหม่

## ขั้นตอนที่ 6: บันทึกเอกสารที่แก้ไขแล้ว

หลังจากตั้งค่าคอนโทรลแล้ว ให้เขียนเอกสารกลับไปยังดิสก์

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

เมื่อคุณเปิด `output.docx` ใน Microsoft Word คุณจะเห็น plain‑text content control ที่มีป้ายชื่อ “CustomerName” พร้อม placeholder “Enter name…” การคลิกภายในคอนโทรลจะทำให้ placeholder หายไปและผู้ใช้สามารถพิมพ์ได้

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ Word (`output.docx`) ที่มี plain‑text content control เพียงหนึ่งตัว  
* คอนโทรลจะแสดง placeholder “Enter name…” จนกว่าผู้ใช้จะพิมพ์อะไรบางอย่าง  
* ตัวระบุแท็กของคอนโทรลคือ `MyTag` ซึ่งคุณสามารถเรียกดูในภายหลังด้วย `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`

## ขั้นตอนที่ 7: วิธีแทรก content control ที่อื่น (ขั้นสูง)

หากคุณต้องการ **วิธีแทรก content control** ที่ตำแหน่งเฉพาะ—เช่น หลังย่อหน้าหนึ่ง—ให้ใช้เมธอด `MoveTo` ก่อนแทรกแท็ก:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

โค้ดส่วนนี้แสดงการ **แทรก plain text control** หลายครั้งในเอกสารเดียวกัน

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|---------|
| Placeholder ไม่แสดง | คอนโทรลมีข้อความอยู่แล้ว (แม้แต่ช่องว่าง) | ตรวจสอบให้แน่ใจว่า `sdt.Text` ว่างเปล่าก่อนตั้งค่า `PlaceholderText`. |
| การชนกันของตัวระบุแท็ก | ใช้ชื่อแท็กเดียวกัน (`MyTag`) ซ้ำในเอกสารเดียวกัน | ใช้ตัวระบุที่ไม่ซ้ำกันสำหรับแต่ละ `StructuredDocumentTag`. |
| ข้อยกเว้นใบอนุญาต | รันโดยไม่มีใบอนุญาต Aspose.Words ที่ถูกต้อง | ใช้ไฟล์ใบอนุญาต (`license.SetLicense("Aspose.Words.lic")`) ที่จุดเริ่มต้นของ `Main`. |
| เอกสารไม่ถูกบันทึก | ลืมเรียก `doc.Save` หรือใช้เส้นทางที่อ่าน‑อย่างเท่านั้น | ตรวจสอบว่าเส้นทางเอาต์พุตสามารถเขียนได้และเรียก `doc.Save`. |

## ตัวอย่างการทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงใน `Program.cs` มันรวมทุกขั้นตอน—**สร้างแท็กแบบกำหนดเอง**, **วิธีแทรก content control**, **เพิ่ม placeholder ให้กับแท็ก**, และ **แทรก plain text control**—ในกระบวนการเดียวกัน

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

เรียกโปรแกรมด้วย `dotnet run` หลังจากรันเสร็จ เปิด `output.docx` เพื่อตรวจสอบว่าคอนโทรลทั้งสองแสดง placeholder ของตนเอง

## ขั้นตอนต่อไป

* **ปรับแต่งรูปลักษณ์** – ใช้ `sdt.Font` เพื่อเปลี่ยนขนาดฟอนต์ สี หรือสไตล์ภายในคอนโทรล  
* **ผูกกับข้อมูล XML** – สำรวจ `sdt.XmlMapping` หากคุณต้องการให้คอนโทรลทำการแมป  

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโครงการของคุณ

- [สร้างเอกสาร Word ด้วยโปรแกรม – เพิ่ม content control และ placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [ตั้งค่าข้อความ Placeholder ใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [สร้างเอกสาร Word ใหม่และแทรก content control ด้วย C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}