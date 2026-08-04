---
category: general
date: 2026-08-04
description: การจัดตำแหน่งป้ายข้อมูลแบบกำหนดเองสำหรับแผนภูมิใน C# ช่วยให้คุณวางป้ายตรงกลางของส่วนของแผนภูมิได้
  ปฏิบัติตามคู่มือขั้นตอนต่อขั้นตอนนี้โดยใช้ Aspose.Words chart API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: th
lastmod: 2026-08-04
og_description: การจัดตำแหน่งป้ายข้อมูลแบบกำหนดเองสำหรับแผนภูมิใน C# แสดงวิธีการจัดศูนย์ป้ายข้อมูลทั้งหมดบนแต่ละส่วนของแผนภูมิ
  Word. เชี่ยวชาญการวางตำแหน่งป้ายข้อมูลแผนภูมิด้วย Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: การจัดตำแหน่งป้ายข้อมูลแบบกำหนดเองสำหรับแผนภูมิใน C# – คู่มือขั้นตอนโดยละเอียด
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: การจัดตำแหน่งป้ายข้อมูลแบบกำหนดเองสำหรับแผนภูมิใน C#
url: /th/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การวางตำแหน่ง Data‑Label แบบกำหนดเองสำหรับแผนภูมิใน C#

**Custom Data‑Label Placement for Charts** ช่วยให้คุณควบคุมตำแหน่งที่แต่ละป้ายแสดงบนแผนภูมิในเอกสาร Word ได้อย่างแม่นยำ ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีการจัดศูนย์ป้ายข้อมูลทั้งหมดบนแต่ละส่วนโดยใช้ C# และ Aspose.Words chart API.

คุณจะได้รับตัวอย่างที่สมบูรณ์และสามารถรันได้ ซึ่งโหลดไฟล์ `.docx` เข้าถึงรูปแผนภูมิแรก เปลี่ยน `Position` ของทุกป้ายเป็น `Center` แล้วบันทึกเอกสารที่อัปเดต ไม่จำเป็นต้องอ้างอิงภายนอก—เพียงแค่ไลบรารี Aspose.Words for .NET และสภาพแวดล้อมการพัฒนา C# เบื้องต้น.

**What you’ll learn**

* วิธีโหลดเอกสาร Word ที่มีแผนภูมิ  
* วิธีค้นหารูปแผนภูมิด้วย Aspose.Words chart API  
* วิธีใช้ **chart data label positioning** กับทุกซีรีส์ในแผนภูมิ  
* วิธีบันทึกเอกสารเพื่อให้ป้ายที่จัดศูนย์แสดงใน Word  

**Prerequisites**

* .NET 6.0 (หรือใหม่กว่า) ที่ติดตั้งแล้ว  
* Visual Studio 2022 (หรือ IDE C# ใดก็ได้)  
* การอ้างอิงแพ็กเกจ NuGet `Aspose.Words`  
* ไฟล์ Word (`Chart.docx`) ที่มีอย่างน้อยหนึ่งแผนภูมิ

---

## การวางตำแหน่ง Data‑Label แบบกำหนดเองสำหรับแผนภูมิ – ขั้นตอนที่ 1: โหลดเอกสาร

การกระทำแรกคือการเปิดไฟล์ Word ที่บรรจุแผนภูมิ `Document` เป็นจุดเริ่มต้นสำหรับการจัดการใด ๆ ด้วย Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*ทำไมขั้นตอนนี้สำคัญ*: หากไม่ได้โหลดเอกสารคุณจะไม่สามารถเข้าถึงอ็อบเจกต์แผนภูมิได้ การตรวจสอบทำให้คุณได้รับข้อผิดพลาดที่ชัดเจนหากไฟล์ไม่มีแผนภูมิ ป้องกันการอ้างอิงค่า null ในภายหลัง.

## การใช้ Aspose.Words chart API เพื่อเข้าถึงรูปแผนภูมิ

Aspose.Words ถือว่าแผนภูมิเป็นอ็อบเจกต์ `Chart` ที่ซ้อนอยู่ภายใน `Shape` คุณสามารถดึงมันออกมาได้โดยการแคสต์โหนดลูกที่เหมาะสม.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*ทำไมขั้นตอนนี้สำคัญ*: การเข้าถึง `Chart` โดยตรงให้คุณควบคุมซีรีส์ จุดข้อมูล และคุณสมบัติป้ายได้อย่างเต็มที่ หากรูปไม่ใช่แผนภูมิ โค้ดจะหยุดทำงานเร็ว ๆ พร้อมข้อความแจ้งที่มีประโยชน์.

## การตั้งค่าการวางตำแหน่งป้ายข้อมูลของแผนภูมิใน C#

ตอนนี้ให้วนลูปผ่านทุกซีรีส์และทุกป้ายข้อมูล ตั้งค่า `Position` เป็น `Center` นี่คือหัวใจของ **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**เคล็ดลับ**: หากคุณต้องการตำแหน่งอื่น (เช่น `InsideEnd` สำหรับแผนภูมิคอลัมน์) ให้เปลี่ยนค่า enum ตามต้องการ `ChartDataLabelPosition` enum ครอบคลุมตำแหน่งมาตรฐานทั้งหมดที่ Word รองรับ.

*ทำไมขั้นตอนนี้สำคัญ*: การเปลี่ยน `label.Position` จะอัปเดตการแสดงผล OOXML ด้านล่าง ทำให้ป้ายแสดงศูนย์กลางเมื่อเปิดเอกสารใน Microsoft Word.

## การบันทึกเอกสาร Word พร้อมป้ายที่อัปเดต

หลังจากแก้ไขแผนภูมิแล้ว ให้บันทึกการเปลี่ยนแปลงกลับไปยังไฟล์ คุณสามารถเขียนทับไฟล์เดิมหรือสร้างสำเนาใหม่ได้.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*ทำไมขั้นตอนนี้สำคัญ*: การบันทึกจะเขียน OOXML ที่อัปเดตลงดิสก์ การเปิด `ChartLabelsCentered.docx` ใน Word จะทำให้ป้ายของแต่ละส่วนแสดงศูนย์กลาง ยืนยันว่า **Custom Data‑Label Placement for Charts** สำเร็จ.

## กรณีขอบและความแตกต่าง

| สถานการณ์ | วิธีจัดการ |
|-----------|---------------|
| **หลายแผนภูมิ** ในเอกสารเดียวกัน | วนลูป `doc.GetChildNodes(NodeType.Shape, true)` และตรวจสอบ `shape.HasChart` สำหรับแต่ละรูป |
| **ประเภทแผนภูมิต่าง ๆ** (pie, doughnut, bar) | `ChartDataLabelPosition.Center` ทำงานได้กับแผนภูมิประเภท pie เช่นกัน สำหรับแผนภูมิแท่ง/คอลัมน์คุณอาจเลือก `InsideEnd` หรือ `OutsideEnd` |
| **ข้อความป้ายต้องการการจัดรูปแบบ** | เข้าถึง `label.TextProperties` เพื่อกำหนดขนาดฟอนต์, สี หรือความหนา |
| **ทำงานบน .NET Core** | ตรวจสอบว่าคุณอ้างอิงเวอร์ชัน .NET Standard ของ Aspose.Words; API จะเหมือนกัน |

## ตัวอย่างการทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในแอปพลิเคชันคอนโซลได้ รวมถึงคำสั่ง `using` ที่จำเป็นทั้งหมดและการจัดการข้อผิดพลาด

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**ผลลัพธ์ที่คาดหวัง**: เปิด `ChartLabelsCentered.docx` ใน Microsoft Word แต่ละส่วนของแผนภูมิจะโชว์ป้ายข้อมูลตรงกลางของส่วนนั้น ทำให้ภาพรวมดูสะอาดตายิ่งขึ้น.

## สรุป

ตอนนี้คุณมีโซลูชัน **Custom Data‑Label Placement for Charts** ครบถ้วนใน C# ด้วยการโหลดเอกสาร, เข้าถึงแผนภูมิผ่าน Aspose.Words chart API, ตั้งค่า `ChartDataLabelPosition.Center` ให้กับทุกป้าย, และบันทึกไฟล์ คุณสามารถทำให้การวางตำแหน่งป้ายเป็นอัตโนมัติสำหรับแผนภูมิใด ๆ ใน Word

ต่อไปสำรวจตัวเลือก **chart data label positioning** อื่น ๆ เช่น `InsideEnd` หรือ `OutsideEnd` หรือทดลอง **C# chart manipulation** เพื่อเปลี่ยนสี, เพิ่มคำอธิบาย, หรือสร้างแผนภูมิตั้งแต่ต้น ส่วนขยายเหล่านี้ต่อเนื่องจากเทคนิคที่อธิบายไว้และขยายทักษะการทำอัตโนมัติแผนภูมิในเอกสาร Word ของคุณ ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโครงการของคุณ

- [ปรับแต่ง Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [จัดรูปแบบ Number Of Data Label ในแผนภูมิ](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}