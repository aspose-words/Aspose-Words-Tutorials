---
category: general
date: 2026-05-26
description: สร้างเอกสาร Word ด้วย C# และ Aspose.Words, แทรกรูปสี่เหลี่ยม, ตั้งค่าสีเติม,
  และเพิ่มเอฟเฟกต์เงา – คู่มือแบบทีละขั้นตอน
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: th
og_description: สร้างเอกสาร Word ด้วย C# โดยใช้ Aspose.Words. เรียนรู้วิธีแทรกรูปสี่เหลี่ยม,
  ตั้งค่าสีเติม, และเพิ่มเงา.
og_title: สร้างเอกสาร Word – แทรกรูปสี่เหลี่ยมและเงาใน C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: สร้างเอกสาร Word – แทรกรูปสี่เหลี่ยมและเงาใน C#
url: /th/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word – แทรกรูปสี่เหลี่ยมและเงาใน C#

เคยสงสัยไหมว่า จะ **สร้างเอกสาร Word** อย่างอัตโนมัติโดยไม่ต้องเปิด Microsoft Word ก่อน? คุณไม่ได้เป็นคนเดียว ในหลายสถานการณ์การทำอัตโนมัติ—เช่น ใบแจ้งหนี้ สัญญา หรือการสร้างรายงานเป็นจำนวนมาก—คุณต้องการวิธีที่เชื่อถือได้ในการสร้างไฟล์ .docx ใส่รูปทรงลงไป ให้สี และอาจเพิ่มเงาเพื่อให้ดูเป็นมืออาชีพ

ในบทเรียนนี้เราจะพาคุณผ่านขั้นตอนทั้งหมด: ใช้ Aspose.Words for .NET เพื่อ **สร้างเอกสาร Word**, **แทรกรูปสี่เหลี่ยม**, ตั้งค่าการเติมสี, และ **เพิ่มเงา**. เมื่อจบคุณจะได้ไฟล์ที่พร้อมบันทึกและสามารถส่งต่อไปยังขั้นตอนต่อไปได้  

เราจะอธิบายเพิ่มเติมเกี่ยวกับ **วิธีแทรกรูปทรง** อย่างยืดหยุ่น, และทำไม **วิธีตั้งค่าการเติมสี** ถึงสำคัญสำหรับความสอดคล้องของภาพ. ไม่มีเนื้อหาเกินความจำเป็น, เพียงโค้ดที่คุณคัดลอก‑วางและรันได้เลย

## ข้อกำหนดเบื้องต้น

- .NET 6+ (หรือ .NET Framework 4.7+) ติดตั้งแล้ว
- ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ทดลองใช้ชั่วคราว)
- Visual Studio, Rider หรือ IDE สำหรับ C# ที่คุณชอบ
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#—ไม่ต้องการความเชี่ยวชาญพิเศษ

มีครบหรือยัง? ดีมาก, มาเริ่มกันเลย

## ขั้นตอนที่ 1 – สร้างเอกสาร Word

สิ่งแรกที่คุณต้องการคืออ็อบเจ็กต์เอกสารเปล่า ซึ่งเป็นผืนผ้าใบที่ทุกอย่างจะถูกวางไว้

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` แทนไฟล์ .docx ในหน่วยความจำ, ส่วน `DocumentBuilder` ให้ API ที่สะดวกสำหรับแทรกข้อความ, ตาราง, และรูปทรง. **การสร้างเอกสาร Word** ด้วยวิธีนี้ทำได้ทันที—ไม่มี UI, ไม่มี COM interop, เพียงแค่ .NET ธรรมดา

## ขั้นตอนที่ 2 – แทรกรูปสี่เหลี่ยม

ตอนนี้เรามีเอกสารแล้ว, มา **แทรกรูปสี่เหลี่ยม** กัน. เมธอด `InsertShape` รับค่า `ShapeType` enum, ความกว้าง, และความสูง (หน่วยเป็น point). เราจะใช้สี่เหลี่ยมขนาด 150 × 80 point, ซึ่งประมาณ 2 × 1 inch

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

เบื้องหลัง Aspose จะสร้างอ็อบเจ็กต์ `Shape`, เพิ่มลงในพารากราฟปัจจุบัน, และคืนอ้างอิงที่คุณสามารถกำหนดสไตล์ได้. นี่คือแก่นของ **วิธีแทรกรูปทรง**—เพียงบรรทัดเดียวของโค้ด แต่ทรงพลังมาก

## ขั้นตอนที่ 3 – วิธีตั้งค่าการเติมสี

รูปทรงที่ไม่มีการเติมสีจะมองไม่เห็นบนหน้าขาว. เรามาให้พื้นหลังสีฟ้าอ่อนที่น่ารับรองกันเถอะ

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

คุณก็สามารถใช้ gradient, texture, หรือแม้แต่การเติมรูปภาพ, แต่สีทึบทำให้ตัวอย่างง่ายขึ้น. ตัวอย่างนี้แสดง **วิธีตั้งค่าการเติมสี** บนรูปทรงใด ๆ ที่คุณสร้าง, เพื่อให้ผู้อ่านได้รับสัญญาณภาพที่คาดหวัง

## ขั้นตอนที่ 4 – วิธีเพิ่มเงา

เงาช่วยเพิ่มความลึกและทำให้รูปทรงโดดเด่น. Aspose.Words มีอ็อบเจ็กต์ `ShadowFormat` ที่ให้คุณเปิด/ปิดการมองเห็น, เลือกสี, และปรับค่า blur, ระยะ, และมุมได้อย่างละเอียด

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

ทำไมต้องใช้ค่าดังกล่าว? มุม 45° ให้แสงจากด้านบน‑ขวาเป็นธรรมชาติ, blur ปานกลางทำให้เงาไม่เด่นเกินไป, และระยะสั้นทำให้รูปทรงไม่ดูแยกจากเนื้อหา. คุณสามารถทดลองปรับเปลี่ยน—เช่น เปลี่ยนมุมเป็น 135° จะทำให้เงาตกลงมาที่ด้านล่าง‑ซ้าย

## ขั้นตอนที่ 5 – บันทึกเอกสาร

ทุกอย่างเสร็จแล้ว; ตอนนี้ให้เขียนไฟล์ลงดิสก์. เลือกเส้นทางใดก็ได้ที่คุณต้องการ, แต่อย่าลืมตรวจสอบว่าโฟลเดอร์มีอยู่จริง

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

เมื่อคุณเปิด `ShadowShape.docx` ด้วย Microsoft Word, คุณจะเห็นสี่เหลี่ยมสีฟ้าอ่อนพร้อมเงาสีเทานุ่ม—ตรงกับที่เราเขียนสคริปต์ไว้

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกส่วนเข้าด้วยกัน, นี่คือโปรแกรมที่พร้อมคัดลอก‑วางทั้งหมด:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

- ไฟล์ชื่อ **ShadowShape.docx** ปรากฏในโฟลเดอร์เป้าหมาย
- เปิดไฟล์ใน Word จะเห็นสี่เหลี่ยมสีฟ้าอ่อนอยู่กึ่งกลางหน้าแรก
- สี่เหลี่ยมมีเงาสีเทาที่มุม 45°, ให้เอฟเฟกต์ 3‑D อย่างละเอียดอ่อน

## คำถามทั่วไป & กรณีขอบ

**ถ้าต้องการรูปทรงอื่น?**  
เปลี่ยน `ShapeType.Rectangle` เป็นค่า enum อื่น (`Ellipse`, `Star`, `Arrow` เป็นต้น). ส่วนอื่นของโค้ดไม่ต้องเปลี่ยน

**สามารถใส่ข้อความภายในรูปทรงได้หรือไม่?**  
ได้—หลังจากสร้างรูปทรง, เรียก `shape.AppendChild(new Paragraph(doc))` แล้วแทรก `Run` พร้อมข้อความของคุณ. อย่าลืมตั้งค่า `shape.TextBox` หากต้องการให้ข้อความห่อหุ้ม

**เรื่อง DPI หรือหน่วยวัดล่ะ?**  
Aspose ทำงานเป็น point (1 pt = 1/72 inch). หากต้องการใช้เซนติเมตร, คูณด้วย 28.35 (เพราะ 1 cm ≈ 28.35 pt)

**ต้องมีใบอนุญาตเพื่อให้ทำงานได้หรือไม่?**  
รุ่นทดลองจะใส่ลายน้ำบนหน้าแรก. ใบอนุญาตเต็มจะลบลายน้ำและเปิดใช้งาน API ทั้งหมด

## เคล็ดลับ & สิ่งที่ต้องระวัง

- **Pro tip:** เรียก `builder.MoveToDocumentEnd()` ก่อนแทรกรูปทรง หากต้องการให้รูปปรากฏที่ส่วนท้ายของเอกสาร
- **ระวัง:** การบันทึกลงโฟลเดอร์ที่เป็น read‑only จะทำให้เกิด `UnauthorizedAccessException`. ตรวจสอบให้แอปของคุณมีสิทธิ์เขียน
- **หมายเหตุประสิทธิภาพ:** สำหรับการสร้างจำนวนมาก (หลายร้อยไฟล์), ควรใช้ `Document` ตัวเดียวเป็นเทมเพลตและคล cloning ด้วย `doc.Clone(true)` เพื่อหลีกเลี่ยงการเริ่มต้นซ้ำหลายครั้ง

## สรุป

ตอนนี้คุณรู้วิธี **สร้างเอกสาร Word**, **แทรกรูปสี่เหลี่ยม**, **ตั้งค่าการเติมสี**, และ **เพิ่มเงา** ด้วย Aspose.Words for .NET. โค้ดข้างต้นเป็นโซลูชันแบบอิสระที่คุณสามารถใส่ลงในโปรเจกต์ C# ใดก็ได้ ไม่ว่าจะเป็นคอนโซลแอป, Web API, หรือบริการพื้นหลัง

ต่อจากนี้คุณอาจสำรวจต่อ:

- เพิ่มรูปทรงหลายรูปด้วยสีที่แตกต่างกัน
- ใช้ gradient หรือ picture fill (`shape.FillColor = ...` → `shape.FillPattern`)
- รวมรูปทรงกับตารางเพื่อสร้างเลย์เอาต์รายงานที่ซับซ้อน

ลองทำดู, ปรับพารามิเตอร์, แล้วดูไฟล์ Word ที่ทำอัตโนมัติของคุณดูเป็นมืออาชีพยิ่งขึ้นด้วยเพียงไม่กี่บรรทัดของโค้ด. Happy coding!

## บทเรียนที่เกี่ยวข้อง

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}