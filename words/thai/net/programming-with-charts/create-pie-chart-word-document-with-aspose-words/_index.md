---
category: general
date: 2026-08-10
description: สร้างเอกสาร Word ที่มีแผนภูมิวงกลมโดยใช้ Aspose.Words เรียนรู้วิธีแทรกแผนภูมิ
  ปรับแต่งสีของแผนภูมิวงกลม และเปลี่ยนสีของส่วนวงกลมใน C#
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: th
lastmod: 2026-08-10
og_description: สร้างเอกสาร Word ที่มีแผนภูมิวงกลมด้วย Aspose.Words คู่มือนี้อธิบายวิธีแทรกแผนภูมิ
  ปรับแต่งสีของแผนภูมิวงกลม และเปลี่ยนสีของชิ้นส่วนวงกลมในแอปพลิเคชัน C#
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: สร้างเอกสาร Word แผนภูมิวงกลม – คู่มือ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: สร้างเอกสาร Word พร้อมแผนภูมิวงกลมด้วย Aspose.Words
url: /th/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word แผนภูมิวงกลมด้วย Aspose.Words

หากคุณต้องการ **สร้างเอกสาร Word แผนภูมิวงกลม** อย่างอัตโนมัติ บทแนะนำนี้จะแสดงวิธีทำอย่างละเอียด เราจะพาคุณผ่านการแทรกแผนภูมิ, **การปรับแต่งสีแผนภูมิวงกลม**, และ **การเปลี่ยนสีชิ้นส่วนวงกลม** ด้วย Aspose.Words for .NET.

คุณจะได้เห็นตัวอย่างที่สมบูรณ์และสามารถรันได้ ซึ่งคุณสามารถคัดลอกไปยัง Visual Studio, รัน, และเปิดไฟล์ *.docx* ที่สร้างขึ้นทันทีเพื่อยืนยันแผนภูมิวงกลมที่มีสไตล์ ไม่จำเป็นต้องอ้างอิงเอกสารภายนอก—ทุกอย่างที่คุณต้องการอยู่ในคู่มือนี้.

## ข้อกำหนดเบื้องต้น

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า ติดตั้งแล้ว  
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ประเมินผลชั่วคราว)  
* Visual Studio 2022 (หรือ IDE สำหรับ C# ใดก็ได้)

โค้ดนี้ใช้เพียงเนมสเปซ `Aspose.Words` และ `Aspose.Words.Drawing.Charts` เท่านั้น ดังนั้นไม่จำเป็นต้องมีแพ็กเกจ NuGet เพิ่มเติมนอกจากไลบรารี Aspose.Words.

## สร้างเอกสาร Word แผนภูมิวงกลม – ตัวอย่างเต็ม

โปรแกรม C# ด้านล่างนี้สร้างเอกสาร Word ใหม่, แทรกแผนภูมิวงกลม, ปรับสไตล์ให้สองชิ้นส่วนแรก, และบันทึกไฟล์ แต่ละขั้นตอนจะอธิบายอย่างละเอียด.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### คำอธิบายของแต่ละขั้นตอน

| ขั้นตอน | ทำอะไร | ทำไมจึงสำคัญ |
|------|--------------|----------------|
| **1** | สร้าง `Document` ใหม่และ `DocumentBuilder`. | `DocumentBuilder` ให้เมธอดแบบ fluent สำหรับแทรกเนื้อหา เช่น แผนภูมิ ลงในไฟล์ Word. |
| **2** | เรียก `InsertChart` ด้วย `ChartType.Pie` และขนาดคงที่. | `InsertChart` คือเมธอด **วิธีแทรกแผนภูมิ**; การกำหนดความกว้าง/สูงทำให้แผนภูมิเหมาะกับหน้า. |
| **3** | เพิ่ม series ของข้อมูลที่มีสามประเภทและค่าตัวเลข. | แผนภูมิวงกลมที่ไม่มีข้อมูลจะไม่แสดง; การใส่ข้อมูลจะแสดงขั้นตอนการจัดสไตล์. |
| **4** | ตั้งค่า `Explosion` ที่จุดแรก. | การทำให้ชิ้นส่วนระเบิดออกดึงความสนใจไปยังส่วนหนึ่ง—มีประโยชน์สำหรับการเน้นข้อมูลสำคัญ. |
| **5** | ตั้งค่า `ForeColor` สำหรับสองจุดแรก. | นี่คือหัวใจของ **การปรับแต่งสีแผนภูมิวงกลม**; คุณสามารถใช้ `System.Drawing.Color` ใดก็ได้. |
| **6** | แสดงวิธี **เปลี่ยนสีชิ้นส่วนวงกลม** สำหรับชิ้นส่วนเพิ่มเติม. | แสดงว่าการจัดสไตล์ไม่ได้จำกัดแค่สองชิ้นส่วนแรก; คุณสามารถกำหนดสีให้แต่ละชิ้นส่วนได้. |
| **7** | บันทึกเอกสารเป็น `PieChartStyled.docx`. | ผลลัพธ์สุดท้ายสามารถเปิดได้ใน Microsoft Word, Google Docs หรือโปรแกรมดูที่รองรับ. |

#### ผลลัพธ์ที่คาดหวัง

การเปิด `PieChartStyled.docx` จะแสดงหน้าเดียวที่มีแผนภูมิวงกลมขนาด 400 × 300 pt:

* ชิ้นส่วน 1 (สีส้ม) ระเบิดออกด้านนอก.  
* ชิ้นส่วน 2 (สีเขียว) อยู่ติดกับชิ้นส่วนที่ระเบิด.  
* ชิ้นส่วน 3 (สีฟ้า‑สตีล) เติมส่วนที่เหลือ.

แผนภูมินี้สะท้อนค่าข้อมูล (30, 45, 25) และสีที่คุณกำหนดเอง.

## วิธีจัดสไตล์วงกลม – เคล็ดลับเพิ่มเติม

* **ใช้สีธีม** – แทนการกำหนดค่า `Color.Orange` อย่างตายตัว, คุณสามารถดึงสีจากธีมของเอกสาร:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **เพิ่มป้ายข้อมูล** – หากต้องการแสดงเปอร์เซ็นต์บนแผนภูมิ:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **ปรับขนาดแบบไดนามิก** – คำนวณขนาดแผนภูมิตามระยะขอบหน้ากระดาษ:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

การปรับเปลี่ยนเหล่านี้แสดงถึงความยืดหยุ่นของ **วิธีจัดสไตล์วงกลม** นอกเหนือจากตัวอย่างพื้นฐาน.

## คำถามที่พบบ่อย

**Q: นี้ทำงานกับ .NET Core หรือไม่?**  
A: ใช่. Aspose.Words for .NET รองรับ .NET Core, .NET 5, .NET 6 และรุ่นต่อไป เพียงอ้างอิงแพ็กเกจ NuGet เดียวกัน.

**Q: ถ้าต้องการแผนภูม donuts แทนวงกลมจะทำอย่างไร?**  
A: แทนที่ `ChartType.Pie` ด้วย `ChartType.Doughnut`. API การจัดสไตล์เดียวกัน (`Explosion`, `ForeColor`) ใช้ได้.

**Q: สามารถแทรกแผนภูมิลงในเอกสารที่มีอยู่แล้วได้หรือไม่?**  
A: เปิดไฟล์ที่มีอยู่ด้วย `new Document("Existing.docx")`, สร้าง `DocumentBuilder` สำหรับเอกสารนั้น, แล้วเรียก `InsertChart` ที่ตำแหน่งเคอร์เซอร์ที่ต้องการ.

**Q: จะจัดการชุดข้อมูลขนาดใหญ่อย่างไร?**  
A: แผนภูมวงกลมเหมาะกับจำนวนประเภทที่จำกัด (โดยทั่วไป < 10). หากมีหลายประเภท, ควรพิจารณาใช้แผนภูมิแท่งหรือคอลัมน์แทน.

## สรุปโค้ดต้นฉบับทั้งหมด

ด้านล่างเป็นโปรแกรมเต็มในบล็อกเดียวเพื่อคัดลอก‑วางได้ง่าย:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

การรันโค้ดนี้จะสร้างเอกสาร Word ที่มีแผนภูมิวงกลมที่จัดสไตล์ตามที่อธิบายไว้ก่อนหน้า.

## สรุป

คุณตอนนี้รู้วิธี **สร้างเอกสาร Word แผนภูมิวงกลม** ด้วย Aspose.Words, **ปรับแต่งสีแผนภูมิวงกลม**, และ **เปลี่ยนสีชิ้นส่วนวงกลม** อย่างอัตโนมัติ คู่มือนี้ครอบคลุมการแทรกแผนภูมิ, เติมข้อมูล, ทำให้ชิ้นส่วนระเบิด, ใช้สีที่กำหนดเอง, และบันทึกผลลัพธ์.  

จากนี้คุณสามารถสำรวจหัวข้อที่เกี่ยวข้อง เช่น **วิธีแทรกแผนภูมิ** ประเภทอื่นนอกจากวงกลม, การเพิ่มคำอธิบาย, หรือการสร้างรายงานหลายหน้าโดยมีหลายแผนภูมิ ทดลองใช้สคีมสีและชุดข้อมูลต่าง ๆ เพื่อให้ตรงกับความต้องการของการรายงานของคุณ.

ขอให้เขียนโค้ดอย่างสนุก!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ.

- [แทรกแผนภูมิคอลัมน์ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [แทรกแผนภูมิพื้นที่ในเอกสาร Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [สร้างแผนภูมิกระจายใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}