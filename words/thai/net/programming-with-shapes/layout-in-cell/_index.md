---
"description": "เรียนรู้วิธีการตั้งค่าเค้าโครงในเซลล์โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือฉบับสมบูรณ์นี้ เหมาะสำหรับนักพัฒนาที่ต้องการปรับแต่งเอกสาร Word"
"linktitle": "เค้าโครงในเซลล์"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "เค้าโครงในเซลล์"
"url": "/th/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เค้าโครงในเซลล์

## การแนะนำ

หากคุณต้องการปรับแต่งเค้าโครงของเซลล์ตารางในเอกสาร Word ด้วยโปรแกรม คุณมาถูกที่แล้ว วันนี้ เราจะมาเจาะลึกวิธีการตั้งค่าเค้าโครงในเซลล์โดยใช้ Aspose.Words สำหรับ .NET เราจะอธิบายตัวอย่างในทางปฏิบัติทีละขั้นตอนเพื่อให้คุณทำตามได้อย่างง่ายดาย

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้นเขียนโค้ด เรามาตรวจสอบก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

1. Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Aspose.Words สำหรับ .NET แล้ว หากยังไม่ได้ติดตั้ง คุณสามารถ [ดาวน์โหลดได้ที่นี่](https://releases-aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: คุณจะต้องมีสภาพแวดล้อมการพัฒนาที่ตั้งค่าด้วย .NET Visual Studio เป็นตัวเลือกที่ดีหากคุณกำลังมองหาคำแนะนำ
3. ความรู้พื้นฐานเกี่ยวกับ C#: แม้ว่าฉันจะอธิบายแต่ละขั้นตอน แต่ความเข้าใจพื้นฐานเกี่ยวกับ C# จะช่วยให้คุณทำตามได้ง่ายขึ้น
4. ไดเรกทอรีเอกสาร: เตรียมเส้นทางไดเรกทอรีที่คุณจะบันทึกเอกสารของคุณ เราจะเรียกสิ่งนี้ว่า `YOUR DOCUMENT DIRECTORY`-

## นำเข้าเนมสเปซ

ในการเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณกำลังนำเข้าเนมสเปซที่จำเป็นในโครงการของคุณ:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

มาแบ่งกระบวนการออกเป็นขั้นตอนที่สามารถจัดการได้

## ขั้นตอนที่ 1: สร้างเอกสารใหม่

ขั้นแรกเราจะสร้างเอกสาร Word ใหม่และเริ่มต้นใช้งาน `DocumentBuilder` วัตถุที่จะช่วยเราสร้างเนื้อหาของเรา

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: เริ่มต้นตารางและตั้งค่ารูปแบบแถว

เราจะเริ่มต้นการสร้างตารางและระบุความสูงและกฎความสูงสำหรับแถว

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## ขั้นตอนที่ 3: แทรกเซลล์และเติมเนื้อหา

ต่อไป เราจะวนซ้ำเพื่อแทรกเซลล์ลงในตาราง สำหรับทุกๆ 7 เซลล์ เราจะสิ้นสุดแถวเพื่อสร้างเซลล์ใหม่

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## ขั้นตอนที่ 4: เพิ่มรูปทรงลายน้ำ

ตอนนี้เรามาเพิ่มลายน้ำลงในเอกสารของเรากัน เราจะสร้าง `Shape` วัตถุและกำหนดคุณสมบัติของมัน

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // แสดงรูปร่างภายนอกเซลล์ตารางหากจะวางไว้ในเซลล์
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## ขั้นตอนที่ 5: ปรับแต่งลักษณะลายน้ำ

เราจะปรับแต่งลักษณะที่ปรากฏของลายน้ำเพิ่มเติมโดยการตั้งค่าคุณสมบัติสีและข้อความ

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## ขั้นตอนที่ 6: แทรกลายน้ำลงในเอกสาร

เราจะค้นหาการทำงานครั้งสุดท้ายในเอกสารและแทรกลายน้ำที่ตำแหน่งนั้น

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## ขั้นตอนที่ 7: เพิ่มประสิทธิภาพเอกสารสำหรับ Word 2010

เพื่อให้แน่ใจว่ามีความเข้ากันได้ เราจะเพิ่มประสิทธิภาพเอกสารสำหรับ Word 2010

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## ขั้นตอนที่ 8: บันทึกเอกสาร

สุดท้ายเราจะบันทึกเอกสารของเราไปยังไดเร็กทอรีที่ระบุ

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณได้สร้างเอกสาร Word ที่มีเค้าโครงตารางที่กำหนดเองได้สำเร็จแล้ว และเพิ่มลายน้ำโดยใช้ Aspose.Words สำหรับ .NET บทช่วยสอนนี้มุ่งหวังที่จะให้คำแนะนำแบบทีละขั้นตอนที่ชัดเจนเพื่อช่วยให้คุณเข้าใจแต่ละส่วนของกระบวนการ ด้วยทักษะเหล่านี้ คุณสามารถสร้างเอกสาร Word ที่ซับซ้อนและกำหนดเองได้มากขึ้นด้วยโปรแกรม

## คำถามที่พบบ่อย

### ฉันสามารถใช้แบบอักษรอื่นสำหรับข้อความลายน้ำได้ไหม
ใช่ คุณสามารถเปลี่ยนแบบอักษรได้โดยการตั้งค่า `watermark.TextPath.FontFamily` คุณสมบัติของแบบอักษรที่คุณต้องการ

### ฉันจะปรับตำแหน่งลายน้ำได้อย่างไร?
คุณสามารถปรับเปลี่ยนได้ `RelativeHorizontalPosition`- `RelativeVerticalPosition`- `HorizontalAlignment`, และ `VerticalAlignment` คุณสมบัติในการปรับตำแหน่งลายน้ำ

### เป็นไปได้ไหมที่จะใช้รูปภาพแทนข้อความสำหรับลายน้ำ?
แน่นอน! คุณสามารถสร้าง `Shape` ด้วยประเภท `ShapeType.Image` และตั้งค่าภาพโดยใช้ `ImageData.SetImage` วิธี.

### ฉันสามารถสร้างตารางที่มีความสูงของแถวแตกต่างกันได้หรือไม่
ใช่ คุณสามารถตั้งค่าความสูงที่แตกต่างกันสำหรับแต่ละแถวได้โดยการเปลี่ยนแปลง `RowFormat.Height` คุณสมบัติก่อนที่จะแทรกเซลล์ลงในแถวนั้น

### ฉันจะลบลายน้ำออกจากเอกสารได้อย่างไร?
คุณสามารถลบลายน้ำได้โดยค้นหาในคอลเล็กชันรูปร่างของเอกสารและเรียกใช้ `Remove` วิธี.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}