---
category: general
date: 2026-09-11
description: เรียนรู้วิธีสร้างเอกสาร Word ด้วย C# และเพิ่มปุ่มคำสั่งโดยโปรแกรมโดยใช้
  Aspose.Words ในไม่กี่ขั้นตอนง่าย ๆ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: th
lastmod: 2026-09-11
og_description: สร้างเอกสาร Word ด้วย C# และเพิ่มปุ่มคำสั่งโดยโปรแกรมด้วย Aspose.Words.
  ทำตามคู่มือฉบับเต็มนี้เพื่อรับโซลูชันที่ทำงานได้.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: สร้างเอกสาร Word ด้วย C# – เพิ่มปุ่มคำสั่งโดยโปรแกรม
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: วิธีสร้างเอกสาร Word ด้วย C# และเพิ่มปุ่มคำสั่งโดยโปรแกรม
url: /th/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้าง word document c# และเพิ่มปุ่มคำสั่งโดยโปรแกรม

หากคุณต้องการ **create word document c#** และฝังปุ่มเชิงโต้ตอบ คู่มือนี้จะแสดงให้คุณเห็นขั้นตอนที่แน่นอนในการทำเช่นนั้น ด้วย Aspose.Words คุณสามารถเพิ่มปุ่มคำสั่งโดยโปรแกรมได้ด้วยเพียงไม่กี่บรรทัดของโค้ด ลดความจำเป็นในการทำงาน UI ด้วยตนเองใน Word

ในบทเรียนนี้คุณจะได้เรียนรู้วิธี:

* เริ่มต้นไฟล์ Word เปล่าด้วย C#  
* แทรกคอนโทรล ActiveX **CommandButton**  
* ตั้งค่าคุณสมบัติต่าง ๆ ของปุ่ม เช่น ชื่อและคำบรรยาย  
* บันทึกเอกสารเพื่อให้ปุ่มปรากฏเมื่อเปิดไฟล์ใน Microsoft Word  

ไม่จำเป็นต้องใช้เครื่องมือภายนอกใด ๆ นอกจากไลบรารี Aspose.Words for .NET และขั้นตอนเหล่านี้ทำงานได้กับ .NET 6+ หรือ .NET Framework 4.6.2 ขึ้นไป

## ความต้องการเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

| Requirement | Reason |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | ให้ runtime สำหรับโปรเจกต์ C# |
| Visual Studio 2022 (or any C# IDE) | ทำให้การเขียน, คอมไพล์, และรันโค้ดเป็นเรื่องง่าย |
| Aspose.Words for .NET NuGet package | มีคลาส `Document`, `DocumentBuilder` และ `Forms2OleControl` ที่ใช้ในตัวอย่าง |
| Basic knowledge of C# syntax | ช่วยให้คุณตามโค้ดได้โดยไม่ต้องเรียนรู้เพิ่มเติม |

คุณสามารถเพิ่มแพคเกจ Aspose.Words ผ่านคอนโซล NuGet ได้ดังนี้:

```powershell
Install-Package Aspose.Words
```

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์คอนโซล C# ใหม่

สร้างแอปพลิเคชันคอนโซลที่จะสร้างไฟล์ Word เปิดเทอร์มินัลและรันคำสั่ง:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

ไฟล์ `Program.cs` ที่สร้างขึ้นจะเป็นที่เก็บโค้ดที่แสดงในขั้นตอนต่อไป

## ขั้นตอนที่ 2: สร้างเอกสารเปล่าและ DocumentBuilder

การดำเนินการแรกคือการสร้างอ็อบเจกต์ `Document` ซึ่งเป็นไฟล์ `.docx` ว่างเปล่า และ `DocumentBuilder` ที่ช่วยให้คุณแก้ไขเนื้อหาในเอกสารได้

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
`Document` คือคอนเทนเนอร์ขององค์ประกอบทั้งหมดใน Word (ย่อหน้า, ตาราง, คอนโทรล) ส่วน `DocumentBuilder` ให้ API แบบ fluent เพื่อแทรกอ็อบเจกต์ที่ตำแหน่งเคอร์เซอร์ปัจจุบันโดยไม่ต้องจัดการกับคอลเลกชันโหนดระดับต่ำ

## ขั้นตอนที่ 3: แทรกคอนโทรล ActiveX CommandButton

Aspose.Words รองรับการแทรกคอนโทรล ActiveX แบบเก่าผ่านเมธอด `InsertForms2OleControl` เมธอดนี้ต้องการประเภทคอนโทรลและขนาดที่ต้องการเป็นจุด

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**สิ่งที่เกิดขึ้นเบื้องหลัง:**  
Word ถือคอนโทรล ActiveX เป็นอ็อบเจกต์ OLE (Object Linking and Embedding) คลาส `Forms2OleControl` จะห่อข้อมูล OLE และเปิดเผยคุณสมบัติต่าง ๆ เช่น `Name` และ `Caption`

## ขั้นตอนที่ 4: ตั้งค่าชื่อและคำบรรยายของปุ่ม

หลังจากวางคอนโทรลแล้ว คุณสามารถปรับแต่งคุณสมบัติของมันได้ การตั้งค่า `Name` ที่มีความหมายช่วยให้คุณระบุปุ่มได้ในภายหลัง ส่วน `Caption` กำหนดข้อความที่แสดงบนปุ่ม

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**เคล็ดลับ:**  
หากคุณต้องการจัดการเหตุการณ์คลิกของปุ่มด้วย VBA, `Name` จะกลายเป็นชื่อแมโครที่คุณอ้างอิง เช่น `Sub btnSubmit_Click()`  

## ขั้นตอนที่ 5: บันทึกเอกสารลงดิสก์

สุดท้ายให้เขียนเอกสารลงไฟล์ `.docx` เลือกโฟลเดอร์ที่คุณมีสิทธิ์เขียน; ตัวอย่างใช้เส้นทางสัมพันธ์ซึ่งจะชี้ไปยังไดเรกทอรีเอาต์พุตของโปรเจกต์

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `CommandButton.docx` การเปิดไฟล์ใน Microsoft Word จะแสดงปุ่ม **Submit** ที่คลิกได้:

![เอกสาร Word ที่มีปุ่ม Submit](/images/command-button.png "ภาพหน้าจอของเอกสาร Word ที่มีปุ่ม Submit สร้างด้วย C#")

*ข้อความแทนภาพ (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## ตรวจสอบผลลัพธ์

1. เปิด Word แล้วเปิดไฟล์ `CommandButton.docx`  
2. คุณควรเห็นปุ่มที่มีข้อความ **Submit** อยู่ในเนื้อหาเอกสาร  
3. เมื่อนำเมาส์ไปวางเหนือปุ่ม จะเห็นชื่อ `btnSubmit` ในแผง **Properties** (แท็บ Developer → Properties)  

หากปุ่มไม่ปรากฏ ตรวจสอบให้แน่ใจว่าแท็บ **Developer** ถูกเปิดใช้งานใน Word (File → Options → Customize Ribbon → เลือก *Developer*) คอนโทรล ActiveX จะถูกซ่อนเมื่อแท็บถูกปิด

## จัดการกับความหลากหลายและกรณีขอบเขตทั่วไป

| Situation | Recommended adjustment |
|-----------|------------------------|
| **Different button size** | เปลี่ยนค่าอาร์กิวเมนต์ความกว้างและความสูงใน `InsertForms2OleControl` ตัวอย่างเช่น `150, 40` จะสร้างปุ่มที่ใหญ่ขึ้น |
| **Multiple buttons** | เรียก `InsertForms2OleControl` ซ้ำ ๆ โดยย้ายเคอร์เซอร์ของ builder ระหว่างการเรียก (`builder.Writeln();`) |
| **Button without ActiveX** | ใช้ `InsertFormField` เพื่อเพิ่มฟิลด์ฟอร์มแบบเก่า (เช่น checkbox) หากต้องการความเข้ากันได้กับเวอร์ชัน Word เก่าที่บล็อก ActiveX |
| **Cross‑platform usage** | คอนโทรล ActiveX ทำงานได้เฉพาะบน Word เวอร์ชัน Windows สำหรับ Mac หรือผู้ชมบนเว็บ ควรพิจารณาแทรกลิงก์ที่สไตล์เป็นปุ่มแทน |
| **Security warnings** | Word อาจแสดงคำเตือนความปลอดภัยเมื่อเปิดเอกสารที่มีคอนโทรล ActiveX การเซ็นเอกสารด้วยใบรับรองที่เชื่อถือได้จะลดความรบกวนนี้ |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมทั้งหมดที่คุณสามารถคัดลอก‑วางลงใน `Program.cs` มันจะคอมไพล์และรันได้โดยไม่ต้องแก้ไขเพิ่มเติมหลังจากเพิ่มแพคเกจ Aspose.Words NuGet

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

การเปิดไฟล์ที่สร้างขึ้นจะแสดงปุ่ม **Submit** พร้อมใช้งาน

## สรุป

คุณได้เรียนรู้วิธี **create word document c#** และ **programmatically add command button** ด้วย Aspose.Words กระบวนการสรุปได้เป็นการสร้าง `Document` แทรก `Forms2OleControl` ตั้งค่าคุณสมบัติ และบันทึกไฟล์ จากนี้คุณสามารถ:

* เพิ่มคอนโทรลอื่น ๆ (เช่น checkbox, text field) โดยเปลี่ยน `ControlType`  
* แนบแมโคร VBA ให้กับปุ่มเพื่อทำตรรกะที่กำหนดเอง  
* ผสานเทคนิคนี้กับฟีเจอร์ Aspose.Words อื่น ๆ เช่น mail merge หรือการเติมเทมเพลต  

ลองปรับขนาด, คำบรรยาย, และจำนวนปุ่มต่าง ๆ เพื่อให้เหมาะกับสถานการณ์อัตโนมัติของคุณ ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโปรเจกต์ของคุณ

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}