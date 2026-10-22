---
category: general
date: 2026-09-05
description: สร้างแผนภูมิเรดาร์ใน Word ด้วย C#. เรียนรู้วิธีสร้างเอกสาร Word เปล่า,
  เพิ่มแผนภูมิเรดาร์, ตั้งขนาดแผนภูมิ, และเปิดใช้งานเครื่องหมายติกอย่างรวดเร็ว.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: th
lastmod: 2026-09-05
og_description: สร้างแผนภูมิเรดาร์ใน Word ด้วย C# คู่มือนี้จะแสดงวิธีสร้างเอกสาร Word
  เปล่า, เพิ่มแผนภูมิเรดาร์, ตั้งขนาดแผนภูมิ, และเปิดใช้งานเครื่องหมายบ่งชี้—ทั้งหมดในไม่กี่นาที.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: สร้างแผนภูมิเรดาร์ใน Word – คู่มือ C# ทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: วิธีสร้างแผนภูมิเรดาร์และเพิ่มแผนภูมิลงใน Word ด้วย C#
url: /th/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างแผนภูมิเรดาร์และเพิ่มแผนภูมิลงใน Word ด้วย C#

หากคุณต้องการ **create radar chart** ภายในไฟล์ Word คำแนะนำนี้จะพาคุณผ่านกระบวนการทั้งหมด คุณจะได้เรียนรู้วิธี **generate blank word document**, แทรกแผนภูมิเรดาร์, **set chart size word**, และเปิดการแสดงระดับแกน—ทั้งหมดด้วยไม่กี่บรรทัดของโค้ด C#  

การเพิ่มข้อมูลภาพลงในรายงานเป็นความต้องการทั่วไป และการใช้ Aspose.Words ทำให้ทำได้อย่างง่ายดาย ในขั้นตอนต่อไปนี้เรายังครอบคลุมวิธี **add chart to word** เอกสารโดยโปรแกรม เพื่อให้คุณสามารถอัตโนมัติแดชบอร์ด สรุปการเงิน หรือเนื้อหาที่ขับเคลื่อนด้วยข้อมูลใด ๆ  

## ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า ติดตั้งแล้ว  
* ใบอนุญาต Aspose.Words for .NET (หรือทดลองใช้ฟรี) – ไลบรารีนี้ให้ `Document`, `DocumentBuilder` และ API ของแผนภูมิที่ใช้ในบทเรียนนี้  
* Visual Studio 2022 (หรือ IDE ของ C# ใดก็ได้)  

> **Pro tip:** หากคุณกำลังทดสอบ ให้วางไฟล์ Aspose.Words DLL ในโฟลเดอร์ `bin` ของโปรเจกต์และอ้างอิงผ่าน NuGet (`Install-Package Aspose.Words`).  

## วิธีสร้างแผนภูมิเรดาร์ในเอกสาร Word

ขั้นตอนแรกคือ **generate blank word document** ที่จะเป็นที่เก็บแผนภูมิ ซึ่งจะให้คุณมีพื้นที่ว่างสะอาดและให้คุณควบคุมเมตาดาต้าของเอกสารก่อนที่จะเพิ่มเนื้อหาใด ๆ  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*ทำไมสิ่งนี้ถึงสำคัญ:* วัตถุ `Document` ที่ว่างเปล่าช่วยให้ไม่มีสไตล์หรือส่วนที่ซ่อนอยู่แทรกแซงการจัดวางแผนภูมิ นอกจากนี้ยังทำให้คุณตั้งค่าคุณสมบัติของเอกสาร (ผู้เขียน, ชื่อเรื่อง) ได้ในภายหลังหากต้องการ  

## วิธีเพิ่มแผนภูมิลงใน Word ด้วย Aspose.Words

ต่อไป สร้าง `DocumentBuilder` ตัวสร้างนี้เป็นหัวใจหลักที่ช่วยให้คุณแทรกข้อความ, รูปภาพ, และแผนภูมิลงในเอกสาร  

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

ตอนนี้คุณสามารถ **add radar chart** ได้โดยตรงที่ตำแหน่งเคอร์เซอร์ วิธี `InsertChart` รับค่า enum `ChartType`, ความกว้างและความสูงเป็นหน่วย points  

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*ทำไม 400 × 300?* ขนาดนี้ทำให้แผนภูมิดูชัดเจนและอ่านง่ายบนหน้า A4 มาตรฐาน คุณสามารถปรับขนาดภายหลังด้วยขั้นตอน **set chart size word** หากการจัดวางของคุณต้องการอัตราส่วนที่ต่างออกไป  

## การตั้งค่าขนาดแผนภูมิใน Word

หากคุณต้องการปรับขนาดอย่างละเอียดหลังจากแทรกแล้ว คุณสามารถแก้ไขคุณสมบัติ `Width` และ `Height` ของแผนภูมิได้ ซึ่งมีประโยชน์เมื่อข้อความรอบข้างหรือขอบหน้ากำหนดสมดุลภาพที่แตกต่าง  

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Note:** การ overload ของ `InsertChart` ได้ตั้งค่าขนาดแล้ว ดังนั้นโค้ดด้านบนเป็นทางเลือกและแสดงเพื่อความครบถ้วน  

## เปิดการแสดงเครื่องหมายติ๊กบนแกนรัศมี

แผนภูมิเรดาร์จะมีประโยชน์สูงสุดเมื่อแกนรัศมีแสดงการแบ่งระดับที่ชัดเจน การตั้งค่าต่อไปนี้จะเปิดเครื่องหมายติ๊กและกำหนดช่วงเป็น 30 องศา ซึ่งสอดคล้องกับการแสดงผลแบบเข็มทิศทั่วไป  

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*ทำไมสิ่งนี้ถึงสำคัญ:* การแบ่งระดับช่วยให้ผู้อ่านประเมินค่าที่แต่ละมุมได้ง่ายขึ้น เพิ่มความอ่านง่ายสำหรับผู้มีส่วนได้ส่วนเสียที่ไม่คุ้นเคยกับข้อมูล  

## บันทึกเอกสารที่มีแผนภูมิ

สุดท้าย ให้เขียนเอกสารลงดิสก์ คุณสามารถเลือกโฟลเดอร์ใดก็ได้; เพียงตรวจสอบให้แน่ใจว่าเส้นทางมีอยู่  

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

เมื่อคุณเปิด `RadialChart.docx` ใน Microsoft Word คุณจะเห็นแผนภูมิเรดาร์ที่แสดงผลเต็มรูปแบบอยู่กึ่งกลางหน้า มีขนาดตามที่ระบุและมีเครื่องหมายติ๊กทุก 30 องศา  

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ `.docx` ชื่อ **RadialChart.docx**  
* หน้าที่หนึ่งมีแผนภูมิเรดาร์ขนาด 400 × 300 points  
* แกน X (แกนรัศมี) แสดงเครื่องหมายติ๊กที่ 0°, 30°, 60°, …, 330°  

คุณสามารถแทนที่ชุดข้อมูลตัวอย่างด้วยค่าของคุณเองโดยเข้าถึง `radarChart.Series` – แต่สิ่งนั้นอยู่นอกขอบเขตของบทเรียนพื้นฐาน **add radar chart** นี้  

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | การปรับเปลี่ยน |
|----------|------------|
| **ประเภทแผนภูมิที่แตกต่าง** | แทนที่ `ChartType.Radar` ด้วย `ChartType.Column`, `ChartType.Pie` เป็นต้น |
| **หลายแผนภูมิ** | เรียก `InsertChart` ซ้ำหลายครั้ง; แต่ละครั้งจะวางแผนภูมิใหม่หลังจากแผนภูมิก่อนหน้า |
| **ชุดข้อมูลขนาดใหญ่** | ใช้ `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` เพื่อเติมหลายจุดข้อมูล |
| **บันทึกเป็น PDF** | เรียก `document.Save("RadialChart.pdf", SaveFormat.Pdf);` หลังจากเพิ่มแผนภูมิ |
| **รันบน .NET Core** | ตรวจสอบว่าคุณอ้างอิงแพ็กเกจ `Aspose.Words.NETCore`; การใช้ API เหมือนกัน |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปพลิเคชันคอนโซลได้ รวมทุกขั้นตอน การปรับขนาดแบบเลือกใช้ และคอมเมนต์เพื่อความชัดเจน  

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

รันโปรแกรม เปิดไฟล์ที่ได้ และคุณจะเห็นแผนภูมิเรดาร์ตรงตามที่อธิบาย  

## สรุป

ตอนนี้คุณรู้วิธี **create radar chart** และ **add chart to Word** เอกสารด้วย C# บทเรียนได้ครอบคลุมการสร้าง **blank word document**, การแทรกแผนภูมิเรดาร์, **set chart size word**, และการเปิดการแสดงระดับแกน ด้วยพื้นฐานนี้คุณสามารถขยายโซลูชันไปยังหลายแผนภูมิ, ชุดข้อมูลที่กำหนดเอง, หรือส่งออกเป็น PDF  

### ขั้นตอนต่อไป

* สำรวจประเภทแผนภูมิอื่น ๆ ด้วย `ChartType` (เช่น `Bar`, `Line`) – ดูคีย์เวิร์ด **add radar chart** สำหรับตัวอย่างที่เกี่ยวข้อง  

## สิ่งที่คุณควรเรียนต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการนำไปใช้แบบอื่นในโครงการของคุณ  

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}