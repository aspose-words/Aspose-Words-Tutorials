---
title: ปรับขนาดแผนภูมิให้สัดส่วนเท่าเดิมเมื่อเปลี่ยนขนาดหน้าใน Word ด้วย Aspose.Words for .NET
weight: 210
limit:
description: เรียนรู้การปรับขนาดอัตโนมัติของแผนภูมิคอลัมน์ใน Word เมื่อเปลี่ยนเอกสารเป็น A4 ด้วย Aspose.Words for .NET
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้การปรับขนาดอัตโนมัติของแผนภูมิคอลัมน์ใน Word เมื่อเปลี่ยนเอกสารเป็น
    A4 ด้วย Aspose.Words for .NET
  headline: ปรับขนาดแผนภูมิให้สัดส่วนเท่าเดิมเมื่อเปลี่ยนขนาดหน้าใน Word ด้วย Aspose.Words
    for .NET
  type: TechArticle
- description: เรียนรู้การปรับขนาดอัตโนมัติของแผนภูมิคอลัมน์ใน Word เมื่อเปลี่ยนเอกสารเป็น
    A4 ด้วย Aspose.Words for .NET
  name: ปรับขนาดแผนภูมิให้สัดส่วนเท่าเดิมเมื่อเปลี่ยนขนาดหน้าใน Word ด้วย Aspose.Words
    for .NET
  steps:
  - name: สร้างอ็อบเจ็กต์ Document ใหม่และ DocumentBuilder เพื่อแก้ไขมัน
    text: สร้างอ็อบเจ็กต์ Document ใหม่และ DocumentBuilder เพื่อแก้ไขมัน
  - name: แทรกแผนภูมิคอลัมน์ขนาด 432×252 จุดและรับอ็อบเจ็กต์ Chart ของมัน
    text: แทรกแผนภูมิคอลัมน์ขนาด 432×252 จุดและรับอ็อบเจ็กต์ Chart ของมัน
  - name: ตั้งค่าข้อความหัวเรื่องของแผนภูมิเป็น "Quarterly Revenue" และทำให้แสดงผล
    text: ตั้งค่าข้อความหัวเรื่องของแผนภูมิเป็น "Quarterly Revenue" และทำให้แสดงผล
  - name: บันทึกเอกสารเป็นไฟล์ที่แสดงขนาดแผนภูมิดั้งเดิม
    text: บันทึกเอกสารเป็นไฟล์ที่แสดงขนาดแผนภูมิดั้งเดิม
  - name: เปลี่ยนขนาดกระดาษของเอกสารเป็น A4 และรีเฟรชเลเอาต์
    text: เปลี่ยนขนาดกระดาษของเอกสารเป็น A4 และรีเฟรชเลเอาต์
  - name: คำนวณความกว้างแผนภูมิใหม่ที่เท่ากับ 80 % ของความกว้างหน้าโดยคงอัตราส่วนเดิมไว้
    text: คำนวณความกว้างแผนภูมิใหม่ที่เท่ากับ 80 % ของความกว้างหน้าโดยคงอัตราส่วนเดิมไว้
  - name: หาก shape มีแผนภูมิ, ให้ใช้ความกว้างและความสูงที่คำนวณไว้เพื่อปรับขนาด
    text: หาก shape มีแผนภูมิ, ให้ใช้ความกว้างและความสูงที่คำนวณไว้เพื่อปรับขนาด
  - name: บันทึกเอกสารหลังจากที่แผนภูมิถูกปรับขนาดเพื่อสะท้อนขนาดหน้าที่ใหม่
    text: บันทึกเอกสารหลังจากที่แผนภูมิถูกปรับขนาดเพื่อสะท้อนขนาดหน้าที่ใหม่
  type: HowTo
- questions:
  - answer: ใช่ การเปลี่ยน `docBuilder.PageSetup.PaperSize` ไม่ได้ปรับขนาด shape ที่มีอยู่โดยอัตโนมัติ
      ดังนั้นคุณต้องคำนวณใหม่และกำหนดค่า `chartContainer.Width` และ `Height` ด้วยตนเองตามที่แสดง
    question: ฉันต้องปรับขนาดแผนภูมิด้วยตนเองหลังจากเปลี่ยนขนาดกระดาษของเอกสารหรือไม่?
  - answer: มันเก็บค่า `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      แล้วคำนวณ `newChartHeight = newChartWidth * originalAspectRatio` หลังจากกำหนดความกว้างใหม่
    question: โค้ดทำอย่างไรเพื่อคงอัตราส่วนความกว้างต่อความสูงเดิมของแผนภูมิเมื่อปรับขนาด?
  - answer: '`UpdatePageLayout()` บังคับให้เอนจินการจัดวางประเมินขนาดหน้าต่อใหม่,
      ทำให้ `docBuilder.PageSetup.PageWidth` สะท้อนความกว้าง A4 ใหม่ก่อนที่ขนาดแผนภูมิจะถูกคำนวณใหม่'
    question: ทำไมจึงเรียก `myDoc.UpdatePageLayout()` หลังจากตั้งค่าขนาดกระดาษเป็น
      A4?
  - answer: เงื่อนไข `if (chartContainer.HasChart)` ป้องกันไม่ให้โค้ดกำหนดค่า `Width`
      และ `Height` เมื่อไม่มีแผนภูมิ, ป้องกันข้อยกเว้นขณะรัน
    question: จะเกิดอะไรขึ้นหาก shape ที่แทรกเข้ามาไม่มีแผนภูมิจริงๆ?
  - answer: แน่นอน — แทนที่ตัวคูณ `0.8` ด้วยอัตราส่วนใดก็ได้ที่คุณต้องการ; ส่วนที่เหลือของตรรกะการปรับขนาดยังคงคงอัตราส่วนเดิมไว้
    question: ฉันสามารถเปลี่ยนตัวคูณการสเกล 80 % เป็นค่าต่าง ๆ ได้หรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: ปรับขนาดแผนภูมิ Word เมื่อสลับเป็น A4
og_description: คงอัตราส่วนของแผนภูมิของคุณโดยการปรับขนาดอัตโนมัติหลังจากเปลี่ยนเอกสารเป็น A4
og_image_alt: ภาพหน้าจอแสดงแผนภูมิคอลัมน์ที่ปรับขนาดอัตโนมัติเพื่อให้พอดีกับเอกสาร Word ขนาด A4 ด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ปรับขนาดแผนภูมิให้สัดส่วนเท่าเดิมเมื่อเปลี่ยนขนาดหน้าใน Word ด้วย Aspose.Words
บทแนะนำนี้แสดงวิธีแทรกแผนภูมิคอลัมน์ลงในเอกสาร Word, เปลี่ยนขนาดหน้าของเอกสารเป็น A4, และให้แผนภูมปรับขนาดโดยอัตโนมัติเพื่อคงอัตราส่วนกับความกว้างหน้าที่ใหม่ โดยทำตามขั้นตอนคุณจะเห็นว่าแผนภูมิปรับขนาดโดยไม่ต้องสเกลด้วยตนเอง, ทำให้เลเอาต์คงที่ในรูปแบบหน้าต่างๆ

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: ฉันต้องปรับขนาดแผนภูมิด้วยตนเองหลังจากเปลี่ยนขนาดกระดาษของเอกสารหรือไม่?**  
A: ใช่ การเปลี่ยน `docBuilder.PageSetup.PaperSize` ไม่ได้ปรับขนาด shape ที่มีอยู่โดยอัตโนมัติ ดังนั้นคุณต้องคำนวณใหม่และกำหนดค่า `chartContainer.Width` และ `Height` ด้วยตนเองตามที่แสดง

**Q: โค้ดทำอย่างไรเพื่อคงอัตราส่วนความกว้างต่อความสูงเดิมของแผนภูมิเมื่อปรับขนาด?**  
A: มันเก็บค่า `originalAspectRatio = chartContainer.Height / chartContainer.Width` แล้วคำนวณ `newChartHeight = newChartWidth * originalAspectRatio` หลังจากกำหนดความกว้างใหม่

**Q: ทำไมจึงเรียก `myDoc.UpdatePageLayout()` หลังจากตั้งค่าขนาดกระดาษเป็น A4?**  
A: `UpdatePageLayout()` บังคับให้เอนจินการจัดวางประเมินขนาดหน้าต่อใหม่, ทำให้ `docBuilder.PageSetup.PageWidth` สะท้อนความกว้าง A4 ใหม่ก่อนที่ขนาดแผนภูมิจะถูกคำนวณใหม่

**Q: จะเกิดอะไรขึ้นหาก shape ที่แทรกเข้ามาไม่มีแผนภูมิจริงๆ?**  
A: เงื่อนไข `if (chartContainer.HasChart)` ป้องกันไม่ให้โค้ดกำหนดค่า `Width` และ `Height` เมื่อไม่มีแผนภูมิ, ป้องกันข้อยกเว้นขณะรัน

**Q: ฉันสามารถเปลี่ยนตัวคูณการสเกล 80 % เป็นค่าต่าง ๆ ได้หรือไม่?**  
A: แน่นอน — แทนที่ตัวคูณ `0.8` ด้วยอัตราส่วนใดก็ได้ที่คุณต้องการ; ส่วนที่เหลือของตรรกะการปรับขนาดยังคงคงอัตราส่วนเดิมไว้

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}