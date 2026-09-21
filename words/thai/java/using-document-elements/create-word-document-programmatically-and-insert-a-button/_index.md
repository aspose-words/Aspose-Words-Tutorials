---
category: general
date: 2026-09-21
description: สร้างเอกสาร Word อย่างอัตโนมัติและเรียนรู้วิธีใช้ปุ่มบันทึกเอกสาร Word,
  แทรกปุ่มคำสั่ง Word, และตั้งค่าคำบรรยายของปุ่มคำสั่งโดยใช้ DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: th
lastmod: 2026-09-21
og_description: สร้างเอกสาร Word อย่างอัตโนมัติด้วย Aspose.Words เรียนรู้วิธีบันทึกเอกสาร
  Word ด้วยปุ่ม, แทรกปุ่มคำสั่ง, ตั้งค่าคำบรรยายของปุ่มคำสั่ง, และใช้ DocumentBuilder
  สำหรับฟอร์มโต้ตอบ.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: สร้างเอกสาร Word โดยอัตโนมัติและเพิ่มปุ่ม
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: สร้างเอกสาร Word ด้วยโปรแกรมและแทรกปุ่ม
url: /th/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word แบบโปรแกรมและแทรกปุ่ม

หากคุณต้องการ **สร้างเอกสาร Word แบบโปรแกรม** Aspose.Words มี API ที่ใช้งานง่ายที่ให้คุณเพิ่มคอนโทรลแบบโต้ตอบ เช่น CommandButton. บทเรียนนี้ยังอธิบาย **วิธีใช้ DocumentBuilder**, **วิธีบันทึกปุ่มเอกสาร Word**, และ **วิธีตั้งค่าคำบรรยายของปุ่มคำสั่ง** เพื่อให้ปุ่มปรากฏตามที่คุณคาดหวังในไฟล์ .docx

คุณจะได้เรียนรู้ว่า:

* เริ่มต้นเอกสารเปล่าด้วย `Document`.
* ทำงานกับ `DocumentBuilder` เพื่อแก้ไขเอกสาร.
* แทรก **CommandButton** (`insert command button word`).
* ตั้งค่าชื่อและคำบรรยายที่มองเห็นของปุ่ม (`set command button caption`).
* บันทึกผลลัพธ์ลงดิสก์ (`save word document button`).

ขั้นตอนเหล่านี้เขียนสำหรับนักพัฒนา .NET ที่ใช้ C# และ Aspose.Words for .NET รุ่นล่าสุด (v24.10). ไม่จำเป็นต้องใช้แพ็กเกจ NuGet เพิ่มเติมนอกจาก Aspose.Words.

---

## สิ่งที่คุณต้องเตรียมก่อนเริ่ม

| สิ่งที่ต้องมี | เหตุผล |
|--------------|--------|
| Visual Studio 2022 (หรือ IDE C# ใดก็ได้) | เพื่อคอมไพล์และรันโค้ดตัวอย่าง. |
| .NET 6.0 SDK หรือใหม่กว่า | ให้ runtime สำหรับตัวอย่าง. |
| Aspose.Words for .NET (v24.10 หรือใหม่กว่า) | ไลบรารีที่ทำให้คุณ **สร้างเอกสาร Word แบบโปรแกรม** และจัดการคอนโทรลฟอร์ม. |
| ความคุ้นเคยพื้นฐานกับ C# และแนวคิด OOP | จำเป็นสำหรับการเข้าใจการไหลของโค้ด. |

คุณสามารถติดตั้ง Aspose.Words ผ่าน NuGet:

```bash
dotnet add package Aspose.Words
```

---

## สร้างเอกสาร Word แบบโปรแกรม

ขั้นตอนแรกคือการสร้างอินสแตนซ์ของ `Document` ที่ว่างเปล่า. อ็อบเจ็กต์นี้แทนไฟล์ Word ทั้งหมดในหน่วยความจำ.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

การสร้างเอกสารแบบโปรแกรมให้คุณมีผืนผ้าใบที่สะอาดซึ่งคุณสามารถเพิ่มย่อหน้า ตาราง หรือคอนโทรลแบบโต้ตอบได้.

---

## วิธีใช้ DocumentBuilder

`DocumentBuilder` เป็นคลาสหลักสำหรับแก้ไข `Document`. มันมีเมธอดสำหรับแทรกข้อความ รูปภาพ และฟิลด์ฟอร์ม. ในบทเรียนนี้เราใช้เพื่อวาง CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder จะรักษา cursor ภายในที่ชี้ไปยังตำแหน่งการแทรกปัจจุบัน. โดยค่าเริ่มต้นมันเริ่มที่จุดเริ่มต้นของส่วนแรก ซึ่งเหมาะกับตัวอย่างของเรา.

---

## แทรก CommandButton ใน Word

Aspose.Words ถือว่า CommandButton เป็นคอนโทรล ActiveX. เมธอด `InsertForms2OleControl` สร้างคอนโทรล OLE ทั่วไปที่เราจะกำหนดให้เป็นปุ่มต่อไป.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

ในขั้นตอนนี้คอนโทรลมีอยู่ในเอกสารแล้ว แต่ยังไม่มีการแสดงผลภาพจนกว่าเราจะกำหนดประเภทของมัน.

---

## ตั้งค่าคำบรรยายของปุ่มคำสั่ง

ตอนนี้เราบอกคอนโทรล OLE ว่ามันควรทำงานเหมือน CommandButton และให้ป้ายชื่อที่เป็นมิตร.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

การตั้งค่า **command button caption** เป็นสิ่งสำคัญเพราะ Word จะแสดงข้อความนี้บนพื้นผิวของปุ่ม. หากคุณละเว้น `SetCaption` ปุ่มจะปรากฏด้วยป้ายชื่อทั่วไป.

---

## บันทึกปุ่มเอกสาร Word

สุดท้ายบันทึกเอกสารลงดิสก์. เมธอด `Save` จะเขียนแพ็กเกจ Word ทั้งหมด รวมถึงปุ่มที่แทรกใหม่ ไปยังไฟล์ .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

ไฟล์ `CommandButton.docx` ตอนนี้มีปุ่มทำงานเต็มรูปแบบที่มีป้าย **Submit**. เมื่อผู้ใช้เปิดไฟล์ใน Microsoft Word และคลิกปุ่ม การกระทำเริ่มต้น (ซึ่งคุณสามารถผูกต่อด้วย VBA ในภายหลัง) จะถูกเรียกใช้.

---

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก วาง และรันได้. มันแสดงขั้นตอนการทำงานทั้งหมดตั้งแต่การสร้างเอกสารจนถึงการบันทึกปุ่ม.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected result**

* ไฟล์ชื่อ `CommandButton.docx` ที่อยู่ในพาธที่คุณระบุ.
* การเปิดไฟล์ใน Microsoft Word จะแสดงปุ่ม **Submit** เพียงหนึ่งปุ่มบนหน้าแรก.
* คุณสามารถเลือก ปรับขนาด หรือเชื่อมโยงปุ่มกับมาโครจากแท็บ **Developer** ของ Word.

---

## คำถามทั่วไปและการจัดการกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| *ถ้าฉันต้องการปุ่มมากกว่าหนึ่งปุ่ม?* | ทำซ้ำขั้นตอน 3–6 ด้วยชื่อและคำบรรยายที่แตกต่างกัน. แต่ละปุ่มต้องมีค่า `SetName` ที่ไม่ซ้ำกัน. |
| *ฉันสามารถตั้งขนาดปุ่มได้หรือไม่?* | ได้. หลังจากแทรกคอนโทรลแล้ว คุณสามารถแก้ไขคุณสมบัติ `Width` และ `Height` ผ่านอ็อบเจ็กต์ `OleFormat`. |
| *ปุ่มจะทำงานบนทุกเวอร์ชันของ Word หรือไม่?* | คอนโทรล ActiveX รองรับในเวอร์ชันเดสก์ท็อปของ Word (Windows). พวกมันไม่แสดงผลใน Word Online หรือบน macOS. |
| *จะเพิ่มตัวจัดการคลิกได้อย่างไร?* | คุณต้องเขียนโค้ด VBA ที่อ้างอิงชื่อปุ่ม (`btnSubmit`). มาโคร VBA สามารถฝังได้โดยใช้ `doc.VbaProject`. |
| *ถ้าฉันต้องการแทรกปุ่มภายในเซลล์ตาราง?* | ย้าย cursor ของ builder ไปยังเซลล์ที่ต้องการ (`builder.MoveTo(cell.FirstParagraph)`) ก่อนเรียก `InsertForms2OleControl`. |

---

## เคล็ดลับระดับมืออาชีพ

* **เคล็ดลับ:** ควรตั้งชื่อที่มีความหมายเสมอด้วย `SetName`. จะทำให้การอัตโนมัติ VBA ง่ายขึ้นและดีบักง่ายกว่า.
* **ระวัง:** ลืมเรียก `SetControlType`. หากไม่เรียก OLE object จะปรากฏเป็นตัวแทนทั่วไปแทนปุ่มที่คลิกได้.
* **เคล็ดลับด้านประสิทธิภาพ:** หากคุณสร้างเอกสารหลายไฟล์ในลูป ให้ใช้ `DocumentBuilder` ตัวเดียวและเรียก `builder.MoveToDocumentEnd()` ก่อนการแทรกแต่ละครั้งเพื่อหลีกเลี่ยงการรีเซ็ต cursor ที่ไม่จำเป็น.

---

## ขั้นตอนต่อไป

ตอนนี้คุณรู้วิธี **สร้างเอกสาร Word แบบโปรแกรม**, **แทรก CommandButton ใน Word**, **ตั้งค่าคำบรรยายของปุ่มคำสั่ง**, และ **บันทึกปุ่มเอกสาร Word**, คุณสามารถสำรวจสถานการณ์ขั้นสูงเพิ่มเติมได้:

* เพิ่มคอนโทรล **TextFormField** สำหรับการป้อนข้อมูลของผู้ใช้.
* ผสานปุ่มกับฟิลด์ **MacroButton** เพื่อเรียกใช้ VBA โดยตรง.
* ใช้ **DocumentBuilder.InsertImage** เพื่อวางไอคอนบนปุ่มของคุณ.
* รวมกับ ASP.NET เพื่อสร้างฟอร์ม Word บน

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลรวมตัวอย่างโค้ดทำงานเต็มที่พร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณ.

- [สร้างเอกสาร Word ใหม่](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [สร้างเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [แทรกรูปภาพ Inline ในเอกสาร Word ด้วย Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}