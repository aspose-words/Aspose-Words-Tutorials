---
title: แทรก Comment บนย่อหน้าที่กำหนดในเอกสาร Word โดยใช้ Aspose.Words for .NET
weight: 210
limit:
description: คู่มือขั้นตอนต่อขั้นตอนในการเพิ่มคอมเมนต์ของผู้เขียนไปยังย่อหน้าที่เลือกในเอกสาร Word และบันทึกเป็น DOCX ด้วย Aspose.Words for .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: คู่มือขั้นตอนต่อขั้นตอนในการเพิ่มคอมเมนต์ของผู้เขียนไปยังย่อหน้าที่เลือกในเอกสาร
    Word และบันทึกเป็น DOCX ด้วย Aspose.Words for .NET.
  headline: แทรก Comment บนย่อหน้าที่กำหนดในเอกสาร Word โดยใช้ Aspose.Words for .NET
  type: TechArticle
- description: คู่มือขั้นตอนต่อขั้นตอนในการเพิ่มคอมเมนต์ของผู้เขียนไปยังย่อหน้าที่เลือกในเอกสาร
    Word และบันทึกเป็น DOCX ด้วย Aspose.Words for .NET.
  name: แทรก Comment บนย่อหน้าที่กำหนดในเอกสาร Word โดยใช้ Aspose.Words for .NET
  steps:
  - name: สร้างอินสแตนซ์ของ Document ใหม่และ DocumentBuilder เพื่อเริ่มสร้างไฟล์ Word.
    text: สร้างอินสแตนซ์ของ Document ใหม่และ DocumentBuilder เพื่อเริ่มสร้างไฟล์ Word.
  - name: ใช้ DocumentBuilder.Writeln เพื่อเพิ่มข้อความสามย่อหน้าแยกกันลงในเอกสาร.
    text: ใช้ DocumentBuilder.Writeln เพื่อเพิ่มข้อความสามย่อหน้าแยกกันลงในเอกสาร.
  - name: ดึงย่อหน้าที่สองอย่างปลอดภัย, หากเอกสารมีน้อยกว่าย่อหน้า 2 จะใช้ย่อหน้าแรกแทน.
    text: ดึงย่อหน้าที่สองอย่างปลอดภัย, หากเอกสารมีน้อยกว่าย่อหน้า 2 จะใช้ย่อหน้าแรกแทน.
  - name: สร้าง Comment พร้อมรายละเอียดผู้เขียน, ตั้งค่าข้อความของมัน, และแนบไปยังย่อหน้าที่เลือก.
    text: สร้าง Comment พร้อมรายละเอียดผู้เขียน, ตั้งค่าข้อความของมัน, และแนบไปยังย่อหน้าที่เลือก.
  - name: บันทึกเอกสารที่แก้ไขเป็นไฟล์ DOCX ชื่อ 'sample.docx' ในโฟลเดอร์ปัจจุบัน.
    text: บันทึกเอกสารที่แก้ไขเป็นไฟล์ DOCX ชื่อ 'sample.docx' ในโฟลเดอร์ปัจจุบัน.
  type: HowTo
- questions:
  - answer: '`if` block จะใช้ย่อหน้าแรก (`paraList[0]`) เมื่อ `paraList.Count` น้อยกว่า
      2 ดังนั้นคอมเมนต์จะถูกแนบไปยังย่อหน้าเดียวนั้นแทนที่จะเป็นย่อหน้าที่สองที่ไม่มี.'
    question: โค้ดทำอะไรเมื่อเอกสารมีเพียงย่อหน้าเดียว?
  - answer: พวกมันถูกส่งไปยังคอนสตรัคเตอร์ `Comment` เป็นอาร์กิวเมนต์ที่สองและสาม
      – `new Comment(wordDoc, "Jordan", "JH", DateTime.Now)` – โดยที่ "Jordan" คือชื่อผู้เขียนและ
      "JH" คืออักษรย่อ.
    question: ชื่อผู้เขียนและอักษรย่อของคอมเมนต์ถูกตั้งค่าอย่างไรในตัวอย่างนี้?
  - answer: ในโค้ดส่วนนี้คอมเมนต์ถูกเชื่อมโยงกับ `Paragraph` ทั้งหมดผ่าน `AppendChild`
      แต่หากต้องการคอมเมนต์บนช่วงข้อความ คุณต้องสร้าง `CommentRangeStart` และ `CommentRangeEnd`
      รอบโหนด `Run` ที่ต้องการ แล้วเพิ่มโหนด `Comment` ระหว่างพวกมัน.
    question: ฉันสามารถแนบคอมเมนต์ไปยังข้อความส่วนหนึ่งโดยไม่ใช่ทั้งย่อหน้าได้หรือไม่?
  - answer: '`AppendChild` เพิ่มโหนด `Comment` ไปยังคอลเลกชันลูกของย่อหน้า, และ Aspose.Words
      จะสร้างเครื่องหมายเริ่มต้น/สิ้นสุดของคอมเมนต์ที่จำเป็นโดยอัตโนมัติเมื่อบันทึกเอกสาร.'
    question: ฉันต้องใส่เครื่องหมายคอมเมนต์ด้วยตนเองหรือไม่, หรือ `AppendChild` จัดการให้เอง?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: แทรกคอมเมนต์ลงในย่อหน้า Word
og_description: เพิ่มคอมเมนต์ของผู้เขียนไปยังย่อหน้าที่กำหนดและส่งออกไฟล์เป็น DOCX ด้วย Aspose.Words.
og_image_alt: คู่มือแสดงวิธีเพิ่มคอมเมนต์ไปยังย่อหน้าในเอกสาร Word โดยใช้ Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรก Comment บนย่อหน้าที่กำหนดในเอกสาร Word โดยใช้ Aspose.Words
ด้วย Aspose.Words for .NET คุณสามารถเพิ่มคอมเมนต์ในไฟล์ Word ผ่านโปรแกรมได้ บทแนะนำนี้อธิบายขั้นตอนการสร้างเอกสารใหม่, แทรกย่อหน้า 3 ย่อหน้า, ค้นหาย่อหน้าที่สอง, และแนบคอมเมนต์ที่มีข้อมูลผู้เขียนและวันที่ สุดท้ายเอกสารจะถูกบันทึกเป็นไฟล์ DOCX ที่คงคอมเมนต์ไว้.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: โค้ดทำอะไรเมื่อเอกสารมีเพียงย่อหน้าเดียว?**  
A: `if` block จะใช้ย่อหน้าแรก (`paraList[0]`) เมื่อ `paraList.Count` น้อยกว่า 2 ดังนั้นคอมเมนต์จะถูกแนบไปยังย่อหน้าเดียวนั้นแทนที่จะเป็นย่อหน้าที่สองที่ไม่มี.

**Q: ชื่อผู้เขียนและอักษรย่อของคอมเมนต์ถูกตั้งค่าอย่างไรในตัวอย่างนี้?**  
A: พวกมันถูกส่งไปยังคอนสตรัคเตอร์ `Comment` เป็นอาร์กิวเมนต์ที่สองและสาม – `new Comment(wordDoc, "Jordan", "JH", DateTime.Now)` – โดยที่ "Jordan" คือชื่อผู้เขียนและ "JH" คืออักษรย่อ.

**Q: ฉันสามารถแนบคอมเมนต์ไปยังข้อความส่วนหนึ่งโดยไม่ใช่ทั้งย่อหน้าได้หรือไม่?**  
A: ในโค้ดส่วนนี้คอมเมนต์ถูกเชื่อมโยงกับ `Paragraph` ทั้งหมดผ่าน `AppendChild` แต่หากต้องการคอมเมนต์บนช่วงข้อความ คุณต้องสร้าง `CommentRangeStart` และ `CommentRangeEnd` รอบโหนด `Run` ที่ต้องการ แล้วเพิ่มโหนด `Comment` ระหว่างพวกมัน.

**Q: ฉันต้องใส่เครื่องหมายคอมเมนต์ด้วยตนเองหรือไม่, หรือ `AppendChild` จัดการให้เอง?**  
A: `AppendChild` เพิ่มโหนด `Comment` ไปยังคอลเลกชันลูกของย่อหน้า, และ Aspose.Words จะสร้างเครื่องหมายเริ่มต้น/สิ้นสุดของคอมเมนต์ที่จำเป็นโดยอัตโนมัติเมื่อบันทึกเอกสาร.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}