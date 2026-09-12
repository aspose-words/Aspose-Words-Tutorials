---
category: general
date: 2026-09-11
description: เรียนรู้วิธีสร้างเอกสาร Word, เพิ่มรูปสี่เหลี่ยม, และตั้งค่าขนาดรูปด้วย
  Aspose.Words. คู่มือ C# ทีละขั้นตอนสำหรับการกำหนดขนาดรูปอย่างแม่นยำ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: th
lastmod: 2026-09-11
og_description: สร้างเอกสาร Word ด้วย Aspose.Words ใน C# คู่มือนี้แสดงวิธีเพิ่มรูปสี่เหลี่ยม
  ตั้งค่าขนาดรูป และจัดการมิติของรูปโดยโปรแกรม.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: สร้างเอกสาร Word พร้อมรูปทรง – บทแนะนำ Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: วิธีสร้างเอกสาร Word พร้อมรูปทรงโดยใช้ Aspose.Words ใน C#
url: /th/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างเอกสาร Word พร้อมรูปทรงโดยใช้ Aspose.Words ใน C#

หากคุณต้องการ **สร้างเอกสาร Word** ที่มีกราฟิกแบบกำหนดเอง คุณสามารถทำได้ทั้งหมดด้วยโค้ด บทแนะนำนี้จะพาคุณผ่านขั้นตอนการสร้างไฟล์ Word การเพิ่มรูปสี่เหลี่ยมผืนผ้า และการควบคุมทุกมิติของรูปทรง เมื่อเสร็จคุณจะได้โค้ดสั้นที่สามารถนำไปใช้ในโปรเจกต์ .NET ใดก็ได้

คุณจะได้เรียนรู้วิธี **เพิ่มรูปสี่เหลี่ยมผืนผ้า**, **กำหนดขนาดรูปทรง**, และ **กำหนดมิติของรูปทรง** ภายในคอนเทนเนอร์แบบกลุ่ม ตัวอย่างใช้ Aspose.Words 13.9 แต่แนวคิดสามารถใช้กับเวอร์ชันต่อ ๆ ไปได้ ไม่จำเป็นต้องมีประสบการณ์กับ Aspose drawing API มาก่อน—เพียงความรู้พื้นฐานของ C#

## ข้อกำหนดเบื้องต้น

- ติดตั้ง .NET 6.0 หรือรุ่นใหม่กว่า  
- แพ็กเกจ NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- IDE เช่น Visual Studio 2022 (เครื่องมือแก้ไขใด ๆ ที่รองรับ C# ก็ใช้ได้)  

การมีเครื่องมือเหล่านี้พร้อมใช้งานทำให้คุณสามารถรันโค้ดได้ทันทีโดยไม่ต้องตั้งค่าเพิ่มเติม

## ขั้นตอนที่ 1: เริ่มต้นเอกสารและ builder – พื้นฐานการสร้างเอกสาร Word

การดำเนินการแรกคือการสร้างอ็อบเจ็กต์ `Document` และ `DocumentBuilder` `Document` แทนไฟล์เอง ส่วน `DocumentBuilder` ให้ API แบบ fluent สำหรับแทรกเนื้อหา

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**ทำไมจึงสำคัญ:**  
การสร้างเอกสารล่วงหน้าจะให้พื้นที่ทำงานที่สะอาด cursor ของ builder จะเริ่มที่ย่อหน้าแรก ซึ่งเป็นที่ที่เราจะ **สร้างรูปทรงใน Word** ในภายหลัง

## ขั้นตอนที่ 2: สร้าง GroupShape เพื่อเก็บกราฟิกหลายรายการ

`GroupShape` ทำหน้าที่เป็นคอนเทนเนอร์; คุณสามารถย้าย, หมุน หรือปรับขนาดกลุ่มทั้งหมดเป็นหน่วยเดียว ที่นี่เรากำหนดความกว้างและความสูงของคอนเทนเนอร์เป็นหน่วย point (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**ทำไมจึงสำคัญ:**  
การจัดกลุ่มรูปทรงทำให้การจัดการเลย์เอาต์ง่ายขึ้น หากคุณต้องการเพิ่มรูปทรงอื่นในภายหลัง (เช่น วงกลมหรือกล่องข้อความ) พวกมันจะสืบทอดตำแหน่งและการสเกลของกลุ่ม

## ขั้นตอนที่ 3: สร้างรูปสี่เหลี่ยมผืนผ้าและกำหนดมิติของมัน

ตอนนี้เราจะเพิ่มสี่เหลี่ยมจริง ๆ ตัวสร้าง `Shape` ต้องการอ้างอิงเอกสารและประเภทของรูปทรง หลังจากสร้างแล้วเราจะกำหนด **ขนาดรูปทรง** และ **มิติของรูปทรง** อย่างชัดเจน

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**ทำไมจึงสำคัญ:**  
การระบุความกว้าง, ความสูง, ซ้าย, และบน ให้การควบคุมรูปทรงที่แม่นยำระดับพิกเซล ซึ่งจำเป็นเมื่อเอกสารต้องตรงตามสเปคการออกแบบหรือแบบฟอร์มที่พิมพ์

## ขั้นตอนที่ 4: ประกอบกลุ่มโดยการต่อสี่เหลี่ยมเข้ากับ GroupShape

การต่อสี่เหลี่ยมเข้ากับ `GroupShape` ทำให้มันเป็นโหนดลูก คุณสามารถเพิ่มโหนดลูกได้ตามต้องการก่อนที่จะใส่กลุ่มลงในเอกสาร

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**เคล็ดลับ:** หากคุณวางแผนจะเพิ่มรูปทรงที่สอง ให้สร้างแบบเดียวกันและเรียก `group.AppendChild(secondShape)` โหนดลูกทั้งหมดจะใช้ระบบพิกัดของกลุ่มเดียวกัน

## ขั้นตอนที่ 5: แทรกรูปทรงที่จัดกลุ่มลงในเอกสารและบันทึก

เมื่อกลุ่มสร้างเสร็จสมบูรณ์ เราใส่มันลงในย่อหน้าปัจจุบัน คุณสมบัติ `CurrentParagraph` ของ builder ให้เข้าถึงโครงสร้างโหนดพื้นฐานโดยตรง

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**ทำไมจึงสำคัญ:**  
การต่อกลุ่มเข้ากับย่อหน้าจะทำให้รูปทรงแสดงผลเป็นส่วนหนึ่งของการไหลของข้อความ การบันทึกเอกสารสรุปการทำงานของ **สร้างเอกสาร Word**.

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | การปรับเปลี่ยน |
|----------|------------|
| **การวางแนวหน้ากระดาษที่แตกต่าง** | ตั้งค่า `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` ก่อนสร้างกลุ่ม |
| **หลายสี่เหลี่ยม** | สร้างอ็อบเจ็กต์ `Shape` เพิ่มเติมและเรียก `group.AppendChild(newRect)` สำหรับแต่ละอัน |
| **ขนาดแบบไดนามิกตามเนื้อหา** | คำนวณความกว้าง/ความสูงจากมิติของภาพหรือเมตริกซ์ของข้อความ แล้วกำหนดให้กับ `rectangle.Width` / `rectangle.Height` |
| **ส่งออกเป็น PDF** | หลังจาก `doc.Save` ให้เรียก `doc.Save("GroupShape.pdf", SaveFormat.Pdf);` |
| **ความเข้ากันได้กับเวอร์ชัน Word เก่า** | บันทึกโดยใช้ `SaveFormat.Doc` แทน `Docx` เพื่อความเข้ากันได้กับ Word 97‑2003 |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก วาง และรันได้ รวมถึงคำสั่ง `using` ทั้งหมด จุดเริ่มต้น `Main` และคอมเมนต์ที่อธิบายแต่ละบรรทัด

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**ผลลัพธ์ที่คาดหวัง:**  
เมื่อคุณเปิด *GroupShape.docx* หน้าแรกจะแสดงสี่เหลี่ยมที่มีขอบสีเทาตำแหน่งห่างจากขอบซ้าย/บน 50 pt โดยสี่เหลี่ยมเองห่างจากขอบในกลุ่ม 10 pt มิติจะตรงกับค่าที่ตั้งในโค้ด

## สรุป

ตอนนี้คุณรู้วิธี **สร้างเอกสาร Word**, **เพิ่มรูปสี่เหลี่ยมผืนผ้า**, และกำหนด **ขนาดรูปทรง** และ **มิติของรูปทรง** อย่างแม่นยำด้วย Aspose.Words วิธีการจัดกลุ่มรูปทรงทำให้เลย์เอาต์ของคุณยืดหยุ่นและพร้อมสำหรับการขยายในอนาคต เช่น กราฟิกเพิ่มเติมหรือกล่องข้อความ

ต่อไปสำรวจหัวข้อที่เกี่ยวข้องเช่น **สร้างรูปทรงใน Word** สำหรับวงกลม, ลูกศร, หรือเส้นทาง SVG แบบกำหนดเอง, และเรียนรู้วิธี **ตั้งค่าสีเติมของรูปทรง** หรือ **ใช้การหมุน** ทดลองกับหน่วยวัดต่าง ๆ เพื่อดูว่า Word แสดงผลจุดเทียบกับเซนติเมตรอย่างไร และผสานโค้ดนี้เข้ากับกระบวนการสร้างเอกสารขนาดใหญ่

ขอให้สนุกกับการเขียนโค้ด และอย่าลังเลที่จะปรับใช้รูปแบบนี้กับการสร้างรายงานอัตโนมัติหรือการกรอกฟอร์มใด ๆ ที่คุณพบ!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ

- [สร้างรูปสี่เหลี่ยมผืนผ้าใน Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [สร้างเอกสาร Word เปล่าพร้อมรูปสี่เหลี่ยมเงา – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [บทแนะนำการเพิ่มเงาให้รูปทรงใน Aspose.Words – เพิ่มเงาให้รูปทรง Word ใน C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}