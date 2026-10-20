---
title: แทรกแผนภูมิคอลัมน์ตัวอย่างในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 410
limit:
description: คู่มือขั้นตอนต่อขั้นตอนในการสร้างไฟล์ Word, แทรกแผนภูมิคอลัมน์เริ่มต้นด้วย DocumentBuilder.InsertChart, เข้าถึงอ็อบเจ็กต์แผนภูมิ, และบันทึกเป็น .docx
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: คู่มือขั้นตอนต่อขั้นตอนในการสร้างไฟล์ Word, แทรกแผนภูมิคอลัมน์เริ่มต้นด้วย
    DocumentBuilder.InsertChart, เข้าถึงอ็อบเจ็กต์แผนภูมิ, และบันทึกเป็น .docx
  headline: แทรกแผนภูมิคอลัมน์ตัวอย่างในเอกสาร Word ด้วย Aspose.Words for .NET
  type: TechArticle
- description: คู่มือขั้นตอนต่อขั้นตอนในการสร้างไฟล์ Word, แทรกแผนภูมิคอลัมน์เริ่มต้นด้วย
    DocumentBuilder.InsertChart, เข้าถึงอ็อบเจ็กต์แผนภูมิ, และบันทึกเป็น .docx
  name: แทรกแผนภูมิคอลัมน์ตัวอย่างในเอกสาร Word ด้วย Aspose.Words for .NET
  steps:
  - name: สร้างเอกสาร Word ว่างและ DocumentBuilder เพื่อแก้ไขเอกสาร
    text: สร้างเอกสาร Word ว่างและ DocumentBuilder เพื่อแก้ไขเอกสาร
  - name: แทรกแผนภูมิคอลัมน์ขนาด 432 × 252 จุดลงในเอกสาร
    text: แทรกแผนภูมิคอลัมน์ขนาด 432 × 252 จุดลงในเอกสาร
  - name: ดึงอ็อบเจ็กต์ Chart จาก Shape ที่แทรกไว้เพื่อปรับแต่งเพิ่มเติมหากต้องการ
    text: ดึงอ็อบเจ็กต์ Chart จาก Shape ที่แทรกไว้เพื่อปรับแต่งเพิ่มเติมหากต้องการ
  - name: บันทึกเอกสารที่ตอนนี้มีแผนภูมิคอลัมน์ที่แทรกไว้เป็นไฟล์ .docx
    text: บันทึกเอกสารที่ตอนนี้มีแผนภูมิคอลัมน์ที่แทรกไว้เป็นไฟล์ .docx
  type: HowTo
- questions:
  - answer: ขนาดถูกระบุเป็นจุด (1 point = 1/72 นิ้ว) ดังนั้น 432 pt ≈ 6 นิ้วและ 252
      pt ≈ 3.5 นิ้ว
    question: หน่วยใดที่ใช้สำหรับพารามิเตอร์ความกว้างและความสูง (432, 252) ใน InsertChart?
  - answer: ได้—หลังจากแทรกแล้วคุณจะมีอ็อบเจ็กต์ Chart ผ่าน `chartContainer.Chart`;
      คุณสามารถแก้ไข SeriesCollection, Categories, และ Values เพื่อแทนที่ข้อมูลตัวอย่างได้
    question: ฉันสามารถเปลี่ยนข้อมูลแผนภูมิหลังจากเรียก InsertChart ด้วยชุดข้อมูลเริ่มต้นได้หรือไม่?
  - answer: เพียงเปลี่ยน `ChartType.Column` เป็นค่า enum อื่นเช่น `ChartType.Line`
      ในการเรียก `InsertChart`
    question: สามารถแทรกประเภทแผนภูมิอื่น (เช่น แผนภูมิเส้น) ด้วยโค้ดเดียวกันได้หรือไม่?
  - answer: ไม่—`docBuilder.InsertChart` จะฝังแผนภูมิลงใน `Shape` โดยอัตโนมัติ; การเรียก
      `wordDoc.Save` จะบันทึกแผนภูมิพร้อมกับเอกสาร
    question: ฉันต้องเรียกเมธอดเพิ่มเติมใดเพื่อฝังแผนภูมิก่อนบันทึกเอกสารหรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: แทรกแผนภูมิคอลัมน์ตัวอย่างลงในเอกสาร Word
og_description: เพิ่มแผนภูมิคอลัมน์สำเร็จรูปลงในเอกสาร Word ด้วย Aspose.Words for .NET ภายในไม่กี่นาที
og_image_alt: ภาพหน้าจอแสดงเอกสาร Word ที่มีแผนภูมิคอลัมน์ตัวอย่างแทรกด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกแผนภูมิคอลัมน์ตัวอย่างในเอกสาร Word ด้วย Aspose.Words
บทแนะนำนี้พาคุณผ่านขั้นตอนการสร้างเอกสาร Word ใหม่และแทรกแผนภูมิคอลัมน์เริ่มต้นด้วย DocumentBuilder.InsertChart คุณจะได้เรียนรู้วิธีดึงอ็อบเจ็กต์ Chart ที่ฝังอยู่เพื่อการจัดการต่อไป และในที่สุดคำแนะนำจะแสดงวิธีบันทึกเอกสารเป็นไฟล์ .docx

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: หน่วยใดที่ใช้สำหรับพารามิเตอร์ความกว้างและความสูง (432, 252) ใน InsertChart?**  
A: ขนาดถูกระบุเป็นจุด (1 point = 1/72 นิ้ว) ดังนั้น 432 pt ≈ 6 นิ้วและ 252 pt ≈ 3.5 นิ้ว

**Q: ฉันสามารถเปลี่ยนข้อมูลแผนภูมิหลังจากเรียก InsertChart ด้วยชุดข้อมูลเริ่มต้นได้หรือไม่?**  
A: ได้—หลังจากแทรกแล้วคุณจะมีอ็อบเจ็กต์ Chart ผ่าน `chartContainer.Chart`; คุณสามารถแก้ไข SeriesCollection, Categories, และ Values เพื่อแทนที่ข้อมูลตัวอย่างได้

**Q: สามารถแทรกประเภทแผนภูมิอื่น (เช่น แผนภูมิเส้น) ด้วยโค้ดเดียวกันได้หรือไม่?**  
A: เพียงเปลี่ยน `ChartType.Column` เป็นค่า enum อื่นเช่น `ChartType.Line` ในการเรียก `InsertChart`

**Q: ฉันต้องเรียกเมธอดเพิ่มเติมใดเพื่อฝังแผนภูมิก่อนบันทึกเอกสารหรือไม่?**  
A: ไม่—`docBuilder.InsertChart` จะฝังแผนภูมิลงใน `Shape` โดยอัตโนมัติ; การเรียก `wordDoc.Save` จะบันทึกแผนภูมิพร้อมกับเอกสาร

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}