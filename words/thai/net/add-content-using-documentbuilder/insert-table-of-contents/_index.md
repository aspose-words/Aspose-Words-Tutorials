---
title: แทรกสารบัญในเอกสาร Word
linktitle: แทรกสารบัญในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีแทรกสารบัญใน Word โดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อการนำทางเอกสารอย่างราบรื่น
weight: 10
url: /th/net/add-content-using-documentbuilder/insert-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกสารบัญในเอกสาร Word

## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีการเพิ่มสารบัญ (TOC) ลงในเอกสาร Word ของคุณอย่างมีประสิทธิภาพโดยใช้ Aspose.Words สำหรับ .NET ฟีเจอร์นี้มีความจำเป็นสำหรับการจัดระเบียบและการนำทางเอกสารยาวๆ การปรับปรุงการอ่าน และการให้ภาพรวมอย่างรวดเร็วของส่วนต่างๆ ของเอกสาร

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- ความเข้าใจพื้นฐานเกี่ยวกับ C# และ .NET framework
- ติดตั้ง Visual Studio ลงบนเครื่องของคุณแล้ว
-  Aspose.Words สำหรับไลบรารี .NET หากคุณยังไม่ได้ติดตั้ง คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/net/).

## นำเข้าเนมสเปซ

ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

มาแบ่งกระบวนการออกเป็นขั้นตอนที่ชัดเจน:

## ขั้นตอนที่ 1: เริ่มต้นใช้งานเอกสาร Aspose.Words และ DocumentBuilder

 ขั้นแรก ให้เริ่มต้น Aspose.Words ใหม่`Document` วัตถุและก`DocumentBuilder` ที่จะทำงานร่วมกับ:

```csharp
// เริ่มต้นใช้งาน Document และ DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: แทรกสารบัญ

 ตอนนี้แทรกสารบัญโดยใช้`InsertTableOfContents` วิธี:

```csharp
// แทรกสารบัญ
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## ขั้นตอนที่ 3: เริ่มเนื้อหาเอกสารบนหน้าใหม่

เพื่อให้แน่ใจว่ามีการจัดรูปแบบที่ถูกต้อง ให้เริ่มเนื้อหาเอกสารจริงบนหน้าใหม่:

```csharp
// แทรกตัวแบ่งหน้า
builder.InsertBreak(BreakType.PageBreak);
```

## ขั้นตอนที่ 4: จัดโครงสร้างเอกสารของคุณด้วยหัวเรื่อง

จัดระเบียบเนื้อหาเอกสารของคุณโดยใช้รูปแบบหัวเรื่องที่เหมาะสม:

```csharp
// ตั้งค่ารูปแบบหัวข้อ
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## ขั้นตอนที่ 5: อัปเดตและเติมข้อมูลในสารบัญ

อัปเดตสารบัญเพื่อแสดงโครงสร้างเอกสาร:

```csharp
// อัปเดตฟิลด์สารบัญ
doc.UpdateFields();
```

## ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารของคุณไปยังไดเร็กทอรีที่ระบุ:

```csharp
// บันทึกเอกสาร
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## บทสรุป

การเพิ่มสารบัญโดยใช้ Aspose.Words สำหรับ .NET เป็นเรื่องง่ายและช่วยเพิ่มการใช้งานเอกสารของคุณได้อย่างมาก หากทำตามขั้นตอนเหล่านี้ คุณจะสามารถจัดระเบียบและนำทางผ่านเอกสารที่ซับซ้อนได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งรูปลักษณ์ของสารบัญได้หรือไม่
ใช่ คุณสามารถปรับแต่งลักษณะที่ปรากฏและลักษณะการทำงานของสารบัญได้โดยใช้ Aspose.Words สำหรับ .NET API

### Aspose.Words รองรับการอัปเดตฟิลด์อัตโนมัติหรือไม่
ใช่ Aspose.Words ช่วยให้คุณอัปเดตฟิลด์ เช่น สารบัญ แบบไดนามิกตามการเปลี่ยนแปลงเอกสาร

### ฉันสามารถสร้างสารบัญหลายรายการในเอกสารเดียวได้หรือไม่
Aspose.Words รองรับการสร้างสารบัญหลายรายการที่มีการตั้งค่าต่างกันภายในเอกสารเดียว

### Aspose.Words เข้ากันได้กับ Microsoft Word เวอร์ชันต่างๆ หรือไม่
ใช่ Aspose.Words รับประกันความเข้ากันได้กับรูปแบบ Microsoft Word เวอร์ชันต่างๆ

### ฉันสามารถหาความช่วยเหลือและการสนับสนุนเพิ่มเติมสำหรับ Aspose.Words ได้จากที่ใด
 หากต้องการความช่วยเหลือเพิ่มเติม โปรดไปที่[ฟอรั่ม Aspose.Words](https://forum.aspose.com/c/words/8) หรือตรวจสอบ[เอกสารอย่างเป็นทางการ](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
