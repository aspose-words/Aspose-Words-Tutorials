---
category: general
date: 2026-07-29
description: เพิ่มปุ่มคำสั่งลงในเอกสาร Word ด้วย Aspose.Words. เรียนรู้วิธีตั้งค่าคุณสมบัติของ
  ActiveX Control และตั้งค่าคำบรรยายของปุ่มคำสั่งในไม่กี่ขั้นตอนง่าย ๆ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: th
lastmod: 2026-07-29
og_description: เพิ่มปุ่มคำสั่งลงในเอกสาร Word ด้วย Aspose.Words บทเรียนนี้จะแสดงวิธีตั้งค่าคุณสมบัติของ
  ActiveX Control และตั้งค่าข้อความบนปุ่มคำสั่งอย่างรวดเร็ว.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: เพิ่มปุ่มคำสั่งในเอกสาร Word – Aspose.Words ขั้นตอนโดยขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: เพิ่มปุ่มคำสั่งในเอกสาร Word ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์
url: /th/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มปุ่มคำสั่งในเอกสาร Word – คู่มือการเขียนโปรแกรมเต็มรูปแบบ

เคยต้องการ **add command button to word document** แต่ไม่แน่ใจว่าจะใช้ API ใด? คุณไม่ได้อยู่คนเดียว; นักพัฒนาจำนวนมากเจออุปสรรคนี้เมื่อพยายามฝังคอนโทรลแบบโต้ตอบในไฟล์ DOCX ครั้งแรก ข่าวดีคือ Aspose.Words ทำให้กระบวนการนี้ง่ายมาก ในคู่มือนี้เราจะอธิบายการสร้าง CommandButton ActiveX control, **set activex control properties**, และ **set command button caption**—ทั้งหมดด้วยโค้ด C# ที่สะอาดและสามารถคัดลอก‑วางได้ทันที

เมื่อจบบทเรียนนี้คุณจะได้ไฟล์ Word ที่ทำงานเต็มรูปแบบซึ่งมีปุ่ม “Submit” ที่คลิกได้ พร้อมเปิดใน Microsoft Word ไม่ต้องใช้สคริปต์ VBA ภายนอก ไม่ต้องปรับ UI ด้วยตนเอง—เพียงการควบคุมแบบโปรแกรมเท่านั้น

## สิ่งที่คุณจะได้เรียนรู้

* วิธีสร้างเอกสาร Word ว่างและ `DocumentBuilder`
* วิธีเรียกใช้เมธอดที่แน่นอนเพื่อ **add command button to word document** ด้วย Aspose.Words
* วิธี **set activex control properties** เช่น ขนาด, ตำแหน่ง, และชื่อ
* เทคนิคที่ถูกต้องในการ **set command button caption** เพื่อให้ปุ่มแสดงข้อความตามที่คุณต้องการ
* เคล็ดลับการจัดการ edge cases เช่น ประเภทปุ่มที่ต่างกัน, การปรับสเกล DPI, และความเข้ากันได้ของเวอร์ชัน Word

> **Prerequisite:** Visual Studio (หรือ IDE C# ใดก็ได้) ที่ติดตั้ง Aspose.Words for .NET (แพคเกจ NuGet `Aspose.Words`). ไม่จำเป็นต้องมีประสบการณ์กับ ActiveX มาก่อน

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า Namespaces

ก่อนที่เราจะ **add command button to word document** เราต้องมีโปรเจกต์ C# ที่อ้างอิง Aspose.Words สร้างแอปคอนโซล .NET ใหม่ แล้วเพิ่มแพคเกจ NuGet:

```bash
dotnet add package Aspose.Words
```

ต่อไปนำ Namespaces ที่จำเป็นเข้ามาในไฟล์ซอร์สของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

สาม `using` นี้ทำให้คุณเข้าถึงคลาส `Document`, `DocumentBuilder` และ `Forms2OleControl` ที่ใช้ในการแทรก ActiveX

*เคล็ดลับ:* หากคุณใช้ Visual Studio, IDE จะเสนอให้เพิ่มเหล่านี้โดยอัตโนมัติเมื่อคุณพิมพ์ชื่อคลาส

## ขั้นตอนที่ 2: สร้างเอกสารว่างและ Builder

อ็อบเจกต์ `Document` ใหม่แสดงถึงไฟล์ Word ที่ว่างเปล่า `DocumentBuilder` คือ “ปากกา” ที่สะดวกของเรา ที่ช่วยให้เราวาด, แทรกข้อความ, และ—สำคัญ—วางคอนโทรล ActiveX

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

ในขั้นตอนนี้เอกสารเป็นเพียงผืนผ้าใบว่าง—คิดว่าเป็นกระดาษเปล่าที่รอปุ่มคำสั่งของคุณ

## ขั้นตอนที่ 3: แทรก CommandButton ActiveX Control

ตอนนี้เราจึง **add command button to word document** อย่างเป็นทางการ Aspose.Words มีเมธอด `InsertForms2OleControl` ที่รับประเภทคอนโทรลและขนาด เราจะใช้ `Forms2OleControlType.CommandButton` และกำหนดความกว้าง 150 points และความสูง 30 points

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

เมธอดนี้จะคืนค่าอินสแตนซ์ `Forms2OleControl` ซึ่งเราจะใช้เพื่อ **set activex control properties** ในขั้นตอนต่อไป

## ขั้นตอนที่ 4: กำหนดค่าคอนโทรล – ชื่อ, คำบรรยาย, และตำแหน่ง

### การตั้งค่า Caption

Caption คือข้อความที่แสดงบนปุ่มเอง เพื่อ **set command button caption** เพียงกำหนดสตริงให้กับ property `Caption`:

```csharp
commandButton.Caption = "Submit";
```

คุณสามารถเปลี่ยน `"Submit"` เป็นอะไรก็ได้—เช่น “Save”, “Export”, “Launch” ฯลฯ—และ Word จะแสดงข้อความนั้นอย่างแม่นยำ

### การตั้งชื่อคอนโทรล

การตั้งชื่อคอนโทรลให้มีความหมายทำให้การอ้างอิงในภายหลังง่ายขึ้น (เช่น เมื่อต้องทำอัตโนมัติด้วยแมโครของ Word) เราจะตั้งค่า property `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### การกำหนดตำแหน่งบนหน้า

Word ใช้หน่วย points (1/72 นิ้ว) สำหรับการจัดวาง ปรับ property `Left` และ `Top` เพื่อวางปุ่มในตำแหน่งที่ต้องการ:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

หากต้องการจัดตำแหน่งปุ่มสัมพันธ์กับย่อหน้า คุณสามารถย้ายเคอร์เซอร์ของ builder ก่อน แล้วแทรกคอนโทรล; พิกัดจะสัมพันธ์กับตำแหน่งนั้น

*Edge case:* บนจอแสดงผลที่มี DPI สูง ขนาดที่มองเห็นอาจแตกต่างเล็กน้อยใน Word เพื่อให้ขนาดจริงของปุ่มคงที่ข้ามอุปกรณ์ คุณสามารถคำนวณ points ตาม DPI ที่ต้องการ (โดยทั่วไป 96 DPI สำหรับ Word)

## ขั้นตอนที่ 5: บันทึกเอกสาร

เมื่อปุ่มถูกกำหนดค่าเรียบร้อย การบันทึกไฟล์ทำได้ด้วยบรรทัดเดียว:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

`CommandButton.docx` ที่ได้จะมีปุ่ม ActiveX ทำงานเต็มรูปแบบ เปิดไฟล์ใน Microsoft Word แล้วคุณจะเห็นปุ่ม “Submit” อยู่ในตำแหน่งที่คุณกำหนดไว้

### ผลลัพธ์ที่คาดหวัง

1. เอกสาร Word เปิดขึ้นด้วยหน้าเดียว  
2. ปุ่มสี่เหลี่ยมที่มีป้าย **Submit** ปรากฏที่พิกัดที่คุณระบุ  
3. หากคุณคลิกขวาที่ปุ่มและเลือก **Properties** คุณจะเห็นชื่อ `btnSubmit` และคุณสมบัติอื่น ๆ ที่คุณตั้งค่า  

## ขั้นตอนที่ 6: ความหลากหลายขั้นสูงและข้อผิดพลาดทั่วไป

### การแทรกประเภท ActiveX อื่น

เมธอด `InsertForms2OleControl` ไม่จำกัดเฉพาะ command button คุณสามารถฝัง check box, option button หรือแม้แต่วัตถุ ActiveX ที่กำหนดเองได้:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

รูปแบบ **set activex control properties** เดียวกันใช้ได้—เพียงเปลี่ยน enum ของประเภท

### การจัดการเวอร์ชัน Word

เวอร์ชัน Word เก่า (ก่อน‑2007) ใช้รูปแบบไบนารี `.doc` ซึ่งเก็บ ActiveX คอนโทรลต่างกัน Aspose.Words จะทำการแปลงคอนโทรลโดยอัตโนมัติเมื่อบันทึกเป็น `.doc` แต่บางคุณสมบัติ (เช่น การกำหนดตำแหน่งที่แม่นยำ) อาจเปลี่ยนแปลง หากคุณมุ่งเป้าไปที่รูปแบบเก่า ควรทดสอบผลลัพธ์ในเวอร์ชัน Word ที่ต้องการ

### การตั้งค่าความปลอดภัย

Word อาจปิดการใช้งาน ActiveX คอนโทรลบนเครื่องที่มีความปลอดภัยของแมโครเข้มงวด เพื่อหลีกเลี่ยงกล่องโต้ตอบ “Security Warning” ให้พิจารณา:

* เซ็นเอกสารด้วยใบรับรองที่เชื่อถือได้  
* แนะนำผู้ใช้ให้เปิดใช้งานเนื้อหา ActiveX สำหรับตำแหน่งไฟล์นั้น  
* ใช้ทางเลือกที่ไม่มีแมโคร (เช่น content control ธรรมดา) หากความปลอดภัยเป็นประเด็น  

## ขั้นตอนที่ 7: ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่สมบูรณ์พร้อมรันที่รวมทุกขั้นตอนที่เราอธิบายไว้ คัดลอกไปยัง `Program.cs` ของคุณ ปรับเส้นทางออกหากจำเป็น แล้วกด **Run**

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**สิ่งที่โค้ดนี้ทำ:**

* เริ่มด้วยเอกสารใหม่  
* แทรกปุ่มคำสั่ง, **sets activex control properties**, และ **sets command button caption**  
* เพิ่มย่อหน้าสั้นอธิบาย  
* บันทึกไฟล์เป็น `CommandButton.docx`

รันโปรแกรม เปิดไฟล์ที่สร้างขึ้น แล้วคุณจะเห็นปุ่มอยู่ใต้ข้อความอธิบาย

## สรุป

เราเพิ่งแสดงวิธี **add command button to word document** ด้วย Aspose.Words, วิธี **set activex control properties**, และวิธี **set command button caption**—ทั้งหมดในสคริปต์ C# สั้นกระชับพร้อมใช้ในผลิตภัณฑ์ วิธีนี้สามารถขยายได้: เปลี่ยนประเภทคอนโทรล, ปรับขนาด, หรือวนลูปผ่านแหล่งข้อมูลเพื่อฝังปุ่มหลายสิบปุ่มโดยอัตโนมัติ

ต้องการทำต่อ? ลอง:

* ผูกปุ่มกับแมโครที่ทำการส่งออกข้อมูล  
* เพิ่มรูปภาพหรือไอคอนกำหนดเองภายในปุ่มโดยใช้ property `Picture`  
* สร้างฟอร์มเต็มรูปแบบที่มีหลาย ActiveX คอนโทรล (textbox, combo box ฯลฯ)

การทดลองเป็นวิธีที่ดีที่สุดในการเชี่ยวชาญการอัตโนมัติของ Word หากคุณเจออุปสรรค อย่าลืมตรวจสอบการคำนวณ DPI และการตั้งค่าความปลอดภัยของ Word อีกครั้ง ขอให้สนุกกับการเขียนโค้ดและเอกสารของคุณมีความโต้ตอบมากยิ่งขึ้น!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ

- [เพิ่มเนื้อหาโดยใช้ Document Builder ใน Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [สร้าง Group Shape ในเอกสาร Word โดยใช้ Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [สร้างเอกสาร Word พร้อม Header และ Footer โดยใช้ Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}