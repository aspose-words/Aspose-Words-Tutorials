---
category: general
date: 2026-10-13
description: เรียนรู้วิธีปรับแต่งป้ายชื่อแผนภูมิในเอกสาร Word อย่างเป็นโปรแกรมด้วย
  C# คู่มือนี้ครอบคลุมการจัดการแผนภูมิด้วย Aspose.Words และการจัดแนวป้ายชื่อ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: th
lastmod: 2026-10-13
og_description: ปรับตำแหน่งป้ายแผนภูมิในเอกสาร Word ด้วย C# อย่างอัตโนมัติ ทำตามบทเรียนฉบับเต็มนี้เพื่อเปลี่ยนตำแหน่งป้าย,
  การจัดแนว, และอื่น ๆ.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: ปรับป้ายแผนภูมิใน Word โดยอัตโนมัติ – คู่มือขั้นตอน C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: ปรับป้ายแผนภูมิในเอกสาร Word ด้วย C# อย่างอัตโนมัติ
url: /th/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ปรับตำแหน่งป้ายชื่อแผนภูมิในไฟล์ Word ด้วย C# อย่างอัตโนมัติ

หากคุณต้องการ **ปรับตำแหน่งป้ายชื่อแผนภูมิอย่างอัตโนมัติ** ในไฟล์ Word คำแนะนำนี้จะแสดงวิธีทำด้วย C# อย่างละเอียด ไม่ว่าคุณจะสร้างรายงานอัตโนมัติ, ทำแดชบอร์ด, หรือปรับแต่งเทมเพลต คุณจะได้เห็นตัวอย่างเต็มที่สามารถรันได้ซึ่งเปลี่ยนตำแหน่งและการจัดแนวของป้ายชื่อแผนภูมิภายในไฟล์ .docx

คุณยังจะได้เรียนรู้วิธีใช้เทคนิค **Aspose.Words chart manipulation**, จัดการหลายซีรีส์, และหลีกเลี่ยงข้อผิดพลาดทั่วไปเมื่อทำงานกับอ็อบเจ็กต์ **C# chart data label** 

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ให้แน่ใจว่าคุณมี:

* .NET 6.0 (หรือใหม่กว่า) ติดตั้งแล้ว  
* Visual Studio 2022 (หรือ IDE สำหรับ C# ใดก็ได้)  
* แพคเกจ NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* ไฟล์ Word (`input.docx`) ที่มีแผนภูมิอย่างน้อยหนึ่งอัน  

สิ่งเหล่านี้จำเป็นสำหรับ **Word document chart example** ที่เราจะทำการแก้ไข

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า namespace

สร้างโปรเจกต์คอนโซลใหม่และเพิ่ม `using` directives ที่จำเป็น ซึ่งจะเตรียมสภาพแวดล้อมสำหรับ **programmatically adjust chart labels**  

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*ทำไมต้องทำขั้นตอนนี้?*  
การโหลดเอกสารจะทำให้คุณเข้าถึง **Word document chart example** tree ภายใน ซึ่งแผนภูมิถูกเก็บเป็นโหนดรูปทรง (shape nodes)

## ขั้นตอนที่ 2: ค้นหา shape ของแผนภูมิแรก

แผนภูมิถูกเก็บเป็นโหนด `Shape` โค้ดต่อไปนี้จะดึงแผนภูมิแรกในเอกสาร ซึ่งเป็นเป้าหมายสำหรับการปรับป้ายชื่อของเรา  

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*ทำไมต้องทำขั้นตอนนี้?*  
เมธอด `GetChild` ค้นหาแบบเรียกซ้ำ (`true`) และคืนค่าโหนดแรกที่เป็นประเภท `Shape` การแคสต์เป็น `Chart` ทำให้เราสามารถใช้ API เฉพาะของแผนภูมิได้

## ขั้นตอนที่ 3: เข้าถึงป้ายชื่อข้อมูลที่ต้องการแก้ไข

แต่ละซีรีส์ในแผนภูมิมีคอลเลกชันของป้ายชื่อข้อมูล สำหรับแผนภูมิแบบง่าย ป้ายชื่อแรกมักเพียงพอ โค้ดด้านล่างแสดงวิธีเข้าถึงมัน  

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*ทำไมต้องทำขั้นตอนนี้?*  
`ChartSeries` แทนซีรีส์ของจุดข้อมูล `DataLabelCollection` เก็บป้ายชื่อของซีรีส์นั้น ทำให้เราควบคุมการวางตำแหน่งและการจัดแนวได้อย่างแม่นยำ

## ขั้นตอนที่ 4: เปลี่ยนตำแหน่งและการจัดแนวของป้ายชื่อ

ตอนนี้เราจะ **programmatically adjust chart labels** โดยตั้งค่าตำแหน่ง, การจัดแนวนอน, และการจัดแนวแนวตั้ง คุณสมบัติเหล่านี้สอดคล้องกับตัวเลือกที่คุณเห็นใน UI ของ Word  

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*ทำไมต้องตั้งค่าเหล่านี้?*  

* `OutsideEnd` วางป้ายชื่อไว้ด้านนอกปลายของแต่ละแท่งหรือคอลัมน์ ทำให้อ่านง่ายขึ้น  
* `HorizontalAlignment.Center` ทำให้ข้อความอยู่กึ่งกลางจุดข้อมูล ส่วน `VerticalAlignment.Top` จัดแนวด้านบนของป้ายชื่อให้ตรงกับจุดข้อมูล ลดการทับซ้อนกับองค์ประกอบอื่น

### เคล็ดลับพิเศษ
หากแผนภูมิมีหลายซีรีส์ ให้วนลูปผ่าน `chart.Series` และใช้การตั้งค่าเดียวกันกับแต่ละ `DataLabelCollection` เพื่อให้แผนภูมิทั้งหมดดูสอดคล้องกัน  

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## ขั้นตอนที่ 5: บันทึกเอกสารที่แก้ไขแล้ว

หลังจากปรับป้ายชื่อเสร็จแล้ว ให้บันทึกการเปลี่ยนแปลงลงไฟล์ใหม่ ซึ่งเป็นขั้นตอนสุดท้ายของกระบวนการ **modify chart label position**  

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

เมื่อคุณเปิด `output.docx` คุณจะเห็นว่าป้ายชื่อของทุกแผนภูมิได้ย้ายไปที่ปลายนอกของจุดข้อมูล, จัดกึ่งกลางแนวนอนและจัดแนวบนแนวตั้งแล้ว

## กรณีขอบและความแปรผัน

| สถานการณ์ | สิ่งที่ควรระวัง | วิธีการแนะนำ |
|-----------|-------------------|----------------------|
| **หลายแผนภูมิ** ในเอกสารเดียว | `GetChild` คืนค่าแค่แผนภูมิแรก | ใช้ `doc.GetChildNodes(NodeType.Shape, true)` เพื่อวนลูปผ่าน shape ของแผนภูมิทั้งหมด |
| **ซีรีส์ที่ไม่มีป้ายชื่อข้อมูล** | `DataLabelCollection` อาจว่างเปล่า | ตรวจสอบ `series.HasDataLabels` ก่อนเข้าถึงคอลเลกชัน |
| **ประเภทแผนภูมิต่างกัน** (pie, line, scatter) | ไม่ใช่ค่าทุกค่าใน `DataLabelPosition` ที่ใช้ได้ | ใช้ `DataLabelPosition.Auto` สำหรับแผนภูมิที่ต้องการให้ระบบกำหนดตำแหน่งอัตโนมัติ |
| **การแปลภาษา** | ค่าคงที่การจัดแนวเป็นภาษากลาง แต่ข้อความที่แสดงอาจต้องการการสนับสนุนจากขวาไปซ้าย | ตั้งค่า `dataLabel.TextDirection` หากต้องการภาษา RTL |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมทั้งหมดที่คุณสามารถคัดลอก, วาง, และรันได้ แทนที่ `YOUR_DIRECTORY` ด้วยพาธโฟลเดอร์จริงของคุณ  

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** การเปิด `output.docx` จะเห็นแต่ละป้ายชื่อแผนภูมิอยู่ด้านนอกจุดข้อมูล, จัดกึ่งกลางแนวนอน, และจัดแนวบนแนวตั้ง — ผลลัพธ์ของ **programmatically adjust chart labels** ที่คุณเขียนโค้ดไว้

## สรุป

ตอนนี้คุณรู้วิธี **programmatically adjust chart labels** ในไฟล์ Word ด้วย C# แล้ว คำแนะนำนี้ครอบคลุม:

* การโหลดเอกสารด้วย **Aspose.Words chart manipulation**  
* การเข้าถึง **C# chart data label**  
* การเปลี่ยน **modify chart label position** และการจัดแนว  
* การบันทึกไฟล์และการจัดการกับกรณีขอบทั่วไป  

ต่อจากนี้คุณสามารถสำรวจสถานการณ์ขั้นสูงเพิ่มเติม เช่น การปรับฟอนต์ของป้ายชื่อ, การเพิ่มการจัดรูปแบบตามเงื่อนไข, หรือการอัปเดตหลายแผนภูมิพร้อมกันในกระบวนการแบตช์ ลองทดลองกับตัวเลือก `DataLabelPosition` ต่าง ๆ เพื่อหาสไตล์ที่เหมาะกับรายงานของคุณที่สุด

---

*พร้อมที่จะยกระดับกระบวนการรายงานอัตโนมัติของคุณหรือยัง? ลองเพิ่มรูปแบบตัวเลขแบบกำหนดเองให้กับป้ายชื่อหรือส่งออกแผนภูมิเป็นภาพเพื่อนำไปใช้ใน PDF*


## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้เกี่ยวกับหัวข้อที่ใกล้เคียงและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}