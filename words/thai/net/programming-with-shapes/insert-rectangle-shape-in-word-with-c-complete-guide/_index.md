---
category: general
date: 2026-08-10
description: แทรกรูปสี่เหลี่ยมใน Word ด้วย C#. เรียนรู้วิธีซ่อนรูป, ซ่อนรูปใน Word,
  และสร้างรูปที่ซ่อนด้วย Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: th
lastmod: 2026-08-10
og_description: แทรกรูปสี่เหลี่ยมผืนผ้าใน Word ด้วย C# บทเรียนนี้อธิบายวิธีซ่อนรูป,
  ซ่อนรูปใน Word, และสร้างรูปที่ซ่อนอยู่พร้อมตัวอย่างโค้ดเต็ม
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: แทรกรูปสี่เหลี่ยมใน Word ด้วย C# – คู่มือแบบขั้นตอนต่อขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: แทรกรูปสี่เหลี่ยมใน Word ด้วย C# – คู่มือฉบับสมบูรณ์
url: /th/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกรูปสี่เหลี่ยมผืนผ้าใน Word ด้วย C# – คู่มือฉบับสมบูรณ์

หากคุณต้องการ **insert rectangle shape** ในเอกสาร Word ด้วย C# คู่มือนี้จะแสดงขั้นตอนที่แน่นอนให้คุณ นอกจากนี้คุณยังจะได้เรียนรู้ **how to hide shape** เพื่อไม่ให้ปรากฏในไฟล์ขั้นสุดท้าย ซึ่งตอบคำถามทั่วไป **hide shape in Word** และสาธิตวิธี **create hidden shape** ด้วยโปรแกรม

บทแนะนำนี้ครอบคลุมทุกอย่างตั้งแต่การตั้งค่า Aspose.Words SDK จนถึงการตรวจสอบว่ารูปถูกซ่อนหรือไม่ เมื่ออ่านจบบทความคุณจะได้โค้ดสแนปเปตที่นำกลับมาใช้ใหม่ได้และสามารถใส่ลงในโปรเจกต์ .NET ใดก็ได้

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดยังทำงานกับ .NET Framework 4.6+ ด้วย)
- ใบอนุญาต Aspose.Words for .NET ที่ถูกต้องหรือคีย์ประเมินผลชั่วคราว
- Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ C#)
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C# และ Document Object Model (DOM) ของไฟล์ Word

ไม่จำเป็นต้องใช้แพ็กเกจ NuGet เพิ่มเติมนอกจาก `Aspose.Words`.

## ขั้นตอนที่ 1: สร้างเอกสารเปล่าใหม่และ DocumentBuilder

การดำเนินการแรกคือการสร้างอ็อบเจกต์ `Document` ตัว `DocumentBuilder` ให้ API ที่สะดวกสำหรับแทรกเนื้อหา เช่น รูปทรง, ย่อหน้า, และตาราง.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**ทำไมเรื่องนี้ถึงสำคัญ:** `Document` แสดงถึงไฟล์ .docx ทั้งหมด, ในขณะที่ `DocumentBuilder` รักษาตำแหน่งเคอร์เซอร์ที่บ่งบอกว่าต้องวางองค์ประกอบต่อไปที่ไหน การกำหนดค่าเริ่มต้นของอ็อบเจกต์ทั้งสองเป็นพื้นฐานสำหรับงานอัตโนมัติของ Word ใด ๆ

## ขั้นตอนที่ 2: แทรกรูปสี่เหลี่ยมผืนผ้า

ตอนนี้คุณจะทำการแทรกรูปสี่เหลี่ยมผืนผ้า เมธอด `InsertShape` ต้องการประเภทของรูปและขนาดในหน่วย points (1 point ≈ 1/72 inch) ขนาด **200 × 100 points** จะให้รูปสี่เหลี่ยมประมาณ 2.78 × 1.39 inch

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**ทำไมเรื่องนี้ถึงสำคัญ:** อ็อบเจกต์ `Shape` ที่คุณได้รับสามารถกำหนดค่าได้เต็มที่—สี, เส้นขอบ, ข้อความ, และการมองเห็นทั้งหมดสามารถปรับเปลี่ยนได้ก่อนบันทึกเอกสาร

## ขั้นตอนที่ 3: ซ่อนรูป

เพื่อป้องกันไม่ให้รูปสี่เหลี่ยมแสดงหรือพิมพ์ ให้ตั้งค่า `Hidden` ของมันเป็น `true` คุณสมบัตินี้ตรงกับแอตทริบิวต์ “Hidden” ของ Word ซึ่ง Word จะเคารพทั้งในโหมดดูและพิมพ์

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**ทำไมเรื่องนี้ถึงสำคัญ:** การตั้งค่า `Hidden` เป็นวิธีมาตรฐานในการ **hide shape in Word** โดยไม่ต้องลบออกจากโครงสร้างเอกสาร รูปยังคงเข้าถึงได้จากโค้ด ทำให้สามารถทำการปรับเปลี่ยนต่อไปได้ เช่น การจัดรูปแบบตามเงื่อนไขหรือการสลับการมองเห็นตามข้อมูล

## ขั้นตอนที่ 4: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารลงดิสก์ เลือกโฟลเดอร์ใดก็ได้ ตัวอย่างใช้เส้นทางตัวแปรที่คุณควรแทนที่ด้วยเส้นทางจริง

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**ทำไมเรื่องนี้ถึงสำคัญ:** การบันทึกทำให้ไฟล์เสร็จสมบูรณ์และเขียนแฟล็กซ่อนลงใน Open XML พื้นฐาน เมื่อคุณเปิดเอกสารใน Microsoft Word รูปสี่เหลี่ยมจะไม่ปรากฏ แสดงว่าคุณได้ **created hidden shape** อย่างสำเร็จ

## ขั้นตอนที่ 5: ตรวจสอบรูปที่ซ่อนอยู่

เปิดไฟล์ `HiddenShape.docx` ที่สร้างขึ้นใน Microsoft Word:

1. ไปที่ **File → Options → Display** และตรวจสอบให้แน่ใจว่า *“Show hidden text”* ไม่ถูกเลือก (**unchecked**).  
2. รูปสี่เหลี่ยมควรไม่ปรากฏบนหน้าใดเลย  
3. เพื่อตรวจสอบอีกครั้ง ให้เปิด *“Show hidden text”*; รูปสี่เหลี่ยมจะปรากฏเป็นเส้นประสีอ่อน แสดงว่ารูปมีอยู่แต่ถูกซ่อน

หากรูปสี่เหลี่ยมยังคงมองเห็นได้ ให้ตรวจสอบว่าคุณได้บันทึกไฟล์หลังจากตั้งค่า `Hidden = true` แล้วและว่าคุณกำลังเปิดไฟล์ที่ถูกต้องหรือไม่

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มรูปแบบที่คุณสามารถคัดลอก, วาง, และรันได้โดยตรง

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** คอนโซลจะแสดงเส้นทางไฟล์และข้อความเตือนสั้น ๆ เมื่อไฟล์เปิดใน Word รูปสี่เหลี่ยมจะไม่ปรากฏ เว้นแต่เปิดการแสดงข้อความซ่อน

## คำถามทั่วไปและกรณีขอบ

### ฉันสามารถซ่อนเฉพาะเส้นขอบแต่ให้สีเติมยังคงมองเห็นได้หรือไม่?

ได้. แทนการตั้งค่า `Hidden = true` คุณสามารถตั้งค่า `rectangle.LineFormat.Visible = false` เพื่อซ่อนเส้นขอบในขณะที่ยังคงสีเติมอยู่ นี่เป็นวิธีหนึ่งของ **how to hide shape** ที่รักษาลักษณะบางส่วนของการแสดงผล

### แฟล็กซ่อนทำงานในเวอร์ชัน Word เก่า (2003, 2007) หรือไม่?

แอตทริบิวต์ซ่อนเป็นส่วนหนึ่งของสเปค Open XML ที่แนะนำตั้งแต่ Word 2007 เอกสารที่บันทึกในรูปแบบไบนารี `.doc` เก่า จะไม่เก็บแฟล็กนี้ไว้ เพื่อรองรับฟอร์แมตเก่า ให้บันทึกเป็น `.docx` และหากต้องการ สามารถแปลงต่อภายหลังโดยใช้ `SaveFormat.Doc` ของ Aspose.Words

### ถ้าฉันต้องการซ่อนหลายรูปพร้อมกันจะทำอย่างไร?

วนลูปผ่านคอลเลกชัน `Document.GetChildNodes(NodeType.Shape, true)` และตั้งค่า `Hidden = true` ให้กับแต่ละรูปที่ตรงตามเกณฑ์ของคุณ (เช่น `ShapeType` เฉพาะหรือค่า `AlternativeText` ที่กำหนดเอง)

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### การซ่อนรูปมีผลต่อประสิทธิภาพหรือไม่?

แฟล็กซ่อนเพิ่มแอตทริบิวต์ XML เล็กน้อย; ไม่ส่งผลต่อความเร็วการเรนเดอร์ อย่างไรก็ตาม หากมีวัตถุซ่อนจำนวนมากอาจทำให้ขนาดไฟล์เพิ่มขึ้นเล็กน้อย ควรลบรูปที่ไม่จำเป็นเพื่อให้เอกสารมีขนาดเบา

## เคล็ดลับและแนวทางปฏิบัติที่ดีที่สุด

- **Give the shape a meaningful name** โดยใช้ `rectangle.Name = "MyHiddenRectangle"`; จะช่วยให้คุณค้นหารูปใน DOM ได้ง่ายขึ้นในภายหลัง.
- **Set `AlternativeText`** ให้เป็นแท็กที่กำหนดเอง (เช่น `"HiddenShape"`). วิธีนี้ทำให้คุณสามารถหาตำแหน่งรูปได้โดยไม่ต้องพึ่งพาดัชนีของมัน.
- **Wrap the code in a try‑catch block** เพื่อจัดการข้อผิดพลาดด้านลิขสิทธิ์หรือข้อยกเว้น I/O อย่างราบรื่น.
- **Dispose of the Document** หลังจากบันทึก หากคุณกำลังประมวลผลไฟล์หลายไฟล์ในลูป เพื่อปลดปล่อยทรัพยากรที่ไม่ได้จัดการ: `document.Dispose();`.

## สรุป

ตอนนี้คุณรู้วิธี **insert rectangle shape** ในเอกสาร Word ด้วย C#, วิธี **hide shape in Word**, และวิธี **create hidden shape** ที่ยังคงเป็นส่วนหนึ่งของโครงสร้างเอกสารแต่ไม่ปรากฏต่อผู้ใช้ ตัวอย่างที่สามารถรันได้เต็มรูปแบบแสดงขั้นตอนทั้งหมด ตั้งแต่การสร้างเอกสารจนถึงการตรวจสอบ

ต่อไปคุณอาจสำรวจ **how to hide shape** ตามข้อมูลที่ผู้ใช้ป้อน, หรือผสานรูปที่ซ่อนกับ content controls เพื่อสร้างเอกสารแบบไดนามิก คุณยังสามารถใช้เทคนิคเดียวกันกับรูปประเภทอื่น ๆ เช่น วงรี, ลูกศร, หรือการวาดแบบกำหนดเอง

ลองทดลองกับขนาด, สี, และการตั้งค่าการมองเห็นที่ต่างกันได้ตามต้องการ หากพบปัญหาใด ๆ ให้กลับไปตรวจสอบขั้นตอนข้างต้นหรือดูเอกสาร Aspose.Words เพื่อรายละเอียด API ที่ลึกขึ้น ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโปรเจกต์ของคุณ

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}