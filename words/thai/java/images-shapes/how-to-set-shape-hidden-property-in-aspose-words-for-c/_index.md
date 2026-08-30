---
category: general
date: 2026-08-20
description: เรียนรู้วิธีตั้งค่าคุณสมบัติ “hidden” ของ shape ใน Aspose.Words สำหรับ
  C# คู่มือนี้จะแสดงการแทรกรูปภาพและการซ่อน shape เพื่อไม่ให้ปรากฏใน UI หรือผลลัพธ์การพิมพ์เลย
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: th
lastmod: 2026-08-20
og_description: ตั้งค่าคุณสมบัติ hidden ของรูปร่างใน Aspose.Words ด้วย C# แทรกรูปภาพ,
  ซ่อนรูปร่าง, และทำให้แน่ใจว่าไม่แสดงใน UI หรือผลลัพธ์การพิมพ์เลย.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: ตั้งค่าคุณสมบัติซ่อนของรูปทรงใน Aspose.Words – คู่มือ C# ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: วิธีตั้งค่าคุณสมบัติซ่อนของรูปทรงใน Aspose.Words สำหรับ C#
url: /th/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งค่า hidden property ของ shape ใน Aspose.Words สำหรับ C#

หากคุณต้องการ **ตั้งค่า hidden property ของ shape** ในเอกสาร Word, บทแนะนำนี้จะแสดงขั้นตอนที่แน่นอนโดยใช้ Aspose.Words สำหรับ .NET ไม่ว่าคุณจะกำลังสร้างเครื่องมือเทมเพลต, สร้างรายงาน, หรือฝังโลโก้ที่ต้องคงเป็นแบบมองไม่เห็น, คุณจะได้เรียนรู้วิธีแทรกรูปภาพและซ่อน shape เพื่อให้ไม่ปรากฏใน UI หรือผลลัพธ์การพิมพ์

ในคู่มือนี้เรายังครอบคลุม **การแทรกรูปภาพลงในเอกสาร**, อธิบายว่าการซ่อน shape มีความสำคัญอย่างไรสำหรับการพิมพ์, และเดินผ่านโค้ดที่สมบูรณ์และสามารถรันได้ ไม่ต้องอ้างอิงภายนอก—เพียงคัดลอก, วาง, และรัน

## ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า (เวอร์ชันล่าสุดของ Aspose.Words รองรับ .NET 6+)
* ใบอนุญาต Aspose.Words สำหรับ .NET ที่ถูกต้อง (หรือใช้โหมดประเมินผลฟรี)
* Visual Studio 2022 หรือ IDE C# ใด ๆ ที่คุณชอบ
* ไฟล์รูปภาพ (เช่น `logo.png`) ที่วางในโฟลเดอร์ที่คุณสามารถอ้างอิงจากโค้ดได้

## ขั้นตอนที่ 1: สร้าง Document และ DocumentBuilder ใหม่

`DocumentBuilder` class เป็นจุดเริ่มต้นสำหรับการสร้างเนื้อหา Word ด้วยโปรแกรม มันช่วยให้คุณแทรกย่อหน้า, ตาราง, และ shape เช่นรูปภาพ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*ทำไมต้องทำขั้นตอนนี้?*  
การสร้าง `Document` จะให้การแสดงผลในหน่วยความจำของไฟล์ .docx, ในขณะที่ `DocumentBuilder` จัดเตรียม Fluent API ที่ใช้แทรกออบเจ็กต์. หากไม่มีออบเจ็กต์เหล่านี้คุณจะไม่สามารถวาง shape ในเอกสารได้.

## ขั้นตอนที่ 2: แทรกรูปภาพเป็น shape

Aspose.Words ถือรูปภาพทุกภาพเป็น `Shape`. เมธอด `InsertImage` จะคืนค่าอินสแตนซ์ของ `Shape` นั้น, ซึ่งคุณสามารถจัดการต่อไปได้.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*ทำไมต้องทำขั้นตอนนี้?*  
การใช้ `InsertImage` ไม่เพียงแค่เพิ่มรูปภาพลงในกระแสของข้อความเท่านั้น แต่ยังให้คุณอ้างอิง (`picture`) ที่สามารถกำหนดค่าได้. นี่เป็นสิ่งสำคัญสำหรับ **C# shape hidden property** ที่เราจะตั้งค่าในขั้นตอนต่อไป.

## ขั้นตอนที่ 3: ตั้งค่า hidden property ของ shape

property `Hidden` ควบคุมว่า shape จะมีส่วนร่วมใน UI และการพิมพ์หรือไม่. การตั้งค่าเป็น `true` ทำให้ shape ไม่ปรากฏใน UI ของ Word และรับประกันว่าจะไม่ถูกพิมพ์.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*ทำไมต้องทำขั้นตอนนี้?*  
เมื่อ shape ถูกทำเครื่องหมายว่า hidden, Word จะจัดการมันเหมือนคอมเมนต์—อยู่ในโครงสร้างของเอกสารแต่ไม่แสดงผล. นี่คือหัวใจของ **set shape hidden property**.

## ขั้นตอนที่ 4: บันทึกเอกสาร

สุดท้าย, เขียนเอกสารลงดิสก์. คุณสามารถเลือกฟอร์แมตใดก็ได้ที่ Aspose.Words รองรับ (`.docx`, `.pdf`, `.html`, ฯลฯ).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*ทำไมต้องทำขั้นตอนนี้?*  
การบันทึกทำให้การเปลี่ยนแปลงในหน่วยความจำเสร็จสมบูรณ์. การเปิด `.docx` ที่ได้ใน Microsoft Word จะไม่แสดงรูปภาพ, และการส่งออกเป็น PDF ยืนยันว่า shape ไม่ปรากฏในผลลัพธ์การพิมพ์.

## ตัวอย่างเต็มที่สามารถรันได้

เมื่อนำทุกอย่างมารวมกัน, นี่คือโปรแกรมเต็มที่คุณสามารถคอมไพล์และรันได้:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง**

* การเปิด `HiddenImageDocument.docx` ใน Microsoft Word จะไม่แสดงรูปภาพใด ๆ.
* การส่งออกหรือพิมพ์เอกสาร (หรือเปิด PDF) ก็จะไม่แสดงรูปภาพ.
* Shape ที่ซ่อนอยู่ยังคงอยู่ใน XML ของเอกสาร, คุณสามารถตรวจสอบได้โดยเปิดไฟล์ `.docx` เป็น zip แล้วดู `word/document.xml` – คุณจะเห็นองค์ประกอบ `<w:pict>` ที่มี `w:hidden="true"`.

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | วิธีทำ | ทำไมจึงสำคัญ |
|-----------|--------|--------------|
| **ไฟล์รูปภาพหาย** | ห่อ `InsertImage` ด้วย `try/catch` และจัดการ `FileNotFoundException`. | ป้องกันไม่ให้แอปพลิเคชันขัดข้องและให้คุณบันทึกข้อผิดพลาดที่ชัดเจน. |
| **หลาย shape ที่ซ่อน** | เรียก `picture.Hidden = true` สำหรับแต่ละ `Shape` ที่คุณแทรก, หรือวนลูปผ่าน `doc.GetChildNodes(NodeType.Shape, true)`. | รับประกันว่าองค์ประกอบภาพที่ไม่ต้องการทั้งหมดจะคงซ่อนอยู่. |
| **ต้องการให้ shape ปรากฏเฉพาะในโหมดแก้ไข** | ตั้งค่า `picture.Hidden = false` หลังการแก้ไข, แล้วสลับกลับก่อนบันทึก. | ทำให้คุณสามารถทำงานกับ shape ใน UI ได้ในขณะที่ผลลัพธ์สุดท้ายยังคงสะอาด. |
| **การพิมพ์บน Word รุ่นเก่า** | ตรวจสอบเอกสารด้วย Word 2010 หรือใหม่กว่า; ธง hidden รองรับในทุกเวอร์ชันสมัยใหม่. | รับประกันความเข้ากันได้กับผู้ใช้ของคุณ. |
| **ใช้รูปแบบไฟล์อื่น (เช่น PDF โดยตรง)** | ธง `Hidden` ทำงานเช่นเดียวกัน; Aspose.Words เคารพมันระหว่างการแปลงเป็น PDF. | ยืนยันว่า **prevent shape from printing** ทำงานสำหรับเป้าหมายการส่งออกทั้งหมด. |

## เคล็ดลับพิเศษ: ตรวจสอบ hidden flag ด้วยโปรแกรม

หากคุณต้องการยืนยันว่า shape ถูกซ่อนก่อนบันทึก, คุณสามารถตรวจสอบ property ได้ดังนี้:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

## สรุป

ตอนนี้คุณรู้วิธี **ตั้งค่า hidden property ของ shape** ใน Aspose.Words สำหรับ C# แล้ว. ด้วยการแทรกรูปภาพ, ตั้งค่า `picture.Hidden = true`, และบันทึกเอกสาร, shape จะไม่ปรากฏใน UI และไม่แสดงในผลลัพธ์การพิมพ์. เทคนิคนี้สำคัญเมื่อคุณต้องการ placeholder, watermark, หรือองค์ประกอบแบรนด์ที่ควรซ่อนจากผู้ใช้ปลายทาง.

### ต่อไปคืออะไร?

* สำรวจ property ของ shape อื่น ๆ เช่น `picture.WrapType`, `picture.Rotation`, และ `picture.RelativeHorizontalPosition`.
* เรียนรู้วิธี **ซ่อน shape ใน Aspose.Words** อย่างมีเงื่อนไขตามข้อมูลผู้ใช้หรือการตั้งค่า.
* ผสาน shape ที่ซ่อนกับลูป **แทรกรูปภาพลงในเอกสาร** เพื่อสร้างมาร์คเกอร์ที่มองไม่เห็นแบบไดนามิกสำหรับการประมวลผลต่อไป (เช่น ฟิลด์ mail‑merge).

อย่าลังเลที่จะทดลองกับรูปแบบภาพต่าง ๆ, เค้าโครงเอกสาร, และเป้าหมายการส่งออก. การซ่อน shape ให้คุณควบคุมอย่างละเอียดว่าอะไรที่ผู้อ่านจะเห็น—และอะไรที่ซ่อนอยู่เบื้องหลัง. ขอให้เขียนโค้ดอย่างสนุกสนาน!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดที่ทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจกต์ของคุณ.

- [สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือขั้นตอน](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words สำหรับ .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [แทรกรูปภาพ Inline ในเอกสาร Word ด้วย Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}