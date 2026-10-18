---
title: แทรกวันที่ไดนามิกในส่วนหัวของเอกสาร Word ด้วย Aspose.Words for .NET
weight: 110
limit:
description: เรียนรู้วิธีเพิ่มฟิลด์ DATE แบบไดนามิกลงในส่วนหัวหลักของเอกสาร Word ด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: เรียนรู้วิธีเพิ่มฟิลด์ DATE แบบไดนามิกลงในส่วนหัวหลักของเอกสาร Word
    ด้วย Aspose.Words for .NET
  headline: แทรกวันที่ไดนามิกในส่วนหัวของเอกสาร Word ด้วย Aspose.Words for .NET
  type: TechArticle
- description: เรียนรู้วิธีเพิ่มฟิลด์ DATE แบบไดนามิกลงในส่วนหัวหลักของเอกสาร Word
    ด้วย Aspose.Words for .NET
  name: แทรกวันที่ไดนามิกในส่วนหัวของเอกสาร Word ด้วย Aspose.Words for .NET
  steps:
  - name: สร้าง Document ใหม่และ DocumentBuilder เพื่อแก้ไขมัน
    text: สร้าง Document ใหม่และ DocumentBuilder เพื่อแก้ไขมัน
  - name: ย้ายเคอร์เซอร์ของ builder ไปยังส่วนหัวหลักเพื่อให้การแทรกต่อไปมีผลต่อส่วนหัว
    text: ย้ายเคอร์เซอร์ของ builder ไปยังส่วนหัวหลักเพื่อให้การแทรกต่อไปมีผลต่อส่วนหัว
  - name: เขียนข้อความคงที่และแทรกฟิลด์ DATE ที่มีรูปแบบ “MMMM d, yyyy” ลงในส่วนหัว
      เพื่อสร้างวันที่แบบไดนามิก
    text: เขียนข้อความคงที่และแทรกฟิลด์ DATE ที่มีรูปแบบ “MMMM d, yyyy” ลงในส่วนหัว
      เพื่อสร้างวันที่แบบไดนามิก
  - name: กลับไปที่เนื้อหาหลักและเพิ่มย่อหน้าตัวอย่าง เพื่อแสดงเนื้อหาเอกสารปกติพร้อมกับส่วนหัว
    text: กลับไปที่เนื้อหาหลักและเพิ่มย่อหน้าตัวอย่าง เพื่อแสดงเนื้อหาเอกสารปกติพร้อมกับส่วนหัว
  - name: บันทึกเอกสารเป็นไฟล์ .docx
    text: บันทึกเอกสารเป็นไฟล์ .docx
  type: HowTo
- questions:
  - answer: คำสั่ง `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` จะวางตำแหน่ง
      builder ไว้ที่ส่วนหัวหลักที่มีอยู่แล้ว และ `Write`/`InsertField` จะเพียงแค่ต่อข้อความต่อจากสิ่งที่มีอยู่
      ไม่ได้ลบเนื้อหาเดิม
    question: ถ้าเอกสารมีส่วนหัวหลักอยู่แล้ว จะเกิดอะไรขึ้น – โค้ดของฉันจะเขียนทับมันหรือไม่?
  - answer: ได้ – ปรับรูปแบบสวิตช์ในโค้ดฟิลด์ที่ส่งให้ `InsertField` เช่น `builder.InsertField("DATE
      \\@ \"yyyy-MM-dd\"")` จะให้ผลลัพธ์เป็นวันที่เช่น 2026-09-22
    question: ฉันสามารถเปลี่ยนรูปแบบวันที่ที่ใช้โดยฟิลด์ DATE ได้หรือไม่ และทำอย่างไร?
  - answer: เปลี่ยน `HeaderFooterType.HeaderPrimary` เป็น `HeaderFooterType.HeaderFirst`
      เมื่อเรียก `MoveToHeaderFooter`; ส่วนอื่นของโค้ดยังคงทำงานเช่นเดิม
    question: ถ้าต้องการฟิลด์วันที่ในส่วนหัวหน้าแรกแทนส่วนหัวหลัก ควรทำอย่างไร?
  - answer: ฟิลด์ถูกแทรกด้วยสวิตช์ `\@` เท่านั้น ซึ่งบอก Word ให้แสดงวันที่ปัจจุบันทุกครั้งที่ฟิลด์ถูกรีเฟรช
      (เช่น เมื่อเปิดไฟล์หรือเมื่อกด Ctrl+Alt+F9)
    question: ฟิลด์ DATE จะอัปเดตโดยอัตโนมัติเมื่อเปิดเอกสารในภายหลังหรือไม่?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: เพิ่มวันที่ไดนามิกในส่วนหัวของ Word
og_description: คู่มือขั้นตอนต่อขั้นตอนในการฝังฟิลด์วันที่แบบสดในส่วนหัว Word ของคุณด้วย Aspose.Words
og_image_alt: ภาพหน้าจอแสดงวิธีแทรกฟิลด์ DATE แบบไดนามิกลงในส่วนหัวของเอกสาร Word ด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกวันที่ไดนามิกในส่วนหัวของเอกสาร Word ด้วย Aspose.Words
บทเรียนนี้แสดงวิธีใช้คลาส Document และ DocumentBuilder ใน Aspose.Words for .NET เพื่อแทรกฟิลด์ DATE แบบไดนามิกลงในส่วนหัวหลักของเอกสาร Word ฟิลด์ที่เพิ่มจะอัปเดตโดยอัตโนมัติเพื่อแสดงวันที่ปัจจุบันทุกครั้งที่เปิดเอกสาร ทำให้ส่วนหัวของคุณแสดงวันที่ล่าสุดเสมอ ให้ทำตามโค้ดขั้นตอนต่อขั้นตอนเพื่อเพิ่มฟิลด์และบันทึกไฟล์ที่อัปเดต

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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

**Q: ถ้าเอกสารมีส่วนหัวหลักอยู่แล้ว จะเกิดอะไรขึ้น – โค้ดของฉันจะเขียนทับมันหรือไม่?**  
A: คำสั่ง `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` จะวางตำแหน่ง builder ไว้ที่ส่วนหัวหลักที่มีอยู่แล้ว และ `Write`/`InsertField` จะเพียงแค่ต่อข้อความต่อจากสิ่งที่มีอยู่ ไม่ได้ลบเนื้อหาเดิม

**Q: ฉันสามารถเปลี่ยนรูปแบบวันที่ที่ใช้โดยฟิลด์ DATE ได้หรือไม่ และทำอย่างไร?**  
A: ได้ – ปรับรูปแบบสวิตช์ในโค้ดฟิลด์ที่ส่งให้ `InsertField` เช่น `builder.InsertField("DATE \\@ \"yyyy-MM-dd\"")` จะให้ผลลัพธ์เป็นวันที่เช่น 2026-09-22

**Q: ถ้าต้องการฟิลด์วันที่ในส่วนหัวหน้าแรกแทนส่วนหัวหลัก ควรทำอย่างไร?**  
A: เปลี่ยน `HeaderFooterType.HeaderPrimary` เป็น `HeaderFooterType.HeaderFirst` เมื่อเรียก `MoveToHeaderFooter`; ส่วนอื่นของโค้ดยังคงทำงานเช่นเดิม

**Q: ฟิลด์ DATE จะอัปเดตโดยอัตโนมัติเมื่อเปิดเอกสารในภายหลังหรือไม่?**  
A: ฟิลด์ถูกแทรกด้วยสวิตช์ `\@` เท่านั้น ซึ่งบอก Word ให้แสดงวันที่ปัจจุบันทุกครั้งที่ฟิลด์ถูกรีเฟรช (เช่น เมื่อเปิดไฟล์หรือเมื่อกด Ctrl+Alt+F9)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}