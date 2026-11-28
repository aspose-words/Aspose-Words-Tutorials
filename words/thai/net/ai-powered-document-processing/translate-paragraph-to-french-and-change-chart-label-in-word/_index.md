---
category: general
date: 2026-10-10
description: แปลย่อหน้าเป็นภาษาฝรั่งเศสและเรียนรู้วิธีเปลี่ยนป้ายข้อมูลของแผนภูมิ
  ปรับแต่งป้ายข้อมูลของแผนภูมิ และบันทึกไฟล์ docx ที่แก้ไขโดยใช้ Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: th
lastmod: 2026-10-10
og_description: แปลย่อหน้าเป็นภาษาฝรั่งเศสและเรียนรู้วิธีเปลี่ยนป้ายข้อมูลแผนภูมิ
  ปรับแต่งป้ายข้อมูลแผนภูมิ และบันทึกไฟล์ docx ที่แก้ไขโดยใช้ Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: แปลย่อหน้าเป็นภาษาฝรั่งเศสและเปลี่ยนป้ายแผนภูมิใน Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: แปลย่อหน้าเป็นภาษาฝรั่งเศสและเปลี่ยนป้ายแผนภูมิใน Word
url: /th/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แปลย่อหน้าภาษา French และเปลี่ยนป้ายชื่อแผนภูมิใน Word

หากคุณต้องการ **แปลย่อหน้าเป็นภาษาฝรั่งเศส** พร้อมกับอัปเดตแผนภูมิในเอกสาร Word เดียวกัน คู่มือนี้จะแสดงให้คุณเห็นขั้นตอนอย่างชัดเจน โดยใช้ Aspose.Words AI คุณสามารถแปลข้อความโดยอัตโนมัติ จากนั้นแก้ไขป้ายข้อมูลของแผนภูมิและสุดท้ายบันทึกไฟล์ `.docx` ที่แก้ไขแล้ว—ทั้งหมดในไม่กี่ขั้นตอนง่าย ๆ  

บทเรียนนี้ครอบคลุมทุกอย่างตั้งแต่การโหลดไฟล์ต้นฉบับจนถึงการบันทึกการเปลี่ยนแปลง เมื่อเสร็จสิ้นคุณจะสามารถแปลย่อหน้าใดก็ได้ ปรับแต่งป้ายข้อมูลของแผนภูมิ และสร้างไฟล์ Word ใหม่พร้อมใช้งานสำหรับการแจกจ่าย ไม่จำเป็นต้องใช้สคริปต์ภายนอก; กระบวนการทั้งหมดทำงานในโปรแกรม C# เดียว  

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+)
- ใบอนุญาต Aspose.Words for .NET (หรือคีย์ทดลองฟรี)
- การเชื่อมต่ออินเทอร์เน็ตสำหรับ Google AI translator (คลาส `Translator` ใช้ API ของ Google ภายใน)
- เอกสาร Word (`input.docx`) ที่มีอย่างน้อยหนึ่งย่อหน้าและหนึ่งแผนภูมิ  

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า namespace

Create a new console application and add the Aspose.Words NuGet package:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

จากนั้นให้รวม namespace ที่จำเป็นไว้ที่ส่วนบนของไฟล์ `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

การนำเข้าตัวเหล่านี้ทำให้คุณเข้าถึงฟังก์ชันการโหลดเอกสาร, การแปลด้วย AI, และการแก้ไขแผนภูมิ  

## ขั้นตอนที่ 2: โหลดเอกสาร Word ต้นฉบับ

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

การโหลดไฟล์จะสร้างการแสดงผลในหน่วยความจำที่คุณสามารถสอบถามและแก้ไขได้โดยไม่ต้องแตะไฟล์ต้นฉบับบนดิสก์  

## ขั้นตอนที่ 3: แปลย่อหน้าแรกเป็นภาษาฝรั่งเศส

ย่อหน้าแรกมักเป็นหัวข้อหรือประโยคแนะนำ ทำให้เป็นตัวเลือกที่ดีสำหรับการแปล คลาส `Translator` ทำหน้าที่เป็นชั้นนามธรรมสำหรับการเรียกใช้โมเดล AI ของ Google  

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**ทำไมวิธีนี้ถึงได้ผล:**  
`paragraph.Runs.Clear()` จะลบข้อความรันที่มีอยู่ทั้งหมด เพื่อให้การแปลใหม่ไม่ต่อเนื่องกับเนื้อหาเดิม `new Run(document, translatedText)` สร้างรันใหม่ที่สืบทอดการจัดรูปแบบของย่อหน้า  

## ขั้นตอนที่ 4: ค้นหาแผนภูมิแรกและปรับแต่งป้ายข้อมูลของมัน

แผนภูมิจะถูกเก็บเป็นโหนด `Shape` ชนิด `NodeType.Shape`. แผนภูมิแรกสามารถดึงได้ด้วย `GetChild`  

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**คำอธิบายขั้นตอนสำคัญ:**

- `GetChild(NodeType.Shape, 0, true)` ทำการค้นหาแบบ depth‑first และคืนค่า shape แรก ซึ่งในกรณีของเราคือแผนภูมิ
- `ChartSeries` แสดงถึงชุดของจุดข้อมูล; series แรก (`Series[0]`) มักจะสอดคล้องกับชุดข้อมูลหลัก
- `ChartDataLabelPosition.OutsideEnd` ย้ายป้ายออกไปที่ส่วนปลายของแถบ เพื่อเพิ่มความอ่านง่าย
- การตั้งค่า `dataLabel.Text` เป็นสตริงภาษาฝรั่งเศสทำให้ป้ายสอดคล้องกับย่อหน้าที่แปลแล้ว  

## ขั้นตอนที่ 5: บันทึกเอกสารพร้อมย่อหน้าที่แปลแล้ว

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

ในขั้นตอนนี้เอกสารมีย่อหน้าภาษาฝรั่งเศสแล้ว แต่ยังคงมีการกำหนดค่าแผนภูมิดั้งเดิม  

## ขั้นตอนที่ 6: บันทึกเอกสารพร้อมแผนภูมิที่อัปเดต

คุณสามารถใช้อินสแตนซ์ `Document` เดิมซ้ำได้—ไม่จำเป็นต้องโหลดใหม่—เพราะการแก้ไขแผนภูมิได้อยู่ในหน่วยความจำแล้ว  

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

ไฟล์ทั้งสองพร้อมสำหรับการแจกจ่ายแล้ว:

- **`translated.docx`** – มีย่อหน้าภาษาฝรั่งเศส
- **`chart-updated.docx`** – มีย่อหน้าภาษาฝรั่งเศส *และ* ป้ายแผนภูมิที่ปรับแต่งแล้ว  

## ตัวอย่างที่สมบูรณ์และสามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงใน `Program.cs`. มันจะคอมไพล์และรันได้ทันที หากคุณได้แทนที่ `YOUR_DIRECTORY` ด้วยเส้นทางโฟลเดอร์จริง  



## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการใช้งานอื่น ๆ ในโครงการของคุณ  

- [ปรับแต่งป้ายข้อมูลแผนภูมิ](/words/english/net/programming-with-charts/chart-data-label/)
- [จัดรูปแบบจำนวนป้ายข้อมูลในแผนภูมิ](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [ป้ายข้อมูลแผนภูมิ](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}