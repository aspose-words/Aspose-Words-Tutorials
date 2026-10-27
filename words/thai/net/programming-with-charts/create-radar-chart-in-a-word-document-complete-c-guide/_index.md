---
category: general
date: 2026-08-10
description: สร้างแผนภูมิเรดาร์อย่างรวดเร็วและเรียนรู้วิธีแทรกแผนภูมิลงในเอกสาร Word
  ด้วย Aspose.Words. ปฏิบัติตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อผลลัพธ์ที่เชื่อถือได้.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- insert chart into word document
- how to insert radar chart
language: th
lastmod: 2026-08-10
og_description: สร้างแผนภูมิเรดาร์ในไฟล์ Word ด้วย Aspose.Words. คู่มือนี้แสดงวิธีแทรกแผนภูมิลงในเอกสาร
  Word และปรับแต่งเพื่อการนำเสนอที่ชัดเจน.
og_image_alt: Radar chart created in a Word document using Aspose.Words
og_title: สร้างแผนภูมิเรดาร์ใน Word – การทำงานเต็มรูปแบบด้วย C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: create radar chart quickly and learn how to insert chart into word
    document using Aspose.Words. Follow this step‑by‑step guide for reliable results.
  headline: create radar chart in a Word document – complete C# guide
  type: TechArticle
- description: create radar chart quickly and learn how to insert chart into word
    document using Aspose.Words. Follow this step‑by‑step guide for reliable results.
  name: create radar chart in a Word document – complete C# guide
  steps:
  - name: Set up the project and add Aspose.Words
    text: '1. Open a new Console App project in Visual Studio. 2. Add the Aspose.Words
      package via NuGet:'
  - name: Create a blank document and a builder
    text: A `Document` represents the .docx file, while `DocumentBuilder` provides
      methods to add content.
  - name: Insert radar chart and obtain the Chart object
    text: The `InsertChart` method inserts a chart placeholder and returns a `Shape`.
      Access the underlying `Chart` to modify its settings.
  - name: Enable graduations on both axes for better readability
    text: Graduations (tick marks) improve data interpretation, especially on radar
      charts where radial spacing matters.
  - name: Define the data series for the radar chart
    text: A radar chart requires a category axis (labels) and one or more data series.
      The example adds a single series named *Series 1*.
  - name: Save the document containing the radar chart
    text: Choose a folder where the output should reside. The file extension `.docx`
      ensures compatibility with Microsoft Word, Google Docs, and LibreOffice.
  type: HowTo
tags:
- Aspose.Words
- C#
- Radar chart
- Word automation
title: สร้างแผนภูมิเรดาร์ในเอกสาร Word – คู่มือ C# ฉบับสมบูรณ์
url: /th/net/programming-with-charts/create-radar-chart-in-a-word-document-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างแผนภูมิเรดาร์ในเอกสาร Word – คู่มือ C# ฉบับสมบูรณ์

หากคุณต้องการ **สร้างแผนภูมิเรดาร์** ในไฟล์ Word, บทแนะนำนี้จะแสดงขั้นตอนที่แน่นอนให้คุณ คุณจะได้เห็นวิธี **แทรกแผนภูมิลงในเอกสาร Word** ด้วย Aspose.Words, กำหนดการแบ่งระดับแกน, และเพิ่มชุดข้อมูลเพื่อให้แผนภูมิพร้อมสำหรับการนำเสนอ

การสร้างแผนภูมิเรดาร์โดยอัตโนมัติช่วยลดความพยายามในการวาดรูปและจัดตำแหน่งข้อมูลด้วยตนเอง เมื่อจบคู่มือนี้คุณจะสามารถตอบ **วิธีแทรกแผนภูมิเรดาร์** ในไฟล์ .docx ใด ๆ, ปรับแต่งลักษณะของมัน, และบันทึกผลลัพธ์ด้วยบรรทัดโค้ดเดียว

## ข้อกำหนดเบื้องต้น

ก่อนเริ่ม, ตรวจสอบว่าคุณมี:

* .NET 6.0 หรือใหม่กว่า  
* Visual Studio 2022 (หรือโปรแกรมแก้ไข C# ใด ๆ)  
* ใบอนุญาต Aspose.Words for .NET (รุ่นทดลองฟรีใช้สำหรับการประเมินได้)

ไม่ต้องการแพ็กเกจ NuGet เพิ่มเติมนอกจาก `Aspose.Words` โค้ดทำงานได้บน Windows, macOS, และ Linux เนื่องจาก Aspose.Words รองรับหลายแพลตฟอร์ม

## วิธีสร้างแผนภูมิเรดาร์ในเอกสาร Word

ส่วนนี้อธิบายขั้นตอนทั้งหมดที่จำเป็นเพื่อ **สร้างแผนภูมิเรดาร์** ตั้งแต่เริ่มต้น วิธีการสอดคล้องกับกระบวนการทำงานมาตรฐานของ Aspose.Words: สร้าง `Document`, รับ `DocumentBuilder`, แทรกแผนภูมิ, ตั้งค่าคุณสมบัติต่าง ๆ, แล้วบันทึกไฟล์

### ขั้นตอนที่ 1: ตั้งค่าโครงการและเพิ่ม Aspose.Words

1. เปิดโปรเจกต์ Console App ใหม่ใน Visual Studio  
2. เพิ่มแพ็กเกจ Aspose.Words ผ่าน NuGet:

```bash
dotnet add package Aspose.Words
```

3. หากคุณมีไฟล์ใบอนุญาต, โหลดมันในตอนเริ่มของ `Main` เพื่อหลีกเลี่ยงลายน้ำการประเมิน:

```csharp
// Load license (optional)
Aspose.Words.License license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

**ทำไมเรื่องนี้ถึงสำคัญ:** การโหลดใบอนุญาตจะปิดการแสดงแบนเนอร์การประเมินและเปิดใช้งานความสามารถในการเรนเดอร์แผนภูมิเต็มรูปแบบ

### ขั้นตอนที่ 2: สร้างเอกสารเปล่าและตัวสร้าง

`Document` แทนไฟล์ .docx, ส่วน `DocumentBuilder` มีเมธอดสำหรับเพิ่มเนื้อหา

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new empty document
Document document = new Document();

// Obtain a builder linked to the document
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

**คำอธิบาย:** ตัวสร้างทำงานคล้ายเคอร์เซอร์; คำสั่งแทรกทุกคำสั่งจะเขียนที่ตำแหน่งปัจจุบัน การเริ่มต้นด้วยเอกสารเปล่าช่วยให้แผนภูมิเรดาร์เป็นองค์ประกอบภาพแรกที่ปรากฏ

### ขั้นตอนที่ 3: แทรกแผนภูมิเรดาร์และรับอ็อบเจกต์ Chart

เมธอด `InsertChart` แทรกตำแหน่งแผนภูมิชั่วคราวและคืนค่า `Shape` ใช้ `Chart` ภายในเพื่อแก้ไขการตั้งค่า

```csharp
// Insert a radar chart of 400x300 points
Chart radarChart = docBuilder.InsertChart(ChartType.Radar, 400, 300).Chart;
```

**ทำไมวิธีนี้ถึงได้ผล:** `ChartType.Radar` บอก Aspose.Words ให้สร้างแผนภูมิเรดาร์ (สไปเดอร์) พารามิเตอร์ขนาดควบคุมพื้นที่ที่แผนภูมิใช้บนหน้า

### ขั้นตอนที่ 4: เปิดการแสดงระดับบนแกนทั้งสองเพื่อความอ่านง่ายขึ้น

การแสดงระดับ (tick marks) ช่วยให้การตีความข้อมูลดีขึ้น, โดยเฉพาะบนแผนภูมิเรดาร์ที่ระยะห่างเชิงรัศมีสำคัญ

```csharp
// Enable graduations on the radial (X) axis
radarChart.AxisX.HasGraduations = true;
radarChart.AxisX.GraduationLineStyle = LineStyle.Thick;

// Enable graduations on the value (Y) axis
radarChart.AxisY.HasGraduations = true;
radarChart.AxisY.GraduationLineStyle = LineStyle.Thick;
```

**เคล็ดลับ:** ใช้ `LineStyle.Thick` ทำให้ระดับเด่นชัดเมื่อพิมพ์หรือดูบนหน้าจอความละเอียดสูง

### ขั้นตอนที่ 5: กำหนดชุดข้อมูลสำหรับแผนภูมิเรดาร์

แผนภูมิเรดาร์ต้องมีแกนประเภท (labels) และหนึ่งหรือหลายชุดข้อมูล ตัวอย่างเพิ่มชุดเดียวชื่อ *Series 1*

```csharp
// Remove any default series
radarChart.Series.Clear();

// Add a new series with three categories
radarChart.Series.Add(
    "Series 1",                     // Series name
    new[] { "A", "B", "C" },        // Category labels
    new[] { 10, 20, 15 }            // Corresponding values
);
```

**คำอธิบาย:** `Series.Add` เชื่อมแต่ละป้ายกำกับกับค่าตัวเลข แผนภูมิจะเชื่อมจุดอัตโนมัติเป็นรูปแบบสไปเดอร์ที่เป็นลักษณะเฉพาะ

### ขั้นตอนที่ 6: บันทึกเอกสารที่มีแผนภูมิเรดาร์

เลือกโฟลเดอร์ที่ต้องการให้ผลลัพธ์อยู่ ส่วนขยายไฟล์ `.docx` ทำให้เข้ากันได้กับ Microsoft Word, Google Docs, และ LibreOffice

```csharp
// Save the document with the radar chart
document.Save("RadialChartGraduations.docx");
```

หลังจากรันโปรแกรม, เปิด `RadialChartGraduations.docx` คุณจะเห็นแผนภูมิเรดาร์พร้อมระดับหนาบนแกนทั้งสองและชุดข้อมูลแสดงเป็นรูปหลายเหลี่ยมปิด

![แผนภูมิเรดาร์พร้อมระดับ](/images/radar-chart.png){: .align-center alt="แผนภูมิเรดาร์ที่สร้างในเอกสาร Word ด้วย Aspose.Words" }

**ผลลัพธ์ที่คาดหวัง:**  

* เอกสาร Word หนึ่งหน้า  
* แผนภูมิเรดาร์ขนาด 400 × 300 จุด อยู่กึ่งกลางหน้า  
* ระดับหนาบนแกนรัศมีและค่า  
* ชุดข้อมูลหนึ่งชุดชื่อ “Series 1” มีค่า 10, 20, 15  

## วิธีแทรกแผนภูมิลงในเอกสาร Word – การปรับแต่งเพิ่มเติม

แม้ขั้นตอนหลักข้างต้นจะตอบ **วิธีแทรกแผนภูมิเรดาร์** แล้ว, บางครั้งคุณอาจต้องการปรับแต่งเพิ่มเติม:

| การปรับแต่ง | ตัวอย่างโค้ด | เมื่อใดควรใช้ |
|---|---|---|
| เปลี่ยนชื่อแผนภูมิ | `radarChart.Title.Text = "Performance Overview";` | เพื่อให้ผู้อ่านเข้าใจบริบท |
| ตั้งค่าสีพื้นหลัง | `radarChart.ChartArea.FillFormat.Color = Color.LightYellow;` | เพื่อการสร้างแบรนด์หรือความแตกต่างทางภาพ |
| เพิ่มชุดข้อมูลที่สอง | `radarChart.Series.Add("Series 2", new[] {"A","B","C"}, new[] {12,18,22});` | เมื่อเปรียบเทียบชุดข้อมูลหลายชุด |
| ปรับขอบเขตแกน | `radarChart.AxisY.Minimum = 0; radarChart.AxisY.Maximum = 30;` | เพื่อให้แผนภูมิอยู่ในช่วงที่กำหนด |

คุณสามารถแทรกโค้ดเหล่านี้หลังจาก **ขั้นตอน 5** และก่อนบันทึกเอกสาร พวกมันแสดงตัวอย่างการปรับเปลี่ยนที่นักพัฒนามักถามเมื่อค้นหา **แทรกแผนภูมิลงในเอกสาร Word**  

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

* **ไม่มีใบอนุญาต** – แผนภูมิจะเรนเดอร์ได้, แต่จะมีลายน้ำการประเมิน โหลดใบอนุญาตที่ถูกต้องตั้งแต่ต้นใน `Main`  
* **ขนาดแผนภูมิไม่ถูกต้อง** – ใช้ค่าพิกเซลแทนจุดจะทำให้ผลลัพธ์บิดเบี้ยว Aspose.Words ต้องการค่าเป็นจุด (1 pt ≈ 1/72 in)  
* **ชุดข้อมูลว่าง** – ลืมเรียก `Series.Clear()` อาจทำให้ข้อมูลตัวอย่างที่เป็นค่าเริ่มต้นเขียนทับชุดข้อมูลของคุณ  

การจัดการกับปัญหาเหล่านี้จะทำให้แผนภูมิเรดาร์ปรากฏตามที่ต้องการ  

## สรุป

คุณได้เรียนรู้วิธี **สร้างแผนภูมิเรดาร์** ในไฟล์ Word ด้วย Aspose.Words for .NET คู่มือนี้ครอบคลุมทุกขั้นตอนตั้งแต่การตั้งค่าโครงการจนถึงการบันทึกเอกสารขั้นสุดท้าย แสดง **วิธีแทรกแผนภูมิเรดาร์** และ **แทรกแผนภูมิลงในเอกสาร Word** พร้อมการตั้งค่าระดับแกนและข้อมูลแบบกำหนดเอง ทดลองเพิ่มชุดข้อมูล, ชื่อ, และสไตล์เพิ่มเติมเพื่อให้แผนภูมิตอบสนองความต้องการรายงานของคุณ  

**ขั้นตอนต่อไป**

* สำรวจประเภทแผนภูมิอื่น (`ChartType.Pie`, `ChartType.Column`) เพื่อขยายเครื่องมืออัตโนมัติของคุณ  
* ผสานการสร้างแผนภูมิกับ mail merge เพื่อรายงานส่วนบุคคล  
* ตรวจสอบเอกสาร Aspose.Words เกี่ยวกับการจัดรูปแบบแผนภูมิสำหรับตัวเลือกสไตล์ขั้นสูง  

ขอให้สนุกกับการเขียนโค้ด!  


## สิ่งที่คุณควรเรียนต่อไปคืออะไร?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ

- [แทรกแผนภูมิพื้นที่ในเอกสาร Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [แทรกแผนภูมิคอลัมน์ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [สร้างแผนภูมิกระจายใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}