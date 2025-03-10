---
title: สร้างส่วนหัวส่วนท้าย
linktitle: สร้างส่วนหัวส่วนท้าย
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการเพิ่มและปรับแต่งส่วนหัวและส่วนท้ายในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET คำแนะนำทีละขั้นตอนนี้จะช่วยให้มั่นใจว่าเอกสารจะได้รับการจัดรูปแบบอย่างมืออาชีพ
weight: 10
url: /th/net/working-with-headers-and-footers/create-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างส่วนหัวส่วนท้าย

## การแนะนำ

การเพิ่มส่วนหัวและส่วนท้ายในเอกสารของคุณจะช่วยเพิ่มความเป็นมืออาชีพและความสามารถในการอ่านได้ ด้วย Aspose.Words สำหรับ .NET คุณสามารถสร้างและปรับแต่งส่วนหัวและส่วนท้ายสำหรับเอกสาร Word ของคุณได้อย่างง่ายดาย ในบทช่วยสอนนี้ เราจะแนะนำคุณทีละขั้นตอนเพื่อให้แน่ใจว่าคุณสามารถนำคุณลักษณะเหล่านี้ไปใช้ได้อย่างราบรื่น

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.Words สำหรับ .NET: ดาวน์โหลดและติดตั้งจาก[ลิงค์ดาวน์โหลด](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา เช่น Visual Studio เพื่อเขียนและรันโค้ดของคุณ
- ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจเกี่ยวกับ C# และ .NET framework
- เอกสารตัวอย่าง: เอกสารตัวอย่างที่จะใช้ใส่ส่วนหัวและส่วนท้าย หรือสร้างส่วนท้ายใหม่ตามที่แสดงในบทช่วยสอน

## นำเข้าเนมสเปซ

ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการ Aspose.Words

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอกสาร

กำหนดไดเรกทอรีที่จะบันทึกเอกสารของคุณ ซึ่งจะช่วยให้จัดการเส้นทางได้อย่างมีประสิทธิภาพ

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## ขั้นตอนที่ 2: สร้างเอกสารใหม่

 สร้างเอกสารใหม่และ`DocumentBuilder`เพื่ออำนวยความสะดวกในการเพิ่มเนื้อหา

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 3: กำหนดค่าการตั้งค่าหน้า

ตั้งค่าหน้า รวมทั้งกำหนดว่าหน้าแรกจะมีส่วนหัว/ส่วนท้ายที่แตกต่างกันหรือไม่

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## ขั้นตอนที่ 4: เพิ่มส่วนหัวลงในหน้าแรก

ย้ายไปที่ส่วนหัวสำหรับหน้าแรกและกำหนดค่าข้อความส่วนหัว

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## ขั้นตอนที่ 5: เพิ่มส่วนหัวหลัก

ย้ายไปที่ส่วนหัวหลักและแทรกภาพและข้อความ

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// แทรกภาพลงในส่วนหัว
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## ขั้นตอนที่ 6: เพิ่มส่วนท้ายหลัก

ย้ายไปที่ส่วนท้ายหลักและสร้างตารางเพื่อจัดรูปแบบเนื้อหาส่วนท้าย

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// เพิ่มการใส่หมายเลขหน้า
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## ขั้นตอนที่ 7: เพิ่มเนื้อหาและการแบ่งหน้า

ย้ายไปที่ท้ายเอกสาร เพิ่มตัวแบ่งหน้า และสร้างส่วนใหม่ที่มีการตั้งค่าหน้าที่แตกต่างกัน

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## ขั้นตอนที่ 8: คัดลอกส่วนหัวและส่วนท้ายจากส่วนก่อนหน้า

หากคุณต้องการนำส่วนหัวและส่วนท้ายจากส่วนก่อนหน้ามาใช้ซ้ำ ให้คัดลอกและปรับเปลี่ยนตามความจำเป็น

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## บทสรุป

หากทำตามขั้นตอนเหล่านี้ คุณสามารถเพิ่มและปรับแต่งส่วนหัวและส่วนท้ายในเอกสาร Word ของคุณได้อย่างมีประสิทธิภาพโดยใช้ Aspose.Words สำหรับ .NET ซึ่งจะช่วยปรับปรุงรูปลักษณ์และความเป็นมืออาชีพของเอกสารของคุณ ทำให้อ่านง่ายและน่าสนใจยิ่งขึ้น

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?

Aspose.Words สำหรับ .NET เป็นไลบรารีที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และแปลงเอกสาร Word โดยใช้โปรแกรมภายในแอปพลิเคชัน .NET ได้

### ฉันสามารถเพิ่มรูปภาพลงในส่วนหัวหรือส่วนท้ายได้หรือไม่?

 ใช่ คุณสามารถเพิ่มรูปภาพลงในส่วนหัวหรือส่วนท้ายได้อย่างง่ายดายโดยใช้`DocumentBuilder.InsertImage` วิธี.

### ฉันจะตั้งค่าส่วนหัวและส่วนท้ายที่แตกต่างกันสำหรับหน้าแรกได้อย่างไร

 คุณสามารถตั้งค่าส่วนหัวและส่วนท้ายที่แตกต่างกันสำหรับหน้าแรกได้โดยใช้`DifferentFirstPageHeaderFooter` ทรัพย์สินของ`PageSetup` ระดับ.

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words ได้จากที่ใด

 คุณสามารถค้นหาเอกสารประกอบที่ครอบคลุมได้ที่[หน้าเอกสาร API ของ Aspose.Words](https://reference.aspose.com/words/net/).

### มีการรองรับ Aspose.Words หรือไม่

 ใช่ Aspose เสนอการสนับสนุนผ่าน[ฟอรั่มสนับสนุน](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
