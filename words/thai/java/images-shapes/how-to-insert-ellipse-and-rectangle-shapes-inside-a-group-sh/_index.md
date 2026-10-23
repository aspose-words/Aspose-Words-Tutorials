---
category: general
date: 2026-10-23
description: เรียนรู้วิธีแทรกรูปวงรีและวิธีเพิ่มรูปสี่เหลี่ยมใน Word โดยใช้ Aspose.Words
  รวมถึงการย้ายเคอร์เซอร์ไปยังรูปและวิธีสร้างรูปกลุ่ม
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: th
lastmod: 2026-10-23
og_description: วิธีแทรกรูปวงรีและวิธีเพิ่มรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words.
  ทำตามคำแนะนำทีละขั้นตอนเพื่อย้ายเคอร์เซอร์ไปยังรูปและสร้างกลุ่มรูป.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: วิธีแทรกรูปวงรีและสี่เหลี่ยมในกลุ่มรูปร่างของ Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีแทรกรูปวงรีและสี่เหลี่ยมภายในกลุ่มรูปทรงด้วย Aspose.Words
url: /th/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทรกรูปวงรีและสี่เหลี่ยมภายในรูปกลุ่มด้วย Aspose.Words

หากคุณต้องการทราบ **วิธีแทรกรูปวงรี** ในเอกสาร Word อย่างโปรแกรมมิ่ง คู่มือนี้จะแสดงขั้นตอนทั้งหมด คุณจะได้เห็น **วิธีเพิ่มรูปสี่เหลี่ยม** เรียนรู้ **การย้ายเคอร์เซอร์ไปยังรูป** และค้นพบ **วิธีสร้างรูปกลุ่ม** ที่บรรจุวัตถุการวาดหลายรายการ

การทำอัตโนมัติของ Word มักต้องการการจัดตำแหน่งวัตถุการวาดอย่างแม่นยำ เมื่อจบบทเรียนนี้คุณจะสามารถสร้างไฟล์ `.docx` ที่มีสี่เหลี่ยมและวงรีเป็นกลุ่ม พร้อมสำหรับการจัดสไตล์หรือการส่งออกต่อไป ไม่จำเป็นต้องใช้เครื่องมือภายนอกใด ๆ นอกจากไลบรารี Aspose.Words for .NET และสภาพแวดล้อมการพัฒนา .NET

## ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า ติดตั้งแล้ว
* Aspose.Words for .NET (แพ็กเกจ NuGet `Aspose.Words`) เพิ่มเข้าในโปรเจกต์ของคุณ
* ความรู้พื้นฐานเกี่ยวกับไวยากรณ์ C# และ Visual Studio (หรือ IDE ใดก็ได้)

ข้อกำหนดเหล่านี้ทำให้โค้ดคอมไพล์ได้โดยไม่ต้องกำหนดค่าเพิ่มเติม

## วิธีสร้างรูปกลุ่มใน Word

รูปกลุ่มทำหน้าที่เป็นคอนเทนเนอร์ที่ให้คุณย้าย, หมุน หรือจัดรูปแบบหลายรูปเป็นหน่วยเดียว โค้ดต่อไปนี้สร้างรูปกลุ่มที่มีขนาดเฉพาะ (300 × 200 points) และเตรียมเอกสารสำหรับการดำเนินการวาดต่อไป

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*ทำไมขั้นตอนนี้ถึงสำคัญ*: รูปกลุ่มกำหนดระบบพิกัดท้องถิ่น รูปทั้งหมดที่เพิ่มหลังจากย้ายเคอร์เซอร์เข้าไปในกลุ่มจะถูกวางตำแหน่งสัมพันธ์กับจุดเริ่มต้นของกลุ่ม ทำให้การคำนวณการจัดวางเป็นเรื่องง่าย

## วิธีเพิ่มรูปสี่เหลี่ยมใน Word

เมื่อรูปกลุ่มมีอยู่แล้ว คุณสามารถ **แทรกรูปสี่เหลี่ยม** ภายในได้ สี่เหลี่ยมจะทำหน้าที่เป็นพื้นหลังหรือที่วางภาพสำหรับเนื้อหาอื่น

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*คำอธิบาย*: `MoveTo(group)` บอกให้ builder ทราบว่าจุดแทรกที่ใช้งานอยู่คือรูปกลุ่ม หากไม่ย้ายเคอร์เซอร์ `InsertShape` จะเพิ่มสี่เหลี่ยมเข้าไปในส่วนหลักของเอกสารแทนที่จะเป็นในกลุ่ม

## วิธีแทรกรูปวงรี

เมื่อสี่เหลี่ยมอยู่ในตำแหน่งแล้ว คุณสามารถสาธิต **วิธีแทรกรูปวงรี** ได้ วงรีจะอยู่ตรงกลางภายในกลุ่มเดียวกัน หากต้องการสามารถทับกับสี่เหลี่ยมได้

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*ทำไมต้องย้ายเคอร์เซอร์*: ทุกการเรียก `InsertShape` จะเคารพตำแหน่งเคอร์เซอร์ปัจจุบัน การเรียก `MoveTo(group)` อีกครั้งรับประกันว่าวงรีก็เป็นลูกของกลุ่มเช่นกัน ทำให้ลำดับชั้นตามที่ต้องการคงไว้

## ย้ายเคอร์เซอร์ไปยังรูปก่อนแทรกวัตถุเพิ่มเติม

หากคุณต้องการเพิ่มรูปเพิ่มเติมในภายหลัง ให้ **ย้ายเคอร์เซอร์ไปยังรูป** ก่อนการแทรกทุกครั้ง รูปแบบนี้ช่วยหลีกเลี่ยงการวางโดยบังเอิญนอกกลุ่ม

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*เคล็ดลับ*: การใช้ซ้ำ `MoveTo(group)` มีค่าใช้จ่ายต่ำและช่วยให้โค้ดอ่านง่ายขึ้น นอกจากนี้ยังทำให้การบำรุงรักษาในอนาคตง่ายกว่าเพราะบริบทการแทรกชัดเจน

## บันทึกเอกสาร

สุดท้าย ให้บันทึกเอกสารลงดิสก์ ตัวอย่างบันทึกไฟล์เป็น `GroupShape.docx` ในโฟลเดอร์ที่คุณระบุ

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

เมื่อคุณเปิดไฟล์ที่บันทึกไว้ใน Microsoft Word คุณจะเห็นกลุ่มเดียวที่บรรจุสี่เหลี่ยมและวงรี ทั้งสองอยู่ในตำแหน่งที่ถูกต้อง

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ `.docx` ชื่อ `GroupShape.docx`
* ภายในเอกสาร มีวัตถุการวาดแบบกลุ่มขนาด 300 × 200 points
* ภายในกลุ่ม:
  * สี่เหลี่ยม (100 × 50 points) อยู่ที่จุดเริ่มต้นของกลุ่ม
  * วงรี (80 × 80 points) ทับกับสี่เหลี่ยม
  * รูปเพิ่มเติมใด ๆ ที่คุณเพิ่มหลังจากย้ายเคอร์เซอร์

## ความแตกต่างทั่วไปและกรณีขอบ

| สถานการณ์ | แนวทางที่แนะนำ |
|-----------|----------------------|
| **ขนาดหน่วยที่แตกต่าง** | Aspose.Words ใช้หน่วย points (1 pt = 1/72 in). แปลงเซนติเมตรหรืออินช์เป็น points ก่อนเรียก `InsertShape`. |
| **การหมุนรูปภายในกลุ่ม** | หลังจากแทรกรูป ให้ดึงอ็อบเจ็กต์ `ShapeBase` ของมันและตั้งค่า `ShapeBase.RotationAngle`. |
| **การเพิ่มข้อความภายในรูป** | ใช้ `ShapeBase.AppendChild(new Paragraph(document))` แล้วเพิ่ม `Run` พร้อมข้อความที่ต้องการ. |
| **บันทึกเป็น PDF แทน DOCX** | เรียก `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – ลำดับชั้นของกลุ่มจะถูกเก็บไว้ในผลลัพธ์ PDF. |

ความแตกต่างเหล่านี้แสดงให้เห็นว่าตรรกะ **วิธีแทรกรูปวงรี** เดียวกันสามารถปรับใช้กับหลายสถานการณ์ในโลกจริงได้

## เคล็ดลับระดับมืออาชีพ

* **ใช้ `DocumentBuilder` ตัวเดียวกันซ้ำ** – ช่วยลดภาระหน่วยความจำและทำให้สถานะของเอกสารสอดคล้องกัน
* **ตรวจสอบขนาดของรูป** – ความกว้างหรือความสูงที่ใหญ่มากอาจทำให้การแสดงผลมีปัญหาใน Word รุ่นเก่า
* **จัดกลุ่มก่อนการจัดสไตล์** – การกำหนดสีเติมหรือสไตล์เส้นให้กับกลุ่มหลังจากเพิ่มลูกทั้งหมดแล้ว จะทำให้ลักษณะดูสม่ำเสมอ

## สรุป

ตอนนี้คุณเข้าใจ **วิธีแทรกรูปวงรี** และ **วิธีเพิ่มรูปสี่เหลี่ยม** ภายในคอนเทนเนอร์ที่จัดกลุ่มในเอกสาร Word ด้วย Aspose.Words การ **ย้ายเคอร์เซอร์ไปยังรูป** อย่างสม่ำเสมอก่อนการแทรกแต่ละครั้งช่วยให้คุณรักษาลำดับชั้นที่เป็นระเบียบและหลีกเลี่ยงการวางโดยบังเอิญ ตัวอย่างเต็มทำงานได้ คอมไพล์และรันได้ และสร้างรูปกลุ่มที่สามารถปรับแต่งหรือส่งออกต่อได้

พร้อมสำรวจต่อหรือยัง? ลองผสานเทคนิคนี้กับ **วิธีสร้างรูปกลุ่ม** เพื่อสร้างแผนภาพซับซ้อน หรือทดลอง **แทรกรูปสี่เหลี่ยมใน Word** ร่วมกับกล่องข้อความเพื่อสร้างรายงานที่หลากหลาย สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ

- [วิธีสร้างรูปสี่เหลี่ยมและรูปกลุ่มใน Word ด้วย Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [วิธีสร้างเอกสาร Word เปล่าและเพิ่มรูปวงรีซ่อนใน C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [วิธีสร้างรูปกลุ่ม docx และเพิ่มคอนโทรลแบบโต้ตอบใน C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}