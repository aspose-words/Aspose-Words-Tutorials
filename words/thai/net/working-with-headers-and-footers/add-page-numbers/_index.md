---
title: เพิ่มเลขหน้าไปยังส่วนท้ายของเอกสาร Word ด้วย Aspose.Words for .NET
weight: 210
limit:
description: เพิ่มเลขหน้าที่อัปเดตอัตโนมัติไปยังส่วนท้ายหลักของเอกสาร Word ด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: เพิ่มเลขหน้าที่อัปเดตอัตโนมัติไปยังส่วนท้ายหลักของเอกสาร Word ด้วย
    Aspose.Words for .NET
  headline: เพิ่มเลขหน้าไปยังส่วนท้ายของเอกสาร Word ด้วย Aspose.Words for .NET
  type: TechArticle
- description: เพิ่มเลขหน้าที่อัปเดตอัตโนมัติไปยังส่วนท้ายหลักของเอกสาร Word ด้วย
    Aspose.Words for .NET
  name: เพิ่มเลขหน้าไปยังส่วนท้ายของเอกสาร Word ด้วย Aspose.Words for .NET
  steps:
  - name: สร้างอ็อบเจกต์ Document ใหม่และ DocumentBuilder ที่เชื่อมโยงกับมัน
    text: สร้างอ็อบเจกต์ Document ใหม่และ DocumentBuilder ที่เชื่อมโยงกับมัน
  - name: ย้ายเคอร์เซอร์ของ builder ไปยังส่วนท้ายหลักของส่วนแรก
    text: ย้ายเคอร์เซอร์ของ builder ไปยังส่วนท้ายหลักของส่วนแรก
  - name: ตั้งค่าการจัดแนวของย่อหน้าเป็นศูนย์กลางเพื่อให้ข้อความส่วนท้ายอยู่กึ่งกลาง
    text: ตั้งค่าการจัดแนวของย่อหน้าเป็นศูนย์กลางเพื่อให้ข้อความส่วนท้ายอยู่กึ่งกลาง
  - name: เขียนข้อความป้าย "Page " แล้วแทรกฟิลด์ PAGE ที่แสดงเลขหน้าปัจจุบัน
    text: เขียนข้อความป้าย "Page " แล้วแทรกฟิลด์ PAGE ที่แสดงเลขหน้าปัจจุบัน
  - name: เขียน " of " แล้วแทรกฟิลด์ NUMPAGES ที่แสดงจำนวนหน้าทั้งหมด
    text: เขียน " of " แล้วแทรกฟิลด์ NUMPAGES ที่แสดงจำนวนหน้าทั้งหมด
  - name: บันทึกเอกสารเป็นไฟล์ .docx
    text: บันทึกเอกสารเป็นไฟล์ .docx
  type: HowTo
- questions:
  - answer: ไม่. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` จะย้าย builder
      ไปยังส่วนท้ายหลักของ *ส่วนแรก* เท่านั้น ดังนั้นฟิลด์จะถูกแทรกเฉพาะที่นั่น
    question: หากเอกสารมีมากกว่าหนึ่งส่วน โค้ดนี้จะเพิ่มเลขหน้าไปยังส่วนท้ายของทุกส่วนหรือไม่?
  - answer: ตั้งค่า `builder.ParagraphFormat.Alignment` เป็นค่า `ParagraphAlignment`
      อื่น (เช่น `ParagraphAlignment.Right`) ก่อนเขียนฟิลด์
    question: ฉันจะเปลี่ยนการจัดแนวของย่อหน้าเลขหน้าในส่วนท้ายได้อย่างไร?
  - answer: '`InsertField` รับโค้ดฟิลด์และผลลัพธ์ฟิลด์ที่เป็นออปชัน; การส่ง `null`
      บอกให้ Aspose.Words ให้ Word คำนวณผลลัพธ์ในขณะรันไทม์'
    question: '`null` ในอาร์กิวเมนต์ของ `InsertField("PAGE", null)` หมายถึงอะไร?'
  - answer: ได้—ให้แทนที่ `HeaderFooterType.FooterPrimary` ด้วย `HeaderFooterType.HeaderPrimary`
      (หรือประเภทส่วนหัวอื่น) ก่อนแทรกฟิลด์
    question: ฉันสามารถวางฟิลด์ "Page X of Y" เดียวกันในส่วนหัวแทนส่วนท้ายได้หรือไม่?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: แทรกเลขหน้าที่อัตโนมัติในส่วนท้ายของ Word
og_description: โค้ดขั้นตอนต่อขั้นตอนเพื่อเพิ่มเลขหน้าที่แสดงแบบเรียลไทม์ในส่วนท้ายของ Word ด้วย Aspose.Words for .NET
og_image_alt: คู่มือแสดงวิธีเพิ่มเลขหน้าที่อัตโนมัติไปยังส่วนท้ายของเอกสาร Word ด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มเลขหน้าไปยังส่วนท้ายของเอกสาร Word ด้วย Aspose.Words
บทเรียนนี้แสดงวิธีใช้ Aspose.Words Document และ DocumentBuilder เพื่อแทรกเลขหน้าที่อัปเดตอัตโนมัติลงในส่วนท้ายหลักของเอกสาร Word การเพิ่มเลขหน้าโดยโปรแกรมจะทำให้การแบ่งหน้าเป็นแบบสม่ำเสมอตลอดไฟล์โดยไม่ต้องแก้ไขด้วยตนเอง โค้ดตัวอย่างพร้อมใช้งานในสภาพแวดล้อม .NET

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: หากเอกสารมีมากกว่าหนึ่งส่วน โค้ดนี้จะเพิ่มเลขหน้าไปยังส่วนท้ายของทุกส่วนหรือไม่?**  
A: ไม่. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` จะย้าย builder ไปยังส่วนท้ายหลักของ *ส่วนแรก* เท่านั้น ดังนั้นฟิลด์จะถูกแทรกเฉพาะที่นั่น

**Q: ฉันจะเปลี่ยนการจัดแนวของย่อหน้าเลขหน้าในส่วนท้ายได้อย่างไร?**  
A: ตั้งค่า `builder.ParagraphFormat.Alignment` เป็นค่า `ParagraphAlignment` อื่น (เช่น `ParagraphAlignment.Right`) ก่อนเขียนฟิลด์

**Q: `null` ในอาร์กิวเมนต์ของ `InsertField("PAGE", null)` หมายถึงอะไร?**  
A: `InsertField` รับโค้ดฟิลด์และผลลัพธ์ฟิลด์ที่เป็นออปชัน; การส่ง `null` บอกให้ Aspose.Words ให้ Word คำนวณผลลัพธ์ในขณะรันไทม์

**Q: ฉันสามารถวางฟิลด์ "Page X of Y" เดียวกันในส่วนหัวแทนส่วนท้ายได้หรือไม่?**  
A: ได้—ให้แทนที่ `HeaderFooterType.FooterPrimary` ด้วย `HeaderFooterType.HeaderPrimary` (หรือประเภทส่วนหัวอื่น) ก่อนแทรกฟิลด์

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}