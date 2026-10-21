---
category: general
date: 2026-10-13
description: วิธีจัดรูปแบบแผนภูมิใน Word ด้วย C# โดยใช้รูปแบบตัวเลขที่กำหนดเอง เช่น
  สกุลเงิน บนแกนแผนภูมิ พร้อมตัวอย่างโค้ดทีละขั้นตอน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: th
lastmod: 2026-10-13
og_description: วิธีจัดรูปแบบแผนภูมิใน Word ด้วย C# ช่วยให้คุณกำหนดรูปแบบตัวเลขแบบกำหนดเองให้กับแกนของแผนภูมิ
  เพื่อให้ค่าปรากฏเป็นสกุลเงิน เปอร์เซ็นต์ หรือรูปแบบใดก็ได้ที่คุณต้องการ ทำตามคู่มือขั้นตอนต่อขั้นตอน
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: วิธีจัดรูปแบบแผนภูมิใน Word ด้วย C# – รูปแบบตัวเลขแบบกำหนดเอง
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: วิธีจัดรูปแบบแผนภูมิใน Word ด้วย C# และรูปแบบตัวเลขที่กำหนดเอง
url: /th/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีจัดรูปแบบแผนภูมิใน Word ด้วย C# และรูปแบบตัวเลขที่กำหนดเอง

การจัดรูปแบบแผนภูมิใน Word ด้วย C# เป็นความต้องการทั่วไปเมื่อคุณต้องการนำเสนอข้อมูลอย่างเป็นมืออาชีพ คู่มือนี้จะแสดงวิธีการใช้รูปแบบตัวเลขที่กำหนดเองกับแกนของแผนภูมิโดยใช้ **Aspose.Words for .NET** เพื่อให้ค่าต่าง ๆ ปรากฏตามที่คุณคาดหวัง

คุณจะได้เรียนรู้วิธีโหลดไฟล์ DOCX, ค้นหาแผนภูมิแรก, อ่านรูปแบบปัจจุบัน, แล้วตั้งรูปแบบใหม่ เช่น สกุลเงินที่มีทศนิยมสองตำแหน่ง คู่มือนี้ยังครอบคลุมวิธีการเปลี่ยนรูปแบบแกนของแผนภูมิสำหรับชุดข้อมูลเพิ่มเติมและวิธีรีเซ็ตรูปแบบหากต้องการ

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 หรือใหม่กว่า  
* โครงการ Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ .NET)  
* แพคเกจ NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* เอกสาร Word (`input.docx`) ที่มีอย่างน้อยหนึ่งแผนภูมิ

คุณสามารถเพิ่มแพคเกจด้วยคำสั่งต่อไปนี้:

```bash
dotnet add package Aspose.Words
```

## วิธีจัดรูปแบบแผนภูมิใน Word ด้วย Aspose.Words

โปรแกรมเต็มรูปแบบต่อไปนี้สาธิตทุกขั้นตอนที่จำเป็นเพื่อ **จัดรูปแบบแผนภูมิ** ของค่าแกน บันทึกไฟล์เป็น `Program.cs` แล้วเรียกใช้จากบรรทัดคำสั่งหรือ IDE ของคุณ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### คำอธิบายของแต่ละขั้นตอน

| ขั้นตอน | ทำไมจึงสำคัญ | โค้ดสำคัญ |
|------|----------------|----------|
| **Load the document** | คุณต้องการอ็อบเจ็กต์ `Document` เพื่อทำงานกับไฟล์ Word | `new Document("input.docx")` |
| **Retrieve the chart** | `Chart` ถูกเก็บเป็นโหนด `Shape`; การแคสท์ทำให้คุณใช้ API เฉพาะแผนภูมิได้ | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Access X‑values** | การจัดรูปแบบแกนจะถูกนำไปใช้กับคอลเลกชันค่าของชุดข้อมูล | `chart.ChartData.Series[0].XValues` |
| **Read current format** | การรู้ `FormatCode` ปัจจุบันช่วยให้คุณตัดสินใจว่าจะเปลี่ยนหรือเพิ่ม | `xValues.FormatCode` |
| **Set custom format** | คุณสมบัติ `FormatCode` ยอมรับรูปแบบที่เข้ากันกับ Excel ใด ๆ ทำให้สามารถใช้สกุลเงิน, เปอร์เซ็นต์, วันที่ ฯลฯ | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Save the document** | การบันทึกการเปลี่ยนแปลงจะเขียนรูปแบบแกนใหม่กลับไปยังไฟล์ DOCX | `doc.Save("output_formatted.docx")` |

การรันโปรแกรมจะสร้างไฟล์ `output_formatted.docx` เปิดไฟล์ใน Word แล้วคุณจะเห็นค่าแกน X ของแผนภูมิแสดงเป็น **$1,234.00**, **$2,345.00**, … แทนตัวเลขธรรมดา

## ใช้รูปแบบตัวเลขที่กำหนดเองกับแกนของแผนภูมิ

หากคุณต้องการ **ใช้รูปแบบตัวเลขที่กำหนดเอง** กับแกน Y หรือกับชุดข้อมูลเพิ่มเติม กระบวนการจะเหมือนเดิม—เพียงแค่เลือกคอลเลกชันที่ต่างออกไป:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **เคล็ดลับ:** ใช้เครื่องหมายคำพูดคู่ภายในสตริงรูปแบบเพื่อฝังอักขระตามตัว (เช่น `"$"` สำหรับสกุลเงิน) ให้หลบหนีเครื่องหมายคำพูดตามที่แสดงด้านบน

## คำสั่งรูปแบบตัวเลขที่กำหนดเอง – การจัดการโลคัลของ Word

Word เคารพโลคัลของเอกสารเมื่อแปลความหมายรูปแบบตัวเลข หากเอกสารใช้โลคัลที่ไม่ใช่สหรัฐอเมริกา คุณอาจต้องปรับสตริงรูปแบบ:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

การทดสอบรูปแบบบนเอกสารที่ตั้งค่าภาษาเยอรมันยืนยันว่าค่าจะปรากฏเป็น **€ 1.234,00**  

## วิธีตั้งค่าคุณสมบัติของแผนภูมิโดยโปรแกรม

นอกเหนือจากการจัดรูปแบบแกนแล้ว คุณมักต้องการ **ตั้งค่าแผนภูมิ** เช่น ชื่อ, คำอธิบาย, หรือป้ายข้อมูล นี่คือตัวอย่างสั้น ๆ ที่แสดงการตั้งชื่อแผนภูมิหลังจากที่คุณได้จัดรูปแบบแกนแล้ว:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

การผสานสิ่งนี้กับรูปแบบตัวเลขที่กำหนดเองจะทำให้คุณได้แผนภูมิที่สมบูรณ์แบบพร้อมสำหรับการรายงาน

## เปลี่ยนรูปแบบแกนของแผนภูมิแบบไดนามิกตามการป้อนข้อมูลของผู้ใช้

ในแอปพลิเคชันจริง คุณอาจให้ผู้ใช้เลือกรูปแบบได้ในขณะทำงาน วิธีต่อไปนี้ทำหน้าที่ห่อหุ้มตรรกะการจัดรูปแบบ:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

คุณสามารถเรียก `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` สำหรับสกุลเงินหรือ `SetAxisFormat(chart, 0, "0%")` สำหรับเปอร์เซ็นต์ วิธีนี้ทำให้โค้ดหลักของคุณสะอาดและรองรับการขยายในอนาคต

## กรณีขอบและข้อผิดพลาดทั่วไป

| สถานการณ์ | สิ่งที่ต้องระวัง | วิธีแก้แนะนำ |
|-----------|-------------------|---------------|
| เอกสาร **ไม่มีแผนภูมิ** | `GetChild` คืนค่า `null` ทำให้เกิดข้อยกเว้นการแคสท์ | ตรวจสอบ `null` ก่อนแคสท์ (ดูตัวอย่าง) |
| มีหลายแผนภูมิในเอกสารเดียว | โค้ดจะดึงแผนภูมิแรกเสมอ (`index 0`) | วนลูปผ่าน `doc.GetChildNodes(NodeType.Shape, true)` แล้วกรองด้วย `ShapeType.Chart` |
| ชุดข้อมูล **ไม่มี X‑values** (เช่น แผนภูมิพาย) | การเข้าถึง `XValues` อาจทำให้เกิด `ArgumentOutOfRangeException` | ตรวจสอบว่า `Series[i].XValues` ไม่ว่างก่อนทำการจัดรูปแบบ |
| โลคัลไม่ตรงกัน | สัญลักษณ์สกุลเงินอาจแสดงไม่ถูกต้อง | ตั้งค่า `xValues.FormatCode` อย่างชัดเจนด้วยสัญลักษณ์โลคัลที่เหมาะสม |

## ผลลัพธ์ที่คาดหวัง

หลังจากรันโปรแกรมตัวอย่าง เปิด **output_formatted.docx** แกน X ของแผนภูมิควรแสดงตัวเลขในรูปแบบที่คุณเลือก สำหรับตัวอย่างสกุลเงิน ป้ายแกนจะเป็นดังนี้:

```
$1,000.00
$2,000.00
$3,000.00
```

หากคุณใช้รูปแบบเปอร์เซ็นต์กับค่า Y ป้ายแกน Y จะปรากฏเป็น:

```
10%
20%
30%
```

## สรุป

บทแนะนำนี้ได้แสดง **วิธีจัดรูปแบบแผนภูมิ** ใน Word ด้วย C# โดย **การใช้รูปแบบตัวเลขที่กำหนดเอง** กับค่าแกน คุณมีรูปแบบที่นำกลับมาใช้ใหม่ได้สำหรับการตั้งค่าสกุลเงิน, เปอร์เซ็นต์ หรือรูปแบบตัวเลขใด ๆ รวมถึงแนวทางการจัดการโลคัล, ชุดข้อมูลหลายชุด, และการรับอินพุตจากผู้ใช้แบบไดนามิก

ต่อไป คุณอาจสำรวจ **วิธีตั้งค่าแผนภูมิ** เช่น ชื่อ, ป้ายข้อมูล, หรือแม้กระทั่งการส่งออกแผนภูมิเป็นภาพโดยใช้ `ChartRenderer` หัวข้อเหล่านี้ต่อเนื่องจากแนวคิดที่อธิบายไว้ที่นี่และจะช่วยให้คุณสร้างโซลูชันการรายงานอัตโนมัติเต็มรูปแบบ

---

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบต่าง ๆ ในโครงการของคุณ

- [รูปแบบตัวเลขสำหรับแกนในแผนภูมิ](/words/english/net/programming-with-charts/number-format-for-axis/)
- [รูปแบบตัวเลขของป้ายข้อมูลในแผนภูมิ](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [จัดรูปแบบแกน X รองและตั้งหน่วยแสดงผลเป็นพันในแผนภูมิเส้นของ Word โดยใช้ Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}