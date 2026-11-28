---
category: general
date: 2026-10-13
description: ตัวอย่างแผนภูมิรัศมีของ Aspose.Words ที่แสดงวิธีเปิดใช้งานการแบ่งระดับบนแผนภูมิรัศมีโดยใช้
  C# และ Aspose.Words 24.9+
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: th
lastmod: 2026-10-13
og_description: ตัวอย่างแผนภูมิรัศมีของ Aspose.Words ที่แสดงการเปิดใช้งานการแบ่งระดับบนแผนภูมิรัศมีด้วย
  C# และไลบรารีล่าสุดเวอร์ชัน 24.9+
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: ตัวอย่างแผนภูมิรัศมี Aspose.Words – เปิดใช้งานการแบ่งระดับใน C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'ตัวอย่างแผนภูมิรัศมี Aspose.Words: เปิดใช้งานการแบ่งระดับใน C#'
url: /th/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตัวอย่างแผนภูมิรัศมี Aspose.Words: เปิดการแสดงระดับใน C#

หากคุณกำลังมองหา **aspose.words radial chart example** คุณมาถูกที่แล้ว บทแนะนำนี้จะพาคุณผ่านขั้นตอนที่จำเป็นเพื่อเปิดการแสดงระดับสำหรับแผนภูมิรัศมีโดยใช้ Aspose.Words for .NET API

แผนภูมิรัศมีมีประโยชน์สำหรับการแสดงข้อมูลเชิงรอบ เช่น ตัวชี้วัดตามเวลาในแต่ละวันหรือแนวโน้มตามฤดูกาล โดยค่าเริ่มต้นระดับ (เครื่องหมายติ๊กรอบแกนวงกลม) จะถูกซ่อน ซึ่งอาจทำให้แผนภูมิเข้าใจยาก การเปิดใช้งานเพียงบรรทัดเดียว แต่คุณต้องรู้โมเดลวัตถุที่ถูกต้องและเวอร์ชันที่รองรับฟีเจอร์นี้

ในคู่มือนี้คุณจะได้เรียนรู้วิธี:

* โหลดเอกสาร Word ที่มีแผนภูมิรัศมีอยู่แล้ว  
* เข้าถึงรูปแผนภูมิผ่าน Aspose.Words chart API  
* เปิด **การแสดงระดับ** (พร้อมใช้งานตั้งแต่ **Aspose.Words version 24.9**)  
* บันทึกเอกสารที่แก้ไขและตรวจสอบผลลัพธ์

โค้ดที่สมบูรณ์และสามารถรันได้รวมอยู่ด้วย คุณสามารถคัดลอกและวางลงในโปรเจกต์คอนโซลใหม่และเห็นผลทันที

![ตัวอย่างแผนภูมิรัศมี Aspose.Words พร้อมระดับ](https://example.com/images/radial-chart-graduations.png "ตัวอย่างแผนภูมิรัศมี Aspose.Words แสดงระดับที่เปิดใช้งาน")

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6.0 หรือใหม่กว่า | Aspose.Words for .NET 24.9+ รองรับ .NET Standard 2.0 และทำงานบน .NET 6+ |
| Aspose.Words for .NET **24.9** หรือใหม่กว่า | คุณสมบัติ `IsGraduationsVisible` ถูกเพิ่มในเวอร์ชัน 24.9. เวอร์ชันเก่าจะทำให้เกิด `MissingMemberException` |
| เอกสาร Word (`RadialChart.docx`) ที่มีแผนภูมิรัศมี | ตัวอย่างนี้แก้ไขแผนภูมิที่มีอยู่; การสร้างจากศูนย์เป็นหัวข้อแยกต่างหาก |
| IDE สำหรับ C# (Visual Studio, Rider, VS Code) | IDE ใดก็ได้ที่สามารถคอมไพล์โปรเจกต์ .NET จะทำงานได้ |
| NuGet package `Aspose.Words` | ติดตั้งด้วย `dotnet add package Aspose.Words --version 24.9.0` (หรือเวอร์ชันใหม่กว่า) |

> **เคล็ดลับ:** หากคุณไม่สามารถอัปเกรดเป็น 24.9 ได้ คุณยังคงแก้ไขคุณสมบัติแผนภูมิอื่น ๆ ได้ แต่ระดับจะยังคงซ่อนอยู่ เนื่องจาก API ไม่ได้เปิดเผยฟลักนี้

## ตัวอย่างแผนภูมิรัศมี Aspose.Words – คู่มือขั้นตอนโดยละเอียด

ส่วนต่อไปนี้จะแบ่งกระบวนการออกเป็นขั้นตอนย่อยที่ทำตามได้ง่าย แต่ละขั้นตอนจะมีโค้ดที่ต้องใช้และคำอธิบายสั้น ๆ ว่า *ทำไม* จึงต้องทำขั้นตอนนั้น

### ขั้นตอนที่ 1: โหลดเอกสารที่มีแผนภูมิรัศมี

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**ทำไมถึงสำคัญ:**  
`Document` เป็นจุดเริ่มต้นของ **Aspose.Words chart API** มันโหลดไฟล์ DOCX เข้าไปในหน่วยความจำ ทำให้คุณเข้าถึงโหนดทุกประเภท—ย่อหน้า ตาราง และรูปแผนภูมิ หากไฟล์ไม่พบ `Document` จะโยน `FileNotFoundException` ซึ่งควรจัดการในโค้ดการผลิต

### ขั้นตอนที่ 2: ดึงรูปแผนภูมิแรกจากเอกสาร

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**ทำไมถึงสำคัญ:**  
แผนภูมิถูกจัดเก็บเป็นโหนด `Shape` เมธอด `GetChild` พร้อม `NodeType.Shape` จะเดินผ่าน DOM และคืนรูปที่ตรงกันเป็นอันแรก การแคสต์เป็น `Chart` ทำให้คุณเข้าถึงคุณสมบัติเฉพาะของแผนภูมิ เช่น `RadialChart` การตรวจสอบค่า null ช่วยให้คุณได้รับข้อผิดพลาดที่ชัดเจนหากเอกสารไม่มีแผนภูมิ ซึ่งเป็นกรณีขอบที่พบบ่อยเมื่อใช้เทมเพลตซ้ำ

### ขั้นตอนที่ 3: เปิดการแสดงระดับบนแผนภูมิรัศมี

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**ทำไมถึงสำคัญ:**  
`IsGraduationsVisible` ควบคุมเครื่องหมายติ๊กรอบแกนวงกลม เมื่อกำหนดเป็น `true` แผนภูมิจะแสดงระดับ ทำให้ผู้อ่านสามารถประเมินค่าต่าง ๆ ได้แม่นยำ คุณสมบัตินี้อยู่ภายใต้ `RadialChart` ซึ่งเป็นชนิดย่อยของ `Chart` หากคุณลองใช้กับแผนภูมิที่ไม่ใช่รัศมี (เช่น แผนภูมิคอลัมน์) `RadialChart` จะเป็น `null` ดังนั้นควรตรวจสอบประเภทแผนภูมิก่อนในสถานการณ์ที่ซับซ้อน

#### การจัดการแผนภูมิที่ไม่ใช่รัศมี (ทางเลือก)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

การตรวจสอบนี้ทำให้โค้ดแข็งแรงเมื่อต้นทางอาจมีแผนภูมิหลายประเภท

### ขั้นตอนที่ 4: บันทึกเอกสารที่แก้ไขแล้ว

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**ทำไมถึงสำคัญ:**  
การเรียก `Save` จะเขียน DOM ที่อยู่ในหน่วยความจำกลับไปเป็นไฟล์ .docx ทำให้การเปลี่ยนแปลงที่คุณทำกับแผนภูมิมีผลไฟล์ผลลัพธ์สามารถเปิดด้วย Microsoft Word, LibreOffice หรือโปรแกรมดู DOCX ใด ๆ ก็ได้ คุณจะเห็นแผนภูมิรัศมีที่มีระดับแสดงอยู่

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมทั้งหมดที่คุณสามารถวางลงใน `Program.cs` ของโปรเจกต์คอนโซล .NET

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เมื่อเปิดไฟล์ `RadialChart_Graduations.docx` ด้วย Word แผนภูมิรัศมีจะมีเครื่องหมายติ๊ก (ระดับ) รอบแกนวงกลม เหมือนกับภาพหน้าจอที่แสดงไว้ก่อนหน้านี้ ส่วนอื่นของแผนภูมิ (ชุดข้อมูล, คำอธิบาย, ชื่อเรื่อง) จะไม่มีการเปลี่ยนแปลง

## ความแปรผันทั่วไปและกรณีขอบ

| Situation | Solution |
|-----------|----------|
| **เวอร์ชัน Aspose.Words เก่า (< 24.9)** | อัปเกรดเป็นแพคเกจ NuGet ล่าสุด `IsGraduationsVisible` ไม่มีในเวอร์ชันก่อน |
| **มีหลายแผนภูมิในเอกสารเดียว** | ใช้ `doc.GetChild(NodeType.Shape, index, true)` พร้อม `index` ที่เหมาะ หรือวนลูป `doc.GetChildNodes(NodeType.Shape, true)` แล้วกรองด้วย `ChartType.Radial` |
| **สร้างแผนภูมิด้วยโปรแกรม** | ใช้ `DocumentBuilder` แทรกแผนภูมิ แล้วตั้งค่า `RadialChart.IsGraduationsVisible` บนแผนภูมิที่สร้างขึ้น |

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานอื่น ๆ ในโครงการของคุณ

- [อัปเดตข้อมูลชุดแผนภูมิในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [ลบชุดแผนภูมิจากเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [ซ่อนขอบพื้นที่พล็อตในแผนภูมิคอลัมน์ด้วย Aspose.Words for .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}