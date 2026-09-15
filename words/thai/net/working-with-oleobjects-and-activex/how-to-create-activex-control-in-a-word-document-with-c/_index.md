---
category: general
date: 2026-09-14
description: สร้างคอนโทรล ActiveX ในเอกสาร Word ด้วย C# เรียนรู้วิธีแทรก ActiveX,
  เพิ่มปุ่มโต้ตอบ, และสร้างไฟล์ .docx อย่างอัตโนมัติ
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: th
lastmod: 2026-09-14
og_description: สร้างคอนโทรล ActiveX ในเอกสาร Word ด้วย C#. ทำตามตัวอย่างเต็มนี้เพื่อแทรก
  ActiveX, เพิ่มปุ่มโต้ตอบ, และบันทึกไฟล์.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: สร้างคอนโทรล ActiveX ใน Word ด้วย C# – คู่มือแบบทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: วิธีสร้าง ActiveX control ในเอกสาร Word ด้วย C#
url: /th/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้าง ActiveX control ในเอกสาร Word ด้วย C#

หากคุณต้องการ **สร้าง ActiveX control** ภายในไฟล์ Microsoft Word คู่มือนี้จะแสดงวิธีแก้ไขที่สมบูรณ์และพร้อมใช้งาน คุณจะได้เห็นวิธีแทรก ActiveX CommandButton ตั้งค่าคุณสมบัติของมัน และบันทึกไฟล์ `.docx` ที่ได้โดยใช้เพียงโค้ด C#  

การเพิ่มปุ่มโต้ตอบลงในเอกสาร Word เป็นความต้องการทั่วไปเมื่อคุณต้องการให้ผู้ใช้ปลายทางเรียกใช้แมโครหรือโลจิกที่กำหนดเองโดยตรงจาก UI ของเอกสาร ตัวอย่างด้านล่างจะแสดง **วิธีแทรก ActiveX** โดยไม่ต้องพึ่งพาเครื่องมือของบุคคลที่สาม และยังครอบคลุม **วิธีสร้าง Word document** ด้วยโปรแกรม

เมื่อจบบทเรียนนี้คุณจะสามารถ **สร้างปุ่มด้วยโค้ด**, ปรับแต่งคำบรรยายของมัน, และสร้างไฟล์ Word ที่พกพาได้ซึ่งคงไว้ซึ่ง ActiveX control

## ข้อกำหนดเบื้องต้น

- .NET 6.0 หรือใหม่กว่า (ไลบรารี Aspose.Words for .NET ทำงานกับ .NET Core และ .NET Framework)
- การอ้างอิงไปยังแพ็กเกจ `Aspose.Words` บน NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
- ความรู้พื้นฐานเกี่ยวกับ C# และการเขียนโปรแกรมเชิงวัตถุ

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า namespaces

สร้างโปรเจกต์คอนโซลใหม่ (หรือผสานโค้ดนี้เข้ากับแอปพลิเคชัน C# ที่มีอยู่) แล้วนำเข้า namespaces ที่จำเป็นเพื่อให้คอมไพเลอร์สามารถค้นหาคลาสการประมวลผล Word  

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **ทำไมขั้นตอนนี้สำคัญ** – API `Aspose.Words` จะให้คลาส `Document`, `DocumentBuilder` และ `Forms2OleControl` ที่ช่วยให้คุณจัดการไฟล์ Word ในระดับอ็อบเจกต์ หากไม่มีการอ้างอิงเหล่านี้ โค้ดส่วนที่เหลือจะไม่สามารถคอมไพล์ได้

## ขั้นตอนที่ 2: สร้าง Word document ใหม่และ DocumentBuilder

อ็อบเจกต์ `Document` แทนชุดไฟล์ `.docx` ทั้งหมด ส่วน `DocumentBuilder` ให้ API แบบ fluent สำหรับแทรกเนื้อหา  

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **คำอธิบาย** – การสร้าง `Document` ใหม่ให้คุณมี “ผ้าใบ” ที่สะอาด Builder จะเริ่มที่ตำแหน่งเคอร์เซอร์แรกของส่วนแรก พร้อมสำหรับการแทรกต่อไป

## ขั้นตอนที่ 3: แทรก ActiveX CommandButton

ใช้เมธอด `InsertForms2OleControl` เพื่อตำแหน่ง ActiveX control ที่ตำแหน่งที่กำหนด เมธอดต้องการประเภทของคอนโทรลและ `RectangleF` ที่กำหนดพิกัด X/Y และขนาด (หน่วยเป็น point)  

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **ทำไมวิธีนี้ถึงได้ผล** – `OleControlType.CommandButton` บอก API ให้สร้าง Windows CommandButton มาตรฐาน ส่วนสี่เหลี่ยมกำหนดตำแหน่งปุ่มสัมพันธ์กับมุมบนซ้ายของหน้า ทำให้คุณ **เพิ่มปุ่มโต้ตอบ** ได้ตรงที่ต้องการ

## ขั้นตอนที่ 4: ตั้งค่าคุณสมบัติของปุ่ม

ตอนนี้ให้ตั้งข้อความที่แสดง (`Caption`) และชื่อภายใน (`Name`) ของปุ่ม คุณสมบัติเหล่านี้คือสิ่งที่ผู้ใช้เห็นและ VBA code จะอ้างอิงต่อไป  

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **เคล็ดลับปฏิบัติ** – `Name` ต้องไม่ซ้ำกันภายในเอกสาร มิฉะนั้นแมโคร VBA อาจอ้างอิงคอนโทรลผิด

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายให้เขียนไฟล์ลงดิสก์ ActiveX control จะถูกเก็บไว้ในแพ็กเกจ Word ดังนั้นไฟล์ที่บันทึกจะคงความทำงานเต็มรูปแบบเมื่อเปิดใน Microsoft Word  

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **ผลลัพธ์** – การเปิด `CommandButton.docx` ใน Word จะแสดง CommandButton ที่คลิกได้พร้อมข้อความ “Click Me” คอนโทรลสามารถเชื่อมโยงกับแมโครได้ผ่าน UI ของ Word (`Developer → Design Mode → Properties`)

## รายการซอร์สโค้ดเต็ม

รวมทุกขั้นตอนเข้าด้วยกันจะได้โปรแกรมเดียวที่ทำงานอิสระ คุณสามารถคัดลอก วาง และรันได้ทันที  

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

การรันโปรแกรมจะพิมพ์บรรทัดยืนยัน:  

```
Document saved to C:\Temp\CommandButton.docx
```

เมื่อคุณเปิดไฟล์ที่สร้างขึ้นใน Microsoft Word คุณจะเห็น **CommandButton** ปรากฏที่พิกัดที่กำหนด การคลิกปุ่มในโหมดออกแบบจะทำให้มันถูกเลือก; ในโหมดรันจะทำงานเหมือน ActiveX button ปกติ

## ความแตกต่างทั่วไปและกรณีขอบ

| สถานการณ์ | การปรับเปลี่ยน |
|----------|------------|
| **Different control type** | แทนที่ `OleControlType.CommandButton` ด้วย `OleControlType.CheckBox`, `OleControlType.OptionButton` ฯลฯ |
| **Multiple buttons** | เรียก `InsertForms2OleControl` ซ้ำหลายครั้งโดยอัปเดตพิกัด `RectangleF` สำหรับแต่ละปุ่มใหม่ |
| **Dynamic sizing** | คำนวณขนาดสี่เหลี่ยมตามขนาดหน้า (`builder.PageSetup.PageWidth`) |
| **Saving to a stream** | ใช้ `document.Save(stream, SaveFormat.Docx)` เมื่อจำเป็นต้องส่งไฟล์กลับจากเว็บ API |
| **Word 97‑2003 format** | เปลี่ยนรูปแบบการบันทึกเป็น `SaveFormat.Doc` เพื่อสร้างไฟล์ `.doc` ที่ยังคงฝัง ActiveX control |

> **Pro tip:** ควรทดสอบเอกสารที่สร้างขึ้นบนเวอร์ชัน Word ที่เป้าหมายเสมอ เพราะบางเวอร์ชันอาจมีการตั้งค่าความปลอดภัยที่ปิดการใช้งาน ActiveX control โดยค่าเริ่มต้น

## คำถามที่พบบ่อย

**ทำงานกับ .NET Core ได้หรือไม่?**  
ใช่ ไลบรารี Aspose.Words เป็นแบบข้ามแพลตฟอร์มและเข้ากันได้เต็มที่กับ .NET Core และ .NET 5/6+

**สามารถกำหนดแมโครให้กับปุ่มโดยโปรแกรมได้หรือไม่?**  
API ไม่ได้ฝังโค้ด VBA โดยตรง หลังจากสร้างเอกสารแล้ว ให้เปิดใน Word, เปิดแท็บ Developer, แล้วบันทึกหรือเขียนแมโครที่อ้างอิง `btnClick`

**ถ้าปุ่มไม่ปรากฏจะทำอย่างไร?**  
ตรวจสอบว่าแท็บ `Developer` เปิดใช้งานใน Word และเอกสารไม่ได้เปิดใน **Protected View** อีกทั้งตรวจสอบว่าพิกัดสี่เหลี่ยมอยู่ภายในขอบกระดาษ

## สรุป

คุณได้เรียนรู้วิธี **สร้าง ActiveX control** ภายในไฟล์ Word ด้วย C# แล้ว บทเรียนนี้ครอบคลุม **วิธีแทรก ActiveX**, แสดง **การเพิ่มปุ่มโต้ตอบ**, สาธิต **การสร้าง Word document** ตั้งแต่ต้น, และอธิบาย **การสร้างปุ่มด้วยโค้ด** ที่คงอยู่หลังการบันทึก  

ต่อจากนี้คุณสามารถสำรวจประเภท ActiveX เพิ่มเติม, เชื่อมปุ่มกับแมโคร VBA, หรือฝังโลจิกนี้ในบริการสร้างเอกสารขนาดใหญ่ ทดลองปรับขนาด, ตำแหน่ง, และคุณสมบัติต่าง ๆ เพื่อให้ได้ประสบการณ์ผู้ใช้ที่ตรงตามความต้องการของคุณ

---


## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีโค้ดตัวอย่างทำงานครบถ้วนพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณเอง

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Vba Project in Word Document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}