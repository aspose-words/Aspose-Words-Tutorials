---
category: general
date: 2026-03-22
description: สร้างรูปสี่เหลี่ยมผืนผ้าใน C# และเพิ่มเงาให้รูปด้วย Aspose.Words เรียนรู้วิธีเพิ่มเงา
  วิธีสร้างสี่เหลี่ยมผืนผ้า และวิธีตั้งค่าคุณสมบัติของเงา
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: th
og_description: สร้างรูปสี่เหลี่ยมผืนผ้าใน C# และเพิ่มเงาให้รูปโดยใช้ Aspose.Words
  คู่มือขั้นตอนโดยละเอียดที่ครอบคลุมวิธีเพิ่มเงา วิธีสร้างสี่เหลี่ยมผืนผ้า และวิธีตั้งค่าเงา
og_title: สร้างรูปสี่เหลี่ยมพร้อมเงาใน C# – คู่มือเต็ม
tags:
- Aspose.Words
- C#
- Document Automation
title: สร้างรูปสี่เหลี่ยมผืนผ้าพร้อมเงาใน C# ด้วย Aspose.Words
url: /th/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมผืนผ้าพร้อมเงาใน C# โดยใช้ Aspose.Words

เคยต้อง **สร้างรูปสี่เหลี่ยมผืนผ้า** ในเอกสาร Word แต่ไม่แน่ใจว่าจะใส่เงาแบบเบา ๆ อย่างไรหรือไม่? คุณไม่ได้อยู่คนเดียว—นักพัฒนาหลายคนเจอปัญหานี้เมื่อลองทำงานอัตโนมัติเอกสารเป็นครั้งแรก ในคู่มือนี้เราจะอธิบายขั้นตอน **การเพิ่มเงาให้รูป** ด้วย Aspose.Words อย่างละเอียด และจะตอบคำถาม “**วิธีเพิ่มเงา**”, “**วิธีสร้างสี่เหลี่ยมผืนผ้า**” และ “**วิธีตั้งค่าเงา**” ไปพร้อมกัน

เราจะเริ่มจาก `Document` เปล่า ๆ วาดสี่เหลี่ยม, เปิดใช้งานเงา, ปรับค่าความเบลอ, ระยะ, มุม, และสี, แล้วบันทึกไฟล์ สุดท้ายคุณจะได้ไฟล์ `.docx` ที่มีสี่เหลี่ยมสีเทาลอยอยู่เหนือหน้าเอกสาร ไม่มีความลับ แค่โค้ดตรง ๆ ที่คุณคัดลอก‑วางได้ในโปรเจกต์ .NET ใดก็ได้

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่ม, ตรวจสอบให้แน่ใจว่าคุณมี:

* **Aspose.Words for .NET** (เวอร์ชันล่าสุด ณ มีนาคม 2026) คุณสามารถติดตั้งจาก NuGet ด้วย `Install-Package Aspose.Words`
* สภาพแวดล้อมการพัฒนา .NET – Visual Studio, Rider หรือแม้แต่ VS Code พร้อมส่วนขยาย C# ก็ใช้ได้
* ความรู้พื้นฐาน C# – ไม่ต้องซับซ้อน เพียงสร้างแอปคอนโซลหรือ WinForms ได้

เท่านี้แค่นั้น ไม่ต้องใช้ไลบรารีเพิ่มเติม ไม่ต้องทำขั้นตอนลับ ๆ พร้อมหรือยัง? ไปกันเลย

## ขั้นตอนที่ 1: เริ่มต้นเอกสารเปล่าใหม่

เพื่อ **สร้างรูปสี่เหลี่ยมผืนผ้า** เราต้องมีคอนเทนเนอร์ – วัตถุ `Document` – ที่เป็นตัวแทนไฟล์ Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

คลาส `Document` คือจุดเริ่มต้นของทุกอย่างที่ Aspose.Words ทำงาน คิดว่าเป็นผ้าใบเปล่า หากไม่มีคุณก็เพิ่มรูป, ตาราง หรือข้อความไม่ได้

## ขั้นตอนที่ 2: สร้างสี่เหลี่ยมที่จะใส่เงา

ต่อไปเราจะ **วิธีสร้างสี่เหลี่ยมผืนผ้า** โดยสร้างอินสแตนซ์ `Shape` ชนิด `Rectangle` พร้อมกำหนดขนาดเป็นพอยต์ (1 พอยต์ ≈ 1/72 นิ้ว)

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

ทำไมเลือก 200 × 100 พอยต์? เป็นขนาดที่เหมาะสมสำหรับการสาธิต – ใหญ่พอเห็นเงาชัดเจน แต่ไม่ใหญ่มากจนเกินหน้า ปรับค่าเหล่านี้ให้เข้ากับการออกแบบของคุณได้ตามต้องการ

## ขั้นตอนที่ 3: เปิดใช้งานเงาและตั้งค่าลักษณะของเงา

นี่คือหัวใจของบทเรียน: **วิธีเพิ่มเงา** และ **วิธีตั้งค่าเงา** Aspose.Words มีอ็อบเจกต์ `Shadow` บนทุกรูป ให้คุณเปิด/ปิดเอฟเฟกต์และปรับพารามิเตอร์ด้านภาพ

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** ทำให้ขอบเงานุ่มขึ้น – ค่ามากกว่าจะทำให้เงาดูกระจายมากขึ้น
* **Distance** เลื่อนเงาออกจากสี่เหลี่ยมไกลขึ้น
* **Angle** กำหนดทิศทางของแสง; 45° ให้เงาแนวทแยงมุมที่ดูเป็นธรรมชาติ
* **Color** ให้คุณเลือก `System.Drawing.Color` ใดก็ได้ สีเทาเป็นค่าเริ่มต้นที่ปลอดภัย แต่คุณก็สามารถใช้ `Color.Black` เพื่อความโดดเด่น หรือ `Color.LightGray` เพื่อความอ่อนโยน

เคล็ดลับ: หากตั้งค่า `Enabled = false` ทุกการตั้งค่าเงาอื่น ๆ จะถูกละเลย ดังนั้นตรวจสอบค่านี้ให้แน่ใจเสมอ

## ขั้นตอนที่ 4: แทรกรูปลงในเนื้อหาเอกสาร

เมื่อสี่เหลี่ยมพร้อมและตั้งค่าเงาแล้ว เราต้องวางมันลงในเอกสาร วิธีที่ง่ายที่สุดคือเพิ่มลงในย่อหน้าแรกของส่วนแรก

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

หากเอกสารของคุณมีข้อความอยู่แล้ว คุณสามารถหาตำแหน่ง `Paragraph` เฉพาะหรือแม้แต่เซลล์ `Table` แล้วแทรกรูปที่นั่นได้ วิธี `AppendChild` มีความยืดหยุ่น – ทำงานกับ `Node` ประเภทใดก็ได้

## ขั้นตอนที่ 5: บันทึกเอกสารและตรวจสอบผลลัพธ์

สุดท้าย เราจะเขียนไฟล์ลงดิสก์ เปลี่ยนเส้นทางให้เป็นที่ที่คุณต้องการ; โฟลเดอร์ต้องมีอยู่แล้ว มิฉะนั้นจะเกิดข้อยกเว้น

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

เปิดไฟล์ `ShadowedRectangle.docx` ที่สร้างขึ้นใน Microsoft Word (หรือ LibreOffice) คุณควรเห็นสี่เหลี่ยมสีเทาพร้อมเงาแนวทแยงมุมที่คมชัดและเลื่อนลง‑ขวา หากเงาดูจางเกินไป ให้เพิ่มค่า `BlurRadius` หรือ `Distance` แล้วรันโค้ดใหม่ – การทดลองเป็นส่วนหนึ่งของความสนุก

![สร้างรูปสี่เหลี่ยมผืนผ้าพร้อมเงาตัวอย่าง](rectangle-shadow.png){alt="สร้างรูปสี่เหลี่ยมผืนผ้าพร้อมเงาตัวอย่าง"}

### ผลลัพธ์ที่คาดหวัง

* เอกสาร Word หน้าหนึ่งหน้า
* สี่เหลี่ยมสีเทาขนาด 200 × 100 พอยต์ อยู่มุมซ้าย‑บนของหน้า
* เงาสีเทาอ่อน เลื่อน 8 พิกเซล ที่มุม 45°, เบลอ 5 พิกเซล

## วิธีเพิ่มเงาให้รูป – การสำรวจเชิงลึก

คุณอาจสงสัย, *“ฉันสามารถทำให้เงาเคลื่อนไหวหรือเปลี่ยนตามการป้อนข้อมูลของผู้ใช้ได้ไหม?”* แม้ว่า Aspose.Words เองจะไม่รองรับแอนิเมชัน แต่คุณสามารถปรับค่าเงาแบบโปรแกรมก่อนบันทึก เพื่อสร้างหลายเวอร์ชันของเอกสารเดียวกันที่มีลักษณะต่างกัน ตัวอย่างเช่น การวนลูปผ่านคอลเลกชันของสี:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

โค้ดสั้น ๆ นี้แสดง **วิธีตั้งค่าเงา** อย่างไดนามิก – เหมาะสำหรับสร้างรายงานธีมต่าง ๆ

## วิธีสร้างสี่เหลี่ยมผืนผ้า – รูปแบบอื่น ๆ

หากต้องการสี่เหลี่ยมมุมโค้ง เพียงเปลี่ยน `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

หรือหากต้องการสี่เหลี่ยมจัตุรัส ให้ตั้งค่า `Width` เท่ากับ `Height` คุณสมบัติเงาเดียวกันจะทำงานได้เช่นกัน ดังนั้นคุณก็พร้อมกับ **วิธีเพิ่มเงา** สำหรับรูปแบบใดก็ได้ที่เลือก

## ข้อผิดพลาดทั่วไปและการแก้ไข

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| เงาไม่ปรากฏ | `Shadow.Enabled` ตั้งเป็น `false` | ตั้งค่า `rectangleShape.Shadow.Enabled = true;` |
| เงาดูคมเกินไป | `BlurRadius` ตั้งเป็น 0 | เพิ่ม `BlurRadius` อย่างน้อยเป็น 3 |
| เกิด `FileNotFoundException` ขณะบันทึก | โฟลเดอร์ปลายทางไม่มีอยู่ | สร้างโฟลเดอร์ก่อนหรือใช้เส้นทางที่ถูกต้อง |
| รูปไม่แสดง | กำหนด Width/Height เป็น 0 | ตรวจสอบให้แน่ใจว่าทั้งสองค่า > 0 |

การใส่ใจในจุดเหล่านี้จะช่วยให้คุณหลีกเลี่ยงสถานการณ์ “ทำไมรูปของฉันไม่แสดง?” ได้

## สรุป – สิ่งที่เราได้ทำ

* **สร้างรูปสี่เหลี่ยมผืนผ้า** ในเอกสาร Word ใหม่ด้วย Aspose.Words  
* **เพิ่มเงาให้รูป** โดยสลับ `Shadow.Enabled` และปรับค่า blur, distance, angle, และ color  
* แสดง **วิธีเพิ่มเงา**, **วิธีสร้างสี่เหลี่ยมผืนผ้า**, และ **วิธีตั้งค่าเงา** ในโค้ดที่สะอาดและนำกลับใช้ได้  
* ให้ตัวอย่างครบถ้วนที่พร้อมรัน คุณสามารถคัดลอกไปวางในโปรเจกต์ C# ใดก็ได้

## ขั้นตอนต่อไป?

เมื่อคุณเชี่ยวชาญพื้นฐานแล้ว ลองสำรวจต่อ:

* **วิธีเพิ่มเงาให้รูปภาพ** – API `Shadow` ทำงานกับ `ShapeType.Image` เช่นกัน
* **การรวมหลายรูป** – สร้างแผนผังหรืออินโฟกราฟิกโดยตรงใน Word
* **ส่งออกเป็น PDF** – เรียก `document.Save("output.pdf")` หลังจากเพิ่มเงาเพื่อได้ไฟล์ที่พร้อมพิมพ์

อย่ากลัวทดลองใช้สี, มุม, หรือแม้แต่การไล่สีแบบ gradient API มีความยืดหยุ่นพอให้คุณสร้างเอกสารระดับมืออาชีพโดยไม่ต้องเปิด Word ด้วยตนเอง

---

ขอให้เขียนโค้ดอย่างสนุก! หากเจออุปสรรคใด ๆ คอมเมนต์ด้านล่างหรือเยี่ยมชมฟอรั่ม Aspose.Words – ชุมชนพร้อมช่วยเหลือเสมอ

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}