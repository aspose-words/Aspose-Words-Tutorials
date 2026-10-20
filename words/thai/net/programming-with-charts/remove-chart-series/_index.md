---
title: ลบ Chart Series จาก Word Document ด้วย Aspose.Words for .NET
weight: 510
limit:
description: เรียนรู้วิธีลบ series ของข้อมูลที่ระบุจาก column chart ใน Word document ด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้วิธีลบ series ของข้อมูลที่ระบุจาก column chart ใน Word document
    ด้วย Aspose.Words for .NET
  headline: ลบ Chart Series จาก Word Document ด้วย Aspose.Words for .NET
  type: TechArticle
- description: เรียนรู้วิธีลบ series ของข้อมูลที่ระบุจาก column chart ใน Word document
    ด้วย Aspose.Words for .NET
  name: ลบ Chart Series จาก Word Document ด้วย Aspose.Words for .NET
  steps:
  - name: สร้าง Word Document ใหม่และ DocumentBuilder ที่เชื่อมต่อกับมัน
    text: สร้าง Word Document ใหม่และ DocumentBuilder ที่เชื่อมต่อกับมัน
  - name: แทรก column chart ขนาด 432×252 จุดและรับอ็อบเจ็กต์ Chart เพื่อการจัดการต่อไป
    text: แทรก column chart ขนาด 432×252 จุดและรับอ็อบเจ็กต์ Chart เพื่อการจัดการต่อไป
  - name: กำหนดดัชนีเริ่มจากศูนย์ของ series ที่ต้องการลบ (series ที่สอง)
    text: กำหนดดัชนีเริ่มจากศูนย์ของ series ที่ต้องการลบ (series ที่สอง)
  - name: หากดัชนีถูกต้อง ให้เรียก RemoveAt บนคอลเลกชัน Series ของ chart เพื่อทำการลบ
      series นั้น
    text: หากดัชนีถูกต้อง ให้เรียก RemoveAt บนคอลเลกชัน Series ของ chart เพื่อทำการลบ
      series นั้น
  - name: บันทึกเอกสารที่อัปเดตเป็นไฟล์ .docx
    text: บันทึกเอกสารที่อัปเดตเป็นไฟล์ .docx
  type: HowTo
- questions:
  - answer: การตรวจสอบ `if` (`targetSeriesIdx < columnChart.Series.Count`) จะล้มเหลว
      ดังนั้น `RemoveAt` จะไม่ถูกเรียกและ chart จะคงเดิมไม่มีการเปลี่ยนแปลง
    question: จะเกิดอะไรขึ้นหากฉันส่งดัชนีที่เท่ากับจำนวน series ใน chart?
  - answer: ใช่, หลังจาก `columnChart.Series.RemoveAt` legend จะถูกสร้างใหม่เพื่อสะท้อน
      series ที่เหลืออยู่ ทำให้รายการที่ถูกลบหายไปจาก legend
    question: การลบ series จะทำให้ legend ของ chart อัปเดตโดยอัตโนมัติหรือไม่?
  - answer: โค้ดนี้ทำงานได้กับประเภท chart ใดก็ได้ที่รองรับคอลเลกชัน `Series`; เพียงเปลี่ยน
      `ChartType.Column` เป็นประเภทที่ต้องการเมื่อแทรก chart
    question: ฉันสามารถใช้โค้ดเดียวกันเพื่อลบ series จาก line chart หรือ pie chart
      ได้หรือไม่?
  - answer: chart ที่ไม่มี series เลยยังคงเป็น `Shape` ที่ถูกต้องและจะถูกบันทึกไว้
      แต่จะปรากฏเป็นช่องว่างในเอกสารที่ได้
    question: หากฉันลบ series เพียงอันเดียวใน chart, chart จะยังคงถูกบันทึกอย่างถูกต้องหรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: ลบ Chart Series ใน Word Document
og_description: คู่มือขั้นตอนต่อขั้นตอนในการลบ series ของข้อมูลจาก Word chart ด้วย Aspose.Words for .NET
og_image_alt: คำแนะนำที่แสดงวิธีลบ series ของข้อมูลที่ระบุจาก column chart ใน Word document ด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ลบ Chart Series จาก Word Document ด้วย Aspose.Words
บทเรียนนี้แสดงวิธีสร้าง Word document, เพิ่ม column chart ด้วย DocumentBuilder, แล้วลบ series ของข้อมูลที่ระบุจาก chart นั้นโดยใช้เมธอด ChartSeriesCollection.RemoveAt. เมื่อเสร็จสิ้น คุณจะได้เอกสารที่บันทึกไว้โดยที่ series ที่ไม่ต้องการถูกลบออก ทำให้คุณควบคุมเนื้อหา chart ได้อย่างแม่นยำโดยตรงจากโค้ด .NET

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: จะเกิดอะไรขึ้นหากฉันส่งดัชนีที่เท่ากับจำนวน series ใน chart?**  
A: การตรวจสอบ `if` (`targetSeriesIdx < columnChart.Series.Count`) จะล้มเหลว ดังนั้น `RemoveAt` จะไม่ถูกเรียกและ chart จะคงเดิมไม่มีการเปลี่ยนแปลง

**Q: การลบ series จะทำให้ legend ของ chart อัปเดตโดยอัตโนมัติหรือไม่?**  
A: ใช่, หลังจาก `columnChart.Series.RemoveAt` legend จะถูกสร้างใหม่เพื่อสะท้อน series ที่เหลืออยู่ ทำให้รายการที่ถูกลบหายไปจาก legend

**Q: ฉันสามารถใช้โค้ดเดียวกันเพื่อลบ series จาก line chart หรือ pie chart ได้หรือไม่?**  
A: โค้ดนี้ทำงานได้กับประเภท chart ใดก็ได้ที่รองรับคอลเลกชัน `Series`; เพียงเปลี่ยน `ChartType.Column` เป็นประเภทที่ต้องการเมื่อแทรก chart

**Q: หากฉันลบ series เพียงอันเดียวใน chart, chart จะยังคงถูกบันทึกอย่างถูกต้องหรือไม่?**  
A: chart ที่ไม่มี series เลยยังคงเป็น `Shape` ที่ถูกต้องและจะถูกบันทึกไว้ แต่จะปรากฏเป็นช่องว่างในเอกสารที่ได้

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}