---
category: general
date: 2026-07-29
description: วิธีแก้ไขแผนภูมิในเอกสาร Word—เรียนรู้การเปลี่ยนตำแหน่งป้ายแผนภูมิ, ปรับป้ายแผนภูมิแท่ง,
  แก้ไขป้ายข้อมูลแผนภูมิ, และเปลี่ยนฟอนต์ของป้ายแผนภูมิ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: th
lastmod: 2026-07-29
og_description: 'วิธีแก้ไขแผนภูมิใน Word อย่างรวดเร็ว: เชี่ยวชาญการเปลี่ยนตำแหน่งป้ายแผนภูมิ,
  ปรับแต่งป้ายแผนภูมิบาร์, แก้ไขป้ายข้อมูลแผนภูมิ, และเปลี่ยนฟอนต์ของป้ายแผนภูมิ.'
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: วิธีแก้ไขแผนภูมิใน Word – เปลี่ยนป้ายชื่อและแบบอักษร
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'วิธีแก้ไขแผนภูมิใน Word: เปลี่ยนตำแหน่งป้ายชื่อ, แบบอักษรและอื่น ๆ'
url: /th/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแก้ไขแผนภูมิใน Word: เปลี่ยนตำแหน่งป้าย, ฟอนต์ & เพิ่มเติม

การแก้ไขแผนภูมิในเอกสาร Word เป็นความต้องการทั่วไปเมื่อคุณต้องการให้รายงานดูเป็นมืออาชีพ เคยประสบปัญหาในการ **change chart label position** หรือทำให้ป้ายอ่านง่ายโดยไม่ต้องค้นหาผ่านเมนูที่ไม่มีที่สิ้นสุดหรือไม่? คุณไม่ได้อยู่คนเดียว—นักพัฒนาส่วนใหญ่เจออุปสรรคนี้เมื่อทำการสร้างรายงานอัตโนมัติ ในคู่มือนี้เราจะพาคุณผ่านตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่งแสดงให้เห็นอย่างชัดเจนวิธี **adjust bar chart labels**, **modify chart data labels**, และ **change chart label font** ด้วย C# และไลบรารี Aspose.Words

## สิ่งที่คุณจะได้เรียนรู้

- โหลดไฟล์ .docx ที่มีแผนภูมิแท่งอยู่แล้ว  
- ดึงรูปแผนภูมิแรกและเข้าถึงคอลเลกชันของป้ายข้อมูล  
- **Change chart label position** เพื่อทำให้แถบดูเรียบร้อยขึ้น  
- **Adjust bar chart labels** ขนาดฟอนต์เพื่อการอ่านที่ดียิ่งขึ้น  
- บันทึกเอกสารที่แก้ไขแล้วกลับไปยังดิสก์  

ไม่มีเครื่องมือภายนอก, ไม่มีขั้นตอน UI แบบแมนนวล—เพียงโค้ดล้วนที่คุณสามารถใส่ลงในโปรเจกต์ .NET ใดก็ได้ เมื่อเสร็จสิ้นคุณจะมีโซลูชันแบบอิสระที่สามารถใช้ซ้ำได้กับเอกสารหลายสิบฉบับ

> **Prerequisites**  
> - .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานบน .NET Framework 4.7+)  
> - Aspose.Words for .NET (พร้อมให้ดาวน์โหลดผ่าน NuGet)  
> - ไฟล์ Word (`BarChart.docx`) ที่มีแผนภูมิแท่งอยู่แล้ว  

หากคุณขาดส่วนใดส่วนหนึ่งเหล่านี้ ให้ดาวน์โหลดแพคเกจ Aspose.Words ล่าสุดได้เลย:

```bash
dotnet add package Aspose.Words
```

---

## วิธีแก้ไขแผนภูมิ: ดึงแผนภูมิจากเอกสาร Word

ขั้นตอนแรกใน **how to edit chart** คือการโหลดเอกสารและค้นหารูปแผนภูมิ Aspose.Words ถือว่าแผนภูมิเป็นโหนด `Shape` ดังนั้นเราจึงสามารถใช้ `GetChild` พร้อม `NodeType.Shape` เพื่อดึงแผนภูมิแรกที่พบได้

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> การเข้าถึงอ็อบเจ็กต์ `Chart` โดยตรงช่วยให้คุณหลีกเลี่ยงการเปิดไฟล์ใน Word และปรับป้ายแต่ละอันด้วยตนเอง ซึ่งเป็นหัวใจหลักของการ **modify chart data labels** แบบอัตโนมัติ

## ปรับป้ายแผนภูมิแท่ง: เปลี่ยนตำแหน่งป้ายแผนภูมิ

ตอนนี้เรามีอินสแตนซ์ `Chart` แล้ว ให้วนลูปผ่าน `DataLabelCollection` ของมัน เป้าหมายคือ **change chart label position** เพื่อให้แต่ละป้ายอยู่ภายในฐานของแถบอย่างเรียบร้อย แทนที่จะลอยอยู่เหนือแถบอย่างอึดอัด

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> `InsideBase` ทำงานได้ดีสำหรับแผนภูมิแท่งแนวตั้ง หากคุณทำงานกับแผนภูมิแท่งแนวนอน ลองใช้ `InsideEnd` แทน การทดลองตำแหน่งต่าง ๆ ทำได้ง่าย—แค่รันโค้ดใหม่และเปิดไฟล์ที่บันทึกไว้

## เปลี่ยนฟอนต์ป้ายแผนภูมิ: ปรับขนาดฟอนต์เพื่อความอ่านง่าย

ฟอนต์ขนาดเล็กเป็นศัตรูเงียบของความชัดเจนในรายงาน เพื่อ **change chart label font** เพียงตั้งค่า `Font.Size` บนแต่ละ `ChartDataLabel` เราจะเพิ่มเป็น 9 pt ซึ่งเป็นขนาดที่เหมาะสมสำหรับรายงานที่พิมพ์ส่วนใหญ่

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Why we do this:**  
> การปรับขนาดฟอนต์เป็นส่วนหนึ่งของแนวปฏิบัติ **modify chart data labels** ฟอนต์ที่ใหญ่ขึ้นช่วยเพิ่มการเข้าถึงและลดความจำเป็นในการทำ post‑processing ด้วยมือ

## บันทึกเอกสารที่อัปเดตแล้ว

หลังจากปรับตำแหน่งและฟอนต์แล้ว ขั้นตอนสุดท้ายใน **how to edit chart** คือการบันทึกการเปลี่ยนแปลง Aspose.Words ทำให้ขั้นตอนนี้เป็นบรรทัดเดียว

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

เปิด `BarChartCustomLabels.docx` ใน Word แล้วคุณจะเห็นป้ายอยู่ภายในแถบอย่างพอดี พร้อมฟอนต์ 9 pt ที่ชัดเจน ไม่ต้องจ้องมองตัวเลขขนาดเล็กอีกต่อไป

---

## ตัวอย่างทำงานเต็มรูปแบบ (ทุกขั้นตอนในไฟล์เดียว)

ด้านล่างเป็นโปรแกรมคอนโซลที่พร้อมรันเต็มรูปแบบซึ่งสาธิตกระบวนการทั้งหมด—from การโหลดเอกสารจนถึงการบันทึกเวอร์ชันที่อัปเดต คัดลอก‑วางลงในโปรเจกต์คอนโซล .NET ใหม่และกด **F5**

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Expected output** เมื่อคุณรันโปรแกรม:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

เปิดไฟล์ที่ได้และคุณจะเห็น **adjust bar chart labels** อยู่ภายในแถบพร้อมขนาดฟอนต์ที่สบายตา

---

## คำถามทั่วไป & กรณีขอบ

### ถ้าเอกสารมีหลายแผนภูมิ?

โค้ดด้านบนดึง *แผนภูมิแรก* (`GetChild(NodeType.Shape, 0, true)`) หากต้องการแก้ไขทุกแผนภูมิ ให้เปลี่ยนการดึงแบบเดี่ยวเป็นลูป:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### วิธี **change chart label font** สำหรับซีรีส์เฉพาะเท่านั้น?

แต่ละ `ChartSeries` มี `DataLabelCollection` ของตนเอง ให้เลือกซีรีส์ตามดัชนี:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### โค้ดนี้ทำงานกับแผนภูมิพายหรือเส้นได้หรือไม่?

ได้—`ChartDataLabelPosition` รองรับค่าเช่น `InsideEnd`, `OutsideEnd` และ `BestFit` สำหรับแผนภูมิพายคุณอาจเลือก `OutsideEnd` เพื่อให้ป้ายอ่านง่าย

### เรื่องการแปลภาษา (เช่น ตัวคั่นทศนิยมที่ต่างกัน) ล่ะ?

Aspose.Words เคารพการตั้งค่าท้องถิ่นของเอกสาร หากต้องการบังคับรูปแบบเฉพาะ ให้ปรับ `label.NumberFormat` ก่อนบันทึก

---

## สรุป & ขั้นตอนต่อไป

เราได้ครอบคลุม **how to edit chart** ในเอกสาร Word ตั้งแต่ต้นจนจบ: การโหลดไฟล์, การดึงแผนภูมิ, **changing chart label position**, **adjusting bar chart labels**, **modifying chart data labels**, และสุดท้าย **changing chart label font** ก่อนบันทึก ตัวอย่างเต็มรูปแบบพร้อมใช้งานในสภาพแวดล้อมการผลิตและสามารถใส่ลงใน pipeline การอัตโนมัติใด ๆ ได้

พร้อมจะก้าวต่อ? พิจารณาแนวคิดต่อไปนี้:

- **Add data label colors** (`dataLabel.Font.Color = Color.Blue;`).  
- **Show values as percentages** (`dataLabel.NumberFormat = "0%";`).  
- **Create charts programmatically** instead of loading existing ones.  

ทั้งหมดนี้สร้างบน API surface เดียวกับที่เราใช้วันนี้ คุณจึงรู้สึกคุ้นเคยได้ทันที

หากคุณเจออุปสรรคใด ๆ ฝากคอมเมนต์ด้านล่างหรือดูเอกสาร Aspose.Words เพื่อเรียนรู้ตัวเลือกการปรับแต่งแผนภูมิแบบลึกขึ้น โค้ดดิ้งให้สนุกและเพลิดเพลินกับแผนภูมิที่มีป้ายสวยงาม!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่อธิบายในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโปรเจกต์ของคุณเอง

- [ปรับแต่งป้ายข้อมูลแผนภูมิ](/words/english/net/programming-with-charts/chart-data-label/)
- [จัดรูปแบบตัวเลขของป้ายข้อมูลในแผนภูมิ](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [ป้ายข้อมูลแผนภูมิ](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}