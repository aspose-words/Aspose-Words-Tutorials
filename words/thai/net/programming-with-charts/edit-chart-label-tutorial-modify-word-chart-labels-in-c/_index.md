---
category: general
date: 2026-09-11
description: บทเรียนการแก้ไขป้ายแผนภูมิที่แสดงวิธีการเปลี่ยนตำแหน่งป้ายแผนภูมิ, ปรับแต่งป้ายข้อมูลแผนภูมิ,
  ซ่อนชื่อหมวดหมู่ของแผนภูมิ, และแสดงค่าป้ายแผนภูมิด้วย Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: th
lastmod: 2026-09-11
og_description: บทเรียนการแก้ไขป้ายแผนภูมิจะพาคุณผ่านการเปลี่ยนตำแหน่งป้ายแผนภูมิ,
  การปรับแต่งป้ายข้อมูลของแผนภูมิ, การซ่อนชื่อหมวดหมู่ของแผนภูมิ, และการแสดงค่าป้ายแผนภูมิโดยใช้
  Aspose.Words สำหรับ .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: บทเรียนการแก้ไขป้ายแผนภูมิ – ปรับแต่งป้ายแผนภูมิ Word ด้วย C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: บทเรียนการแก้ไขป้ายแผนภูมิ – ปรับเปลี่ยนป้ายแผนภูมิของ Word ด้วย C#
url: /th/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แก้ไขบทแนะนำการตั้งค่าป้ายแผนภูมิ – ปรับแต่งป้ายแผนภูมิ Word ใน C#

หากคุณต้องการ **edit chart label tutorial** สำหรับเอกสาร Word คำแนะนำนี้จะแสดงให้คุณเห็นอย่างชัดเจนว่าจะเปลี่ยนตำแหน่งป้ายแผนภูมิอย่างไร ปรับแต่งป้ายข้อมูลแผนภูมิ ซ่อนชื่อหมวดหมู่ของแผนภูมิ และแสดงค่าป้ายแผนภูมิโดยใช้ Aspose.Words for .NET คุณจะได้เห็นตัวอย่างที่สมบูรณ์และสามารถรันได้ซึ่งคุณสามารถนำไปใส่ในโปรเจกต์ C# ใดก็ได้

การทำงานกับป้ายแผนภูมิเป็นความต้องการทั่วไปเมื่อสร้างรายงาน ใบแจ้งหนี้ หรือแดชบอร์ดโดยอัตโนมัติ คำแนะนำนี้ครอบคลุมทุกขั้นตอน—from การโหลดเอกสารจนถึงการบันทึกการเปลี่ยนแปลง—เพื่อให้คุณสร้างแผนภูมิที่ดูเป็นมืออาชีพโดยไม่ต้องแก้ไขด้วยตนเอง

## ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า  
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ประเมินผลชั่วคราว)  
* Visual Studio 2022 หรือ IDE ที่รองรับ C# ใดก็ได้  
* ไฟล์ Word (`Chart.docx`) ที่มีอย่างน้อยหนึ่งแผนภูมิ  

ไม่จำเป็นต้องใช้แพ็กเกจ NuGet เพิ่มเติมนอกจาก `Aspose.Words`.

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้าเนมสเปซ

สร้างแอปพลิเคชันคอนโซลใหม่และเพิ่มแพ็กเกจ NuGet ของ Aspose.Words:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

เปิด `Program.cs` และนำเข้าเนมสเปซที่จำเป็น:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

เนมสเปซเหล่านี้ให้คุณเข้าถึงคลาส `Document` สำหรับจัดการไฟล์ Word และคลาส `Chart` สำหรับจัดการองค์ประกอบแผนภูมิ

## ขั้นตอนที่ 2: โหลดเอกสาร Word ที่มีแผนภูมิ

บรรทัดแรกที่ทำงานจะโหลดเอกสารต้นฉบับ แทนที่ `YOUR_DIRECTORY` ด้วยพาธจริงที่ไฟล์ `Chart.docx` อยู่

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

การโหลดเอกสารจะสร้างการแสดงผลในหน่วยความจำที่คุณสามารถท่องและแก้ไขได้

## ขั้นตอนที่ 3: ดึงแผนภูมิแรกในเอกสาร

แผนภูมิจะถูกจัดเก็บเป็นโหนดลูกประเภท `NodeType.Chart` เมธอด `GetChild` จะค้นหาในโครงสร้างต้นไม้ของเอกสารและคืนค่าแผนภูมิที่คุณต้องการแก้ไข

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

หากเอกสารมีหลายแผนภูมิ คุณสามารถเปลี่ยนดัชนีเพื่อเลือกแผนภูมิอื่นได้

## ขั้นตอนที่ 4: เข้าถึงและปรับแต่งป้ายข้อมูลของซีรีส์แรก

แต่ละซีรีส์ของแผนภูมิมีอ็อบเจ็กต์ `DataLabel` ที่ควบคุมการแสดงผลของป้าย โค้ดด้านล่างแสดงการปรับแต่งสำคัญสี่ประการตามคีย์เวิร์ดรองของบทแนะนำ

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**ทำไมการตั้งค่าเหล่านี้ถึงสำคัญ**

* `DataLabelPosition.Center` ย้ายป้ายจากตำแหน่งเริ่มต้นที่อยู่นอกจุดไปยังกลางของจุดข้อมูล ทำให้แผนภูมอง่ายต่อการอ่านเมื่อจุดข้อมูลหนาแน่น  
* การตั้งค่า `Separator` แบบกำหนดเองช่วยให้คุณควบคุมวิธีการต่อชื่อซีรีส์ ค่า และส่วนอื่น ๆ  
* การซ่อนชื่อหมวดหมู่ (`ShowCategoryName = false`) ลดความรกของภาพเมื่อหมวดหมู่แสดงชัดเจนจากแกน  
* การเปิดใช้งาน `ShowValue` ทำให้ค่าข้อมูลจริงแสดงออก ซึ่งมักจำเป็นสำหรับรายงานทางการเงินหรือสถิติ

## ขั้นตอนที่ 5: บันทึกเอกสารที่แก้ไขแล้ว

หลังจากปรับคุณสมบัติป้ายแล้ว ให้บันทึกการเปลี่ยนแปลงกลับไปยังไฟล์ใหม่:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

ไฟล์ใหม่ (`CustomLabelChart.docx`) มีเลเอาต์แผนภูมิเหมือนเดิม แต่ป้ายจะปรากฏตามที่คุณกำหนด

## โค้ดต้นฉบับเต็ม

ด้านล่างเป็นโปรแกรมที่สมบูรณ์และพร้อมรัน คัดลอกไปยัง `Program.cs` ปรับพาธไฟล์ตามต้องการ แล้วรันโปรเจกต์

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เปิด `CustomLabelChart.docx` ใน Microsoft Word คุณควรเห็นป้ายของซีรีส์แรกอยู่กึ่งกลางแต่ละจุดข้อมูล แสดงเฉพาะค่าตัวเลข และใช้ “; ” เป็นตัวคั่น ชื่อหมวดหมู่จะไม่ปรากฏข้างค่าตัวเลขอีกต่อไป

## คำถามทั่วไปและกรณีขอบ

| Question | Answer |
|----------|--------|
| **ถ้าเอกสารไม่มีแผนภูมิจะเป็นอย่างไร?** | ตัวอย่างจะตรวจสอบว่าแผนภูมิเป็น `null` หรือไม่และออกจากโปรแกรมอย่างราบรื่นพร้อมข้อความบนคอนโซล |
| **ฉันสามารถแก้ไขป้ายสำหรับหลายซีรีส์ได้หรือไม่?** | ได้ครับ/ค่ะ. วนลูปผ่าน `chart.Series` แล้วใช้การตั้งค่า `DataLabel` เดียวกันกับแต่ละ `Series[i].DataLabel` |
| **ฉันจะเปลี่ยนสไตล์ฟอนต์ของป้ายได้อย่างไร?** | ใช้ `label.Font` (เช่น `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **`DataLabelPosition.Center` รองรับทุกประเภทแผนภูมิหรือไม่?** | ส่วนใหญ่ของแผนภูมิ 2‑D รองรับ แต่สำหรับแผนภูมิ 3‑D บางตำแหน่งอาจถูก Word เพิกเฉย |
| **ฉันต้องการใบอนุญาตสำหรับ Aspose.Words หรือไม่?** | โหมดประเมินผลทำงานได้แต่จะมีลายน้ำ ใบอนุญาตจะลบลายน้ำและเปิดใช้งานฟังก์ชันเต็ม |

## เคล็ดลับระดับมืออาชีพ

* **การประมวลผลแบบชุด:** ห่อหุ้มตรรกะการโหลดและบันทึกในเมธอดที่รับพาธอินพุตและเอาต์พุต ทำให้ง่ายต่อการประมวลผลหลายสิบเอกสารในลูป  
* **ประสิทธิภาพ:** ใช้ `Document` ตัวเดียวซ้ำเมื่อแก้ไขหลายแผนภูมิในไฟล์เดียวเพื่อหลีกเลี่ยง I/O ซ้ำ  
* **การทดสอบ:** ตรวจสอบการเปลี่ยนแปลงป้ายโดยอัตโนมัติด้วยการเปรียบเทียบภาพ (เช่น ใช้ตัวดู Word แบบ headless) หากต้องการยืนยันผลลัพธ์ใน pipeline CI  

## ขั้นตอนต่อไป

ตอนนี้คุณสามารถทำพื้นฐานของ **edit chart label tutorial** ได้แล้ว ลองสำรวจต่อไปนี้:

* **เปลี่ยนตำแหน่งป้ายแผนภูมิ** สำหรับซีรีส์อื่นหรือประเภทแผนภูมิอื่น  
* **ปรับแต่งรูปแบบป้ายข้อมูลแผนภูมิ** เช่น รูปแบบตัวเลข สีฟอนต์ หรือการเติมพื้นหลัง  
* **ซ่อนชื่อหมวดหมู่ของแผนภูมิ** แต่ยังแสดงชื่อซีรีส์สำหรับแผนภูมิหลายซีรีส์  
* **แสดงค่าป้ายแผนภูมิ** พร้อมค่าร้อยละสำหรับแผนภูมิพาย  

หัวข้อเหล่านี้จะทำให้คุณควบคุมรูปลักษณ์ของแผนภูมิ Word ได้ลึกซึ้งขึ้นและเตรียมพร้อมสำหรับสถานการณ์การรายงานขั้นสูง

---

*ขอให้สนุกกับการเขียนโค้ด! หากคุณพบว่าบทแนะนำนี้เป็นประโยชน์ โปรดแชร์ให้เพื่อนร่วมทีมหรือร่วมปรับปรุงบน GitHub.*

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบต่าง ๆ ในโครงการของคุณ

- [ปรับแต่งป้ายข้อมูลแผนภูมิ](/words/english/net/programming-with-charts/chart-data-label/)
- [ป้ายข้อมูลแผนภูมิ](/words/german/net/programming-with-charts/chart-data-label/)
- [ป้ายข้อมูลแผนภูมิ](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}