---
title: ตรวจสอบชุดข้อมูลและจุดข้อมูลของแผนภูมิในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 710
limit:
description: เรียนรู้การสร้างแผนภูมิคอลัมน์ใน Word, เติมข้อมูลด้วยชุดข้อมูล, ตรวจสอบจำนวนชุดและจุดข้อมูล, และบันทึกด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, chart validation, Word chart series, column chart .NET, validate chart data, Aspose.Words chart API]
url: /net/programming-with-charts/validate-chart-data/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้การสร้างแผนภูมิคอลัมน์ใน Word, เติมข้อมูลด้วยชุดข้อมูล, ตรวจสอบจำนวนชุดและจุดข้อมูล,
    และบันทึกด้วย Aspose.Words for .NET
  headline: ตรวจสอบชุดข้อมูลและจุดข้อมูลของแผนภูมิในเอกสาร Word ด้วย Aspose.Words
    for .NET
  type: TechArticle
- description: เรียนรู้การสร้างแผนภูมิคอลัมน์ใน Word, เติมข้อมูลด้วยชุดข้อมูล, ตรวจสอบจำนวนชุดและจุดข้อมูล,
    และบันทึกด้วย Aspose.Words for .NET
  name: ตรวจสอบชุดข้อมูลและจุดข้อมูลของแผนภูมิในเอกสาร Word ด้วย Aspose.Words for
    .NET
  steps:
  - name: กำหนดจำนวนชุดข้อมูลและจุดข้อมูลที่แผนภูมิต้องมี
    text: กำหนดจำนวนชุดข้อมูลและจุดข้อมูลที่แผนภูมิต้องมี
  - name: สร้าง Word Document ใหม่และ DocumentBuilder เพื่อเพิ่มเนื้อหาเข้าไป
    text: สร้าง Word Document ใหม่และ DocumentBuilder เพื่อเพิ่มเนื้อหาเข้าไป
  - name: แทรกแผนภูมิคอลัมน์ขนาด 400×300 ลงในเอกสารและรับอ็อบเจกต์ Chart ของมัน
    text: แทรกแผนภูมิคอลัมน์ขนาด 400×300 ลงในเอกสารและรับอ็อบเจกต์ Chart ของมัน
  - name: ลบชุดข้อมูลตัวอย่างที่ Aspose.Words เพิ่มโดยค่าเริ่มต้น
    text: ลบชุดข้อมูลตัวอย่างที่ Aspose.Words เพิ่มโดยค่าเริ่มต้น
  - name: กำหนดป้ายแกน X และเพิ่มสองชุดข้อมูล (Alpha และ Beta) แต่ละชุดมีสามจุดเข้าไปในแผนภูมิ
    text: กำหนดป้ายแกน X และเพิ่มสองชุดข้อมูล (Alpha และ Beta) แต่ละชุดมีสามจุดเข้าไปในแผนภูมิ
  - name: ตรวจสอบว่าแผนภูมิมีจำนวนชุดข้อมูลตรงตามที่ต้องการและโยนข้อยกเว้นหากไม่เป็นเช่นนั้น
    text: ตรวจสอบว่าแผนภูมิมีจำนวนชุดข้อมูลตรงตามที่ต้องการและโยนข้อยกเว้นหากไม่เป็นเช่นนั้น
  - name: วนผ่านแต่ละชุดข้อมูลและตรวจสอบว่ามีจำนวนจุดข้อมูลตามที่คาดหวัง หากไม่ตรงกันให้ยกข้อยกเว้น
    text: วนผ่านแต่ละชุดข้อมูลและตรวจสอบว่ามีจำนวนจุดข้อมูลตามที่คาดหวัง หากไม่ตรงกันให้ยกข้อยกเว้น
  - name: บันทึกเอกสารที่ตรวจสอบแล้วเป็นไฟล์ .docx
    text: บันทึกเอกสารที่ตรวจสอบแล้วเป็นไฟล์ .docx
  type: HowTo
- questions:
  - answer: แผนภูมิจะคงชุดข้อมูลตัวอย่างที่ Aspose.Words แทรกโดยอัตโนมัติ ดังนั้น
      `chartObj.Series.Count` จะมากกว่าค่า `requiredSeriesCount` และการตรวจสอบจะโยน
      `InvalidOperationException`
    question: จะเกิดอะไรขึ้นหากฉันลืมเรียก `chartObj.Series.Clear()` ก่อนเพิ่มชุดข้อมูลของฉัน?
  - answer: ได้, การตรวจสอบเพียงตรวจสอบ `chartObj.Series.Count` และ `ChartSeries.DataPoints.Count`
      ของแต่ละชุด; การเปลี่ยน `ChartType` ใน `InsertChart` จะไม่กระทบต่อการตรวจสอบเหล่านั้น
    question: ฉันสามารถใช้ประเภทแผนภูมิอื่น (เช่น `ChartType.Line`) และยังคงตรรกะการตรวจสอบเหมือนเดิมได้หรือไม่?
  - answer: เมื่อคุณเรียก `chartObj.Series.Add` ความยาวของอาร์เรย์ป้ายแกน X ต้องตรงกับความยาวของอาร์เรย์ค่าต่าง
      ๆ; หากไม่ตรง Aspose.Words จะโยน `ArgumentException` ก่อนการตรวจสอบจะทำงาน
    question: ทำไมการเพิ่มชุดข้อมูลบางครั้งถึงทำให้เกิดข้อยกเว้นเกี่ยวกับความยาวข้อมูลที่ไม่ตรงกัน?
  - answer: แทนที่ค่าคงที่ `requiredPointsPerSeries` ด้วยการตรวจสอบต่อชุด (เช่น เก็บจำนวนที่คาดหวังในดิกชันนารี)
      และเปรียบเทียบ `seriesItem.DataPoints.Count` กับค่าที่คาดหวังที่สอดคล้องกันภายในลูป
    question: ฉันจะตรวจสอบแผนภูมิที่มีจำนวนจุดข้อมูลต่อชุดแตกต่างกันได้อย่างไร?
  - answer: เฉพาะเมื่อชุดข้อมูลที่มีอยู่ทำให้ `chartObj.Series.Count` เกินค่า `requiredSeriesCount`
      ที่คาดไว้; หากไม่เช่นนั้นคุณสามารถเก็บไว้และปรับค่า `requiredSeriesCount` ให้ตรงกับจำนวนชุดข้อมูลจริงที่ต้องการตรวจสอบ
    question: หากฉันโหลดเอกสารที่มีแผนภูมิพร้อมชุดข้อมูลที่เติมไว้ล่วงหน้า ฉันยังต้องลบชุดข้อมูลเหล่านั้นหรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/validate-chart-data/og-image.png
og_title: ตรวจสอบชุดข้อมูลและจุดข้อมูลของแผนภูมิใน Word
og_description: คำแนะนำแบบขั้นตอนต่อขั้นตอนในการเพิ่มแผนภูมิคอลัมน์, ตรวจสอบชุดข้อมูลและจุดของมัน, และบันทึกไฟล์ Word ด้วย Aspose.Words
og_image_alt: คู่มือแสดงวิธีตรวจสอบชุดข้อมูลและจุดข้อมูลของแผนภูมิในเอกสาร Word ด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ตรวจสอบชุดข้อมูลและจุดข้อมูลของแผนภูมิในเอกสาร Word ด้วย Aspose.Words
ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีสร้างเอกสาร Word ที่มีแผนภูมิคอลัมน์, เพิ่มชุดข้อมูลที่ต้องการโดยโปรแกรม, และตรวจสอบว่าแผนภูมิมีจำนวนชุดข้อมูลและจุดข้อมูลตามที่คาดหวังก่อนบันทึก ซึ่งจะทำให้แผนภูมิที่สร้างขึ้นสมบูรณ์และแม่นยำ

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/validate-chart-data" >}}


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

**Q: จะเกิดอะไรขึ้นหากฉันลืมเรียก `chartObj.Series.Clear()` ก่อนเพิ่มชุดข้อมูลของฉัน?**  
A: แผนภูมิจะคงชุดข้อมูลตัวอย่างที่ Aspose.Words แทรกโดยอัตโนมัติ ดังนั้น `chartObj.Series.Count` จะมากกว่าค่า `requiredSeriesCount` และการตรวจสอบจะโยน `InvalidOperationException`

**Q: ฉันสามารถใช้ประเภทแผนภูมิอื่น (เช่น `ChartType.Line`) และยังคงตรรกะการตรวจสอบเหมือนเดิมได้หรือไม่?**  
A: ได้, การตรวจสอบเพียงตรวจสอบ `chartObj.Series.Count` และ `ChartSeries.DataPoints.Count` ของแต่ละชุด; การเปลี่ยน `ChartType` ใน `InsertChart` จะไม่กระทบต่อการตรวจสอบเหล่านั้น

**Q: ทำไมการเพิ่มชุดข้อมูลบางครั้งถึงทำให้เกิดข้อยกเว้นเกี่ยวกับความยาวข้อมูลที่ไม่ตรงกัน?**  
A: เมื่อคุณเรียก `chartObj.Series.Add` ความยาวของอาร์เรย์ป้ายแกน X ต้องตรงกับความยาวของอาร์เรย์ค่าต่าง ๆ; หากไม่ตรง Aspose.Words จะโยน `ArgumentException` ก่อนการตรวจสอบจะทำงาน

**Q: ฉันจะตรวจสอบแผนภูมิที่มีจำนวนจุดข้อมูลต่อชุดแตกต่างกันได้อย่างไร?**  
A: แทนที่ค่าคงที่ `requiredPointsPerSeries` ด้วยการตรวจสอบต่อชุด (เช่น เก็บจำนวนที่คาดหวังในดิกชันนารี) และเปรียบเทียบ `seriesItem.DataPoints.Count` กับค่าที่คาดหวังที่สอดคล้องกันภายในลูป

**Q: หากฉันโหลดเอกสารที่มีแผนภูมิพร้อมชุดข้อมูลที่เติมไว้ล่วงหน้า ฉันยังต้องลบชุดข้อมูลเหล่านั้นหรือไม่?**  
A: เฉพาะเมื่อชุดข้อมูลที่มีอยู่ทำให้ `chartObj.Series.Count` เกินค่า `requiredSeriesCount` ที่คาดไว้; หากไม่เช่นนั้นคุณสามารถเก็บไว้และปรับค่า `requiredSeriesCount` ให้ตรงกับจำนวนชุดข้อมูลจริงที่ต้องการตรวจสอบ

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}