---
category: general
date: 2026-09-11
description: เรียนรู้วิธีซ่อนรูปร่างใน Word ด้วย C# คู่มือนี้ยังแสดงวิธีแทรกรูปสี่เหลี่ยมและแทรกรูปร่างลงในเอกสาร
  Word ด้วย Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: th
lastmod: 2026-09-11
og_description: วิธีซ่อนรูปร่างใน Word ด้วย C# และ Aspose.Words. ทำตามบทแนะนำขั้นตอนต่อขั้นตอนเพื่อแทรกรูปสี่เหลี่ยมและจัดการรูปร่างในเอกสาร
  Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: วิธีซ่อนรูปร่างใน Word – คู่มือ C# ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีซ่อนรูปทรงใน Word ด้วย C# และ Aspose.Words
url: /th/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีซ่อนรูปร่างใน Word ด้วย C# และ Aspose.Words

หากคุณต้องการซ่อนรูปร่างใน Word แต่ยังคงให้รูปร่างอยู่ในโครงสร้างของเอกสาร คำแนะนำนี้จะแสดงวิธีทำอย่างละเอียด ด้วย Aspose.Words for .NET คุณสามารถแทรกรูปร่างสี่เหลี่ยมผืนผ้า ซ่อนมัน และยังคงตำแหน่งไว้สำหรับการประมวลผลต่อไป

การทำอัตโนมัติของ Word มักต้องการการควบคุมรูปร่างอย่างละเอียด—ไม่ว่าจะเป็นการสร้างเทมเพลต การเตรียมรายงาน หรือการสร้างบริการแก้ไขเอกสาร เมื่อคุณอ่านคู่มือนี้จนจบแล้ว คุณจะสามารถ:

* แทรกรูปร่างสี่เหลี่ยมผืนผ้าเข้าไปในเอกสาร Word (`insert rectangle shape`).
* ซ่อนรูปร่างใด ๆ โดยไม่ลบออก (`how to hide shape in word`).
* บันทึกผลลัพธ์และตรวจสอบว่ารูปร่างที่ซ่อนอยู่ไม่ปรากฏในมุมมองที่แสดง (`insert shape into word document`).

ตัวอย่างนี้ทำงานกับ Aspose.Words 24.10 หรือใหม่กว่าและกำหนดเป้าหมายที่ .NET 6.0+ แต่แนวคิดยังใช้ได้กับเวอร์ชันก่อนหน้าเช่นกัน.

## ข้อกำหนดเบื้องต้น

* **Aspose.Words for .NET** ≥ 24.10. คุณสามารถรับใบอนุญาตชั่วคราวฟรีจากเว็บไซต์ของ Aspose.
* **.NET SDK** 6.0 หรือใหม่กว่า ติดตั้งบนเครื่องของคุณ.
* สภาพแวดล้อมการพัฒนา เช่น Visual Studio 2022, VS Code หรือ Rider.
* ความคุ้นเคยพื้นฐานกับ C# และแนวคิด Word Open XML (ไม่จำเป็นแต่เป็นประโยชน์).

## วิธีซ่อนรูปร่างใน Word ด้วย Aspose.Words

ด้านล่างเป็นโปรแกรมที่สมบูรณ์และสามารถรันได้ ซึ่งแสดงกระบวนการทำงานทั้งหมด—from การสร้างเอกสาร ไปจนถึงการแทรกรูปร่างสี่เหลี่ยมผืนผ้าและสุดท้ายการซ่อนมัน.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### คำอธิบายของแต่ละขั้นตอน

1. **Create a new document** – `Document` แทนไฟล์ Word ในหน่วยความจำ `DocumentBuilder` ให้ API แบบ fluent สำหรับแทรกเนื้อหา.
2. **Insert rectangle shape** – `InsertShape` สร้างออบเจกต์การวาดประเภท `Rectangle` ขนาดจะระบุเป็น points (1 pt ≈ 1/72 in) ซึ่งตอบสนองความต้องการ `insert rectangle shape`.
3. **Hide the shape** – การตั้งค่า `Shape.Hidden = true` ทำเครื่องหมายให้รูปร่างเป็น hidden ใน markup ของ Word (`<w:hidden/>`) รูปร่างยังคงอยู่ในโครงสร้างของเอกสาร ดังนั้นคุณสามารถยกเลิกการซ่อนหรืออ้างอิงโปรแกรมได้ นี่คือหัวใจของ `how to hide shape in word`.
4. **Save the file** – เอกสารถูกเขียนไปยัง `output.docx` เมื่อเปิดใน Microsoft Word สี่เหลี่ยมจะไม่ปรากฏ แต่ยังคงอยู่ใน XML และสามารถตรวจสอบด้วยโปรแกรมดูไฟล์ ZIP หรือ Open XML SDK.

### ผลลัพธ์ที่คาดหวัง

Open `output.docx` ใน Microsoft Word:

* เอกสารดูเหมือนว่างเปล่า—ไม่มีรูปร่างที่มองเห็น.
* หากคุณตรวจสอบ XML พื้นฐาน (`word/document.xml`) คุณจะพบองค์ประกอบ `<w:pict>` ที่มีแอตทริบิวต์ `<w:hidden/>` ยืนยันว่ารูปร่างยังคงอยู่แต่ถูกซ่อน.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

คุณสามารถทำให้รูปร่างที่ซ่อนอยู่ปรากฏอีกครั้งโดยตั้งค่า `Hidden = false` แล้วบันทึกเอกสารใหม่.

## แทรกรูปร่างสี่เหลี่ยมผืนผ้าเข้าไปในเอกสาร Word

แม้เป้าหมายหลักจะเป็นการซ่อนรูปร่าง แต่หลายสถานการณ์เริ่มต้นด้วยการแทรกรูปร่างก่อน วิธี `InsertShape` รองรับค่า `ShapeType` มากมาย รวมถึง `Rectangle`, `Ellipse`, `Line` และรูปภาพแบบกำหนดเอง.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**ทำไมต้องใช้สี่เหลี่ยมผืนผ้า?**  
สี่เหลี่ยมผืนผ้าให้คอนเทนเนอร์ที่เรียบง่ายและจัดแนวตามแกน สามารถบรรจุข้อความ รูปภาพ หรือรูปร่างซ้อนอื่น ๆ ได้ มักใช้เป็นตัวแทนสำหรับเนื้อหาแบบไดนามิก เช่น ตารางหรือแผนภูมิ การแทรกสี่เหลี่ยมก่อนจะช่วยรักษาความสอดคล้องของเลย์เอาต์แม้หลังจากที่คุณซ่อนมันในภายหลัง.

## การแทรกรูปร่างเข้าไปในเอกสาร Word – แนวทางปฏิบัติที่ดีที่สุด

เมื่อคุณ `insert shape into word document` ให้พิจารณาต่อไปนี้:

* **กำหนดขนาดอย่างชัดเจน** – หลีกเลี่ยงการพึ่งพาการปรับขนาดอัตโนมัติ; ระบุความกว้างและความสูงเป็น points เพื่อให้เลย์เอาต์สอดคล้องในทุกแพลตฟอร์ม.
* **กำหนดตำแหน่ง** – โดยค่าเริ่มต้นรูปร่างจะถูกยึดกับย่อหน้าปัจจุบัน ใช้ `builder.MoveTo` หรือ `builder.StartBookmark` เพื่อวางตำแหน่งอย่างแม่นยำ.
* **ใช้สไตล์ตั้งแต่ต้น** – สีเติม, สไตล์เส้น, และการห่อหุ้มข้อความมีผลต่อรูปลักษณ์สุดท้าย แม้รูปร่างที่ซ่อนอยู่ก็จะได้ประโยชน์จากการสไตล์ที่เหมาะสมเนื่องจาก markup ไม่เปลี่ยนแปลง.
* **ความเข้ากันได้ของเวอร์ชัน** – คุณสมบัติ `Hidden` มีตั้งแต่ Aspose.Words 24.10 ขึ้นไป หากคุณใช้เวอร์ชันเก่า คุณสามารถเพิ่มแอตทริบิวต์ `<w:hidden/>` ด้วยตนเองโดยใช้ API `Node`.

### การเพิ่มแอตทริบิวต์ hidden ด้วยตนเอง (fallback)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## ตัวอย่างครบวงจรจากต้นจนจบ

การรวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมเดียวที่:

1. แทรกสี่เหลี่ยมผืนผ้า.
2. ซ่อนรูปร่าง.
3. แทรกวงรีที่มองเห็นได้เพื่อเปรียบเทียบ.
4. บันทึกเอกสาร.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `demo_output.docx` เมื่อเปิดคุณจะเห็นเพียงวงรีสีปะการัง; สี่เหลี่ยมสีเขียวอยู่ใน XML แต่ถูกซ่อนจากมุมมอง.

## คำถามทั่วไปและกรณีขอบ

**ถาม: การซ่อนรูปร่างมีผลต่อการแบ่งหน้าไหม?**  
ตอบ: ไม่. รูปร่างที่ซ่อนจะถูกเอาออกจากการคำนวณของเอนจินการจัดวาง ดังนั้นจึงไม่ใช้พื้นที่ ซึ่งเป็นประโยชน์สำหรับเนื้อหา placeholder ที่ไม่ควรส่งผลต่อการแบ่งหน้า.

**ถาม: ฉันสามารถซ่อนรูปร่างที่เป็นส่วนหนึ่งของส่วนหัวหรือส่วนท้ายได้ไหม?**  
ตอบ: ได้. คุณสมบัติ `Hidden` ทำงานกับรูปร่างที่อยู่ในตำแหน่งใด ๆ ของโครงสร้างเอกสาร รวมถึงส่วนหัว, ส่วนท้าย, และแม้แต่ภายในตาราง.

**ถาม: ถ้าฉันต้องการซ่อนหลายรูปร่างพร้อมกันทำอย่างไร?**  
ตอบ: วนลูปผ่านคอลเลกชัน `Document.GetChildNodes(NodeType.Shape, true)` และตั้งค่า `Hidden = true` สำหรับแต่ละรูปร่างที่ต้องการ.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**ถาม: แอตทริบิวต์ hidden จะถูกเก็บไว้เมื่อแปลงเป็น PDF หรือไม่?**  
ตอบ: เมื่อแปลงเป็น PDF รูปร่างที่ซ่อนจะถูกละเว้นโดยค่าเริ่มต้น ซึ่งสอดคล้องกับพฤติกรรมการแสดงผลของ Word หากคุณต้องการให้มันปรากฏใน PDF คุณต้องยกเลิกการซ่อนก่อนทำการแปลง.

## เคล็ดลับและข้อควรระวัง

* **เคล็ดลับมืออาชีพ:** ตั้งค่า `shape.WrapType = WrapType.None` ก่อนทำการซ่อน หากคุณวางแผนจะยกเลิกการซ่อนในภายหลังโดยไม่กระทบต่อข้อความรอบข้าง.
* **ระวังเวอร์ชันเก่าของ Aspose.Words:** คุณสมบัติ `Hidden` จะทำให้เกิด `NotSupportedException` ก่อนเวอร์ชัน 24.10 ใช้วิธีเพิ่ม XML ด้วยตนเองในกรณีนั้น.
* **การทดสอบ:** เปิดไฟล์ `.docx` ที่สร้างขึ้นใน Word เสมอและใช้ “Show XML markup” (แท็บ Developer) เพื่อตรวจสอบว่าแอตทริบิวต์ `<w:hidden/>` มีอยู่.

## สรุป

ตอนนี้คุณรู้วิธีซ่อนรูปร่างใน Word ด้วย C# และ Aspose.Words รวมถึงวิธีแทรกสี่เหลี่ยมผืนผ้าและแทรกรูปร่างเข้าไปในเอกสาร Word พร้อมการควบคุมการมองเห็นอย่างเต็มที่ ด้วยการใช้คุณสมบัติ `Hidden` คุณสามารถเก็บรูปร่างไว้ในโมเดลของเอกสารเพื่อการประมวลผลต่อไป ในขณะที่แสดงมุมมองที่สะอาดต่อผู้ใช้ปลายทาง.

ต่อไปสำรวจหัวข้อที่เกี่ยวข้อง เช่น **การอัปเดตคุณสมบัติของรูปร่างในขณะทำงาน**, **การแปลงรูปร่างที่ซ่อนเป็นภาพ**, หรือ **การใช้ Open XML SDK เพื่อจัดการกับองค์ประกอบที่ซ่อนโดยตรง** ส่วนขยายเหล่านี้จะช่วยเพิ่มความเข้าใจของคุณต่อไป

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบต่าง ๆ ในโครงการของคุณเอง.

- [แทรกรูปร่างในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [สร้างสี่เหลี่ยมผืนผ้าใน Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}