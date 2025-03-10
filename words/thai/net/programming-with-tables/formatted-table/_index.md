---
title: ตารางที่จัดรูปแบบ
linktitle: ตารางที่จัดรูปแบบ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการสร้างและจัดรูปแบบตารางในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนโดยละเอียดนี้
weight: 10
url: /th/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตารางที่จัดรูปแบบ

## การแนะนำ

การสร้างและจัดรูปแบบตารางในเอกสาร Word ด้วยโปรแกรมอาจดูเหมือนเป็นงานที่น่าปวดหัว แต่ด้วย Aspose.Words สำหรับ .NET จะทำให้ทุกอย่างเป็นเรื่องง่ายและจัดการได้ ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับวิธีสร้างตารางที่มีรูปแบบในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เราจะครอบคลุมทุกอย่างตั้งแต่การตั้งค่าสภาพแวดล้อมของคุณไปจนถึงการบันทึกเอกสารด้วยตารางที่มีรูปแบบสวยงาม

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเจาะลึกโค้ด เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

1. Aspose.Words สำหรับไลบรารี .NET: ดาวน์โหลดจาก[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: IDE เช่น Visual Studio
3. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework ไว้ในเครื่องของคุณแล้ว

## นำเข้าเนมสเปซ

ก่อนที่จะเขียนโค้ดจริง คุณต้องนำเข้าเนมสเปซที่จำเป็น:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสารของคุณ

ขั้นแรกคุณต้องกำหนดเส้นทางที่จะบันทึกเอกสารของคุณ

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงที่คุณต้องการบันทึกเอกสาร

## ขั้นตอนที่ 2: เริ่มต้นใช้งาน Document และ DocumentBuilder

ตอนนี้ ให้เริ่มต้นเอกสารใหม่และอ็อบเจ็กต์ DocumentBuilder

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 การ`DocumentBuilder` เป็นคลาสตัวช่วยที่ทำให้กระบวนการสร้างเอกสารง่ายขึ้น

## ขั้นตอนที่ 3: เริ่มต้นตาราง

 ต่อไปเริ่มสร้างตารางโดยใช้`StartTable` วิธี.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

การแทรกเซลล์เป็นสิ่งจำเป็นในการเริ่มตาราง

## ขั้นตอนที่ 4: ใช้การจัดรูปแบบทั้งตาราง

คุณสามารถใช้การจัดรูปแบบที่ส่งผลต่อตารางทั้งหมดได้ ตัวอย่างเช่น การตั้งค่าการเยื้องด้านซ้าย:

```csharp
table.LeftIndent = 20.0;
```

## ขั้นตอนที่ 5: จัดรูปแบบแถวส่วนหัว

ตั้งค่าความสูง การจัดตำแหน่ง และคุณสมบัติอื่นๆ ให้กับแถวส่วนหัว

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

ในขั้นตอนนี้ เราทำให้แถวส่วนหัวโดดเด่นโดยการตั้งค่าสีพื้นหลัง ขนาดแบบอักษร และการจัดตำแหน่ง

## ขั้นตอนที่ 6: แทรกเซลล์ส่วนหัวเพิ่มเติม

แทรกเซลล์เพิ่มเติมสำหรับแถวส่วนหัว:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## ขั้นตอนที่ 7: จัดรูปแบบแถวเนื้อหา

หลังจากตั้งค่าส่วนหัวแล้ว ให้จัดรูปแบบเนื้อหาของตาราง:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## ขั้นตอนที่ 8: แทรกแถวเนื้อหา

แทรกแถวเนื้อหาที่มีเนื้อหา:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

ทำซ้ำสำหรับแถวเพิ่มเติม:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## ขั้นตอนที่ 9: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารไปยังไดเร็กทอรีที่ระบุ:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

ซึ่งจะสร้างและบันทึกเอกสาร Word โดยมีตารางที่จัดรูปแบบไว้

## บทสรุป

และแล้วคุณก็ทำได้แล้ว! ด้วยการทำตามขั้นตอนเหล่านี้ คุณก็สามารถสร้างตารางที่มีรูปแบบที่ดีในเอกสาร Word ได้โดยใช้ Aspose.Words สำหรับ .NET ไลบรารีอันทรงพลังนี้ทำให้การจัดการเอกสาร Word ด้วยโปรแกรมเป็นเรื่องง่าย ช่วยประหยัดเวลาและความพยายามของคุณ

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังสำหรับการสร้าง แก้ไข และแปลงเอกสาร Word ด้วยโปรแกรม

### ฉันสามารถใช้สีที่แตกต่างกันสำหรับแต่ละแถวได้หรือไม่
ใช่ คุณสามารถจัดรูปแบบที่แตกต่างกัน รวมถึงสี ให้กับแถวหรือเซลล์ที่แตกต่างกันได้

### Aspose.Words สำหรับ .NET ฟรีหรือเปล่า?
 Aspose.Words สำหรับ .NET เป็นไลบรารีที่ต้องชำระเงิน แต่คุณสามารถรับได้[ทดลองใช้งานฟรี](https://releases.aspose.com/).

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร
 คุณสามารถรับการสนับสนุนได้จาก[ฟอรั่มชุมชน Aspose](https://forum.aspose.com/c/words/8).

### ฉันสามารถสร้างเอกสารประเภทอื่นๆ ด้วย Aspose.Words สำหรับ .NET ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET รองรับรูปแบบเอกสารต่างๆ รวมถึง PDF, HTML และ TXT
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
