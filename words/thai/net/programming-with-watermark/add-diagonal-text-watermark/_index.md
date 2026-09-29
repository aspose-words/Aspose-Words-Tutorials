---
title: สร้างลายน้ำข้อความแนวทแยงด้วยแบบอักษรกำหนดเองในเอกสาร Word โดยใช้ Aspose.Words for .NET
weight: 210
limit:
description: โค้ดแบบขั้นตอนต่อขั้นตอนสำหรับเพิ่มลายน้ำข้อความแนวทแยงด้วยแบบอักษรกำหนดเองในไฟล์ Word .docx โดยใช้ Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: โค้ดแบบขั้นตอนต่อขั้นตอนสำหรับเพิ่มลายน้ำข้อความแนวทแยงด้วยแบบอักษรกำหนดเองในไฟล์
    Word .docx โดยใช้ Aspose.Words for .NET.
  headline: สร้างลายน้ำข้อความแนวทแยงด้วยแบบอักษรกำหนดเองในเอกสาร Word โดยใช้ Aspose.Words
    for .NET
  type: TechArticle
- description: โค้ดแบบขั้นตอนต่อขั้นตอนสำหรับเพิ่มลายน้ำข้อความแนวทแยงด้วยแบบอักษรกำหนดเองในไฟล์
    Word .docx โดยใช้ Aspose.Words for .NET.
  name: สร้างลายน้ำข้อความแนวทแยงด้วยแบบอักษรกำหนดเองในเอกสาร Word โดยใช้ Aspose.Words
    for .NET
  steps:
  - name: สร้างอินสแตนซ์เอกสาร Word ว่างใหม่ชื่อ `document`.
    text: สร้างอินสแตนซ์เอกสาร Word ว่างใหม่ชื่อ `document`.
  - name: กำหนดค่า `watermarkSettings` ด้วยแบบอักษร Arial ขนาด 48‑pt สีเทา, การจัดวางแนวทแยง,
      และการเรนเดอร์แบบทึบ.
    text: กำหนดค่า `watermarkSettings` ด้วยแบบอักษร Arial ขนาด 48‑pt สีเทา, การจัดวางแนวทแยง,
      และการเรนเดอร์แบบทึบ.
  - name: ใช้ลายน้ำข้อความ "Private" กับ `document` โดยใช้การตั้งค่าที่กำหนดไว้ก่อนหน้า.
    text: ใช้ลายน้ำข้อความ "Private" กับ `document` โดยใช้การตั้งค่าที่กำหนดไว้ก่อนหน้า.
  - name: กำหนดเส้นทางไฟล์ที่ลายน้ำของเอกสารจะถูกบันทึก.
    text: กำหนดเส้นทางไฟล์ที่ลายน้ำของเอกสารจะถูกบันทึก.
  - name: บันทึก `document` ที่แก้ไขแล้วไปยังเส้นทางที่ระบุเป็นไฟล์ .docx.
    text: บันทึก `document` ที่แก้ไขแล้วไปยังเส้นทางที่ระบุเป็นไฟล์ .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` กำหนดว่าลายน้ำจะถูกเรนเดอร์ด้วยความทึบบางหรือไม่;
      ตั้งค่าเป็น `false` จะทำให้ลายน้ำทึบเต็มที่, ส่วน `true` จะใช้เอฟเฟกต์กึ่งโปร่งใสตามค่าเริ่มต้น.'
    question: ฟลัก **IsSemitrasparent** ควบคุมอะไรใน `TextWatermarkOptions`?
  - answer: ได้—ตั้งค่า property `Layout` เป็น `WatermarkLayout.Horizontal` (หรือค่า
      enum อื่น) ก่อนเรียก `document.Watermark.SetText`.
    question: ฉันสามารถเปลี่ยนการวางแนวของลายน้ำเป็นแนวนอนแทนแนวทแยงได้หรือไม่?
  - answer: Word จะใช้แบบอักษรเริ่มต้นของมันสำหรับลายน้ำ, ดังนั้นข้อความจะยังคงแสดงแต่อาจดูแตกต่างจากสไตล์ที่ต้องการ.
    question: จะเกิดอะไรขึ้นหาก `FontFamily` ที่ระบุ (เช่น "Arial") ไม่ได้ติดตั้งบนเครื่องเป้าหมาย?
  - answer: โหลดไฟล์ที่มีอยู่ด้วย `Document document = new Document("Existing.docx");`
      จากนั้นกำหนดค่า `TextWatermarkOptions` และเรียก `document.Watermark.SetText`
      ตามที่แสดง.
    question: สามารถเพิ่มลายน้ำในไฟล์ `.docx` ที่มีอยู่แล้วแทนการสร้างไฟล์ใหม่ได้หรือไม่?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: เพิ่มลายน้ำข้อความแนวทแยงด้วยแบบอักษรกำหนดเอง
og_description: เรียนรู้การฝังลายน้ำข้อความเอียงด้วยแบบอักษรของคุณลงในไฟล์ Word ภายในไม่กี่นาที.
og_image_alt: คู่มือแสดงวิธีเพิ่มลายน้ำข้อความแนวทแยงด้วยแบบอักษรกำหนดเองในเอกสาร Word โดยใช้ Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# สร้างลายน้ำข้อความแนวทแยงด้วยแบบอักษรกำหนดเองในเอกสาร Word โดยใช้ Aspose.Words
บทแนะนำนี้จะพาคุณผ่านขั้นตอนการสร้างเอกสาร Word ใหม่, กำหนดค่าลายน้ำข้อความแนวทแยงด้วยการตั้งค่าแบบอักษรที่คุณเลือก, นำไปใช้ผ่าน API Document.Watermark.SetText, และบันทึกผลลัพธ์เป็นไฟล์ .docx. เมื่อเสร็จคุณจะได้เอกสารที่มีลายน้ำอย่างมืออาชีพซึ่งแสดงแบรนด์หรือความเป็นเจ้าของของคุณ. โค้ดแบบขั้นตอนต่อขั้นตอนพร้อมคัดลอกไปใส่ในโครงการ .NET ใดก็ได้.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ฟลัก **IsSemitrasparent** ควบคุมอะไรใน `TextWatermarkOptions`?**  
A: `IsSemitrasparent` กำหนดว่าลายน้ำจะถูกเรนเดอร์ด้วยความทึบบางหรือไม่; ตั้งค่าเป็น `false` จะทำให้ลายน้ำทึบเต็มที่, ส่วน `true` จะใช้เอฟเฟกต์กึ่งโปร่งใสตามค่าเริ่มต้น.

**Q: ฉันสามารถเปลี่ยนการวางแนวของลายน้ำเป็นแนวนอนแทนแนวทแยงได้หรือไม่?**  
A: ได้—ตั้งค่า property `Layout` เป็น `WatermarkLayout.Horizontal` (หรือค่า enum อื่น) ก่อนเรียก `document.Watermark.SetText`.

**Q: จะเกิดอะไรขึ้นหาก `FontFamily` ที่ระบุ (เช่น "Arial") ไม่ได้ติดตั้งบนเครื่องเป้าหมาย?**  
A: Word จะใช้แบบอักษรเริ่มต้นของมันสำหรับลายน้ำ, ดังนั้นข้อความจะยังคงแสดงแต่อาจดูแตกต่างจากสไตล์ที่ต้องการ.

**Q: สามารถเพิ่มลายน้ำในไฟล์ `.docx` ที่มีอยู่แล้วแทนการสร้างไฟล์ใหม่ได้หรือไม่?**  
A: โหลดไฟล์ที่มีอยู่ด้วย `Document document = new Document("Existing.docx");` จากนั้นกำหนดค่า `TextWatermarkOptions` และเรียก `document.Watermark.SetText` ตามที่แสดง.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}