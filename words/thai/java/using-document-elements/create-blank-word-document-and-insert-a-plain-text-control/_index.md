---
category: general
date: 2026-09-18
description: สร้างเอกสาร Word ว่างโดยใช้ C# แล้วตั้งค่าข้อความตัวแทน จากนั้นบันทึกเอกสารเป็นไฟล์
  docx เรียนรู้การแทรกคอนโทรลข้อความธรรมดาและเพิ่มชื่อตัวแทน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: th
lastmod: 2026-09-18
og_description: สร้างเอกสาร Word เปล่าโดยใช้ C# ตั้งค่าข้อความตัวแทน แทรกคอนโทรลข้อความธรรมดา
  เพิ่มชื่อ placeholder แล้วบันทึกเอกสารเป็นไฟล์ docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: สร้างเอกสาร Word ว่างพร้อมข้อความตัวอย่าง – คู่มือ C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: สร้างเอกสาร Word ว่างและแทรกการควบคุมข้อความธรรมดา
url: /th/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word ว่างและแทรกการควบคุมข้อความธรรมดา

หากคุณต้องการ **สร้างเอกสาร Word ว่าง** อย่างโปรแกรมมิ่ง คู่มือนี้จะแสดงวิธีทำด้วย C# คุณจะได้เรียนรู้การ **แทรกการควบคุมข้อความธรรมดา**, **ตั้งค่าข้อความตัวแทน**, **เพิ่มชื่อ placeholder**, และสุดท้าย **บันทึกเอกสารเป็น docx** ขั้นตอนทั้งหมดเป็นอิสระเต็มที่ ดังนั้นคุณสามารถคัดลอกโค้ดไปใส่ในโปรเจกต์ .NET ใดก็ได้และรันได้ทันที

การทำงานกับไฟล์ Word มักต้องการจุดเริ่มต้นที่สะอาด—เอกสารว่างที่มีการควบคุมที่ผู้ใช้ของคุณจะกรอกไว้แล้ว เมื่อจบบทเรียนนี้คุณจะได้ไฟล์ `.docx` ที่มีการควบคุมเนื้อหาข้อความธรรมดาพร้อมตัวแทนที่เป็นประโยชน์ และตามด้วยเนื้อหาปกติ

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดยังทำงานกับ .NET Framework 4.6+ ด้วย)
- การอ้างอิงไปยังไลบรารี **Aspose.Words for .NET** (สามารถติดตั้งผ่าน NuGet `Install-Package Aspose.Words`)
- ความคุ้นเคยพื้นฐานกับแอปพลิเคชันคอนโซล C#
- สิทธิ์การเขียนในโฟลเดอร์ผลลัพธ์ที่คุณระบุใน `doc.save(...)`

## สิ่งที่คุณจะสร้าง

เอกสารสุดท้าย (`SDT.docx`) มี:

1. ไฟล์ Word ว่าง (**blank Word document** ที่คุณสร้าง)
2. การควบคุมเนื้อหาข้อความธรรมดา (ขั้นตอน **insert plain text control**)
3. ข้อความตัวแทนที่ปรากฏภายในการควบคุมจนกว่าผู้ใช้จะพิมพ์อะไรบางอย่าง (ขั้นตอน **set placeholder text**)
4. ชื่อ placeholder ที่สามารถใช้สำหรับการเข้าถึงแบบโปรแกรมในภายหลัง (ขั้นตอน **add placeholder name**)
5. บรรทัดข้อความปกติหลังจากการควบคุม เพื่อแสดงว่าข้อความธรรมดาสามารถตามมาได้

## ขั้นตอน 1: สร้างเอกสาร Word ว่าง

การดำเนินการแรกคือการสร้างอ็อบเจ็กต์ `Document` ว่าง ซึ่งอ็อบเจ็กต์นี้แทนเอกสารใหม่ทั้งหมด, **blank Word document** ในหน่วยความจำ

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*ทำไมเรื่องนี้ถึงสำคัญ:* `Document` ว่างให้คุณควบคุมทุกองค์ประกอบที่คุณเพิ่มได้อย่างเต็มที่ เพื่อให้แน่ใจว่าไม่มีสไตล์หรือส่วนที่ซ่อนอยู่แทรกแซงการควบคุมเนื้อหาที่คุณจะใส่ในภายหลัง

## ขั้นตอน 2: เริ่มต้น DocumentBuilder

`DocumentBuilder` เป็นคลาสช่วยเหลือที่ให้คุณเขียนลงใน `Document` มันติดตามตำแหน่งเคอร์เซอร์ปัจจุบันและให้เมธอดสำหรับแทรกวัตถุต่าง ๆ ของ Word

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*ทำไมเรื่องนี้ถึงสำคัญ:* การใช้ `DocumentBuilder` ทำให้กระบวนการเพิ่ม **plain‑text control** ง่ายขึ้น เพราะตัวสร้างรู้จุดแทรกที่แน่นอน

## ขั้นตอน 3: แทรกการควบคุมข้อความธรรมดา

ตอนนี้เราจะเพิ่ม **plain‑text content control** (หรือที่เรียกว่า Structured Document Tag, หรือ SDT) ประเภทการควบคุม `StructuredDocumentTagType.PLAIN_TEXT` บอก Word ให้ถือเนื้อหาเป็นข้อความธรรมดา ไม่ใช่รูปแบบที่ซับซ้อน

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*ทำไมเรื่องนี้ถึงสำคัญ:* เมธอด `InsertStructuredDocumentTag` สร้างการควบคุมและคืนค่าอ้างอิง (`sdt`) ที่คุณสามารถกำหนดค่าเพิ่มเติมได้ เช่น การเพิ่มข้อความตัวแทนหรือชื่อที่กำหนดเอง

## ขั้นตอน 4: ตั้งค่าข้อความตัวแทนและเพิ่มชื่อ placeholder

ข้อความตัวแทนให้ผู้ใช้สัญญาณภาพว่าต้องพิมพ์อะไร ขั้นตอน **add placeholder name** กำหนดตัวระบุแบบโปรแกรมที่คุณสามารถเรียกดูในภายหลังด้วย `doc.GetChildNodes` หรือ API ที่คล้ายกัน

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*ทำไมเรื่องนี้ถึงสำคัญ:* `SetPlaceholderName` ควบคุมข้อความคำแนะนำสีเทาที่แสดงภายในการควบคุมเนื้อหา การตั้งค่า `Tag` (การกระทำ **add placeholder name**) ทำให้คุณสามารถหาการควบคุมนั้นในโครงสร้างเอกสารโดยไม่ต้องสแกนไฟล์ทั้งหมด

## ขั้นตอน 5: เพิ่มเนื้อหาปกติหลังจากการควบคุม

เพื่อพิสูจน์ว่าเอกสารดำเนินต่อไปอย่างปกติหลังการควบคุม เราจะเขียนบรรทัดข้อความง่าย ๆ

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## ขั้นตอน 6: บันทึกเอกสารเป็น docx

สุดท้าย เราจะบันทึกเอกสารในหน่วยความจำลงดิสก์ นี่คือการทำงาน **save document as docx** ที่สร้างไฟล์ที่คุณสามารถเปิดใน Microsoft Word

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*ทำไมเรื่องนี้ถึงสำคัญ:* การใช้รูปแบบ `.docx` ทำให้เข้ากันได้สูงสุดกับเวอร์ชัน Word สมัยใหม่, Google Docs, และเครื่องมืออื่น ๆ ที่เข้ากันกับ Office

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอกไปยังโปรเจกต์ console‑app ได้ แทนที่ `YOUR_DIRECTORY` ด้วยเส้นทางโฟลเดอร์จริงบนเครื่องของคุณ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

- เปิด `SDT.docx` ใน Word จะเห็นกล่องสีเทาว่างพร้อมข้อความ **Enter text…** ด้านใน
- กล่องนั้นเป็นการควบคุมเนื้อหาข้อความธรรมดา; คุณสามารถพิมพ์โดยตรงลงในนั้นได้
- ด้านล่างกล่อง จะมีบรรทัด **After the tag.** ปรากฏเป็นข้อความย่อหน้าปกติ

หากข้อความตัวแทนไม่ปรากฏ ตรวจสอบว่าคุณใช้ Aspose.Words เวอร์ชันล่าสุด (v23.1 หรือใหม่กว่า) และเอกสารเปิดด้วย Word เวอร์ชันที่รองรับการควบคุมเนื้อหา (Word 2007+)

## ความแปรผันทั่วไปและกรณีขอบ

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Multiple placeholders** | เรียก `InsertStructuredDocumentTag` อีกครั้งโดยใช้ tag ID และชื่อ placeholder ที่แตกต่างกัน. |
| **Rich‑text control** | ใช้ `StructuredDocumentTagType.RichText` แทน `PlainText`. |
| **Setting default text** | หลังการแทรก ให้กำหนด `sdt.Text = "Default value";` – ข้อความนี้จะแทนที่ placeholder เมื่อเอกสารโหลด. |
| **Saving to a stream** | แทนที่ `doc.Save(outputPath);` ด้วย `doc.Save(stream, SaveFormat.Docx);` เพื่อส่งไฟล์ผ่าน HTTP. |
| **Changing placeholder color** | ใช้ `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (ต้องมี `using System.Drawing`). |

## เคล็ดลับระดับมืออาชีพ

- **Reuse the tag ID**: การรักษา tag (`MyTag`) ให้สอดคล้องกันในทุกเอกสารทำให้คุณสามารถทำการเติมข้อมูลอัตโนมัติในภายหลังด้วย `doc.Range.Replace` หรือ `StructuredDocumentTagCollection`.
- **Avoid hard‑coded paths**: ใช้ `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` เพื่อกำหนดตำแหน่งผลลัพธ์ที่พกพาได้.
- **Performance**: หากคุณต้องการสร้างเอกสารหลายพันไฟล์ ให้สร้างเทมเพลต `Document` เพียงไฟล์เดียวที่มี SDT อยู่แล้ว จากนั้นทำการคลอนด้วย `doc.Clone()` สำหรับแต่ละรอบ.

## สรุป

ตอนนี้คุณรู้วิธี **create blank Word document**, **insert plain text control**, **set placeholder text**, **add placeholder name**, และ **save document as docx** ด้วย Aspose.Words for .NET รูปแบบนี้เป็นพื้นฐานสำหรับสร้างเทมเพลต Word ที่มีแบบฟอร์ม, รายงานอัตโนมัติ, หรือโซลูชันใด ๆ ที่ต้องการ placeholder ที่ผู้ใช้สามารถแก้ไขได้

คุณสามารถทดลองใช้ประเภทการควบคุมอื่น ๆ, รวมหลาย placeholder, หรือรวมโค้ดนี้เข้าใน Web API ที่ส่งไฟล์ `.docx` ที่สร้างขึ้นโดยตรงให้ผู้เรียกใช้ได้อย่างอิสระ สำหรับขั้นตอนต่อไป ลองสำรวจ **populate a content control with data programmatically** หรือ **convert the generated Word file to PDF** ด้วยฟีเจอร์การแปลงในตัวของ Aspose.Words. Happy coding!

## สิ่งที่คุณควรเรียนต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ

- [แทรกฟิลด์ฟอร์มข้อความในเอกสาร Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [สร้างเอกสาร Word พร้อมตารางโดยใช้ Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [สร้างเอกสาร Word พร้อมส่วนหัวและส่วนท้ายโดยใช้ Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}