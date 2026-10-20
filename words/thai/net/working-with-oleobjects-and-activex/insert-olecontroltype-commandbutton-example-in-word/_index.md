---
category: general
date: 2026-08-17
description: แทรกตัวอย่าง OleControlType.CommandButton ใน Word ด้วย Aspose.Words.
  เรียนรู้วิธีเพิ่มฟอร์มคอนโทรลลงในเอกสาร Word อย่างโปรแกรมมิ่ง.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: th
lastmod: 2026-08-17
og_description: แทรกตัวอย่าง OleControlType.CommandButton ใน Word ด้วย Aspose.Words.
  ทำตามคำแนะนำนี้เพื่อเพิ่มคอนโทรลฟอร์มในเอกสาร Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: แทรกตัวอย่าง OleControlType.CommandButton ใน Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: แทรกตัวอย่าง OleControlType.CommandButton ใน Word
url: /th/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกตัวอย่าง OleControlType.CommandButton ใน Word

หากคุณต้องการ **insert OleControlType.CommandButton example** ลงในไฟล์ Word คำแนะนำนี้จะแสดงวิธีทำ คุณจะได้เรียนรู้ **how to add form controls to a Word document** ด้วย Aspose.Words พร้อมโปรแกรม C# ที่สมบูรณ์และสามารถรันได้

ฟอร์มคอนโทรล เช่น ปุ่ม ActiveX ช่วยให้คุณสร้างเทมเพลต Word ที่โต้ตอบได้—มีประโยชน์สำหรับสัญญา แบบสอบถาม หรือเครื่องมือภายใน ขั้นตอนต่อไปนี้ครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโครงการจนถึงการตรวจสอบว่าปุ่มปรากฏอย่างถูกต้องในไฟล์ `.docx` ที่บันทึกไว้

## ข้อกำหนดเบื้องต้น

- .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า ติดตั้งแล้ว  
- Visual Studio 2022 (หรือ IDE C# ใดก็ได้)  
- ใบอนุญาต Aspose.Words for .NET หรือใบอนุญาตชั่วคราวฟรี  
- ความคุ้นเคยพื้นฐานกับ C# และแนวคิดไฟล์ Word  

> **Pro tip:** หากคุณใช้รุ่นทดลองฟรี ให้วางไฟล์ใบอนุญาตในโฟลเดอร์เดียวกับไฟล์ executable และโหลดมันในตอนเริ่มต้นของ `Main`.

## ขั้นตอนที่ 1: สร้างโปรเจกต์คอนโซลใหม่และเพิ่ม Aspose.Words

เปิดเทอร์มินัลและรัน:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

คำสั่งนี้จะสร้างโปรเจกต์ที่สะอาดและดึงแพคเกจ Aspose.Words ล่าสุด ซึ่งให้ API `Document`, `DocumentBuilder`, และ `InsertForms2OleControl` ที่จำเป็นสำหรับ **insert OleControlType.CommandButton example**.

## ขั้นตอนที่ 2: เขียนโปรแกรมเต็มรูปแบบ

สร้างหรือแทนที่ไฟล์ `Program.cs` ด้วยโค้ดต่อไปนี้ ซึ่งประกอบด้วยคำสั่ง `using` ที่จำเป็นทั้งหมด การโหลดใบอนุญาต และกระบวนการทำงานสี่ขั้นตอนที่แสดงในตัวอย่างต้นฉบับ

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### ทำไมแต่ละบรรทัดจึงสำคัญ

* **License loading** – ทำให้แน่ใจว่าคุณไม่ได้ถูกจำกัดโดยข้อจำกัดของรุ่นทดลอง.  
* **`Document doc = new Document();`** – สร้างคอนเทนเนอร์สำหรับเนื้อหา Word ทั้งหมด; นี้เป็นพื้นฐานของ **insert OleControlType.CommandButton example**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – ให้ API แบบ fluent เพื่อเพิ่มข้อความ, รูปภาพ, และคอนโทรล.  
* **`InsertForms2OleControl`** – เมธอดหลักที่ทำงาน **how to add form controls to a Word document**. ค่า enum `OleControlType.CommandButton` บอก Aspose.Words ให้สร้างปุ่ม ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – กำหนดตำแหน่งปุ่ม 100 pts จากขอบซ้ายและบน, ความกว้าง 80 pts และความสูง 30 pts. ปรับค่าตัวเลขเหล่านี้ให้เหมาะกับเลย์เอาต์ของคุณ.  
* **`doc.Save`** – เขียนไฟล์ .docx ไปยังดิสก์; ไฟล์ตอนนี้มีปุ่มที่ฝังอยู่.

## ขั้นตอนที่ 3: สร้างและรันโปรแกรม

จากโฟลเดอร์โปรเจกต์ ให้เรียกใช้:

```bash
dotnet run
```

คุณควรเห็นข้อความในคอนโซล:

```
Document saved to ActiveXButton.docx
```

เปิดไฟล์ `ActiveXButton.docx` ด้วย Microsoft Word คุณจะเห็นปุ่มที่มีข้อความ **ClickMe** อยู่ประมาณกลางหน้า การคลิกปุ่มจะเรียกพฤติกรรมเริ่มต้นของ ActiveX (ซึ่งโดยทั่วไปไม่มีการทำงานใด ๆ เว้นแต่คุณจะผูกแมโคร).

![ตัวอย่าง insert olecontroltype.commandbutton](/images/activex-button.png "ActiveX CommandButton แทรกลงในเอกสาร Word")

*ข้อความแทนภาพ:* insert olecontroltype.commandbutton example – ปุ่ม ActiveX CommandButton ที่แสดงในเอกสาร Word.

## ขั้นตอนที่ 4: ปรับแต่งปุ่ม (ทางเลือก)

ตัวอย่าง **insert OleControlType.CommandButton example** พื้นฐานจะสร้างปุ่มเริ่มต้น คุณสามารถแก้ไขข้อความบนปุ่ม, ฟอนต์, หรือแม้แต่ผูกแมโครโดยแก้ไขอ็อบเจกต์ OLE ที่อยู่ด้านล่างนี้เป็นวิธีสั้น ๆ ในการเปลี่ยนข้อความของปุ่มหลังจากแทรก:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Note:** การจัดการโดยตรงกับคุณสมบัติ OLE ต้องอาศัยความเข้าใจในอินเทอร์เฟซ COM ที่อยู่ด้านล่าง สำหรับสถานการณ์ส่วนใหญ่ ข้อความเริ่มต้นก็เพียงพอ.

## ขั้นตอนที่ 5: ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| ปุ่มไม่ปรากฏใน Word | เอกสารถูกบันทึกเป็น `.docx` แต่เปิดในโปรแกรมดูที่ลบคอนโทรล OLE (เช่น Google Docs). | เปิดไฟล์ด้วย Microsoft Word หรือ Word Online พร้อมสิทธิ์แก้ไข. |
| Runtime error `ArgumentOutOfRangeException` | พิกัด `Rectangle` อยู่เหนือขอบกระดาษ. | ใช้ค่าที่อยู่ภายในขนาดหน้า (เช่น 0‑500 สำหรับ A4). |
| License exception | ใบอนุญาตทดลองหมดอายุหลัง 30 วัน. | โหลดไฟล์ใบอนุญาตที่ถูกต้องหรือขอทดลองใช้ต่อจาก Aspose. |

## ขั้นตอนที่ 6: ตัวอย่างนี้เข้ากับโครงการอัตโนมัติขนาดใหญ่ได้อย่างไร

เมื่อคุณต้องการ **how to add form controls to Word document** ในระดับใหญ่—เช่นการสร้างเทมเพลตสัญญาหลายร้อยฉบับ—ให้ห่อหุ้มตรรกะการแทรกในเมธอดที่ใช้ซ้ำได้:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

จากนั้นคุณสามารถเรียก `AddCommandButton` ภายในลูปที่ประมวลผลแถวข้อมูล เพื่อให้แน่ใจว่าแต่ละเอกสารที่สร้างมีปุ่มที่มีชื่อเฉพาะ (เช่น `Approve_001`, `Approve_002`).

## สรุป

ตอนนี้คุณมี **insert OleControlType.CommandButton example** ที่สมบูรณ์ซึ่งแสดง **how to add form controls to a Word document** ด้วย Aspose.Words for .NET คู่มือได้ครอบคลุมการตั้งค่าโครงการ, โค้ดต้นฉบับเต็ม, เคล็ดลับการปรับแต่ง, และขั้นตอนการแก้ไขปัญหาทั่วไป

จากนี้คุณอาจสำรวจ:

- เพิ่มประเภทคอนโทรลอื่น ๆ เช่น **CheckBox** หรือ **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- ผูกปุ่มกับแมโคร VBA เพื่อเพิ่มความโต้ตอบ.  
- สร้าง PDF จากเอกสารเดียวกันพร้อมคงฟิลด์ฟอร์ม.

ทดลองใช้ขนาด, ตำแหน่ง, และชื่อคอนโทรลที่แตกต่างกันเพื่อให้เหมาะกับกรณีการใช้งานของคุณ. ขอให้เขียนโค้ดอย่างสนุก!

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ

- [แทรกฟิลด์ฟอร์ม Combo Box ในเอกสาร Word](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [แทรกฟิลด์ฟอร์ม Check Box ในเอกสาร Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [แทรกฟิลด์ฟอร์ม Text Input ในเอกสาร Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}