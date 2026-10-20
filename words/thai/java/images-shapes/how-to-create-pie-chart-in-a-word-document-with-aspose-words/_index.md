---
category: general
date: 2026-10-20
description: สร้างแผนภูมิวงกลมในเอกสาร Word โดยใช้ Aspose.Words – คู่มือขั้นตอนที่แสดงวิธีตั้งค่าสี,
  แยกชิ้นส่วน, และบันทึกเอกสาร Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: th
lastmod: 2026-10-20
og_description: สร้างแผนภูมิวงกลมในเอกสาร Word ด้วย Aspose.Words เรียนรู้วิธีตั้งค่าสี
  แยกชิ้นส่วน และบันทึกเอกสาร Word ในตัวอย่างเดียวที่สามารถรันได้.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: สร้างแผนภูมิวงกลมในเอกสาร Word – คู่มือ C# ฉบับเต็ม
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: วิธีสร้างแผนภูมิวงกลมในเอกสาร Word ด้วย Aspose.Words
url: /th/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างแผนภูมิวงกลมในเอกสาร Word ด้วย Aspose.Words

หากคุณต้องการ **สร้างแผนภูมิวงกลม** ภายในไฟล์ Word คำแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนอย่างละเอียด คุณจะได้เรียนรู้วิธีตั้งค่าสีที่กำหนดเอง, แยกชิ้นส่วนเพื่อเน้น, และสุดท้าย **บันทึกเอกสาร Word** พร้อมแผนภูมิที่ฝังอยู่

การสร้างแผนภูมิด้วยโปรแกรมจะช่วยขจัดขั้นตอนการเปิด Word, แทรกแผนภูมิ, และปรับแต่งลักษณะของมันด้วยตนเอง เมื่อจบบทเรียนนี้คุณจะมีแอปพลิเคชันคอนโซล C# ที่ทำงานได้สมบูรณ์ซึ่งสร้างแผนภูมิวงกลม, ปรับแต่งมัน, และบันทึกผลลัพธ์ลงดิสก์

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มต้น, ตรวจสอบให้แน่ใจว่าคุณมี:

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า ติดตั้งแล้ว  
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ประเมินผลฟรี)  
* IDE เช่น Visual Studio 2022 หรือ VS Code  

ไม่จำเป็นต้องใช้แพ็กเกจ NuGet เพิ่มเติมนอกจาก `Aspose.Words`.

## วิธีสร้างแผนภูมิวงกลมในเอกสาร Word

ขั้นตอนแรกคือการสร้างอินสแตนซ์ของ `Document` และ `DocumentBuilder` ตัวสร้างนี้ให้คุณเข้าถึงฟีเจอร์ระดับสูงของ Word รวมถึงการแทรกแผนภูมิ

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

ในขั้นตอนนี้เอกสารจะมีแผนภูมิวงกลมพื้นฐานอยู่แล้ว ส่วนต่อไปจะอธิบาย **วิธีแยกชิ้นส่วน**, **วิธีตั้งค่าสี**, และ **วิธีบันทึกเอกสาร Word**.

## วิธีแยกชิ้นส่วนเพื่อเน้น

การแยกชิ้นส่วนจะทำให้ชิ้นนั้นแยกออกจากส่วนอื่นของวงกลม, ดึงความสนใจของผู้อ่าน. API ของ Aspose.Words ให้คุณระยะการแยก (explosion) เป็นหน่วย points

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

ทำไมต้องแยกชิ้นส่วน? ในรายงานที่เน้นหมวดหมู่เฉพาะ—เช่น “สินค้าขายดีอันดับต้นๆ”—การแยกเชิงภาพทำให้จุดข้อมูลนั้นโดดเด่นและรับรู้ได้ทันที

## วิธีตั้งค่าสีให้ชิ้นส่วนของแผนภูมิ

สีที่กำหนดเองช่วยเสริมความสอดคล้องของแบรนด์และความอ่านง่าย คุณสามารถกำหนด `System.Drawing.Color` ใดก็ได้ให้กับจุดข้อมูลเฉพาะ

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

คุณไม่ได้จำกัดอยู่แค่สีที่กำหนดไว้ล่วงหน้า; คุณสามารถสร้างค่า `Color.FromArgb` เพื่อกำหนดเฉดสีที่แม่นยำได้

## วิธีบันทึกเอกสาร Word พร้อมแผนภูมิ

เมื่อแผนภูมิดูตามที่คุณต้องการ การบันทึกไฟล์ก็ทำได้ง่าย เมธอด `Document.Save` จะเขียนเอกสารในรูปแบบที่คุณระบุ—ในที่นี้เราใช้ค่าเริ่มต้น `.docx`

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `PieChart.docx`. การเปิดไฟล์ใน Microsoft Word จะเห็นแผนภูมิวงกลมที่ชิ้นแรกถูกแยกออกและสีแดง, ตรงตามที่โค้ดกำหนด

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ Word ชื่อ **PieChart.docx** อยู่ใน `C:\Temp`.  
* เอกสารมีแผนภูมิวงกลมหนึ่งชิ้น ขนาด 400 × 300 points.  
* ชิ้นส่วน 0 ถูกย้ายออก 20 points และเติมสีแดง, ส่วนชิ้นอื่นคงสีเริ่มต้น  

คุณสามารถตรวจสอบการแยกและสีได้โดยการเลือกแผนภูมิใน Word แล้วตรวจสอบคุณสมบัติของชิ้นส่วน

## เคล็ดลับระดับมืออาชีพและข้อผิดพลาดทั่วไป

* **เคล็ดลับระดับมืออาชีพ:** หากต้องการเปลี่ยนชื่อแผนภูมิหรือคำอธิบาย, ใช้คุณสมบัติ `pieChart.Title.Text` และ `pieChart.Legend` ก่อนบันทึก.  
* **ระวัง:** การลืมล้างจุดข้อมูลเริ่มต้นอาจทำให้เกิดชิ้นส่วนเพิ่มที่ไม่ต้องการ. ควรเรียก `Series[0].DataPoints.Clear()` ก่อนเพิ่มข้อมูลของคุณ.  
* **เคล็ดลับประสิทธิภาพ:** สำหรับเอกสารขนาดใหญ่, ควรใช้อินสแตนซ์ `DocumentBuilder` เพียงหนึ่งตัวแทนการสร้างหลายตัว; จะช่วยลดการใช้หน่วยความจำ.

## วิธีสร้างแผนภูมิด้วย Aspose.Words (บริบทเพิ่มเติม)

เมธอด `InsertChart` รองรับหลายประเภทของแผนภูมิ นอกจากแผนภูมิวงกลม เช่น คอลัมน์, เส้น, และพื้นที่. เพื่อสลับเป็นประเภทอื่น, ให้แทนที่ `ChartType.Pie` ด้วยค่า enum ที่ต้องการ, เช่น `ChartType.Column`. ขั้นตอนการปรับแต่งที่เหลือ (การแยกชิ้นส่วน, การตั้งค่าสี) ทำตามรูปแบบเดียวกัน, แม้ว่าประเภทแผนภูมิบางประเภทอาจไม่มีคุณสมบัติ “explosion”.

## วิธีแยกชิ้นส่วนในประเภทแผนภูมิอื่น

เฉพาะแผนภูมิประเภทวงกลมเท่านั้นที่มีเมธอด `SetExplosion`. หากเรียกใช้บนแผนภูมิบาร์, API จะโยน `ArgumentException`. ในกรณีนั้น, ควรใช้ป้ายข้อมูลหรือ callout เพื่อเน้นบาร์ที่ต้องการ.

## วิธีตั้งค่าสีให้กับซีรีส์แทนการตั้งค่าสีชิ้นเดียว

หากต้องการให้ทุกชิ้นส่วนในซีรีส์มีสีเดียวกัน, ให้วนลูปผ่านจุดข้อมูล:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

วิธีนี้สะดวกเมื่อคุณต้องการโทนสีสม่ำเสมอในหลายแผนภูมิ.

## วิธีบันทึกเอกสาร Word ในรูปแบบอื่น

Aspose.Words สามารถส่งออกเป็น PDF, HTML, และรูปแบบอื่นๆ ได้หลายรูปแบบ. เปลี่ยนส่วนขยายไฟล์ใน `Save` และอาจส่งผ่านอ็อบเจ็กต์ `SaveOptions` เพิ่มเติม:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

เอนจินการเรนเดอร์แผนภูมิจะทำการแปลงแผนภูมิเป็นรูปแบบเป้าหมายโดยอัตโนมัติ, รักษาสีและการตั้งค่า explosion ไว้

## สรุป

ตอนนี้คุณรู้วิธี **สร้างแผนภูมิวงกลม** ในเอกสาร Word, ปรับลักษณะของมันโดย **แยกชิ้นส่วน** และ **ตั้งค่าสี**, และสุดท้าย **บันทึกเอกสาร Word** พร้อมแผนภูมิที่ฝังอยู่ ตัวอย่างครบวงจรนี้ให้พื้นฐานที่มั่นคงสำหรับการอัตโนมัติการสร้างรายงาน, แดชบอร์ด, หรือสถานการณ์ใดๆ ที่ต้องแทรกข้อมูลเชิงภาพโดยโปรแกรม

### ขั้นตอนต่อไป

* สำรวจประเภทแผนภูมิอื่น (`ChartType.Column`, `ChartType.Line`) เพื่อขยายเครื่องมือรายงานของคุณ.  
* รวมหลายแผนภูมิในเอกสารเดียวเพื่อสร้างแดชบอร์ดที่ครอบคลุม.  
* ทดลองใช้ `ChartDataLabel` เพื่อแสดงเปอร์เซ็นต์หรือค่าตรงบนชิ้นส่วน.  

คุณสามารถปรับโค้ดให้เข้ากับแหล่งข้อมูลของคุณได้ตามต้องการ—ไม่ว่าจะดึงค่าจากฐานข้อมูล, API, หรือไฟล์ CSV, กระบวนการทำงานของ Aspose.Words จะเหมือนกัน. ขอให้สนุกกับการสร้างแผนภูมิ!

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดที่ทำงานสมบูรณ์พร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่นในโครงการของคุณ.

- [แยกชิ้นส่วนแผนภูมิวงกลมใน C# ด้วย Aspose.Words – คู่มือเต็ม](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [แทรกแผนภูมิคอลัมน์แบบกำหนดเองในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [อัปเดตข้อมูลซีรีส์ของแผนภูมิในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}