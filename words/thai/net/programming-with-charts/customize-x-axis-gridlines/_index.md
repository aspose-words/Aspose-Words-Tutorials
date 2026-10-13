---
title: ปรับแต่งเส้นกริดแกน X ในแผนภูมิคอลัมน์โดยใช้ Aspose.Words for .NET
weight: 610
limit:
description: เรียนรู้วิธีเพิ่มและปรับสีเส้นกริดหลักของแกน X ในแผนภูมิคอลัมน์ของ Word ด้วย Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้วิธีเพิ่มและปรับสีเส้นกริดหลักของแกน X ในแผนภูมิคอลัมน์ของ
    Word ด้วย Aspose.Words for .NET.
  headline: ปรับแต่งเส้นกริดแกน X ในแผนภูมิคอลัมน์โดยใช้ Aspose.Words for .NET
  type: TechArticle
- description: เรียนรู้วิธีเพิ่มและปรับสีเส้นกริดหลักของแกน X ในแผนภูมิคอลัมน์ของ
    Word ด้วย Aspose.Words for .NET.
  name: ปรับแต่งเส้นกริดแกน X ในแผนภูมิคอลัมน์โดยใช้ Aspose.Words for .NET
  steps:
  - name: สร้างเอกสาร Word ใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนั้น.
    text: สร้างเอกสาร Word ใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนั้น.
  - name: แทรกแผนภูมิคอลัมน์ขนาด 432×252 ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน.
    text: แทรกแผนภูมิคอลัมน์ขนาด 432×252 ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน.
  - name: ลบซีรีส์เริ่มต้นและเพิ่มซีรีส์ที่กำหนดเองที่มีสามกลุ่มและค่าต่าง ๆ.
    text: ลบซีรีส์เริ่มต้นและเพิ่มซีรีส์ที่กำหนดเองที่มีสามกลุ่มและค่าต่าง ๆ.
  - name: รับอ้างอิงถึงแกนแนวนอน (X) หลักของแผนภูมิ.
    text: รับอ้างอิงถึงแกนแนวนอน (X) หลักของแผนภูมิ.
  - name: เปิดการแสดงเส้นกริดหลักบนแกน X หลัก.
    text: เปิดการแสดงเส้นกริดหลักบนแกน X หลัก.
  - name: ตั้งค่าสีของเส้นกริดเป็นสีฟ้าและความหนาเป็น 2 จุด.
    text: ตั้งค่าสีของเส้นกริดเป็นสีฟ้าและความหนาเป็น 2 จุด.
  - name: บันทึกเอกสารเป็นไฟล์ .docx.
    text: บันทึกเอกสารเป็นไฟล์ .docx.
  type: HowTo
- questions:
  - answer: 'ตั้งค่าคุณสมบัติแกนเดียวกันเป็น false: `horizontalAxis.HasMajorGridlines
      = false;` จะสลับการมองเห็นของเส้นกริดหลักของแกน X.'
    question: ฉันจะซ่อนเส้นกริดหลักอีกครั้งหลังจากเปิดใช้งานแล้วได้อย่างไร?
  - answer: ไม่, การตั้งค่า `Format.Stroke` จะใช้กับแกนที่คุณแก้ไขเท่านั้น; หากต้องการจัดรูปแบบเส้นกริดของแกน
      Y คุณต้องปรับ `chart.AxisY.Format.Stroke` แยกต่างหาก.
    question: การเปลี่ยน `horizontalAxis.Format.Stroke.Color` จะส่งผลต่อเส้นกริดของแกน
      Y ด้วยหรือไม่?
  - answer: ใช้ `horizontalAxis.Format.Stroke.Weight` และกำหนดค่า double (เช่น `0.5`)
      เพื่อทำให้เส้นกริดบางลง.
    question: คุณสมบัติใดที่ควบคุมความหนาของเส้นกริดหลักของแกน X?
  - answer: ได้, ตั้งค่า `horizontalAxis.Format.Stroke.DashStyle` เป็นค่า enum ของ
      `DashStyle` เช่น `DashStyle.Dash` หรือ `DashStyle.Dot`.
    question: ฉันสามารถเปลี่ยนรูปแบบเส้นประของเส้นกริดหลักของแกน X ได้หรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: จัดรูปแบบเส้นกริดแกน X ในแผนภูมิคอลัมน์ของ Word
og_description: เปิดและปรับสีเส้นกริดหลักของแกน X ของแผนภูมิ Word ด้วย Aspose.Words for .NET.
og_image_alt: คู่มือที่แสดงเอกสาร Word พร้อมแผนภูมิคอลัมน์ที่เส้นกริดหลักของแกน X ถูกเน้นด้วยสีที่กำหนดเองโดยใช้ Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ปรับแต่งเส้นกริดแกน X ในแผนภูมิคอลัมน์โดยใช้ Aspose.Words
ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีสร้างเอกสาร Word, แทรกแผนภูมิคอลัมน์, แทนที่ข้อมูลเริ่มต้นของมัน, แล้วเปิดใช้งานเส้นกริดหลักบนแกน X หลัก คุณยังจะได้เห็นวิธีเปลี่ยนสีเส้นของกริดให้ตรงกับการออกแบบของคุณ ตามโค้ดขั้นตอนต่อขั้นตอนเพื่อควบคุมการมองเห็นและการจัดรูปแบบของเส้นกริดแกน X อย่างแม่นยำ.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: ฉันจะซ่อนเส้นกริดหลักอีกครั้งหลังจากเปิดใช้งานแล้วได้อย่างไร?**  
A: ตั้งค่าคุณสมบัติแกนเดียวกันเป็น false: `horizontalAxis.HasMajorGridlines = false;` จะสลับการมองเห็นของเส้นกริดหลักของแกน X.

**Q: การเปลี่ยน `horizontalAxis.Format.Stroke.Color` จะส่งผลต่อเส้นกริดของแกน Y ด้วยหรือไม่?**  
A: ไม่, การตั้งค่า `Format.Stroke` จะใช้กับแกนที่คุณแก้ไขเท่านั้น; หากต้องการจัดรูปแบบเส้นกริดของแกน Y คุณต้องปรับ `chart.AxisY.Format.Stroke` แยกต่างหาก.

**Q: คุณสมบัติใดที่ควบคุมความหนาของเส้นกริดหลักของแกน X?**  
A: ใช้ `horizontalAxis.Format.Stroke.Weight` และกำหนดค่า double (เช่น `0.5`) เพื่อทำให้เส้นกริดบางลง.

**Q: ฉันสามารถเปลี่ยนรูปแบบเส้นประของเส้นกริดหลักของแกน X ได้หรือไม่?**  
A: ได้, ตั้งค่า `horizontalAxis.Format.Stroke.DashStyle` เป็นค่า enum ของ `DashStyle` เช่น `DashStyle.Dash` หรือ `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}