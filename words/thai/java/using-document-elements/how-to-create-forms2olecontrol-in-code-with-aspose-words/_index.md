---
category: general
date: 2026-09-11
description: เรียนรู้วิธีสร้าง forms2olecontrol ในโค้ดโดยใช้ Aspose.Words DocumentBuilder 
  คู่มือขั้นตอนนี้ครอบคลุมการแทรกปุ่มคำสั่ง ActiveX, การใช้ setOleClassName และการกำหนดขนาด.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: th
lastmod: 2026-09-11
og_description: สร้าง forms2olecontrol ด้วยโค้ดโดยใช้ Aspose.Words. ทำตามคำแนะนำนี้เพื่อแทรกปุ่มคำสั่ง
  ActiveX, ตั้งชื่อคลาสของมัน, และปรับขนาดของปุ่ม.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: สร้าง forms2olecontrol ด้วยโค้ด – คู่มือ Aspose.Words ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: วิธีสร้าง forms2olecontrol ด้วยโค้ดโดยใช้ Aspose.Words
url: /th/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้าง forms2olecontrol ในโค้ดด้วย Aspose.Words

หากคุณต้องการ **create forms2olecontrol in code** คำแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนทั้งหมดโดยใช้ Aspose.Words .NET API ไม่ว่าคุณจะทำอัตโนมัติเทมเพลตที่ต้องการปุ่ม ActiveX command button หรือเพียงแค่ต้องการเพิ่มความสามารถให้กับเอกสาร Word ด้วยโปรแกรม ขั้นตอนต่อไปนี้ครอบคลุมทุกอย่างตั้งแต่การแทรกคอนโทรลจนถึงการกำหนดลักษณะการแสดงผล

ในบทเรียนนี้คุณจะได้เรียนรู้วิธีใช้ **Aspose.Words DocumentBuilder** เพื่อแทรก **ActiveX command button**, ตั้งคลาสด้วย **setOleClassName method**, และปรับ **Forms2OleControl size** ของมัน ไม่ต้องใช้เครื่องมือภายนอก—เพียงสภาพแวดล้อมการพัฒนา .NET และไลบรารี Aspose.Words

## Prerequisites

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 หรือใหม่กว่า (โค้ดนี้ยังทำงานกับ .NET Framework 4.7+)
* เวอร์ชันล่าสุดของแพคเกจ Aspose.Words for .NET บน NuGet
* ความคุ้นเคยพื้นฐานกับ C# และแนวคิดของ ActiveX controls ในเอกสาร Word

หากขาดส่วนใดส่วนหนึ่ง ให้ติดตั้งแพคเกจ NuGet ด้วยคำสั่ง:

```bash
dotnet add package Aspose.Words
```

## What this tutorial covers

* การสร้างอินสแตนซ์ `DocumentBuilder`
* การแทรก `Forms2OleControl` (อ็อบเจ็กต์พื้นฐานสำหรับปุ่ม ActiveX command button)
* การกำหนดชื่อคลาสที่ถูกต้องด้วย `setOleClassName`
* การตั้งค่าความกว้างและความสูงด้วยคุณสมบัติ **Forms2OleControl size**
* การบันทึกเอกสารและตรวจสอบผลลัพธ์

เมื่อจบบทเรียน คุณจะมีไฟล์ Word ที่ทำงานได้เต็มรูปแบบซึ่งมีปุ่มที่คลิกได้ ซึ่งคุณสามารถปรับแต่งเพิ่มเติมหรือผูกกับ VBA macro ได้

---

## How to create forms2olecontrol in code – step‑by‑step

### Step 1: Initialise the DocumentBuilder

คลาส `DocumentBuilder` เป็นจุดเริ่มต้นสำหรับงานสร้างเอกสารส่วนใหญ่ใน Aspose.Words มันให้เมธอดสำหรับเพิ่มข้อความ, รูปภาพ, ตาราง, และที่สำคัญสำหรับบทเรียนนี้คือ OLE controls

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
`DocumentBuilder` รักษาตำแหน่งเคอร์เซอร์ปัจจุบันภายในเอกสาร การสร้างมันตั้งแต่ต้นทำให้คุณมั่นใจว่าการแทรกต่อไป—เช่น **ActiveX command button**—จะปรากฏตรงตำแหน่งที่ต้องการ

### Step 2: Insert the Forms2OleControl

เมธอด `insertForms2OleControl` จะคืนค่าอ็อบเจ็กต์ `Forms2OleControl` ซึ่งเป็นตัวแทนของ placeholder OLE ที่ Word จะเรนเดอร์เป็นปุ่ม ActiveX

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Why this matters:**  
หากไม่มีการเรียกเมธอดนี้ คุณจะไม่สามารถจัดการคุณสมบัติของคอนโทรลได้ `Forms2OleControl` ที่คืนมาจะให้คุณเข้าถึง **setOleClassName method**, คุณลักษณะขนาด, และการตั้งค่า OLE‑specific อื่น ๆ อย่างเต็มที่

### Step 3: Specify the ActiveX class with setOleClassName

Word ต้องรู้ว่าต้องเรนเดอร์คอนโทรล ActiveX ประเภทใด ชื่อคลาสสำหรับปุ่ม command button มาตรฐานคือ `"Forms.CommandButton.1"`

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Why this matters:**  
เมธอด `setOleClassName` เป็นสะพานเชื่อมระหว่าง placeholder OLE ทั่วไปกับ **ActiveX command button** ที่เป็นรูปธรรม การใช้ชื่อคลาสผิดจะทำให้วัตถุเป็นช่องว่างหรือเกิดข้อผิดพลาดขณะเปิดเอกสาร

### Step 4: Adjust the Forms2OleControl size

ปุ่มที่เล็กเกินไปหรือใหญ่เกินไปจะดูไม่เป็นมืออาชีพ คุณสามารถควบคุมขนาดได้ด้วย `setWidth` และ `setHeight`

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Why this matters:**  
คุณสมบัติเหล่านี้เป็นส่วนประกอบของ **Forms2OleControl size** พวกมันส่งผลต่อการแสดงผลของปุ่มใน UI ของ Word และทำให้มั่นใจว่ามีพื้นที่คลิกที่เพียงพอสำหรับแมโครที่ผูกไว้

### Step 5: Save the document and test

หลังจากกำหนดค่าคอนโทรลแล้ว ให้บันทึกเอกสารไปยังตำแหน่งที่คุณต้องการ

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

เปิด `ActiveXButton.docx` ด้วย Microsoft Word คุณควรเห็นปุ่มที่มีข้อความ “CommandButton1” (caption เริ่มต้น) การคลิกจะไม่มีผลใด ๆ เว้นแต่คุณจะเพิ่ม VBA macro, แต่คอนโทรลเองทำงานได้เต็มที่

**Expected output:**  

![เอกสาร Word ที่มีปุ่ม ActiveX command button แทรกอยู่](/images/activeX-button.png "ภาพหน้าจอของเอกสาร Word ที่แสดงปุ่ม ActiveX command button ที่สร้างใหม่โดยโค้ด")

*ข้อความ alt ของรูปภาพมีคีย์เวิร์ดหลักเพื่อการเข้าถึงและ SEO.*

---

## Understanding the ActiveX Forms2OleControl class

คลาส `Forms2OleControl` หุ้มโครงสร้าง OLE ระดับล่างที่ Word ใช้สำหรับองค์ประกอบ ActiveX มันสืบทอดจาก `Shape` ทำให้คุณสามารถใช้การจัดรูปแบบรูปทรงทั่วไป (เช่น เส้นขอบ, การหมุน) ได้หากต้องการ

* **ActiveX command button** – การใช้งานที่พบบ่อยที่สุด; คุณสามารถผูกกับแมโครผ่านเครื่องมือพัฒนาใน Word
* **setOleClassName method** – กำหนดว่า Word จะโหลด COM class ใด; ค่าที่ใช้ได้อื่น ๆ ได้แก่ `"Forms.TextBox.1"` และ `"Forms.ComboBox.1"`
* **Forms2OleControl size** – ควบคุมผ่าน `SetWidth`/`SetHeight` เมธอดเหล่านี้รับค่าเป็นจุด (1 pt = 1/72 in)

### When to use Forms2OleControl vs. Content Controls

หากคุณต้องการการป้อนข้อมูลอย่างง่าย (เช่น ฟิลด์ข้อความธรรมดา) คอนเทนต์คอนโทรลใน Word จะเบากว่า ใช้ `Forms2OleControl` เมื่อคุณต้องการฟังก์ชัน ActiveX เต็มรูปแบบ เช่น การจัดการเหตุการณ์หรือการโต้ตอบกับ VBA

---

## Setting additional properties (optional)

แม้ขั้นตอนหลักจะเพียงพอสำหรับ **create forms2olecontrol in code**, บ่อยครั้งคุณอาจต้องปรับแต่งลักษณะหรือพฤติกรรมของปุ่มเพิ่มเติม

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Why this matters:**  
`SetOleData` ให้คุณเขียนค่าคุณสมบัติต่าง ๆ ลงในสตรีม OLE โดยตรง นี่เป็นวิธีที่ยืดหยุ่นที่สุดในการปรับแต่ง **ActiveX command button** โดยไม่ต้องพึ่งพา VBA

---

## Common pitfalls and troubleshooting

| Symptom | Likely cause | Fix |
|--------|--------------|-----|
| Button appears as a gray box | Incorrect class name passed to `setOleClassName` | Verify the string is exactly `"Forms.CommandButton.1"` (case‑sensitive) |
| Size does not change | Width/Height set before inserting the control | Always call `SetWidth`/`SetHeight` **after** `InsertForms2OleControl` |
| Document throws “OLE object not found” on open | Missing Aspose.Words license (evaluation version may limit OLE) | Apply a valid license or use the free trial with full OLE support |
| Button caption stays “CommandButton1” | `SetOleData` not used or macro not reading the property | Use a VBA macro to read the `"Caption"` property or set the caption via the Word UI |

---

## Full, runnable example

ด้านล่างเป็นแอปพลิเคชันคอนโซลเต็มรูปแบบที่คุณสามารถคัดลอก, วาง, และรันได้ มันสาธิตทุกอย่างที่ครอบคลุมในบทเรียนนี้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Explanation of each section**

* **Using directives** – ดึงเนมสเปซ Aspose.Words ที่จำเป็นสำหรับ `Document`, `DocumentBuilder`, และ `Forms2OleControl`
* **Document creation** – สร้างไฟล์ Word เปล่า
* **InsertForms2OleControl** – วางคอนโทรล OLE ที่ตำแหน่งเคอร์เซอร์ปัจจุบันของ builder
* **SetOleClassName** – แจ้ง Word ว่าคอนโทรลเป็น **ActiveX command button**
* **SetWidth / SetHeight** – ปรับ **Forms2OleControl size** ให้ดูเป็นมืออาชีพ
* **SetOleData (optional)** – แสดงวิธีเขียนคุณสมบัติเพิ่มเติม เช่น caption
* **Save** – เขียนไฟล์ `.docx` สุดท้ายลงดิสก์

เรียกใช้โปรแกรม (`dotnet run`) แล้วเปิด `ActiveXButton.docx` คุณควรเห็นปุ่มที่สามารถเชื่อมต่อกับแมโครในภายหลังได้

---

## Conclusion

คุณได้เรียนรู้วิธี **create forms2olecontrol in code** ด้วย Aspose.Words ตั้งแต่การเริ่มต้น `DocumentBuilder` จนถึงการกำหนดค่า **ActiveX command button** ด้วย `setOleClassName` และการควบคุม **Forms2OleControl size** วิธีนี้ช่วยให้คุณอัตโนมัติเอกสาร Word ที่ซับซ้อน, ฝังองค์ประกอบ UI ที่โต้ตอบได้, และเก็บตรรกะทั้งหมดไว้ภายในโค้ดของคุณ

## What Should You Learn Next?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดที่ทำงานได้เต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบต่าง ๆ ในโครงการของคุณ

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}