---
category: general
date: 2026-10-20
description: สร้างเอกสาร Word อย่างโปรแกรมเมติกและเพิ่มปุ่มคำสั่งโดยใช้ Aspose.Words
  เรียนรู้การแทรกคอนโทรล ActiveX และตั้งค่าข้อความบนปุ่ม.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: th
lastmod: 2026-10-20
og_description: สร้างเอกสาร Word ด้วยโปรแกรมและฝังปุ่มคำสั่ง ActiveX บทเรียนนี้อธิบายวิธีแทรกคอนโทรลและตั้งค่าคำบรรยายของมันด้วย
  Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: สร้างเอกสาร Word ด้วยโปรแกรม – เพิ่มปุ่ม ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: สร้างเอกสาร Word อย่างอัตโนมัติด้วยปุ่ม ActiveX
url: /th/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word อย่างโปรแกรมด้วยปุ่ม ActiveX

สร้างเอกสาร Word อย่างโปรแกรมด้วย Aspose.Words, จากนั้นเพิ่มปุ่มคำสั่งที่ผู้ใช้สามารถคลิกได้ คู่มือฉบับนี้จะพาคุณผ่านการแทรก ActiveX control, การกำหนดค่าคุณสมบัติของมัน, และการบันทึกผลลัพธ์เป็นไฟล์ **.docx**  

คุณจะได้เห็นตัวอย่างที่สมบูรณ์และสามารถรันได้ซึ่งคุณสามารถคัดลอกไปยังแอปพลิเคชันคอนโซลได้ เมื่อจบบทเรียนคุณจะสามารถสร้างไฟล์ Word ที่มีปุ่มคำสั่งทำงานเต็มรูปแบบ และคุณจะเข้าใจวิธี **add command button**, **add activex control**, **insert activex button**, และ **set button caption** โดยไม่ต้องออกจากโค้ด C# ของคุณ  

## ข้อกำหนดเบื้องต้น

* .NET 6.0 SDK หรือรุ่นที่ใหม่กว่า ติดตั้งแล้ว  
* Visual Studio 2022 (หรือ IDE ที่รองรับ C# ใดก็ได้)  
* ไฟล์ใบอนุญาต Aspose.Words for .NET (รุ่นทดลองฟรีทำงานได้กับตัวอย่างนี้)  
* ความคุ้นเคยพื้นฐานกับ C# และระบบโครงการ .NET  

ไม่จำเป็นต้องติดตั้งแพ็กเกจ NuGet เพิ่มเติมนอกจาก **Aspose.Words** เนื่องจากการสนับสนุน ActiveX ถูกสร้างไว้ในไลบรารีแล้ว  

## ขั้นตอนที่ 1: ตั้งค่าโครงการและเพิ่ม Aspose.Words

1. เปิดเทอร์มินัลหรือ Visual Studio แล้วสร้างโปรเจกต์คอนโซลใหม่:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. เพิ่มแพ็กเกจ Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (ทางเลือก) หากคุณมีไฟล์ใบอนุญาต ให้วางไว้ที่โฟลเดอร์รากของโปรเจกต์และเพิ่มบรรทัดต่อไปนี้ที่ส่วนเริ่มต้นของ `Program.cs` เพื่อหลีกเลี่ยงลายน้ำการประเมินผล:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## ขั้นตอนที่ 2: สร้างเอกสาร Word อย่างโปรแกรม – เริ่มต้นเอกสาร

การดำเนินการแรกคือ **create Word document programmatically**. คุณทำเช่นนี้โดยการสร้างอ็อบเจกต์ `Document` และ `DocumentBuilder` ที่ช่วยให้คุณแก้ไขเนื้อหาเอกสารได้  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` แสดงถึงไฟล์ทั้งหมด, ส่วน `DocumentBuilder` จะรักษาตำแหน่งเคอร์เซอร์ที่คุณสามารถย้ายไปยังตำแหน่งใดก็ได้ในเอกสาร การแยกนี้ทำให้ API สะอาดและทำให้คุณสามารถ **add activex control** ในภายหลังโดยไม่ต้องจัดการโครงสร้างระดับต่ำด้วยตนเอง  

## ขั้นตอนที่ 3: เพิ่มปุ่มคำสั่ง – การแทรก ActiveX control

ตอนนี้คุณจะ **add command button** โดยการแทรก ActiveX control ชนิด `OleControlType.CommandButton`. เมธอด `InsertForms2OleControl` ต้องการประเภทของคอนโทรล, ตำแหน่ง (`Point`), และขนาด (`Size`).  

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

การเรียกด้านบน **insert activex button** ลงในเอกสารที่พิกัดที่คุณระบุ พิกัดวัดเป็นจุด (1 pt ≈ 1/72 in). หากคุณต้องการปุ่มในย่อหน้าที่กำหนด, ให้ย้ายเคอร์เซอร์ของ builder ก่อน:  

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## ขั้นตอนที่ 4: ตั้งค่าคำบรรยายปุ่ม – ปรับแต่งข้อความของปุ่มคำสั่ง

ปุ่มที่ไม่มีป้ายกำกับจะทำให้สับสน, ดังนั้นคุณจะ **set button caption** ให้มีความหมาย `Caption` กำหนดข้อความที่แสดงบนปุ่ม, ส่วน `Name` ให้คอนโทรลมีตัวระบุแบบโปรแกรม  

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

หากคุณส่งออกเอกสารเป็นรูปแบบที่รองรับแมโคร (`.docm`) ค่า `OnClick` ต้องตรงกับชื่อแมโคร VBA. สำหรับ `.docx` ธรรมดา, คุณสมบัตินี้จะถูกเก็บไว้แต่ไม่ทำงาน, ซึ่งเพียงพอสำหรับสถานการณ์อัตโนมัติจำนวนมาก  

## ขั้นตอนที่ 5: บันทึกเอกสารที่มีปุ่ม ActiveX

หลังจากกำหนดค่าคอนโทรลแล้ว, คุณสามารถ **save the document**. เลือกไดเรกทอรีที่คุณมีสิทธิ์เขียน, และใช้ส่วนขยาย `.docx` เพื่อความเข้ากันได้สูงสุด.  

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

เมื่อคุณเปิดไฟล์ที่สร้างใน Microsoft Word, คุณจะเห็นปุ่มที่มีป้าย **Submit** ที่พิกัดที่ระบุ การคลิกปุ่มในไคลเอนต์เดสก์ท็อปจะพยายามเรียกแมโคร `SubmitForm` (หากมี).  

## ขั้นตอนที่ 6: ตรวจสอบผลลัพธ์และแก้ไขปัญหาทั่วไป

1. เปิดไฟล์ `ActiveXCommandButton.docx` ใน Microsoft Word.  
2. สลับไปที่ **Design Mode** (แท็บ Developer → **Design Mode**) เพื่อดูขอบของปุ่ม.  
3. หากปุ่มไม่ปรากฏ, ตรวจสอบว่าแท็บ **Developer** ถูกเปิดใช้งานและเวอร์ชัน Word ของคุณรองรับ ActiveX control.  
4. สำหรับไฟล์ที่รองรับแมโคร (`.docm`), ตรวจสอบให้แน่ใจว่าชื่อแมโครใน `OnClick` ตรงกับรูทีน VBA; มิฉะนั้น Word จะโชว์คำเตือนด้านความปลอดภัย.  

### เคล็ดลับพิเศษ

ActiveX control ใช้ได้เฉพาะบน Windows. หากคุณต้องการการโต้ตอบข้ามแพลตฟอร์ม, พิจารณาใช้ **Content Controls** (`RichTextContentControl`) แทนปุ่ม ActiveX.  

## โค้ดต้นฉบับเต็ม

ด้านล่างเป็นโปรแกรมที่สมบูรณ์พร้อมรัน. คัดลอกไปยัง `Program.cs` แล้วรันด้วย `dotnet run`.  



## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณเอง  

- [สร้างเอกสาร Word พร้อมปุ่ม ActiveX – คู่มือ C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [เพิ่มปุ่มคำสั่งลงในเอกสาร Word ด้วย Aspose.Words – คู่มือเต็ม](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [สร้างปุ่มในเอกสาร Word ด้วย Aspose.Words – ตัวอย่างโค้ดเต็ม](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}