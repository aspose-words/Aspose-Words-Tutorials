---
category: general
date: 2026-10-07
description: เรียนรู้วิธีสร้างเอกสาร Word และแทรกแผนภูมิวงกลมโดยใช้ Aspose.Words ใน
  C# คู่มือนี้ยังแสดงวิธีสร้างไฟล์ Word พร้อมป้ายชื่อแผนภูมิที่กำหนดเอง.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: th
lastmod: 2026-10-07
og_description: สร้างเอกสาร Word และแทรกแผนภูมิวงกลมใน C# ตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อสร้างไฟล์
  Word พร้อมป้ายแผนภูมิที่ปรับแต่งได้เต็มที่
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: สร้างเอกสาร Word พร้อมแผนภูมิวงกลมที่กำหนดเองใน C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: วิธีสร้างเอกสาร Word พร้อมแผนภูมิวงกลมที่กำหนดเองใน C#
url: /th/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create word document with a customized pie chart in C#

หากคุณต้องการ **create word document** อย่างโปรแกรมเมติก, บทแนะนำนี้จะแสดงวิธี **insert pie chart** และปรับแต่งป้ายข้อมูลของมันโดยใช้ Aspose.Words for .NET คุณยังจะได้เรียนรู้วิธี **generate word file** ที่มีแผนภูมิที่ออกแบบเต็มรูปแบบ ครอบคลุมตั้งแต่การตั้งค่าโครงการจนถึงการบันทึกเอกสารขั้นสุดท้าย

คู่มือจะเดินผ่านแต่ละขั้นตอนที่จำเป็นเพื่อเพิ่มแผนภูมิ, ปรับตำแหน่งป้าย, เปิดใช้งานเส้นนำ, และสุดท้ายบันทึกผลลัพธ์เป็นไฟล์ `.docx` ไม่ต้องใช้เครื่องมือภายนอกใด ๆ นอกจากไลบรารี Aspose.Words, และโค้ดต้นฉบับทั้งหมดจะถูกจัดให้คุณสามารถคัดลอก, วาง, และรันได้ทันที

## Prerequisites

ก่อนเริ่ม, โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า ติดตั้งแล้ว  
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ประเมินผลฟรี)  
* IDE เช่น Visual Studio 2022 หรือ Visual Studio Code  

คุณยังต้องเพิ่มแพคเกจ NuGet ต่อไปนี้ในโครงการของคุณ:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

แพคเกจเหล่านี้ทำให้คุณเข้าถึงคลาส `Document`, `DocumentBuilder`, และคลาสที่เกี่ยวข้องกับแผนภูมิที่ใช้ในตัวอย่างด้านล่าง

## Create word document and add a chart

ขั้นตอนแรกคือ **create word document** และรับ `DocumentBuilder` ที่ให้คุณแทรกเนื้อหา ตัว builder ทำงานคล้ายกับเคอร์เซอร์ที่วางอยู่ภายในเอกสาร

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

อ็อบเจ็กต์ `Document` แทนไฟล์ Word ทั้งหมด, ส่วน `DocumentBuilder` มีเมธอดเช่น `InsertChart` ที่วางอ็อบเจ็กต์โดยตรงลงในโฟลว์ของเอกสาร

## Insert pie chart into the document

เมื่อ builder พร้อมแล้ว, คุณสามารถ **insert pie chart** ด้วยขนาดที่กำหนดได้ แผนภูมิจะถูกเพิ่มที่ตำแหน่งปัจจุบันของ builder

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` จะคืนค่าอ็อบเจ็กต์ `Chart` ที่คุณสามารถจัดการต่อได้ ข้อมูลตัวอย่างสร้างสี่ส่วนที่แสดงยอดขายไตรมาส

## Customize pie chart data labels

เพื่อทำให้แผนภูมิเข้าใจง่ายขึ้น, คุณมักต้อง **customize pie chart** ป้าย—วางตำแหน่งนอกส่วนและแสดงเส้นนำ นี่คือจุดที่ `ChartDataLabelCollection` เข้ามาช่วย

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

การตั้งค่า `Position` เป็น `OutsideEnd` จะย้ายป้ายแต่ละอันออกไปเหนือขอบของส่วน, ส่วน `ShowLeaderLines` จะวาดเส้นที่เชื่อมป้ายกับส่วนของมัน ธงเลือก `ShowValue` และ `ShowPercentage` จะให้ผู้อ่านเห็นทั้งตัวเลขดิบและเปอร์เซ็นต์สัมพันธ์

**Pro tip:** หากต้องการจัดรูปแบบฟอนต์ของป้าย, ใช้ `dataLabels.Font` เพื่อกำหนดขนาด, สี, และสไตล์ ซึ่งจะทำให้แผนภูมิตรงกับแบรนด์ขององค์กรคุณ

## Save and generate word file

หลังจากแผนภูมิถูกตั้งค่าอย่างเต็มที่, คุณสามารถ **generate word file** โดยบันทึกอินสแตนซ์ `Document` ไปยังดิสก์ เลือกฟอร์แมต `.docx` เพื่อความเข้ากันได้สูงสุดกับเวอร์ชัน Word สมัยใหม่

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

เมื่อคุณเปิด `CustomPieChart.docx`, คุณจะเห็นแผนภูมิวงกลมที่มีสี่ส่วน, แต่ละส่วนมีป้ายอยู่ด้านนอก, เชื่อมด้วยเส้นนำ, และแสดงทั้งค่าและเปอร์เซ็นต์

![Screenshot of a Word document that contains a customized pie chart created with C#](image-placeholder.png)

*ภาพนี้แสดงผลลัพธ์สุดท้ายของบทแนะนำ **create word document***  

## Common variations and edge cases

| Scenario | How to adapt the code |
|----------|----------------------|
| **Multiple series** | เพิ่มอ็อบเจ็กต์ `ChartSeries` เพิ่มเติมไปที่ `pieChart.Series`. แต่ละชุดสามารถมีคอลเลกชัน `DataLabels` ของตนเองเพื่อการจัดรูปแบบอิสระ |
| **Different chart size** | เปลี่ยนพารามิเตอร์ความกว้างและความสูงใน `InsertChart(width, height)`. ค่าเป็นหน่วยพอยต์ (1 pt ≈ 1/72 in) |
| **Chart title** | ใช้ `pieChart.Title.Text = "Quarterly Sales"` เพื่อเพิ่มหัวเรื่องอธิบาย |
| **Export to PDF** | เรียก `document.Save("Report.pdf", SaveFormat.Pdf);` หลังจากสร้างแผนภูมิเสร็จ |
| **License handling** | วางไฟล์ไลเซนส์ของคุณ (`Aspose.Words.lic`) ในโฟลเดอร์แอปพลิเคชันและโหลดด้วย `new License().SetLicense("Aspose.Words.lic");` ก่อนสร้างเอกสาร |

การปรับเปลี่ยนเหล่านี้ช่วยให้คุณตอบคำถาม **how to add pie chart** ในหลายสถานการณ์จริง ตั้งแต่รายงานง่าย ๆ จนถึงแดชบอร์ดซับซ้อน

## Conclusion

ตอนนี้คุณรู้วิธี **create word document**, **insert pie chart**, และ **customize pie chart** ป้ายโดยใช้ Aspose.Words for .NET ตัวอย่างเต็มแสดงขั้นตอนทำงานที่ชัดเจน: เริ่มต้นเอกสาร, เพิ่มแผนภูมิ, ปรับตำแหน่งป้ายข้อมูล, เปิดใช้งานเส้นนำ, และสุดท้าย **generate word file** ที่สามารถแชร์ให้กับใครก็ได้

ลองขยายบทแนะนำนี้โดยทดลองใช้ประเภทแผนภูมิอื่น (`ChartType.Column`, `ChartType.Line`) หรือโดยใช้พาเลตสีที่กำหนดเองให้ตรงกับแบรนด์ของคุณ หากพบปัญหา, ให้ดูเอกสาร Aspose.Words หรือสำรวจหัวข้อที่เกี่ยวข้องเช่น “how to add pie chart” พร้อมหลายชุดข้อมูลและแหล่งข้อมูลแบบไดนามิก

ขอให้สนุกกับการเขียนโค้ด, และอย่าลังเลที่จะแบ่งปันผลลัพธ์หรือถามคำถามต่อในคอมเมนต์!

## What Should You Learn Next?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}