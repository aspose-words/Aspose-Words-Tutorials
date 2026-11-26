---
category: general
date: 2026-11-18
description: เรียนรู้วิธีสร้างรูปสี่เหลี่ยมผืนผ้าในเอกสาร Word ด้วย C# คู่มือนี้ยังครอบคลุมการตั้งค่าขนาดรูป,
  การตั้งค่าตำแหน่งรูป, และการจัดกลุ่มรูปใน Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: th
lastmod: 2026-11-18
og_description: สร้างรูปสี่เหลี่ยมในไฟล์ Word ด้วย C# และเรียนรู้การตั้งค่าขนาดรูป,
  การกำหนดตำแหน่งรูป, และการจัดกลุ่มรูปใน Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: สร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Word ด้วย C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีสร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Word ด้วย C#
url: /th/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Word ด้วย C#

หากคุณต้องการ **สร้างรูปสี่เหลี่ยม** ในเอกสาร Word, บทแนะนำนี้จะแสดงวิธีแก้ไขที่สมบูรณ์และพร้อมรัน คุณจะได้เห็นวิธีตั้งขนาดรูป, ตั้งตำแหน่งรูป, และจัดกลุ่มรูปใน Word ให้ทำงานเป็นวัตถุเดียว

การทำงานกับรูปเป็นความต้องการทั่วไปเมื่อสร้างรายงาน, ใบแจ้งหนี้, หรือแผนภาพโดยอัตโนมัติ เมื่ออ่านจบคู่มือนี้คุณจะสามารถสร้างไฟล์ `.docx` ที่มีรูปสี่เหลี่ยม, รูปวงรี, และคอนเทนเนอร์ที่จัดกลุ่ม—ทั้งหมดสร้างด้วย Aspose.Words for .NET

## ข้อกำหนดเบื้องต้น

- .NET 6.0 SDK หรือเวอร์ชันใหม่กว่า (โค้ดยังทำงานได้กับ .NET Framework 4.7+)
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)
- เครื่องมือแก้ไขโค้ดหรือ IDE (Visual Studio, VS Code, Rider, ฯลฯ)

ไม่จำเป็นต้องใช้ไลบรารีเพิ่มเติม.

## วิธีสร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Word

ขั้นตอนหลักมีดังนี้:

1. **สร้างเอกสารเปล่า** และ `DocumentBuilder`.
2. **แทรก `GroupShape`** ที่จะเก็บรูปย่อยแต่ละรูป.
3. **สร้างรูปสี่เหลี่ยม**, ตั้งขนาดและเพิ่มเข้าไปในกลุ่ม.
4. **สร้างรูปวงรี**, ตั้งขนาดและตำแหน่ง, แล้วเพิ่มเข้าไปในกลุ่ม.
5. **บันทึก** เอกสาร.

แต่ละขั้นตอนจะอธิบายด้านล่าง และโค้ดต้นฉบับเต็มจะตามหลังการอธิบาย

### ขั้นตอน 1: เริ่มต้นเอกสารและ builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` แสดงถึงไฟล์ Word ทั้งไฟล์, ส่วน `DocumentBuilder` ให้ API แบบ fluent เพื่อแทรกเนื้อหา การเริ่มต้นพวกมันเป็นสิ่งจำเป็นก่อนที่คุณจะเพิ่มรูปใด ๆ

### ขั้นตอน 2: แทรกกลุ่มรูป

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` ทำงานเหมือนคอนเทนเนอร์; รูปย่อยทั้งหมดจะเคลื่อนที่พร้อมกัน นี่เป็นวิธีที่แนะนำในการ **จัดกลุ่มรูปใน Word** เมื่อคุณต้องการการแปลงแบบรวม (เช่น การย้าย, การหมุน, หรือการลบ).

### ขั้นตอน 3: สร้างรูปสี่เหลี่ยมและตั้งขนาด

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

ที่นี่เราจะ **สร้างรูปสี่เหลี่ยม** และ **ตั้งขนาดรูป** โดยกำหนด `Width` และ `Height`. ใน Aspose.Words, ขนาดจะระบุเป็นจุด (1 pt ≈ 1/72 in). การกำหนดขนาดอย่างชัดเจนทำให้รูปสี่เหลี่ยมแสดงผลตามที่ต้องการ

### ขั้นตอน 4: สร้างรูปวงรี, ตั้งขนาด, และกำหนดตำแหน่ง

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

**การตั้งขนาดรูป** สำหรับรูปวงรีจะเท่ากันทั้งความกว้างและความสูง ทำให้ได้วงกลมที่สมบูรณ์ คุณสมบัติ `Left` แสดง **การตั้งตำแหน่งรูป**: รูปวงรีเริ่มที่ 120 pt ทางขวาของจุดเริ่มต้นของกลุ่ม, ดังนั้นจึงไม่ทับกับรูปสี่เหลี่ยม.

### ขั้นตอน 5: บันทึกเอกสาร

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

การบันทึกจะเขียนไฟล์ Word ลงดิสก์ คุณสามารถเปิด `GroupShape.docx` ใน Microsoft Word เพื่อตรวจสอบว่ารูปสี่เหลี่ยมและรูปวงรีถูกจัดกลุ่มและวางตำแหน่งอย่างถูกต้อง

## การตั้งขนาดและมิติของรูป – การดูเชิงลึก

- **Points vs. inches**: 72 pt = 1 in. หากคุณต้องการใช้หน่วยนิ้ว, ให้คูณด้วย 72 (เช่น `2.5 * 72` สำหรับ 2.5 in).
- **Automatic scaling**: หากคุณละ `Width` หรือ `Height`, รูปจะใช้ขนาดเริ่มต้นโดยอัตโนมัติ ให้ **ตั้งขนาดรูป** อย่างชัดเจนเพื่อหลีกเลี่ยงการจัดวางที่ไม่คาดคิด.
- **Aspect ratio**: สำหรับรูปเช่น `Ellipse`, การทำให้ `Width` และ `Height` เท่ากันจะคงลักษณะเป็นวงกลม.

## การกำหนดตำแหน่งรูปใน Word

คุณสมบัติ `Left` และ `Top` ควบคุมการเยื้องของรูปภายในคอนเทนเนอร์ของมัน (กลุ่มหรือหน้า). ค่าเป็นบวกจะย้ายรูปไปทางขวา/ลง; ค่าเป็นลบจะย้ายไปทางซ้าย/ขึ้น. เมื่อจัดกลุ่ม, ตำแหน่งจะอ้างอิงจากจุดเริ่มต้นของกลุ่ม, ทำให้การคำนวณการจัดวางง่ายขึ้น.

## การจัดกลุ่มรูปใน Word ด้วย Aspose.Words

การจัดกลุ่มเป็นสิ่งสำคัญเมื่อคุณต้องการให้หลายรูปทำงานเป็นหน่วยเดียว `GroupShape` object:

- รองรับ `AppendChild` เพื่อเพิ่ม `Shape` ใด ๆ (สี่เหลี่ยม, วงรี, รูปภาพ, ฯลฯ).
- ให้คุณย้าย, หมุน, หรือ ลบกลุ่มทั้งหมดด้วยคำสั่งเดียว.
- รักษาตำแหน่งของรูปย่อยสัมพันธ์กับกลุ่ม, ทำให้แผนภาพซับซ้อนจัดการได้ง่ายขึ้น.

**เคล็ดลับ:** หลังจากเพิ่มรูปย่อยทั้งหมด, คุณสามารถปรับ `Width`, `Height`, `Left`, และ `Top` ของกลุ่มเพื่อย้ายตำแหน่งของคอลเลกชันทั้งหมดในขั้นตอนเดียว.

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก, วาง, และรันได้ รวมถึงคำสั่ง `using` ทั้งหมด, เมธอด `Main`, และคอมเมนต์ที่อธิบายแต่ละบรรทัด.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** หลังจากรันโปรแกรม, `GroupShape.docx` จะปรากฏในโฟลเดอร์การทำงาน การเปิดไฟล์ใน Word จะเห็นรูปสี่เหลี่ยม (100 pt × 50 pt) ทางซ้ายและรูปวงรี (80 pt × 80 pt) อยู่ห่าง 120 pt ไปทางขวา, ทั้งสองอยู่ในอ็อบเจ็กต์ที่จัดกลุ่มเดียว.

![เอกสาร Word ที่มีรูปสี่เหลี่ยมและวงรีที่จัดกลุ่ม](grouped_shapes.png){: .center alt="ภาพหน้าจอของเอกสาร Word ที่แสดงรูปสี่เหลี่ยมและวงรีที่จัดกลุ่มซึ่งสร้างด้วย C#" }

*ภาพด้านบนแสดงผลลัพธ์สุดท้าย; รูปสี่เหลี่ยมและวงรีสามารถเลือกได้เป็นกลุ่มเดียว.*

## คำถามทั่วไปและกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ฉันสามารถเพิ่มรูปมากกว่าสองรูปได้หรือไม่?** | ได้. เรียก `group.AppendChild(yourShape)` สำหรับแต่ละรูปเพิ่มเติม. |
| **ถ้าฉันต้องการหมุนกลุ่มล่ะ?** | ใช้ `group.RotationAngle = 45;` (หน่วยองศา) หลังจากเพิ่มรูปย่อยทั้งหมด. |
| **ฉันจะเปลี่ยนสีพื้นหลังของกลุ่มได้อย่างไร?** | ตั้งค่า `group.FillColor = System.Drawing.Color.LightGray;`. |
| **โค้ดนี้จะทำงานกับไฟล์ .doc ได้หรือไม่?** | Aspose.Words รองรับไฟล์ `.doc` และ `.docx`. โค้ดเดียวกันทำงานได้; เพียงเปลี่ยนส่วนขยายไฟล์ใน `Save`. |
| **การจัดกลุ่มรูปจำนวนมากมีผลต่อการใช้หน่วยความจำหรือไม่?** | การจัดกลุ่มเองเพิ่มภาระเพียงเล็กน้อย. สิ่งที่ควรใส่ใจคือจำนวนรูปทั้งหมด; ควรจำกัดจำนวนให้เหมาะสมสำหรับเอกสารขนาดใหญ่. |

## สรุป

ในบทแนะนำนี้คุณได้เรียนรู้วิธี **สร้างรูปสี่เหลี่ยม** ในไฟล์ Word ด้วย C#, วิธี **ตั้งขนาดรูป**, **ตั้งมิติรูป**, **ตั้งตำแหน่งรูป**, และสุดท้ายวิธี **จัดกลุ่มรูปใน Word** ด้วย Aspose.Words ตัวอย่างเต็มแสดงแนวทางที่สะอาดและดูแลได้ง่าย ซึ่งคุณสามารถต่อยอดไปสู่แผนภาพ, ชาร์ต, หรือกราฟิกแบบกำหนดเองที่ซับซ้อนยิ่งขึ้น.

ต่อไป, คุณอาจสำรวจ:

- เพิ่มข้อความภายในรูป (`Shape.TextPath.Text = "Hello"`).
- แทรกรูปภาพลงใน `GroupShape`.
- ส่งออกรูปที่จัดกลุ่มเป็น PDF ด้วย `doc.Save("output.pdf")`.

คุณสามารถทดลองกับขนาด, ตำแหน่ง, และประเภทรูปเพิ่มเติมต่าง ๆ เพื่อให้ตรงกับความต้องการของโครงการของคุณได้เลย. ขอให้เขียนโค้ดสนุก!

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโครงการของคุณ.

- [วิธีสร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Word ด้วย Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}