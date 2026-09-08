---
category: general
date: 2026-09-08
description: วิธีบันทึกไฟล์ docx ขณะแทรกคอนโทรล ActiveX ใน C#. ทำตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อเพิ่มปุ่มคำสั่งโดยโปรแกรม.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: th
lastmod: 2026-09-08
og_description: วิธีบันทึกไฟล์ docx ขณะแทรก ActiveX control ใน C# บทเรียนนี้จะพาคุณผ่านขั้นตอนการสร้างเอกสาร
  Word ด้วยโปรแกรม การเพิ่มปุ่มคำสั่ง และการบันทึกไฟล์อย่างถาวร
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: วิธีบันทึกไฟล์ docx และฝังปุ่ม ActiveX ใน C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: วิธีบันทึกไฟล์ docx และแทรกปุ่ม ActiveX ด้วย C#
url: /th/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีบันทึกไฟล์ docx และแทรกปุ่ม ActiveX ด้วย C#

หากคุณต้องการสร้างเอกสาร Word อย่างอัตโนมัติแล้วบันทึกเป็น docx พร้อมปุ่มโต้ตอบ คู่มือนี้จะแสดงวิธีทำ คุณจะได้เรียนรู้การแทรกคอนโทรล ActiveX, เพิ่มปุ่ม ActiveX, และบันทึกไฟล์ .docx ที่ได้ด้วย C# และไลบรารี Aspose.Words

บทเรียนนี้ครอบคลุมทุกขั้นตอนที่จำเป็นในการ **สร้างเอกสาร Word อย่างโปรแกรมมิ่ง**, ฝัง **ปุ่มคำสั่ง**, และบันทึกไฟล์ลงดิสก์ ไม่จำเป็นต้องมีประสบการณ์กับวัตถุ COM ก่อนหน้า แต่ควรมีความรู้พื้นฐานของ C# และติดตั้ง Visual Studio ไว้แล้ว

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือใหม่กว่า  
* Visual Studio 2022 (หรือ IDE สำหรับ C# ใดก็ได้)  
* Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
* ความเข้าใจโครงสร้างโปรเจกต์ C#  

รายการเหล่านี้รับประกันว่าโค้ดจะคอมไพล์และทำงานได้โดยไม่ต้องตั้งค่าเพิ่มเติม

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์คอนโซล C# ใหม่

สร้างแอปพลิเคชันคอนโซลที่จะเป็นโฮสต์ให้กับตรรกะการทำงานของ Word

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

คำสั่งข้างต้นจะสร้างโฟลเดอร์ชื่อ **WordActiveXDemo**, เพิ่มการอ้างอิง Aspose.Words, และเตรียมโปรเจกต์สำหรับการคอมไพล์

## ขั้นตอนที่ 2: สร้างเอกสาร Word อย่างโปรแกรมมิ่ง

เปิดไฟล์ `Program.cs` ที่สร้างขึ้นและเพิ่ม `using` directives ที่จำเป็น

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

จากนั้นสร้างอ็อบเจกต์ `Document` เปล่าออบเจกต์นี้เป็นตัวแทนของไฟล์ Word ทั้งไฟล์ในหน่วยความจำ

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

คลาส `Document` เป็นจุดเริ่มต้นสำหรับการดำเนินการทุกอย่างของการประมวลผล Word ในขั้นตอนนี้เอกสารยังไม่มีหน้าใด ๆ แต่ Aspose.Words จะสร้างส่วน (section) เริ่มต้นโดยอัตโนมัติเมื่อคุณเพิ่มเนื้อหา

## ขั้นตอนที่ 3: แทรกคอนโทรล ActiveX – เพิ่มปุ่ม activex

อ็อบเจกต์ **Forms2OleControl** ช่วยให้คุณฝังคอนโทรล ActiveX ไว้ในย่อหน้าของ Word โค้ดต่อไปนี้จะแทรก **CommandButton** ที่มีความกว้าง 150 pt และความสูง 30 pt

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` จะสร้างคอนโทรลและคืนค่าเป็นอินสแตนซ์ `Forms2OleControl` ที่มีชนิดชัดเจน ซึ่งคุณสามารถกำหนดค่าเพิ่มเติมได้ วิธีการนี้จะเพิ่มย่อหน้าใหม่โดยอัตโนมัติเพื่อเป็นโฮสต์ให้คอนโทรล ดังนั้นคุณไม่ต้องจัดการอ็อบเจกต์ย่อหน้าเอง

## ขั้นตอนที่ 4: ตั้งค่าปุ่มคำสั่ง – วิธีเพิ่มคุณสมบัติของปุ่มคำสั่ง

กำหนดคุณสมบัติ **Name** และ **Caption** ของปุ่มเพื่อให้สามารถระบุได้ในระหว่างรันไทม์และเป็นมิตรต่อผู้ใช้ใน UI

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

แอตทริบิวต์ `Name` มีประโยชน์เมื่อคุณต้องการจัดการเหตุการณ์คลิกของปุ่มผ่าน VBA หรือแมโครของ Word ส่วน `Caption` คือข้อความที่ผู้ใช้เห็นบนพื้นผิวของปุ่ม

### เคล็ดลับ
หากคุณวางแผนจะจัดการเหตุการณ์คลิกจาก C#, ให้ฝังแมโคร VBA ที่อ้างอิง `cmdSubmit` Word จะถามผู้ใช้ให้เปิดใช้งานแมโครเมื่อเปิดเอกสาร ซึ่งเป็นพฤติกรรมความปลอดภัยมาตรฐานสำหรับคอนโทรล ActiveX

## ขั้นตอนที่ 5: วิธีบันทึก docx

เมื่อคอนโทรลถูกวางไว้แล้ว ให้บันทึกเอกสารเป็นไฟล์ .docx วิธี `Save` จะเลือกฟอร์แมตที่เหมาะสมโดยอัตโนมัติตามส่วนขยายของไฟล์

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

การบันทึกไฟล์เป็นขั้นตอนสุดท้ายของ **วิธีบันทึก docx** ไฟล์ที่ได้สามารถเปิดใน Microsoft Word ได้โดยปุ่ม ActiveX จะปรากฏบนหน้าแรก เมื่อคลิกปุ่ม Word จะแสดงข้อความตัวอย่างหากไม่มีแมโครเชื่อมต่อ

## ขั้นตอนที่ 6: รันโปรแกรมและตรวจสอบผลลัพธ์

คอมไพล์และเรียกใช้แอปคอนโซล:

```bash
dotnet run
```

หลังจากโปรแกรมทำงานเสร็จ ให้เปิด `C:\Temp\CommandButton.docx` ใน Microsoft Word:

* เอกสารมีหน้าเดียวพร้อมปุ่ม **Submit** อยู่ใกล้ด้านบน  
* การวางเมาส์เหนือปุ่มจะแสดง tooltip ที่มีชื่อ `cmdSubmit`  
* ไม่มีเนื้อหาหายไปและขนาดไฟล์เทียบเคียงกับ .docx เปล่ามาตรฐาน

หากปุ่มไม่ปรากฏ ให้ตรวจสอบว่า:

1. การตั้งค่า **Trust Center** ของ Word อนุญาตคอนโทรล ActiveX  
2. ไฟล์ถูกบันทึกด้วยส่วนขยาย `.docx` (ไม่ใช่ `.doc`)  

## กรณีขอบและความแตกต่างทั่วไป

| สถานการณ์ | การปรับแต่งที่แนะนำ |
|-----------|------------------------|
| ต้องการขนาดปุ่มที่ต่างออกไป | เปลี่ยนค่า width และ height ใน `InsertForms2OleControl` |
| ต้องการให้ปุ่มอยู่บนหน้าที่กำหนด | ใช้ `builder.MoveToDocumentEnd();` หลังจากเพิ่มหน้า หรือแทรกการขึ้นหน้า (page break) ก่อนคอนโทรล |
| ต้องรองรับสภาพแวดล้อมที่ไม่มี Aspose.Words | ใช้ Open XML SDK เพื่อแทรกองค์ประกอบ `w:object` แต่โค้ดจะซับซ้อนมากขึ้น |
| ต้องการเอกสารที่เปิดใช้งานแมโคร | บันทึกด้วยส่วนขยาย `.docm` (`document.Save("MyDoc.docm");`) และฝังโมดูล VBA ที่จัดการ `cmdSubmit_Click` |

## โค้ดต้นฉบับครบชุด

ด้านล่างเป็นโปรแกรมเต็มรูปแบบที่คุณสามารถคัดลอกไปวางใน `Program.cs` และรันได้โดยไม่ต้องแก้ไข (ยกเว้นเส้นทางเอาต์พุต)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล

```
Document saved to C:\Temp\CommandButton.docx
```

การเปิดไฟล์ใน Word จะแสดงปุ่มที่มีข้อความ **Submit** การคลิกปุ่มจะทำให้เกิดพฤติกรรมเริ่มต้นของ ActiveX (กล่องข้อความบอกว่าไม่มีแมโครเชื่อมต่อ)

## สรุป

บทเรียนนี้ได้สาธิต **วิธีบันทึก docx** พร้อมฝัง **คอนโทรล ActiveX**, โดยเฉพาะ **add activex button** ที่ทำหน้าที่เป็นปุ่มคำสั่ง คุณได้เรียนรู้วิธี **สร้างเอกสาร Word อย่างโปรแกรมมิ่ง**, ตั้งค่าคุณสมบัติของปุ่ม, และบันทึกไฟล์เพื่อให้ผู้ใช้โต้ตอบได้

จากนี้คุณสามารถสำรวจต่อได้:

* เพิ่มแมโคร VBA เพื่อจัดการ `cmdSubmit_Click`  
* แทรกคอนโทรล ActiveX อื่น ๆ เช่น กล่องตรวจสอบหรือคอมโบบ็อกซ์  
* สร้างเอกสารหลายหน้าที่มีองค์ประกอบโต้ตอบหลายชิ้น  

ลองทดลองกับประเภทคอนโทรลและตัวเลือกการจัดวางต่าง ๆ เพื่อสร้างเทมเพลต Word ที่มีความโต้ตอบสูงและช่วยเร่งกระบวนการธุรกิจของคุณได้

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [how to recover docx – C# guide for corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [How to Save Word as Markdown – Complete C# Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}