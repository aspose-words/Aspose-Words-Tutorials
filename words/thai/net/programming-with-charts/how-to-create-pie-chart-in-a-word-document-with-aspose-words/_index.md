---
category: general
date: 2026-09-21
description: เรียนรู้วิธีสร้างแผนภูมิวงกลมและแทรกแผนภูมิลงใน Word ด้วย Aspose.Words,
  เพิ่มป้ายข้อมูลให้แผนภูมิวงกลม, และแสดงเปอร์เซ็นต์บนแผนภูมิวงกลมในไม่กี่ขั้นตอน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: th
lastmod: 2026-09-21
og_description: สร้างแผนภูมิวงกลมใน Word ด้วย Aspose.Words, แทรกแผนภูมิลงใน Word,
  เพิ่มป้ายข้อมูลให้กับแผนภูมิวงกลม, และแสดงเปอร์เซ็นต์บนแผนภูมิวงกลม—ทั้งหมดพร้อมตัวอย่างโค้ดที่ชัดเจน
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: สร้างแผนภูมิวงกลมใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: วิธีสร้างแผนภูมิวงกลมในเอกสาร Word ด้วย Aspose.Words
url: /th/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างแผนภูมิวงกลมในเอกสาร Word ด้วย Aspose.Words

หากคุณต้องการ **สร้างแผนภูมิวงกลม** ด้วยโปรแกรมมิ่ง Aspose.Words ทำให้ขั้นตอนนี้ง่ายดาย ในบทแนะนำนี้คุณจะได้เห็นวิธี **แทรกแผนภูมิลงใน Word**, ตั้งค่าซีรีส์, **เพิ่มป้ายข้อมูลให้แผนภูมิวงกลม**, และสุดท้าย **แสดงเปอร์เซ็นต์บนแผนภูมิวงกลม** เพื่อให้ภาพแสดงค่าที่แม่นยำ เมื่ออ่านจบคุณจะมีตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่งสามารถนำไปใช้ในโปรเจกต์ .NET ใดก็ได้

คู่มือนี้ครอบคลุมทุกสิ่งที่คุณต้องรู้: แพ็กเกจ NuGet ที่จำเป็น, โค้ด C# เต็มรูปแบบ, คำอธิบายว่าทำไมแต่ละ API จึงสำคัญ, และเคล็ดลับในการปรับแต่งแผนภูมิ ไม่ต้องอ้างอิงเอกสารภายนอก—แค่คัดลอก, รัน, และปรับใช้

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า  
* Visual Studio 2022 (หรือ IDE ใดก็ได้ที่รองรับ .NET)  
* ใบอนุญาต Aspose.Words for .NET (รุ่นทดลองฟรีก็ใช้ทดสอบได้)  
* ความคุ้นเคยพื้นฐานกับ C# และโครงสร้างเอกสาร Word  

หากคุณมีทั้งหมดนี้แล้ว สามารถข้ามไปยังขั้นตอนโค้ดได้ทันที

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า Aspose.Words

สร้างโปรเจกต์คอนโซลใหม่และเพิ่มแพ็กเกจ NuGet ของ Aspose.Words:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

แพ็กเกจนี้รวมเนมสเปซ `Aspose.Words.Drawing.Charts` ซึ่งมีคลาส `Chart` และ `ChartSeries` ที่เราจะใช้

> **เคล็ดลับ:** เก็บไฟล์ใบอนุญาต (`Aspose.Words.lic`) ไว้ที่โฟลเดอร์รากของโปรเจกต์และโหลดในตอนเริ่มต้นเพื่อหลีกเลี่ยงลายน้ำการประเมินผล

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## ขั้นตอนที่ 2: สร้างเอกสารเปล่าและ DocumentBuilder

`Document` แทนไฟล์ Word ส่วน `DocumentBuilder` ให้ API แบบ fluent สำหรับแทรกเนื้อหา

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**เหตุผลที่สำคัญ:** `DocumentBuilder` ควบคุมตำแหน่งการแทรกปัจจุบัน ทำให้แผนภูมิเกิดขึ้นตรงที่คุณต้องการในลำดับของเอกสาร

## ขั้นตอนที่ 3: แทรกแผนภูมิวงกลมลงในเอกสาร Word

ตอนนี้เราจะ **แทรกแผนภูมิลงใน Word** เมธอด `InsertChart` รับประเภทแผนภูมิ, ความกว้าง, และความสูง (หน่วยเป็นพอยต์)

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

ในขั้นตอนนี้แผนภูมิมีซีรีส์ข้อมูลเริ่มต้นที่มีค่า placeholder (25, 25, 25, 25) คุณสามารถเปลี่ยนค่าเหล่านี้ได้ภายหลังหากต้องการ

## ขั้นตอนที่ 4: เข้าถึงซีรีส์แรกและปรับแต่งป้ายข้อมูล

แผนภูมิวงกลมโดยทั่วไปมีซีรีส์เดียว เพื่อ **เพิ่มป้ายข้อมูลให้แผนภูมิวงกลม** เราจะดึงซีรีส์นั้นและเปิดใช้งานการแสดงเปอร์เซ็นต์

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**เหตุผลที่ตั้งค่า `ShowPercentage`:** ธงนี้บอก Aspose.Words ให้คำนวณสัดส่วนของแต่ละชิ้นและแสดงเป็นเปอร์เซ็นต์ `Position` ทำให้ป้ายไม่ทับกับชิ้นส่วน ช่วยให้อ่านง่ายขึ้นโดยเฉพาะเมื่อชิ้นส่วนมีขนาดเล็ก

## ขั้นตอนที่ 5: (ทางเลือก) แทนค่าข้อมูล placeholder

หากต้องการค่าที่เฉพาะเจาะจง ให้แทนที่จุดข้อมูลเริ่มต้น:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

เปอร์เซ็นต์ที่แสดงจะปรับอัตโนมัติเพื่อสะท้อนค่าที่ใหม่

## ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้ายให้เขียนเอกสารลงดิสก์ ส่วนขยายไฟล์จะกำหนดรูปแบบ; `.docx` จะสร้างไฟล์ Word รุ่นใหม่

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

เมื่อรันโปรแกรมจะได้ไฟล์ชื่อ **PieChart.docx** ในโฟลเดอร์ผลลัพธ์ การเปิดไฟล์ด้วย Microsoft Word จะเห็นแผนภูมิวงกลมที่แต่ละชิ้นมีป้ายเปอร์เซ็นต์และอยู่ด้านนอกชิ้น

### ผลลัพธ์ที่คาดหวัง

เมื่อเปิดเอกสารที่สร้างขึ้น คุณควรเห็น:

* แผนภูมิวงกลมเดียว ขนาด 400 × 300 pt  
* สี่ชิ้น (หรือจำนวนจุดที่คุณเพิ่ม)  
* ป้ายเปอร์เซ็นต์เช่น “40 %”, “30 %” ฯลฯ แสดงอยู่ด้านนอกแต่ละชิ้น  

หากป้ายแสดงอยู่ด้านในชิ้น ให้ตรวจสอบว่าตั้งค่า `ChartDataLabelPosition.OutsideEnd` ถูกต้องหรือไม่

## ขั้นตอนที่ 7: การปรับเปลี่ยนทั่วไปและกรณีขอบ

### เพิ่มหัวเรื่องให้แผนภูมิ

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### เปลี่ยนสีของชิ้นส่วน

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### จัดการกับซีรีส์ที่ว่างเปล่า

หากแหล่งข้อมูลของคุณอาจว่างเปล่า ให้ป้องกัน `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### ส่งออกเป็น PDF แทน Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

ตรรกะการเรนเดอร์แผนภูมิเช่นเดิม; Aspose.Words จะทำการแปลงเลย์เอาต์ Word เป็น PDF โดยอัตโนมัติ

## รายการซอร์สโค้ดเต็ม

ด้านล่างเป็นโปรแกรมที่พร้อมรันทั้งหมด คัดลอกไปยัง `Program.cs` แล้วสั่ง `dotnet run`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## สรุป

ตอนนี้คุณรู้วิธี **สร้างแผนภูมิวงกลม** ในไฟล์ Word ด้วย Aspose.Words, **แทรกแผนภูมิลงใน Word**, **เพิ่มป้ายข้อมูลให้แผนภูมิวงกลม**, และ **แสดงเปอร์เซ็นต์บนแผนภูมิวงกลม** ตัวอย่างนี้สาธิตขั้นตอนทั้งหมด—from ตั้งค่าโปรเจกต์จนถึงเอกสารสุดท้าย—เพื่อให้คุณนำไปปรับใช้ในแดชบอร์ด, รายงาน, หรือการสร้างใบแจ้งหนี้อัตโนมัติ

ต่อไปลองสำรวจหัวข้อที่เกี่ยวข้อง เช่น **วิธีแสดงเปอร์เซ็นต์ในคำอธิบายแผนภูมิ**, การปรับสีแผนภูมิ, หรือการแปลงเอกสาร Word เป็น PDF เพื่อแจกจ่าย ทดลองใช้ประเภทแผนภูมิอื่น (Bar, Line) ด้วยเมธอด `InsertChart` เดียวกันเพื่อขยายความสามารถของการอัตโนมัติของคุณ

ขอให้สนุกกับการสร้างแผนภูมิ!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่นในโปรเจกต์ของคุณ

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}