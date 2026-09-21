---
category: general
date: 2026-09-21
description: เรียนรู้วิธีสร้างเอกสาร Word ด้วย C# และแทรกแผนภูมิคอลัมน์ ตั้งค่าตำแหน่งป้ายกำกับ
  และแสดงค่าโดยใช้ Aspose.Words ในคู่มือแบบทีละขั้นตอน
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: th
lastmod: 2026-09-21
og_description: สร้างเอกสาร Word ด้วย C# และ Aspose.Words. บทเรียนนี้แสดงวิธีแทรกแผนภูมิคอลัมน์
  ตั้งค่าตำแหน่งป้ายกำกับ และแสดงค่า.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: สร้างเอกสาร Word ด้วย C# – แทรกแผนภูมิคอลัมน์, ตั้งค่าป้าย, แสดงค่า
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: วิธีสร้างเอกสาร Word ด้วย C# พร้อมแผนภูมิคอลัมน์และป้ายกำกับที่จัดรูปแบบ
url: /th/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างเอกสาร Word ด้วย C# พร้อมแผนภูมิคอลัมน์และป้ายกำกับที่จัดรูปแบบ

หากคุณต้องการ **create Word document C#** ที่รวมแผนภูมิ คู่มือนี้จะแสดงวิธีทำอย่างละเอียด คุณจะได้เรียนรู้วิธีแทรกแผนภูมิคอลัมน์ การกำหนดตำแหน่งป้ายข้อมูล และการแสดงค่าของป้าย—ทั้งหมดด้วย Aspose.Words for .NET.

การสร้างไฟล์ Word ที่มีแผนภูมิเดิมต้องทำงานด้วยมือใน Microsoft Word. ด้วยขั้นตอน **how to insert chart** ที่อธิบายไว้ที่นี่ คุณสามารถทำอัตโนมัติทั้งหมดจากโค้ด ทำให้การสร้างรายงานเร็วและทำซ้ำได้ บทเรียนยังครอบคลุม **how to set label** และ **how to display values** เพื่อให้แผนภูมิพร้อมใช้งานสำหรับผู้ใช้ปลายทาง.

เมื่ออ่านบทความนี้จนจบ คุณจะได้โปรแกรม C# ที่ทำงานได้สมบูรณ์ซึ่งสร้างไฟล์ `.docx` ที่มีแผนภูมิคอลัมน์โดยป้ายข้อมูลปรากฏภายในแต่ละคอลัมน์และแสดงค่าตัวเลขของมัน.

## ข้อกำหนดเบื้องต้น

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า  
* สำเนา **Aspose.Words for .NET** ที่มีลิขสิทธิ์ (รุ่นทดลองฟรีใช้สำหรับการทดสอบได้)  
* IDE เช่น Visual Studio 2022 หรือ Visual Studio Code  

ไม่จำเป็นต้องมีแพ็กเกจ NuGet เพิ่มเติมนอกจาก `Aspose.Words`.

## ขั้นตอนที่ 1: ตั้งค่าโครงการและเพิ่ม Aspose.Words

สร้างโปรเจกต์คอนโซลใหม่และเพิ่มแพ็กเกจ Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

`คำสั่ง `dotnet add package` ดึงเวอร์ชันเสถียรล่าสุดของ **Aspose.Words** ซึ่งรวม API ของแผนภูมิที่ใช้ในตัวอย่าง **insert column chart word**.

## ขั้นตอนที่ 2: สร้างเอกสาร Word ว่างใหม่

โค้ดส่วนแรกนี้สร้างเอกสารเปล่าและ `DocumentBuilder` ที่ให้คุณแทรกเนื้อหา นี่คือพื้นฐานสำหรับ **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` แทนไฟล์ `.docx` ทั้งหมด ในขณะที่ `DocumentBuilder` มีเมธอดเช่น `InsertParagraph`, `InsertImage` และที่สำคัญสำหรับบทเรียนนี้คือ `InsertChart`.

## ขั้นตอนที่ 3: แทรกแผนภูมิคอลัมน์ (how to insert chart)

ตอนนี้เราจะแทรก **column chart** เมธอด `InsertChart` รับประเภทแผนภูมิ, ความกว้างและความสูงเป็นหน่วยจุด.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

ในขั้นตอนนี้แผนภูมิจะมีชุดข้อมูลเริ่มต้นพร้อมค่าตัวแทน คุณสามารถแทนที่ข้อมูลชุดนี้ได้หากต้องการตัวเลขกำหนดเอง แต่เพื่อสาธิต **how to set label** และ **how to display values** ข้อมูลเริ่มต้นก็เพียงพอ.

## ขั้นตอนที่ 4: กำหนดตำแหน่งป้ายข้อมูลภายในแต่ละคอลัมน์ (how to set label)

ป้ายข้อมูลคือข้อความที่ปรากฏบนแต่ละคอลัมน์ เพื่อทำให้แผนภูมิเข้าใจง่ายขึ้น เราจะย้ายป้ายไปอยู่ภายในคอลัมน์และเปิดใช้งานค่าตัวเลขของมัน.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` วางป้ายที่ด้านบนของคอลัมน์แต่ยังคงอยู่ภายในรูปร่างของคอลัมน์ ซึ่งเป็นสไตล์ที่นิยมในรายงาน การตั้งค่า `ShowValue` เป็น `true` ทำให้ตรงตามความต้องการของ **how to display values**.

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารลงดิสก์ ไฟล์นี้สามารถเปิดด้วย Microsoft Word, LibreOffice หรือโปรแกรมดูไฟล์ใด ๆ ที่รองรับรูปแบบ Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

การรันโปรแกรมจะสร้าง `output.docx` ที่มีแผนภูคคอลัมน์พร้อมป้ายข้อมูลที่วางอยู่ภายในแต่ละคอลัมน์และแสดงค่าของมัน.

### ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิด `output.docx` คุณควรเห็นแผนภูมิคอลัมน์เดียวที่คล้ายกับภาพด้านล่าง แต่ละคอลัมน์จะมีป้ายตัวเลขที่ด้านบน ภายในคอลัมน์ แสดงค่าของชุดข้อมูล.

![แผนภูมิในเอกสาร Word ที่สร้างด้วย C#](/images/word-chart-example.png "แผนภูมิในเอกสาร Word ที่สร้างด้วย C# – create word document C#")

*ข้อความแทนภาพ:* *แผนภูมิในเอกสาร Word ที่สร้างด้วย C# ซึ่งแสดงวิธีแทรก column chart word และแสดงค่า.*

## ความแตกต่างทั่วไปและกรณีขอบ

### การเพิ่มข้อมูลกำหนดเองลงในแผนภูมิ

หากคุณต้องการแทนที่ข้อมูลตัวแทน คุณสามารถแก้ไขคอลเลกชัน `Series` ของแผนภูมิได้:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### การเปลี่ยนแบบอักษรและสีของป้าย

คุณสามารถปรับแต่งลักษณะของป้ายเพิ่มเติมได้:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### การแทรกหลายแผนภูมิ

`DocumentBuilder` สามารถแทรกแผนภูมิจำนวนเท่าที่ต้องการ เพียงเรียก `InsertChart` อีกครั้งหลังจากย้ายเคอร์เซอร์ด้วย `builder.Writeln()` หรือ `builder.InsertParagraph()`.

## เคล็ดลับระดับมืออาชีพ

* **เคล็ดลับระดับมืออาชีพ:** ตั้งค่า `chart.HasTitle = true` และกำหนด `chart.Title.Text` เพื่อให้แผนภูมิมีหัวข้ออธิบาย ซึ่งช่วยเพิ่มการเข้าถึงสำหรับโปรแกรมอ่านหน้าจอ.
* **ระวัง:** เมื่อบันทึกไปยังแชร์เครือข่าย ให้ตรวจสอบว่าแอปพลิเคชันมีสิทธิ์เขียน มิฉะนั้น `doc.Save` จะโยน `UnauthorizedAccessException`.
* **เคล็ดลับประสิทธิภาพ:** ใช้ `DocumentBuilder` ตัวเดียวสำหรับการแทรกหลายครั้ง; การสร้าง builder ใหม่สำหรับแต่ละการดำเนินการจะเพิ่มภาระที่ไม่จำเป็น.

## สรุป

ตอนนี้คุณรู้วิธี **create Word document C#** ที่มีแผนภูมิคอลัมน์ วิธี **insert chart** การกำหนดตำแหน่ง **set label** และ **display values** ภายในแต่ละคอลัมน์ ตัวอย่างโค้ดเต็มที่แสดงข้างต้นพร้อมรันแล้ว และคุณสามารถขยายด้วยข้อมูลกำหนดเอง การจัดรูปแบบ หรือแผนภูมิเพิ่มเติม.

ต่อไปสำรวจหัวข้อที่เกี่ยวข้องเช่น **how to insert picture**, **how to generate tables**, หรือ **how to apply document themes** เพื่อทำให้รายงานอัตโนมัติของคุณสมบูรณ์ยิ่งขึ้น ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ.

- [แทรกแผนภูมิคอลัมน์ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [แทรกแผนภูมิคอลัมน์แบบง่ายใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [แทรกแผนภูมิพื้นที่ในเอกสาร Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}