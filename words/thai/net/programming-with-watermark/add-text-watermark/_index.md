---
title: เพิ่มลายน้ำข้อความสีแดงแนวทแยงในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 110
limit:
description: ใช้ลายน้ำข้อความสีแดงแนวทแยงโดยอัตโนมัติในทุกไฟล์ Word ที่สร้างในชุดโดยใช้ Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: ใช้ลายน้ำข้อความสีแดงแนวทแยงโดยอัตโนมัติในทุกไฟล์ Word ที่สร้างในชุดโดยใช้
    Aspose.Words for .NET.
  headline: เพิ่มลายน้ำข้อความสีแดงแนวทแยงในเอกสาร Word ด้วย Aspose.Words for .NET
  type: TechArticle
- description: ใช้ลายน้ำข้อความสีแดงแนวทแยงโดยอัตโนมัติในทุกไฟล์ Word ที่สร้างในชุดโดยใช้
    Aspose.Words for .NET.
  name: เพิ่มลายน้ำข้อความสีแดงแนวทแยงในเอกสาร Word ด้วย Aspose.Words for .NET
  steps:
  - name: สร้างโฟลเดอร์ "GeneratedReports" ที่จะบันทึกไฟล์ผลลัพธ์.
    text: สร้างโฟลเดอร์ "GeneratedReports" ที่จะบันทึกไฟล์ผลลัพธ์.
  - name: เริ่มลูปที่ทำการสร้างเอกสารแยกกันสามไฟล์.
    text: เริ่มลูปที่ทำการสร้างเอกสารแยกกันสามไฟล์.
  - name: สร้างอ็อบเจกต์เอกสาร Word ใหม่ที่ว่างเปล่า.
    text: สร้างอ็อบเจกต์เอกสาร Word ใหม่ที่ว่างเปล่า.
  - name: ใช้ DocumentBuilder เพื่อเขียนบรรทัดหัวเรื่องและคำอธิบายลงในเอกสาร.
    text: ใช้ DocumentBuilder เพื่อเขียนบรรทัดหัวเรื่องและคำอธิบายลงในเอกสาร.
  - name: กำหนดลักษณะของลายน้ำ รวมถึงแบบอักษร, ขนาด, สี, และการจัดวางแนวทแยง.
    text: กำหนดลักษณะของลายน้ำ รวมถึงแบบอักษร, ขนาด, สี, และการจัดวางแนวทแยง.
  - name: ใช้ลายน้ำสีแดงแนวทแยงที่กำหนดพร้อมข้อความ "PROTECTED" กับเอกสาร.
    text: ใช้ลายน้ำสีแดงแนวทแยงที่กำหนดพร้อมข้อความ "PROTECTED" กับเอกสาร.
  - name: บันทึกเอกสารที่มีลายน้ำลงในโฟลเดอร์ "GeneratedReports" ด้วยชื่อไฟล์ที่ไม่ซ้ำกัน.
    text: บันทึกเอกสารที่มีลายน้ำลงในโฟลเดอร์ "GeneratedReports" ด้วยชื่อไฟล์ที่ไม่ซ้ำกัน.
  - name: ปิดลูปหลังจากประมวลผลเอกสารปัจจุบัน.
    text: ปิดลูปหลังจากประมวลผลเอกสารปัจจุบัน.
  type: HowTo
- questions:
  - answer: IsSemitrasparent กำหนดว่าลายน้ำจะถูกเรนเดอร์ด้วยความทึบบางหรือไม่; การตั้งค่าเป็น
      **true** ทำให้ข้อความเป็นกึ่งโปร่งแสงเพื่อให้เนื้อหาที่อยู่ด้านล่างอ่านได้ง่ายขึ้น.
    question: ตัวเลือก **IsSemitrasparent** ควบคุมอะไรและการตั้งค่าเป็น **true** มีผลอย่างไร?
  - answer: ใช่—ตั้งค่า property **Layout** เป็น **WatermarkLayout.Horizontal** ใน
      **TextWatermarkOptions** ก่อนเรียก **document.Watermark.SetText**.
    question: ฉันสามารถเปลี่ยนการวางแนวของลายน้ำเป็นแนวนอนแทนแนวทแยงได้หรือไม่?
  - answer: ส่วนย่อยนี้สร้างอินสแตนซ์ **Document** ใหม่ แต่คุณสามารถเปิดไฟล์ที่มีอยู่ใดก็ได้
      (เช่น `new Document("Existing.docx")`) แล้วเรียก **document.Watermark.SetText**
      เพื่อใช้ลายน้ำเดียวกัน.
    question: โค้ดนี้จะเพิ่มลายน้ำให้กับไฟล์ Word ที่มีอยู่หรือเฉพาะเอกสารที่สร้างใหม่เท่านั้น?
  - answer: กำหนดสีที่กำหนดเองด้วย **Color.FromArgb(red, green, blue)** ให้กับ property
      **Color** ของ **TextWatermarkOptions** เช่น `Color = Color.FromArgb(128, 0,
      128)` สำหรับสีม่วง.
    question: ฉันจะใช้สี RGB ที่กำหนดเองสำหรับลายน้ำแทน **Color.Red** ที่กำหนดไว้ล่วงหน้าได้อย่างไร?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: เพิ่มลายน้ำข้อความสีแดงแนวทแยงในเอกสาร Word
og_description: ดูวิธีการใช้ลายน้ำสีแดงแนวทแยงอัตโนมัติในแต่ละเอกสาร Word ในชุดด้วย Aspose.Words.
og_image_alt: คู่มือที่แสดงวิธีเพิ่มลายน้ำข้อความสีแดงแนวทแยงในเอกสาร Word ด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มลายน้ำข้อความสีแดงแนวทแยงในเอกสาร Word ด้วย Aspose.Words
บทแนะนำนี้แสดงวิธีการฝังลายน้ำข้อความสีแดงแนวทแยงโดยอัตโนมัติลงในแต่ละเอกสาร Word ที่สร้างระหว่างการสร้างรายงานแบบชุด โดยใช้คลาส Document และ DocumentBuilder ของ Aspose.Words for .NET ลายน้ำจะถูกนำไปใช้โดยโปรแกรมเมติกขณะไฟล์ถูกสร้าง เพื่อให้ทุกเอกสารมีแบรนด์หรือประกาศความลับเดียวกันโดยไม่ต้องทำด้วยมือ.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: ตัวเลือก **IsSemitrasparent** ควบคุมอะไรและการตั้งค่าเป็น **true** มีผลอย่างไร?**  
A: IsSemitrasparent กำหนดว่าลายน้ำจะถูกเรนเดอร์ด้วยความทึบบางหรือไม่; การตั้งค่าเป็น **true** ทำให้ข้อความเป็นกึ่งโปร่งแสงเพื่อให้เนื้อหาที่อยู่ด้านล่างอ่านได้ง่ายขึ้น.

**Q: ฉันสามารถเปลี่ยนการวางแนวของลายน้ำเป็นแนวนอนแทนแนวทแยงได้หรือไม่?**  
A: ใช่—ตั้งค่า property **Layout** เป็น **WatermarkLayout.Horizontal** ใน **TextWatermarkOptions** ก่อนเรียก **document.Watermark.SetText**.

**Q: โค้ดนี้จะเพิ่มลายน้ำให้กับไฟล์ Word ที่มีอยู่หรือเฉพาะเอกสารที่สร้างใหม่เท่านั้น?**  
A: ส่วนย่อยนี้สร้างอินสแตนซ์ **Document** ใหม่ แต่คุณสามารถเปิดไฟล์ที่มีอยู่ใดก็ได้ (เช่น `new Document("Existing.docx")`) แล้วเรียก **document.Watermark.SetText** เพื่อใช้ลายน้ำเดียวกัน.

**Q: ฉันจะใช้สี RGB ที่กำหนดเองสำหรับลายน้ำแทน **Color.Red** ที่กำหนดไว้ล่วงหน้าได้อย่างไร?**  
A: กำหนดสีที่กำหนดเองด้วย **Color.FromArgb(red, green, blue)** ให้กับ property **Color** ของ **TextWatermarkOptions** เช่น `Color = Color.FromArgb(128, 0, 128)` สำหรับสีม่วง.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}