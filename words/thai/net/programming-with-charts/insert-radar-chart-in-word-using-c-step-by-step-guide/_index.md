---
category: general
date: 2026-09-14
description: แทรกแผนภูมิเรดาร์ใน Word ด้วย C# เรียนรู้วิธีตั้งชื่อแผนภูมิ, เพิ่มหลายชุดข้อมูล,
  และสร้างแผนภูมิโดยเขียนโค้ดเพียงไม่กี่บรรทัด.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: th
lastmod: 2026-09-14
og_description: แทรกแผนภูมิเรดาร์ใน Word ด้วย C# บทเรียนนี้แสดงวิธีตั้งชื่อแผนภูมิ,
  เพิ่มหลายชุดข้อมูล, และสร้างแผนภูมิโดยโปรแกรมมิ่ง
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: แทรกแผนภูมิเรดาร์ใน Word ด้วย C# – คู่มือการเขียนโปรแกรมอย่างรวดเร็ว
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: แทรกแผนภูมิเรดาร์ใน Word ด้วย C# – คู่มือแบบทีละขั้นตอน
url: /th/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรก radar chart ใน Word ด้วย C# – คู่มือแบบขั้นตอน

หากคุณต้องการ **insert radar chart** ลงในเอกสาร Word, คู่มือนี้จะแสดงวิธีทำโดยใช้ C# อย่างโปรแกรมเมติก คุณจะได้เรียนรู้วิธี **set chart title**, เพิ่ม **multiple series radar chart**, และบันทึกไฟล์โดยไม่ต้องออกจาก IDE ของคุณ

บทแนะนำนี้ครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโปรเจกต์จนถึงการเรียก `doc.Save` สุดท้าย, ดังนั้นคุณสามารถคัดลอก‑วางตัวอย่างเต็มและรันได้ทันที ไม่จำเป็นต้องค้นหาเอกสารภายนอก

## ข้อกำหนดเบื้องต้น

ก่อนเริ่ม, โปรดตรวจสอบว่าคุณมี:

* .NET 6 (หรือใหม่กว่า) ติดตั้งแล้ว
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ประเมินผลชั่วคราว)
* Visual Studio 2022 หรือ IDE C# ใด ๆ ที่คุณชอบ

> **เคล็ดลับ:** หากคุณใช้รุ่นทดลองฟรี, อย่าลืมตั้งค่าใบอนุญาตก่อนการสร้าง `Document` ครั้งแรกเพื่อหลีกเลี่ยงลายน้ำการประเมินผล

## ขั้นตอนที่ 1: Insert radar chart ลงในเอกสาร Word

การดำเนินการแรกคือการสร้าง `Document` ใหม่และ `DocumentBuilder` ตัวสร้างให้คุณเข้าถึงเนื้อหาเอกสารและวาง **radar chart** ตรงที่คุณต้องการได้อย่างแม่นยำ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*ทำไมขั้นตอนนี้ถึงสำคัญ:* `InsertChart` สร้างอ็อบเจ็กต์แผนภูมิที่คุณสามารถกำหนดค่าได้เต็มที่ก่อนบันทึกเอกสาร การใช้ `ChartType.Radar` บอก Word ให้แสดงแผนภูมิเชิงรัศมีแทนคอลัมน์หรือเส้น

## ขั้นตอนที่ 2: Set chart title และ axis graduations

แผนภูมิที่ไม่มีหัวเรื่องอาจทำให้สับสน ที่นี่เราจะ **set chart title** เป็น “Sales Radar” และเปิดใช้งาน graduations บนแกนทั้งสอง (พร้อมใช้งานตั้งแต่ Aspose.Words 24.9 ขึ้นไป)

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*ทำไมขั้นตอนนี้ถึงสำคัญ:* หัวเรื่องให้บริบทกับผู้อ่าน, และ graduations ช่วยเพิ่มความอ่านง่ายโดยแสดงตำแหน่งของแต่ละจุดข้อมูลบนสเกล

## ขั้นตอนที่ 3: Create multiple series for radar chart

**multiple series radar chart** ช่วยให้คุณเปรียบเทียบช่วงเวลาต่าง ๆ ข้างเคียงกัน ด้านล่างเราจะเพิ่มสอง series — Q1 และ Q2 — แต่ละ series มีสามจุดข้อมูล

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*ทำไมขั้นตอนนี้ถึงสำคัญ:* การเพิ่มหลาย series แสดงวิธีเปรียบเทียบชุดข้อมูลบน radar เดียวกัน, ซึ่งเป็นความต้องการทั่วไปสำหรับการขาย, ประสิทธิภาพ, หรือผลสำรวจ

## ขั้นตอนที่ 4: Save the Word document programmatically

สุดท้าย, คุณจะ **create chart programmatically** และบันทึกเอกสารลงดิสก์ วิธี `Save` จะเขียนไฟล์ `.docx` ที่สามารถเปิดด้วย Microsoft Word

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

เมื่อคุณเปิด `RadialGraduations.docx`, คุณจะเห็น radar chart ที่มีหัวเรื่อง “Sales Radar” พร้อมสอง series (Q1 และ Q2) plotted against เดือน Jan‑Mar

### ผลลัพธ์ที่คาดหวัง

![Radar chart in Word](https://example.com/radar-chart.png){: .align-center alt="เอกสาร Word แสดง radar chart พร้อมสองชุดข้อมูล"}

ภาพหน้าจอ (หรือไฟล์จริง) ยืนยันว่าแผนภูมิถูกแทรก, ตั้งหัวเรื่อง, และเติมข้อมูลอย่างถูกต้อง

## ตัวอย่างเต็มที่สามารถรันได้

รวมทุกอย่างเข้าด้วยกัน, นี่คือโปรแกรมอิสระที่คุณสามารถคอมไพล์และรันได้:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

รันโปรแกรม, เปิดไฟล์ที่สร้างขึ้น, และตรวจสอบว่าการ **insert radar chart** ทำงานสำเร็จ

## คำถามทั่วไป & กรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ฉันสามารถเปลี่ยนประเภทแผนภูมิหลังจากการแทรกได้หรือไม่?** | ได้ หลังจาก `InsertChart` ให้กำหนด `ChartType` ใหม่ให้กับ `chart.Type` อย่างไรก็ตาม การสร้างแผนภูมิด้วยประเภทที่ถูกต้องตั้งแต่แรกจะมีประสิทธิภาพมากกว่า. |
| **ถ้าฉันต้องการมากกว่าสอง series จะทำอย่างไร?** | เรียก `chart.Series.Add` สำหรับแต่ละ series เพิ่มเติม แผนภูมิจะปรับ legend และสีโดยอัตโนมัติ. |
| **ฉันจะปรับแต่งสีหรือเครื่องหมายอย่างไร?** | ใช้ `chart.Series[i].Format.Fill.ForeColor` สำหรับสีเติมและ `chart.Series[i].Marker` สำหรับสไตล์เครื่องหมาย. |
| **API นี้เข้ากันได้กับ .NET Framework หรือไม่?** | โค้ดเดียวกันทำงานกับ .NET Framework 4.7+; เพียงแค่อ้างอิง Aspose.Words DLL ที่เหมาะสม. |
| **ถ้าฉันใช้ Aspose.Words เวอร์ชันเก่า จะทำอย่างไร?** | Graduations (`HasGraduations`) ถูกเพิ่มในเวอร์ชัน 24.9 สำหรับเวอร์ชันเก่ากว่า คุณสามารถเพิ่มเส้นกริดด้วยตนเองโดยใช้ `chart.AxisX.MajorGridLines` และ `chart.AxisY.MajorGridLines`. |

## สรุป

คุณตอนนี้รู้วิธี **insert radar chart** ลงในเอกสาร Word ด้วย C#, **set chart title**, เพิ่ม **multiple series radar chart**, และ **create the chart programmatically** โซลูชันแบบครบวงจรนี้ช่วยให้คุณอัตโนมัติการรายงาน, แดชบอร์ด, หรือสถานการณ์ใด ๆ ที่ต้องการการเปรียบเทียบภาพของหมวดหมู่

ต่อไป, สำรวจหัวข้อที่เกี่ยวข้องเช่น **customizing chart colors**, **exporting charts as images**, หรือ **embedding charts in PDF files** ทดลองกับชุดข้อมูลต่าง ๆ เพื่อดูว่า radar visualization ปรับตัวอย่างไร

ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโปรเจกต์ของคุณเอง

- [แทรกแผนภูมิคอลัมน์ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [แทรกแผนภูมิบับเบิลใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [แทรกแผนภูมิพื้นที่ในเอกสาร Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}