---
category: general
date: 2026-09-21
description: สร้างเอกสาร Word ว่างโดยใช้ Aspose.Words ตั้งขนาดรูปทรง ตั้งตำแหน่งรูปทรง
  ตั้งสีรูปทรง และบันทึกไฟล์ docx ในขั้นตอนเดียว
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: th
lastmod: 2026-09-21
og_description: สร้างเอกสาร Word เปล่า ตั้งค่าขนาดรูปทรง ตั้งค่าตำแหน่งรูปทรง ตั้งค่าสีรูปทรง
  และบันทึกไฟล์ docx ด้วย Aspose.Words ภายในไม่กี่นาที.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: สร้างเอกสาร Word ว่างและเพิ่มรูปทรงสี – คู่มือ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: สร้างเอกสาร Word ว่างและเพิ่มรูปทรงสีด้วย Aspose.Words
url: /th/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word ว่างและเพิ่มรูปทรงสีด้วย Aspose.Words

หากคุณต้องการ **สร้างเอกสาร Word ว่าง** อย่างอัตโนมัติ คู่มือนี้จะแสดงวิธีทำด้วย Aspose.Words คุณจะได้เรียนรู้วิธี **ตั้งค่าขนาดรูปทรง**, **ตั้งค่าตำแหน่งรูปทรง**, **ตั้งค่าสีรูปทรง**, และสุดท้าย **บันทึกไฟล์ docx** โดยไม่ต้องออกจาก IDE ของคุณ

การทำงานกับไฟล์ Word ใน C# มักหมายถึงการจัดการกับการเรียกใช้ OpenXML ระดับต่ำ, แต่ Aspose.Words จะทำให้ซับซ้อนนั้นง่ายขึ้น เมื่อจบบทเรียนนี้คุณจะมีไฟล์ `.docx` ที่ทำงานได้เต็มรูปแบบซึ่งมีรูปทรงกลุ่มที่ประกอบด้วยสี่เหลี่ยมสีสองอัน—เหมาะสำหรับรายงาน, ใบรับรอง, หรือเทมเพลตที่กำหนดเอง

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 หรือใหม่กว่า (ติดตั้งผ่าน NuGet: `Install-Package Aspose.Words`)
- ความคุ้นเคยพื้นฐานกับ C# และ Visual Studio (หรือเครื่องมือแก้ไข C# ใด ๆ)

ไม่จำเป็นต้องมีไฟล์ Word อยู่แล้ว; บทเรียนนี้เริ่มต้นด้วยการ **สร้างเอกสาร Word ว่าง** ตั้งแต่ต้น

## สร้างเอกสาร Word ว่างด้วย Aspose.Words

ขั้นตอนแรกคือการสร้างอ็อบเจกต์ `Document` นี้เป็นอ็อบเจกต์ที่แทนไฟล์ Word ว่างในหน่วยความจำ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` เริ่มต้นเป็นไฟล์ว่าง ซึ่งเป็นสิ่งที่คุณต้องการเมื่อ **สร้างเอกสาร Word ว่าง** `builder` จะถูกใช้ต่อไปเพื่อแทรกกลุ่มรูปทรงที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

## ตั้งค่าขนาดรูปทรงและสร้าง GroupShape

`GroupShape` ทำงานเหมือนคอนเทนเนอร์ที่สามารถบรรจุรูปทรงหลายรูปได้ ก่อนอื่นกำหนดมิติรวมของคอนเทนเนอร์

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

ที่นี่เรา **ตั้งค่าขนาดรูปทรง** สำหรับกลุ่มเอง (300 × 200) ชื่อคุณสมบัติเดียวกัน (`Width`, `Height`) ถูกใช้กับแต่ละรูปทรงย่อย ทำให้คุณควบคุมแต่ละองค์ประกอบได้อย่างละเอียด

## เพิ่มสี่เหลี่ยมแรกและตั้งค่าสีรูปทรง

ตอนนี้เพิ่มสี่เหลี่ยมลงในกลุ่มและกำหนดสีพื้นหลังให้มัน

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

คุณสมบัติ `FillColor` **ตั้งค่าสีรูปทรง** การใช้ `System.Drawing.Color` ทำให้คุณเลือกค่า ARGB ที่กำหนดไว้ล่วงหน้าหรือกำหนดเองได้

## เพิ่มสี่เหลี่ยมที่สอง, ตั้งค่าขนาด, ตำแหน่ง, และสีของมัน

สี่เหลี่ยมที่สองแสดงวิธี **ตั้งค่าตำแหน่งรูปทรง** relativo กับกลุ่มและวิธีเปลี่ยนสีของมัน

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

เนื่องจากความกว้างของกลุ่มคือ 300 พอยต์ สี่เหลี่ยม 120‑พอยต์สองอันจึงวางได้อย่างสบายด้วยช่องว่าง 30‑พอยต์ ปรับค่า `Left` และ `Top` หากต้องการจัดวางแบบอื่น

## แทรก GroupShape ลงในเอกสาร

เมื่อกลุ่มตั้งค่าเสร็จสมบูรณ์ ให้วางมันที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` เขียนรูปทรงโดยตรงลงในเนื้อหาเอกสาร, รักษา **ตำแหน่งรูปทรงที่ตั้งค่า** ที่คุณกำหนดไว้ก่อนหน้าอย่างแม่นยำ

## บันทึกไฟล์ docx

ขั้นตอนสุดท้ายคือการบันทึกเอกสารลงดิสก์ นี่เป็นการสาธิตการทำงาน **บันทึกไฟล์ docx**

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

หลังจากรันโปรแกรม, เปิด `GroupShape.docx` ใน Microsoft Word คุณควรเห็นหน้าว่างที่มีรูปทรงกลุ่มประกอบด้วยสี่เหลี่ยมสีสองอันที่วางเคียงกัน

### ผลลัพธ์ที่คาดหวัง

- ไฟล์ `.docx` หนึ่งหน้าเดียว
- หน้านั้นมีรูปทรงกลุ่มตั้งอยู่ 100 พอยต์จากขอบซ้ายและบน
- ภายในกลุ่ม, มีสี่เหลี่ยมสีฟ้าอ่อนอยู่ด้านซ้าย, และสี่เหลี่ยมสีโค랄อ่อนอยู่ด้านขวา, แต่ละอันขนาด 120 × 80 พอยต์

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปพลิเคชันคอนโซลได้ ไม่ต้องใช้ไฟล์เพิ่มเติม

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

การรันโปรแกรมนี้จะสร้างเอกสารที่อธิบายไว้ข้างต้นอย่างแม่นยำ, ครอบคลุมเป้าหมายสี่ประการ: **สร้างเอกสาร Word ว่าง**, **ตั้งค่าขนาดรูปทรง**, **ตั้งค่าตำแหน่งรูปทรง**, **ตั้งค่าสีรูปทรง**, และ **บันทึกไฟล์ docx**

## การปรับเปลี่ยนทั่วไปและกรณีขอบ

| สถานการณ์ | สิ่งที่ต้องเปลี่ยน | เหตุผลที่สำคัญ |
|----------|----------------|----------------|
| **ประเภทรูปทรงที่แตกต่าง** | แทนที่ `ShapeType.Rectangle` ด้วย `ShapeType.Ellipse`, `ShapeType.Triangle` เป็นต้น | ช่วยให้คุณสร้างกราฟิกที่ซับซ้อนมากขึ้นโดยไม่ต้องใช้รูปภาพภายนอก |
| **มิติแบบไดนามิก** | คำนวณ `Width` และ `Height` จากการป้อนของผู้ใช้หรือไฟล์กำหนดค่า | ทำให้โซลูชันสามารถนำกลับมาใช้ใหม่ได้ในหลายเทมเพลตของเอกสาร |
| **บันทึกเป็น PDF** | เรียก `document.Save("output.pdf", SaveFormat.Pdf);` | หากผู้รับต้องการรูปแบบที่ไม่สามารถแก้ไขได้ PDF เป็นตัวเลือกที่ปลอดภัย |
| **เพิ่มข้อความภายในรูปทรง** | สร้างรูปทรง `TextBox` และกำหนด `TextBox.Text` | มีประโยชน์สำหรับการสร้างแบดจ์หรือคอลเอาต์ที่มีป้ายกำกับ |
| **หลายกลุ่มบนหน้าเดียว** | ทำซ้ำขั้นตอนที่ 2‑5 ด้วยค่า `Left`/`Top` ที่แตกต่างกัน | ทำให้คุณสร้างแดชบอร์ดหรือเลเอาต์หลายส่วนได้ |

### เคล็ดลับพิเศษ

เมื่อคุณต้องการจัดตำแหน่งรูปทรงอย่างแม่นยำ, ใช้คุณสมบัติ `ShapeBase.WrapType = WrapType.Inline` ก่อนแทรกกลุ่ม นี้จะบังคับให้กลุ่มทำงานเหมือนย่อหน้า, ป้องกันการไหลของข้อความที่ไม่คาดคิดรอบๆ

## สรุป

ตอนนี้คุณรู้วิธี **สร้างเอกสาร Word ว่าง** ด้วย Aspose.Words, **ตั้งค่าขนาดรูปทรง**, **ตั้งค่าตำแหน่งรูปทรง**, **ตั้งค่าสีรูปทรง**, และ **บันทึกไฟล์ docx** ตัวอย่างเต็มแสดงรูปแบบที่สะอาดและนำกลับมาใช้ใหม่ได้สำหรับการเพิ่มกราฟิกกลุ่มลงในโครงการอัตโนมัติของ Word ใด ๆ

จากนี้คุณสามารถสำรวจต่อได้:

- เพิ่มรูปทรงหรือรูปภาพเพิ่มเติมใน `GroupShape` เดียว (**ตั้งค่าขนาดรูปทรง**, **ตั้งค่าสีรูปทรง** แบบต่าง ๆ)
- ใช้ `ShapeBase.Rotation` เพื่อหมุนสี่เหลี่ยมสำหรับเอฟเฟกต์ตกแต่ง
- ส่งออกเอกสารเดียวกันเป็น PDF หรือ HTML เพื่อขยายการกระจาย (**บันทึกไฟล์ docx** ทางเลือก)

คุณสามารถทดลองใช้สี, ขนาด, และตรรกะการจัดวางที่แตกต่างเพื่อให้ตรงกับความต้องการการรายงานหรือเทมเพลตของคุณได้อย่างอิสระ ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการนำไปใช้แบบทางเลือกในโครงการของคุณ

- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words สำหรับ .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [สร้างรูปทรงสี่เหลี่ยมใน Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [บทแนะนำ Shape Shadow ของ Aspose.Words – เพิ่มเงาให้รูปทรง Word ใน C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}