---
category: general
date: 2026-09-05
description: สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Aspose.Words แล้วเรียนรู้วิธีแทรกรูปวงรีและจัดกลุ่มรูปทรงใน
  Word เพื่อการจัดวางที่หลากหลายยิ่งขึ้น.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: th
lastmod: 2026-09-05
og_description: สร้างรูปสี่เหลี่ยมผืนผ้าในเอกสาร Word ด้วย Aspose.Words จากนั้นดูวิธีแทรกรูปวงรีและจัดกลุ่มรูปร่างใน
  Word สำหรับการจัดวางที่ซับซ้อน.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: สร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Word – คู่มือ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีสร้างรูปสี่เหลี่ยมและจัดกลุ่มรูปใน Word ด้วย Aspose.Words
url: /th/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างรูปสี่เหลี่ยมและการจัดกลุ่มรูปใน Word ด้วย Aspose.Words

หากคุณต้องการ **create rectangle shape** ในเอกสาร Word คำแนะนำนี้จะแสดงขั้นตอนที่แม่นยำด้วย Aspose.Words for .NET คุณจะได้เห็นวิธีการ **insert ellipse word**, การจัดกลุ่มรูปใน Word, และการบันทึกผลลัพธ์เป็นไฟล์ DOCX โซลูชันนี้ทำงานได้ในโครงการ .NET 6+ ใด ๆ และไม่จำเป็นต้องติดตั้ง Microsoft Office บนเซิร์ฟเวอร์

บทเรียนนี้ครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโครงการจนถึงการจัดการกับปัญหาเลย์เอาต์ทั่วไป เพื่อให้คุณสามารถคัดลอกโค้ดและรันได้ทันที

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* .NET 6 SDK หรือเวอร์ชันใหม่กว่า  
* IDE ที่รองรับ NuGet (Visual Studio, Rider หรือ VS Code)  
* ใบอนุญาต Aspose.Words for .NET (หรือคีย์ประเมินผลชั่วคราว)  
* ความรู้พื้นฐานเกี่ยวกับ C# และโครงสร้างเอกสาร Word  

สิ่งเหล่านี้ทำให้โค้ดคอมไพล์และรูปแสดงผลได้อย่างถูกต้อง

## ขั้นตอนที่ 1: ตั้งค่าโครงการและเพิ่ม Aspose.Words

สร้างโครงการคอนโซลใหม่และเพิ่มแพคเกจ Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

แพคเกจนี้ให้คลาส `Document`, `DocumentBuilder`, `Shape` และ `GroupShape` ที่ใช้ตลอดบทเรียนนี้

## ขั้นตอนที่ 2: เริ่มต้นเอกสารเปล่าและตัวสร้าง

อ็อบเจ็กต์ `Document` แทนไฟล์ Word ทั้งไฟล์ ในขณะที่ `DocumentBuilder` ช่วยให้คุณแทรกเนื้อหาโดยโปรแกรม

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

การสร้างเอกสารก่อนทำให้แน่ใจว่าการดำเนินการกับรูปทั้งหมดต่อไปมีคอนเทนเนอร์ที่ถูกต้อง

## ขั้นตอนที่ 3: **Create rectangle shape** และตั้งค่าขนาดของมัน

รูปสี่เหลี่ยมเป็นคอนเทนเนอร์ที่ใช้บ่อยที่สุดสำหรับข้อความหรือรูปภาพ คุณกำหนดขนาดเป็นหน่วยพอยต์ (1 pt ≈ 1/72 inch)

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

ทำไมขั้นตอนนี้สำคัญ: คลาส `Shape` รวมคุณสมบัติของเรขาคณิต, การเติมสี, และเส้น การตั้งค่า `Width` และ `Height` ก่อนแทรกทำให้รูปปรากฏด้วยขนาดที่คาดหวัง

## ขั้นตอนที่ 4: **How to insert ellipse word** – เพิ่มรูปวงรี

วงรีสามารถใช้เป็นไอคอน, มาร์คเกอร์ หรือองค์ประกอบตกแต่ง โค้ดจะคล้ายกับการสร้างสี่เหลี่ยม เพียงแค่เปลี่ยน `ShapeType`

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

คุณสมบัติ `FillColor` และ `Line.Color` แสดงวิธีปรับแต่งลักษณะโดยไม่ต้องใช้รูปภาพภายนอก

## ขั้นตอนที่ 5: **Group shapes in Word** – รวมรูปสี่เหลี่ยมและวงรี

การจัดกลุ่มทำให้คุณย้าย, ปรับขนาด, หรือหมุนหลายรูปพร้อมกันเป็นหน่วยเดียว ซึ่งจำเป็นเมื่อคุณต้องการกราฟิกเชิงประกอบ (เช่น ไอคอนพร้อมป้ายชื่อ)

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

เมื่อเรียก `AppendChild` รูปเดิมจะถูกลบออกจากการไหลของเอกสารหลักและกลายเป็นลูกของ `GroupShape` กลุ่มจะแสดงเป็นรูปเดียว ซึ่งทำให้การปรับเลย์เอาต์ต่อไปง่ายขึ้น

## ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้ายให้เขียนเอกสารลงดิสก์ คุณสามารถเลือกฟอร์แมตที่รองรับใดก็ได้ (`.docx`, `.pdf`, `.html`, ฯลฯ) สำหรับบทเรียนนี้เราจะเก็บเป็นฟอร์แมต Word ดั้งเดิม

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

หลังจากรันโปรแกรมแล้ว เปิด *GroupShape.docx* ด้วย Microsoft Word คุณจะเห็นสี่เหลี่ยมและวงรีที่จัดกลุ่มกันอยู่ในตำแหน่งที่คุณระบุไว้

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | สิ่งที่ต้องเปลี่ยน | เหตุผล |
|-----------|----------------|--------|
| **Different size units** | ใช้ `ConvertUtil.InchToPoint(2.5)` สำหรับนิ้วหรือ `ConvertUtil.MillimeterToPoint(30)` สำหรับมิลลิเมตร | ทำให้โค้ดอ่านง่ายเมื่อทำงานกับหน่วยที่ไม่ใช่พอยต์ |
| **Adding text inside the rectangle** | สร้างโหนด `Paragraph`, ตั้งค่า `Text` แล้วเพิ่มเข้าไปใน `rectangleShape` ผ่าน `AppendChild` | ให้คุณตั้งชื่อรูปโดยไม่ต้องใช้กล่องข้อความแยก |
| **Rotating the group** | ตั้งค่า `groupShape.Rotation = 45;` (องศา) | มีประโยชน์สำหรับการสร้างแบจ์ดเอียงหรือลายน้ำ |
| **Saving as PDF** | เรียก `doc.Save("GroupShape.pdf");` | Aspose.Words จะทำการแรสเตอร์รูปเวกเตอร์อัตโนมัติสำหรับการส่งออกเป็น PDF |
| **Multiple groups** | สร้างอินสแตนซ์ `GroupShape` เพิ่มเติมและทำซ้ำขั้นตอนการเพิ่ม/แทรก | ช่วยสร้างเลย์เอาต์หน้าที่ซับซ้อนด้วยคอมโพสิตอิสระหลายชุด |

### เคล็ดลับพิเศษ

ควรเพิ่มรูป **before** ที่จะจัดกลุ่ม หากพยายามจัดกลุ่มรูปที่อยู่ในกลุ่มอื่นอยู่แล้ว Aspose.Words จะโยน `ArgumentException` การสร้างกลุ่มในเมธอดเดียวช่วยป้องกันข้อผิดพลาดนี้

### สิ่งที่ต้องระวัง

* **Coordinate system** – `Left` และ `Top` วัดจากระยะขอบซ้ายและบนของหน้า ไม่ได้จากขอบเอกสาร การเข้าใจผิดอาจทำให้รูปอยู่นอกหน้า
* **Licensing** – หากไม่มีใบอนุญาตที่ถูกต้อง เอกสารที่บันทึกจะมีลายน้ำว่า “Aspose.Words for .NET Evaluation” ให้ตั้งค่าใบอนุญาตตั้งแต่ต้นโค้ด (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) เพื่อหลีกเลี่ยง

## โค้ดเต็ม (สามารถรันได้)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

การรันโปรแกรมนี้จะสร้าง *GroupShape.docx* ที่มีรูปที่จัดกลุ่มตามที่อธิบายไว้

## สรุป

คุณได้เรียนรู้วิธี **create rectangle shape**, **how to insert ellipse word**, และ **group shapes in Word** ด้วย Aspose.Words ตัวอย่างเต็มแสดงขั้นตอนการทำงานทั้งหมด—from การเริ่มต้นเอกสารจนถึงการบันทึกไฟล์สุดท้าย—เพื่อให้คุณสามารถผสานการจัดการรูปเข้าไปในโซลูชันการรายงานหรือการสร้างเอกสารอัตโนมัติใด ๆ

### ขั้นตอนต่อไปคืออะไร?

* สำรวจ **aspose.words create shapes** เพื่อสร้างเรขาคณิตที่ซับซ้อนยิ่งขึ้น เช่น `Polygon` หรือ `Freeform`  
* ผสานรูปที่จัดกลุ่มกับ **content controls** เพื่อสร้างเทมเพลตแบบไดนามิก  
* แปลง DOCX เป็น PDF หรือ HTML เพื่อดูว่ารูปเวกเตอร์แสดงผลอย่างไรในแต่ละฟอร์แมต  

ลองทดลองกับขนาด, สี, และการหมุนที่ต่างกัน เมื่อคุณเชี่ยวชาญการจัดกลุ่มรูป คุณจะสร้างไดอะแกรม, แบจ์ด, และองค์ประกอบ UI ที่กำหนดเองโดยตรงในเอกสาร Word ได้อย่างมืออาชีพ

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบต่าง ๆ ในโครงการของคุณ

- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [แทรกรูปในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [สร้างรูปสี่เหลี่ยมใน Word ด้วย C# – คู่มือแบบขั้นตอน](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}