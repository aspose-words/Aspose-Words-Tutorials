---
category: general
date: 2026-07-19
description: แยกชิ้นส่วนของแผนภูมิวงกลมโดยใช้ Aspose.Words สำหรับ C#. เรียนรู้วิธีการแยกชิ้นส่วนของพาย,
  ปรับขนาดรูของโดนัท, และเปลี่ยนจุดข้อมูลของแผนภูมิอย่างรวดเร็ว.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: th
lastmod: 2026-07-19
og_description: ระเบิดชิ้นส่วนของแผนภูมิวงกลมด้วย Aspose.Words สำหรับ C#. คู่มือนี้จะแสดงวิธีการระเบิดชิ้นส่วนของแผนภูมิวงกลม,
  ปรับขนาดรูของโดนัท, และเปลี่ยนจุดข้อมูลของแผนภูมิอย่างมีประสิทธิภาพ.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: แยกชิ้นกราฟวงกลมใน C# – บทเรียน Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: แยกชิ้นกราฟวงกลมใน C# ด้วย Aspose.Words – คู่มือเต็ม
url: /th/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การแยกชิ้นส่วนแผนภูมิวงกลมใน C# ด้วย Aspose.Words – คู่มือเต็ม

เคยสงสัยไหมว่า **การแยกชิ้นส่วนแผนภูมิวงกลม** ในเอกสาร Word ด้วย C# ทำอย่างไร? คุณไม่ได้เป็นคนเดียว ไม่ว่าคุณจะกำลังเตรียมสไลด์การขายหรือแสดงผลสำรวจ การแยกชิ้นส่วนจะดึงความสนใจไปยังจุดที่คุณต้องการ ในบทแนะนำนี้เราจะพาคุณผ่านกระบวนการทั้งหมด—โหลดเอกสาร, ดึงแผนภูมิ, แยกชิ้นส่วนแรก, ปรับขนาดรูโดนัท, และแม้แต่เปลี่ยนค่าข้อมูลของแผนภูมิ

เราจะเพิ่มแนวคิดรองที่คุณอาจกำลังมองหา: **วิธีแยกชิ้นส่วนแผนภูมิวงกลม**, **ปรับขนาดรูโดนัท**, และ **เปลี่ยนค่าข้อมูลของแผนภูมิ** ไม่มีส่วนเกิน เพียงโซลูชันพร้อมคัดลอก‑วางครบถ้วน

---

## สิ่งที่คุณต้องมี

ก่อนที่เราจะดำเนินการต่อ ตรวจสอบให้แน่ใจว่าคุณมี:

- **Aspose.Words for .NET** (เวอร์ชันล่าสุด ณ วันที่ 2026‑07‑19) คุณสามารถดาวน์โหลดจาก NuGet ด้วยคำสั่ง `Install-Package Aspose.Words`
- โปรเจกต์ **.NET 6+** (หรือ .NET Framework 4.7.2+ หากคุณยังใช้รุ่นเก่า)
- ไฟล์ Word (`Chart.docx`) ที่มีแผนภูมิวงกลมหรือโดนัทอยู่แล้ว หากไม่มี ให้สร้างแผนภูมิง่าย ๆ ใน Word แล้วบันทึก

เท่านี้—ไม่มีไลบรารีเพิ่มเติม ไม่มี COM interop เพียงโค้ดที่จัดการได้ทั้งหมด

---

## การแยกชิ้นส่วนแผนภูมิวงกลม – ขั้นตอน‑ตาม‑ขั้นตอน

ด้านล่างเราจะแบ่งงานเป็นขั้นตอนย่อย ๆ แต่ละส่วนมีหัวข้อชัดเจน, โค้ดสั้น ๆ, และคำอธิบายสั้น ๆ เกี่ยวกับ *เหตุผล* ที่ทำเช่นนั้น

### ขั้นตอนที่ 1: ติดตั้งและอ้างอิง Aspose.Words

เริ่มแรกให้เพิ่มแพคเกจ Aspose.Words เข้าในโปรเจกต์ของคุณ ใน Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **เคล็ดลับ:** หากคุณใช้ NuGet UI ของ Visual Studio ให้ค้นหา “Aspose.Words” แล้วคลิก Install วิธีนี้จะทำให้คุณได้เวอร์ชันล่าสุดพร้อมการแก้บั๊กและความสามารถในการทำงานกับแผนภูมิแบบพร้อมใช้งาน

### ขั้นตอนที่ 2: โหลดเอกสาร Word ที่มีแผนภูมิ

เราต้องการอ็อบเจกต์ `Document` ที่ชี้ไปยังไฟล์ `.docx` ที่มีแผนภูมิที่ต้องการแก้ไข

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **ทำไมต้องทำเช่นนี้:** `Document` เป็นจุดเริ่มต้นของทุกการทำงานใน Aspose.Words การตรวจสอบแผนภูมิก่อนจะช่วยหลีกเลี่ยงการอ้างอิงค่า null เมื่อเราพยายามแยกชิ้นส่วนต่อไป

### ขั้นตอนที่ 3: ดึงโหนดแผนภูมิลำดับแรก

ตัวอย่างส่วนใหญ่สมมติว่ามีแผนภูมิเพียงหนึ่งอัน เราจะดึงอันแรก หากคุณมีหลายแผนภูมิให้ปรับดัชนีตามต้องการ

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **หมายเหตุ:** การแคสต์เป็น `Chart` จะปลอดภัยหลังจากที่เรายืนยันว่ามีแผนภูมิอยู่แล้ว อ็อบเจกต์นี้ให้เราเข้าถึง series, data points, และการตั้งค่าเฉพาะประเภทแผนภูมิ

### ขั้นตอนที่ 4: แยกชิ้นส่วนแรกของแผนภูมิวงกลม

นี่คือหัวใจของเรื่อง—**วิธีแยกชิ้นส่วนแผนภูมิวงกลม** เราจะตั้งค่า `Exploded` ของ data point แรก

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **ทำไมวิธีนี้ถึงได้ผล:** `Exploded` บอก Word ให้ดึงชิ้นส่วนนั้นออกจากศูนย์กลาง สร้างเอฟเฟกต์ “pie chart ที่แยกส่วน” แบบคลาสสิก ค่าของ property เป็น boolean การตั้งเป็น `true` ก็พอ

### ขั้นตอนที่ 5: ปรับขนาดรูโดนัท (หากเป็นแผนภูมิโดนัท)

หากแผนภูมิของคุณเป็นโดนัท คุณอาจต้องการ **ปรับขนาดรูโดนัท** ขนาดรูเป็นเปอร์เซ็นต์ของรัศมีแผนภูมิ

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **ความหมายของตัวเลข:** ค่า `30` หมายความว่าวงในจะครอบคลุม 30 % ของรัศมีทั้งหมด ทำให้แถบภายนอกหนาขึ้น

### ขั้นตอนที่ 6: เปลี่ยนค่าข้อมูลของแผนภูมิ (ตามต้องการ)

บางครั้งคุณต้อง **เปลี่ยนค่าข้อมูลของแผนภูมิ** — เช่น มีการอัปเดตตัวเลขพื้นฐานและต้องการให้กราฟแสดงผลใหม่

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **เหตุผลที่ทำเช่นนี้:** การเปลี่ยนค่าของ data point จะทำให้เปอร์เซ็นต์ของชิ้นส่วนคำนวณใหม่โดยอัตโนมัติ ทำให้แผนภูมิมีความแม่นยำโดยไม่ต้องแก้ไขด้วยตนเองใน Word

### ขั้นตอนที่ 7: บันทึกเอกสารที่แก้ไขแล้ว

สุดท้ายให้เขียนการเปลี่ยนแปลงกลับไปยังดิสก์ คุณสามารถเขียนทับไฟล์เดิมหรือสร้างไฟล์ใหม่ก็ได้ตามต้องการ

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **เคล็ดลับ:** ใช้ `SaveFormat.Docx` หากต้องการระบุรูปแบบอย่างชัดเจน แต่ `Save(string)` จะตรวจจับรูปแบบจากนามสกุลไฟล์โดยอัตโนมัติ

---

## ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิด `FormattedChart.docx` ใน Microsoft Word คุณควรเห็น:

- ชิ้นส่วนแรกของแผนภูมิวงกลม **แยกออก** ไปด้านนอก
- หากเป็นแผนภูมิโดนัท รูกลางจะมีขนาด **30 %** ของรัศมี
- ค่าข้อมูลที่แก้ไขแล้วจะแสดงเป็นค่าที่คุณตั้งไว้

ด้านล่างเป็นตัวอย่างภาพจำลองของชิ้นส่วนที่แยกออก (ภาพเพื่ออธิบายเท่านั้น)

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*ข้อความแทนภาพ:* **ชิ้นส่วนแผนภูมิวงกลมที่แยกออก** แสดงส่วนที่ดึงห่างจากศูนย์กลางในเอกสาร Word

---

## คำถามทั่วไป & กรณีขอบ

**ถ้าแผนภูมิไม่ใช่วงกลมหรือโดนัทล่ะ?**  
โค้ดจะตรวจสอบ `ChartType` ก่อนที่จะตั้งค่า `Exploded` หรือ `HoleSize` สำหรับแผนภูมิบาร์, ไลน์ หรือเอเรียย์ คุณสมบัติเหล่านั้นไม่มีอยู่ ดังนั้นตรรกะจะข้ามอย่างปลอดภัย

**ฉันสามารถแยกหลายชิ้นส่วนได้หรือไม่?**  
ทำได้เลย ลูปผ่าน `chart.PieChartData.Series[0].DataPoints` แล้วตั้ง `Exploded = true` ที่ดัชนีใดก็ได้ที่ต้องการ

**ต้องกังวลเรื่องรูปแบบตัวเลขตามวัฒนธรรมหรือไม่?**  
Aspose.Words เก็บค่าตัวเลขเป็น double โดยไม่ขึ้นกับ locale ดังนั้นคุณจึงปลอดภัยจากปัญหาเครื่องหมายจุลภาคหรือจุด

**แผนภูมิที่ฝังอยู่ในส่วนหัว/ส่วนท้ายล่ะ?**  
ใช้ `doc.GetChildNodes(NodeType.Chart, true)` เพื่อดึงแผนภูมิทั้งหมด แล้วตรวจสอบ `ParentNode` ของแต่ละโหนดเพื่อดูตำแหน่งที่อยู่ การแยกชิ้นส่วนทำงานเช่นเดียวกัน

---

## สรุป

ตอนนี้คุณมีโซลูชันพร้อมคัดลอก‑วางสำหรับ **การแยกชิ้นส่วนแผนภูมิวงกลม** ด้วย Aspose.Words ใน C# ครอบคลุมขั้นตอนทั้งหมด—from การโหลดเอกสาร, ดึงแผนภูมิ, แยกชิ้นส่วน, **ปรับขนาดรูโดนัท**, ไปจนถึง **การเปลี่ยนค่าข้อมูลของแผนภูมิ** และบันทึกไฟล์

ลองทดลองเพิ่มเติม: แยกชิ้นส่วนอื่น, ปรับขนาดรูเป็น 45 %, หรืออัปเดตหลายค่าในคราวเดียว Aspose.Words API ทำให้การปรับแต่งเหล่านี้ง่ายดายและผลลัพธ์จะแสดงทันทีเมื่อเปิดไฟล์ Word

---

### สิ่งต่อไปที่คุณควรทำ

- **จัดรูปแบบชิ้นส่วนที่แยกออก** (เปลี่ยนสีเติม, เส้นขอบ, หรือเพิ่มป้ายข้อมูล) ค้นหา “Aspose.Words chart formatting”
- **ทำการประมวลผลแบบชุด** ของหลายเอกสาร—วนลูปโฟลเดอร์, แยกชิ้นส่วน, แล้วบันทึกเวอร์ชันใหม่
- **รวมกับ Aspose.Slides** หากต้องการแผนภูมิเดียวกันใน PowerPoint

หากมีคำถามเพิ่มเติมเกี่ยวกับการจัดการแผนภูมิ หรืออยากเจาะลึกประเภทแผนภูมิอื่น ๆ แสดงความคิดเห็นด้านล่าง แล้วขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานครบถ้วนพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจกต์ของคุณ

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}