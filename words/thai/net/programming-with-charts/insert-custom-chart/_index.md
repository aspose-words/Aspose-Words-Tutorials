---
title: แทรก Custom Column Chart ใน Word Document ด้วย Aspose.Words for .NET
weight: 310
limit:
description: สร้างไฟล์ Word, แทรก column chart, แทนที่ข้อมูลด้วยอาเรย์ที่กำหนดเอง, เพิ่ม title, และบันทึก—ทั้งหมดด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: สร้างไฟล์ Word, แทรก column chart, แทนที่ข้อมูลด้วยอาเรย์ที่กำหนดเอง,
    เพิ่ม title, และบันทึก—ทั้งหมดด้วย Aspose.Words for .NET
  headline: แทรก Custom Column Chart ใน Word Document ด้วย Aspose.Words for .NET
  type: TechArticle
- description: สร้างไฟล์ Word, แทรก column chart, แทนที่ข้อมูลด้วยอาเรย์ที่กำหนดเอง,
    เพิ่ม title, และบันทึก—ทั้งหมดด้วย Aspose.Words for .NET
  name: แทรก Custom Column Chart ใน Word Document ด้วย Aspose.Words for .NET
  steps:
  - name: สร้าง Document ใหม่และ DocumentBuilder ที่เชื่อมต่อกับมัน
    text: สร้าง Document ใหม่และ DocumentBuilder ที่เชื่อมต่อกับมัน
  - name: แทรก column chart ขนาด 432x252 points ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน
    text: แทรก column chart ขนาด 432x252 points ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน
  - name: ลบ series ตัวอย่างที่สร้างโดยอัตโนมัติออกจาก chart
    text: ลบ series ตัวอย่างที่สร้างโดยอัตโนมัติออกจาก chart
  - name: กำหนดป้ายกำกับ category ของแกน X และรายการ legend สำหรับแต่ละ series
    text: กำหนดป้ายกำกับ category ของแกน X และรายการ legend สำหรับแต่ละ series
  - name: สร้าง two‑dimensional array ที่แต่ละแถวเก็บค่าของหนึ่ง series
    text: สร้าง two‑dimensional array ที่แต่ละแถวเก็บค่าของหนึ่ง series
  - name: วนซ้ำแต่ละ series, ดึงค่าจากแถวของ matrix, และเพิ่ม series ลงใน chart พร้อมกับ
      legend entry ที่สอดคล้องและป้ายกำกับแกน X
    text: วนซ้ำแต่ละ series, ดึงค่าจากแถวของ matrix, และเพิ่ม series ลงใน chart พร้อมกับ
      legend entry ที่สอดคล้องและป้ายกำกับแกน X
  - name: ตั้งค่าข้อความ title ของ chart เป็น 'Half‑Yearly Revenue' และทำให้แสดงผล
    text: ตั้งค่าข้อความ title ของ chart เป็น 'Half‑Yearly Revenue' และทำให้แสดงผล
  - name: บันทึกเอกสารที่มี chart ที่กำหนดเองเป็นไฟล์ .docx
    text: บันทึกเอกสารที่มี chart ที่กำหนดเองเป็นไฟล์ .docx
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` คาดว่าความยาวของอาเรย์ค่าต้องเท่ากับจำนวนป้ายกำกับแกน
      X, และคุณต้องเพิ่ม series หนึ่งรายการต่อ legend entry; หากไม่ตรงกันจะทำให้เกิด
      `ArgumentException` ขณะรันไทม์'
    question: ถ้าแถวหรือคอลัมน์ใน `dataMatrix` ไม่ตรงกับความยาวของ `legendEntries`
      หรือ `xLabels` จะเกิดอะไรขึ้น?
  - answer: ได้—ให้แทนที่ `ChartType.Column` ใน `docBuilder.InsertChart` ด้วย `ChartType`
      ใดก็ได้ (เช่น `ChartType.Line`) แล้วการเรียก `Series.Add` ต่อไปจะเติมข้อมูลให้
      chart ใหม่ในลักษณะเดียวกัน
    question: ฉันสามารถใช้ประเภท chart อื่น เช่น line chart, กับตรรกะการเติมข้อมูลเดียวกันได้หรือไม่?
  - answer: ปรับคุณสมบัติ `Width` และ `Height` ของ `Shape` ที่ `InsertChart` คืนค่า
      (เช่น `chartContainer.Width = 500; chartContainer.Height = 300;`).
    question: ฉันจะเปลี่ยนขนาดของ chart หลังจากที่แทรกแล้วได้อย่างไร?
  - answer: ตั้งค่า `chartObj.Series[i].HasDataLabel = true;` สำหรับแต่ละ series หลังจากเพิ่ม,
      หรือวนลูปผ่าน `chartObj.Series` แล้วเปิด `HasDataLabel` เพื่อแสดงค่าบน chart
    question: มีวิธีเร็ว ๆ ที่จะแสดง data label บนแต่ละคอลัมน์ของ chart หรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: เพิ่ม Custom Column Chart ไปยัง Word Document
og_description: สลับข้อมูลเริ่มต้นของ chart ด้วยอาเรย์ของคุณและตั้งค่า title ภายในไม่กี่วินาที
og_image_alt: ภาพหน้าจอแสดง Word Document ที่มี custom column chart สร้างด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรก Custom Column Chart ใน Word Document ด้วย Aspose.Words
บทแนะนำนี้จะพาคุณผ่านขั้นตอนการสร้างเอกสาร Word, แทรก column chart, ล้างข้อมูลเริ่มต้น, และเติมค่าแบบกำหนดเองจาก two‑dimensional array—โดยจับคู่แต่ละแถวกับ series และแต่ละคอลัมน์กับ category. คุณจะได้เห็นวิธีเพิ่ม title ของ chart ก่อนบันทึกไฟล์. ทำตามขั้นตอนเพื่อสร้าง chart ที่ปรับแต่งได้เต็มรูปแบบโดยตรงในไฟล์ Word ของคุณ

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: ถ้าแถวหรือคอลัมน์ใน `dataMatrix` ไม่ตรงกับความยาวของ `legendEntries` หรือ `xLabels` จะเกิดอะไรขึ้น?**  
A: `Chart.Series.Add` คาดว่าความยาวของอาเรย์ค่าต้องเท่ากับจำนวนป้ายกำกับแกน X, และคุณต้องเพิ่ม series หนึ่งรายการต่อ legend entry; หากไม่ตรงกันจะทำให้เกิด `ArgumentException` ขณะรันไทม์

**Q: ฉันสามารถใช้ประเภท chart อื่น เช่น line chart, กับตรรกะการเติมข้อมูลเดียวกันได้หรือไม่?**  
A: ได้—ให้แทนที่ `ChartType.Column` ใน `docBuilder.InsertChart` ด้วย `ChartType` ใดก็ได้ (เช่น `ChartType.Line`) แล้วการเรียก `Series.Add` ต่อไปจะเติมข้อมูลให้ chart ใหม่ในลักษณะเดียวกัน

**Q: ฉันจะเปลี่ยนขนาดของ chart หลังจากที่แทรกแล้วได้อย่างไร?**  
A: ปรับคุณสมบัติ `Width` และ `Height` ของ `Shape` ที่ `InsertChart` คืนค่า (เช่น `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: มีวิธีเร็ว ๆ ที่จะแสดง data label บนแต่ละคอลัมน์ของ chart หรือไม่?**  
A: ตั้งค่า `chartObj.Series[i].HasDataLabel = true;` สำหรับแต่ละ series หลังจากเพิ่ม, หรือวนลูปผ่าน `chartObj.Series` แล้วเปิด `HasDataLabel` เพื่อแสดงค่าบน chart

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}