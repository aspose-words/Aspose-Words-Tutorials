---
title: สร้างตารางอย่างมีสไตล์
linktitle: สร้างตารางอย่างมีสไตล์
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการสร้างและกำหนดรูปแบบตารางในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนที่ครอบคลุมนี้
weight: 10
url: /th/net/programming-with-table-styles-and-formatting/build-table-with-style/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างตารางอย่างมีสไตล์

## การแนะนำ

การสร้างเอกสารที่มีสไตล์และเป็นมืออาชีพมักต้องการมากกว่าแค่ข้อความธรรมดา ตารางเป็นวิธีที่ยอดเยี่ยมในการจัดระเบียบข้อมูล แต่การทำให้ข้อมูลดูน่าสนใจนั้นเป็นความท้าทายที่แตกต่างออกไปโดยสิ้นเชิง ลองใช้ Aspose.Words สำหรับ .NET ดูสิ ในบทช่วยสอนนี้ เราจะเจาะลึกถึงวิธีการสร้างตารางที่มีสไตล์ เพื่อทำให้เอกสาร Word ของคุณดูสวยงามและเป็นมืออาชีพ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะไปดูคำแนะนำทีละขั้นตอน เรามาตรวจสอบก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

1.  Aspose.Words สำหรับ .NET: หากคุณยังไม่ได้ดาวน์โหลดและติดตั้ง[Aspose.คำศัพท์สำหรับ .NET](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: คุณควรมีการตั้งค่าสภาพแวดล้อมการพัฒนาไว้ Visual Studio เป็นตัวเลือกที่ดีสำหรับบทช่วยสอนนี้
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะช่วยให้คุณทำตามได้ง่ายขึ้น

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณต้องนำเข้าเนมสเปซที่จำเป็น ซึ่งจะทำให้คุณสามารถเข้าถึงคลาสและวิธีการที่จำเป็นในการจัดการเอกสาร Word ได้

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## ขั้นตอนที่ 1: สร้างเอกสารใหม่และ DocumentBuilder

 สิ่งแรกที่ต้องทำคือคุณต้องสร้างเอกสารใหม่และ`DocumentBuilder` วัตถุ. นี้`DocumentBuilder` จะช่วยคุณสร้างตารางในเอกสารของคุณ

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: เริ่มสร้างตาราง

ตอนนี้เรามีเอกสารและโปรแกรมสร้างพร้อมแล้ว เรามาเริ่มสร้างตารางกันเลย

```csharp
Table table = builder.StartTable();
```

## ขั้นตอนที่ 3: แทรกแถวแรก

ตารางที่ไม่มีแถวเป็นเพียงโครงสร้างว่างๆ เราต้องแทรกอย่างน้อยหนึ่งแถวก่อนจึงจะกำหนดรูปแบบตารางได้

```csharp
builder.InsertCell();
```

## ขั้นตอนที่ 4: ตั้งค่ารูปแบบตาราง

 เมื่อแทรกเซลล์แรกแล้ว ก็ถึงเวลาเพิ่มสไตล์ให้กับตารางของเรา เราจะใช้`StyleIdentifier` เพื่อใช้รูปแบบที่กำหนดไว้ล่วงหน้า

```csharp
// ตั้งค่ารูปแบบตารางที่ใช้โดยอิงตามตัวระบุรูปแบบเฉพาะ
table.StyleIdentifier = StyleIdentifier.MediumShading1Accent1;
```

## ขั้นตอนที่ 5: กำหนดตัวเลือกสไตล์

ตัวเลือกสไตล์ตารางจะกำหนดว่าส่วนใดของตารางที่จะได้รับการจัดสไตล์ ตัวอย่างเช่น เราสามารถเลือกจัดสไตล์คอลัมน์แรก แถบแถว และแถวแรกได้

```csharp
// ใช้ฟีเจอร์ใดจึงควรจัดรูปแบบตามสไตล์
table.StyleOptions = TableStyleOptions.FirstColumn | TableStyleOptions.RowBands | TableStyleOptions.FirstRow;
```

## ขั้นตอนที่ 6: ปรับตารางให้พอดีกับเนื้อหา

เพื่อให้แน่ใจว่าโต๊ะของเราดูเรียบร้อยและเป็นระเบียบ เราสามารถใช้`AutoFit` วิธีการปรับตารางให้พอดีกับเนื้อหา

```csharp
table.AutoFit(AutoFitBehavior.AutoFitToContents);
```

## ขั้นตอนที่ 7: แทรกข้อมูลลงในตาราง

ตอนนี้ถึงเวลาที่จะเติมตารางด้วยข้อมูลบางส่วนแล้ว เราจะเริ่มด้วยแถวส่วนหัว จากนั้นจึงเพิ่มข้อมูลตัวอย่าง

### การแทรกแถวส่วนหัว

```csharp
builder.Writeln("Item");
builder.CellFormat.RightPadding = 40;
builder.InsertCell();
builder.Writeln("Quantity (kg)");
builder.EndRow();
```

#### การแทรกแถวข้อมูล

```csharp
builder.InsertCell();
builder.Writeln("Apples");
builder.InsertCell();
builder.Writeln("20");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Bananas");
builder.InsertCell();
builder.Writeln("40");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Carrots");
builder.InsertCell();
builder.Writeln("50");
builder.EndRow();
```

## ขั้นตอนที่ 8: บันทึกเอกสาร

หลังจากใส่ข้อมูลทั้งหมดแล้ว ขั้นตอนสุดท้ายคือการบันทึกเอกสาร

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.BuildTableWithStyle.docx");
```

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณได้สร้างตารางที่มีสไตล์ในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ไลบรารีอันทรงพลังนี้ทำให้การสร้างเอกสาร Word ให้เป็นอัตโนมัติและปรับแต่งตามความต้องการของคุณเป็นเรื่องง่าย ไม่ว่าคุณจะกำลังสร้างรายงาน ใบแจ้งหนี้ หรือเอกสารประเภทอื่นใด Aspose.Words ก็ช่วยคุณได้

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และจัดการเอกสาร Word ด้วยโปรแกรมโดยใช้ C#

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET เพื่อกำหนดรูปแบบตารางที่มีอยู่ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET สามารถใช้เพื่อกำหนดรูปแบบทั้งตารางใหม่และตารางที่มีอยู่แล้วในเอกสาร Word ของคุณได้

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.Words สำหรับ .NET หรือไม่?
 ใช่ Aspose.Words สำหรับ .NET ต้องมีใบอนุญาตจึงจะใช้งานได้เต็มรูปแบบ คุณสามารถรับได้[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) หรือซื้อแบบเต็มอัน[ที่นี่](https://purchase.aspose.com/buy).

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET เพื่อสร้างเอกสารประเภทอื่นๆ อัตโนมัติได้หรือไม่
แน่นอน! Aspose.Words สำหรับ .NET รองรับเอกสารประเภทต่างๆ รวมถึง DOCX, PDF, HTML และอื่นๆ อีกมากมาย

### ฉันสามารถหาตัวอย่างและเอกสารเพิ่มเติมได้ที่ไหน
 คุณสามารถค้นหาเอกสารและตัวอย่างที่ครอบคลุมได้ที่[หน้าเอกสาร Aspose.Words สำหรับ .NET](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
