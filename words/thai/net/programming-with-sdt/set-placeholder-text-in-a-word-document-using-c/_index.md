---
category: general
date: 2026-10-20
description: ตั้งข้อความตัวแทนในเอกสาร Word ด้วย C#. เรียนรู้วิธีเพิ่มการควบคุมและตั้งค่าตัวแทนอย่างรวดเร็วด้วย
  Aspose.Words สำหรับ .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: th
lastmod: 2026-10-20
og_description: กำหนดข้อความตัวแทนในเอกสาร Word ด้วย C# บทเรียนนี้จะแสดงวิธีเพิ่มการควบคุม
  ตั้งค่าตัวแทน และสร้างไฟล์ Word อย่างอัตโนมัติ
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: ตั้งค่าข้อความตัวแทนในเอกสาร Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: ตั้งค่าข้อความตัวแทนในเอกสาร Word ด้วย C#
url: /th/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าข้อความตัวแทนในเอกสาร Word ด้วย C#

หากคุณต้องการ **set placeholder text** ในไฟล์ Microsoft Word ขณะสร้างด้วย C# คู่มือนี้จะแสดงให้คุณเห็นอย่างชัดเจน คุณจะได้เห็นโซลูชันสั้นกระชับแบบครบวงจรที่เพิ่ม content control, กำหนดตัวแทน, และบันทึกเอกสาร—ทั้งหมดด้วย Aspose.Words for .NET

นักพัฒนาหลายคนสงสัย **how to add control** ในเอกสาร Word หรือ **how to set placeholder** โดยไม่ต้องเปิด Word ด้วยตนเอง คู่มือนี้ตอบคำถามเหล่านั้นและยังแสดงวิธีที่สะอาดในการ **generate Word C#** ไฟล์ที่พร้อมสำหรับการป้อนข้อมูลของผู้ใช้

## สิ่งที่คุณจะทำสำเร็จ

เมื่อจบคู่มือนี้คุณจะ:

* สร้างเอกสาร Word ว่างโดยโปรแกรม
* แทรก Plain‑text Structured Document Tag (SDT) ซึ่งเป็นชื่อทางเทคนิคของ content control
* กำหนด title ที่มีความหมายและข้อความ placeholder ให้กับ SDT
* บันทึกไฟล์ `.docx` ที่ได้ลงดิสก์

ไม่จำเป็นต้องใช้เครื่องมือเพิ่มเติมใด ๆ นอกจากไลบรารี Aspose.Words และสภาพแวดล้อมการพัฒนา .NET 6 (หรือใหม่กว่า)

## ข้อกำหนดเบื้องต้น

* ติดตั้ง .NET 6 SDK หรือใหม่กว่า  
* Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ .NET)  
* แพ็กเกจ NuGet ของ Aspose.Words for .NET (`Install-Package Aspose.Words`)  

> **Pro tip:** ใช้เวอร์ชันประเมินผลฟรีของ Aspose.Words หากคุณกำลังทดสอบเท่านั้น; มันจะเพิ่มลายน้ำแต่ทำงานเช่นเดียวกับเวอร์ชันที่มีลิขสิทธิ์

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า namespace

สร้างโปรเจกต์คอนโซลใหม่และเพิ่ม `using` directives ที่จำเป็น สิ่งเหล่านี้จะทำให้คลาสหลักของ Aspose.Words และ namespace markup อยู่ในขอบเขต

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*ทำไมขั้นตอนนี้สำคัญ:* การนำเข้า `Aspose.Words.Markup` ทำให้คุณเข้าถึง `StructuredDocumentTag`, `SdtType`, และ `MarkupLevel`—อ็อบเจ็กต์ที่จำเป็นสำหรับ **add control** และ **set placeholder**.

## ขั้นตอนที่ 2: สร้างเอกสารเปล่าและ DocumentBuilder

`Document` แสดงถึงไฟล์ Word ทั้งหมด, ส่วน `DocumentBuilder` ให้ตัวชี้ที่สะดวกสำหรับการแทรกองค์ประกอบ

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*ทำไมขั้นตอนนี้สำคัญ:* การเริ่มต้นด้วยเอกสารที่สะอาดทำให้แน่ใจว่าตัวแทนที่คุณตั้งจะแสดงตรงตำแหน่งที่ต้องการโดยไม่มีการแทรกแซงจากเนื้อหาที่มีอยู่

## ขั้นตอนที่ 3: สร้าง content control (Structured Document Tag)

ที่นี่เราจะสร้าง plain‑text SDT, ตั้งชื่อให้, และกำหนดข้อความ placeholder ที่ผู้ใช้จะเห็นเมื่อ control ว่าง

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*ทำไมขั้นตอนนี้สำคัญ:* คุณสมบัติ `Title` ทำให้คุณอ้างอิง control ภายหลัง (เช่น สำหรับ data binding). `PlaceholderName` คือ **set placeholder text** ที่คุณต้องการให้แสดง, ช่วยแนะนำผู้ใช้

## ขั้นตอนที่ 4: แทรก control ที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

โดยใช้ `DocumentBuilder`, แทรก SDT ลงในเอกสารที่ตำแหน่งที่ builder อยู่ในขณะนั้น

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*ทำไมขั้นตอนนี้สำคัญ:* การแทรก node จะผูก control เข้ากับ DOM ของเอกสาร หากคุณต้องการเพิ่มหลาย placeholder, คุณสามารถย้ายเคอร์เซอร์ของ builder แล้วทำซ้ำขั้นตอนนี้

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้าย, เขียนเอกสารลงดิสก์ แทนที่ `YOUR_DIRECTORY` ด้วยพาธจริงบนเครื่องของคุณ

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

เมื่อคุณเปิด `SDT.docx` ใน Microsoft Word, คุณจะเห็นกล่องข้อความอินไลน์สีเทาที่มีข้อความ **Enter name here**. การคลิกภายในกล่องจะลบ placeholder, ให้ผู้ใช้พิมพ์ชื่อลูกค้า

### ผลลัพธ์ที่คาดหวัง

| ตำแหน่งไฟล์ | ตัวอย่างเนื้อหา |
|---------------|-----------------|
| `C:\Temp\SDT.docx` | Inline placeholder **Enter name here** ภายใน plain‑text content control ที่มี title *CustomerName* |

## กรณีขอบและการปรับเปลี่ยน

| Situation | Recommended adjustment |
|-----------|------------------------|
| **Multiple placeholders** | สร้าง `StructuredDocumentTag` เพิ่มเติมโดยใช้ค่า `Title` และ `PlaceholderName` ที่แตกต่างกัน, แล้วแทรกแต่ละอันตามที่ต้องการ. |
| **Rich‑text placeholder** | ใช้ `SdtType.RichText` แทน `PlainText` เพื่อให้สามารถจัดรูปแบบภายใน placeholder ได้. |
| **Block‑level control** | เปลี่ยน `MarkupLevel.Inline` เป็น `MarkupLevel.Block` เพื่อให้ control ทำงานเหมือนย่อหน้าทั้งหมด. |
| **Placeholder not visible** | ตรวจสอบให้แน่ใจว่าการตั้งค่าการมองเห็นของเอกสารใน Word ไม่ได้ซ่อน content controls (`File → Options → Advanced → Show content controls`). |
| **Saving to a stream** | เรียก `doc.Save(stream, SaveFormat.Docx)` หากต้องการส่งไฟล์ผ่าน HTTP แทนการบันทึกลงดิสก์. |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก, วาง, และรันได้ รวมขั้นตอนทั้งหมดข้างต้นในเมธอด `Main` เดียว

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

รันโปรแกรม, เปิดไฟล์ที่สร้างขึ้น, และคุณจะเห็นข้อความ placeholder พร้อมสำหรับการป้อนข้อมูลของผู้ใช้

## คำถามที่พบบ่อย

**Q: Does this work with .NET Core?**  
A: ใช่. Aspose.Words for .NET รองรับ .NET Core, .NET 5, และ .NET 6+. โค้ดเดียวกันทำงานโดยไม่ต้องเปลี่ยนแปลง

**Q: Can I set a default value in addition to the placeholder?**  
A: ใช้ `sdt.SetText("Default value")` หลังจากสร้าง SDT. placeholder จะหายไปเมื่อมีค่าถูกตั้ง

**Q: What if I need to retrieve the entered value later?**  
A: โหลดเอกสาร, ค้นหา SDT ด้วย `Title` ของมัน (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) และอ่านค่าโดย `sdt.GetText()`

## สรุป

ตอนนี้คุณรู้วิธี **set placeholder text** ในเอกสาร Word ด้วย C# แล้ว โดยการสร้าง plain‑text `StructuredDocumentTag`, กำหนด title และ placeholder, แทรกด้วย `DocumentBuilder`, และบันทึกไฟล์, คุณสามารถ **add control** และ **generate Word C#** ไฟล์โดยโปรแกรม  

จากนี้คุณอาจสำรวจต่อ:

* การเพิ่ม rich‑text หรือ dropdown list controls (`SdtType.RichText`, `SdtType.DropDownList`).  
* การเติมหลาย placeholder จากฐานข้อมูล.  
* การแปลง `.docx` ที่สร้างเป็น PDF ด้วย Aspose.Words

ลองทดลองกับประเภท control และสไตล์ placeholder ต่าง ๆ เพื่อให้ตรงกับความต้องการของแอปพลิเคชันของคุณ. Happy coding!

## สิ่งที่คุณควรเรียนต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโครงการของคุณ

- [ตั้งค่าข้อความ Placeholder ใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [สร้างเอกสาร Word ด้วยโปรแกรม – เพิ่ม content control และ placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [วิธีเพิ่ม Content Control และสร้างเอกสาร Word ด้วย Aspose – ฉบับสมบูรณ์](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}