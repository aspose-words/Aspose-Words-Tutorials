---
category: general
date: 2026-08-17
description: วิธีเพิ่มคอนโทรล ActiveX และแทรกแผนภูมิวงกลมในเอกสาร Word ด้วย Aspose.Words.
  แยกชิ้นส่วนหนึ่งของแผนภูมิและบันทึกเป็นไฟล์ DOCX เพียงไม่กี่ขั้นตอน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: th
lastmod: 2026-08-17
og_description: วิธีเพิ่มคอนโทรล ActiveX, แทรกแผนภูมิวงกลม, แยกชิ้นส่วน, และบันทึกเป็น
  DOCX ด้วย Aspose.Words – คู่มือขั้นตอนเต็ม.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: วิธีเพิ่ม ActiveX และแทรกแผนภูมิวงกลมในเอกสาร Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: วิธีเพิ่ม ActiveX และแทรกแผนภูมิวงกลมในเอกสาร Word
url: /th/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่ม ActiveX และแทรกแผนภูมิวงกลมในเอกสาร Word

หากคุณต้องการ **how to add ActiveX** ควบคุมและฝังแผนภูมิในเอกสาร Word, บทแนะนำนี้จะแสดงวิธีแก้ไขที่สมบูรณ์และสามารถรันได้ โดยใช้ Aspose.Words คุณสามารถวาง ActiveX CommandButton, สร้างแผนภูมิวงกลม, แยกชิ้นส่วนหนึ่งเพื่อเน้น, และสุดท้าย **save as DOCX** เพียงไม่กี่บรรทัดของ C#.

ในส่วนต่อไปนี้คุณจะเห็นการนำเข้าที่จำเป็นทั้งหมด, รายการโค้ดเต็ม, และคำอธิบายว่าทำไมแต่ละขั้นตอนจึงสำคัญ. เมื่อเสร็จสิ้นคุณจะสามารถรวมควบคุมแบบโต้ตอบและข้อมูลเชิงภาพเข้าไปในไฟล์ .docx ใด ๆ ที่คุณสร้างโดยโปรแกรม.

## ข้อกำหนดเบื้องต้น

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+)
* แพ็กเกจ Aspose.Words for .NET (สามารถดาวน์โหลดได้ผ่าน NuGet)
* สภาพแวดล้อมการพัฒนา เช่น Visual Studio 2022 หรือ VS Code
* ความคุ้นเคยพื้นฐานกับ C# และ Word object model

ไม่จำเป็นต้องใช้ไลบรารีแผนภูมิของบุคคลที่สามเพิ่มเติม—Aspose.Words มีฟังก์ชันการสร้างแผนภูมิในตัว.

## วิธีเพิ่มควบคุม ActiveX ด้วย Aspose.Words

ควบคุม ActiveX ช่วยให้คุณฝังองค์ประกอบ UI แบบโต้ตอบโดยตรงในไฟล์ Word. ในคู่มือนี้เราจะเพิ่ม **CommandButton** ที่สามารถเชื่อมต่อกับโค้ด VBA ได้ในภายหลัง.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**ทำไมวิธีนี้ถึงได้ผล:**  
`InsertForms2OleControl` สร้างคอนเทนเนอร์ OLE ที่ UI ของ Word จดจำเป็นควบคุม ActiveX. การตั้งค่าชนิดของควบคุมเป็น `CommandButton` และกำหนดคำบรรยายทำให้มันทำงานเหมือนปุ่มมาตรฐานเมื่อผู้ใช้เปิดไฟล์ใน Word.

## แทรกแผนภูมิวงกลมและแยกชิ้นส่วนหนึ่ง

แผนภูมิเป็นประโยชน์สำหรับการแสดงข้อมูลโดยไม่ต้องออกจากเอกสาร. ขั้นตอนต่อไปนี้แสดง **how to insert chart** และโดยเฉพาะ **pie chart** ที่ชิ้นส่วนแรกถูกแยกออก.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**ทำไมต้องแยกชิ้นส่วน:**  
การเรียก `SetExplode(0, true)` บอก Aspose.Words ให้ย้ายตำแหน่งจุดข้อมูลแรกออกมา ทำให้ผู้ชมสนใจส่วนนั้น นี่เป็นเทคนิคทั่วไปในงานนำเสนอเพื่อเน้นค่าที่สำคัญ.

## บันทึกเป็น DOCX

หลังจากเพิ่มปุ่ม ActiveX และแผนภูมิแล้ว ให้บันทึกเอกสารลงดิสก์ ขั้นตอนนี้แสดง **save as DOCX** ด้วยวิธีมาตรฐาน.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

ไฟล์ `Output.docx` ตอนนี้มีปุ่มโต้ตอบ, แผนภูมิวงกลมที่มีชิ้นส่วนที่แยกออก, และสามารถเปิดใน Microsoft Word ได้โดยไม่ต้องใช้ปลั๊กอินเพิ่มเติม.

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

เมื่อนำทุกอย่างมารวมกัน นี่คือโปรแกรมแบบ self‑contained ที่คุณสามารถคัดลอกไปใส่ในแอปพลิเคชันคอนโซลและรันได้ทันที.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:**  
การเปิด `Output.docx` ใน Word จะเห็นปุ่มที่มีข้อความ *Click Me* และแผนภูมิวงกลมที่ชิ้นส่วนแรก (January) ถูกย้ายออกจากส่วนอื่น ปุ่มพร้อมสำหรับการจัดการเหตุการณ์ VBA, และแผนภูมิสามารถแก้ไขได้ด้วยเครื่องมือแผนภูมิในตัวของ Word.

## คำถามทั่วไปและกรณีขอบ

* **ฉันสามารถเพิ่มประเภท ActiveX อื่นได้หรือไม่?**  
  ได้. แทนที่ `Forms2OleControlType.CommandButton` ด้วยค่าใดค่าหนึ่งจาก enum `Forms2OleControlType` (เช่น `CheckBox`, `OptionButton`). รูปแบบการแทรกเดียวกันใช้ได้.

* **ถ้าฉันต้องการประเภทแผนภูมิอื่น?**  
  ใช้ `ChartType.Bar`, `ChartType.Line` เป็นต้น ในการเรียก `InsertChart`. ขั้นตอน **how to insert chart** ยังคงเหมือนเดิม; เพียงค่า enum ที่เปลี่ยน.

* **จะควบคุมขนาดของชิ้นส่วนที่แยกออกได้อย่างไร?**  
  Aspose.Words ปัจจุบันรองรับเพียงแฟล็ก explode แบบบูลีน (true/false). หากต้องการควบคุมละเอียดกว่า (เช่น ระยะการย้าย) คุณต้องแก้ไข OOXML ที่อยู่ภายหลังการบันทึก.

* **เอกสารนี้เข้ากันได้กับเวอร์ชัน Word เก่าไหม?**  
  การบันทึกเป็น DOCX ทำให้เข้ากันได้กับ Word 2007 และรุ่นต่อไป. สำหรับ Word 2003 คุณสามารถเปลี่ยนเป็น `SaveFormat.Doc` แต่การสนับสนุน ActiveX มีจำกัดในฟอร์แมตนั้น.

* **ฉันต้องอ้างอิง `System.Drawing` หรือไม่?**  
  ไม่. วัตถุการวาดทั้งหมดมาจาก Aspose.Words, ดังนั้นแพ็กเกจ NuGet ที่ต้องการเพียงอย่างเดียวคือ `Aspose.Words`.

## สรุป

ตอนนี้คุณรู้ **how to add ActiveX**, **insert a pie chart**, **explode a pie slice**, และ **save as DOCX** ด้วย Aspose.Words for .NET. ตัวอย่างเต็มครอบคลุมทุกขั้นตอนตั้งแต่การสร้างเอกสารจนถึงการบันทึกขั้นสุดท้าย, และอธิบายเหตุผลเบื้องหลังแต่ละการเรียก API.

ต่อไปคุณอาจสำรวจ:

* เพิ่มแมโคร VBA ที่ตอบสนองต่อการคลิก CommandButton (**how to insert chart** และอัตโนมัติการอัปเดตข้อมูล)
* ปรับแต่งลักษณะของแผนภูมิ (สี, ป้ายข้อมูล) ให้สอดคล้องกับแบรนด์ขององค์กร
* ฝังควบคุม ActiveX เพิ่มเติมเช่น **ComboBox** หรือ **ListBox** เพื่อแบบฟอร์มที่สมบูรณ์ขึ้น

คุณสามารถทดลองกับโค้ด, แทนที่ข้อมูลตัวอย่าง, และรวมโซลูชันนี้เข้าสู่กระบวนการสร้างเอกสารของคุณเองได้อย่างอิสระ. ขอให้เขียนโค้ดอย่างสนุก!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ.

- [แทรกแผนภูมิคอลัมน์ใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [แทรกแผนภูมิคอลัมน์แบบง่ายใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [แทรกแผนภูมิบับเบิลใน Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}