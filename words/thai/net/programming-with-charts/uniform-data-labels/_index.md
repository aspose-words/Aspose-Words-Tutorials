---
title: ตั้งค่าป้ายกำกับข้อมูลแบบสม่ำเสมอในแผนภูมิคอลัมน์โดยใช้ Aspose.Words for .NET
weight: 110
limit:
description: เรียนรู้วิธีสร้างแผนภูมิคอลัมน์ใน Word และใช้ขนาดฟอนต์และสีของป้ายกำกับข้อมูลแบบสม่ำเสมอกับทุกชุดข้อมูลด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้วิธีสร้างแผนภูมิคอลัมน์ใน Word และใช้ขนาดฟอนต์และสีของป้ายกำกับข้อมูลแบบสม่ำเสมอกับทุกชุดข้อมูลด้วย
    Aspose.Words for .NET
  headline: ตั้งค่าป้ายกำกับข้อมูลแบบสม่ำเสมอในแผนภูมิคอลัมน์โดยใช้ Aspose.Words for
    .NET
  type: TechArticle
- description: เรียนรู้วิธีสร้างแผนภูมิคอลัมน์ใน Word และใช้ขนาดฟอนต์และสีของป้ายกำกับข้อมูลแบบสม่ำเสมอกับทุกชุดข้อมูลด้วย
    Aspose.Words for .NET
  name: ตั้งค่าป้ายกำกับข้อมูลแบบสม่ำเสมอในแผนภูมิคอลัมน์โดยใช้ Aspose.Words for .NET
  steps:
  - name: สร้างเอกสาร Word ว่างใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนั้น
    text: สร้างเอกสาร Word ว่างใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนั้น
  - name: แทรกแผนภูมิคอลัมน์ขนาด 500×300 ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน
    text: แทรกแผนภูมิคอลัมน์ขนาด 500×300 ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน
  - name: ลบชุดข้อมูลตัวอย่างเริ่มต้นที่ Aspose.Words เพิ่มเข้าไปในแผนภูมิใหม่
    text: ลบชุดข้อมูลตัวอย่างเริ่มต้นที่ Aspose.Words เพิ่มเข้าไปในแผนภูมิใหม่
  - name: กำหนดป้ายชื่อหมวดหมู่และเพิ่มชุดข้อมูลสองชุด (Item Alpha และ Item Beta)
      พร้อมค่าของพวกมันลงในแผนภูมิ
    text: กำหนดป้ายชื่อหมวดหมู่และเพิ่มชุดข้อมูลสองชุด (Item Alpha และ Item Beta)
      พร้อมค่าของพวกมันลงในแผนภูมิ
  - name: ตั้งค่าขนาดฟอนต์และสีพื้นฐานที่จะนำไปใช้กับป้ายกำกับข้อมูลทั้งหมด
    text: ตั้งค่าขนาดฟอนต์และสีพื้นฐานที่จะนำไปใช้กับป้ายกำกับข้อมูลทั้งหมด
  - name: เปิดใช้งานป้ายกำกับข้อมูลสำหรับแต่ละชุด, แสดงค่าตัวเลข, และใช้ขนาดฟอนต์และสีที่กำหนดไว้ล่วงหน้า
    text: เปิดใช้งานป้ายกำกับข้อมูลสำหรับแต่ละชุด, แสดงค่าตัวเลข, และใช้ขนาดฟอนต์และสีที่กำหนดไว้ล่วงหน้า
  - name: บันทึกเอกสารเป็นไฟล์ .docx
    text: บันทึกเอกสารเป็นไฟล์ .docx
  type: HowTo
- questions:
  - answer: '`InsertChart` สร้างแผนภูมิพร้อมชุดข้อมูลตัวอย่างเริ่มต้น; การลบออกจะทำให้ส่วนที่เป็นตัวแทนนั้นหายไป
      ดังนั้นแผนภูมิจะโชว์เฉพาะชุดข้อมูลที่คุณเพิ่ม (`Item Alpha` และ `Item Beta`)'
    question: ทำไมฉันต้องเรียก `chart.Series.Clear()` ก่อนเพิ่มชุดข้อมูลของฉันเอง?
  - answer: แทนที่ `Color.White` ด้วยค่า `System.Drawing.Color` ใดก็ได้ เช่น `Color.Black`
      หรือ `Color.FromArgb(255, 30, 144, 255)`; สีใหม่จะถูกนำไปใช้ผ่าน `series.DataLabels.Font.Color`
      ภายในลูป
    question: ฉันจะเปลี่ยนสีของป้ายกำกับข้อมูลให้เป็นสีอื่นที่ไม่ใช่สีขาวได้อย่างไร?
  - answer: ป้ายกำกับข้อมูลจะถูกซ่อน ทำให้การตั้งค่าฟอนต์ที่คุณกำหนดไม่แสดงผล; คุณต้องตั้งค่า
      `HasDataLabels` เป็น `true` เพื่อให้ป้ายกำกับ (และสไตล์ของมัน) ปรากฏ
    question: จะเกิดอะไรขึ้นหากฉันตั้งค่า `series.HasDataLabels = false` หลังจากกำหนดขนาดฟอนต์และสีแล้ว?
  - answer: ใช่ — แต่ละ `ChartSeries` มีอ็อบเจ็กต์ `DataLabels` ของตนเอง ดังนั้นชุดข้อมูลใด
      ๆ ที่เพิ่มหลังจากลูปแรกต้องตั้งค่า `HasDataLabels`, `ShowValue` และคุณสมบัติฟอนต์เช่นกัน
      ไม่ว่าจะโดยการวนลูปอีกครั้งหรือโดยการแยกสไตล์ออกเป็นเมธอดช่วยเหลือ
    question: ฉันต้องวนลูปผ่านชุดข้อมูลอีกครั้งหรือไม่ หากฉันเพิ่มชุดข้อมูลอื่นในภายหลังในโค้ด?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: ใช้ป้ายกำกับข้อมูลแบบสม่ำเสมอกับแผนภูมิ Word
og_description: ให้ทุกป้ายกำกับของแผนภูมิมีขนาดฟอนต์และสีเดียวกันอย่างรวดเร็วด้วย Aspose.Words for .NET
og_image_alt: คู่มือที่แสดงเอกสาร Word พร้อมแผนภูมิคอลัมน์ที่ป้ายกำกับข้อมูลทั้งหมดใช้ขนาดฟอนต์และสีเดียวกัน ซึ่งสร้างด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าป้ายกำกับข้อมูลแบบสม่ำเสมอในแผนภูมิคอลัมน์โดยใช้ Aspose.Words
บทแนะนำนี้แสดงวิธีสร้างเอกสาร Word, แทรกแผนภูมิคอลัมน์, และเพิ่มชุดข้อมูลแบบกำหนดเองด้วย Aspose.Words for .NET จากนั้นจะแสดงการกำหนดขนาดฟอนต์และสีของป้ายกำกับข้อมูลเริ่มต้นเพื่อให้ทุกชุดข้อมูลในแผนภูมิแสดงป้ายกำกับที่เหมือนกัน การใช้สไตล์เดียวช่วยให้ลักษณะภาพรวมของแผนภูมิมีความสอดคล้องกันทั่วทั้งแผนภูมิ

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: ทำไมฉันต้องเรียก `chart.Series.Clear()` ก่อนเพิ่มชุดข้อมูลของฉันเอง?**  
A: `InsertChart` สร้างแผนภูมิพร้อมชุดข้อมูลตัวอย่างเริ่มต้น; การลบออกจะทำให้ส่วนที่เป็นตัวแทนนั้นหายไป ดังนั้นแผนภูมิจะโชว์เฉพาะชุดข้อมูลที่คุณเพิ่ม (`Item Alpha` และ `Item Beta`)

**Q: ฉันจะเปลี่ยนสีของป้ายกำกับข้อมูลให้เป็นสีอื่นที่ไม่ใช่สีขาวได้อย่างไร?**  
A: แทนที่ `Color.White` ด้วยค่า `System.Drawing.Color` ใดก็ได้ เช่น `Color.Black` หรือ `Color.FromArgb(255, 30, 144, 255)`; สีใหม่จะถูกนำไปใช้ผ่าน `series.DataLabels.Font.Color` ภายในลูป

**Q: จะเกิดอะไรขึ้นหากฉันตั้งค่า `series.HasDataLabels = false` หลังจากกำหนดขนาดฟอนต์และสีแล้ว?**  
A: ป้ายกำกับข้อมูลจะถูกซ่อน ทำให้การตั้งค่าฟอนต์ที่คุณกำหนดไม่แสดงผล; คุณต้องตั้งค่า `HasDataLabels` เป็น `true` เพื่อให้ป้ายกำกับ (และสไตล์ของมัน) ปรากฏ

**Q: ฉันต้องวนลูปผ่านชุดข้อมูลอีกครั้งหรือไม่ หากฉันเพิ่มชุดข้อมูลอื่นในภายหลังในโค้ด?**  
A: ใช่ — แต่ละ `ChartSeries` มีอ็อบเจ็กต์ `DataLabels` ของตนเอง ดังนั้นชุดข้อมูลใด ๆ ที่เพิ่มหลังจากลูปแรกต้องตั้งค่า `HasDataLabels`, `ShowValue` และคุณสมบัติฟอนต์เช่นกัน ไม่ว่าจะโดยการวนลูปอีกครั้งหรือโดยการแยกสไตล์ออกเป็นเมธอดช่วยเหลือ

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}