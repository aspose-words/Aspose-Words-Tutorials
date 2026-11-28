---
category: general
date: 2026-06-02
description: แสดงคำอธิบายกราฟในเอกสาร Word ด้วย C# เรียนรู้วิธีเพิ่มคำอธิบายกราฟ,
  ใช้สไตล์กราฟที่กำหนดไว้ล่วงหน้า, และปรับแต่งภาพกราฟใน Word ภายในไม่กี่นาที.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: th
og_description: แสดงคำอธิบายแผนภูมิในเอกสาร Word ทันที คู่มือนี้จะพาคุณผ่านการเพิ่มคำอธิบายแผนภูมิ
  การใช้สไตล์แผนภูมิกำหนดล่วงหน้า และการจัดการกรณีเฉพาะ
og_title: แสดงคำอธิบายแผนภูมิใน Word – คำแนะนำ C# ฉบับเต็ม
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: แสดงคำอธิบายแผนภูมิใน Word ด้วย C# – คู่มือขั้นตอนเต็มรูปแบบ
url: /th/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แสดงคำอธิบายแผนภูมิใน Word ด้วย C# – คู่มือขั้นตอนเต็ม

เคยสงสัย **วิธีเพิ่มคำอธิบายแผนภูมิ** ที่อยู่ในเอกสาร Word หรือไม่? คุณไม่ได้เป็นคนเดียว ในรายงานหลายฉบับ การไม่มีคำอธิบายทำให้ข้อมูลดูเป็นรหัสลับ และการแก้ไขไม่ควรเป็นเรื่องยุ่งยาก.  

ในบทแนะนำนี้ เราจะ **แสดงคำอธิบายแผนภูมิ** ในไฟล์ Word ด้วย Aspose.Words for .NET, ใช้สไตล์แผนภูมิกำหนดล่วงหน้า, และทำให้คำอธิบายปรากฏตรงตำแหน่งที่คุณต้องการ เมื่อเสร็จคุณจะได้ตัวอย่างที่พร้อมรันซึ่งสามารถนำไปใส่ในโปรเจกต์ C# ใดก็ได้.

## สิ่งที่คู่มือนี้ครอบคลุม

เราจะเดินผ่านกระบวนการทั้งหมด:

1. โหลดไฟล์ *.docx* ที่มีแผนภูมิอยู่แล้ว.  
2. ดึงแผนภูมิแรก (หรือแผนภูมิใด ๆ ที่คุณต้องการ).  
3. **ใช้สไตล์แผนภูมิกำหนดล่วงหน้า** เพื่อให้ภาพดูเป็นมืออาชีพ.  
4. **แสดงคำอธิบายแผนภูมิ**, วางไว้ด้านขวา, และจัดการกรณีพิเศษเช่นแผนภูมิ Waterfall.  
5. บันทึกเอกสารที่แก้ไข.

ไม่มีเครื่องมือภายนอก, ไม่มีการปรับแต่ง UI ด้วยมือ—เพียงโค้ดเท่านั้น เงื่อนไขเบื้องต้นคือการอ้างอิงแพคเกจ NuGet ของ Aspose.Words (เวอร์ชัน 23.10 หรือใหม่กว่า) และความเข้าใจพื้นฐานของ C#.

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (ตัวอย่างทำงานกับ .NET Framework 4.7.2 ด้วย).  
- ไลบรารี Aspose.Words for .NET ติดตั้งแล้ว (`Install-Package Aspose.Words`).  
- ไฟล์ Word (`input.docx`) ที่มีแผนภูมิอย่างน้อยหนึ่งรายการ.  
- Visual Studio, Rider, หรือ IDE ใด ๆ ที่คุณชอบ.

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และโหลดเอกสาร

แรกเริ่ม, สร้างแอปคอนโซล (หรือรวมโค้ดนี้เข้าในโปรเจกต์ที่มีอยู่). เพิ่มคำสั่ง `using` และโหลดไฟล์ `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **ทำไมเรื่องนี้สำคัญ:** การโหลดเอกสารเป็นพื้นฐาน หากไม่มีอินสแตนซ์ `Document` คุณจะไม่สามารถเข้าถึงอ็อบเจกต์แผนภูมิที่ Aspose.Words เปิดเผยได้.

## ขั้นตอนที่ 2: ดึงแผนภูมิเป้าหมาย

แผนภูมิถูกเก็บเป็นโหนดภายในโครงสร้างต้นไม้ของเอกสาร เมธอด `GetChild` ทำการค้นหาแบบลึก ช่วยให้เราดึงแผนภูมิแรกไม่ว่ามันจะอยู่ที่ส่วนใด (หัวกระดาษ, เนื้อหา, ส่วนท้าย, ฯลฯ).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **เคล็ดลับ:** หากคุณมีหลายแผนภูมิ, เปลี่ยนดัชนี `0` เป็น `1`, `2`, … หรือวนลูปผ่าน `doc.GetChildNodes(NodeType.Chart, true)`.

## ขั้นตอนที่ 3: ใช้สไตล์ภาพลักษณ์กำหนดล่วงหน้า

แผนภูมิที่ดูดีมักเริ่มจากสไตล์ Aspose.Words มาพร้อมกับสไตล์ในตัวหลายสิบแบบ; `ChartStyle.Style12` เป็นตัวเลือกที่เรียบง่ายและทันสมัย.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **วิธีการทำงาน:** คุณสมบัติ `Style` เชื่อมต่อกับสไตล์แผนภูมิใน Word ที่มีอยู่ใน UI การเลือกสไตล์กำหนดล่วงหน้าช่วยคุณไม่ต้องตั้งค่าสี, ฟอนต์, และเครื่องหมายด้วยตนเอง.

## ขั้นตอนที่ 4: เปิดใช้งานคำอธิบายและกำหนดตำแหน่ง

ต่อไปคือจุดเด่นของการแสดง—**แสดงคำอธิบายแผนภูมิ** เราจะเปิดคำอธิบาย แล้ววางไว้ด้านขวาของแผนภูมิ.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **ทำไมถึงวางด้านขวา?** การวางคำอธิบายทางด้านขวาช่วยให้พื้นที่ข้อมูลกว้างขึ้น ซึ่งเป็นประโยชน์โดยเฉพาะสำหรับแผนภูมิแท่งหรือคอลัมน์.

## ขั้นตอนที่ 5: จัดการแผนภูมิ Waterfall (กรณีพิเศษ)

แผนภูมิ Waterfall ทำงานแตกต่างเล็กน้อย; คำอธิบายอาจถูกซ่อนโดยค่าเริ่มต้น เงื่อนไขตรวจสอบต่อไปนี้ทำให้แน่ใจว่าคำอธิบายจะแสดงเมื่อประเภทแผนภูมิเป็น Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **หมายเหตุกรณีขอบ:** เวอร์ชัน Word เก่าบางรุ่นไม่สนใจ `HasLegend` สำหรับแผนภูมิ Waterfall ดังนั้นการตั้งค่า `Legend.Show` อย่างชัดเจนจึงรับประกันการมองเห็น.

## ขั้นตอนที่ 6: บันทึกเอกสารที่แก้ไข

สุดท้าย, เขียนการเปลี่ยนแปลงกลับไปยังดิสก์ คุณสามารถเขียนทับไฟล์เดิมหรือสร้างไฟล์ใหม่ได้.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

การรันโปรแกรมจะสร้าง `output.docx` ที่มีคำอธิบายแสดงด้านขวา และใช้สไตล์ `Style12`. เปิดไฟล์ใน Word เพื่อตรวจสอบผลลัพธ์.

## ตัวอย่างทำงานเต็ม (รวมทุกขั้นตอน)

ด้านล่างเป็นโค้ดที่สมบูรณ์พร้อมรัน คัดลอกและวางลงใน `Program.cs` (หรือไฟล์ C# ใดก็ได้) แล้วปรับเส้นทางไฟล์ตามต้องการ.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** การเปิด `output.docx` จะแสดงแผนภูดิมาตรฐานพร้อมคำอธิบายจัดชิดขวา ใช้สไตล์ `Style12` ที่ทันสมัย ทุกชุดข้อมูลจะมีป้ายกำกับชัดเจน ทำให้แผนภูมิเข้าใจได้ทันที.

## คำถามที่พบบ่อย (FAQ)

### วิธีเพิ่มคำอธิบายให้กับแผนภูมิเฉพาะ (ไม่ใช่แผนภูมิแรก)?

เปลี่ยนดัชนี `0` ใน `GetChild(NodeType.Chart, 0, true)` เป็นตำแหน่งเริ่มจากศูนย์ของแผนภูมิเป้าหมายของคุณ, หรือวนลูปผ่านโหนดแผนภูมิทั้งหมด:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### ฉันสามารถวางคำอธิบายที่ด้านล่างแทนด้านขวาได้ไหม?

ได้เลย เพียงเปลี่ยนค่า enum `LegendPosition` :

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### ถ้าแผนภูมิมีคำอธิบายแล้วแต่ฉันต้องการซ่อนมันล่ะ?

ตั้งค่า `HasLegend` เป็น `false` :

```csharp
chart.HasLegend = false;
```

### วิธีนี้ทำงานกับ Word 2010, 2016 และรุ่นต่อ ๆ ไปหรือไม่?

ใช่ Aspose.Words แยกส่วนเวอร์ชัน Word ที่อยู่ด้านล่างออก, ดังนั้นโค้ดเดียวกันทำงานได้กับไฟล์ .docx สมัยใหม่ทั้งหมด.

## เคล็ดลับระดับมืออาชีพ & ข้อผิดพลาดทั่วไป

- **เคล็ดลับระดับมืออาชีพ:** หลังจากใช้สไตล์แล้ว, คุณยังสามารถปรับแต่งองค์ประกอบแต่ละส่วน (สี, ป้ายข้อมูล) ผ่านคอลเลกชัน `Chart.Series`. สไตล์ให้พื้นฐานที่มั่นคง.  
- **ระวัง:** หากแผนภูมิอยู่ในเซลล์ตาราง, คำอธิบายอาจแคบเกินไป. พิจารณาเพิ่มขนาดแผนภูมิ (`chart.Width`, `chart.Height`) ก่อนกำหนดตำแหน่งคำอธิบาย.  
- **หมายเหตุประสิทธิภาพ:** การโหลดเอกสารขนาดใหญ่ (หลายร้อย MB) ใช้หน่วยความจำมาก. ใช้ `LoadOptions` กับ `LoadFormat.Docx` เพื่อลดภาระหากคุณต้องการจัดการแค่แผนภูมิ.

## ขั้นตอนต่อไป

ตอนนี้คุณรู้ **วิธีเพิ่มคำอธิบาย** และ **ใช้สไตล์แผนภูมิกำหนดล่วงหน้า** ใน Word แล้ว คุณอาจสำรวจ:

- **สีแผนภูมิแบบกำหนดเอง** (`chart.Series[i].Format.Fill.ForeColor`).  
- **การจัดรูปแบบป้ายข้อมูล** (`chart.Series[i].HasDataLabel = true`).  
- **ส่งออกแผนภูมิเป็นภาพ** (`chart.ToImage()`), มีประโยชน์สำหรับฝังในที่อื่น.  

หัวข้อเหล่านี้ทั้งหมดอิงจากโมเดลอ็อบเจกต์เดียวกัน, ดังนั้นคุณจะพบว่าการเรียนรู้ไม่ยาก.

## สรุป

เราได้แสดงวิธีแก้ปัญหาแบบครบวงจรสำหรับ **การแสดงคำอธิบายแผนภูมิ** ในเอกสาร Word ด้วย C#. ด้วยการโหลดเอกสาร, ดึงแผนภูมิ, ใช้สไตล์กำหนดล่วงหน้า, เปิดใช้งานคำอธิบาย, และจัดการข้อแตกต่างของ Waterfall, คุณจะได้แผนภูมิที่สวยงามพร้อมใช้ในรายงานธุรกิจใดก็ได้.  

อย่าลังเลที่จะทดลองค่า `ChartStyle` อื่น ๆ หรือตำแหน่งคำอธิบาย—การแสดงผลข้อมูลของคุณสมควรได้รับการนำเสนอที่ดีที่สุด หากเจอปัญหาใด ๆ ฝากคอมเมนต์ด้านล่าง; โค้ดดิ้งสนุก!

## คุณควรเรียนต่ออะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ.

- [แทรกแผนภูมิคอลัมน์ในเอกสาร Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [ซ่อนแกนแผนภูมิในเอกสาร Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [การใช้ Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}