---
title: จัดรูปแบบแกน X รองและตั้งหน่วยการแสดงผลเป็นพันในแผนภูมิเส้นของ Word โดยใช้ Aspose.Words for .NET
weight: 710
limit:
description: สร้างแผนภูมิเส้น Word, เพิ่มแกน X รอง, ตั้งหน่วยการแสดงผลเป็นพัน, และใช้รูปแบบตัวเลขแบบกำหนดเองด้วย Aspose.Words for .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: สร้างแผนภูมิเส้น Word, เพิ่มแกน X รอง, ตั้งหน่วยการแสดงผลเป็นพัน, และใช้รูปแบบตัวเลขแบบกำหนดเองด้วย
    Aspose.Words for .NET.
  headline: จัดรูปแบบแกน X รองและตั้งหน่วยการแสดงผลเป็นพันในแผนภูมิเส้นของ Word โดยใช้
    Aspose.Words for .NET
  type: TechArticle
- description: สร้างแผนภูมิเส้น Word, เพิ่มแกน X รอง, ตั้งหน่วยการแสดงผลเป็นพัน, และใช้รูปแบบตัวเลขแบบกำหนดเองด้วย
    Aspose.Words for .NET.
  name: จัดรูปแบบแกน X รองและตั้งหน่วยการแสดงผลเป็นพันในแผนภูมิเส้นของ Word โดยใช้
    Aspose.Words for .NET
  steps:
  - name: สร้าง Document ใหม่และ DocumentBuilder เพื่อเริ่มสร้างไฟล์ Word.
    text: สร้าง Document ใหม่และ DocumentBuilder เพื่อเริ่มสร้างไฟล์ Word.
  - name: แทรกแผนภูมิเส้นขนาด 500×300 ลงในเอกสารและรับอ็อบเจกต์ Chart.
    text: แทรกแผนภูมิเส้นขนาด 500×300 ลงในเอกสารและรับอ็อบเจกต์ Chart.
  - name: ลบซีรีส์ตัวอย่างเริ่มต้นที่ Aspose.Words เพิ่มโดยอัตโนมัติ.
    text: ลบซีรีส์ตัวอย่างเริ่มต้นที่ Aspose.Words เพิ่มโดยอัตโนมัติ.
  - name: กำหนดอาร์เรย์ของป้ายหมวดหมู่ที่จะใช้สำหรับแกน X.
    text: กำหนดอาร์เรย์ของป้ายหมวดหมู่ที่จะใช้สำหรับแกน X.
  - name: เพิ่มซีรีส์ข้อมูลหลักที่ชื่อ "Main Data" โดยใช้ป้ายและค่า.
    text: เพิ่มซีรีส์ข้อมูลหลักที่ชื่อ "Main Data" โดยใช้ป้ายและค่า.
  - name: สร้างกลุ่มซีรีส์รองประเภท Line และกำหนดให้กับกลุ่มแกนรอง.
    text: สร้างกลุ่มซีรีส์รองประเภท Line และกำหนดให้กับกลุ่มแกนรอง.
  - name: ตั้งหน่วยการแสดงผลของแกน X รองเป็นพันเพื่อให้ค่าถูกแสดงเป็น K.
    text: ตั้งหน่วยการแสดงผลของแกน X รองเป็นพันเพื่อให้ค่าถูกแสดงเป็น K.
  - name: ใช้รูปแบบตัวเลขแบบกำหนดเอง "#,##0.0" กับป้ายติ๊กของแกน X รอง.
    text: ใช้รูปแบบตัวเลขแบบกำหนดเอง "#,##0.0" กับป้ายติ๊กของแกน X รอง.
  - name: หากต้องการสามารถเพิ่มซีรีส์ข้อมูลช่วยเหลือไปยังกลุ่มรองได้.
    text: หากต้องการสามารถเพิ่มซีรีส์ข้อมูลช่วยเหลือไปยังกลุ่มรองได้.
  - name: บันทึกเอกสารเป็นไฟล์ .docx.
    text: บันทึกเอกสารเป็นไฟล์ .docx.
  type: HowTo
- questions:
  - answer: ไม่ – การตั้งค่า `AxisX` เป็นของ `ChartSeriesGroup` ดังนั้นคุณสามารถตั้งค่า
      `secondaryGroup.AxisX.DisplayUnit.Unit` และ `secondaryGroup.AxisX.NumberFormat.FormatCode`
      ก่อนหรือหลังการเพิ่มซีรีส์; การกำหนดค่าจะถูกนำไปใช้กับแกนของกลุ่มไม่ว่ากรณีใด.
    question: ฉันต้องเพิ่มซีรีส์รองก่อนตั้งหน่วยการแสดงผลและรูปแบบตัวเลขบนแกน X รองหรือไม่?
  - answer: ได้ – กำหนดค่าใด ๆ ของ `AxisBuiltInUnit` เช่น `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` เพื่อแสดงค่าของแกนเป็นล้านแทนพัน.
    question: ฉันสามารถใช้หน่วยในตัวอื่น เช่น ล้าน, สำหรับแกน X รองได้หรือไม่?
  - answer: ไม่ – รหัสรูปแบบจะถูกนำไปใช้เฉพาะแกนที่คุณแก้ไข (`secondaryGroup.AxisX.NumberFormat.FormatCode`)
      ดังนั้นแกน X หลักจะคงรูปแบบเริ่มต้นไว้.
    question: รูปแบบกำหนดเอง `"#,##0.0"` จะส่งผลต่อป้ายแกน X หลักหรือไม่?
  - answer: แผนภูมิจะมีซีรีส์ตัวอย่างเริ่มต้นรวมกับซีรีส์ที่คุณเพิ่ม ซึ่งอาจทำให้มีเส้นเพิ่มและหมวดหมู่ไม่ตรงกัน;
      การล้างคอลเลกชันจะทำให้มีเฉพาะข้อมูลที่คุณต้องการแสดงเท่านั้น.
    question: จะเกิดอะไรขึ้นหากฉันลืมล้างซีรีส์ตัวอย่างด้วย `lineChart.Series.Clear();`
      ?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: จัดรูปแบบแกน X รองและตั้งหน่วยเป็นพัน
og_description: เพิ่มแกน X รองให้กับแผนภูมิเส้น Word และจัดรูปแบบป้ายของมันเป็นพันด้วยรูปแบบกำหนดเอง.
og_image_alt: คู่มือแสดงวิธีเพิ่มแกน X รองให้กับแผนภูมิเส้น Word และจัดรูปแบบป้ายของมันให้แสดงหน่วยเป็นพันโดยใช้ Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# จัดรูปแบบแกน X รองและตั้งหน่วยการแสดงผลเป็นพันในแผนภูมิเส้นของ Word โดยใช้ Aspose.Words
บทแนะนำนี้จะพาคุณผ่านขั้นตอนการสร้างเอกสาร Word ที่มีแผนภูมิเส้น, การเพิ่มแกน X รอง, และการกำหนดค่าแกนนั้นให้แสดงค่าเป็นพัน คุณยังจะได้เรียนรู้วิธีใช้รูปแบบตัวเลขแบบกำหนดเองกับป้ายแกนรอง เพื่อให้คุณควบคุมการแสดงข้อมูลได้อย่างแม่นยำ ปฏิบัติตามขั้นตอนเพื่อเพิ่มความอ่านง่ายของแผนภูมิหลายแกนในรายงาน Word ของคุณ.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: ฉันต้องเพิ่มซีรีส์รองก่อนตั้งหน่วยการแสดงผลและรูปแบบตัวเลขบนแกน X รองหรือไม่?**  
A: ไม่ – การตั้งค่า `AxisX` เป็นของ `ChartSeriesGroup` ดังนั้นคุณสามารถตั้งค่า `secondaryGroup.AxisX.DisplayUnit.Unit` และ `secondaryGroup.AxisX.NumberFormat.FormatCode` ก่อนหรือหลังการเพิ่มซีรีส์; การกำหนดค่าจะถูกนำไปใช้กับแกนของกลุ่มไม่ว่ากรณีใด.

**Q: ฉันสามารถใช้หน่วยในตัวอื่น เช่น ล้าน, สำหรับแกน X รองได้หรือไม่?**  
A: ได้ – กำหนดค่าใด ๆ ของ `AxisBuiltInUnit` เช่น `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` เพื่อแสดงค่าของแกนเป็นล้านแทนพัน.

**Q: รูปแบบกำหนดเอง `"#,##0.0"` จะส่งผลต่อป้ายแกน X หลักหรือไม่?**  
A: ไม่ – รหัสรูปแบบจะถูกนำไปใช้เฉพาะแกนที่คุณแก้ไข (`secondaryGroup.AxisX.NumberFormat.FormatCode`) ดังนั้นแกน X หลักจะคงรูปแบบเริ่มต้นไว้.

**Q: จะเกิดอะไรขึ้นหากฉันลืมล้างซีรีส์ตัวอย่างด้วย `lineChart.Series.Clear();` ?**  
A: แผนภูมิจะมีซีรีส์ตัวอย่างเริ่มต้นรวมกับซีรีส์ที่คุณเพิ่ม ซึ่งอาจทำให้มีเส้นเพิ่มและหมวดหมู่ไม่ตรงกัน; การล้างคอลเลกชันจะทำให้มีเฉพาะข้อมูลที่คุณต้องการแสดงเท่านั้น.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}