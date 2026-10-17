---
title: ใช้สไตล์กำหนดเองกับข้อความคอมเมนต์ในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 310
limit:
description: เรียนรู้วิธีเพิ่มคอมเมนต์และใช้สไตล์ย่อหน้าที่กำหนดเองกับข้อความคอมเมนต์ทั้งหมดในเอกสาร Word ด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, style comment text, custom comment style, Word document comments, apply paragraph style, document branding]
url: /net/working-with-comments/style-comment-text/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้วิธีเพิ่มคอมเมนต์และใช้สไตล์ย่อหน้าที่กำหนดเองกับข้อความคอมเมนต์ทั้งหมดในเอกสาร
    Word ด้วย Aspose.Words for .NET
  headline: ใช้สไตล์กำหนดเองกับข้อความคอมเมนต์ในเอกสาร Word ด้วย Aspose.Words for
    .NET
  type: TechArticle
- description: เรียนรู้วิธีเพิ่มคอมเมนต์และใช้สไตล์ย่อหน้าที่กำหนดเองกับข้อความคอมเมนต์ทั้งหมดในเอกสาร
    Word ด้วย Aspose.Words for .NET
  name: ใช้สไตล์กำหนดเองกับข้อความคอมเมนต์ในเอกสาร Word ด้วย Aspose.Words for .NET
  steps:
  - name: สร้าง Document ใหม่ที่ว่างเปล่าและ DocumentBuilder เพื่อแก้ไขมัน
    text: สร้าง Document ใหม่ที่ว่างเปล่าและ DocumentBuilder เพื่อแก้ไขมัน
  - name: แทรกประโยคตัวอย่างสองประโยคลงในเอกสาร
    text: แทรกประโยคตัวอย่างสองประโยคลงในเอกสาร
  - name: สร้างคอมเมนต์โดย Carol ตั้งข้อความของคอมเมนต์ ย้ายไปที่จุดเริ่มต้นของเอกสาร
      และแนบคอมเมนต์ไปยังย่อหน้าแรก
    text: สร้างคอมเมนต์โดย Carol ตั้งข้อความของคอมเมนต์ ย้ายไปที่จุดเริ่มต้นของเอกสาร
      และแนบคอมเมนต์ไปยังย่อหน้าแรก
  - name: สร้างคอมเมนต์โดย Dave ตั้งข้อความของคอมเมนต์ ย้ายไปที่จุดสิ้นสุดของเอกสาร
      และแนบคอมเมนต์ไปยังย่อหน้าสุดท้าย
    text: สร้างคอมเมนต์โดย Dave ตั้งข้อความของคอมเมนต์ ย้ายไปที่จุดสิ้นสุดของเอกสาร
      และแนบคอมเมนต์ไปยังย่อหน้าสุดท้าย
  - name: กำหนดสไตล์ย่อหน้าที่กำหนดเองชื่อ "BrandComment" ด้วยฟอนต์ Arial ขนาด 10 pt
      สีฟ้าเข้ม และรูปแบบตัวหนา เพื่อให้สอดคล้องกับแบรนด์ขององค์กร
    text: กำหนดสไตล์ย่อหน้าที่กำหนดเองชื่อ "BrandComment" ด้วยฟอนต์ Arial ขนาด 10 pt
      สีฟ้าเข้ม และรูปแบบตัวหนา เพื่อให้สอดคล้องกับแบรนด์ขององค์กร
  - name: รวบรวมโหนด Comment ทั้งหมดในเอกสารไว้ในรายการ
    text: รวบรวมโหนด Comment ทั้งหมดในเอกสารไว้ในรายการ
  - name: วนซ้ำแต่ละคอมเมนต์และใช้สไตล์ BrandComment กับย่อหน้าทุกอันภายในคอมเมนต์
    text: วนซ้ำแต่ละคอมเมนต์และใช้สไตล์ BrandComment กับย่อหน้าทุกอันภายในคอมเมนต์
  - name: สร้างโฟลเดอร์ Results หากจำเป็นและบันทึกเอกสารที่แก้ไขแล้วเป็นไฟล์ StyledCommentsDocument.docx
    text: สร้างโฟลเดอร์ Results หากจำเป็นและบันทึกเอกสารที่แก้ไขแล้วเป็นไฟล์ StyledCommentsDocument.docx
  type: HowTo
- questions:
  - answer: โค้ดเรียก `commentNode.EnsureMinimum()` ซึ่งจะสร้างย่อหน้าเริ่มต้นหากคอมเมนต์ว่างเปล่า
      ดังนั้นการกำหนดสไตล์ต่อมาจะมีย่อหน้าที่ทำงานอยู่เสมอ
    question: จะเกิดอะไรขึ้นหากโหนดคอมเมนต์ไม่มีย่อหน้าเมื่อฉันรันลูปการใช้สไตล์?
  - answer: เฉพาะย่อหน้าภายในอ็อบเจ็กต์ `Comment` เท่านั้นที่ถูกจัดรูปแบบ; ข้อความ
      anchor ในเอกสารหลักจะคงรูปแบบเดิมไว้เนื่องจากสไตล์ถูกนำไปใช้กับ `para.ParagraphFormat.Style`
      ภายในแต่ละคอมเมนต์
    question: สไตล์กำหนดเอง "BrandComment" มีผลต่อ anchor ของคอมเมนต์ (ข้อความที่ไฮไลท์ในเอกสารหลัก)
      หรือเพียงข้อความของคอมเมนต์เท่านั้น?
  - answer: ได้, ดึงสไตล์ที่มีอยู่ด้วย `document.Styles["ExistingStyleName"]` แล้วกำหนดให้กับ
      `para.ParagraphFormat.Style` ในลูปเดียวกัน โดยข้ามขั้นตอน `document.Styles.Add`
    question: ฉันสามารถใช้สไตล์ย่อหน้าที่มีอยู่แล้วแทนการสร้างสไตล์ใหม่สำหรับคอมเมนต์ได้หรือไม่?
  - answer: มันจะคืนค่าโหนด `Comment` ทุกอันในโครงสร้างเอกสาร รวมถึงการตอบกลับที่ซ้อนกันด้วย
      เนื่องจากอาร์กิวเมนต์ `true` ทำให้การค้นหาเป็นแบบเรียกซ้ำ
    question: เมธอด `document.GetChildNodes(NodeType.Comment, true)` จะคืนค่าการตอบกลับของคอมเมนต์
      (โหนดคอมเมนต์ที่ซ้อนกัน) ด้วยหรือไม่?
  - answer: ไม่, `document.Styles.Add` จะสร้างสไตล์เฉพาะเมื่อไม่มีสไตล์ที่มีชื่อนั้นอยู่แล้ว;
      การรันครั้งต่อไปจะใช้สไตล์ "BrandComment" ที่มีอยู่แล้ว
    question: หากฉันรันโค้ดหลายครั้งบนเอกสารเดียวกัน จะมีสไตล์ "BrandComment" ซ้ำกันถูกสร้างขึ้นหรือไม่?
  type: FAQPage
images:
- /net/working-with-comments/style-comment-text/og-image.png
og_title: จัดรูปแบบข้อความคอมเมนต์ทั้งหมดในเอกสาร Word
og_description: ดูวิธีเพิ่มคอมเมนต์อย่างอัตโนมัติและกำหนดสไตล์ที่กำหนดเองให้กับคอมเมนต์ด้วย Aspose.Words for .NET
og_image_alt: ภาพหน้าจอแสดงเอกสาร Word ที่มีข้อความคอมเมนต์ที่จัดรูปแบบโดยใช้ Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ใช้สไตล์กำหนดเองกับข้อความคอมเมนต์ในเอกสาร Word ด้วย Aspose.Words
บทเรียนนี้แสดงวิธีใช้ Aspose.Words for .NET เพื่อเพิ่มคอมเมนต์ในไฟล์ Word อย่างอัตโนมัติและจากนั้นใช้สไตล์ย่อหน้าที่กำหนดเองกับย่อหน้าคอมเมนต์ทุกอัน การจัดรูปแบบข้อความคอมเมนต์ช่วยให้คุณมั่นใจว่าข้อคิดเห็นทั้งหมดสอดคล้องกับแบรนด์ขององค์กรโดยไม่ต้องทำการจัดรูปแบบด้วยตนเอง ตัวอย่างนี้ครอบคลุมการสร้างคอมเมนต์ การกำหนดสไตล์ และการกำหนดสไตล์นั้นให้กับบล็อกคอมเมนต์แต่ละอัน

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/style-comment-text" >}}


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

**Q: จะเกิดอะไรขึ้นหากโหนดคอมเมนต์ไม่มีย่อหน้าเมื่อฉันรันลูปการใช้สไตล์?**  
A: โค้ดเรียก `commentNode.EnsureMinimum()` ซึ่งจะสร้างย่อหน้าเริ่มต้นหากคอมเมนต์ว่างเปล่า ดังนั้นการกำหนดสไตล์ต่อมาจะมีย่อหน้าที่ทำงานอยู่เสมอ

**Q: สไตล์กำหนดเอง "BrandComment" มีผลต่อ anchor ของคอมเมนต์ (ข้อความที่ไฮไลท์ในเอกสารหลัก) หรือเพียงข้อความของคอมเมนต์เท่านั้น?**  
A: เฉพาะย่อหน้าภายในอ็อบเจ็กต์ `Comment` เท่านั้นที่ถูกจัดรูปแบบ; ข้อความ anchor ในเอกสารหลักจะคงรูปแบบเดิมไว้เนื่องจากสไตล์ถูกนำไปใช้กับ `para.ParagraphFormat.Style` ภายในแต่ละคอมเมนต์

**Q: ฉันสามารถใช้สไตล์ย่อหน้าที่มีอยู่แล้วแทนการสร้างสไตล์ใหม่สำหรับคอมเมนต์ได้หรือไม่?**  
A: ได้, ดึงสไตล์ที่มีอยู่ด้วย `document.Styles["ExistingStyleName"]` แล้วกำหนดให้กับ `para.ParagraphFormat.Style` ในลูปเดียวกัน โดยข้ามขั้นตอน `document.Styles.Add`

**Q: เมธอด `document.GetChildNodes(NodeType.Comment, true)` จะคืนค่าการตอบกลับของคอมเมนต์ (โหนดคอมเมนต์ที่ซ้อนกัน) ด้วยหรือไม่?**  
A: มันจะคืนค่าโหนด `Comment` ทุกอันในโครงสร้างเอกสาร รวมถึงการตอบกลับที่ซ้อนกันด้วย เนื่องจากอาร์กิวเมนต์ `true` ทำให้การค้นหาเป็นแบบเรียกซ้ำ

**Q: หากฉันรันโค้ดหลายครั้งบนเอกสารเดียวกัน จะมีสไตล์ "BrandComment" ซ้ำกันถูกสร้างขึ้นหรือไม่?**  
A: ไม่, `document.Styles.Add` จะสร้างสไตล์เฉพาะเมื่อไม่มีสไตล์ที่มีชื่อนั้นอยู่แล้ว; การรันครั้งต่อไปจะใช้สไตล์ "BrandComment" ที่มีอยู่แล้ว

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}