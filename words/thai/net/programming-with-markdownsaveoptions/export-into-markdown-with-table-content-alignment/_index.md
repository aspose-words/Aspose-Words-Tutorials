---
title: ส่งออกเป็นมาร์กดาวน์พร้อมการจัดตำแหน่งเนื้อหาตาราง
linktitle: ส่งออกเป็นมาร์กดาวน์พร้อมการจัดตำแหน่งเนื้อหาตาราง
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการส่งออกเอกสาร Word ไปยัง Markdown พร้อมจัดตารางให้ตรงกันโดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อสร้างตาราง Markdown ที่สมบูรณ์แบบ
weight: 10
url: /th/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ส่งออกเป็นมาร์กดาวน์พร้อมการจัดตำแหน่งเนื้อหาตาราง

## การแนะนำ

สวัสดี! คุณเคยสงสัยไหมว่าจะส่งออกเอกสาร Word ของคุณเป็นรูปแบบ Markdown พร้อมจัดวางตารางให้ตรงกันได้อย่างไร ไม่ว่าคุณจะเป็นนักพัฒนาที่ทำงานด้านเอกสารหรือเพียงแค่คนที่ชื่นชอบ Markdown คู่มือนี้เหมาะสำหรับคุณ เราจะเจาะลึกรายละเอียดการใช้ Aspose.Words สำหรับ .NET เพื่อให้บรรลุสิ่งนี้ พร้อมหรือยังที่จะเปลี่ยนตาราง Word ของคุณให้เป็นตาราง Markdown ที่จัดวางอย่างเรียบร้อย มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกโค้ด มีบางสิ่งที่คุณจะต้องมี:

1.  ไลบรารี Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณมีไลบรารี Aspose.Words สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณ Visual Studio เป็นตัวเลือกยอดนิยมสำหรับการพัฒนา .NET
3. ความรู้พื้นฐานเกี่ยวกับ C#: การทำความเข้าใจ C# ถือเป็นสิ่งสำคัญเนื่องจากเราจะเขียนโค้ดในภาษานี้
4. ตัวอย่างเอกสาร Word: มีเอกสาร Word ที่คุณสามารถใช้สำหรับการทดสอบได้

## นำเข้าเนมสเปซ

ก่อนที่เราจะเริ่มเขียนโค้ด เรามาทำการนำเข้าเนมสเปซที่จำเป็นกันก่อน ซึ่งจะช่วยให้เข้าถึงคลาสและเมธอด Aspose.Words ที่เราจะใช้

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน Document และ DocumentBuilder

สิ่งแรกที่ต้องทำคือเราต้องสร้างเอกสาร Word ใหม่และเริ่มต้นใช้งาน`DocumentBuilder` วัตถุที่จะเริ่มสร้างเอกสารของเรา

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";

// สร้างเอกสารใหม่
Document doc = new Document();

// เริ่มต้นการใช้งาน DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: แทรกเซลล์และจัดตำแหน่งเนื้อหา

ต่อไป เราจะแทรกเซลล์บางเซลล์ลงในเอกสารและกำหนดการจัดตำแหน่ง ซึ่งเป็นสิ่งสำคัญเพื่อให้แน่ใจว่าการส่งออก Markdown จะรักษาการจัดตำแหน่งที่ถูกต้อง

```csharp
// แทรกเซลล์และตั้งค่าการจัดตำแหน่งไปทางขวา
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// แทรกเซลล์อื่นและจัดตำแหน่งให้ตรงกลาง
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## ขั้นตอนที่ 3: ตั้งค่าการจัดตำแหน่งเนื้อหาตารางสำหรับการส่งออกมาร์กดาวน์

 ตอนนี้ถึงเวลาที่จะกำหนดค่าแล้ว`MarkdownSaveOptions` เพื่อควบคุมการจัดวางเนื้อหาตารางในไฟล์ Markdown ที่ส่งออก เราจะบันทึกเอกสารด้วยการตั้งค่าการจัดวางที่แตกต่างกันเพื่อดูว่ามันทำงานอย่างไร

```csharp
// สร้างอ็อบเจ็กต์ MarkdownSaveOptions
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// บันทึกเอกสารโดยจัดชิดซ้าย
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// เปลี่ยนการจัดตำแหน่งไปทางขวาและบันทึก
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// เปลี่ยนการจัดตำแหน่งให้เป็นศูนย์กลางและบันทึก
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## ขั้นตอนที่ 4: ใช้การจัดตำแหน่งเนื้อหาตารางอัตโนมัติ

 การ`Auto`ตัวเลือกการจัดตำแหน่งจะจัดตำแหน่งจากย่อหน้าแรกในคอลัมน์ตารางที่เกี่ยวข้อง ซึ่งอาจมีประโยชน์ในกรณีที่คุณมีการจัดตำแหน่งแบบผสมในตารางเดียว

```csharp
// ตั้งค่าการจัดตำแหน่งเป็นอัตโนมัติ
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// บันทึกเอกสารด้วยการจัดตำแหน่งอัตโนมัติ
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## บทสรุป

และแล้วคุณก็ทำได้! การส่งออกเอกสาร Word ไปยัง Markdown ที่มีตารางที่จัดแนวโดยใช้ Aspose.Words สำหรับ .NET เป็นเรื่องง่ายเมื่อคุณรู้วิธีดำเนินการ ไลบรารีอันทรงพลังนี้ทำให้การควบคุมการจัดรูปแบบและการจัดแนวตารางของคุณเป็นเรื่องง่าย ทำให้มั่นใจได้ว่าเอกสาร Markdown ของคุณจะมีลักษณะตามที่คุณต้องการ ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข แปลง และส่งออกเอกสาร Word โดยโปรแกรมได้

### ฉันสามารถตั้งค่าการจัดตำแหน่งที่แตกต่างกันสำหรับคอลัมน์ต่างๆ ในตารางเดียวกันได้หรือไม่
 ใช่ โดยการใช้`Auto` ตัวเลือกการจัดตำแหน่ง คุณสามารถมีการจัดตำแหน่งที่แตกต่างกันตามย่อหน้าแรกในแต่ละคอลัมน์ได้

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.Words สำหรับ .NET หรือไม่?
 ใช่ Aspose.Words สำหรับ .NET ต้องมีใบอนุญาตจึงจะใช้งานได้เต็มรูปแบบ คุณสามารถรับได้[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อการประเมินผล

### สามารถส่งออกองค์ประกอบเอกสารอื่นๆ ไปยัง Markdown โดยใช้ Aspose.Words ได้หรือไม่
ใช่ Aspose.Words รองรับการส่งออกองค์ประกอบต่างๆ เช่น หัวเรื่อง รายการ และรูปภาพไปเป็นรูปแบบ Markdown

### ฉันจะได้รับการสนับสนุนได้ที่ไหนหากประสบปัญหา?
 คุณสามารถรับการสนับสนุนได้จาก[ฟอรั่มสนับสนุน Aspose.Words](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
