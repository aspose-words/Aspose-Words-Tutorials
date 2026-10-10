---
category: general
date: 2026-10-10
description: ตั้งค่าข้อความของปุ่มและเพิ่มปุ่ม ActiveX ใน C# ด้วย Aspose.Words เรียนรู้วิธีแทรกปุ่ม
  สร้างคอนโทรลปุ่ม และปรับแต่งคำบรรยายในเอกสาร Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: th
lastmod: 2026-10-10
og_description: ตั้งค่าข้อความของปุ่มและเพิ่มปุ่ม ActiveX ใน C# ด้วย Aspose.Words.
  ทำตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อแทรกปุ่ม, สร้างคอนโทรลปุ่ม, และปรับแต่งคำบรรยายของปุ่ม.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: ตั้งค่าข้อความปุ่มและเพิ่มปุ่ม ActiveX ใน C# – คู่มือฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: กำหนดข้อความปุ่มและเพิ่มปุ่ม ActiveX ใน C#
url: /th/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าข้อความปุ่มและเพิ่มปุ่ม ActiveX ใน C#

หากคุณต้องการ **ตั้งค่าข้อความปุ่ม** บนปุ่ม ActiveX ภายในเอกสาร Word คำแนะนำนี้จะแสดงให้คุณเห็นอย่างชัดเจนจนถึงขั้นตอนสุดท้าย หลังจากทำตามบทเรียนนี้แล้ว คุณจะสามารถ **แทรกปุ่ม**, สร้าง **การควบคุมปุ่ม**, และปรับแต่งคำบรรยายของมันได้ด้วยเพียงไม่กี่บรรทัดของโค้ด C#  

การทำงานกับคอนโทรล ActiveX เป็นเรื่องทั่วไปเมื่อคุณต้องการแบบฟอร์มแบบโต้ตอบใน Word—ไม่ว่าจะเป็นการสร้างเทมเพลตสัญญา, แบบสำรวจ, หรือเครื่องมือภายใน ตัวอย่างนี้ใช้ Aspose.Words for .NET ซึ่งเป็นไลบรารีที่ช่วยให้คุณจัดการไฟล์ Word ได้โดยไม่ต้องติดตั้ง Microsoft Office  

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า ติดตั้งแล้ว  
* Visual Studio 2022 (หรือ IDE ใดก็ได้ที่รองรับ C#)  
* ใบอนุญาต Aspose.Words for .NET (รุ่นทดลองฟรีใช้เพื่อการเรียนรู้ได้)  

คุณยังต้องอ้างอิงแพ็กเกจ NuGet `Aspose.Words` ด้วย:

```bash
dotnet add package Aspose.Words
```

## วิธีแทรกปุ่มลงในเอกสาร Word

ขั้นตอนแรกคือการสร้าง `Document` และ `DocumentBuilder` ใหม่ ตัว Builder เป็นจุดเริ่มต้นสำหรับการเพิ่มเนื้อหา รวมถึงคอนโทรล ActiveX  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**ทำไมเรื่องนี้สำคัญ:** `Document` แทนไฟล์ .docx ทั้งหมด, ในขณะที่ `DocumentBuilder` ให้เมธอดระดับสูงเช่น `InsertParagraph` และ `InsertFormField`. การเริ่มต้นด้วยเอกสารเปล่าช่วยให้ปุ่มปรากฏตรงตำแหน่งที่คุณต้องการ  

## สร้างคอนโทรลปุ่มด้วย Forms2OleControl

ตอนนี้เราจะสร้างคอนโทรลปุ่มจริง `Forms2OleControl` เป็นคลาสที่ Aspose.Words ใช้สำหรับออบเจ็กต์ ActiveX ทั้งหมด, และประเภท `COMMANDBUTTON` จะปรากฏเป็นปุ่มที่คลิกได้ใน Word  

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**คำอธิบาย:**  
* `InsertForms2OleControl` วางคอนโทรลที่พิกัดที่คุณระบุอย่างแม่นยำ.  
* ขนาดกำหนดเป็นหน่วย points (1 point = 1/72 นิ้ว). ปรับค่าตัวเลขเหล่านี้ให้เข้ากับการจัดวางของคุณ.  

## เพิ่มคอนโทรล ActiveX และตั้งชื่อให้เป็นเอกลักษณ์

ทุกออบเจ็กต์ ActiveX ควรมีชื่อที่แตกต่างกันเพื่อให้คุณอ้างอิงได้ในภายหลัง (เช่น เมื่อจัดการเหตุการณ์ใน VBA)  

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**เคล็ดลับ:** อย่าใช้ช่องว่างหรืออักขระพิเศษในชื่อ; Word จะถือชื่อเป็นตัวระบุในโมเดลฟอร์มภายใน  

## ตั้งค่าข้อความปุ่ม (caption) บนปุ่ม ActiveX

นี่คือจุดที่คีย์เวิร์ดหลัก **set button text** เข้ามามีบทบาท. คุณสมบัติ `Caption` กำหนดข้อความที่ผู้ใช้เห็นบนปุ่ม  

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

คุณสามารถเปลี่ยน caption ได้ตลอดเวลาก่อนบันทึกเอกสาร หากต้องการทำให้ UI รองรับหลายภาษาในภายหลัง เพียงเรียก `SetCaption` อีกครั้งพร้อมสตริงใหม่  

## บันทึกเอกสารและตรวจสอบผลลัพธ์

สุดท้ายให้เขียนเอกสารลงดิสก์ การเปิดไฟล์ใน Microsoft Word จะทำให้เห็นปุ่มพร้อม caption ที่กำหนดเอง  

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เมื่อคุณเปิด *ActiveXButton.docx* ใน Word, คุณจะเห็นปุ่มที่วางตามพิกัดที่ระบุ, มีข้อความ **Click Me**. การคลิกปุ่มจะเรียกพฤติกรรมปุ่มคำสั่งของ Word ตามค่าเริ่มต้น (ซึ่งคุณสามารถปรับแต่งต่อด้วย VBA)  

![Set button text example](https://example.com/activex-button.png){alt="ตัวอย่างการตั้งค่าข้อความปุ่ม"}

## เพิ่มปุ่ม ActiveX และจัดการเหตุการณ์ (ทางเลือก)

หากคุณต้องการให้ปุ่มทำงานตามการกระทำที่กำหนดเอง คุณสามารถเพิ่มแมโคร VBA ที่ตอบสนองต่อเหตุการณ์ `Click`. แมโครสามารถฉีดเข้าโดยโปรแกรมได้ แต่เกินขอบเขตของบทเรียนนี้ ส่วนสำคัญคือปุ่มได้ถูกสร้างและตั้งค่า caption แล้ว—พร้อมสำหรับการจัดการเหตุการณ์ใด ๆ ที่คุณเลือก  

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|---------|
| ปุ่มแสดงตำแหน่งไม่ตรง | พิกัดเป็นหน่วย points ไม่ใช่พิกเซล | แปลงค่าพิกเซลเป็น points (`points = pixels * 72 / DPI`) |
| Caption ไม่เปลี่ยนหลังบันทึก | `SetCaption` ถูกเรียกหลังจาก `Save` | ตั้งค่า caption **ก่อน** เรียก `doc.Save` เสมอ |
| คอนโทรลไม่แสดงใน Word รุ่นเก่า | บางรุ่น Word เก่าไม่มีการสนับสนุน ActiveX อย่างเต็มที่ | ทดสอบบนรุ่น Word ที่ต้องการ; พิจารณาใช้ `CheckBox` หรือ `DropDownList` เป็นทางเลือกสำรอง |
| คำเตือนใบอนุญาตในผลลัพธ์ | ใบอนุญาตทดลองหมดอายุ | ใช้ใบอนุญาต Aspose.Words ที่ถูกต้องโดยใช้ `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมเต็มที่คุณสามารถคัดลอก, วาง, และรันได้ รวมถึงคำสั่ง `using` ที่จำเป็นทั้งหมดและแสดงขั้นตอนการทำงานทั้งหมดตั้งแต่การสร้างเอกสารจนถึงการบันทึก  

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

รันโปรแกรมด้วย `dotnet run`. หลังจากทำงานเสร็จ เปิด *ActiveXButton.docx* เพื่อยืนยันว่าข้อความบนปุ่มคือ **Click Me**.  

## สรุปสิ่งที่คุณได้เรียนรู้

* คุณได้เรียนรู้วิธี **ตั้งค่าข้อความปุ่ม** บนปุ่ม ActiveX ด้วย Aspose.Words.  
* คุณได้เห็นขั้นตอนที่ชัดเจนในการ **แทรกปุ่ม**, **สร้างคอนโทรลปุ่ม**, และ **เพิ่มคอนโทรล ActiveX** ลงในเอกสาร Word.  
* ตอนนี้คุณมีโค้ดสแนปที่นำกลับมาใช้ใหม่ได้ ซึ่งสามารถปรับใช้กับโครงการอัตโนมัติ Word ที่ใช้แบบฟอร์มใดก็ได้  

## ขั้นตอนต่อไป

* สำรวจค่า `Forms2OleControlType` อื่น ๆ เช่น `CHECKBOX` หรือ `LISTBOX` เพื่อสร้างแบบฟอร์มที่หลากหลายยิ่งขึ้น.  
* ผสานปุ่มกับแมโคร VBA เพื่อทำการคำนวณหรือการตรวจสอบข้อมูล.  
* ใช้ API `FormField` ของ Aspose.Words เพื่ออ่านข้อมูลที่ผู้ใช้กรอกหลังจากเอกสารถูกเติมเต็มแล้ว.  

Feel free to experiment with the size, position, and caption to match your design requirements. If you run into any issues, the Aspose.Words documentation provides detailed references for every class used in this tutorial.  

ขอให้เขียนโค้ดอย่างสนุก!  

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบต่าง ๆ ในโครงการของคุณเอง  

- [สร้างเอกสาร Word ว่างด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)  
- [เพิ่มเงาให้ Shape ใน Word ด้วย Aspose.Words – ขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)  
- [เพิ่มเลขหน้าในส่วนท้ายของเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}