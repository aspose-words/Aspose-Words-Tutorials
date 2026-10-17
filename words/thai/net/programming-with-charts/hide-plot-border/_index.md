---
title: ซ่อนขอบพื้นที่พล็อตในแผนภูมิคอลัมน์ด้วย Aspose.Words for .NET
weight: 410
limit:
description: เรียนรู้วิธีซ่อนขอบพื้นที่พล็อตของแผนภูมิในขณะที่ยังคงให้เส้นแกนมองเห็นในแผนภูมิคอลัมน์ของ Word ด้วย Aspose.Words for .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้วิธีซ่อนขอบพื้นที่พล็อตของแผนภูมิในขณะที่ยังคงให้เส้นแกนมองเห็นในแผนภูมิคอลัมน์ของ
    Word ด้วย Aspose.Words for .NET.
  headline: ซ่อนขอบพื้นที่พล็อตในแผนภูมิคอลัมน์ด้วย Aspose.Words for .NET
  type: TechArticle
- description: เรียนรู้วิธีซ่อนขอบพื้นที่พล็อตของแผนภูมิในขณะที่ยังคงให้เส้นแกนมองเห็นในแผนภูมิคอลัมน์ของ
    Word ด้วย Aspose.Words for .NET.
  name: ซ่อนขอบพื้นที่พล็อตในแผนภูมิคอลัมน์ด้วย Aspose.Words for .NET
  steps:
  - name: สร้างเอกสาร Word ว่างใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนั้น.
    text: สร้างเอกสาร Word ว่างใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนั้น.
  - name: แทรกแผนภูมิคอลัมน์ขนาด 432×252 ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน.
    text: แทรกแผนภูมิคอลัมน์ขนาด 432×252 ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน.
  - name: ล้างซีรีส์ที่มีอยู่ทั้งหมด, กำหนดป้ายชื่อหมวดหมู่สามรายการ, และเพิ่มซีรีส์ที่มีค่าตัวอย่างลงในแผนภูมิ.
    text: ล้างซีรีส์ที่มีอยู่ทั้งหมด, กำหนดป้ายชื่อหมวดหมู่สามรายการ, และเพิ่มซีรีส์ที่มีค่าตัวอย่างลงในแผนภูมิ.
  - name: ตั้งค่า stroke weight ของพื้นที่พล็อตเป็นศูนย์, ลบขอบของมันออกในขณะที่ยังคงให้เส้นแกนมองเห็น.
    text: ตั้งค่า stroke weight ของพื้นที่พล็อตเป็นศูนย์, ลบขอบของมันออกในขณะที่ยังคงให้เส้นแกนมองเห็น.
  - name: บันทึกเอกสารที่แก้ไขแล้วเป็นไฟล์ .docx.
    text: บันทึกเอกสารที่แก้ไขแล้วเป็นไฟล์ .docx.
  type: HowTo
- questions:
  - answer: '`Stroke` เป็นคุณสมบัติของรูปแบบโดยรวมของอ็อบเจ็กต์ `Chart`, ซึ่งวาดขอบสี่เหลี่ยมรอบพื้นที่พล็อต;
      เส้นแกนเป็นอ็อบเจ็กต์ `Axis` แยกต่างหากและไม่ได้รับผลกระทบจากการตั้งค่า `Stroke`
      ของแผนภูมิ.'
    question: ทำไมการตั้งค่า `columnChart.Format.Stroke.Weight = 0` ถึงทำให้ขอบพื้นที่พล็อตหายไปแต่ยังคงให้เส้นแกนมองเห็น?
  - answer: ไม่, คุณสมบัติ `Stroke` ควบคุมขอบพื้นที่พล็อตทั้งหมดเป็นสี่เหลี่ยมเดียว,
      ดังนั้นไม่สามารถซ่อนขอบบางส่วนได้ผ่าน Aspose.Words; คุณต้องใส่รูปทรงกำหนดเองทับหรือแก้ไขแผนภูมิด้วยตนเอง.
    question: ฉันสามารถซ่อนขอบพื้นที่พล็อตเพียงด้านเดียว (เช่น ด้านซ้าย) ในขณะที่ยังคงให้สามด้านอื่นมองเห็นได้หรือไม่?
  - answer: ใช่, คุณสมบัติ `Stroke` ไม่ขึ้นกับ `ChartType`, ดังนั้นการตั้งค่า `Weight`
      เป็น 0 จะลบขอบพื้นที่พล็อตสำหรับ Line, Pie หรือประเภทแผนภูมิที่รองรับอื่นใด.
    question: ถ้าฉันเปลี่ยนประเภทแผนภูมิเป็น Line หรือ Pie, `columnChart.Format.Stroke.Weight
      = 0` จะยังคงซ่อนขอบพื้นที่พล็อตหรือไม่?
  - answer: ไม่จำเป็นต้องรีเฟรชเพิ่มเติม; การล้างซีรีส์และเพิ่มใหม่จะอัปเดตแผนภูมิภายใน,
      และ `wordDoc.Save(...)` จะเขียนสถานะปัจจุบันลงในไฟล์ .docx.
    question: หลังจากเรียก `columnChart.Series.Clear()` ฉันต้องรีเฟรชแผนภูมิก่อนบันทึกเอกสารหรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: ซ่อนขอบพล็อตในแผนภูมิคอลัมน์ของ Word
og_description: ลบขอบพื้นที่พล็อตในขณะที่ยังคงให้เส้นแกนมองเห็นในแผนภูมิคอลัมน์ของ Word ด้วย Aspose.Words for .NET.
og_image_alt: คู่มือที่แสดงเอกสาร Word พร้อมแผนภูมิคอลัมน์ที่ขอบพื้นที่พล็อตถูกซ่อนแต่เส้นแกนยังคงมองเห็นโดยใช้ Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ซ่อนขอบพื้นที่พล็อตในแผนภูมิคอลัมน์ด้วย Aspose.Words
ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีสร้างเอกสาร Word, แทรกแผนภูมิคอลัมน์, เติมข้อมูลตัวอย่าง, แล้วซ่อนขอบพื้นที่พล็อตของแผนภูมิในขณะที่ยังคงให้เส้นแกนมองเห็น. โค้ดแบบขั้นตอนแสดงแต่ละการดำเนินการและจบด้วยการบันทึกเอกสาร, เพื่อให้คุณเห็นผลลัพธ์ทันที.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: ทำไมการตั้งค่า `columnChart.Format.Stroke.Weight = 0` ถึงทำให้ขอบพื้นที่พล็อตหายไปแต่ยังคงให้เส้นแกนมองเห็น?**  
A: `Stroke` เป็นคุณสมบัติของรูปแบบโดยรวมของอ็อบเจ็กต์ `Chart`, ซึ่งวาดขอบสี่เหลี่ยมรอบพื้นที่พล็อต; เส้นแกนเป็นอ็อบเจ็กต์ `Axis` แยกต่างหากและไม่ได้รับผลกระทบจากการตั้งค่า `Stroke` ของแผนภูมิ.

**Q: ฉันสามารถซ่อนขอบพื้นที่พล็อตเพียงด้านเดียว (เช่น ด้านซ้าย) ในขณะที่ยังคงให้สามด้านอื่นมองเห็นได้หรือไม่?**  
A: ไม่, คุณสมบัติ `Stroke` ควบคุมขอบพื้นที่พล็อตทั้งหมดเป็นสี่เหลี่ยมเดียว, ดังนั้นไม่สามารถซ่อนขอบบางส่วนได้ผ่าน Aspose.Words; คุณต้องใส่รูปทรงกำหนดเองทับหรือแก้ไขแผนภูมิด้วยตนเอง.

**Q: ถ้าฉันเปลี่ยนประเภทแผนภูมิเป็น Line หรือ Pie, `columnChart.Format.Stroke.Weight = 0` จะยังคงซ่อนขอบพื้นที่พล็อตหรือไม่?**  
A: ใช่, คุณสมบัติ `Stroke` ไม่ขึ้นกับ `ChartType`, ดังนั้นการตั้งค่า `Weight` เป็น 0 จะลบขอบพื้นที่พล็อตสำหรับ Line, Pie หรือประเภทแผนภูมิที่รองรับอื่นใด.

**Q: หลังจากเรียก `columnChart.Series.Clear()` ฉันต้องรีเฟรชแผนภูมิก่อนบันทึกเอกสารหรือไม่?**  
A: ไม่จำเป็นต้องรีเฟรชเพิ่มเติม; การล้างซีรีส์และเพิ่มใหม่จะอัปเดตแผนภูมิภายใน, และ `wordDoc.Save(...)` จะเขียนสถานะปัจจุบันลงในไฟล์ .docx.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}