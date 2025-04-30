---
"description": "เรียนรู้วิธีนำเข้าเอกสารโดยคงรูปแบบไว้โดยใช้ Aspose.Words สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด"
"linktitle": "รักษาหมายเลขแหล่งที่มา"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "รักษาหมายเลขแหล่งที่มา"
"url": "/th/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# รักษาหมายเลขแหล่งที่มา

## การแนะนำ

เมื่อทำงานกับ Aspose.Words สำหรับ .NET การนำเข้าเอกสารจากแหล่งหนึ่งไปยังอีกแหล่งหนึ่งโดยยังคงรักษาการจัดรูปแบบไว้สามารถจัดการได้อย่างมีประสิทธิภาพโดยใช้ `NodeImporter` ชั้นเรียน บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการทีละขั้นตอน

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio ลงบนเครื่องของคุณแล้ว
- ติดตั้ง Aspose.Words สำหรับ .NET แล้ว ถ้ายังไม่ได้ติดตั้ง ให้ดาวน์โหลดจาก [ที่นี่](https://releases-aspose.com/words/net/).
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C# และ .NET

## นำเข้าเนมสเปซ

ขั้นแรก ให้รวมเนมสเปซที่จำเป็นในโครงการของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

เริ่มต้นด้วยการสร้างโปรเจ็กต์ C# ใหม่ใน Visual Studio และติดตั้ง Aspose.Words ผ่านตัวจัดการแพ็กเกจ NuGet

## ขั้นตอนที่ 2: เริ่มต้นเอกสาร
สร้างอินสแตนซ์ของแหล่งที่มา (`srcDoc`) และจุดหมายปลายทาง (`dstDoc`) เอกสาร

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการนำเข้า
ตั้งค่าตัวเลือกการนำเข้าเพื่อรักษาการจัดรูปแบบต้นฉบับ รวมถึงย่อหน้าที่มีหมายเลข

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## ขั้นตอนที่ 4: นำเข้าย่อหน้า
ทำซ้ำผ่านย่อหน้าในเอกสารต้นฉบับและนำเข้าสู่เอกสารปลายทาง

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารที่ผสานไปยังตำแหน่งที่คุณต้องการ

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## บทสรุป

สรุปแล้ว การใช้ Aspose.Words สำหรับ .NET เพื่อนำเข้าเอกสารโดยยังคงรักษาการจัดรูปแบบไว้เป็นเรื่องง่ายด้วย `NodeImporter` วิธีนี้ช่วยให้มั่นใจว่าเอกสารของคุณยังคงรูปลักษณ์และโครงสร้างเดิมได้อย่างลงตัว

## คำถามที่พบบ่อย

### ฉันสามารถนำเข้าเอกสารที่มีรูปแบบการจัดรูปแบบที่แตกต่างกันได้หรือไม่
ใช่ครับ `NodeImporter` คลาสนี้รองรับการนำเข้าเอกสารที่มีรูปแบบการจัดรูปแบบที่หลากหลาย

### จะเกิดอะไรขึ้นหากเอกสารของฉันมีตารางและรูปภาพที่ซับซ้อน?
Aspose.Words สำหรับ .NET จัดการโครงสร้างที่ซับซ้อนเช่นตารางและรูปภาพในระหว่างการดำเนินการนำเข้า

### Aspose.Words สามารถทำงานร่วมกับ .NET ทุกเวอร์ชันได้หรือไม่
Aspose.Words รองรับเวอร์ชันของ .NET Framework และ .NET Core เพื่อการรวมเข้ากันที่ราบรื่น

### ฉันจะจัดการข้อผิดพลาดในระหว่างการนำเข้าเอกสารได้อย่างไร
ใช้บล็อก try-catch เพื่อจัดการข้อยกเว้นที่อาจเกิดขึ้นในระหว่างกระบวนการนำเข้า

### ฉันสามารถหาเอกสารโดยละเอียดเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ไหน
เยี่ยมชม [เอกสารประกอบ](https://reference.aspose.com/words/net/) สำหรับคำแนะนำที่ครอบคลุมและการอ้างอิง API



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}