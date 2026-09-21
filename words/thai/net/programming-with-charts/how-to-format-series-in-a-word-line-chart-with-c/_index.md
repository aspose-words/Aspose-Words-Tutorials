---
category: general
date: 2026-09-21
description: วิธีจัดรูปแบบซีรีส์ในแผนภูมิเส้นของ Word ด้วย C#. เรียนรู้การสร้างเอกสาร
  Word, แทรกแผนภูมิเส้น, และใช้รูปแบบตัวเลขแบบกำหนดเอง.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: th
lastmod: 2026-09-21
og_description: วิธีจัดรูปแบบซีรีส์ในแผนภูมิเส้นของ Word ด้วย C# บทเรียนนี้จะแสดงวิธีสร้างเอกสาร
  Word, แทรกแผนภูมิเส้น, และใช้รูปแบบตัวเลขที่กำหนดเอง.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: วิธีจัดรูปแบบซีรีส์ในแผนภูมิเส้นของ Word ด้วย C# – คู่มือทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: วิธีจัดรูปแบบซีรีส์ในแผนภูมิเส้นของ Word ด้วย C#
url: /th/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีจัดรูปแบบ series ในแผนภูมิเส้นของ Word ด้วย C#

หากคุณต้องการ **how to format series** ในแผนภูมิเส้นของ Word คู่มือนี้จะให้วิธีแก้ที่สมบูรณ์และพร้อมใช้งาน คุณจะได้เห็นวิธี **create a Word document**, **insert line chart**, และ **apply custom number format** กับค่า Y‑values—ทั้งหมดด้วย Aspose.Words for .NET.

การทำงานอัตโนมัติของ Word จะง่ายขึ้นเมื่อคุณเข้าใจโมเดลวัตถุของแผนภูมิ เมื่อจบบทเรียนนี้คุณจะมีไฟล์ Word ที่มีแผนภูมิเส้นโดย series ของข้อมูลจะแสดงเป็นเปอร์เซ็นต์พร้อมทศนิยมสองตำแหน่ง.

## สิ่งที่คุณจะได้ทำ

* สร้างไฟล์ `.docx` ว่างโดยโปรแกรม  
* เพิ่มแผนภูมิเส้นขนาด 400 × 300 points  
* เข้าถึง series ข้อมูลแรกของแผนภูมิ  
* ใช้รหัสรูปแบบ `#,##0.00%` เพื่อให้ค่า Y‑values แสดงเป็นเปอร์เซ็นต์  

ไม่จำเป็นต้องใช้เครื่องมือภายนอกใด ๆ นอกจากแพคเกจ Aspose.Words NuGet

## ข้อกำหนดเบื้องต้น

* .NET 6.0 SDK หรือใหม่กว่า  
* Visual Studio 2022 (หรือ IDE ของ C# ใดก็ได้)  
* Aspose.Words for .NET 23.10 หรือใหม่กว่า – ติดตั้งโดยใช้ `dotnet add package Aspose.Words`.  

โค้ดนี้ทำงานบน Windows, Linux, และ macOS เนื่องจาก Aspose.Words เป็นแบบไม่ขึ้นกับแพลตฟอร์ม

## สร้างเอกสาร Word ด้วย Aspose.Words

ขั้นตอนแรกคือการสร้างอ็อบเจ็กต์ `Document` ซึ่งอ็อบเจ็กต์นี้แทนไฟล์ Word ทั้งหมดในหน่วยความจำ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*ทำไมจึงสำคัญ*: `Document` เป็นจุดเริ่มต้นสำหรับการทำงานกับ Word ทั้งหมด หากไม่มีคุณจะไม่สามารถเพิ่มย่อหน้า ตาราง หรือแผนภูมิได้

## แทรกแผนภูมิเส้นลงในเอกสาร

`DocumentBuilder` เขียนเนื้อหาเข้าไปใน `Document` การเรียก `InsertChart` จะสร้างรูปร่างแผนภูมิบนหน้าปัจจุบัน

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*ทำไมจึงสำคัญ*: `InsertChart` คืนค่าอ็อบเจ็กต์ `Chart` ที่ให้คุณควบคุม series, แกน, และการจัดรูปแบบได้อย่างเต็มที่ พารามิเตอร์ขนาดระบุเป็น points (1 point = 1/72 inch).

## เข้าถึง series ข้อมูลแรก

แต่ละแผนภูมิมีหนึ่งหรือหลาย `ChartSeries` series แรกอยู่ที่ดัชนี 0

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*ทำไมจึงสำคัญ*: อ็อบเจ็กต์ `ChartSeries` เก็บค่า Y‑values, X‑values, และตัวเลือกการจัดรูปแบบสำหรับเส้นเดียวในแผนภูมิเส้น การแก้ไขอ็อบเจ็กต์นี้จะเปลี่ยนการแสดงผลของข้อมูล

## ใช้รูปแบบตัวเลขแบบกำหนดเองกับ series

คุณสมบัติ `FormatCode` ควบคุมการแสดงค่าตัวเลข การตั้งค่าเป็น `#,##0.00%` จะบอก Word ให้แสดงค่าดังกล่าวเป็นเปอร์เซ็นต์พร้อมทศนิยมสองตำแหน่ง

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*ทำไมจึงสำคัญ*: หากไม่มีรูปแบบกำหนดเอง Word จะแสดงตัวเลขทศนิยมดิบ (เช่น `0.15`). รหัสรูปแบบจะแปลงเป็น `15.00%` ซึ่งมักเป็นสิ่งที่รายงานธุรกิจต้องการ

## บันทึกเอกสารและตรวจสอบผลลัพธ์

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

เมื่อคุณเปิด `FormattedSeriesLineChart.docx` ใน Microsoft Word คุณจะเห็นแผนภูมิเส้นที่ป้ายแกน Y แสดงเป็น `15.00%`, `30.00%`, `45.00%`, และ `60.00%`. ขนาดแผนภูมิตรงกับมิติที่ระบุใน `InsertChart`.

### ภาพหน้าจอผลลัพธ์ที่คาดหวัง

> *Image: หน้าเอกสาร Word ที่แสดงแผนภูมิเส้นพร้อมค่าตามเปอร์เซ็นต์บนแกน Y.*  
> *(Alt text: ภาพหน้าจอของเอกสาร Word ที่แสดงแผนภูมิเส้นพร้อมค่าตามเปอร์เซ็นต์บนแกน Y)*

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | การปรับ |
|-----------|------------|
| **Multiple series** | วนลูปผ่าน `chart.Series` และตั้งค่า `FormatCode` สำหรับแต่ละ series. |
| **Different chart type** | แทนที่ `ChartType.Line` ด้วย `ChartType.Column`, `ChartType.Pie` เป็นต้น. |
| **Locale‑specific separators** | ใช้สตริงรูปแบบที่รับรู้ `CultureInfo` เช่น `"# ##0,00 %"` สำหรับภาษาฝรั่งเศส. |
| **Dynamic data source** | เติมค่า `series.YValues` จากฐานข้อมูลหรือไฟล์ CSV ก่อนการตั้งรูปแบบ. |

**เคล็ดลับ:** ควรตั้งรูปแบบ **หลังจาก** ที่คุณได้เพิ่มค่า Y‑values แล้ว การเปลี่ยนรูปแบบก่อนแล้วค่อยเพิ่มค่าก็ทำได้เช่นกัน แต่การตั้งภายหลังจะรับประกันว่ารูปแบบจะถูกใช้กับชุดข้อมูลสุดท้าย

## สรุป

ตอนนี้คุณรู้แล้วว่า **how to format series** ในแผนภูมิเส้นของ Word ด้วย C# บทเรียนได้ครอบคลุม:

* สร้างเอกสาร Word (`create word document`).  
* แทรกแผนภูมิเส้น (`insert line chart`, `add chart to word`).  
* เข้าถึง series แรกของแผนภูมิ.  
* ใช้รูปแบบตัวเลขแบบกำหนดเอง (`apply custom number format`) เพื่อแสดงเป็นเปอร์เซ็นต์.

## ขั้นตอนต่อไป

* ทดลองใช้ค่า `ChartType` ต่าง ๆ เพื่อดูว่าการแสดงผลอื่น ๆ ทำงานอย่างไร.  
* เพิ่มหัวเรื่อง, ป้ายแกน, และคำอธิบายโดยใช้ `chart.Title`, `chart.AxisX.Title`, และ `chart.AxisY.Title`.  
* ส่งออกแผนภูมิเป็นภาพ (`chart.Save` กับ `SaveFormat.Png`) เพื่อใช้ในรายงานเว็บ.

คุณสามารถปรับใช้รูปแบบนี้เพื่อสร้างแดชบอร์ด, รายงานการเงิน, หรือเอกสารใด ๆ ที่ต้องการการสร้างแผนภูมิโดยอัตโนมัติได้ตามต้องการ ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดที่ทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโครงการของคุณ.

- [สร้างแผนภูมิเส้นใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [แทรกแผนภูมิคอลัมน์ในเอกสาร Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [แทรกแผนภูมิพื้นที่ในเอกสาร Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}