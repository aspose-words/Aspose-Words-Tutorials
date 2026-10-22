---
title: อัปเดตข้อมูลซีรีส์ของแผนภูมิในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 610
limit:
description: เรียนรู้การแก้ไขจุดข้อมูลของซีรีส์แผนภูมิในเอกสาร Word และรีเฟรชแผนภูมิด้วย Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้การแก้ไขจุดข้อมูลของซีรีส์แผนภูมิในเอกสาร Word และรีเฟรชแผนภูมิด้วย
    Aspose.Words for .NET.
  headline: อัปเดตข้อมูลซีรีส์ของแผนภูมิในเอกสาร Word ด้วย Aspose.Words for .NET
  type: TechArticle
- description: เรียนรู้การแก้ไขจุดข้อมูลของซีรีส์แผนภูมิในเอกสาร Word และรีเฟรชแผนภูมิด้วย
    Aspose.Words for .NET.
  name: อัปเดตข้อมูลซีรีส์ของแผนภูมิในเอกสาร Word ด้วย Aspose.Words for .NET
  steps:
  - name: สร้าง Document ใหม่, แทรกแผนภูมิคอลัมน์ด้วย DocumentBuilder, แล้วบันทึกเป็นไฟล์เริ่มต้น
    text: สร้าง Document ใหม่, แทรกแผนภูมิคอลัมน์ด้วย DocumentBuilder, แล้วบันทึกเป็นไฟล์เริ่มต้น
  - name: เปิดไฟล์ที่บันทึกไว้และค้นหา shape ของแผนภูมิเพื่อรับอ็อบเจ็กต์ Chart ที่มีอยู่
    text: เปิดไฟล์ที่บันทึกไว้และค้นหา shape ของแผนภูมิเพื่อรับอ็อบเจ็กต์ Chart ที่มีอยู่
  - name: ล้างค่าของซีรีส์แรกและเพิ่มจุดใหม่, จากนั้นปรับซีรีส์ที่สองโดยลบจุดแรกออกและเพิ่มจุดใหม่หนึ่งจุด
    text: ล้างค่าของซีรีส์แรกและเพิ่มจุดใหม่, จากนั้นปรับซีรีส์ที่สองโดยลบจุดแรกออกและเพิ่มจุดใหม่หนึ่งจุด
  - name: บันทึกเอกสารที่แก้ไขเป็นไฟล์ใหม่ที่มีแผนภูมิอัปเดต
    text: บันทึกเอกสารที่แก้ไขเป็นไฟล์ใหม่ที่มีแผนภูมิอัปเดต
  type: HowTo
- questions:
  - answer: ใช้ `document.GetChildNodes(NodeType.Shape, true)` เพื่อดึง shape ทั้งหมด,
      จากนั้นกรองด้วย `s.HasChart` และเลือกอันแรก (หรืออันที่ต้องการ) – วิธีนี้จะหลีกเลี่ยงการเลือกรูปภาพหรือกล่องข้อความที่ไม่เกี่ยวข้อง.
    question: ฉันจะค้นหา shape ของแผนภูมิในเอกสารที่อาจมี shape อื่น ๆ อย่างมั่นใจได้อย่างไร?
  - answer: '`ClearValues()` จะลบจุดข้อมูลที่มีอยู่; หากไม่ทำเช่นนั้น จุดใหม่จะถูกต่อท้ายกับจุดเก่า
      ซึ่งอาจทำให้เกิดหมวดหมู่ซ้ำหรือผลรวมที่ไม่ถูกต้อง.'
    question: ทำไมต้องเรียก `ClearValues()` ก่อนเพิ่มจุดใหม่เข้าไปในซีรีส์?
  - answer: ใช้ `FromString` เมื่อหมวดหมู่บนแกน X ของแผนภูมิเป็นข้อความ (เช่น "Group
      A"), และใช้ `FromDouble` เมื่อแกนต้องการค่าตัวเลขเช่น วันที่หรือการวัด.
    question: ควรใช้ `ChartXValue.FromString` หรือ `ChartXValue.FromDouble` สำหรับค่าบนแกน
      X เมื่อใด?
  - answer: การพยายามเข้าถึงซีรีส์ที่ไม่มีจะทำให้เกิด `ArgumentOutOfRangeException`;
      ควรตรวจสอบ `existingChart.Series.Count` ก่อนอ้างอิงดัชนีใด ๆ เสมอ.
    question: จะเกิดอะไรขึ้นหากแผนภูมิมีเพียงซีรีส์เดียวและฉันพยายามเข้าถึง `existingChart.Series[1]`?
  - answer: การบันทึก `openedDoc` เพียงพอแล้ว เพราะมันเป็นอินสแตนซ์ของเอกสารที่มีแผนภูมิที่แก้ไขแล้ว;
      `document` ดั้งเดิมใช้เพียงเพื่อสร้างไฟล์เริ่มต้นเท่านั้น.
    question: ฉันต้องบันทึก `document` ดั้งเดิมใหม่หลังจากแก้ไขแผนภูมิหรือไม่, หรือการบันทึก
      `openedDoc` เพียงพอแล้ว?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: แก้ไขข้อมูลซีรีส์ของแผนภูมิใน Word
og_description: คู่มือขั้นตอนต่อขั้นตอนในการเปลี่ยนค่าซีรีส์ของแผนภูมิในไฟล์ Word ด้วย Aspose.Words for .NET.
og_image_alt: คู่มือแสดงเอกสาร Word ที่มีแผนภูมิคอลัมน์ก่อนและหลังการอัปเดตข้อมูลซีรีส์ด้วย Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# อัปเดตข้อมูลซีรีส์ของแผนภูมิในเอกสาร Word ด้วย Aspose.Words
บทแนะนำนี้แสดงวิธีสร้างเอกสาร Word ที่มีแผนภูมิคอลัมน์, จากนั้นเปิดไฟล์ใหม่อีกครั้ง, ดึงซีรีส์ของแผนภูมิที่มีอยู่, แก้ไขจุดข้อมูลของมัน, และบันทึกเอกสารเพื่อให้แผนภูมิแสดงค่าที่ใหม่. ทำตามโค้ดขั้นตอนต่อขั้นตอนเพื่อดูว่าการปรับข้อมูลแผนภูมิด้วยโปรแกรมเป็นเรื่องง่ายแค่ไหนด้วย Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: ฉันจะค้นหา shape ของแผนภูมิในเอกสารที่อาจมี shape อื่น ๆ อย่างมั่นใจได้อย่างไร?**  
A: ใช้ `document.GetChildNodes(NodeType.Shape, true)` เพื่อดึง shape ทั้งหมด, จากนั้นกรองด้วย `s.HasChart` และเลือกอันแรก (หรืออันที่ต้องการ) – วิธีนี้จะหลีกเลี่ยงการเลือกรูปภาพหรือกล่องข้อความที่ไม่เกี่ยวข้อง.

**Q: ทำไมต้องเรียก `ClearValues()` ก่อนเพิ่มจุดใหม่เข้าไปในซีรีส์?**  
A: `ClearValues()` จะลบจุดข้อมูลที่มีอยู่; หากไม่ทำเช่นนั้น จุดใหม่จะถูกต่อท้ายกับจุดเก่า ซึ่งอาจทำให้เกิดหมวดหมู่ซ้ำหรือผลรวมที่ไม่ถูกต้อง.

**Q: ควรใช้ `ChartXValue.FromString` หรือ `ChartXValue.FromDouble` สำหรับค่าบนแกน X เมื่อใด?**  
A: ใช้ `FromString` เมื่อหมวดหมู่บนแกน X ของแผนภูมิเป็นข้อความ (เช่น "Group A"), และใช้ `FromDouble` เมื่อแกนต้องการค่าตัวเลขเช่น วันที่หรือการวัด.

**Q: จะเกิดอะไรขึ้นหากแผนภูมิมีเพียงซีรีส์เดียวและฉันพยายามเข้าถึง `existingChart.Series[1]`?**  
A: การพยายามเข้าถึงซีรีส์ที่ไม่มีจะทำให้เกิด `ArgumentOutOfRangeException`; ควรตรวจสอบ `existingChart.Series.Count` ก่อนอ้างอิงดัชนีใด ๆ เสมอ.

**Q: ฉันต้องบันทึก `document` ดั้งเดิมใหม่หลังจากแก้ไขแผนภูมิหรือไม่, หรือการบันทึก `openedDoc` เพียงพอแล้ว?**  
A: การบันทึก `openedDoc` เพียงพอแล้ว เพราะมันเป็นอินสแตนซ์ของเอกสารที่มีแผนภูมิที่แก้ไขแล้ว; `document` ดั้งเดิมใช้เพียงเพื่อสร้างไฟล์เริ่มต้นเท่านั้น.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}