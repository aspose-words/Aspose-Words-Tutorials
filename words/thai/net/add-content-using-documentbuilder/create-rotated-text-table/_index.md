---
title: สร้างตารางข้อความหมุนในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 110
limit:
description: เรียนรู้การสร้างตาราง Word ที่มีความกว้างคอลัมน์คงที่, ข้อความหมุน, ความสูงแถวที่แม่นยำ, และเซลล์ที่มีข้อมูลโดยใช้ Aspose.Words for .NET
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: เรียนรู้การสร้างตาราง Word ที่มีความกว้างคอลัมน์คงที่, ข้อความหมุน,
    ความสูงแถวที่แม่นยำ, และเซลล์ที่มีข้อมูลโดยใช้ Aspose.Words for .NET
  headline: สร้างตารางข้อความหมุนในเอกสาร Word ด้วย Aspose.Words for .NET
  type: TechArticle
- description: เรียนรู้การสร้างตาราง Word ที่มีความกว้างคอลัมน์คงที่, ข้อความหมุน,
    ความสูงแถวที่แม่นยำ, และเซลล์ที่มีข้อมูลโดยใช้ Aspose.Words for .NET
  name: สร้างตารางข้อความหมุนในเอกสาร Word ด้วย Aspose.Words for .NET
  steps:
  - name: สร้างอินสแตนซ์ใหม่ของ Document และ DocumentBuilder ที่จะใช้ในการสร้างตาราง
    text: สร้างอินสแตนซ์ใหม่ของ Document และ DocumentBuilder ที่จะใช้ในการสร้างตาราง
  - name: เริ่มตารางใหม่, แทรกเซลล์แรก, และกำหนดความกว้างคอลัมน์ให้คงที่เพื่อไม่ให้ปรับอัตโนมัติ
    text: เริ่มตารางใหม่, แทรกเซลล์แรก, และกำหนดความกว้างคอลัมน์ให้คงที่เพื่อไม่ให้ปรับอัตโนมัติ
  - name: จัดแนวเนื้อหาในแนวตั้งให้อยู่กึ่งกลางในเซลล์ปัจจุบันและเขียนข้อความของเซลล์แรกของแถวแรก
    text: จัดแนวเนื้อหาในแนวตั้งให้อยู่กึ่งกลางในเซลล์ปัจจุบันและเขียนข้อความของเซลล์แรกของแถวแรก
  - name: แทรกเซลล์ที่สองของแถวแรกและเขียนข้อความของมัน
    text: แทรกเซลล์ที่สองของแถวแรกและเขียนข้อความของมัน
  - name: ปิดแถวแรกเพื่อสรุปการจัดวางของแถว
    text: ปิดแถวแรกเพื่อสรุปการจัดวางของแถว
  - name: เริ่มเซลล์แรกของแถวที่สอง, ตั้งค่าความสูงของแถวให้เท่ากับ 100 พอยต์อย่างแม่นยำ,
      หมุนข้อความขึ้นด้านบน, และเขียนข้อความในเซลล์
    text: เริ่มเซลล์แรกของแถวที่สอง, ตั้งค่าความสูงของแถวให้เท่ากับ 100 พอยต์อย่างแม่นยำ,
      หมุนข้อความขึ้นด้านบน, และเขียนข้อความในเซลล์
  - name: แทรกเซลล์ที่สองของแถวที่สอง, หมุนข้อความของมันลงด้านล่าง, และเขียนข้อความในเซลล์
    text: แทรกเซลล์ที่สองของแถวที่สอง, หมุนข้อความของมันลงด้านล่าง, และเขียนข้อความในเซลล์
  - name: ปิดแถวที่สองเพื่อเสร็จสิ้นบรรทัดที่สองของตาราง
    text: ปิดแถวที่สองเพื่อเสร็จสิ้นบรรทัดที่สองของตาราง
  - name: ยุติการสร้างตารางเพื่อปิดโครงสร้างของตาราง
    text: ยุติการสร้างตารางเพื่อปิดโครงสร้างของตาราง
  - name: บันทึกเอกสารที่เสร็จสมบูรณ์เป็นไฟล์ .docx
    text: บันทึกเอกสารที่เสร็จสมบูรณ์เป็นไฟล์ .docx
  type: HowTo
- questions:
  - answer: หลังจากกำหนดความกว้างคอลัมน์แล้ว, ให้กำหนดความกว้างให้กับแต่ละเซลล์โดยใช้
      `builder.CellFormat.Width = <valueInPoints>;` ก่อนแทรกเซลล์ถัดไป; ตารางจะรักษาความกว้างที่แน่นอนเหล่านั้น
    question: ฉันจะตั้งค่าความกว้างคอลัมน์เฉพาะหลังจากเรียก `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`
      ได้อย่างไร?
  - answer: '`builder.CellFormat.VerticalAlignment` เป็นการตั้งค่าระดับเซลล์, ดังนั้นคุณต้องตั้งค่าใหม่สำหรับเซลล์ในแถวที่สอง
      (เช่น `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`)
      ก่อนเขียนเนื้อหา'
    question: ทำไมการจัดแนวแนวตั้งจึงส่งผลต่อแถวแรกเท่านั้นและไม่ส่งผลต่อแถวที่สอง?
  - answer: ได้—ตั้งค่า `builder.RowFormat.Height` และ `builder.RowFormat.HeightRule
      = HeightRule.Exactly` ก่อนเรียก `builder.EndRow();` ทุกครั้ง; แถวถัดไปสามารถมีค่าความสูงที่แตกต่างกันได้
    question: ฉันสามารถกำหนดความสูงที่แน่นอนแตกต่างกันให้แต่ละแถวได้หรือไม่? ถ้าได้ทำอย่างไร?
  - answer: รีเซ็ตการหมุนโดยกำหนด `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      ก่อนเขียนในเซลล์ถัดไป
    question: ฉันจะรีเซ็ตการหมุนข้อความกลับเป็นค่าเริ่มต้นหลังจากใช้ `TextOrientation.Upward`
      หรือ `Downward` อย่างไร?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: สร้างตารางข้อความหมุนใน Word ด้วย Aspose.Words
og_description: โค้ดขั้นตอนต่อขั้นตอนสำหรับสร้างตารางความกว้างคงที่ที่มีข้อความหมุนในแนวตั้งและความสูงแถวที่แน่นอน
og_image_alt: ภาพหน้าจอแสดงเอกสาร Word ที่มีตารางที่มีความกว้างคอลัมน์คงที่, ข้อความหมุนในเซลล์, และความสูงแถวที่กำหนด, สร้างด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# สร้างตารางข้อความหมุนในเอกสาร Word ด้วย Aspose.Words
บทแนะนำนี้แสดงวิธีสร้างเอกสาร Word และเพิ่มตารางที่คอลัมน์มีความกว้างคงที่, แถวมีความสูงที่แน่นอน, และข้อความในเซลล์ถูกหมุนในแนวตั้ง คุณจะได้เรียนรู้การตั้งค่าการจัดแนวแนวตั้ง, ใช้การหมุนข้อความ, เติมเนื้อหาในแต่ละเซลล์, และในที่สุดบันทึกเอกสาร—ทั้งหมดนี้ด้วย Aspose.Words for .NET

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ฉันจะตั้งค่าความกว้างคอลัมน์เฉพาะหลังจากเรียก `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` ได้อย่างไร?**  
A: หลังจากกำหนดความกว้างคอลัมน์แล้ว, ให้กำหนดความกว้างให้กับแต่ละเซลล์โดยใช้ `builder.CellFormat.Width = <valueInPoints>;` ก่อนแทรกเซลล์ถัดไป; ตารางจะรักษาความกว้างที่แน่นอนเหล่านั้น

**Q: ทำไมการจัดแนวแนวตั้งจึงส่งผลต่อแถวแรกเท่านั้นและไม่ส่งผลต่อแถวที่สอง?**  
A: `builder.CellFormat.VerticalAlignment` เป็นการตั้งค่าระดับเซลล์, ดังนั้นคุณต้องตั้งค่าใหม่สำหรับเซลล์ในแถวที่สอง (เช่น `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) ก่อนเขียนเนื้อหา

**Q: ฉันสามารถกำหนดความสูงที่แน่นอนแตกต่างกันให้แต่ละแถวได้หรือไม่? ถ้าได้ทำอย่างไร?**  
A: ได้—ตั้งค่า `builder.RowFormat.Height` และ `builder.RowFormat.HeightRule = HeightRule.Exactly` ก่อนเรียก `builder.EndRow();` ทุกครั้ง; แถวถัดไปสามารถมีค่าความสูงที่แตกต่างกันได้

**Q: ฉันจะรีเซ็ตการหมุนข้อความกลับเป็นค่าเริ่มต้นหลังจากใช้ `TextOrientation.Upward` หรือ `Downward` อย่างไร?**  
A: รีเซ็ตการหมุนโดยกำหนด `builder.CellFormat.Orientation = TextOrientation.Horizontal;` ก่อนเขียนในเซลล์ถัดไป

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}