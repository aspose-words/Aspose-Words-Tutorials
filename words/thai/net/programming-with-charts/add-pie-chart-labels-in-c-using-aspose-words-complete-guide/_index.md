---
category: general
date: 2026-07-20
description: เพิ่มป้ายชื่อแผนภูมิวงกลมด้วย Aspose.Words สำหรับ .NET เรียนรู้วิธีเปลี่ยนป้ายชื่อแผนภูมิวงกลม
  แสดงป้ายเปอร์เซ็นต์ และอัปเดตป้ายชื่อชุดข้อมูลของแผนภูมิอย่างรวดเร็ว.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: th
lastmod: 2026-07-20
og_description: เพิ่มป้ายชื่อแผนภูมิวงกลมใน C# ด้วย Aspose.Words. เชี่ยวชาญการเปลี่ยนแปลงป้ายชื่อแผนภูมิวงกลม,
  แสดงป้ายเปอร์เซ็นต์, และอัปเดตป้ายชื่อซีรีส์ของแผนภูมิในไม่กี่ขั้นตอน.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: เพิ่มป้ายชื่อแผนภูมิวงกลมใน C# – คำแนะนำเต็มของ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: เพิ่มป้ายชื่อแผนภูมิวงกลมใน C# ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์
url: /th/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มป้ายแผนภูมิวงกลมใน C# ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์

ต้องการ **เพิ่มป้ายแผนภูมิวงกลม** ลงในเอกสาร Word ด้วย C# หรือไม่? ด้วย Aspose.Words คุณสามารถ **เปลี่ยนป้ายแผนภูมิวงกลม** และ **แสดงเปอร์เซ็นต์ของแผนภูมิวงกลม** ได้อย่างง่ายดายโดยตรงในไฟล์—ไม่ต้องปรับแก้ด้วยตนเองใน Word  

ในบทแนะนำนี้ เราจะอธิบายขั้นตอนอย่างละเอียดเพื่อ **แสดงป้ายเปอร์เซ็นต์**, ปรับตำแหน่งของป้าย, และแม้กระทั่ง **อัปเดตป้ายซีรีส์ของแผนภูมิ** สำหรับข้อมูลแบบไดนามิก สุดท้ายคุณจะได้โค้ดสั้นที่สามารถนำไปใช้ในโปรเจกต์ .NET ใดก็ได้

> **ดูตัวอย่างอย่างรวดเร็ว:** หลังจากทำตามคำแนะนำแล้ว การเปิดไฟล์ `.docx` ที่บันทึกไว้จะพบแผนภูมิวงกลมที่แต่ละชิ้นมีป้ายแสดงเปอร์เซ็นต์และอยู่ด้านนอกของชิ้นเพื่อความอ่านง่ายสูงสุด

---

## สิ่งที่คุณต้องการ

- **Aspose.Words for .NET** (เวอร์ชันล่าสุด ณ ปี 2026) คุณสามารถดาวน์โหลดได้จาก NuGet: `Install-Package Aspose.Words`.
- เอกสาร **Word** ที่มีแผนภูมิวงกลมหรือโดนัทอยู่แล้ว (เราจะเรียกมันว่า `Chart.docx`).
- ความคุ้นเคยพื้นฐานกับ **C#** และ Visual Studio (หรือ IDE ที่คุณชื่นชอบ).

เท่านี้—ไม่มีไลบรารีเพิ่มเติม, ไม่มี COM interop, เพียงโค้ดที่จัดการโดย .NET เท่านั้น

---

## เพิ่มป้ายแผนภูมิวงกลม – การทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมคอนโซล C# **ครบถ้วนและสามารถรันได้** ที่โหลดเอกสาร, แก้ไขแผนภูมิวงกลมแรก, และบันทึกผลลัพธ์ ทุกบรรทัดมีคอมเมนต์เพื่อให้คุณเข้าใจ **เหตุผล** ที่ทำเช่นนั้น ไม่ใช่แค่ **สิ่งที่ทำ**  

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เปิดไฟล์ `ChartWithCustomLabels.docx` ด้วย Microsoft Word คุณควรเห็นแผนภูมิวงกลม **ที่มีป้ายเปอร์เซ็นต์อยู่ด้านนอกแต่ละชิ้น** ป้ายจะมีลักษณะเช่น “35 %”, “20 %”, เป็นต้น ทำให้แผนภูมิเข้าใจได้ทันที

---

## เปลี่ยนป้ายแผนภูมิวงกลม: การจัดตำแหน่งและการจัดรูปแบบ

หากคุณต้องการเพียง **เปลี่ยนป้ายแผนภูมิวงกลม** โดยไม่แสดงเปอร์เซ็นต์ คุณสามารถปรับคุณสมบัติ `Position` ให้เป็นหนึ่งในค่าต่อไปนี้:

| ค่าตัวแปร Position | ผลลัพธ์ที่เห็น |
|---------------------|----------------|
| `InsideEnd`   | ป้ายอยู่ภายในชิ้น, ติดขอบของชิ้น. |
| `Center`      | ป้ายปรากฏที่กลางของชิ้น (เหมาะกับแผนภูมิขนาดเล็ก). |
| `OutsideEnd`  | ป้ายอยู่ด้านนอกของชิ้น, เชื่อมด้วยเส้นนำ (ค่าเริ่มต้นของเรา). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**เคล็ดลับ:** `OutsideEnd` ทำงานดีที่สุดเมื่อแผนภูมิมีหลายชิ้น; จะช่วยป้องกันข้อความทับซ้อน

---

## แสดงป้ายเปอร์เซ็นต์บนแผนภูมิวงกลม

คุณสมบัติ `ShowPercentage` เป็น **ค่าแบบบูลีน** การตั้งค่าเป็น `true` จะบอก Aspose.Words ให้คำนวณส่วนแบ่งของแต่ละชิ้นจากแหล่งข้อมูลพื้นฐาน  

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

คุณยังสามารถรวมกับ `ShowValue` หากต้องการทั้งค่าตัวเลขดิบ **และ** เปอร์เซ็นต์:  

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

เมื่อเปิดใช้งานทั้งสองค่า ป้ายจะมีรูปแบบเช่น “45 % (120)”.

---

## อัปเดตป้ายซีรีส์ของแผนภูมิสำหรับข้อมูลแบบไดนามิก

บ่อยครั้งคุณจะสร้างแผนภูมิแบบเรียลไทม์—เช่น ยอดขายรายเดือนหรือผลสำรวจ เพื่อ **อัปเดตป้ายซีรีส์ของแผนภูมิ** ผ่านโค้ด ให้แก้ไขคอลเลกชัน `Series` ก่อนที่จะจัดการกับป้ายข้อมูล:  

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

โค้ดสั้นนี้แสดงวิธี **อัปเดตป้ายซีรีส์ของแผนภูมิ** สำหรับซีรีส์ใดก็ได้ ไม่ใช่แค่ซีรีส์แรกเท่านั้น มีประโยชน์เมื่อคุณสร้างรายงานที่รวมข้อมูลจริงกับการคาดการณ์

---

## กรณีขอบและข้อผิดพลาดทั่วไป

| สถานการณ์ | สิ่งที่ควรระวัง | วิธีแก้ |
|-----------|-------------------|-----|
| **แผนภูมิไม่ใช่แบบวงกลมหรือโดนัท** | `Position` อาจไม่มีผลต่อการแสดงผล. | ตรวจสอบว่า `chart.Type` เป็น `ChartType.Pie` หรือ `ChartType.Doughnut`. |
| **ไม่พบแผนภูมิ** | `GetChild` คืนค่า `null`. | เพิ่มเงื่อนไขตรวจสอบ (ดูโค้ด) และบันทึกข้อความแจ้งที่เป็นประโยชน์. |
| **เวอร์ชัน Word เก่า** | ฟีเจอร์บางอย่างของป้ายอาจถูกละเลย. | บันทึกเป็น `.docx` (รูปแบบใหม่) เพื่อรับประกันการสนับสนุนเต็มรูปแบบ. |
| **จำนวนชิ้นมาก** | ป้ายอาจทับซ้อนแม้ใช้ `OutsideEnd`. | พิจารณาลดจำนวนชิ้นหรือเพิ่มขนาดแผนภูมิ. |

---

## ตัวอย่างทำงานเต็มรูปแบบ (คัดลอก‑วาง)

ด้านล่างเป็น **โปรแกรมทั้งหมด** ที่คุณสามารถคัดลอกไปยังโปรเจกต์คอนโซลใหม่ เพียงเปลี่ยน `YOUR_DIRECTORY` ให้เป็นโฟลเดอร์ที่เก็บ `Chart.docx`.



## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ

- [ตั้งค่าตัวเลือกเริ่มต้นสำหรับป้ายข้อมูลในแผนภูมิ](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [ปรับแต่งซีรีส์เดียวในแผนภูมิ](/words/english/net/programming-with-charts/single-chart-series/)
- [แทรกแผนภูมิคอลัมน์ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}