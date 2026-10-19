---
title: เพิ่ม Hyperlink Comment และส่งออกเป็น PDF Annotation ด้วย Aspose.Words for .NET
weight: 110
limit:
description: เรียนรู้การเพิ่ม hyperlink comment ในไฟล์ Word และส่งออกเป็น PDF annotation ด้วย Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้การเพิ่ม hyperlink comment ในไฟล์ Word และส่งออกเป็น PDF annotation
    ด้วย Aspose.Words for .NET.
  headline: เพิ่ม Hyperlink Comment และส่งออกเป็น PDF Annotation ด้วย Aspose.Words
    for .NET
  type: TechArticle
- description: เรียนรู้การเพิ่ม hyperlink comment ในไฟล์ Word และส่งออกเป็น PDF annotation
    ด้วย Aspose.Words for .NET.
  name: เพิ่ม Hyperlink Comment และส่งออกเป็น PDF Annotation ด้วย Aspose.Words for
    .NET
  steps:
  - name: สร้างอ็อบเจ็กต์ Document ว่างใหม่และ DocumentBuilder เพื่อทำงานกับมัน.
    text: สร้างอ็อบเจ็กต์ Document ว่างใหม่และ DocumentBuilder เพื่อทำงานกับมัน.
  - name: เขียนบรรทัดข้อความที่มองเห็นได้ซึ่งจะเป็นที่วางคอมเมนต์ที่กำลังจะเพิ่ม.
    text: เขียนบรรทัดข้อความที่มองเห็นได้ซึ่งจะเป็นที่วางคอมเมนต์ที่กำลังจะเพิ่ม.
  - name: สร้าง Comment ที่เขียนโดย Jane Doe และแนบเข้ากับย่อหน้าแรกของเอกสาร.
    text: สร้าง Comment ที่เขียนโดย Jane Doe และแนบเข้ากับย่อหน้าแรกของเอกสาร.
  - name: ภายในคอมเมนต์, เพิ่มย่อหน้าและแทรกลิงก์สีน้ำเงินที่มีขีดเส้นใต้ไปยังเว็บไซต์
      Aspose.Words Library.
    text: ภายในคอมเมนต์, เพิ่มย่อหน้าและแทรกลิงก์สีน้ำเงินที่มีขีดเส้นใต้ไปยังเว็บไซต์
      Aspose.Words Library.
  - name: ตั้งค่าเอกสารให้แสดงคอมเมนต์เป็น PDF annotation และรีเฟรชเลย์เอาต์.
    text: ตั้งค่าเอกสารให้แสดงคอมเมนต์เป็น PDF annotation และรีเฟรชเลย์เอาต์.
  - name: สร้างโฟลเดอร์ "Output" ในไดเรกทอรีปัจจุบันเพื่อเก็บ PDF ที่สร้างขึ้น.
    text: สร้างโฟลเดอร์ "Output" ในไดเรกทอรีปัจจุบันเพื่อเก็บ PDF ที่สร้างขึ้น.
  - name: บันทึกเอกสารที่เตรียมไว้เป็นไฟล์ PDF โดยใช้ PdfSaveOptions.
    text: บันทึกเอกสารที่เตรียมไว้เป็นไฟล์ PDF โดยใช้ PdfSaveOptions.
  - name: ตรวจสอบว่าไฟล์ PDF มีอยู่และมีข้อมูล, จากนั้นแสดงผลลัพธ์บนคอนโซล.
    text: ตรวจสอบว่าไฟล์ PDF มีอยู่และมีข้อมูล, จากนั้นแสดงผลลัพธ์บนคอนโซล.
  type: HowTo
- questions:
  - answer: พารามิเตอร์ที่สามของ `InsertHyperlink` ระบุว่าลิงก์ควรถือเป็นฟิลด์หรือไม่;
      ตั้งค่าเป็น `false` จะใส่ hyperlink ธรรมดาที่ทำงานใน PDF annotation โดยไม่ต้องใช้โค้ดฟิลด์.
    question: อาร์กิวเมนต์ที่สาม (`false`) ใน `InsertHyperlink` ควบคุมอะไร?
  - answer: ตั้งค่า `myDocument.LayoutOptions.CommentDisplayMode` เป็น `CommentDisplayMode.ShowInBalloons`
      ก่อนเรียก `Save`; จากนั้น PDF จะมีคอมเมนต์เป็นคอมเมนต์ Word ปกติแทนการเป็น annotation.
    question: ฉันจะทำให้คอมเมนต์แสดงเป็นบอลลูนในเอกสาร Word แทน PDF annotation ได้อย่างไร?
  - answer: ใช่—แต่ละ `Comment` ที่คุณเพิ่มลงในย่อหน้าสามารถมีการเรียก `InsertHyperlink`
      ของตนเองได้, และลิงก์ทั้งหมดจะถูกเก็บเป็น PDF annotation แยกกันเมื่อบันทึกเอกสาร.
    question: ถ้าฉันเพิ่มคอมเมนต์มากกว่าหนึ่งรายการ, ลิงก์แต่ละอันจะทำงานใน PDF ที่ส่งออกหรือไม่?
  - answer: เปิด PDF ที่สร้างขึ้น, ค้นหา comment annotation (มักแสดงเป็นไอคอนโน้ต),
      คลิกเพื่อแสดงข้อความคอมเมนต์, แล้วคลิกที่ลิงก์สีน้ำเงินที่มีขีดเส้นใต้; มันควรเปิด
      URL ปลายทางในเว็บเบราว์เซอร์.
    question: ฉันจะตรวจสอบว่าลิงก์ภายในคอมเมนต์ทำงานจริงหลังจากสร้าง PDF หรือไม่?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: แทรก Hyperlink Comment และส่งออกเป็น PDF
og_description: เรียนรู้การฝังลิงก์คลิกได้ในคอมเมนต์ของ Word และเปลี่ยนเป็น PDF annotation.
og_image_alt: คู่มือแสดงวิธีเพิ่มคอมเมนต์ที่มีลิงก์คลิกได้ในเอกสาร Word และส่งออกเป็น PDF annotation ด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่ม Hyperlink Comment และส่งออกเป็น PDF Annotation ด้วย Aspose.Words
ในบทแนะนำนี้คุณจะได้เห็นวิธีสร้างเอกสาร Word, แทรกคอมเมนต์ที่มีลิงก์คลิกได้ไปยังเว็บไซต์ภายนอก, ตั้งค่าให้คอมเมนต์แสดงเป็น PDF annotation, ส่งออกเอกสารเป็น PDF, และตรวจสอบไฟล์ PDF ที่ได้ ผลโค้ดแบบขั้นตอนช่วยให้คุณเพิ่มคอมเมนต์ที่มีลิงก์อย่างเต็มรูปแบบและคงไว้เมื่อตรวจแปลงเป็น PDF ทำให้ง่ายต่อการแชร์โน้ตเชิงโต้ตอบกับผู้อ่าน.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: อาร์กิวเมนต์ที่สาม (`false`) ใน `InsertHyperlink` ควบคุมอะไร?**  
A: พารามิเตอร์ที่สามของ `InsertHyperlink` ระบุว่าลิงก์ควรถือเป็นฟิลด์หรือไม่; ตั้งค่าเป็น `false` จะใส่ hyperlink ธรรมดาที่ทำงานใน PDF annotation โดยไม่ต้องใช้โค้ดฟิลด์.

**Q: ฉันจะทำให้คอมเมนต์แสดงเป็นบอลลูนในเอกสาร Word แทน PDF annotation ได้อย่างไร?**  
A: ตั้งค่า `myDocument.LayoutOptions.CommentDisplayMode` เป็น `CommentDisplayMode.ShowInBalloons` ก่อนเรียก `Save`; จากนั้น PDF จะมีคอมเมนต์เป็นคอมเมนต์ Word ปกติแทนการเป็น annotation.

**Q: ถ้าฉันเพิ่มคอมเมนต์มากกว่าหนึ่งรายการ, ลิงก์แต่ละอันจะทำงานใน PDF ที่ส่งออกหรือไม่?**  
A: ใช่—แต่ละ `Comment` ที่คุณเพิ่มลงในย่อหน้าสามารถมีการเรียก `InsertHyperlink` ของตนเองได้, และลิงก์ทั้งหมดจะถูกเก็บเป็น PDF annotation แยกกันเมื่อบันทึกเอกสาร.

**Q: ฉันจะตรวจสอบว่าลิงก์ภายในคอมเมนต์ทำงานจริงหลังจากสร้าง PDF หรือไม่?**  
A: เปิด PDF ที่สร้างขึ้น, ค้นหา comment annotation (มักแสดงเป็นไอคอนโน้ต), คลิกเพื่อแสดงข้อความคอมเมนต์, แล้วคลิกที่ลิงก์สีน้ำเงินที่มีขีดเส้นใต้; มันควรเปิด URL ปลายทางในเว็บเบราว์เซอร์.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}