---
category: general
date: 2026-09-21
description: เรียนรู้วิธีจัดกลุ่มรูปทรงใน Word ด้วย Aspose.Words สำหรับ C# คู่มือขั้นตอนนี้ครอบคลุมการสร้าง
  การจัดตำแหน่ง และการบันทึกรูปทรงที่จัดกลุ่ม.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: th
lastmod: 2026-09-21
og_description: จัดกลุ่มรูปทรงใน Word ด้วย Aspose.Words สำหรับ C# . ทำตามบทแนะนำสั้น
  ๆ นี้เพื่อสร้าง, กำหนดตำแหน่งและบันทึกรูปทรงที่จัดกลุ่มโดยอัตโนมัติ.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: จัดกลุ่มรูปร่างใน Word ด้วย Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีจัดกลุ่มรูปทรงใน Word ด้วย Aspose.Words สำหรับ C#
url: /th/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการจัดกลุ่มรูปร่างใน Word ด้วย Aspose.Words สำหรับ C#

หากคุณต้องการ **จัดกลุ่มรูปร่างใน Word** อย่างอัตโนมัติ Aspose.Words ทำให้เรื่องนี้ง่ายขึ้น คู่มือฉบับนี้จะแสดงวิธีสร้างรูปร่างสี่เหลี่ยมสองรูป วางเคียงกัน รวมเข้าด้วยกันเป็น `GroupShape` และบันทึกผลลัพธ์เป็นไฟล์ DOCX

คุณจะได้เห็นตัวอย่างที่สมบูรณ์และสามารถรันได้ คำอธิบายว่าทำไมแต่ละขั้นตอนจึงสำคัญ และเคล็ดลับในการจัดการกรณีขอบทั่วไป เช่น รูปร่างทับกันหรือการกำหนดขนาดแบบไดนามิก เมื่ออ่านจบคู่มือนี้คุณจะสามารถผสานการจัดกลุ่มรูปร่างเข้าไปในโครงการอัตโนมัติของ Word ใด ๆ ได้

## ข้อกำหนดเบื้องต้น

* .NET 6.0 (หรือใหม่กว่า) ติดตั้งแล้ว – Aspose.Words รองรับ .NET Standard 2.0+, .NET Core, และ .NET Framework.
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ประเมินผลชั่วคราว) – ไลบรารีทำงานได้โดยไม่มีใบอนุญาตแต่จะมีลายน้ำ.
* Visual Studio 2022 (หรือ IDE สำหรับ C# ใด ๆ) เพื่อคอมไพล์และรันตัวอย่าง.

ไม่ต้องการแพ็กเกจ NuGet เพิ่มเติมนอกจาก `Aspose.Words`.

## วิธีการจัดกลุ่มรูปร่างใน Word ด้วย Aspose.Words

หัวใจของวิธีแก้คืออ็อบเจ็กต์ **`GroupShape`** ที่ทำหน้าที่เป็นคอนเทนเนอร์สำหรับรูปร่างแต่ละอัน ด้านล่างเราจะแบ่งกระบวนการออกเป็นขั้นตอนที่ชัดเจน

### ขั้นตอนที่ 1: สร้างเอกสารเปล่าและ `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*ทำไมต้องทำขั้นตอนนี้?*  
`Document` แทนไฟล์ DOCX ทั้งหมด ในขณะที่ `DocumentBuilder` ให้เมธอดแบบ fluent (เช่น `InsertShape`) ที่วางองค์ประกอบใหม่โดยอัตโนมัติที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

### ขั้นตอนที่ 2: แทรกรูปร่างสี่เหลี่ยมแรก

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

คำสั่ง `InsertShape` จะเพิ่มรูปร่างลงในเอกสารและคืนค่าอ็อบเจ็กต์ `Shape` ที่คุณสามารถกำหนดค่าเพิ่มเติม (สี, เส้นขอบ ฯลฯ) ขนาดจะระบุเป็นพอยท์ (1 pt ≈ 1/72 in).

### ขั้นตอนที่ 3: แทรกรูปร่างสี่เหลี่ยมที่สองและเลื่อนตำแหน่ง

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

การตั้งค่า `Left` จะกำหนดตำแหน่งของรูปร่างสัมพันธ์กับขอบกระดาษ การเลื่อนต้องมากกว่าความกว้างของรูปร่างแรก (100 pt) เพื่อหลีกเลี่ยงการทับกัน; เราใช้ 120 pt เพื่อเว้นช่องว่างเล็กน้อย

### ขั้นตอนที่ 4: สร้าง `GroupShape` ที่มีขนาดพอสำหรับสี่เหลี่ยมทั้งสอง

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` รับ `Document` เจ้าของและขนาดของคอนเทนเนอร์ ความกว้างของคอนเทนเนอร์ควรมากกว่าขอบขวาที่ไกลที่สุดของรูปร่าง; หากไม่เช่นนั้นรูปร่างที่สองจะถูกตัด

### ขั้นตอนที่ 5: เพิ่มรูปร่างแต่ละอันเข้าไปในกลุ่ม

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

การเพิ่ม (Append) จะย้ายรูปร่างเข้าไปในคอลเลกชันภายในของกลุ่ม หลังจากเรียกนี้รูปร่างจะไม่เป็นอ็อบเจ็กต์อิสระในโครงสร้างต้นไม้ของเอกสารอีกต่อไป – พวกมันเป็นส่วนของกลุ่ม

### ขั้นตอนที่ 6: แทรกรูปร่างที่จัดกลุ่มกลับเข้าสู่เอกสาร

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` จะวาง `GroupShape` ทั้งหมดที่ตำแหน่งเคอร์เซอร์ปัจจุบัน หากคุณต้องการให้กลุ่มอยู่ในย่อหน้าที่กำหนด ให้ย้าย builder ไปยังย่อมนั้นก่อน

### ขั้นตอนที่ 7: บันทึกเอกสาร

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

ไฟล์ที่ได้จะมีสี่เหลี่ยมสองรูปที่ทำงานเป็นอ็อบเจ็กต์เดียว – คุณสามารถย้าย, ปรับขนาด, หรือ ลบ ทั้งสองพร้อมกันใน Microsoft Word

## โค้ดต้นฉบับเต็ม

การรวมทุกขั้นตอนเข้าด้วยกันจะได้โปรแกรมที่ทำงานอิสระ:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** การเปิด *GroupedShapes.docx* ใน Microsoft Word จะแสดงสี่เหลี่ยมสองรูปเคียงกัน ถูกจัดเป็นอ็อบเจ็กต์เดียวที่เลือกได้ การลากกลุ่มจะย้ายสี่เหลี่ยมทั้งสองพร้อมกัน

## ความหลากหลายและกรณีขอบที่พบบ่อย

| Situation | Recommended adjustment |
|-----------|------------------------|
| **มากกว่าสองรูปร่าง** | สร้างอ็อบเจ็กต์ `Shape` เพิ่มเติม, กำหนดตำแหน่งให้เหมาะสม, แล้วเพิ่มแต่ละอันเข้าไปใน `GroupShape` เดียวกัน. |
| **ขนาดไดนามิก** | คำนวณความกว้าง/ความสูงของกลุ่มโดยอิงจากค่ามากสุดของ `Right` และ `Bottom` ของรูปร่างลูก. |
| **ประเภทรูปร่างที่ต่างกัน** | `ShapeType.Ellipse`, `ShapeType.Triangle` เป็นต้น สามารถแทรกได้เช่นเดียวกัน; คอนเทนเนอร์ของกลุ่มไม่สนใจประเภท. |
| **รูปร่างที่หมุน** | ตั้งค่า `shape.Rotation = 45;` ก่อนเพิ่ม; การหมุนจะถูกเก็บไว้ภายในกลุ่ม. |
| **บันทึกเป็น PDF** | เรียก `doc.Save("GroupedShapes.pdf");` – กลุ่มจะคงอยู่ในการแสดงผล PDF. |

**เคล็ดลับ:** หลังจากจัดกลุ่มแล้ว คุณยังสามารถแก้ไขรูปร่างแต่ละอันได้โดยเข้าถึง `group.GetChildNodes(NodeType.Shape, true)` ซึ่งเป็นประโยชน์เมื่อคุณต้องการเปลี่ยนสีเติมของสี่เหลี่ยมหนึ่งโดยไม่ทำลายกลุ่ม

## วิธีตรวจสอบการจัดกลุ่มโดยโปรแกรม

หากคุณต้องการยืนยันว่ารูปร่างถูกจัดกลุ่มอย่างถูกต้อง (เช่น ในการทดสอบหน่วย) ให้ตรวจสอบโครงสร้างต้นไม้ของเอกสาร:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

The output should be:

```
Number of groups: 1
Children in first group: 2
```

นี่เป็นการยืนยันว่า **การจัดกลุ่มรูปร่างใน Word** ถูกสร้างตามที่คาดหวัง

## สรุป

ตอนนี้คุณรู้วิธี **จัดกลุ่มรูปร่างใน Word** ด้วย Aspose.Words สำหรับ C# แล้ว กระบวนการประกอบด้วยการสร้างรูปร่างแต่ละอัน, กำหนดตำแหน่ง, ห่อหุ้มด้วย `GroupShape`, แล้วแทรกกลุ่มกลับเข้าสู่เอกสาร ด้วยตัวอย่างครบถ้วนข้างต้นคุณสามารถขยายเทคนิคนี้ไปยังจำนวนรูปร่างใด ๆ, ประเภทที่แตกต่างกัน, หรือแม้แต่รวมกับกล่องข้อความและรูปภาพ

ต่อไปให้สำรวจหัวข้อที่เกี่ยวข้องเช่น **การจัดกลุ่มรูปร่าง Aspose.Words**, **การจัดการรูปร่าง Word ด้วย C#**, และ **DocumentBuilder insert shape** เพื่อสถานการณ์อัตโนมัติเอกสารขั้นสูง ทดลองใช้การกำหนดขนาดแบบไดนามิก, การจัดกลุ่มตามเงื่อนไข, และการส่งออกเป็น PDF เพื่อใช้ศักยภาพของ Aspose.Words อย่างเต็มที่

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ

- [แทรกรูปร่างในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [สร้างรูปร่างสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [บทแนะนำการเพิ่มเงาให้รูปร่าง Aspose.Words – เพิ่มเงาให้รูปร่าง Word ใน C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}