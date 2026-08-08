---
category: general
date: 2026-08-07
description: แทรกรูปร่างสี่เหลี่ยมใน C# ด้วย Aspose.Words และเรียนรู้วิธีซ่อนรูป,
  ตั้งค่าสีเติม, และเพิ่มรูปสี่เหลี่ยมลงในเอกสาร Word อย่างมีประสิทธิภาพ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: th
lastmod: 2026-08-07
og_description: แทรกรูปสี่เหลี่ยมในเอกสาร Word ด้วย C# เรียนรู้วิธีซ่อนรูป, ตั้งค่าสีเติม,
  และเพิ่มรูปสี่เหลี่ยมโดยใช้ Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: แทรกรูปสี่เหลี่ยมใน C# – บทแนะนำ Aspose.Words อย่างครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: แทรกรูปสี่เหลี่ยมผืนผ้าใน C# ด้วย Aspose.Words – คู่มือแบบขั้นตอนต่อขั้นตอน
url: /th/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกรูปสี่เหลี่ยมผืนผ้าใน C# ด้วย Aspose.Words – คู่มือทีละขั้นตอน

หากคุณต้องการ **insert rectangle shape** ในเอกสาร Word จาก C# คู่มือนี้จะแสดงให้คุณเห็นอย่างชัดเจนว่าต้องทำอย่างไร คุณจะได้เห็นวิธีตั้งค่าสีเติม, ซ่อนรูปเพื่อไม่ให้ปรากฏในเลย์เอาต์สุดท้าย, และบันทึกไฟล์—ทั้งหมดด้วยเพียงไม่กี่บรรทัดของโค้ด

ในส่วนต่อไปนี้ เราจะครอบคลุมทุกอย่างที่คุณต้องรู้: ข้อกำหนดเบื้องต้น, รายการโค้ดเต็ม, คำอธิบายแต่ละขั้นตอน, และเคล็ดลับสำหรับการเปลี่ยนแปลงทั่วไป เช่น การทำให้รูปปรากฏอีกครั้งหรือการใช้สีต่าง ๆ เมื่อเสร็จสิ้นคุณจะสามารถ **add rectangle shape** ไปยังไฟล์ .docx ใดก็ได้โดยอัตโนมัติ

## ข้อกำหนดเบื้องต้น

* **Aspose.Words for .NET** (เวอร์ชัน 23.10 หรือใหม่กว่า) คุณสามารถติดตั้งผ่าน NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK หรือใหม่กว่า ที่ติดตั้งบนเครื่องของคุณ
* ความเข้าใจพื้นฐานเกี่ยวกับ C# และ Visual Studio (หรือ IDE ใดก็ได้ที่คุณชอบ)

ไม่ต้องการไลบรารีเพิ่มเติม—API ที่เกี่ยวกับรูปเป็นส่วนหนึ่งของแพคเกจหลักของ Aspose.Words

## แทรกรูปสี่เหลี่ยมผืนผ้าด้วย Aspose.Words

หัวใจของวิธีแก้คือโปรแกรมสั้น ๆ ที่ทำงานอิสระซึ่งสร้างเอกสารเปล่า, แทรกรูปสี่เหลี่ยม, เติมสี, ซ่อน, แล้วบันทึกไฟล์ ด้านล่างเป็นซอร์สโค้ดเต็มพร้อมคอมเมนต์ในบรรทัดที่อธิบาย *ทำไม* ของแต่ละบรรทัด

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### สิ่งที่แต่ละขั้นตอนทำ

| Step | Reason |
|------|--------|
| **Create a new document** | ให้ผ้าใบที่สะอาด; คุณยังสามารถโหลดไฟล์ .docx ที่มีอยู่โดยส่งพาธไฟล์ไปยัง `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` เป็นตัวช่วยระดับสูงที่ทำให้คุณสามารถแทรกข้อความ, ตาราง, และรูปได้โดยไม่ต้องจัดการกับโครงสร้างโหนดระดับต่ำ |
| **Insert rectangle shape** | เมธอด `InsertShape` จะคืนค่าเป็นอ็อบเจ็กต์ `Shape` ที่คุณสามารถปรับแต่งต่อได้ (ขนาด, ตำแหน่ง, เส้นขอบ ฯลฯ) |
| **Set fill color** | คุณสมบัติ `FillColor` ควบคุมสีภายใน; คุณสามารถใช้ค่า `Color` ใดก็ได้ (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, ฯลฯ) |
| **Hide the shape** | `Hidden = true` บอกให้ Word เพิกเฉยรูปในระหว่างการจัดเลย์เอาต์ แต่ยังคงเก็บไว้ใน XML ของเอกสาร นี่เป็นวิธีมาตรฐานในการเก็บวัตถุที่มองไม่เห็น |
| **Save the document** | บันทึกการเปลี่ยนแปลงลงในไฟล์ .docx ไฟล์ที่บันทึกจะมีรูปสี่เหลี่ยมที่ซ่อนอยู่ |

## วิธีตั้งค่าสีเติมให้กับรูป

การเปลี่ยนสีเติมทำได้ง่ายโดยการกำหนดค่า `System.Drawing.Color` ให้กับคุณสมบัติ `FillColor` หากคุณต้องการเฉดสีกำหนดเอง ให้ใช้ `Color.FromArgb` :

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*ทำไมเรื่องนี้สำคัญ*: สีเติมจะถูกเก็บใน XML ของรูป (`<w:fill>` attribute) เมื่อรูปถูกซ่อน สียังคงอยู่ ซึ่งอาจมีประโยชน์สำหรับการประมวลผลต่อเนื่อง (เช่น การสกัดข้อมูลเมตาโดยอิงสีโค้ด)

## วิธีซ่อนรูปในเอกสารสุดท้าย

แฟล็ก `Hidden` เป็นคุณสมบัติแบบบูลีนในคลาส `Shape` การตั้งค่าเป็น `true` จะทำให้ Word เพิกเฉยรูปในกระบวนการจัดเลย์เอาต์

```csharp
rectangleShape.Hidden = true;
```

**ข้อผิดพลาดทั่วไป**

* **Hidden vs. Visible** – หากคุณต้องการให้รูปปรากฏในภายหลัง เพียงตั้งค่า `Hidden = false`.
* **Compatibility** – เวอร์ชัน Word เก่ากว่า (ก่อน 2007) อาจจัดการวัตถุวาดที่ซ่อนต่างกัน Aspose.Words รักษาความเข้ากันได้โดยเก็บแฟล็กในองค์ประกอบ OOXML ที่เหมาะสม

## วิธีแทรกรูปโดยโปรแกรม

แม้ตัวอย่างจะใช้สี่เหลี่ยม, เมธอด `InsertShape` เดียวกันทำงานกับรูปอื่น ๆ มากมาย (วงรี, สามเหลี่ยม, เส้น, ฯลฯ) อาร์กิวเมนต์แรกเป็นค่า enum `ShapeType` :

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**เคล็ดลับ**: หากคุณต้องการวางรูปในตำแหน่งเฉพาะบนหน้า ให้ใช้ `builder.MoveTo` เพื่อตั้งจุดแทรกก่อนเรียก `InsertShape`.

## เพิ่มรูปสี่เหลี่ยมผืนผ้าในเอกสารที่มีอยู่

บ่อยครั้งคุณจะทำการปรับแต่งเทมเพลตแทนการเริ่มจากศูนย์ ให้แทนที่ขั้นตอน 1 ด้วย:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

ขั้นตอนต่อมาทั้งหมดยังคงเหมือนเดิม และสี่เหลี่ยมจะถูกเพิ่มในตำแหน่งที่เคอร์เซอร์ของ builder อยู่ (โดยปกติจะอยู่ที่ส่วนท้ายของเอกสาร)

## การจัดการกรณีขอบและการเปลี่ยนแปลง

### 1. ทำให้รูปปรากฏอีกครั้ง

หากส่วนต่อมาของกระบวนการทำงานของคุณต้องการเปิดเผยสี่เหลี่ยมที่ซ่อนอยู่ คุณสามารถสลับแฟล็กได้:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. เพิ่มเส้นขอบ (stroke)

รูปที่ซ่อนอยู่ยังคงสามารถมีเส้นขอบที่มองเห็นได้เมื่อคุณตัดสินใจแสดงมัน ตั้งค่าคุณสมบัติ `LineColor` และ `LineWidth` :

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. กำหนดตำแหน่งสี่เหลี่ยมแบบแน่นอน

เพื่อการควบคุมเลย์เอาต์ที่แม่นยำ ให้เปลี่ยน `WrapType` ของรูปเป็น `WrapType.Inline` (ค่าเริ่มต้น) หรือ `WrapType.TopBottom` แล้วปรับค่าคุณสมบัติ `Left`/`Top` :

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. ใช้หน่วยวัดอื่น

Aspose.Words ทำงานในหน่วยพอยต์ (1 pt = 1/72 inch) หากคุณต้องการเซนติเมตร ให้แปลงก่อน:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

ด้านล่างเป็นโปรแกรม *เต็ม* ที่คุณสามารถคัดลอก, วาง, และรันได้ รวมถึงคำสั่ง `using` ที่จำเป็นทั้งหมดและใช้พาธแบบเต็มที่คุณควรปรับให้เหมาะกับสภาพแวดล้อมของคุณ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง**: ไฟล์ `HiddenRectangleShape.docx` เปิดใน Microsoft Word โดย *ไม่มีรูปที่มองเห็น* แต่สี่เหลี่ยมที่ซ่อนอยู่ปรากฏใน XML ของเอกสาร คุณสามารถตรวจสอบได้โดยเปิดไฟล์ .docx เป็นไฟล์ zip และตรวจสอบ `word/document.xml` เพื่อหาองค์ประกอบ `<w:shape>` ที่มีแอตทริบิวต์ `w:fill="yellow"` และ `w:hidden="true"`

## สรุป

ตอนนี้คุณรู้วิธี **insert rectangle shape** ในเอกสาร Word ด้วย C# และ Aspose.Words, วิธี **set fill color**, และวิธี **hide shape** เพื่อให้มันไม่ปรากฏในเลย์เอาต์สุดท้าย รูปแบบเดียวกันนี้ทำงานกับรูปประเภทอื่น, สีกำหนดเอง, และเทมเพลตที่มีอยู่แล้ว ทดลองกับเส้นขอบ, การกำหนดตำแหน่งแน่นอน, และหน่วยวัดต่าง ๆ เพื่อปรับรูปให้ตรงตามความต้องการของคุณ

### ขั้นตอนต่อไป

* สำรวจ **how to insert shape** ภายในตารางหรือส่วนหัว/ส่วนท้ายเพื่อใช้เป็นลายน้ำ.
* ผสาน **add rectangle shape** กับ content controls เพื่อสร้างตัวแทนแบบไดนามิก.
* ตรวจสอบ API **shape manipulation** ของ Aspose.Words สำหรับฟีเจอร์ขั้นสูงเช่นการหมุน, การเติมแบบไล่สี, และการนำเข้า SVG.

คุณสามารถปรับโค้ดให้เข้ากับโปรเจคของคุณได้ตามต้องการ และบอกเราผ่านคอมเมนต์ว่าความท้าทายที่เกี่ยวกับรูปอะไรที่คุณแก้ไขต่อไป!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจคของคุณ

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}