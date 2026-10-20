---
category: general
date: 2026-04-21
description: สร้างเอกสาร Word พร้อมสี่เหลี่ยมสไตล์และเงา เรียนรู้วิธีเพิ่มเงา แทรกรูปทรงสี่เหลี่ยม
  ตั้งค่าสีเงา และอื่น ๆ ใน C#
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: th
og_description: สร้างเอกสาร Word และเพิ่มรูปสี่เหลี่ยมที่มีเงาใน C#. ทำตามคำแนะนำนี้เพื่อกำหนดสีเงา,
  ความเบลอ และการเลื่อนตำแหน่งได้อย่างง่ายดาย.
og_title: สร้างเอกสาร Word ด้วยสี่เหลี่ยมเงา – ทีละขั้นตอน
tags:
- Aspose.Words
- C#
- Document Automation
title: สร้างเอกสาร Word พร้อมสี่เหลี่ยมเงา – คู่มือฉบับสมบูรณ์
url: /th/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word พร้อมสี่เหลี่ยมเงา – คู่มือฉบับสมบูรณ์

เคยต้อง **สร้างเอกสาร word** ที่ดูเรียบหรูกว่าหน้าข้อความเปล่า ๆ หรือไม่? บางทีคุณอาจกำลังทำเทมเพลตรายงานหรือโบรชัวร์และสี่เหลี่ยมง่าย ๆ พร้อมเงาเบา ๆ ก็พอใช้ได้ ในบทเรียนนี้เราจะพาคุณผ่านขั้นตอนนั้น—วิธีแทรกรูปทรงสี่เหลี่ยม, เปิดเงา, และปรับสี, ความเบลอ, และการเยื้อง—ทั้งหมดด้วย C# และ Aspose.Words

เราจะอธิบาย **วิธีเพิ่มเงา** ที่ทำงานได้ไม่ว่าคุณจะกำหนดเป้าหมายเป็น Word 2016, 2019 หรือรุ่นล่าสุดของ Office 365 สุดท้ายคุณจะได้ไฟล์ *.docx* ที่พร้อมบันทึกซึ่งแสดงสี่เหลี่ยมที่มีเงาอย่างสวยงาม และคุณจะเข้าใจ “เหตุผล” ของแต่ละคุณสมบัติที่ตั้งค่า

## ข้อกำหนดเบื้องต้น

- .NET 6 (หรือเวอร์ชัน .NET Framework ใกล้เคียง)  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ C#  
- IDE เช่น Visual Studio (แต่ใด ๆ ก็ได้)

ไม่มีไลบรารีเพิ่มเติมที่จำเป็น; ทุกอย่างที่เหลืออยู่ใน Aspose.Words

## ขั้นตอนที่ 1 – เริ่มต้น Document และ Builder (Create Word Document)

เพื่อ **สร้างเอกสาร word** อย่างโปรแกรมเมติกคุณเริ่มด้วยคลาส `Document` ส่วน `DocumentBuilder` คือแปรงสีของคุณ; มันให้คุณเพิ่มข้อความ, รูปร่าง, และองค์ประกอบอื่น ๆ

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*ทำไมจึงสำคัญ:* วัตถุ `Document` แทนไฟล์ .docx ทั้งหมด หากไม่มีคุณก็ไม่มีที่ใดจะใส่สี่เหลี่ยมหรือเงาได้

## ขั้นตอนที่ 2 – แทรกรูปทรงสี่เหลี่ยม (Insert Rectangle Shape)

ตอนนี้เราจะ **แทรกรูปทรงสี่เหลี่ยม** จริง ๆ เมธอด `InsertShape` รับค่า `ShapeType` enum พร้อมความกว้างและความสูงเป็นพอยต์

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*เคล็ดลับ:* 1 พอยต์ ≈ 1/72 นิ้ว, ดังนั้น 200 pts ประมาณ 2.78 นิ้วกว้าง ปรับค่าตามการจัดวางของคุณ

## ขั้นตอนที่ 3 – เปิดใช้งานเงา (How to Add Shadow)

เงาจะถูกปิดโดยค่าเริ่มต้น ให้สลับแฟล็ก `Visible` เพื่อเปิดใช้งาน

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*เกิดอะไรขึ้น?* เมื่อ `Visible` เป็น true, Word จะเรนเดอร์เงาตกตามคุณสมบัติอื่น ๆ ที่คุณตั้งค่าต่อไป

## ขั้นตอนที่ 4 – ปรับแต่งลักษณะเงา (Set Shadow Color, Blur, Offsets)

นี่คือจุดที่คุณ **ตั้งค่าสีเงา**, รัศมีเบลอ, และการเยื้อง X/Y ลองทดลองดู—ค่าต่าง ๆ จะให้แสงนุ่ม, เงาตกลึก, หรือแม้แต่เอฟเฟกต์ “ลอย”

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*ทำไมต้องเป็นตัวเลขเหล่านี้?* เบลอ 5 pts ให้ขอบที่นุ่มนวล, ส่วนการเยื้อง 4 pts ทำให้เงาเลื่อนลง‑ขวา, จำลองแหล่งแสงจากบน‑ซ้าย เปลี่ยน `Color` เป็น `Color.Black` เพื่อคอนทราสต์ที่แรงกว่า, หรือใช้ `Color.FromArgb(128, 0, 0, 0)` สำหรับสีดำกึ่งโปร่งใส

### กรณีพิเศษและรูปแบบต่าง ๆ

- **ไม่มีเบลอ:** ตั้ง `Blur = 0` เพื่อให้เงาขอบคมชัด  
- **การเยื้องเป็นลบ:** ใช้ `OffsetX = -4` เพื่อดันเงาไปทางซ้าย  
- **รูปทรงอื่น:** คุณสมบัติเงาเดียวกันทำงานกับวงกลม, สามเหลี่ยม, หรือรูปวาดอิสระ—แค่เปลี่ยน `ShapeType` ในขั้นตอน 2  
- **ความเข้ากันได้:** Aspose.Words เขียนข้อมูลเงาในรูปแบบ Office Open XML ซึ่งทำงานได้กับ Word 2010‑2021 และ Office 365

## ขั้นตอนที่ 5 – บันทึกเอกสาร (Create Word Document)

สุดท้ายให้บันทึกไฟล์ลงดิสก์ คุณสามารถเลือกฟอร์แมตที่รองรับ (`.docx`, `.pdf`, `.odt`, …) แต่ในคู่มือนี้เราจะใช้ฟอร์แมต Word ดั้งเดิม

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

เมื่อคุณเปิด **ShadowRectangle.docx** ใน Microsoft Word คุณจะเห็นสี่เหลี่ยมสีเทาพร้อมเงาเบลออ่อน ๆ ที่เยื้องลง‑ขวา—ตรงกับที่เราสคริปต์ไว้

### ผลลัพธ์ที่คาดหวัง

- ไฟล์ *.docx* หนึ่งหน้า  
- สี่เหลี่ยม 200 pt × 100 pt อยู่กึ่งกลางตำแหน่งเคอร์เซอร์เมื่อเรียก `InsertShape`  
- เงาสีเทาที่เยื้อง 4 pts ไปทางขวาและลง 4 pts, พร้อมเบลอ 5 pt

หากรูปทรงดูไม่กึ่งกลาง, คุณสามารถย้ายเคอร์เซอร์ด้วย `builder.MoveTo` ก่อนแทรก, หรือปรับคุณสมบัติ `Left` และ `Top` ของรูปหลังการแทรก

## คำถามที่พบบ่อยและการแก้ไขปัญหา

**ถาม: เงาไม่แสดงใน Word**  
ตอบ: ตรวจสอบว่า `ShadowFormat.Visible` เป็น `true` แล้ว ตรวจสอบว่าคุณใช้ Aspose.Words เวอร์ชันล่าสุด (ฟีเจอร์เงาเพิ่มในเวอร์ชัน 20.3)

**ถาม: สามารถใส่ gradient ให้เงาได้หรือไม่?**  
ตอบ: ไม่ได้โดยตรงผ่าน `ShadowFormat` UI ของ Word รองรับเงา gradient, แต่สคีม่า Open XML (ที่ Aspose.Words ปฏิบัติตาม) ให้เฉพาะเงาสีทึบเท่านั้น คุณต้องแก้ไข XML ด้านล่างด้วยตนเอง—เป็นกรณีขั้นสูง

**ถาม: ต้องการสี่เหลี่ยมโปร่งใสที่มีแค่เงาเท่านั้นทำอย่างไร?**  
ตอบ: ตั้ง `rectangle.FillColor = Color.Transparent;` หลังการแทรก เงาจะยังคงแสดงเพราะเป็นอิสระจากสีเติม

## เคล็ดลับสำหรับโค้ดระดับ Production

- **ใช้ builder ซ้ำ:** หากเพิ่มหลายรูป, ใช้ instance `DocumentBuilder` เดียวกัน—การสร้างใหม่สำหรับแต่ละรูปเพิ่มภาระโดยไม่จำเป็น  
- **บันทึกเป็นชุด:** บันทึกครั้งเดียวหลังทำการแก้ไขทั้งหมด; I/O บ่อยทำให้การสร้างเอกสารขนาดใหญ่ช้าลง  
- **จัดการข้อผิดพลาด:** ห่อบล็อกทั้งหมดใน `try / catch` แล้วบันทึกข้อยกเว้นของ `Aspose.Words`; ข้อยกเว้นมักมีหมายเลขบรรทัดที่ช่วยเมื่อเทมเพลตเอกสารเสียหาย

## ขั้นตอนต่อไป (Related Topics)

- **วิธีเพิ่มเงา** ให้รูปภาพหรือกล่องข้อความ (การใช้ `ShadowFormat` แบบเดียวกัน)  
- **แทรกสี่เหลี่ยม** ภายในเซลล์ตารางเพื่อสไตล์เซลล์แบบกำหนดเอง  
- **สร้างสี่เหลี่ยมใน Word** ด้วย XML ดิบของ Word (สำหรับผู้ที่ชอบ Open XML ดิบ)  
- **ตั้งค่าสีเงา** แบบไดนามิกตามอินพุตของผู้ใช้หรือธีมสี

ลองเล่นกับสีต่าง ๆ, รัศมีเบลอ, และการเยื้อง—อาจเป็นแสงสีฟ้าอ่อนสำหรับรายงานองค์กร, หรือเงาดำลึกสำหรับโบรชัวร์ที่ดราม่า ความเป็นไปได้ไม่มีที่สิ้นสุด, และการเปลี่ยนโค้ดก็แค่เล็กน้อย

---

### สรุปสั้น ๆ

- เรา **สร้างเอกสาร word** ตั้งแต่ต้น  
- เรา **แทรกสี่เหลี่ยม** และเปิดเงาให้มัน  
- เรา **ตั้งค่าสีเงา**, เบลอ, และการเยื้องเพื่อให้ได้ลุคมืออาชีพ  
- เราบันทึกไฟล์พร้อมแจกจ่าย

ตอนนี้คุณมีพื้นฐานแข็งแรงสำหรับเพิ่มความสวยงามให้กับโครงการอัตโนมัติ Word ของคุณ มีไอเดียเพิ่มเติม? แสดงความคิดเห็นและเราจะคุยต่อไป ขอให้โค้ดสนุก!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}