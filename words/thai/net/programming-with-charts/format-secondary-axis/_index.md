---
title: จัดรูปแบบแกน Y รองเป็นสกุลเงินในแผนภูมิ Word ด้วย Aspose.Words for .NET
weight: 710
limit:
description: เรียนรู้วิธีเพิ่มและจัดรูปแบบแกน Y รองเป็นสกุลเงินในแผนภูมิเส้น Word ด้วย Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้วิธีเพิ่มและจัดรูปแบบแกน Y รองเป็นสกุลเงินในแผนภูมิเส้น Word
    ด้วย Aspose.Words for .NET.
  headline: จัดรูปแบบแกน Y รองเป็นสกุลเงินในแผนภูมิ Word ด้วย Aspose.Words for .NET
  type: TechArticle
- description: เรียนรู้วิธีเพิ่มและจัดรูปแบบแกน Y รองเป็นสกุลเงินในแผนภูมิเส้น Word
    ด้วย Aspose.Words for .NET.
  name: จัดรูปแบบแกน Y รองเป็นสกุลเงินในแผนภูมิ Word ด้วย Aspose.Words for .NET
  steps:
  - name: สร้างเอกสาร Word ว่างใหม่และ DocumentBuilder เพื่อแก้ไขมัน.
    text: สร้างเอกสาร Word ว่างใหม่และ DocumentBuilder เพื่อแก้ไขมัน.
  - name: แทรกแผนภูมิเส้นขนาด 450×250 จุดลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน.
    text: แทรกแผนภูมิเส้นขนาด 450×250 จุดลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน.
  - name: ลบชุดข้อมูลตัวแทนค่าเริ่มต้นที่ Aspose เพิ่มให้กับแผนภูมิใหม่.
    text: ลบชุดข้อมูลตัวแทนค่าเริ่มต้นที่ Aspose เพิ่มให้กับแผนภูมิใหม่.
  - name: กำหนดป้ายกำกับไตรมาสและเพิ่มชุดข้อมูลหลักพร้อมค่าตัวอย่างลงในแผนภูมิ.
    text: กำหนดป้ายกำกับไตรมาสและเพิ่มชุดข้อมูลหลักพร้อมค่าตัวอย่างลงในแผนภูมิ.
  - name: สร้างกลุ่มชุดข้อมูลรองประเภท Line และกำหนดให้กับกลุ่มแกนรอง.
    text: สร้างกลุ่มชุดข้อมูลรองประเภท Line และกำหนดให้กับกลุ่มแกนรอง.
  - name: ซ่อนแกน X รองเพื่อให้เห็นเฉพาะแกน Y รอง.
    text: ซ่อนแกน X รองเพื่อให้เห็นเฉพาะแกน Y รอง.
  - name: แสดงชื่อแกน Y รองและตั้งข้อความเป็น \"Sales (USD)\".
    text: แสดงชื่อแกน Y รองและตั้งข้อความเป็น \"Sales (USD)\".
  - name: ตั้งรูปแบบตัวเลขของแกน Y รองเป็นรูปแบบสกุลเงินที่มีสองตำแหน่งทศนิยมและยกเลิกการเชื่อมโยงกับรูปแบบแหล่งข้อมูล.
    text: ตั้งรูปแบบตัวเลขของแกน Y รองเป็นรูปแบบสกุลเงินที่มีสองตำแหน่งทศนิยมและยกเลิกการเชื่อมโยงกับรูปแบบแหล่งข้อมูล.
  - name: เพิ่มชุดข้อมูลเสริมไปยังกลุ่มรอง เพื่อให้ข้อมูลถูกพล็อตกับแกน Y รอง.
    text: เพิ่มชุดข้อมูลเสริมไปยังกลุ่มรอง เพื่อให้ข้อมูลถูกพล็อตกับแกน Y รอง.
  - name: บันทึกเอกสารที่เสร็จแล้วเป็นไฟล์ชื่อ ProfitChart.docx ในไดเรกทอรีปัจจุบัน.
    text: บันทึกเอกสารที่เสร็จแล้วเป็นไฟล์ชื่อ ProfitChart.docx ในไดเรกทอรีปัจจุบัน.
  type: HowTo
- questions:
  - answer: แผนภูมิจะคงชุดข้อมูลตัวแทนค่าเริ่มต้นที่ Aspose.Words แทรกไว้ ดังนั้น
      \"Main Series\" ที่คุณกำหนดเองจะปรากฏพร้อมกับจุดข้อมูลที่ไม่ต้องการ.
    question: จะเกิดอะไรขึ้นหากฉันละเว้นการเรียก `lineChart.Series.Clear()`?
  - answer: ตั้งค่า `secondarySeriesGroup.AxisX.Hidden = false;` (หรือเพียงละเว้นบรรทัดที่ตั้งค่าเป็น
      `true`).
    question: ฉันจะทำให้แกน X รองแสดงแทนการซ่อนได้อย่างไร?
  - answer: ได้ – เปลี่ยนสตริงรูปแบบ เช่น `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"\\\"€\\\"#,##0.00\";` สำหรับยูโรหรือปรับรูปแบบให้เหมาะกับท้องถิ่นของคุณ.
    question: ฉันสามารถใช้สัญลักษณ์สกุลเงินหรือรูปแบบอื่นสำหรับแกน Y รองได้หรือไม่?
  - answer: เมื่อ `IsLinkedToSource` เป็น true แกนจะสืบทอดรูปแบบตัวเลขจากแหล่งข้อมูลพื้นฐาน
      ซึ่งจะทับรูปแบบ `FormatCode` ที่กำหนดเอง; การตั้งค่าเป็น false จะบังคับให้แผนภูมิใช้รูปแบบที่คุณระบุ.
    question: ทำไมต้องตั้งค่า `IsLinkedToSource = false` เมื่อใช้รูปแบบตัวเลขแบบกำหนดเอง?
  - answer: ได้, กำหนด `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (หรือ `Right` สำหรับค่าเริ่มต้น) เพื่อควบคุมว่าจะแสดงแกนที่ด้านใด.
    question: สามารถย้ายแกน Y รองไปด้านซ้ายของแผนภูมิได้หรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: จัดรูปแบบแกนรองของแผนภูมิเป็นสกุลเงิน
og_description: เรียนรู้วิธีเพิ่มแกน Y รองในแผนภูมิเส้น Word และทำให้มีสไตล์เป็นสกุลเงินด้วยสองตำแหน่งทศนิยม.
og_image_alt: ภาพหน้าจอแสดงแผนภูมิเส้น Word ที่มีแกน Y รองจัดรูปแบบเป็นสกุลเงินโดยใช้ Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# จัดรูปแบบแกน Y รองเป็นสกุลเงินในแผนภูมิ Word ด้วย Aspose.Words
ในบทแนะนำนี้คุณจะได้เห็นวิธีสร้างเอกสาร Word, แทรกแผนภูมิเส้น, เพิ่มแกน Y รอง, จัดรูปแบบแกนนั้นเป็นสกุลเงินด้วยสองตำแหน่งทศนิยม, และผูกชุดข้อมูลรองกับมันโดยใช้ Aspose.Words for .NET การจัดรูปแบบแกนรองเป็นสกุลเงินช่วยให้คุณนำเสนอข้อมูลการเงินอย่างชัดเจนพร้อมกับชุดข้อมูลหลัก ทำตามโค้ดขั้นตอนต่อขั้นตอนเพื่อดูแผนภูมิที่แสดงผลโดยตรงในเอกสารที่สร้างขึ้น.

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

**Q: จะเกิดอะไรขึ้นหากฉันละเว้นการเรียก `lineChart.Series.Clear()`?**  
A: แผนภูมิจะคงชุดข้อมูลตัวแทนค่าเริ่มต้นที่ Aspose.Words แทรกไว้ ดังนั้น \"Main Series\" ที่คุณกำหนดเองจะปรากฏพร้อมกับจุดข้อมูลที่ไม่ต้องการ.

**Q: ฉันจะทำให้แกน X รองแสดงแทนการซ่อนได้อย่างไร?**  
A: ตั้งค่า `secondarySeriesGroup.AxisX.Hidden = false;` (หรือเพียงละเว้นบรรทัดที่ตั้งค่าเป็น `true`).

**Q: ฉันสามารถใช้สัญลักษณ์สกุลเงินหรือรูปแบบอื่นสำหรับแกน Y รองได้หรือไม่?**  
A: ได้ – เปลี่ยนสตริงรูปแบบ เช่น `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";` สำหรับยูโรหรือปรับรูปแบบให้เหมาะกับท้องถิ่นของคุณ.

**Q: ทำไมต้องตั้งค่า `IsLinkedToSource = false` เมื่อใช้รูปแบบตัวเลขแบบกำหนดเอง?**  
A: เมื่อ `IsLinkedToSource` เป็น true แกนจะสืบทอดรูปแบบตัวเลขจากแหล่งข้อมูลพื้นฐาน ซึ่งจะทับรูปแบบ `FormatCode` ที่กำหนดเอง; การตั้งค่าเป็น false จะบังคับให้แผนภูมิใช้รูปแบบที่คุณระบุ.

**Q: สามารถย้ายแกน Y รองไปด้านซ้ายของแผนภูมิได้หรือไม่?**  
A: ได้, กำหนด `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (หรือ `Right` สำหรับค่าเริ่มต้น) เพื่อควบคุมว่าจะแสดงแกนที่ด้านใด.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}