---
category: general
date: 2026-09-30
description: จัดกลุ่มรูปร่างใน Word ด้วย C# – เรียนรู้วิธีจัดกลุ่มรูปร่าง, เพิ่มสี่เหลี่ยมและวงรี,
  และแทรกรูปร่างสี่เหลี่ยมในเอกสาร Word อย่างอัตโนมัติ
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: th
lastmod: 2026-09-30
og_description: จัดกลุ่มรูปทรงใน Word ด้วย C# และ Aspose.Words. ทำตามคู่มือฉบับเต็มนี้เพื่อเพิ่มสี่เหลี่ยม,
  เพิ่มวงรี, และเรียนรู้วิธีจัดกลุ่มรูปทรงอย่างมีประสิทธิภาพ.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: จัดกลุ่มรูปร่างใน Word ด้วย C# – คู่มือทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีจัดกลุ่มรูปทรงใน Word ด้วย C# และ Aspose.Words
url: /th/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการจัดกลุ่มรูปร่างใน Word ด้วย C# และ Aspose.Words

หากคุณต้องการ **จัดกลุ่มรูปร่างใน Word** ด้วยโปรแกรม การแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนอย่างละเอียด คุณจะได้เรียนรู้วิธีเพิ่มสี่เหลี่ยม, เพิ่มวงรี, แล้วรวมพวกมันเป็นกลุ่มรูปร่างเดียวโดยใช้ไลบรารี Aspose.Words สำหรับ .NET

การทำงานกับรูปร่างเป็นความต้องการทั่วไปเมื่อสร้างรายงาน, สัญญา, หรือสื่อการตลาดโดยอัตโนมัติ เมื่อจบบทเรียนนี้คุณจะมีเมธอด C# ที่สามารถโหลดไฟล์ DOCX, แทรกสี่เหลี่ยมและวงรี, จัดกลุ่มพวกมัน, และบันทึกผลลัพธ์—ทั้งหมดโดยไม่ต้องเปิด Word ด้วยตนเอง

## ความต้องการเบื้องต้น

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า  
* สภาพแวดล้อมการพัฒนา เช่น Visual Studio 2022 (รุ่น Community ใช้งานได้)  
* ไลเซนส์ Aspose.Words for .NET หรือสำเนาประเมินผลฟรี (API ทำงานได้โดยไม่มีไลเซนส์แต่จะมีลายน้ำ)  

คุณยังต้องมีไฟล์ Word ต้นฉบับ (`input.docx`) อยู่ในโฟลเดอร์ที่สามารถอ้างอิงจากโค้ดได้ ไฟล์เอกสารอาจเป็นไฟล์เปล่า; บทเรียนนี้มุ่งเน้นที่การจัดการรูปร่าง

## ขั้นตอนที่ 1: สร้างโปรเจกต์คอนโซลใหม่และเพิ่ม Aspose.Words

เปิดเทอร์มินัลหรือ Visual Studio command prompt แล้วรัน:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

คำสั่งนี้จะสร้างแอปพลิเคชันคอนโซลใหม่ชื่อ **WordShapeDemo** และเพิ่มแพคเกจ NuGet `Aspose.Words` ซึ่งประกอบด้วยคลาส `Document` และ `DocumentBuilder` ที่ใช้จัดการไฟล์ Word

## ขั้นตอนที่ 2: โหลดหรือสร้างเอกสาร

การดำเนินการแรกเมื่อทำงานกับ **group shapes in Word** คือการได้อ็อบเจ็กต์ `Document` คุณสามารถโหลดไฟล์ DOCX ที่มีอยู่หรือเริ่มจากเอกสารเปล่าได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

คลาส `Document` แทนไฟล์ Word ทั้งหมด การโหลดไฟล์จะให้ “ผ้าใบ” พร้อมสำหรับการแทรกรูปร่าง

## ขั้นตอนที่ 3: เริ่มกลุ่มรูปร่าง

*group shape* ทำให้คุณสามารถจัดการหลายรูปร่างอิสระเป็นหน่วยเดียว—เหมาะสำหรับการย้ายหรือปรับขนาดพร้อมกัน เพื่อเริ่มกลุ่ม ให้เรียก `StartGroupShape()` บน `DocumentBuilder`

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

การเรียก `StartGroupShape` จะบอก Aspose.Words ว่ารูปร่างทุกชิ้นที่แทรกต่อจากนี้เป็นส่วนหนึ่งของกลุ่มเดียวกันจนกว่าจะเรียก `EndGroupShape`

## ขั้นตอนที่ 4: วิธีการเพิ่มสี่เหลี่ยมใน Word

เมื่อกลุ่มเปิดอยู่แล้ว ให้แทรกสี่เหลี่ยม วิธี `InsertShape` รับค่า `ShapeType` enum ตามด้วยความกว้างและความสูง (หน่วยเป็นพอยต์)

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

สี่เหลี่ยมจะกลายเป็นสมาชิกคนแรกของกลุ่ม คุณสามารถปรับสีเติม, เส้นขอบ, หรือข้อความภายหลังได้ตามต้องการ

## ขั้นตอนที่ 5: วิธีการเพิ่มวงรีใน Word

ต่อไปให้เพิ่มวงรี (จะเป็นวงกลมเมื่อความกว้างเท่ากับความสูง) ตัวอย่างนี้แสดง **วิธีการเพิ่มวงรี** ด้วย builder เดียวกัน

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

ตอนนี้รูปร่างทั้งสองแชร์พื้นที่พิกัดเดียวกันภายในกลุ่ม ทำให้จัดตำแหน่งได้ง่าย

## ขั้นตอนที่ 6: ปิดการกำหนดกลุ่มรูปร่าง

เมื่อคุณแทรกสมาชิกที่ต้องการครบแล้ว ให้ปิดกลุ่ม การทำเช่นนี้จะสรุปคอลเลกชันของรูปร่างให้ Word ถือว่าเป็นอ็อบเจ็กต์เดียว

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

ในขณะนี้เอกสารจะมีรูปร่างที่จัดกลุ่มเป็นหนึ่งเดียว ประกอบด้วยสี่เหลี่ยมและวงรี

## ขั้นตอนที่ 7: บันทึกเอกสารที่แก้ไขแล้ว

สุดท้ายให้เขียนการเปลี่ยนแปลงกลับไปยังดิสก์ คุณสามารถเขียนทับไฟล์เดิมหรือสร้างไฟล์ใหม่ได้

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

เมื่อรันโปรแกรมจะได้ไฟล์ `output.docx` เปิดไฟล์ใน Microsoft Word, เลือกรูปร่าง แล้วคุณจะเห็นว่าสี่เหลี่ยมและวงรีเคลื่อนที่พร้อมกัน—พิสูจน์ว่าการ **group shapes in Word** ทำงานสำเร็จ

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ Word มีอ็อบเจ็กต์ที่จัดกลุ่มเป็นหนึ่งเดียว  
* การเลือกกลุ่มทำให้คุณสามารถลาก, ปรับขนาด, หรือหมุนสี่เหลี่ยมและวงรีพร้อมกันได้  
* ไม่ต้องมีการโต้ตอบกับ Word ด้วยมือ; ทุกอย่างทำผ่านโค้ด C#  

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*ข้อความอธิบายภาพ: “Screenshot of a Word document showing a grouped rectangle and ellipse shape”* (ตอบสนองข้อกำหนดของข้อความอธิบายภาพ)

## ทำไมการจัดกลุ่มรูปร่างจึงสำคัญ

การจัดกลุ่มรูปร่างไม่ใช่แค่เพื่อความสวยงามเท่านั้น แต่ยังช่วยให้คุณ:

* **รักษาความสอดคล้องของเลย์เอาต์** – การย้ายกลุ่มทำให้ตำแหน่งสัมพันธ์คงที่  
* **ใช้การแปลงครั้งเดียว** – หมุนหรือสเกลกลุ่มทั้งหมดแทนการทำแต่ละรูปร่างแยกกัน  
* **ลดความซับซ้อนของการประมวลผลต่อไป** – เมื่อเครื่องมืออื่นอ่าน DOCX พวกมันจะเห็นรูปร่างเชิงประกอบเดียว ลดความซับซ้อน

หากคุณต้องการเพิ่มรูปร่างอื่น (เช่น เส้นหรือกล่องข้อความ) ไปยังหน่วยตรรกะเดียวกัน เพียงเรียก `InsertShape` อีกครั้งก่อน `EndGroupShape`

## ความแตกต่างทั่วไปและกรณีขอบ

| สถานการณ์ | วิธีจัดการ |
|-----------|------------|
| **หน่วยต่างกัน** – มีการวัดเป็นเซนติเมตร | แปลงเซนติเมตรเป็นพอยต์ (`1 cm ≈ 28.35 pt`) ก่อนเรียก `InsertShape` |
| **เพิ่มป้ายข้อความ** – ต้องการคำบรรยายภายในกลุ่ม | แทรก `ShapeType.TextBox` หลังสี่เหลี่ยมและวงรี แล้วตั้งค่า `Text` |
| **กำหนดสีเติม** – ต้องการสี่เหลี่ยมสีฟ้า | หลัง `InsertShape` ให้ดึงรูปร่างล่าสุดผ่าน `builder.CurrentParagraph.Runs[0].Font` แล้วตั้ง `shape.FillColor = System.Drawing.Color.Blue;` |
| **ใช้รูปแบบเอกสารอื่น** – ต้องการ `.doc` แทน `.docx` | โค้ดเดียวกันทำงานได้; เพียงเปลี่ยนนามสกุลไฟล์เมื่อเรียก `Save` Aspose.Words จะจัดการรูปแบบโดยอัตโนมัติ |

## เคล็ดลับระดับมืออาชีพ

* **ใช้ builder ซ้ำ** – คุณสามารถเริ่มและจบหลายกลุ่มในเอกสารเดียว; เพียงเรียก `StartGroupShape` อีกครั้งหลัง `EndGroupShape`  
* **ประสิทธิภาพ** – การแทรกรูปร่างเป็นชุดภายในบล็อก `StartGroupShape/EndGroupShape` หนึ่งครั้งเร็วกว่าแทรกรูปร่างแยกกันนอกกลุ่ม  
* **ไลเซนส์** – ไลเซนส์ประเมินผลจะใส่ลายน้ำบนหน้าแรก ติดตั้งไลเซนส์เต็มเพื่อเอาออกในสภาพแวดล้อมการผลิต

## สรุป

ตอนนี้คุณรู้วิธี **จัดกลุ่มรูปร่างใน Word** ด้วย C#, วิธี **เพิ่มสี่เหลี่ยม**, วิธี **เพิ่มวงรี**, และวิธี **แทรกรูปร่างสี่เหลี่ยมในเอกสาร Word** ด้วย Aspose.Words ตัวอย่างที่ทำงานได้เต็มรูปแบบแสดงทุกขั้นตอนตั้งแต่การตั้งค่าโปรเจกต์จนถึงการบันทึกไฟล์สุดท้าย

จากนี้คุณสามารถสำรวจประเภทรูปร่างเพิ่มเติม, ปรับสไตล์, หรือรวมกลุ่มรูปร่างกับตารางและรูปภาพเพื่อสร้างเอกสารที่ซับซ้อนและสร้างโดยอัตโนมัติ

---

**ขั้นตอนต่อไป**

* เรียนรู้วิธี **หมุนกลุ่มรูปร่าง**: ใช้ `Shape.RotationAngle` หลังจากปิดกลุ่ม  
* สำรวจ **การปรับสีเติมและเส้นขอบ** สำหรับสี่เหลี่ยมและวงรี  
* ผสานตรรกะนี้เข้ากับ API ASP.NET Core เพื่อสร้างรายงานตามความต้องการ  

ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจกต์ของคุณ

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}