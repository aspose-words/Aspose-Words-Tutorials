---
title: อัปเดตชื่อแผนภูมิและสลับการแสดงผลของคำอธิบายใน Word ด้วย Aspose.Words for .NET
weight: 810
limit:
description: เรียนรู้วิธีเปลี่ยนชื่อแผนภูมิและควบคุมการแสดงผลของคำอธิบายในเอกสาร Word ด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: เรียนรู้วิธีเปลี่ยนชื่อแผนภูมิและควบคุมการแสดงผลของคำอธิบายในเอกสาร
    Word ด้วย Aspose.Words for .NET
  headline: อัปเดตชื่อแผนภูมิและสลับการแสดงผลของคำอธิบายใน Word ด้วย Aspose.Words
    for .NET
  type: TechArticle
- description: เรียนรู้วิธีเปลี่ยนชื่อแผนภูมิและควบคุมการแสดงผลของคำอธิบายในเอกสาร
    Word ด้วย Aspose.Words for .NET
  name: อัปเดตชื่อแผนภูมิและสลับการแสดงผลของคำอธิบายใน Word ด้วย Aspose.Words for
    .NET
  steps:
  - name: กำหนดชื่อแผนภูมิที่ผู้ใช้ระบุและกำหนดว่าคำอธิบาย (legend) ควรแสดงหรือไม่
    text: กำหนดชื่อแผนภูมิที่ผู้ใช้ระบุและกำหนดว่าคำอธิบาย (legend) ควรแสดงหรือไม่
  - name: สร้างเอกสาร Word ใหม่และใช้ DocumentBuilder เพื่อเพิ่มเนื้อหา
    text: สร้างเอกสาร Word ใหม่และใช้ DocumentBuilder เพื่อเพิ่มเนื้อหา
  - name: แทรกแผนภูมิคอลัมน์ขนาด 432 × 252 pt ลงในเอกสารและตรวจสอบว่า Shape นั้นจริง
      ๆ มีแผนภูมิอยู่
    text: แทรกแผนภูมิคอลัมน์ขนาด 432 × 252 pt ลงในเอกสารและตรวจสอบว่า Shape นั้นจริง
      ๆ มีแผนภูมิอยู่
  - name: ดึงอ็อบเจ็กต์ Chart, ตั้งค่าข้อความชื่อให้เป็นค่าที่ผู้ใช้ระบุ และตรวจสอบให้ชื่อแสดงผล
    text: ดึงอ็อบเจ็กต์ Chart, ตั้งค่าข้อความชื่อให้เป็นค่าที่ผู้ใช้ระบุ และตรวจสอบให้ชื่อแสดงผล
  - name: 'กำหนดค่าคำอธิบาย (legend): แสดงที่ด้านขวาหากต้องการ มิฉะนั้นซ่อน และให้สามารถซ้อนทับพื้นที่พล็อตได้'
    text: 'กำหนดค่าคำอธิบาย (legend): แสดงที่ด้านขวาหากต้องการ มิฉะนั้นซ่อน และให้สามารถซ้อนทับพื้นที่พล็อตได้'
  - name: บันทึกเอกสารที่แก้ไขแล้วลงดิสก์เป็นไฟล์ CustomChart.docx
    text: บันทึกเอกสารที่แก้ไขแล้วลงดิสก์เป็นไฟล์ CustomChart.docx
  type: HowTo
- questions:
  - answer: เมื่อ `displayLegend` เป็น `true` โค้ดจะตั้งค่า `chartLegend.Position`
      เป็น `LegendPosition.Right` ทำให้คำอธิบายแสดงที่ด้านขวาของพื้นที่พล็อต; คุณสมบัติ
      `Overlay` ยังคงเป็น `true` ดังนั้นคำอธิบายสามารถซ้อนทับกับแผนภูมิเพื่อประหยัดพื้นที่
    question: การตั้งค่า `displayLegend` เป็น `true` มีผลอย่างไรต่อแผนภูมิที่สร้างขึ้น?
  - answer: ตั้งค่า `chartTitle.Show = false` (หรือไม่ตั้งค่า `Show` เป็น `true` หลังจากกำหนด
      `chartTitle.Text`) ชื่อแผนภูมิจะไม่ถูกแสดงในเอกสาร Word
    question: ฉันจะซ่อนชื่อแผนภูมิได้อย่างไรหากผู้ใช้ไม่ได้ระบุชื่อ?
  - answer: ใช่ — `InsertChart` จะคืนค่าเป็น `Shape` ที่ควรมีแผนภูมิอยู่ แต่การตรวจสอบ
      `HasChart` จะทำให้มั่นใจว่า Shape นั้นจริง ๆ มีอ็อบเจ็กต์ `Chart`; หากไม่เป็นเช่นนั้น
      โค้ดจะโยน `InvalidOperationException`
    question: จำเป็นต้องตรวจสอบ `chartContainer.HasChart` หลังจากเรียก `InsertChart`
      หรือไม่?
  - answer: แน่นอน; สามารถกำหนดค่าใด ๆ จาก enum `LegendPosition` (เช่น `LegendPosition.Top`,
      `LegendPosition.Bottom`, `LegendPosition.Left`) ให้กับ `chartLegend.Position`
      เพื่อย้ายตำแหน่งคำอธิบายตามต้องการ
    question: ฉันสามารถวางคำอธิบายในตำแหน่งอื่นที่ไม่ใช่ด้านขวาได้หรือไม่?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: เปลี่ยนชื่อแผนภูมิและคำอธิบายใน Word
og_description: เรียนรู้การตั้งชื่อแผนภูมิแบบกำหนดเองและควบคุมการแสดงผลของคำอธิบายในเอกสาร Word ด้วย Aspose.Words for .NET
og_image_alt: คู่มือที่แสดงโค้ดสำหรับอัปเดตชื่อแผนภูมิและสลับการแสดงผลของคำอธิบายในเอกสาร Word ด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# อัปเดตชื่อแผนภูมิและสลับการแสดงผลของคำอธิบายใน Word ด้วย Aspose.Words
บทเรียนนี้แสดงวิธีการแก้ไขแผนภูมิภายในเอกสาร Word อย่างโปรแกรมมิ่งด้วย Aspose.Words for .NET คุณจะได้เรียนรู้การแทรกแผนภูมิคอลัมน์, แทนที่ชื่อของมันด้วยข้อความที่ผู้ใช้ให้, และควบคุมการแสดงผลและการซ้อนทับของคำอธิบายตามการตั้งค่าของผู้ใช้ ขั้นตอนเหล่านี้ช่วยให้คุณปรับแต่งการนำเสนอแผนภูมิได้แบบไดนามิกโดยไม่ต้องแก้ไขด้วยมือ

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: การตั้งค่า `displayLegend` เป็น `true` มีผลอย่างไรต่อแผนภูมิที่สร้างขึ้น?**  
A: เมื่อ `displayLegend` เป็น `true` โค้ดจะตั้งค่า `chartLegend.Position` เป็น `LegendPosition.Right` ทำให้คำอธิบายแสดงที่ด้านขวาของพื้นที่พล็อต; คุณสมบัติ `Overlay` ยังคงเป็น `true` ดังนั้นคำอธิบายสามารถซ้อนทับกับแผนภูมิเพื่อประหยัดพื้นที่

**Q: ฉันจะซ่อนชื่อแผนภูมิได้อย่างไรหากผู้ใช้ไม่ได้ระบุชื่อ?**  
A: ตั้งค่า `chartTitle.Show = false` (หรือไม่ตั้งค่า `Show` เป็น `true` หลังจากกำหนด `chartTitle.Text`) ชื่อแผนภูมิจะไม่ถูกแสดงในเอกสาร Word

**Q: จำเป็นต้องตรวจสอบ `chartContainer.HasChart` หลังจากเรียก `InsertChart` หรือไม่?**  
A: ใช่ — `InsertChart` จะคืนค่าเป็น `Shape` ที่ควรมีแผนภูมิอยู่ แต่การตรวจสอบ `HasChart` จะทำให้มั่นใจว่า Shape นั้นจริง ๆ มีอ็อบเจ็กต์ `Chart`; หากไม่เป็นเช่นนั้น โค้ดจะโยน `InvalidOperationException`

**Q: ฉันสามารถวางคำอธิบายในตำแหน่งอื่นที่ไม่ใช่ด้านขวาได้หรือไม่?**  
A: แน่นอน; สามารถกำหนดค่าใด ๆ จาก enum `LegendPosition` (เช่น `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) ให้กับ `chartLegend.Position` เพื่อย้ายตำแหน่งคำอธิบายตามต้องการ

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}