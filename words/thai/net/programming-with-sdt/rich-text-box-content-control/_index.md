---
title: การควบคุมเนื้อหากล่องข้อความแบบ Rich Text
linktitle: การควบคุมเนื้อหากล่องข้อความแบบ Rich Text
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการเพิ่มและปรับแต่งตัวควบคุมเนื้อหากล่องข้อความที่มีรูปแบบ Rich Text ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนโดยละเอียดนี้
weight: 10
url: /th/net/programming-with-sdt/rich-text-box-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การควบคุมเนื้อหากล่องข้อความแบบ Rich Text

## การแนะนำ

ในโลกของการประมวลผลเอกสาร ความสามารถในการเพิ่มองค์ประกอบแบบโต้ตอบลงในเอกสาร Word ของคุณจะช่วยเพิ่มประสิทธิภาพการใช้งานได้อย่างมาก องค์ประกอบแบบโต้ตอบดังกล่าวคือตัวควบคุมเนื้อหา Rich Text Box การใช้ Aspose.Words สำหรับ .NET ช่วยให้คุณสามารถแทรกและปรับแต่ง Rich Text Box ในเอกสารของคุณได้อย่างง่ายดาย คู่มือนี้จะแนะนำคุณทีละขั้นตอนในกระบวนการ เพื่อให้คุณเข้าใจถึงวิธีการนำคุณลักษณะนี้ไปใช้ได้อย่างมีประสิทธิภาพ

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มบทช่วยสอนนี้ โปรดแน่ใจว่าคุณมีสิ่งต่อไปนี้:

1.  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Aspose.Words สำหรับ .NET แล้ว หากคุณยังไม่ได้ติดตั้ง คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/net/).

2. Visual Studio: สภาพแวดล้อมการพัฒนาเช่น Visual Studio จะช่วยคุณเขียนและดำเนินการโค้ด

3. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# และ .NET จะเป็นประโยชน์เนื่องจากเราจะเขียนโค้ดในภาษานี้

4. .NET Framework: ตรวจสอบให้แน่ใจว่าโครงการของคุณกำหนดเป้าหมายไปที่ .NET Framework เวอร์ชันที่เข้ากันได้

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณต้องรวมเนมสเปซที่จำเป็นไว้ในโปรเจ็กต์ C# ของคุณ ซึ่งจะทำให้คุณสามารถใช้คลาสและเมธอดที่ Aspose.Words จัดเตรียมไว้ได้

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Drawing;
```

ตอนนี้ เรามาดูขั้นตอนการเพิ่มตัวควบคุมเนื้อหากล่องข้อความที่มีรูปแบบ Rich Text ลงในเอกสาร Word ของคุณกัน

## ขั้นตอนที่ 1: กำหนดเส้นทางไปยังไดเรกทอรีเอกสารของคุณ

ขั้นแรก ให้ระบุเส้นทางที่คุณต้องการบันทึกเอกสาร นี่คือที่ที่ไฟล์ที่สร้างขึ้นจะถูกจัดเก็บไว้

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงที่คุณต้องการบันทึกเอกสารของคุณ

## ขั้นตอนที่ 2: สร้างเอกสารใหม่

 สร้างใหม่`Document` วัตถุซึ่งจะทำหน้าที่เป็นรากฐานให้เอกสาร Word ของคุณ

```csharp
Document doc = new Document();
```

นี่เป็นการเริ่มต้นเอกสาร Word เปล่าที่คุณจะเพิ่มเนื้อหาของคุณ

## ขั้นตอนที่ 3: สร้างแท็กเอกสารที่มีโครงสร้างสำหรับข้อความที่มีโครงสร้าง

 หากต้องการเพิ่มกล่องข้อความแบบ Rich Text คุณต้องสร้าง`StructuredDocumentTag` (SDT) ประเภท`RichText`.

```csharp
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RichText, MarkupLevel.Block);
```

 ที่นี่,`SdtType.RichText` ระบุว่า SDT จะเป็น Rich Text Box และ`MarkupLevel.Block` กำหนดพฤติกรรมของมันในเอกสาร

## ขั้นตอนที่ 4: เพิ่มเนื้อหาลงในกล่องข้อความแบบ Rich Text

 สร้าง`Paragraph` และก`Run` วัตถุที่จะเก็บเนื้อหาที่คุณต้องการแสดงในกล่องข้อความแบบ Rich Text ปรับแต่งข้อความและการจัดรูปแบบตามต้องการ

```csharp
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.Text = "Hello World";
run.Font.Color = Color.Green;
para.Runs.Add(run);
sdtRichText.ChildNodes.Add(para);
```

ในตัวอย่างนี้ เราจะเพิ่มย่อหน้าที่มีข้อความ "Hello World" พร้อมด้วยตัวอักษรสีเขียวลงในกล่องข้อความ Rich Text

## ขั้นตอนที่ 5: ผนวกกล่องข้อความ Rich Text ลงในเอกสาร

 เพิ่ม`StructuredDocumentTag` เข้าสู่เนื้อหาของเอกสาร

```csharp
doc.FirstSection.Body.AppendChild(sdtRichText);
```

ขั้นตอนนี้จะทำให้แน่ใจว่ากล่องข้อความแบบ Rich Text จะรวมอยู่ในเนื้อหาของเอกสาร

## ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารไปยังไดเร็กทอรีที่ระบุ

```csharp
doc.Save(dataDir + "WorkingWithSdt.RichTextBoxContentControl.docx");
```

ซึ่งจะสร้างเอกสาร Word ใหม่โดยใช้ตัวควบคุมเนื้อหากล่องข้อความแบบ Rich Text

## บทสรุป

การเพิ่มตัวควบคุมเนื้อหา Rich Text Box โดยใช้ Aspose.Words สำหรับ .NET เป็นกระบวนการตรงไปตรงมาที่ช่วยเพิ่มการโต้ตอบของเอกสาร Word ของคุณ โดยทำตามขั้นตอนที่ระบุไว้ในคู่มือนี้ คุณสามารถรวม Rich Text Box ลงในเอกสารและปรับแต่งให้เหมาะกับความต้องการของคุณได้อย่างง่ายดาย

## คำถามที่พบบ่อย

### แท็กเอกสารที่มีโครงสร้าง (SDT) คืออะไร?
แท็กเอกสารที่มีโครงสร้าง (SDT) เป็นประเภทของการควบคุมเนื้อหาในเอกสาร Word ที่ใช้สำหรับเพิ่มองค์ประกอบแบบโต้ตอบ เช่น กล่องข้อความและรายการแบบดรอปดาวน์

### ฉันสามารถปรับแต่งลักษณะของกล่องข้อความ Rich Text ได้หรือไม่
 ใช่ คุณสามารถปรับแต่งรูปลักษณ์โดยการแก้ไขคุณสมบัติของ`Run`วัตถุ เช่น สีแบบอักษร ขนาด และรูปแบบ

### ฉันสามารถใช้ SDT ประเภทอื่นๆ อะไรกับ Aspose.Words ได้บ้าง
นอกจาก Rich Text แล้ว Aspose.Words ยังรองรับ SDT ประเภทอื่นๆ เช่น Plain Text, Date Picker และ Drop-Down List

### ฉันจะเพิ่ม Rich Text Box หลายกล่องลงในเอกสารได้อย่างไร
 คุณสามารถสร้างได้หลาย`StructuredDocumentTag` และเพิ่มอินสแตนซ์ตามลำดับลงในเนื้อหาของเอกสาร

### ฉันสามารถใช้ Aspose.Words เพื่อแก้ไขเอกสารที่มีอยู่ได้หรือไม่
ใช่ Aspose.Words ช่วยให้คุณเปิด แก้ไข และบันทึกเอกสาร Word ที่มีอยู่ รวมถึงการเพิ่มหรืออัปเดต SDT

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
