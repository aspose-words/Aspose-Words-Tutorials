---
category: general
date: 2026-08-07
description: เรียนรู้วิธีเพิ่ม ActiveX Control ในเอกสาร Word ด้วย C# รวมถึงการเชื่อมโยงแมโครกับปุ่มและเพิ่มตัวอย่างปุ่มที่คลิกได้ใน
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: th
lastmod: 2026-08-07
og_description: วิธีเพิ่ม ActiveX Control ในเอกสาร Word ด้วย Aspose.Words. ทำตามคำแนะนำนี้เพื่อแทรกปุ่ม,
  เชื่อมโยงมาโครกับปุ่ม, และเพิ่มคำที่เป็นปุ่มคลิกได้.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: วิธีเพิ่ม ActiveX Control ใน Word – คอร์สสอน C# อย่างครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: วิธีเพิ่มคอนโทรล ActiveX ใน Word ด้วย Aspose.Words – คู่มือแบบขั้นตอนต่อขั้นตอน
url: /th/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่ม ActiveX control ใน Word ด้วย Aspose.Words

หากคุณต้องการ **วิธีเพิ่ม ActiveX control** ในไฟล์ Microsoft Word อย่างโปรแกรมมิ่ง คำแนะนำนี้จะแสดงขั้นตอนที่แน่นอนโดยใช้ Aspose.Words for .NET คุณจะได้เห็นวิธีแทรกปุ่มคำสั่ง ตั้งค่าคำบรรยายของมัน และ **เชื่อมโยงแมโครกับปุ่ม** เพื่อให้คอนโทรลทำงานเมื่อผู้ใช้คลิก สุดท้ายคุณจะได้ไฟล์ `.docm` ที่เปิดใช้งานแมโครซึ่งมีปุ่มทำงานเต็มรูปแบบ

การเพิ่มปุ่ม ActiveX เป็นความต้องการทั่วไปเมื่อสร้างเทมเพลตแบบโต้ตอบ เช่น ใบสมัครกู้เงิน แบบฟอร์มรับพนักงานใหม่ หรือรายงานอัตโนมัติ คู่มือนี้จะอธิบายโค้ดแต่ละบรรทัด ทำความเข้าใจ **ทำไม** แต่ละขั้นตอนถึงสำคัญ และครอบคลุมข้อผิดพลาดทั่วไปที่คุณอาจเจอ

## ข้อกำหนดเบื้องต้น

* .NET 6 (หรือ .NET Core 3.1 / .NET Framework 4.8) ติดตั้งแล้ว
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้องหรือคีย์ประเมินผลชั่วคราว
* Visual Studio 2022 (หรือ IDE ใด ๆ ที่รองรับ C#)
* ความคุ้นเคยพื้นฐานกับแมโครของ Word (VBA) หากคุณวางแผนจะเขียนแมโครที่ปุ่มจะเรียกใช้

> **Pro tip:** เมื่อคุณรันตัวอย่าง ให้บันทึกผลลัพธ์ลงในโฟลเดอร์ที่คุณมีสิทธิ์เขียน มิฉะนั้น `doc.Save` จะโยนข้อยกเว้น

## วิธีเพิ่ม ActiveX control ในเอกสาร Word โดยใช้ Aspose.Words

แกนหลักของวิธีแก้คือโปรแกรม C# สั้น ๆ ที่สร้างเอกสารใหม่ แทรกคอนโทรล ActiveX **CommandButton** และบันทึกไฟล์เป็นเอกสารที่เปิดใช้งานแมโคร (`.docm`) โค้ดเต็มพร้อมคัดลอก‑วาง

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### ทำไมแต่ละบรรทัดถึงสำคัญ

| Line | วัตถุประสงค์ |
|------|----------------|
| `Document doc = new Document();` | สร้างอินสแตนซ์ของแพ็กเกจ Word ใหม่ในหน่วยความจำ |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | ให้ API แบบ fluent สำหรับแทรกเนื้อหา รวมถึง ActiveX control |
| `InsertForms2OleControl` | เมธอดเดียวของ Aspose.Words ที่สร้าง ActiveX control; คุณระบุประเภทของคอนโทรล (`CommandButton`) และรูปทรงของมัน |
| `commandButton.Caption = "Click Me";` | ตั้งค่า **ข้อความบนปุ่มที่คลิกได้** ที่ผู้ใช้เห็น หากไม่มีคำบรรยายปุ่มจะว่างเปล่า |
| `commandButton.OnAction = "MyMacro";` | **เชื่อมโยงแมโครกับปุ่ม** – บอก Word ว่าแมโคร VBA ใดจะทำงานเมื่อคอนโทรลถูกคลิก |
| `doc.Save("CommandButton.docm");` | บันทึกเอกสารเป็นไฟล์ที่เปิดใช้งานแมโคร; ไฟล์ `.docx` ปกติจะลบคอนโทรลและแมโครออก |

> **Note:** พิกัด (ซ้าย, บน) วัดเป็นจุด (1 pt ≈ 1/72 in). ปรับค่าเหล่านี้เพื่อวางตำแหน่งปุ่มตามที่ต้องการบนหน้า

## วิธีเชื่อมโยงแมโครกับปุ่ม

คุณสมบัติ `OnAction` เชื่อมปุ่มกับแมโคร VBA ชื่อ `MyMacro` คุณยังต้องสร้างแมโครนั้นภายในไฟล์ Word ไม่ว่าจะทำด้วยตนเองหรือโดยการฉีดโค้ด VBA โปรแกรมmatically (Aspose.Words ไม่เขียนโค้ด VBA) นี่คือแมโครขั้นต่ำที่คุณสามารถเพิ่มได้โดยใช้ตัวแก้ไข **Developer → Visual Basic** ของ Word:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

เมื่อผู้ใช้เปิด `CommandButton.docm` และคลิกปุ่ม Word จะเรียก `MyMacro` และแสดงกล่องข้อความ หากการรักษาความปลอดภัยของแมโครตั้งค่าเป็น **Disable all macros without notification** ปุ่มจะปรากฏเป็นไม่ทำงาน แนะนำให้ผู้ใช้เปิดใช้งานแมโครสำหรับเอกสารหรือเซ็นแมโครด้วยใบรับรองที่เชื่อถือได้

### ข้อผิดพลาดทั่วไปเมื่อเชื่อมโยงแมโคร

* **การตั้งค่าความปลอดภัยของแมโคร** – หากเอกสารถูกเปิดบนเครื่องที่มีนโยบายความปลอดภัยเข้มงวด แมโครอาจถูกบล็อก ให้แนะนำวิธีลดระดับความปลอดภัยหรือเซ็นแมโคร
* **ความขัดแย้งของชื่อ** – ชื่อแมโครต้องไม่ซ้ำกันภายในโครงการ VBA ของเอกสาร; มิฉะนั้น Word จะแจ้งข้อผิดพลาด “duplicate procedure name”
* **Word 64‑bit กับ 32‑bit** – ActiveX control ทำงานเช่นเดียวกัน แต่ VBA editor อาจแสดงข้อความเตือนที่แตกต่างกันขึ้นอยู่กับเวอร์ชันของ Office

## วิธีเพิ่มข้อความบนปุ่มคลิกได้ในฟอร์ม Word

คุณสมบัติ `Caption` คือข้อความที่ผู้ใช้เห็นบนปุ่ม คุณสามารถปรับแต่งเพิ่มเติมได้:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

หากต้องการให้คำบรรยายเปลี่ยนแปลงตามข้อมูลที่ผู้ใช้ป้อน คุณสามารถเข้าถึงคอนโทรลผ่านโมเดลวัตถุของ Word ได้ในภายหลัง:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### กรณีขอบ: คำบรรยายยาว

Word จะตัดคำบรรยายที่ยาวเกินความกว้างของปุ่ม เพื่อหลีกเลี่ยงการตัด ให้เพิ่มค่า width ใน `InsertForms2OleControl` หรือย่อข้อความ การทดสอบกับภาษาต่าง ๆ (เช่น เยอรมันหรือญี่ปุ่น) แนะนำเนื่องจากความกว้างของอักขระแตกต่างกัน

## วิธีเพิ่มคำสั่งปุ่มสำหรับการทำงานอัตโนมัติของฟอร์ม

นอกจากคำบรรยายที่มองเห็นได้แล้ว แนวคิด **add command button word** ยังครอบคลุมชื่อโปรแกรมของคอนโทรล Aspose.Words ไม่ได้เปิดเผยคุณสมบัติ `Name` โดยตรงสำหรับ ActiveX control แต่คุณสามารถตั้งค่า `AltText` ซึ่ง Word จะถือว่าเป็นตัวระบุของคอนโทรล:

```csharp
commandButton.AltText = "SubmitButton";
```

ใน VBA คุณสามารถอ้างอิงปุ่มโดยค่า `AltText` ของมันได้:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

เทคนิคนี้มีประโยชน์เมื่อคุณมีหลายปุ่มและต้องการแยกแยะพวกมันในระดับโปรแกรม

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมครบถ้วนที่คุณสามารถคอมไพล์และรันเป็นแอปพลิเคชันคอนโซล รวมสไตล์เสริม การเชื่อมโยงแมโคร และบล็อกคอมเมนต์อธิบายแต่ละขั้นตอน

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** การเปิด `SubmitForm.docm` ใน Microsoft Word จะแสดงปุ่มที่มีกรอบสีน้ำเงินและป้าย *Submit Form* การคลิกปุ่มจะเรียกแมโคร VBA `SubmitMacro` (หากคุณได้เพิ่มแมโครลงในเอกสาร) ปุ่มสามารถย้าย ปรับขนาด หรือปรับสไตล์ต่อได้โดยใช้วัตถุ `Forms2OleControl` เดียวกัน

## ทดสอบวิธีแก้

1. สร้างและรันแอปคอนโซล C#  
2. เปิด `SubmitForm.docm` ที่สร้างขึ้นใน Word  
3. หากมีการแจ้ง ให้เปิดใช้งานแมโคร  
4. คลิกปุ่ม *Submit Form* – คุณควรเห็นกล่องข้อความที่กำหนดใน `SubmitMacro`

หากปุ่มปรากฏแต่ไม่ทำอะไร ให้ตรวจสอบว่าชื่อแมโครตรงกันอย่างแม่นยำ (`SubmitMacro`) และการตั้งค่าความปลอดภัยของแมโครไม่ได้บล็อกการทำงาน

## คำถามที่พบบ่อย

| คำถาม | คำตอบ |
|----------|--------|
| *ฉันสามารถเพิ่ม ActiveX button มากกว่าหนึ่งปุ่มได้หรือไม่?* | ใช่. เรียก `InsertForms2OleControl` หลายครั้งโดยใช้พิกัดที่ต่างกัน ใช้ค่า `OnAction` และ `AltText` ที่แตกต่างกันเพื่อแยกแยะ |
| *ActiveX control สามารถมองเห็นได้ใน Word Online หรือไม่?* | ไม่ |

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณเอง

- [เพิ่มเนื้อหาโดยใช้ Document Builder ใน Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow Tutorial – เพิ่มเงาให้ Shape ใน Word ด้วย C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [เพิ่ม Section ใหม่ในเอกสาร Word | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}