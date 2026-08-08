---
category: general
date: 2026-08-07
description: สร้างแผนภูมิวงกลมใน C# อย่างรวดเร็ว เรียนรู้วิธีแทรกแผนภูมิวงกลม, เพิ่มป้ายข้อมูลในแผนภูมิวงกลม,
  แสดงเปอร์เซ็นต์ของแผนภูมิ, และปรับแต่งป้ายข้อมูลของแผนภูมิ
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: th
lastmod: 2026-08-07
og_description: สร้างแผนภูมิวงกลมใน Word ด้วย C# และ Aspose.Words บทเรียนนี้แสดงวิธีแทรกแผนภูมิวงกลม,
  เพิ่มป้ายข้อมูลบนแผนภูมิวงกลม, และแสดงเปอร์เซ็นต์บนแผนภูมิพร้อมการปรับแต่งป้ายข้อมูลของแผนภูมิ
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: สร้างแผนภูมิวงกลม Word ใน C# – บทเรียนฉบับเต็ม
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: สร้างแผนภูมิวงกลมใน Word ด้วย C# – คู่มือแบบขั้นตอนต่อขั้นตอน
url: /th/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างแผนภูมิวงกลมใน Word ด้วย C# – คู่มือขั้นตอนโดยละเอียด

หากคุณต้องการ **สร้างแผนภูมิวงกลมใน Word** ด้วย C# คำแนะนำนี้จะให้โซลูชันที่พร้อมใช้งานและทำงานได้ทันที คุณจะได้เรียนรู้วิธี **แทรกแผนภูมิวงกลม**, **เพิ่มป้ายข้อมูลในแผนภูมิวงกลม**, และ **แสดงเปอร์เซ็นต์บนแผนภูมิ** พร้อมกับ **ปรับแต่งป้ายข้อมูลของแผนภูมิ** เพื่อให้ได้ผลลัพธ์ที่ดูเป็นมืออาชีพ

การสร้างแผนภูมิโดยอัตโนมัติช่วยลดการแก้ไขด้วยมือ โดยเฉพาะเมื่อจำเป็นต้องสร้างรายงานหรือแดชบอร์ดโดยอัตโนมัติ ในส่วนต่อไปนี้คุณจะได้เรียนรู้ทุกอย่างที่จำเป็นเพื่อฝังแผนภูมิวงกลมที่มีป้ายข้อมูลครบถ้วนลงในไฟล์ Word ด้วย Aspose.Words for .NET

## ข้อกำหนดเบื้องต้นและการตั้งค่า

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า  
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ทดลองใช้ชั่วคราว)  
* Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ C#)  

เพิ่มแพคเกจ NuGet ของ Aspose.Words ลงในโปรเจกต์ของคุณ:

```bash
dotnet add package Aspose.Words
```

> **เคล็ดลับ:** หากคุณวางแผนจะสร้างแผนภูมิหลาย ๆ ชิ้น ให้เปิดใช้งานโหมด **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) เพื่อเพิ่มประสิทธิภาพ

## สร้างแผนภูมิวงกลมใน Word ด้วย Aspose.Words

ขั้นตอนแรกคือการสร้างเอกสาร Word เปล่าและ `DocumentBuilder` ซึ่งอ็อบเจกต์นี้จะเป็นตัวขับเคลื่อนการแทรกทั้งหมดต่อไป

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*ทำไมจึงสำคัญ*: `Document` แทนไฟล์ `.docx` ทั้งหมด ส่วน `DocumentBuilder` ให้ API แบบ fluent เพื่อเพิ่มย่อหน้า ตาราง และแผนภูมิ การเริ่มต้นด้วยเอกสารที่สะอาดช่วยป้องกันรูปแบบที่ซ่อนอยู่มาขัดขวางการจัดวางแผนภูมิ

## แทรกแผนภูมิวงกลมลงในเอกสาร

ต่อไปเราจะวางแผนภูมิวงกลมขนาดที่ต้องการ เมธอด `InsertChart` จะคืนค่าอ็อบเจกต์ `Chart` ที่เราสามารถกำหนดค่าเพิ่มเติมได้

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*ทำไมจึงสำคัญ*: ธง `ChartType.Pie` บอก Aspose.Words ให้สร้างแผนภูมิวงกลม ความกว้าง (`400`) และความสูง (`300`) ระบุเป็นจุด (points) ทำให้คุณควบคุมพื้นที่แสดงผลได้อย่างแม่นยำ

## เติมข้อมูลให้แผนภูมิ

แผนภูมิวงกลมต้องมีชุดข้อมูลอย่างน้อยหนึ่งชุด ที่นี่เราจะเพิ่มสามประเภท: “Apples”, “Bananas”, และ “Cherries”

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*ทำไมจึงสำคัญ*: การเรียก `AddCategory` แต่ละครั้งจะสร้างส่วนหนึ่งของวงกลม ค่าตัวเลขกำหนดขนาดของส่วน ส่วนป้ายชื่อจะเป็นชื่อประเภทที่แสดงเมื่อเปิดใช้งานป้ายข้อมูล

## เพิ่มป้ายข้อมูลในแผนภูมิวงกลมและแสดงเปอร์เซ็นต์

เพื่อทำให้แผนภูมิมีข้อมูลครบถ้วน เราจะเปิดใช้งานป้ายข้อมูล วางตำแหน่งไว้ด้านนอกส่วน และสั่งให้ Aspose.Words แสดงทั้งชื่อประเภทและเปอร์เซ็นต์

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*ทำไมจึงสำคัญ*: การตั้งค่า `Position` เป็น `OutsideEnd` ช่วยให้อ่านง่ายขึ้น โดยเฉพาะเมื่อส่วนมีขนาดเล็ก การเปิด `ShowCategoryName` และ `ShowPercentage` ตอบสนองความต้องการ **show percentage chart** และ **add data labels pie** อย่างครบถ้วน

## ปรับแต่งป้ายข้อมูลของแผนภูมิเพิ่มเติม (เลือกทำ)

คุณอาจต้องการเปลี่ยนฟอนต์ เพิ่มเส้นเชื่อม หรือซ่อน legend ตัวอย่างโค้ดต่อไปนี้แสดงการปรับแต่งที่พบบ่อย

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*ทำไมจึงสำคัญ*: การปรับลักษณะป้ายข้อมูลทำให้แผนภูมิตรงกับสไตล์ของเอกสาร การลบ legend ช่วยลดความรกเมื่อป้ายข้อมูลบอกข้อมูลครบแล้ว

## บันทึกเอกสารพร้อมแผนภูมิที่ปรับแต่งแล้ว

สุดท้ายให้เขียนเอกสารลงดิสก์ เลือกพาธที่คุณมีสิทธิ์เขียนได้

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

เมื่อคุณเปิดไฟล์ `ChartWithCustomLabels.docx` ใน Microsoft Word คุณจะเห็นแผนภูมิวงกลมที่แต่ละส่วนมีป้ายชื่อแสดงชื่อประเภทและเปอร์เซ็นต์ วางตำแหน่งด้านนอกส่วน และใช้การตั้งค่าฟอนต์ที่กำหนดเอง

### ผลลัพธ์ที่คาดหวัง

| ส่วน      | ค่า   | เปอร์เซ็นต์ | ป้ายที่แสดงใน Word |
|-----------|-------|-------------|----------------------|
| Apples    | 40    | 40 %        | Apples – 40 %       |
| Bananas   | 35    | 35 %        | Bananas – 35 %      |
| Cherries  | 25    | 25 %        | Cherries – 25 %     |

แผนภูมิควรมีลักษณะคล้ายภาพด้านล่าง:

![เอกสาร Word ที่แสดงแผนภูมิวงกลมพร้อมป้ายเปอร์เซ็นต์ด้านนอกแต่ละส่วน](pie-chart-word.png "Create pie chart word example")

*ข้อความ alt ของรูปภาพรวมคีย์เวิร์ดหลักเพื่อ SEO*

## จัดการหลายชุดข้อมูลและกรณีขอบเขต

ตัวอย่างพื้นฐานใช้ชุดข้อมูลเดียวซึ่งเป็นแบบทั่วไปสำหรับแผนภูมิวงกลม หากต้องการแสดงหลายชุดข้อมูล (เช่น เปรียบเทียบสองปี) คุณต้อง:

1. เรียก `chart.Series.Add()` สำหรับแต่ละชุดข้อมูลเพิ่มเติม  
2. ตรวจสอบให้แต่ละชุดใช้ประเภทเดียวกัน มิฉะนั้น Aspose.Words จะโยน `ArgumentException`  
3. หากต้องการแยกแยะส่วน สามารถตั้งค่า `labels.ShowSeriesName = true`

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

เมื่อมีหลายชุดข้อมูล แผนภูมิจะถูกเรนเดอร์อัตโนมัติเป็น **clustered pie** (หรือที่เรียกว่า “pie of pies”) ตรวจสอบผลลัพธ์เพื่อให้แน่ใจว่าป้ายยังอ่านได้ชัดเจน

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| ปัญหา                     | สาเหตุ                                 | วิธีแก้ |
|---------------------------|----------------------------------------|---------|
| ป้ายทับกับส่วน          | พื้นที่แผนภูมิกลางหรือประเภทมากเกินไป | เพิ่มขนาดแผนภูมิ (`InsertChart(width, height)`) หรือเปลี่ยน `Position` เป็น `InsideEnd` |
| เปอร์เซ็นต์ไม่รวมเป็น 100 % | ความคลาดเคลื่อนจากการปัดเศษข้อมูล   | ใช้ `labels.ShowPercentage = true` (Aspose.Words จะทำการปรับให้เป็น 100 % โดยอัตโนมัติ) |
| แผนภูมิแสดงเป็นสีขาวใน Word | ขาดใบอนุญาตหรือหมดเวลาการทดลอง   | ตรวจสอบให้โหลดใบอนุญาต Aspose.Words ที่ถูกต้องก่อนสร้างเอกสาร |
| สีฟอนต์ไม่ตรงกับธีม Word | ตั้งค่าฟอนต์ในโค้ดเป็นค่ากำหนดเอง   | ลบการตั้งค่าฟอนต์ที่กำหนดเองหรือใช้สีของธีม Word (`System.Drawing.Color.Black`) |

## โค้ดเต็ม (พร้อมรัน)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

เมื่อรันโปรแกรมจะสร้างไฟล์ `ChartWithCustomLabels.docx` ซึ่งมีตัวอย่าง **create pie chart word** ที่ตอบสนองทุกข้อกำหนดที่ระบุในบทเรียนนี้

## สรุป

ตอนนี้คุณรู้วิธี **สร้างแผนภูมิวงกลมใน Word** ด้วย C# และ Aspose.Words แล้ว คู่มือได้ครอบคลุมการแทรกแผนภูมิวงกลม, **add data labels pie**, **show percentage chart**, และ **customize chart data labels** เพื่อให้ได้ไฟล์ Word ที่ดูเป็นมืออาชีพและขับเคลื่อนด้วยข้อมูล  

ต่อไปคุณสามารถสำรวจหัวข้อที่เกี่ยวข้อง เช่น **insert pie chart** ลงในย่อหน้าที่มีอยู่แล้ว, สร้าง **bar** หรือ **line** chart, หรือทำการอัตโนมัติการสร้างรายงานเป็นชุดโดยใช้ชุดข้อมูลที่แตกต่างกัน ทดลองปรับตำแหน่งป้าย, สไตล์ฟอนต์, และการตั้งค่าหลายชุดเพื่อให้ผลลัพธ์ตรงกับความต้องการของการรายงานของคุณ

ขอให้สนุกกับการสร้างแผนภูมิ!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบต่าง ๆ ในโปรเจกต์ของคุณ

- [ปรับแต่งป้ายข้อมูลแผนภูมิ](/words/english/net/programming-with-charts/chart-data-label/)
- [ตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูลในแผนภูมิ](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [แทรกแผนภูมิคอลัมน์ในเอกสาร Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}