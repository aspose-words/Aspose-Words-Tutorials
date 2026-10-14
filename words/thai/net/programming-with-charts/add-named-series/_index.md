---
title: เพิ่มชุดข้อมูลที่มีชื่อให้กับแผนภูมิฮิสโตแกรมใน Word ด้วย Aspose.Words for .NET
weight: 610
limit:
description: เรียนรู้วิธีฝังแผนภูมิฮิสโตแกรมในเอกสาร Word และเพิ่มชุดข้อมูลที่มีชื่อด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้วิธีฝังแผนภูมิฮิสโตแกรมในเอกสาร Word และเพิ่มชุดข้อมูลที่มีชื่อด้วย
    Aspose.Words for .NET
  headline: เพิ่มชุดข้อมูลที่มีชื่อให้กับแผนภูมิฮิสโตแกรมใน Word ด้วย Aspose.Words
    for .NET
  type: TechArticle
- description: เรียนรู้วิธีฝังแผนภูมิฮิสโตแกรมในเอกสาร Word และเพิ่มชุดข้อมูลที่มีชื่อด้วย
    Aspose.Words for .NET
  name: เพิ่มชุดข้อมูลที่มีชื่อให้กับแผนภูมิฮิสโตแกรมใน Word ด้วย Aspose.Words for
    .NET
  steps:
  - name: สร้างเอกสาร Word ว่างใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนั้น
    text: สร้างเอกสาร Word ว่างใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนั้น
  - name: แทรกรูปแผนภูมิฮิสโตแกรมขนาด 500×300 ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน
    text: แทรกรูปแผนภูมิฮิสโตแกรมขนาด 500×300 ลงในเอกสารและรับอ็อบเจ็กต์ Chart ของมัน
  - name: ลบชุดข้อมูลตัวแทนค่าเริ่มต้นที่ Aspose.Words เพิ่มให้กับแผนภูมิใหม่
    text: ลบชุดข้อมูลตัวแทนค่าเริ่มต้นที่ Aspose.Words เพิ่มให้กับแผนภูมิใหม่
  - name: เพิ่มชุดข้อมูลที่มีชื่อว่า "Demo Series" พร้อมจุดข้อมูลที่ระบุลงในแผนภูมิฮิสโตแกรม
    text: เพิ่มชุดข้อมูลที่มีชื่อว่า "Demo Series" พร้อมจุดข้อมูลที่ระบุลงในแผนภูมิฮิสโตแกรม
  - name: บันทึกเอกสารเป็นไฟล์ .docx ที่มีชุดข้อมูลแผนภูมิที่มีป้ายชื่อ
    text: บันทึกเอกสารเป็นไฟล์ .docx ที่มีชุดข้อมูลแผนภูมิที่มีป้ายชื่อ
  type: HowTo
- questions:
  - answer: '`InsertChart` สร้างชุดข้อมูลตัวแทนค่าเริ่มต้น; การลบออกจะทำให้ชุดข้อมูลว่างนั้นหายไป
      ทำให้แผนภูมิแสดงเฉพาะข้อมูลที่คุณเพิ่มด้วย `Series.Add` เท่านั้น'
    question: ทำไมต้องเรียก `histogramChart.Series.Clear()` ก่อนเพิ่มชุดข้อมูลของฉัน?
  - answer: ได้, เรียก `histogramChart.Series.Add` หลายครั้ง, แต่ละครั้งใช้ชื่อที่แตกต่างและค่า
      `double[]`; แต่ละชุดข้อมูลจะถูกแสดงในคำอธิบายแผนภูมิพร้อมชื่อที่ระบุ
    question: ฉันสามารถเพิ่มหลายชุดข้อมูลโดยใช้ overload เดียวกันได้หรือไม่ และแต่ละชุดจะปรากฏพร้อมป้ายชื่อของตนเองหรือไม่?
  - answer: การ overload นี้คาดหวัง `double[]`; หากคุณมี `int[]` หรืออาเรย์ตัวเลขอื่น
      ๆ ให้แปลงหรือคาสท์เป็น `double[]` ก่อนส่งเข้าไป
    question: อาร์กิวเมนต์ `double[]` เป็นประเภทเดียวที่รับได้สำหรับจุดข้อมูลหรือไม่?
  - answer: สตริงที่ส่งเป็นอาร์กิวเมนต์แรก (เช่น "Demo Series") จะถูกใช้เป็นชื่อชุดข้อมูลและจะแสดงในคำอธิบายแผนภูมิโดยค่าเริ่มต้น
    question: ชื่อชุดข้อมูลที่ฉันระบุจะปรากฏในแผนภูมิโดยอัตโนมัติหรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: เพิ่มชุดข้อมูลที่มีชื่อให้กับแผนภูมิฮิสโตแกรมใน Word
og_description: ตั้งป้ายชื่อชุดข้อมูลในแผนภูมิของ Word อย่างรวดเร็วด้วย Aspose.Words และดูผลลัพธ์ที่แสดงทันที
og_image_alt: ภาพหน้าจอแสดงเอกสาร Word ที่มีแผนภูมิฮิสโตแกรมซึ่งรวมชุดข้อมูลที่มีป้ายชื่อที่สร้างด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มชุดข้อมูลที่มีชื่อให้กับแผนภูมิฮิสโตแกรมใน Word ด้วย Aspose.Words
บทแนะนำนี้แสดงวิธีสร้างเอกสาร Word ด้วย Aspose.Words for .NET, แทรกแผนภูมิฮิสโตแกรม, และเพิ่มชุดข้อมูลที่มีป้ายชื่อโดยใช้การ overload ของ ChartSeriesCollection.Add ที่รับชื่อและค่า การตั้งชื่อชุดข้อมูลช่วยให้คุณระบุแต่ละชุดข้อมูลในแผนภูมิได้อย่างชัดเจน ทำให้ผลลัพธ์ภาพง่ายต่อการอ่านและตีความ

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


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

**Q: ทำไมต้องเรียก `histogramChart.Series.Clear()` ก่อนเพิ่มชุดข้อมูลของฉัน?**  
A: `InsertChart` สร้างชุดข้อมูลตัวแทนค่าเริ่มต้น; การลบออกจะทำให้ชุดข้อมูลว่างนั้นหายไป ทำให้แผนภูมิแสดงเฉพาะข้อมูลที่คุณเพิ่มด้วย `Series.Add` เท่านั้น

**Q: ฉันสามารถเพิ่มหลายชุดข้อมูลโดยใช้ overload เดียวกันได้หรือไม่ และแต่ละชุดจะปรากฏพร้อมป้ายชื่อของตนเองหรือไม่?**  
A: ได้, เรียก `histogramChart.Series.Add` หลายครั้ง, แต่ละครั้งใช้ชื่อที่แตกต่างและค่า `double[]`; แต่ละชุดข้อมูลจะถูกแสดงในคำอธิบายแผนภูมิพร้อมชื่อที่ระบุ

**Q: อาร์กิวเมนต์ `double[]` เป็นประเภทเดียวที่รับได้สำหรับจุดข้อมูลหรือไม่?**  
A: การ overload นี้คาดหวัง `double[]`; หากคุณมี `int[]` หรืออาเรย์ตัวเลขอื่น ๆ ให้แปลงหรือคาสท์เป็น `double[]` ก่อนส่งเข้าไป

**Q: ชื่อชุดข้อมูลที่ฉันระบุจะปรากฏในแผนภูมิโดยอัตโนมัติหรือไม่?**  
A: สตริงที่ส่งเป็นอาร์กิวเมนต์แรก (เช่น "Demo Series") จะถูกใช้เป็นชื่อชุดข้อมูลและจะแสดงในคำอธิบายแผนภูมิโดยค่าเริ่มต้น

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}