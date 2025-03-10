---
title: ละเว้นกล่องข้อความ
linktitle: ละเว้นกล่องข้อความ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: รวมเอกสาร Word ด้วย Aspose.Words สำหรับ .NET โดยรับรองว่าการจัดรูปแบบกล่องข้อความจะคงอยู่ ปฏิบัติตามคำแนะนำทีละขั้นตอนนี้เพื่อการประมวลผลเอกสารที่ราบรื่น
weight: 10
url: /th/net/join-and-append-documents/ignore-text-boxes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ละเว้นกล่องข้อความ

## การแนะนำ

ยินดีต้อนรับสู่บทช่วยสอนโดยละเอียดเกี่ยวกับการใช้ Aspose.Words สำหรับ .NET เพื่อผสานเอกสาร Word โดยไม่สนใจกล่องข้อความ หากคุณต้องการปรับปรุงการประมวลผลเอกสารและให้แน่ใจว่าการจัดรูปแบบของกล่องข้อความได้รับการรักษาไว้ คุณมาถูกที่แล้ว มาเจาะลึกคู่มือทีละขั้นตอนนี้กันเลย

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

1.  Aspose.Words สำหรับ .NET: ดาวน์โหลด[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา .NET: Visual Studio หรือ IDE อื่นๆ ที่ต้องการ
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจเกี่ยวกับแนวคิดการเขียนโปรแกรมขั้นพื้นฐานใน C#

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นในโครงการของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Importing;
```

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

ขั้นแรก ตรวจสอบว่าโครงการของคุณได้รับการตั้งค่าอย่างถูกต้อง เปิด IDE ของคุณ สร้างโครงการใหม่ และติดตั้งไลบรารี Aspose.Words สำหรับ .NET ผ่านตัวจัดการแพ็กเกจ NuGet

### วิธีการติดตั้ง Aspose.Words

1. เปิดตัวจัดการแพ็คเกจ NuGet ใน IDE ของคุณ
2. ค้นหา "Aspose.Words"
3. คลิก "ติดตั้ง"

## ขั้นตอนที่ 2: กำหนดไดเรกทอรีเอกสาร

จากนั้นระบุไดเร็กทอรีที่เอกสารต้นทางและปลายทางของคุณตั้งอยู่

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` พร้อมเส้นทางจริงไปยังไดเร็กทอรีเอกสารของคุณ

## ขั้นตอนที่ 3: โหลดเอกสาร

ตอนนี้โหลดเอกสารทั้งต้นฉบับและปลายทางลงในโปรเจ็กต์ของคุณ

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## ขั้นตอนที่ 4: กำหนดค่าตัวเลือกการนำเข้า

 เพื่อให้แน่ใจว่าการจัดรูปแบบของกล่องข้อความได้รับการรักษาไว้ ให้ตั้งค่า`IgnoreTextBoxes` ตัวเลือกที่จะ`false`.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { IgnoreTextBoxes = false };
```

## ขั้นตอนที่ 5: เริ่มต้นตัวนำเข้าโหนด

 เริ่มต้นการใช้งาน`NodeImporter` การนำเข้าโหนดจากเอกสารต้นฉบับไปยังเอกสารปลายทาง

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting, importFormatOptions);
```

## ขั้นตอนที่ 6: นำเข้าย่อหน้าจากเอกสารต้นฉบับ

ดึงย่อหน้าทั้งหมดจากส่วนแรกของเอกสารต้นฉบับ

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
```

## ขั้นตอนที่ 7: ผนวกย่อหน้าที่นำเข้าไปยังเอกสารปลายทาง

วนซ้ำแต่ละย่อหน้าและผนวกเข้ากับเอกสารปลายทาง

```csharp
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, true);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## ขั้นตอนที่ 8: บันทึกเอกสารที่ผสาน

ขั้นสุดท้าย ให้บันทึกเอกสารที่ผสานด้วยชื่อใหม่เพื่อหลีกเลี่ยงการเขียนทับไฟล์ต้นฉบับ

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.IgnoreTextBoxes.docx");
```

## บทสรุป

คุณได้รวมเอกสาร Word สองฉบับสำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET โดยที่มั่นใจได้ว่ากล่องข้อความจะไม่ถูกละเว้นในระหว่างการนำเข้า กระบวนการนี้มีค่าอย่างยิ่งสำหรับการรักษาความสมบูรณ์ของการจัดรูปแบบของเอกสารของคุณ ไม่ว่าคุณจะจัดการกับรายงาน สัญญา หรือเอกสารประเภทอื่นใด Aspose.Words สำหรับ .NET จะทำให้กระบวนการนี้ราบรื่น

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
 Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังสำหรับการสร้าง จัดการ และแปลงเอกสาร Word ภายในแอปพลิเคชัน .NET[เรียนรู้เพิ่มเติม](https://reference.aspose.com/words/net/).

### ฉันสามารถทดลองใช้ Aspose.Words สำหรับ .NET ก่อนซื้อได้หรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร
คุณสามารถขอใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.aspose.com/temporary-license/).

### ฉันสามารถหาเอกสารรายละเอียดเพิ่มเติมได้ที่ไหน
 คุณสามารถค้นหาเอกสารประกอบฉบับสมบูรณ์ได้[ที่นี่](https://reference.aspose.com/words/net/).

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร
 หากต้องการความช่วยเหลือ โปรดไปที่ฟอรัม Aspose[ที่นี่](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
