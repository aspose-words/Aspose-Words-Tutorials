---
category: general
date: 2026-10-13
description: 'บันทึกเอกสารที่แก้ไขแล้วหลังจากปรับแต่งแผนภูมิวงกลม: แยกชิ้นส่วน, เปลี่ยนมุมของชิ้นส่วนแรก,
  และแสดงป้ายเปอร์เซ็นต์ใน C#'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: th
lastmod: 2026-10-13
og_description: บันทึกเอกสารที่แก้ไขหลังจากปรับแต่งแผนภูมิวงกลมใน C# เรียนรู้วิธีแยกชิ้นส่วนของแผนภูมิวงกลม,
  เปลี่ยนมุมของชิ้นแรก, และแสดงป้ายเปอร์เซ็นต์.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: บันทึกเอกสารที่แก้ไขพร้อมชิ้นส่วนแผนภูมิวงกลมที่แยกออก – คู่มือ C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: บันทึกเอกสารที่แก้ไขพร้อมส่วนของแผนภูมิวงกลมที่แยกออกใน C#
url: /th/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# บันทึกเอกสารที่แก้ไขพร้อมชิ้นส่วนพายชาร์ตที่แยกออกใน C#

หากคุณต้องการ **save modified document** หลังจากปรับแต่งพายชาร์ตใน Word คำแนะนำนี้จะแสดงวิธีทำอย่างละเอียด คุณจะได้เรียนรู้การแยกชิ้นส่วนพายชาร์ต, การเปลี่ยนมุมของชิ้นส่วนแรก, และการแสดงป้ายเปอร์เซ็นต์—ทั้งหมดด้วยไม่กี่บรรทัดของโค้ด C#.

การปรับแต่งชาร์ตเป็นความต้องการทั่วไปเมื่อสร้างรายงาน, ใบแจ้งหนี้ หรือแดชบอร์ดโดยอัตโนมัติ เมื่อจบบทเรียนนี้คุณจะสามารถโหลดไฟล์ DOCX, แก้ไขลักษณะของชาร์ต, และ **save modified document** พร้อมสำหรับการแจกจ่าย.

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 หรือใหม่กว่า (รุ่นทดลองฟรีหรือสำเนาที่ได้รับใบอนุญาต)
- ไฟล์ Word (`input.docx`) ที่มีพายชาร์ตเดียว
- Visual Studio 2022 หรือ IDE C# ใดก็ได้

> **Tip:** แพคเกจ NuGet ของ Aspose.Words ถูกเพิ่มด้วยคำสั่ง `dotnet add package Aspose.Words`.

## ขั้นตอนที่ 1: โหลดเอกสาร Word ที่มีชาร์ต

ขั้นตอนแรกคือการเปิดไฟล์ DOCX ต้นฉบับ คลาส `Document` แทนไฟล์ Word ทั้งหมดในหน่วยความจำ

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

การโหลดเอกสารทำให้คุณเข้าถึงทุกโหนดได้เต็มที่ รวมถึงรูปทรงที่เป็นโฮสต์ของชาร์ต

## ขั้นตอนที่ 2: ดึงรูปทรงชาร์ตแรกจากเอกสาร

ชาร์ตถูกเก็บอยู่ภายในโหนด `Shape` คุณสามารถค้นหาชาร์ตแรกด้วย `GetChild`

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

หากเอกสารมีหลายชาร์ต ให้ปรับดัชนี (`0`) หรือวนลูปผ่านคอลเลกชัน บรรทัดนี้ทำให้คุณมีการอ้างอิงถึงอ็อบเจ็กต์ `Chart` ที่จะทำการแก้ไข

## ขั้นตอนที่ 3: แยกชิ้นส่วนพายชาร์ต

การแยกชิ้นส่วนทำให้ชิ้นนั้นแยกออกจากส่วนอื่นของพาย ช่วยให้ชาร์ตอ่านง่ายขึ้น คุณสมบัติ `Explode` ทำงานกับทั้งซีรีส์

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

การตั้งค่า `Explode` เป็น `true` **explodes pie chart slices** สำหรับทั้งซีรีส์ ซึ่งมีประโยชน์เมื่อคุณต้องการให้ทุกชิ้นส่วนโดดเด่น

## ขั้นตอนที่ 4: เปลี่ยนมุมของชิ้นส่วนแรก

บางครั้งคุณอาจต้องการให้ชิ้นส่วนแรกเริ่มที่มุมกำหนดเอง เช่น เพื่อให้สอดคล้องกับแนวทางการออกแบบ

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

คุณสมบัติ `FirstSliceAngle` **changes first slice** ทิศทาง โดยหมุนพายทั้งหมดให้ชิ้นส่วนแรกเริ่มที่ 30 องศา

## ขั้นตอนที่ 5: แสดงป้ายเปอร์เซ็นต์บนชิ้นส่วนพาย

การแสดงส่วนประกอบเชิงตัวเลขของแต่ละชิ้นส่วนมักจำเป็นในรายงาน ธง `DataLabel.ShowPercentage` เปิดค่าเปอร์เซ็นต์

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

ขั้นตอนนี้ **show percentage labels** โดยตรงบนชาร์ต ซึ่งยังตอบสนองความต้องการ **display percentages pie**

## ขั้นตอนที่ 6: บันทึกเอกสารที่แก้ไข

หลังจากปรับแต่งทั้งหมดแล้ว ให้บันทึกการเปลี่ยนแปลงลงไฟล์ใหม่ เมธอด `Save` จะเขียนไฟล์ DOCX ที่อัปเดตลงดิสก์

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

ตอนนี้คุณมี **save modified document** ที่มีพายชาร์ตที่แยกออก, ชิ้นส่วนแรกที่หมุน, และป้ายเปอร์เซ็นต์ที่มองเห็นได้

![บันทึกเอกสารที่แก้ไขแสดงชิ้นส่วนพายชาร์ตที่แยกออกและป้ายเปอร์เซ็นต์](/images/pie-chart-exploded.png "บันทึกเอกสารที่แก้ไขพร้อมชิ้นส่วนพายชาร์ตที่แยกออกและป้ายเปอร์เซ็นต์")

*ภาพหน้าจอแสดงผลลัพธ์สุดท้ายหลังจากบันทึกเอกสารแล้ว.*

## ตัวอย่างเต็มที่สามารถรันได้

เมื่อนำส่วนต่าง ๆ มารวมกัน นี่คือโปรแกรมเต็มที่คุณสามารถคัดลอก‑วางลงในโครงการคอนโซล:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### ผลลัพธ์ที่คาดหวัง

การเปิด `output.docx` จะทำให้แสดงพายชาร์ตที่:

- ทุกชิ้นส่วนแยกออกเล็กน้อย (**exploded pie chart slices**)
- ชิ้นส่วนแรกเริ่มที่การเลื่อน 30 องศา (**change first slice**)
- แต่ละชิ้นส่วนแสดงส่วนแบ่งเป็นเปอร์เซ็นต์ (**show percentage labels**, **display percentages pie**)
- ไฟล์ได้ถูก **save modified document** โดยไม่ทำให้ต้นฉบับเปลี่ยนแปลง

## คำถามทั่วไปและกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ถ้าเอกสารไม่มีชาร์ต?** | โค้ดจะตรวจสอบ `null` หลังจาก `GetChild`. หากไม่มีชาร์ต คุณสามารถเพิ่มชาร์ตโปรแกรมmatically หรือยกเลิกพร้อมข้อความชัดเจน. |
| **ฉันสามารถแยกชิ้นส่วนเดียวได้หรือไม่?** | ได้ ใช้ `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` โดยที่ `i` คือดัชนีของชิ้นส่วน. |
| **ฉันจะเปลี่ยนรูปแบบป้ายอย่างไร (เช่น แสดงค่า + %)?** | ตั้งค่า `chart.PieChart.DataLabel.ShowValue = true;` และโดยเลือก `chart.PieChart.DataLabel.ShowPercentage = true;` เพื่อรวมทั้งสอง. |
| **สไตล์ของชาร์ตยังคงอยู่หลังการบันทึกหรือไม่?** | Aspose.Words รักษาการจัดรูปแบบทั้งหมด รวมถึงสีและฟอนต์ เมื่อคุณ **save modified document**. |
| **ฉันสามารถประมวลผลหลายชาร์ตในไฟล์เดียวได้หรือไม่?** | วนลูปผ่านโหนด `Shape` ทั้งหมดด้วย `NodeType.Shape` และกรองด้วย `shape.HasChart`. ใช้ขั้นตอนเดียวกันกับแต่ละชาร์ต. |

## สรุป

ตอนนี้คุณรู้วิธี **save modified document** หลังจากปรับแต่งพายชาร์ตใน Word ด้วยโปรแกรม คำแนะนำได้ครอบคลุมการแยกชิ้นส่วนพายชาร์ต, การเปลี่ยนมุมของชิ้นส่วนแรก, และการแสดงป้ายเปอร์เซ็นต์—ตอบสนองความต้องการ **show percentage labels**, **explode pie chart slices**, **display percentages pie**, และ **change first slice**.

ต่อไป, พิจารณาการสำรวจ:

- เพิ่มชุดข้อมูลแบบไดนามิก (`chart.Series.Add(...)`)
- ปรับตำแหน่งของ legend และหัวข้อชาร์ต
- แปลง DOCX เป็น PDF พร้อมคงสไตล์ของชาร์ต

คุณสามารถทดลองกับมุมต่าง ๆ, การตั้งค่าแยกชิ้นส่วน, หรือรูปแบบป้ายเพื่อให้ตรงกับความต้องการของรายงานของคุณได้เลย ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ

- [วิธีบันทึกเอกสารที่แก้ไขใน C# ด้วย Aspose.Words – คู่มือขั้นตอน](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [อัปเดตข้อมูลซีรีส์ของชาร์ตในเอกสาร Word โดยใช้ Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [แทรกคอลัมน์ชาร์ตในเอกสาร Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}