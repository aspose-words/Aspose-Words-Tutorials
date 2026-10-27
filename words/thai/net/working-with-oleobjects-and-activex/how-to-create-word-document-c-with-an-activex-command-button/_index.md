---
category: general
date: 2026-10-26
description: เรียนรู้วิธีสร้างเอกสาร Word ด้วย C# และเพิ่มปุ่ม ActiveX อย่างโปรแกรมเมติก
  คู่มือขั้นตอนนี้ครอบคลุมการแทรกปุ่มคำสั่ง การซ่อนปุ่มในระหว่างการออกแบบ และการบันทึกไฟล์
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: th
lastmod: 2026-10-26
og_description: สร้างเอกสาร Word ด้วย C# และเพิ่มปุ่ม ActiveX ด้วยโค้ด ทำตามบทแนะนำฉบับเต็มนี้เพื่อฝังปุ่มคำสั่งที่จะแสดงเฉพาะในขณะรันไทม์.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: สร้างเอกสาร Word ด้วย C# พร้อมปุ่มคำสั่ง ActiveX – คู่มือเต็ม
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: วิธีสร้างเอกสาร Word ด้วย C# พร้อมปุ่มคำสั่ง ActiveX
url: /th/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้าง Word document C# พร้อมปุ่มคำสั่ง ActiveX

หากคุณต้องการ **create Word document C#** ที่มีปุ่มโต้ตอบ คู่มือนี้จะแสดงให้คุณเห็นอย่างชัดเจน หลังจากสองประโยคแรกคุณจะเข้าใจแนวทางโดยรวม และขั้นตอนต่อไปจะพาคุณผ่านทุกบรรทัดของโค้ดที่ต้องเขียน

คุณจะได้เรียนรู้วิธีเพิ่มปุ่ม ActiveX, ซ่อนมันในระหว่างการออกแบบ, และทำให้มันปรากฏเฉพาะเมื่อผู้ใช้เปิดไฟล์ เท่านั้น นอกจากนี้บทเรียนยังครอบคลุมข้อผิดพลาดทั่วไป เช่น คำเตือนด้านความปลอดภัยและความเข้ากันได้ของเวอร์ชัน เพื่อให้คุณสามารถจัดส่งเอกสารที่เชื่อถือได้

## Prerequisites

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* .NET 6.0 หรือใหม่กว่า ติดตั้งแล้ว  
* สำเนา **Aspose.Words for .NET** ที่มีลิขสิทธิ์ (รุ่นทดลองฟรีใช้สำหรับทดลองได้)  
* ความคุ้นเคยพื้นฐานกับ C# และ Visual Studio (IDE ใดก็ได้ที่รองรับ .NET จะใช้ได้)  

ไม่จำเป็นต้องเพิ่มแพ็กเกจ NuGet ใด ๆ นอกเหนือจาก `Aspose.Words`

## Step 1: Create a Word document C# and initialize the DocumentBuilder

ขั้นตอนแรกคือการสร้างอ็อบเจ็กต์ `Document` และ `DocumentBuilder` `Document` แทนไฟล์ .docx ทั้งหมด ส่วน `DocumentBuilder` ให้เมธอดแบบ fluent เพื่อเพิ่มเนื้อหา

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** หากไม่มี `DocumentBuilder` คุณจะต้องจัดการกับ OpenXML DOM ด้วยตนเอง ซึ่งเสี่ยงต่อข้อผิดพลาดและอ่านยาก ตัว builder จะซ่อนรายละเอียดเหล่านั้นและรับประกันว่าไฟล์ Word จะถูกสร้างอย่างถูกต้อง

## Step 2: How to add ActiveX button – insert a CommandButton control

ตอนนี้เราจะใส่ **CommandButton ActiveX control** ที่ตำแหน่งเฉพาะ สี่เหลี่ยมกำหนดตำแหน่งของปุ่ม (X, Y) และขนาด (ความกว้าง, ความสูง) เป็นหน่วย point

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Why this matters:** `InsertForms2OleControl` เป็นเมธอดเดียวของ Aspose.Words ที่สร้างอ็อบเจ็กต์ ActiveX OLE ที่แท้จริง ค่า enum `Forms2OleControlType.CommandButton` บอก Word ให้ฝังปุ่มที่คลิกได้แทนคอนเทนเนอร์ OLE ทั่วไป

## Step 3: Programmatically add command button – hide it until runtime

Word จะถือว่า shape ใดที่แทรกเข้ามาจะมองเห็นได้โดยค่าเริ่มต้น เพื่อให้ปุ่มไม่ปรากฏขณะออกแบบเทมเพลต ให้ตั้งค่า `Hidden` บน shape ที่ builder เพิ่งสร้าง

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Why this matters:** การตั้งค่า `Hidden = true` ป้องกันไม่ให้ปุ่มรกมุมมองการออกแบบ เมื่อเปิดเอกสารใน Word สภาพแวดล้อม runtime จะเปิดเผยคอนโทรลโดยอัตโนมัติ ทำให้ประสบการณ์ผู้ใช้เป็นไปตามที่ตั้งใจ

## Step 4: Save the file – create command button word document

สุดท้ายให้บันทึกเอกสารลงดิสก์ เลือกพาธที่แอปพลิเคชันของคุณสามารถเขียนได้ และใช้ส่วนขยาย `.docx` เพื่อความเข้ากันได้สมัยใหม่

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Why this matters:** การบันทึกเป็น `.docx` รับประกันว่า ActiveX control ที่ฝังอยู่สอดคล้องกับมาตรฐาน Office Open XML ซึ่งรองรับโดย Word 2007 ขึ้นไป หากต้องการสนับสนุน `.doc` แบบเก่า ให้เปลี่ยนส่วนขยายและใช้ `SaveFormat.Doc`

## Full working example

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมเต็มที่คุณสามารถคัดลอก, วาง, และรันได้:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Expected output:** หลังจากรันโปรแกรมแล้ว เปิด `C:\Temp\ActiveX.docx` ใน Microsoft Word คุณจะเห็นเอกสารเปล่า; ปุ่มจะไม่ปรากฏในโหมดออกแบบ กด **Alt + F9** เพื่อสลับ field codes แล้วคลิกพื้นที่ปุ่ม — Word จะเรนเดอร์ ActiveX control และคุณสามารถโต้ตอบกับมันได้ (เช่น ดับเบิล‑คลิกเพื่อดูคุณสมบัติ)

## Edge cases and best‑practice tips

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **User disables ActiveX** | Word อาจแสดงคำเตือนด้านความปลอดภัยหรือบล็อกคอนโทรล | แนะนำผู้ใช้ให้เปิด “ActiveX controls” ใน Trust Center หรือให้ทางเลือกที่ลงนามด้วย macro |
| **Document opened in Word Online** | Word Online ไม่รองรับ ActiveX; ปุ่มจะถูกละเว้น | ใช้ลิงก์สำรองหรือ content control หากต้องการความเข้ากันได้กับคลาวด์ |
| **Different DPI settings** | ขนาดสี่เหลี่ยมอาจดูใหญ่หรือเล็กบนจอ DPI สูง | ใช้ `GraphicsUnit.Point` (ค่าเริ่มต้น) และทดสอบบน DPI ที่พบบ่อย (96 dpi, 120 dpi) |
| **Multiple buttons** | การเรียก `GetChildNodes(NodeType.Shape, true)[0]` จะดึง shape แรกเท่านั้น | วนลูป `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` แล้วตั้ง `Hidden` ให้กับแต่ละ shape ที่เพิ่ม |
| **Legacy .doc format** | คุณสมบัติบางอย่างของ ActiveX จะหายไปเมื่อบันทึกเป็น `.doc` | แนะนำใช้ `.docx` เว้นแต่มีความต้องการแบบ legacy อย่างเคร่งครัด |

**Pro tip:** หลังจากแทรกปุ่มแล้ว คุณสามารถกำหนด macro ให้กับ property `OnAction` ของมันผ่าน UI ของ Word วิธีนี้ทำให้คุณกำหนดพฤติกรรมการคลิกแบบกำหนดเองได้โดยไม่ต้องเขียนโค้ด C# เพิ่ม

## Frequently asked questions

* **Does this work with .NET Core?**  
  ใช่ Aspose.Words for .NET รองรับ .NET 5, .NET 6, และรุ่นต่อ ๆ ไป เพียงอ้างอิงแพ็กเกจ NuGet เดียวกัน

* **Can I change the button caption after the document is generated?**  
  คำบรรยายที่ตั้งค่าใน `InsertForms2OleControl` จะเป็นข้อความเริ่มต้นในช่วงออกแบบ ผู้ใช้สามารถแก้ไขใน Word ได้ แต่คุณก็สามารถอัปเดตคำบรรยายโดยโปรแกรมผ่านคุณสมบัติของอ็อบเจ็กต์ OLE ด้วย API `Shape.OleFormat`

* **What if I need a different size for the button?**  
  ปรับค่าใน `RectangleF` พารามิเตอร์สองตัวแรกคือพิกัด X‑และ Y‑, สองตัวสุดท้ายคือความกว้างและความสูงเป็น point (1 pt = 1/72 inch)

## Conclusion

คุณตอนนี้รู้วิธี **create Word document C#** และ **programmatically add command button** ด้วย Aspose.Words แล้ว บทเรียนได้ครอบคลุมการเริ่มต้นเอกสาร, การแทรกปุ่ม ActiveX, การซ่อนจนถึง runtime, และการบันทึกไฟล์สุดท้าย ด้วยบล็อกเหล่านี้คุณสามารถฝังคอนโทรลโต้ตอบในเทมเพลต Word ใด ๆ ที่คุณสร้างได้

ต่อไปสำรวจหัวข้อที่เกี่ยวข้อง เช่น **how to add ActiveX button** การจัดการเหตุการณ์, **create command button word** การสไตลิ่งด้วย VBA, และ **programmatically add command button** ในเอกสารที่มีอยู่ การขยายรูปแบบนี้ไปยัง checkbox, combo box หรือ OLE object แบบกำหนดเองทำได้โดยเปลี่ยนค่า enum `Forms2OleControlType`

เริ่มทดลอง: เปลี่ยนคำบรรยาย, ปรับตำแหน่ง, หรือเชื่อมต่อหลายคอนโทรลเข้าด้วยกัน ยิ่งฝึกฝนมาก คุณจะยิ่งคล่องแคล่วในการสร้างเอกสาร Word ที่มีความโต้ตอบจาก C# ขอให้สนุกกับการเขียนโค้ด!

## What Should You Learn Next?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [วิธีเพิ่มปุ่มคำสั่งโดยโปรแกรมในเอกสาร Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [วิธีเพิ่มปุ่ม ActiveX ในเอกสาร Word ด้วย Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [สร้าง Word Document พร้อมปุ่ม ActiveX – คู่มือ C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}