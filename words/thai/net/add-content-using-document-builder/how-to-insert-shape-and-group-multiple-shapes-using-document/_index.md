---
category: general
date: 2026-11-15
description: เรียนรู้วิธีแทรกรูปทรงในเอกสาร Word และจัดกลุ่มหลายรูปทรงด้วย Aspose.Words
  DocumentBuilder รวมตัวอย่างการแทรกรูปสี่เหลี่ยมและการแทรกหลายรูปทรง.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: th
lastmod: 2026-11-15
og_description: วิธีแทรกรูปทรงในไฟล์ Word ด้วย Aspose.Words คู่มือนี้ครอบคลุมการจัดกลุ่มรูปทรงหลายรูป
  การแทรกรูปสี่เหลี่ยมผืนผ้า และการเพิ่มรูปทรงหลายรูปอย่างมีประสิทธิภาพ.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: วิธีแทรกรูปทรงและจัดกลุ่มหลายรูปทรงด้วย DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: วิธีแทรกรูปทรงและจัดกลุ่มหลายรูปทรงโดยใช้ DocumentBuilder ใน C#
url: /th/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทรกรูปทรงและจัดกลุ่มหลายรูปทรงโดยใช้ DocumentBuilder ใน C#

หากคุณต้องการทราบ **วิธีแทรกรูปทรง** ลงในเอกสาร Word ด้วย Aspose.Words คำแนะนำนี้จะแสดงขั้นตอนที่แน่นอน คุณจะได้เรียนรู้วิธี **จัดกลุ่มหลายรูปทรง** เพื่อให้ทำงานเป็นอ็อบเจ็กต์เดียวกัน และวิธี **แทรกรูปสี่เหลี่ยม** ควบคู่กับกราฟิกอื่น ๆ

การทำงานอัตโนมัติของเอกสารมักต้องการการเพิ่มกราฟิกหลายประเภท—เช่น แผนภูมิ, โลโก้, คอล‑เอาต์—พร้อมกับการจัดระเบียบที่ดี หลังจากทำตามบทเรียนนี้แล้ว คุณจะสามารถ **แทรกหลายรูปทรง**, ใส่ไว้ในกลุ่ม, และบันทึกเลเอาต์ที่สะอาดและนำกลับมาใช้ใหม่ได้

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 หรือใหม่กว่า  
* Visual Studio 2022 (หรือ IDE สำหรับ C# ใด ๆ)  
* ไลเซนส์ Aspose.Words for .NET หรือคีย์ทดลองใช้งานฟรี  
* ความคุ้นเคยพื้นฐานกับ C# และคลาส `DocumentBuilder` ของ Aspose.Words  

คุณ **ไม่จำเป็น** ต้องใช้ไลบรารีของบุคคลที่สามอื่น ๆ; ทุกอย่างที่ต้องการอยู่ใน Aspose.Words แล้ว

## ขั้นตอนที่ 1: ติดตั้ง Aspose.Words ผ่าน NuGet

เปิดโปรเจกต์ของคุณใน Visual Studio แล้วรันคำสั่งต่อไปนี้ใน Package Manager Console:

```powershell
Install-Package Aspose.Words
```

แพคเกจนี้รวมคลาส `DocumentBuilder`, `Shape`, และ `GroupShape` ที่ใช้ตลอดบทเรียน

## ขั้นตอนที่ 2: สร้างอินสแตนซ์ DocumentBuilder – พื้นฐานสำหรับ **วิธีแทรกรูปทรง**

บรรทัดแรกของโค้ดที่ทำงานได้คือการสร้าง `DocumentBuilder` วัตถุนี้ให้คุณเข้าถึงโครงสร้างเอกสารโดยตรง ทำให้คุณสามารถวางรูปทรงได้ตรงตำแหน่งที่ต้องการ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*ทำไมจึงสำคัญ*: `DocumentBuilder` มีเคอร์เซอร์ (จุด “แทรก”) ทุกการเรียก `Insert...` จะใช้เคอร์เซอร์นี้ ซึ่งเป็นเหตุผลที่เราต้องย้ายเคอร์เซอร์เข้าไปใน `GroupShape` เพื่อให้รูปทรงทั้งหมดอยู่รวมกัน

## ขั้นตอนที่ 3: **แทรกรูปสี่เหลี่ยม** – กราฟิกแรกที่คุณจะเพิ่ม

สี่เหลี่ยมเป็นตัวแทนทั่วไปสำหรับตาราง, รูปภาพ, หรือคอล‑เอาต์ ใช้ `InsertShape` พร้อม `ShapeType.Rectangle` และกำหนดความกว้างและความสูงเป็นพอยต์ (1 pt ≈ 1/72 in)

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

สี่เหลี่ยมจะปรากฏที่ตำแหน่งเคอร์เซอร์ปัจจุบัน คุณสามารถปรับสีพื้น, สไตล์เส้น, หรือข้อความภายหลังได้ตามต้องการ

## ขั้นตอนที่ 4: แทรกรูปทรงอื่น – วงรีเพื่อเพิ่มความหลากหลาย

การเพิ่มรูปทรงมากกว่าหนึ่งรูปแสดงให้เห็น **การแทรกหลายรูปทรง** วงรีจะอยู่ต่อจากสี่เหลี่ยมในลำดับของเอกสาร

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

ตอนนี้เอกสารมีรูปทรงอิสระสองรูป หากคุณย้ายเคอร์เซอร์หรือเพิ่มข้อความ รูปทรงจะคงที่ตามตำแหน่งที่แทรกไว้

## ขั้นตอนที่ 5: **จัดกลุ่มหลายรูปทรง** เพื่อให้ทำงานเป็นหน่วยเดียว

การจัดกลุ่มเป็นสิ่งจำเป็นเมื่อคุณต้องการย้าย, หมุน, หรือกำหนดรูปแบบหลายกราฟิกพร้อมกัน โค้ดต่อไปนี้สร้าง `GroupShape`, ย้ายเคอร์เซอร์ของ builder เข้าไปในกลุ่ม, แล้วแทรกรูปทรงเดิมอีกครั้ง—ครั้งนี้รูปทรงจะเป็นลูกของกลุ่ม

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### ทำไมต้องใช้กลุ่ม?

* **การแปลงแบบจุดเดียว** – หมุนหรือปรับขนาดกลุ่มทั้งหมดด้วยคำสั่งเดียว  
* **การจัดระเบียบเชิงตรรกะ** – โครงสร้างต้นไม้ของ Word จะสะท้อนการจัดกลุ่ม ทำให้การแก้ไขภายหลังง่ายขึ้น  
* **เลเอาต์สม่ำเสมอ** – การย้ายกลุ่มจะรักษาตำแหน่งสัมพัทธ์ของลูกไว้ไม่เปลี่ยน

### เพิ่มรูปทรงเพิ่มเติม – ขยาย **การแทรกหลายรูปทรง** ภายในกลุ่ม

คุณสามารถเรียก `InsertShape` ต่อไปได้ตราบใดที่เคอร์เซอร์ยังคงอยู่ใน `GroupShape` ตัวอย่างเช่น การเพิ่มสามเหลี่ยม:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

แต่ละการเรียกจะเคารพบริบทของกลุ่ม ดังนั้นสามเหลี่ยมจะกลายเป็นส่วนหนึ่งของชุดที่จัดกลุ่มโดยอัตโนมัติ

## ขั้นตอนที่ 6: บันทึกเอกสารและตรวจสอบผลลัพธ์

หลังจากวางรูปทรงทั้งหมดแล้ว ให้บันทึกเอกสารเป็นไฟล์ `.docx` การเปิดไฟล์ใน Microsoft Word (หรือโปรแกรมดูที่รองรับ) ควรแสดงรูปทรงสองรูปแยกกันตามด้วยชุดที่จัดกลุ่มซึ่งประกอบด้วยสี่เหลี่ยม, วงรี, และสามเหลี่ยมเดียวกัน

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### ผลลัพธ์ที่คาดหวัง

* **สองรูปแรก** – สี่เหลี่ยมและวงรีที่วางแยกกันอย่างอิสระบนหน้า  
* **บล็อกที่จัดกลุ่ม** – สี่เหลี่ยม, วงรี, และสามเหลี่ยมที่ย้ายพร้อมกันเมื่อคลิกรูปใดรูปหนึ่งใน Word

คุณสามารถทดสอบการจัดกลุ่มโดยเลือกรูปใดรูปหนึ่งภายในกลุ่ม; Word จะไฮไลท์คอลเลกชันทั้งหมด ยืนยันว่าการ **จัดกลุ่มหลายรูปทรง** ทำงานสำเร็จ

## ข้อผิดพลาดทั่วไปและเคล็ดลับระดับมืออาชีพ

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|--------|
| รูปทรงปรากฏนอกหน้าที่ต้องการ | เคอร์เซอร์ของ builder ไม่ได้ย้ายเข้าไปใน `GroupShape` ก่อนการแทรก | เรียก `builder.MoveTo(group)` **ก่อน** คำสั่ง `InsertShape` ที่เป็นของกลุ่ม |
| กลุ่มหายไปหลังบันทึก | กลุ่มถูกแทรกโดยไม่ได้เพิ่มเข้าไปในคอลเลกชันโหนดของเอกสาร | ใช้ `builder.InsertNode(group)` ทันทีหลังสร้าง `GroupShape` |
| ขนาดไม่ตรงเพราะ DPI ของเอกสาร | Aspose.Words ใช้หน่วยพอยต์; หากคิดเป็นพิกเซลอาจทำให้ขนาดไม่ตรง | แปลงพิกเซลเป็นพอยต์ (`points = pixels * 72 / 96`) หรือทำงานโดยตรงในพอยต์ |
| รูปทรงทับกันโดยไม่ได้ตั้งใจ | ไม่ได้กำหนดตำแหน่งอย่างชัดเจน; Word จะวางตามลำดับ | ตั้งค่า `Shape.Left` และ `Shape.Top` หลังการแทรกเพื่อควบคุมตำแหน่งที่แม่นยำ |

**เคล็ดลับระดับมืออาชีพ:** หลังจากจัดกลุ่มแล้ว คุณสามารถดึงคอลเลกชัน `Shapes` ของกลุ่ม (`group.Shapes`) เพื่อวนลูป, เปลี่ยนชื่อ, หรือใช้การจัดรูปแบบแบบกลุ่มได้

## ขั้นตอนที่ 7: ขยายตัวอย่าง – ต่อไปทำอะไรได้บ้าง?

เมื่อคุณรู้ **วิธีแทรกรูปทรง**, **แทรกรูปสี่เหลี่ยม**, และ **จัดกลุ่มหลายรูปทรง** แล้ว คุณสามารถสำรวจต่อไปได้:

* **ทำให้รูปที่จัดกลุ่มเคลื่อนไหว** – ตั้งค่าการหมุนหรือการพลิกของกลุ่ม  
* **ใช้สไตล์** – ใช้ `Shape.FillColor`, `Shape.LineFormat`, หรือ `Shape.TextBox` เพื่อเพิ่มป้ายกำกับ  
* **ส่งออกเป็น PDF** – เลเอาต์ที่จัดกลุ่มเดียวกันจะถูกเรนเดอร์อย่างถูกต้องเมื่อเรียก `doc.Save("output.pdf")`  

ส่วนขยายเหล่านี้ทั้งหมดใช้กระบวนการทำงานของ `DocumentBuilder` เหมือนเดิม ทำให้โค้ดของคุณสะอาดและดูแลได้ง่าย

## สรุป

บทเรียนนี้ได้สาธิต **วิธีแทรกรูปทรง** ลงในเอกสาร Word ด้วย Aspose.Words, วิธี **แทรกรูปสี่เหลี่ยม**, และวิธี **จัดกลุ่มหลายรูปทรง** เพื่อให้ทำงานเป็นอ็อบเจ็กต์เดียวกัน ด้วยการทำตามโค้ดทีละขั้นตอน คุณจะสามารถ **แทรกหลายรูปทรง**, จัดระเบียบเป็นกลุ่ม, และสร้างเอกสารระดับมืออาชีพโดยอัตโนมัติ

อย่ากลัวที่จะทดลองกับรูปทรงชนิดต่าง ๆ, สี, และการแปลงกลุ่ม เมื่อพร้อมแล้ว ให้นำรูปแบบนี้ไปผสานกับโซลูชันการรายงานหรือการเทมเพลตที่ใหญ่ขึ้น เพื่ออัตโนมัติการจัดเลเอาต์เอกสารที่ซับซ้อน ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานครบถ้วนพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}