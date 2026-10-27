---
category: general
date: 2026-10-26
description: เรียนรู้วิธีแทรกการควบคุมเนื้อหาแบบข้อความธรรมดาโดยใช้ Aspose.Words ใน
  C# คู่มือขั้นตอนต่อขั้นตอนที่ครอบคลุม StructuredDocumentTag, ชื่อเรื่อง, และรหัสแท็ก
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: th
lastmod: 2026-10-26
og_description: แทรกการควบคุมเนื้อหาแบบข้อความธรรมดาโดยใช้ Aspose.Words ใน C# ทำตามคำแนะนำนี้เพื่อเพิ่มหัวเรื่อง
  รหัสแท็ก และปรับแต่งลักษณะ.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: แทรกการควบคุมเนื้อหาแบบข้อความธรรมดาใน Word ด้วย C# – คู่มือฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีแทรกการควบคุมเนื้อหาแบบข้อความธรรมดาในเอกสาร Word ด้วย C#
url: /th/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรก plain text content control ในเอกสาร Word ด้วย C#

หากคุณต้องการ **แทรก plain text content control** ลงในไฟล์ Word, บทแนะนำนี้จะแสดงให้คุณเห็นอย่างชัดเจนว่าทำอย่างไรโดยใช้ Aspose.Words for .NET ไม่ว่าคุณจะกำลังสร้างบริการสร้างเอกสารอัตโนมัติหรือทำแบบฟอร์มอัตโนมัติ ขั้นตอนต่อไปนี้จะช่วยให้คุณเพิ่มพื้นที่ที่สามารถใช้ซ้ำและแก้ไขได้ซึ่งผู้ใช้ปลายทางสามารถกรอกข้อมูลได้

คุณจะได้เรียนรู้วิธีสร้าง `Document`, ใช้ `DocumentBuilder` เพื่อวาง Structured Document Tag (SDT) แบบ plain‑text, ตั้งชื่อหัวเรื่องที่เป็นมิตร, และกำหนดตัวระบุ tag ที่ไม่ซ้ำกัน คู่มือยังอธิบายการปรับเปลี่ยนทั่วไป—เช่นการเปลี่ยนลักษณะหรือการซ้อนกันของคอนโทรล—เพื่อให้คุณสามารถปรับใช้โซลูชันกับโครงการใดก็ได้

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+)
- ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ประเมินผลฟรี)
- Visual Studio 2022 หรือ IDE ที่รองรับ C# ใดก็ได้
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#

> **เคล็ดลับ:** หากคุณใช้รุ่นประเมินผลฟรี จำไว้ว่าเอกสารผลลัพธ์จะมีลายน้ำ เวอร์ชันที่มีลิขสิทธิ์จะลบออกโดยอัตโนมัติ.

## วิธีแทรก plain text content control ด้วย Aspose.Words

หัวใจของโซลูชันคือกระบวนการสามขั้นตอน:

1. **สร้าง `Document` และ `DocumentBuilder`.**  
2. **แทรก plain‑text Structured Document Tag (SDT) พร้อมลักษณะเริ่มต้น.**  
3. **กำหนดชื่อหัวเรื่องและตัวระบุ tag ให้กับ SDT.**  

แต่ละขั้นตอนจะอธิบายด้านล่างพร้อมโค้ดที่สมบูรณ์และสามารถรันได้.

### ขั้นตอนที่ 1: เริ่มต้น Document และ Builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` แทนไฟล์ Word ทั้งหมด, ส่วน `DocumentBuilder` มีเมธอดเช่น `InsertParagraph`, `InsertImage`, และที่สำคัญสำหรับบทแนะนำนี้คือ `InsertStructuredDocumentTag`. การเริ่มต้นพวกมันก่อนจะให้คุณมีพื้นที่สำหรับวาง **plain text content control**.

### ขั้นตอนที่ 2: แทรก plain‑text content control (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` บอก Aspose.Words ให้สร้าง **plain text content control** ซึ่งทำงานเหมือนกล่องข้อความง่าย ๆ ที่ผู้ใช้สามารถแก้ไขได้ `SdtAppearance.Default` แสดงคอนโทรลด้วยพื้นหลังสีอ่อน ทำให้เห็นชัดเจนในเอกสารว่าพื้นที่นี้สามารถแก้ไขได้.

> **ทำไมต้องใช้ `SdtAppearance.Default`?**  
> ลักษณะเริ่มต้นเป็นสไตล์ที่เข้ากันได้ที่สุดในหลายเวอร์ชันของ Word หากคุณต้องการลุคไม่มีขอบ คุณสามารถเปลี่ยนเป็น `SdtAppearance.Hidden` ในภายหลัง.

### ขั้นตอนที่ 3: ตั้งชื่อหัวเรื่องและตัวระบุ tag

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) ปรากฏในแถบ *Content Controls* ของ Word, ช่วยให้ผู้ใช้เข้าใจวัตถุประสงค์ของฟิลด์  
- **Tag** (`sdt.Tag`) เป็นตัวระบุที่มุ่งเน้นนักพัฒนา ซึ่งคุณสามารถเรียกดูภายหลังด้วย `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`  
- **PlaceholderName** ให้ข้อความแนะนำสีเทาเมื่อคอนโทรลว่าง, ปรับปรุงประสบการณ์ผู้ใช้  

โค้ดสแนปช็อตที่สมบูรณ์ด้านบนเป็นโปรแกรมที่ทำงานอิสระที่คุณสามารถคอมไพล์และรันได้ หลังจากทำงาน `output.docx` จะมี plain‑text content control เพียงหนึ่งรายการที่มีชื่อหัวเรื่อง *MyTag* และ tag *TagId*.

![แผนภาพแสดงการแทรก plain text content control ในเอกสาร Word](image.png){alt="แทรก plain text content control"}

## ทำความเข้าใจ StructuredDocumentTag (SDT) และคุณสมบัติของมัน

**Structured Document Tag** (SDT) คือโมเดลอ็อบเจ็กต์พื้นฐานสำหรับคอนโทรลของ Word คุณสมบัติที่สำคัญที่สุดสำหรับการแทรก plain text control มีดังนี้:

| คุณสมบัติ | วัตถุประสงค์ | ค่าที่พบบ่อย |
|----------|---------------|----------------|
| `SdtType` | กำหนดประเภทของคอนโทรล (plain text, rich text, picture, ฯลฯ) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | สไตล์การแสดงผลของคอนโทรล | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | ชื่อที่มนุษย์อ่านได้แสดงในแถบ *Content Controls* | Any short string |
| `Tag` | ตัวระบุที่เครื่องอ่านได้ใช้ในโค้ด | Alphanumeric string |
| `PlaceholderName` | ข้อความที่แสดงเมื่อคอนโทรลว่าง | Custom hint text |

เมื่อคุณตั้งค่า `SdtType.PlainText`, Word จะจำกัดเนื้อหาให้เป็นอักขระธรรมดาเท่านั้น ป้องกันการจัดรูปแบบแบบ rich ทำให้คอนโทรลนี้เหมาะสำหรับฟิลด์ฟอร์มง่าย ๆ เช่น *Name*, *Email*, หรือ *Phone Number*.

### การปรับเปลี่ยนที่คุณอาจต้องการ

| สถานการณ์ | การเปลี่ยนแปลงโค้ด |
|-----------|-------------------|
| **ไม่มีการแรเงา** (ไม่มีขอบ) | ใช้ `SdtAppearance.Hidden` แทน `Default`. |
| **ฟิลด์แบบอ่านอย่างเดียว** | หลังจากแทรก, ตั้งค่า `sdt.LockContentControl = true`. |
| **เติมข้อมูลล่วงหน้า** | ตั้งค่า `sdt.Text = "John Doe";` หลังจากสร้าง tag. |
| **หลายคอนโทรลในตาราง** | แทรก SDT ภายในเซลล์ตารางโดยใช้ `builder.InsertCell();` ก่อนเรียก `InsertStructuredDocumentTag`. |

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

1. **ลืมตั้งค่า title** – Word ยังจะสร้างคอนโทรล, แต่ผู้ใช้จะไม่เห็นคำอธิบายที่มีความหมายในแถบ *Content Controls*. ควรกำหนด `sdt.Title` เสมอ.  
2. **ใช้ `SdtType` ผิด** – หากคุณต้องการ plain text แต่เลือก `RichText` โดยบังเอิญ คอนโทรลจะอนุญาตการจัดรูปแบบ ซึ่งอาจทำให้การประมวลผลต่อเนื่องล้มเหลว ตรวจสอบค่า enum อีกครั้ง.  
3. **บันทึกลงโฟลเดอร์ที่อ่านอย่างเดียว** – การเรียก `doc.Save` จะทำให้เกิด `UnauthorizedAccessException`. ตรวจสอบให้แน่ใจว่าไดเรกทอรีเป้าหมายสามารถเขียนได้หรือใช้ `Path.GetTempPath()` สำหรับการทดสอบ.  
4. **ไม่ได้ใส่ลิขสิทธิ์** – หากไม่มีลิขสิทธิ์ที่ถูกต้อง เอกสารผลลัพธ์จะมีลายน้ำการประเมินค่า ใช้ลิขสิทธิ์ตั้งแต่ต้นในโปรแกรมของคุณ:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมทั้งหมดพร้อมคัดลอกและวางลงในโปรเจกต์คอนโซลใหม่.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** การเปิด `output.docx` ใน Microsoft Word จะเห็นบรรทัดข้อความ *“Please fill in the following field:”* ตามด้วยพื้นที่สีเทาอ่อนที่มีกรอบและป้ายชื่อ *MyTag*. Placeholder *Enter your text here* จะปรากฏเป็นสีเทาอ่อนจนกว่าผู้ใช้จะพิมพ์.

## สรุป

ตอนนี้คุณรู้วิธี **แทรก plain text content control** ลงในเอกสาร Word ด้วย Aspose.Words for .NET แล้ว บทแนะนำได้ครอบคลุมการเริ่มต้น `Document`, การแทรก `StructuredDocumentTag` ชนิด `PlainText`, และการปรับแต่ง title, tag, และ placeholder. ด้วยความเข้าใจตัวเลือก `SdtAppearance` และข้อผิดพลาดทั่วไป คุณสามารถสร้างฟอร์ม, แม่แบบ, และรายงานอัตโนมัติที่พึ่งพาคอนโทรลที่แก้ไขได้อย่างมั่นใจ.

### ขั้นตอนต่อไป?

- สำรวจประเภท SDT อื่น ๆ เช่น `RichText` หรือ `ComboBox` สำหรับ dropdown.  
- รวมหลาย content control ไว้ในตารางหรือทำซ้ำโดยใช้ `RepeatingSection`.  
- ใช้ `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` เพื่ออ่านหรือแก้ไขค่าคอนโทรลโดยโปรแกรม.

คุณสามารถทดลองกับการปรับเปลี่ยนที่แสดงไว้ข้างต้นและผสานรูปแบบนี้เข้ากับกระบวนการสร้างเอกสารขนาดใหญ่ของคุณได้อย่างอิสระ. Happy coding!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการนำไปใช้แบบอื่นในโครงการของคุณ.

- [วิธีสร้าง content control ด้วย C# และ Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [สร้างเอกสาร Word ใหม่และแทรก content control ด้วย C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [เพิ่มเนื้อหาโดยใช้ Document Builder ใน Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}