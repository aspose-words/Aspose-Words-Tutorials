---
title: ย้ายไปที่ส่วนหัว ส่วนท้าย ในเอกสาร Word
linktitle: ย้ายไปที่ส่วนหัว ส่วนท้าย ในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการย้ายส่วนหัวและส่วนท้ายในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคำแนะนำทีละขั้นตอนของเรา พัฒนาทักษะการสร้างเอกสารของคุณ
weight: 10
url: /th/net/add-content-using-documentbuilder/move-to-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ย้ายไปที่ส่วนหัว ส่วนท้าย ในเอกสาร Word

## การแนะนำ

เมื่อต้องสร้างและจัดการเอกสาร Word ด้วยโปรแกรม Aspose.Words สำหรับ .NET เป็นเครื่องมืออันทรงพลังที่ช่วยประหยัดเวลาและความพยายามของคุณได้มาก ในบทความนี้ เราจะมาสำรวจวิธีการย้ายส่วนหัวและส่วนท้ายภายในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ฟีเจอร์นี้มีความจำเป็นเมื่อคุณต้องการเพิ่มเนื้อหาเฉพาะลงในส่วนหัวหรือส่วนท้ายของเอกสาร ไม่ว่าคุณจะกำลังสร้างรายงาน ใบแจ้งหนี้ หรือเอกสารใดๆ ที่ต้องการความเป็นมืออาชีพ การทำความเข้าใจวิธีการจัดการส่วนหัวและส่วนท้ายถือเป็นสิ่งสำคัญ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกโค้ด เรามาตรวจสอบกันก่อนว่าคุณได้ตั้งค่าทุกอย่างเรียบร้อยแล้ว:

1. **Aspose.Words for .NET** : ตรวจสอบว่าคุณมีไลบรารี Aspose.Words สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/).
2. **Development Environment**คุณต้องมีสภาพแวดล้อมการพัฒนาเช่น Visual Studio
3. **Basic Knowledge of C#**:การเข้าใจพื้นฐานของการเขียนโปรแกรม C# จะช่วยให้คุณทำตามได้

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็น ขั้นตอนนี้มีความสำคัญสำหรับการเข้าถึงคลาสและวิธีการที่ Aspose.Words จัดทำไว้สำหรับ .NET

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System;
```

มาแบ่งขั้นตอนต่างๆ ออกเป็นขั้นตอนง่ายๆ กัน แต่ละขั้นตอนจะได้รับการอธิบายอย่างชัดเจนเพื่อช่วยให้คุณเข้าใจว่าโค้ดทำงานอย่างไรและทำไม

## ขั้นตอนที่ 1: เริ่มต้นเอกสาร

ขั้นตอนแรกคือการเริ่มต้นเอกสารใหม่และวัตถุ DocumentBuilder คลาส DocumentBuilder ช่วยให้คุณสามารถสร้างและจัดการเอกสารได้

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 ในขั้นตอนนี้ คุณจะสร้างอินสแตนซ์ใหม่ของ`Document` ชั้นเรียนและ`DocumentBuilder` ชั้นเรียน.`dataDir` ตัวแปรใช้เพื่อระบุไดเร็กทอรีที่คุณต้องการบันทึกเอกสาร

## ขั้นตอนที่ 2: กำหนดค่าการตั้งค่าหน้า

ต่อไป เราจะต้องระบุว่าส่วนหัวและส่วนท้ายควรจะแตกต่างกันสำหรับหน้าแรก หน้าคู่ และหน้าคี่

```csharp
//ระบุว่าเราต้องการให้ส่วนหัวและส่วนท้ายแตกต่างกันสำหรับหน้าแรก หน้าคู่ และหน้าคี่
builder.PageSetup.DifferentFirstPageHeaderFooter = true;
builder.PageSetup.OddAndEvenPagesHeaderFooter = true;
```

การตั้งค่าเหล่านี้ทำให้แน่ใจว่าคุณมีส่วนหัวและส่วนท้ายที่ไม่ซ้ำกันสำหรับหน้าประเภทต่างๆ

## ขั้นตอนที่ 3: ย้ายไปที่ส่วนหัว/ส่วนท้ายและเพิ่มเนื้อหา

ทีนี้มาดูส่วนหัวและส่วนท้ายและเพิ่มเนื้อหากันบ้าง

```csharp
// สร้างส่วนหัว
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.Write("Header for the first page");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderEven);
builder.Write("Header for even pages");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);
builder.Write("Header for all other pages");
```

 ในขั้นตอนนี้เราใช้`MoveToHeaderFooter` วิธีการนำทางไปยังส่วนหัวหรือส่วนท้ายที่ต้องการ`Write` จากนั้นใช้วิธีการเพิ่มข้อความลงในส่วนเหล่านี้

## ขั้นตอนที่ 4: เพิ่มเนื้อหาลงในเนื้อหาของเอกสาร

เพื่อแสดงส่วนหัวและส่วนท้าย ให้เราเพิ่มเนื้อหาลงในเนื้อหาของเอกสารและสร้างหน้าสองสามหน้า

```csharp
// สร้างสองหน้าในเอกสาร
builder.MoveToSection(0);
builder.Writeln("Page1");
builder.InsertBreak(BreakType.PageBreak);
builder.Writeln("Page2");
```

ที่นี่เราเพิ่มข้อความลงในเอกสารและแทรกตัวแบ่งหน้าเพื่อสร้างหน้าที่สอง

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารไปยังไดเร็กทอรีที่ระบุ

```csharp
doc.Save(dataDir + "AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx");
```

บรรทัดโค้ดนี้จะบันทึกเอกสารด้วยชื่อ "AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx" ในไดเร็กทอรีที่ระบุ

## บทสรุป

 หากทำตามขั้นตอนเหล่านี้ คุณจะสามารถจัดการส่วนหัวและส่วนท้ายในเอกสาร Word ได้อย่างง่ายดายโดยใช้ Aspose.Words สำหรับ .NET บทช่วยสอนนี้ครอบคลุมพื้นฐาน แต่ Aspose.Words นำเสนอฟังก์ชันต่างๆ มากมายสำหรับการจัดการเอกสารที่ซับซ้อนมากขึ้น อย่าลังเลที่จะลองดู[เอกสารประกอบ](https://reference.aspose.com/words/net/) สำหรับคุณสมบัติขั้นสูงเพิ่มเติม

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และแปลงเอกสาร Word ด้วยโปรแกรมโดยใช้ C#

### ฉันสามารถเพิ่มรูปภาพลงในส่วนหัวและส่วนท้ายได้หรือไม่
 ใช่ คุณสามารถเพิ่มรูปภาพลงในส่วนหัวและส่วนท้ายได้โดยใช้`DocumentBuilder.InsertImage` วิธี.

### เป็นไปได้ไหมที่จะมีส่วนหัวและส่วนท้ายที่ต่างกันสำหรับแต่ละส่วน?
 แน่นอน! คุณสามารถมีส่วนหัวและส่วนท้ายที่ไม่ซ้ำใครสำหรับแต่ละส่วนได้โดยการตั้งค่าที่แตกต่างกัน`HeaderFooterType` สำหรับแต่ละส่วน

### ฉันจะสร้างเค้าโครงที่ซับซ้อนยิ่งขึ้นในส่วนหัวและส่วนท้ายได้อย่างไร
คุณสามารถใช้ตาราง รูปภาพ และตัวเลือกการจัดรูปแบบต่างๆ ที่ให้มาโดย Aspose.Words เพื่อสร้างเค้าโครงที่ซับซ้อนได้

### ฉันสามารถหาตัวอย่างและบทช่วยสอนเพิ่มเติมได้ที่ไหน
 ตรวจสอบออก[เอกสารประกอบ](https://reference.aspose.com/words/net/) และ[ฟอรั่มสนับสนุน](https://forum.aspose.com/c/words/8) สำหรับตัวอย่างเพิ่มเติมและการสนับสนุนจากชุมชน

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
