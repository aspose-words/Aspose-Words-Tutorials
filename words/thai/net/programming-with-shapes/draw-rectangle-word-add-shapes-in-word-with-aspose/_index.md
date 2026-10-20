---
category: general
date: 2026-07-29
description: วาดสี่เหลี่ยมใน Word ด้วย Aspose.Words. เรียนรู้วิธีเพิ่มรูปทรงสี่เหลี่ยม,
  เพิ่มรูปทรงเส้น, และจัดการหลายรูปทรงใน Word ในเอกสารเดียว.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: th
lastmod: 2026-07-29
og_description: วาดสี่เหลี่ยมใน Word ด้วย Aspose.Words. ทำตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อเพิ่มรูปสี่เหลี่ยม,
  เพิ่มรูปเส้น, และทำงานกับหลายรูปใน Word อย่างง่ายดาย.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: วาดสี่เหลี่ยมใน Word – เชี่ยวชาญการเพิ่มรูปร่างใน Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: วาดสี่เหลี่ยมใน Word – เพิ่มรูปทรงใน Word ด้วย Aspose
url: /th/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – คู่มือฉบับสมบูรณ์สำหรับการเพิ่มรูปทรงใน Word

เคยสงสัยไหมว่า如何 **draw rectangle word** เอกสารโดยไม่ต้องเปิด UI ทุกครั้ง? คุณไม่ได้เป็นคนเดียวที่คิดเช่นนั้น. นักพัฒนาจำนวนมากต้องการสร้างไฟล์ Word อย่างรวดเร็ว, และวิธีที่ง่ายที่สุดคือให้ไลบรารีทำงานหนักแทน. ในบทแนะนำนี้เราจะแสดงให้คุณเห็นอย่างชัดเจน **วิธีเพิ่มรูปทรง**—โดยเฉพาะสี่เหลี่ยมผืนผ้าและเส้น—โดยใช้ Aspose.Words for .NET, และเราจะเน้นที่วลี *draw rectangle word* เพื่อให้คุณไม่หลง.

คิดว่ามันเป็นสตูดิโอศิลปะขนาดเล็กที่อยู่ภายในโค้ดของคุณ. เมื่อจบคุณจะสามารถ **add rectangle shape**, **add line shape**, และแม้กระทั่งรวมพวกมันเป็นกลุ่ม **multiple shapes word**. ไม่มี UI, ไม่มีการปรับแต่งด้วยมือ, เพียงแค่ C# ที่สะอาดและทำซ้ำได้.

## สิ่งที่คุณจะได้เรียนรู้

- ตั้งค่าเอกสาร Word ใหม่ด้วย Aspose.Words.  
- สร้าง **GroupShape** ที่สามารถเก็บหลายวัตถุ.  
- **add rectangle shape** และ **add line shape** ภายในกลุ่มนั้น.  
- แทรกรูปทรงที่จัดกลุ่มลงในส่วนเนื้อหาเอกสาร.  
- บันทึกไฟล์และดูผลลัพธ์ทันที.  

หากคุณคุ้นเคยกับ C# เบื้องต้นและมีสำเนาของ Aspose.Words, คุณพร้อมแล้ว. ไม่จำเป็นต้องใช้แพ็กเกจ NuGet เพิ่มเติมนอกจากไลบรารีหลัก.

> **เคล็ดลับ:** Aspose.Words ทำงานกับ .NET 6, .NET 7, และ .NET Framework 4.6+. เลือก runtime ที่ตรงกับโปรเจกต์ของคุณ.

![ตัวอย่าง draw rectangle word](https://example.com/placeholder-image.png "draw rectangle word – รูปทรงที่จัดกลุ่มในไฟล์ Word")

## draw rectangle word – การตั้งค่าเอกสาร

ก่อนที่เราจะ **draw rectangle word** เราต้องมีผืนผ้าใบที่สะอาด. คลาส `Document` คือผืนผ้าใบนั้น; `DocumentBuilder` คือแปรงของเรา.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

สองบรรทัดด้านบนให้เราได้ไฟล์ `.docx` ใหม่ในหน่วยความจำ. ยังไม่มีการเขียนใด ๆ ไปยังดิสก์, ซึ่งหมายความว่าเราสามารถทดลองได้โดยไม่ทำให้ระบบไฟล์รก.

## วิธีเพิ่มรูปทรง – การสร้างคอนเทนเนอร์ GroupShape

เมื่อคุณต้องการให้ **multiple shapes word** ทำงานเป็นหน่วยเดียว—เคลื่อนที่พร้อมกัน, หมุนพร้อมกัน—คุณจะห่อหุ้มพวกมันใน `GroupShape`. คิดว่ากลุ่มเป็นโฟลเดอร์ที่เก็บรูปทรงอื่น ๆ.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

ทำไมต้องเป็นกลุ่ม? เพราะต่อมาคุณอาจต้องการ **add rectangle shape** และ **add line shape** แล้วย้ายพวกมันพร้อมกัน. หากไม่มีกลุ่ม, คุณจะต้องปรับตำแหน่งแต่ละรูปทรงแยกกัน.

## add rectangle shape – การแทรกสี่เหลี่ยมผืนผ้าในกลุ่ม

ตอนนี้คอนเทนเนอร์มีอยู่แล้ว, มา **add rectangle shape** กัน. สี่เหลี่ยมผืนผ้าเป็น `Shape` ที่ `ShapeType` เป็น `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

สังเกตว่า ค่า `Left` และ `Top` เป็นค่าที่สัมพันธ์กับจุดเริ่มต้นของกลุ่ม, ไม่ใช่หน้า. สิ่งนี้ทำให้จัดตำแหน่งรูปทรงได้อย่างแม่นยำ. สี่เหลี่ยมผืนผ้าจะปรากฏใกล้มุมบน‑ซ้ายของกลุ่ม.

## add line shape – การเพิ่มเส้นในกลุ่มเดียวกัน

เส้นเป็นเพียง `Shape` อีกอันหนึ่ง, แต่ `ShapeType` ของมันคือ `Line`. เราจะวางตำแหน่งมันใต้สี่เหลี่ยมผืนผ้า.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

เนื่องจากความสูงของเส้นเป็นศูนย์, คุณสมบัติ `Top` กำหนดตำแหน่งแนวตั้งของเส้น. `Width` ควบคุมความยาวของเส้นในแนวนอน.

## multiple shapes word – การแทรกกลุ่มลงในส่วนเนื้อหาเอกสาร

เรามีกลุ่มที่ตอนนี้เก็บ **add rectangle shape** และ **add line shape**. ขั้นตอนสุดท้ายคือใส่ทั้งหมดลงในเอกสาร.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` วางกลุ่มตรงตำแหน่งที่ `DocumentBuilder` อยู่ในขณะนั้น. หากคุณต้องการให้มันอยู่ในย่อหน้าที่ระบุ, ให้ย้าย builder ด้วย `builder.MoveToParagraph(index)` ก่อน.

## การบันทึกผลลัพธ์ – ดูผลลัพธ์ draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

เปิดไฟล์ที่สร้างขึ้นใน Microsoft Word แล้วคุณจะเห็นกลุ่มเดียวที่มีสี่เหลี่ยมผืนผ้าและเส้น. คุณสามารถคลิกกลุ่ม, ลากมัน, หรือแม้กระทั่งปรับขนาด—รูปทรงทั้งหมดจะเคลื่อนที่พร้อมกัน. นั่นคือพลังของ **multiple shapes word**.

### ผลลัพธ์ที่คาดหวัง

- ไฟล์ `.docx` ชื่อ `GroupShape.docx`.  
- หนึ่งหน้าโดยมีสี่เหลี่ยมผืนผ้าจัดกลุ่ม (120 × 80 pt) ใกล้มุมบน‑ซ้าย.  
- เส้นแนวนอน (ยาว 150 pt) อยู่ใต้สี่เหลี่ยมผืนผ้า.  
- ทั้งสองรูปทรงสามารถเลือกได้เป็นอ็อบเจ็กต์เดียว.

หากคุณดับเบิลคลิกที่กลุ่ม, Word จะให้คุณแก้ไขแต่ละรูปทรงแยกกัน—เหมาะสำหรับการปรับแต่งละเอียด.

## คำถามทั่วไป & กรณีขอบ

**ถ้าฉันต้องการมากกว่าสองรูปทรง?**  
เพียงเรียก `group.AppendChild(yourShape)` ต่อไปสำหรับแต่ละอ็อบเจ็กต์เพิ่มเติม. กลุ่มสามารถเก็บรูปทรงจำนวนใดก็ได้, ทำให้เหมาะกับไดอะแกรมที่ซับซ้อน.

**ฉันสามารถเปลี่ยนสีเติมของสี่เหลี่ยมผืนผ้าได้หรือไม่?**  
ได้แน่นอน. หลังจากสร้างสี่เหลี่ยมผืนผ้า, ตั้งค่า `rectangle.FillColor = System.Drawing.Color.LightBlue;`. วิธีนี้ทำงานกับรูปทรงใด ๆ ที่รองรับการเติมสี.

**ฉันต้องตั้งค่า `Height = 0` สำหรับเส้นหรือไม่?**  
ใช่, สำหรับเส้นแนวนอนตรง ความสูงควรเป็นศูนย์. สำหรับเส้นแนวตั้ง, ตั้งค่า `Width = 0` และให้ `Height` มีค่าบวก.

**วิธีนี้จะทำงานกับไฟล์ .doc (Word 97‑2003) หรือไม่?**  
Aspose.Words สามารถบันทึกเป็นรูปแบบ `.doc` เก่าได้, แต่บางคุณสมบัติของรูปทรงสมัยใหม่อาจถูกจำกัด. ควรใช้ `.docx` เพื่อความสมบูรณ์เต็มรูปแบบ.

**ฉันจะหมุนกลุ่มทั้งหมดอย่างไร?**  
คุณสามารถตั้งค่า `group.Rotation = 45;` (องศา) ก่อนแทรก. การหมุนจะใช้กับรูปทรงลูกทุกอัน.

## สรุป – วิธีเพิ่มรูปทรงใน Word ด้วยโปรแกรม

- **draw rectangle word** เริ่มต้นด้วยการสร้าง `Document` และ `DocumentBuilder`.  
- สร้าง **GroupShape** เพื่อเก็บ **multiple shapes word**.  
- **add rectangle shape** และ **add line shape** ถูกเพิ่มเข้าไปในกลุ่ม.  
- แทรกกลุ่มลงในส่วนเนื้อหาด้วย `builder.InsertNode`.  
- บันทึกไฟล์และเปิดเพื่อยืนยันผลลัพธ์ภาพ.

นี่คือกระบวนการทำงานทั้งหมด, ถูกจัดเป็นโค้ดรายการเดียวที่อ่านง่าย.

## ขั้นตอนต่อไป & หัวข้อที่เกี่ยวข้อง

เมื่อคุณรู้ **how to add shapes** แล้ว, พิจารณาสำรวจ:

- **add rectangle shape** พร้อมมุมโค้ง (`ShapeType.Rectangle` + `CornerRadius`).  
- การจัดรูปแบบเส้นด้วยรูปแบบ dash ที่แตกต่าง (`line.LineFormat.DashStyle`).  
- ฝังรูปภาพพร้อมกับรูปทรงเพื่อรายงานที่สมบูรณ์ยิ่งขึ้น.  
- ใช้ **multiple shapes word** เพื่อสร้างแผนผังหรือไดอะแกรม UML อย่างง่าย.  

แต่ละหัวข้อเหล่านี้ต่อยอดจากพื้นฐานที่เรานำเสนอที่นี่อย่างเป็นธรรมชาติ, และทั้งหมดใช้รูปแบบเดียวกันของการสร้างรูปทรง, การกำหนดค่า, และการจัดกลุ่มหากจำเป็น.

---

ขอให้เขียนโค้ดอย่างสนุก! หากคุณเจอปัญหาหรือมีกรณีการใช้งานที่เจ๋งอยากแชร์, ฝากคอมเมนต์ด้านล่าง. ความคิดเห็นของคุณช่วยให้เราทุกคนเชี่ยวชาญศิลปะของ **draw rectangle word** และต่อไป.

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แหล่งข้อมูลแต่ละรายการมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจกต์ของคุณ.

- [สร้างสี่เหลี่ยมผืนผ้าใน Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [สร้างสี่เหลี่ยมผืนผ้าใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [แทรกรูปทรงในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}