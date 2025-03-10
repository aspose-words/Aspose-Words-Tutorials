---
title: ย้ายโหนดในเอกสารที่ติดตาม
linktitle: ย้ายโหนดในเอกสารที่ติดตาม
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการย้ายโหนดในเอกสาร Word ที่ถูกติดตามโดยใช้ Aspose.Words สำหรับ .NET พร้อมคำแนะนำทีละขั้นตอนโดยละเอียดของเรา เหมาะสำหรับนักพัฒนา
weight: 10
url: /th/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ย้ายโหนดในเอกสารที่ติดตาม

## การแนะนำ

สวัสดีแฟนๆ Aspose.Words! หากคุณเคยจำเป็นต้องย้ายโหนดในเอกสาร Word ขณะติดตามการแก้ไข คุณมาถูกที่แล้ว วันนี้ เราจะมาเจาะลึกวิธีการดำเนินการดังกล่าวโดยใช้ Aspose.Words สำหรับ .NET ไม่เพียงแต่คุณจะได้เรียนรู้ขั้นตอนทีละขั้นตอนเท่านั้น แต่ยังจะได้รับเคล็ดลับและเทคนิคบางอย่างเพื่อให้การจัดการเอกสารของคุณราบรื่นและมีประสิทธิภาพอีกด้วย

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มลงมือเขียนโค้ด เรามาตรวจสอบกันก่อนดีกว่าว่าคุณมีทุกสิ่งที่คุณต้องการแล้ว:

-  Aspose.Words สำหรับ .NET: ดาวน์โหลด[ที่นี่](https://releases.aspose.com/words/net/).
- สภาพแวดล้อม .NET: ให้แน่ใจว่าคุณมีการตั้งค่าสภาพแวดล้อมการพัฒนา .NET ที่เข้ากันได้
- ความรู้พื้นฐานเกี่ยวกับ C#: บทช่วยสอนนี้ถือว่าคุณมีความเข้าใจพื้นฐานเกี่ยวกับ C#

เข้าใจทุกอย่างแล้วใช่ไหม เยี่ยมเลย! มาดูเนมสเปซที่เราต้องนำเข้ากันดีกว่า

## นำเข้าเนมสเปซ

สิ่งแรกที่ต้องทำคือนำเข้าเนมสเปซที่จำเป็น ซึ่งจำเป็นสำหรับการทำงานกับ Aspose.Words และการจัดการโหนดเอกสาร

```csharp
using Aspose.Words;
using System;
```

เอาล่ะ มาแบ่งกระบวนการออกเป็นขั้นตอนที่จัดการได้ แต่ละขั้นตอนจะได้รับการอธิบายอย่างละเอียดเพื่อให้แน่ใจว่าคุณเข้าใจสิ่งที่เกิดขึ้นในแต่ละจุด

## ขั้นตอนที่ 1: เริ่มต้นเอกสาร

 ในการเริ่มต้น เราจะต้องสร้างเอกสารใหม่และใช้`DocumentBuilder` เพื่อเพิ่มบางย่อหน้า

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// การเพิ่มย่อหน้าบางส่วน
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// ตรวจสอบจำนวนย่อหน้าแรก
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## ขั้นตอนที่ 2: เริ่มติดตามการแก้ไข

ขั้นต่อไป เราต้องเริ่มติดตามการแก้ไข ซึ่งถือเป็นสิ่งสำคัญ เพราะช่วยให้เราเห็นการเปลี่ยนแปลงที่เกิดขึ้นกับเอกสารได้

```csharp
// เริ่มติดตามการแก้ไข
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## ขั้นตอนที่ 3: ย้ายโหนด

ตอนนี้มาถึงส่วนหลักของงานของเราแล้ว: การย้ายโหนดจากตำแหน่งหนึ่งไปยังอีกตำแหน่งหนึ่ง เราจะย้ายย่อหน้าที่สามและวางไว้ก่อนย่อหน้าแรก

```csharp
// กำหนดโหนดที่จะย้ายและช่วงสิ้นสุด
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// ย้ายโหนดภายในช่วงที่กำหนด
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## ขั้นตอนที่ 4: หยุดการติดตามการแก้ไข

เมื่อเราได้ย้ายโหนดแล้ว เราต้องหยุดติดตามการแก้ไข

```csharp
// หยุดการติดตามการแก้ไข
doc.StopTrackRevisions();
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายเรามาบันทึกเอกสารที่เราแก้ไขลงในไดเร็กทอรีที่ระบุ

```csharp
// บันทึกเอกสารที่แก้ไข
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// แสดงผลการนับย่อหน้าสุดท้าย
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณได้ย้ายโหนดในเอกสารที่ติดตามโดยใช้ Aspose.Words สำหรับ .NET สำเร็จแล้ว ไลบรารีอันทรงพลังนี้ทำให้การจัดการเอกสาร Word ด้วยโปรแกรมเป็นเรื่องง่าย ไม่ว่าคุณจะกำลังสร้าง แก้ไข หรือติดตามการเปลี่ยนแปลง Aspose.Words ก็ช่วยคุณได้ ดังนั้น ลองใช้ดูได้เลย ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?

Aspose.Words สำหรับ .NET เป็นไลบรารีคลาสสำหรับการทำงานกับเอกสาร Word ด้วยโปรแกรม ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข แปลง และพิมพ์เอกสาร Word ภายในแอปพลิเคชัน .NET ได้

### ฉันจะติดตามการแก้ไขในเอกสาร Word โดยใช้ Aspose.Words ได้อย่างไร

 เพื่อติดตามการแก้ไข ให้ใช้`StartTrackRevisions` วิธีการบน`Document` วัตถุ การดำเนินการนี้จะช่วยให้สามารถติดตามการแก้ไข โดยแสดงการเปลี่ยนแปลงใดๆ ที่เกิดขึ้นกับเอกสาร

### ฉันสามารถย้ายโหนดหลายโหนดใน Aspose.Words ได้หรือไม่

ใช่ คุณสามารถย้ายโหนดหลายโหนดได้โดยการวนซ้ำและใช้วิธีการเช่น`InsertBefore` หรือ`InsertAfter` เพื่อวางไว้ในตำแหน่งที่ต้องการ

### ฉันจะหยุดการติดตามการแก้ไขใน Aspose.Words ได้อย่างไร

 ใช้`StopTrackRevisions` วิธีการบน`Document` คัดค้านการหยุดติดตามการแก้ไข

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด

 คุณสามารถค้นหาเอกสารรายละเอียดได้[ที่นี่](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
