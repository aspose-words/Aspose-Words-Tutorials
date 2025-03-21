---
title: การเพิ่มข้อความที่คั่นหน้าในเอกสาร Word
linktitle: การเพิ่มข้อความที่คั่นหน้าในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการผนวกข้อความที่คั่นหน้าไว้ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนนี้ เหมาะสำหรับนักพัฒนา
weight: 10
url: /th/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การเพิ่มข้อความที่คั่นหน้าในเอกสาร Word

## การแนะนำ

สวัสดี! คุณเคยพยายามผนวกข้อความจากส่วนที่คั่นหน้าในเอกสาร Word และพบว่าทำได้ยากหรือไม่ คุณโชคดีแล้ว! บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับกระบวนการโดยใช้ Aspose.Words สำหรับ .NET เราจะแบ่งขั้นตอนดังกล่าวออกเป็นขั้นตอนง่ายๆ เพื่อให้คุณทำตามได้อย่างง่ายดาย มาเริ่มกันเลยและผนวกข้อความที่คั่นหน้าไว้แบบมืออาชีพ!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

-  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งแล้ว หากยังไม่ได้ติดตั้ง คุณสามารถทำได้[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนา .NET ใดๆ เช่น Visual Studio
- ความรู้พื้นฐานเกี่ยวกับ C#: การทำความเข้าใจแนวคิดการเขียนโปรแกรม C# ขั้นพื้นฐานจะเป็นประโยชน์
- เอกสาร Word ที่มีบุ๊กมาร์ก: เอกสาร Word ที่มีการตั้งค่าบุ๊กมาร์กไว้ ซึ่งเราจะใช้ในการผนวกข้อความจากนั้น

## นำเข้าเนมสเปซ

ขั้นแรกเลย เรามาทำการนำเข้าเนมสเปซที่จำเป็นกันก่อน วิธีนี้จะช่วยให้มั่นใจได้ว่าเรามีเครื่องมือทั้งหมดที่จำเป็นอยู่ในมือ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

เรามาแบ่งตัวอย่างออกเป็นขั้นตอนโดยละเอียดกัน

## ขั้นตอนที่ 1: โหลดเอกสารและกำหนดค่าตัวแปร

เอาล่ะ มาเริ่มต้นด้วยการโหลดเอกสาร Word ของเราและกำหนดค่าตัวแปรที่เราต้องการ

```csharp
// โหลดเอกสารต้นทางและปลายทาง
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// เริ่มต้นตัวนำเข้าเอกสาร
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// ค้นหาบุ๊กมาร์กในเอกสารต้นฉบับ
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## ขั้นตอนที่ 2: ระบุย่อหน้าเริ่มต้นและย่อหน้าสิ้นสุด

ตอนนี้ เรามาค้นหาย่อหน้าที่บุ๊กมาร์กเริ่มต้นและสิ้นสุดกัน ซึ่งเป็นสิ่งสำคัญมาก เนื่องจากเราต้องจัดการข้อความภายในขอบเขตเหล่านี้

```csharp
// นี่คือย่อหน้าที่ประกอบด้วยจุดเริ่มต้นของบุ๊กมาร์ก
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// นี่คือย่อหน้าที่เป็นส่วนท้ายของบุ๊กมาร์ก
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## ขั้นตอนที่ 3: ตรวจสอบผู้ปกครองย่อหน้า

เราต้องแน่ใจว่าย่อหน้าเริ่มต้นและย่อหน้าสิ้นสุดมีผู้ปกครองคนเดียวกัน นี่เป็นสถานการณ์ง่ายๆ เพื่อให้ทุกอย่างตรงไปตรงมา

```csharp
// จำกัดตัวเองให้อยู่ในสถานการณ์ที่ค่อนข้างเรียบง่าย
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## ขั้นตอนที่ 4: ระบุโหนดที่จะหยุด

ขั้นต่อไป เราต้องกำหนดโหนดที่จะหยุดการคัดลอกข้อความ ซึ่งจะเป็นโหนดที่อยู่หลังย่อหน้าสุดท้ายทันที

```csharp
// เราต้องการคัดลอกย่อหน้าทั้งหมดตั้งแต่ย่อหน้าเริ่มต้นจนถึง (และรวมถึง) ย่อหน้าสุดท้าย
// ดังนั้นโหนดที่เราหยุดจะอยู่หลังย่อหน้าสุดท้าย
Node endNode = endPara.NextSibling;
```

## ขั้นตอนที่ 5: ผนวกข้อความที่คั่นหน้าไว้ในเอกสารปลายทาง

ในที่สุด ให้เราวนซ้ำผ่านโหนดจากย่อหน้าเริ่มต้นไปยังโหนดหลังย่อหน้าสิ้นสุด และผนวกเข้ากับเอกสารปลายทาง

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // ซึ่งจะสร้างสำเนาของโหนดปัจจุบันและนำเข้า (ทำให้ถูกต้อง) ในบริบท
    // ของเอกสารปลายทาง การนำเข้าหมายถึงการปรับรูปแบบและรายการตัวระบุให้ถูกต้อง
    Node newNode = importer.ImportNode(curNode, true);

    // ผนวกโหนดที่นำเข้าไปยังเอกสารปลายทาง
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// บันทึกเอกสารปลายทางพร้อมข้อความผนวก
dstDoc.Save("appended_document.docx");
```

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณสามารถเพิ่มข้อความจากส่วนที่คั่นหน้าไว้ในเอกสาร Word ได้สำเร็จโดยใช้ Aspose.Words สำหรับ .NET เครื่องมืออันทรงพลังนี้ทำให้การจัดการเอกสารเป็นเรื่องง่าย และตอนนี้คุณก็มีกลเม็ดอีกอันอยู่ในมือแล้ว ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### ฉันสามารถผนวกข้อความจากบุ๊กมาร์กหลาย ๆ อันในครั้งเดียวได้ไหม
ใช่ คุณสามารถทำซ้ำขั้นตอนสำหรับแต่ละบุ๊กมาร์กและผนวกข้อความตามนั้นได้

### จะเกิดอะไรขึ้นถ้าย่อหน้าเริ่มต้นและย่อหน้าสิ้นสุดมีผู้ปกครองต่างกัน?
ตัวอย่างปัจจุบันถือว่ามีผู้ปกครองคนเดียวกัน สำหรับผู้ปกครองที่แตกต่างกัน จำเป็นต้องมีการจัดการที่ซับซ้อนกว่านี้

### ฉันสามารถรักษารูปแบบดั้งเดิมของข้อความผนวกไว้ได้หรือไม่
 แน่นอน!`ImportFormatMode.KeepSourceFormatting` ช่วยให้แน่ใจว่ารูปแบบดั้งเดิมนั้นได้รับการรักษาไว้

### สามารถผนวกข้อความในตำแหน่งที่ระบุในเอกสารปลายทางได้หรือไม่
ใช่ คุณสามารถผนวกข้อความในตำแหน่งใดๆ ได้โดยการนำทางไปยังโหนดที่ต้องการในเอกสารปลายทาง

### จะเกิดอะไรขึ้นหากฉันต้องการผนวกข้อความจากบุ๊กมาร์กไปยังส่วนใหม่?
คุณสามารถสร้างส่วนใหม่ในเอกสารปลายทางและผนวกข้อความไว้ที่นั่นได้
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
