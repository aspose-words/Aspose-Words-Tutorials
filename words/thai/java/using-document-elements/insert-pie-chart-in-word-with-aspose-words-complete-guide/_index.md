---
category: general
date: 2026-07-26
description: แทรกแผนภูมิวงกลมลงในเอกสาร Word ด้วย Aspose.Words. เรียนรู้วิธีเพิ่มแผนภูมิ
  แยกชิ้นส่วน และแสดงเปอร์เซ็นต์ในไม่กี่ขั้นตอน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: th
lastmod: 2026-07-26
og_description: แทรกแผนภูมิวงกลมลงในไฟล์ Word ด้วย Aspose.Words. ทำตามคู่มือนี้เพื่อเรียนรู้วิธีเพิ่มแผนภูมิ,
  แยกชิ้นส่วน, และแสดงเปอร์เซ็นต์อย่างรวดเร็ว.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: แทรกแผนภูมิวงกลมใน Word – คำแนะนำ Aspose.Words ทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: แทรกแผนภูมิวงกลมใน Word ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์
url: /th/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกแผนภูมิวงกลมใน Word ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์

เคยต้องการ **insert pie chart** ลงในรายงาน Word แต่ไม่แน่ใจว่าจะเริ่มต้นอย่างไรหรือไม่? คุณไม่ได้อยู่คนเดียว ในหลายแอปธุรกิจ การใช้แผนภูมิวงกลมทำให้ข้อมูลดูเข้าใจได้ทันที และ Aspose.Words ทำให้สิ่งนั้นเป็นไปได้ด้วยเพียงไม่กี่บรรทัดของโค้ด

ในบทแนะนำนี้ เราจะพาคุณผ่านขั้นตอนที่แม่นยำเพื่อ **add chart to Word**, ทำการ explode slice เพื่อเน้น, และแสดงเปอร์เซ็นต์บนป้ายข้อมูล เมื่อเสร็จคุณจะได้ตัวอย่างที่พร้อม‑รันซึ่งสามารถนำไปใช้ในโปรเจกต์ .NET ใดก็ได้

---

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดทำงานได้กับ .NET Core และ .NET Framework ทั้งสอง)
- แพคเกจ NuGet ของ Aspose.Words for .NET ติดตั้งแล้ว  
  ```bash
  dotnet add package Aspose.Words
  ```
- ความเข้าใจพื้นฐานของไวยากรณ์ C# — ไม่จำเป็นต้องมีความซับซ้อน
- IDE ที่คุณเลือก (Visual Studio, Rider หรือ VS Code)

เท่านี้แหละ เริ่มลงมือทำกันเลย

---

## แทรกแผนภูมิวงกลมลงในเอกสาร Word

สิ่งแรกที่เราต้องการคืออ็อบเจกต์ `Document` ใหม่และ `DocumentBuilder` คิดว่า builder เป็นเหมือนปากกาที่เขียนโดยตรงบนผืนแคนวาสของ Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **ทำไมเรื่องนี้ถึงสำคัญ:** `Document` แสดงถึงไฟล์ .docx ทั้งหมด, ในขณะที่ `DocumentBuilder` ให้ API ที่สะดวกสำหรับการแทรกองค์ประกอบเช่นแผนภูมิ, ตาราง, และข้อความ นี่คือพื้นฐานสำหรับทุกการดำเนินการ **how to add chart**

## วิธีเพิ่มแผนภูมิลงใน Word

เมื่อเรามี builder แล้ว เราสามารถ **insert pie chart** ได้จริง ๆ วิธี `insertChart` รับประเภทแผนภูมิและขนาดที่ต้องการเป็นหน่วย point (1 point = 1/72 นิ้ว)

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **เคล็ดลับ:** หากต้องการขนาดอื่น เพียงปรับค่าความกว้างและความสูง แผนภูมิจะปรับขนาดอัตโนมัติเพื่อให้พอดีกับขอบหน้ากระดาษ

## วิธี Explode Slice เพื่อเน้น

การปรับแต่งภาพที่พบบ่อยคือการ “explode” slice เพื่อให้มันโผล่ออกมานอกวงกลม สิ่งนี้จะดึงความสนใจของผู้อ่านไปยังส่วนที่สำคัญที่สุด

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **ทำไมต้อง explode slice?** เมื่อคุณต้องการเน้นหมวดหมู่เฉพาะ—เช่น “รายได้ไตรมาส 1” ในรายงานการเงิน—การ explode slice ทำให้มันโดดเด่นทันทีโดยไม่ต้องใช้ข้อความเพิ่มเติม

## วิธีแสดงเปอร์เซ็นต์บนป้ายข้อมูล

แผนภูมิวงกลมส่วนใหญ่ดูดีขึ้นเมื่อแต่ละ slice แสดงเปอร์เซ็นต์ของมัน Aspose.Words ให้เราสามารถเปิดใช้งานนี้ด้วยคุณสมบัติเดียว

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **หมายเหตุสั้น:** ธง `ShowPercentage` ทำงานกับทุกจุดใน series ดังนั้นคุณไม่จำเป็นต้องตั้งค่าสำหรับแต่ละ slice

## บันทึกเอกสารที่มีแผนภูมิ

สุดท้าย เราจะเขียนเอกสารลงดิสก์ เลือกโฟลเดอร์ใดก็ได้ที่คุณต้องการ; เพียงตรวจสอบให้แน่ใจว่าเส้นทางมีอยู่

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

เมื่อคุณเปิด `PieChart.docx` ใน Microsoft Word คุณจะเห็นแผนภูมิวงกลมที่เรนเดอร์อย่างสมบูรณ์พร้อม slice แรกที่ถูก explode และแสดงเปอร์เซ็นต์—ตรงกับที่คุณคาดหวังจากรายงานธุรกิจที่เรียบหรู

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่สมบูรณ์พร้อมคัดลอก‑วาง‑ใช้ได้ รันเป็นแอปคอนโซลและตรวจสอบไฟล์ผลลัพธ์

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิด `PieChart.docx` ที่สร้างขึ้น คุณจะเห็นแผนภูมิวงกลมสาม slice ชื่อ “Sales Q1” โดย slice แรกถูกดึงออกและแต่ละ slice มีป้าย “30 %”, “45 %”, และ “25 %”. ภาพแสดงตรงกับข้อมูลที่เราใส่เข้าไป

## คำถามทั่วไปและกรณีขอบ

- **What if I need more than one series?**  
  เพียงเพิ่มอ็อบเจกต์ `ChartSeries` เพิ่มเติมไปยัง `chart.Series`. แต่ละ series สามารถมีชุดข้อมูล, สี, และการตั้งค่า explode ของตนเอง

- **Can I change the chart’s colors?**  
  ได้. แต่ละ `ChartPoint` มีคุณสมบัติ `Format.Fill.ForeColor` ที่คุณสามารถตั้งค่าเป็น `System.Drawing.Color` ใดก็ได้

- **What about different chart types?**  
  enum `ChartType` มีประเภทแผนภูมิหลายแบบ เช่น bar, line, doughnut ฯลฯ เปลี่ยน `ChartType.Pie` เป็นประเภทที่คุณต้องการ

- **Is the chart editable in Word after insertion?**  
  แน่นอน. Word จะถือแผนภูมิเป็นแผนภูมิ Office ดั้งเดิม ดังนั้นผู้ใช้สามารถดับเบิล‑คลิกเพื่อเปิดตัวแก้ไขแผนภูมิในตัว

## สรุป

ตอนนี้คุณรู้แล้วว่าต้อง **insert pie chart** ลงในเอกสาร Word ด้วย Aspose.Words อย่างไร, **how to add chart to word**, **how to explode slice**, และ **how to show percentages** บนป้ายข้อมูล ตัวอย่างเต็มที่กล่าวมาพร้อมใช้งานแล้ว และคุณสามารถขยายต่อด้วยข้อมูลที่กำหนดเอง, การจัดรูปแบบ, หรือ series เพิ่มเติม

พร้อมก้าวต่อไปหรือยัง? ลองเปลี่ยน pie เป็น doughnut chart, หรือสร้างชุดรายงานหลายชุดด้วยชุดข้อมูลที่แตกต่างโดยอัตโนมัติ หากคุณสนใจการแสดงผลอื่น ๆ ตรวจสอบคู่มือของเราที่ **how to add chart** สำหรับกราฟแท่งและเส้น, หรือสำรวจเอกสารอ้างอิง API **add chart to word** เพื่อการปรับแต่งที่ลึกซึ้งยิ่งขึ้น

ขอให้เขียนโค้ดอย่างสนุกสนาน และขอให้เอกสารของคุณชัดเจนเสมอเหมือนกับพายที่ถูกตัดอย่างสมบูรณ์!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโปรเจกต์ของคุณ

- [แทรกแผนภูมิคอลัมน์ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [แทรกแผนภูมิพื้นที่ในเอกสาร Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [สร้างแผนภูมิ Scatter ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}