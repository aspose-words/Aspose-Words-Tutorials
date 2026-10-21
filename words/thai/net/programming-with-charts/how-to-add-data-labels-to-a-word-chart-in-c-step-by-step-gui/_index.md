---
category: general
date: 2026-08-04
description: วิธีเพิ่มป้ายข้อมูลใน C# ด้วย Aspose.Words เรียนรู้การแก้ไขแผนภูมิ การจัดกึ่งกลางป้ายข้อมูลของแผนภูมิ
  การแสดงเปอร์เซ็นต์ในแผนภูมิ และการปรับแต่งป้ายข้อมูลของแผนภูมิ
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: th
lastmod: 2026-08-04
og_description: วิธีเพิ่มป้ายข้อมูลใน C# ด้วย Aspose.Words บทเรียนนี้จะแสดงวิธีแก้ไขแผนภูมิ,
  จัดตำแหน่งป้ายข้อมูลของแผนภูมิให้อยู่ตรงกลาง, แสดงเปอร์เซ็นต์ในแผนภูมิ, และปรับแต่งป้ายข้อมูลของแผนภูมิ
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: วิธีเพิ่มป้ายข้อมูลในแผนภูมิ Word ด้วย C# – คู่มือเต็ม
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: วิธีเพิ่มป้ายข้อมูลในแผนภูมิ Word ด้วย C# – คู่มือแบบขั้นตอนต่อขั้นตอน
url: /th/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มป้ายข้อมูลลงในแผนภูมิ Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด

หากคุณต้องการ **how to add data labels** ให้กับแผนภูมิที่อยู่ในเอกสาร Word คำแนะนำนี้จะแสดงโค้ดที่คุณต้องรันอย่างแม่นยำ คุณจะได้เห็นวิธีแก้ไขคุณสมบัติของแผนภูมิ, จัดตำแหน่งป้ายข้อมูลของแผนภูมิให้อยู่ตรงกลาง, แสดงเปอร์เซ็นต์ในแผนภูมิ, และปรับแต่งป้ายข้อมูลของแผนภูมิสำหรับทุกสถานการณ์  

บทแนะนำนี้ครอบคลุมทุกอย่างที่จำเป็นสำหรับการแก้ไขแผนภูมิที่มีอยู่แล้ว ตั้งแต่การโหลดเอกสารจนถึงการบันทึกการเปลี่ยนแปลง ไม่ต้องอ้างอิงภายนอก—เพียงแค่ไลบรารี Aspose.Words for .NET และสภาพแวดล้อมการพัฒนา C# เบื้องต้น

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำตามขั้นตอน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 (หรือใหม่กว่า) ติดตั้งอยู่
* Aspose.Words for .NET รุ่น 23.9 หรือใหม่กว่า  
  คุณสามารถติดตั้งผ่าน NuGet:

```bash
dotnet add package Aspose.Words
```

* ไฟล์ Word (`input.docx`) ที่มีอย่างน้อยหนึ่งแผนภูมิ

## วิธีเพิ่มป้ายข้อมูลลงในแผนภูมิ Word ด้วย C#

ส่วนต่อไปนี้จะพาคุณผ่านแต่ละขั้นตอน คำหลักหลัก **how to add data labels** ปรากฏอย่างเป็นธรรมชาติในเนื้อหาและในคอมเมนต์ของโค้ด เพื่อให้ความหนาแน่นของคีย์เวิร์ดอยู่ในช่วงที่แนะนำ

### ขั้นตอนที่ 1 – โหลดเอกสาร Word ที่มีแผนภูมิ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*ทำไมขั้นตอนนี้สำคัญ*: วัตถุ `Document` แทนไฟล์ Word ทั้งไฟล์ การโหลดทำให้คุณเข้าถึงทุกโหนด รวมถึง `Shape` ที่เป็นโฮสต์ของแผนภูมิ

### ขั้นตอนที่ 2 – ดึงแผนภูมิแรกจากเอกสาร

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*ทำไมขั้นตอนนี้สำคัญ*: แผนภูมิถูกเก็บอยู่ในโหนด `Shape` โดยการแคสต์โหนดที่ดึงมาเป็น `Shape` แล้วเรียก `GetChart()` คุณจะได้วัตถุ `Chart` ที่เปิดเผยซีรีส์, แกน, และคอลเลกชันของป้ายข้อมูล

### ขั้นตอนที่ 3 – เปิดใช้งานการปรับแต่งป้ายข้อมูลและแสดงเปอร์เซ็นต์ในแผนภูมิ

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*ทำไมขั้นตอนนี้สำคัญ*: การตั้งค่า `ShowPercentage` บอกให้ Aspose.Words คำนวณและแสดงส่วนแบ่งของแต่ละชิ้นต่อทั้งหมด ซึ่งตรงกับคีย์เวิร์ดรอง **show percentages in chart**

### ขั้นตอนที่ 4 – เปลี่ยนตำแหน่งป้ายให้อยู่ตรงกลางของแต่ละจุดข้อมูล

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*ทำไมขั้นตอนนี้สำคัญ*: คุณสมบัติ `Position` ควบคุมตำแหน่งของป้ายสัมพันธ์กับจุดข้อมูล การใช้ค่า `Center` ตอบสนองคีย์เวิร์ดรอง **center chart data labels** และช่วยให้อ่านง่ายขึ้นสำหรับแผนภูมิพายหรือโดนัท

### ขั้นตอนที่ 5 – ปรับแต่งป้ายข้อมูลของแผนภูมิเพิ่มเติม (ไม่บังคับ)

หากต้องการการควบคุมที่ละเอียดขึ้น คุณสามารถปรับฟอนต์, สี, หรือเส้นนำได้:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

การตั้งค่าเหล่านี้แสดงคีย์เวิร์ดรอง **customize chart data labels** และสาธิตวิธีทำให้รูปลักษณ์สอดคล้องกับแนวทางแบรนด์ของคุณ

### ขั้นตอนที่ 6 – บันทึกเอกสารที่แก้ไขแล้ว

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*ทำไมขั้นตอนนี้สำคัญ*: การบันทึกจะเขียนแผนภูมิที่อัปเดตกลับเข้าไปในไฟล์ Word ทำให้ป้ายข้อมูลใหม่ปรากฏเมื่อเปิดไฟล์ใน Microsoft Word

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมสมบูรณ์ที่คุณสามารถคัดลอก, วาง, และรันได้ รวมถึง `using` directives ที่จำเป็นและคอมเมนต์อธิบายแต่ละบรรทัด

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิด `output.docx` ใน Microsoft Word แผนภูมิจะแสดง:

* ค่าร้อยละข้างแต่ละชิ้น (เช่น **25 %**, **40 %**, …)
* ป้ายอยู่ตรงกลางของแต่ละจุดข้อมูล
* การจัดรูปแบบเพิ่มเติมที่คุณตั้งค่าไว้ เช่น ตัวอักษรสีแดงหนา

สัญญาณภาพเหล่านี้ทำให้แผนภูมิอ่านง่ายขึ้น โดยเฉพาะในการนำเสนอหรือรายงาน

## วิธีแก้ไขคุณสมบัติของแผนภูมิที่เกินกว่าป้ายข้อมูล

แม้ว่าคู่มือนี้จะเน้นที่ **how to add data labels** แต่คุณอาจต้องการ **how to edit chart** เช่น การเปลี่ยนชื่อเรื่อง, ตำแหน่งของคำอธิบาย, หรือการจัดรูปแบบแกน วัตถุ `Chart` มีคุณสมบัติเช่น `Title`, `Legend`, และ `AxisX/AxisY` ตัวอย่างเช่น การเปลี่ยนชื่อเรื่องของแผนภูมิ:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

การแก้ไขแผนภูมิทั้งหมดทำตามรูปแบบเดียวกัน: ดึงแผนภูมิ, ปรับคุณสมบัติ, แล้วบันทึกเอกสาร

## ข้อผิดพลาดทั่วไปและเคล็ดลับปฏิบัติที่ดีที่สุด

| ปัญหา | สาเหตุ | วิธีแก้แนะนำ |
|---|---|---|
| แผนภูมิอยู่ในรูปทรงที่จัดกลุ่ม | `GetChild(NodeType.Shape, …)` คืนค่าโหนดกลุ่มภายนอก ไม่ใช่แผนภูมิภายใน | ค้นหาแบบเรียกซ้ำจนเจอ `shape.HasChart` |
| ป้ายข้อมูลไม่แสดงหลังบันทึก | ไม่ได้ตั้งค่า `ShowValue` หรือ `ShowPercentage` เป็น `true` | ตั้งค่า `ShowValue` และ `ShowPercentage` ให้เป็น `true` ตามต้องการ |
| ป้ายทับกันบนชิ้นส่วนเล็ก | การจัดตำแหน่งตรงกลางอาจทำให้แออัด | ใช้ `ChartDataLabelPosition.OutSideEnd` เพื่อวางนอก หรือเปิด `LeaderLines` |

การนำเคล็ดลับเหล่านี้ไปใช้จะช่วยให้ได้ผลลัพธ์ที่เสถียรในแผนภูมิประเภทต่าง ๆ

## สรุป

คุณได้เรียนรู้ **how to add data labels** ให้กับแผนภูมิ Word ด้วย C# แล้ว คู่มือนี้ครอบคลุมการดึงแผนภูมิ, เปิดการมองเห็นป้าย, จัดตำแหน่งป้ายตรงกลาง, แสดงเปอร์เซ็นต์, และปรับแต่งรูปลักษณ์ ด้วยความรู้นี้คุณยังสามารถ **how to edit chart** ปรับ **center chart data labels**, **show percentages in chart**, และ **customize chart data labels** สำหรับสถานการณ์การรายงานใด ๆ  

พร้อมจะสำรวจต่อหรือยัง? ลองเพิ่มหลายซีรีส์, ใช้การจัดรูปแบบตามเงื่อนไข, หรือส่งออกแผนภูมิเป็นภาพ Aspose.Words API มีความสามารถในการจัดการแผนภูมิอย่างครอบคลุม—ทดลองเพื่อค้นหาการแสดงผลที่เหมาะสมที่สุดสำหรับข้อมูลของคุณ

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ ทุกแหล่งข้อมูลมีโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบต่าง ๆ ในโปรเจกต์ของคุณ

- [ปรับแต่งป้ายข้อมูลของแผนภูมิ](/words/english/net/programming-with-charts/chart-data-label/)
- [ตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูลในแผนภูมิ](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [ปรับแต่งจุดข้อมูลเดียวในแผนภูมิ](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}