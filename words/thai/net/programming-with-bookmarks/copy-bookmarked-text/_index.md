---
title: คัดลอกข้อความที่คั่นหน้าในเอกสาร Word
linktitle: คัดลอกข้อความที่คั่นหน้าในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: คัดลอกข้อความที่คั่นหน้าระหว่างเอกสาร Word ได้อย่างง่ายดายโดยใช้ Aspose.Words สำหรับ .NET เรียนรู้วิธีการด้วยคู่มือทีละขั้นตอนนี้
weight: 10
url: /th/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# คัดลอกข้อความที่คั่นหน้าในเอกสาร Word

## การแนะนำ

คุณเคยพบว่าคุณต้องคัดลอกส่วนต่างๆ จากเอกสาร Word หนึ่งไปยังอีกเอกสารหนึ่งหรือไม่? ถือว่าคุณโชคดี! ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับวิธีการคัดลอกข้อความที่คั่นหน้าจากเอกสาร Word หนึ่งไปยังอีกเอกสารหนึ่งโดยใช้ Aspose.Words สำหรับ .NET ไม่ว่าคุณจะกำลังสร้างรายงานแบบไดนามิกหรือสร้างเอกสารโดยอัตโนมัติ คู่มือนี้จะทำให้กระบวนการนี้ง่ายขึ้นสำหรับคุณ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึก ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.Words สำหรับไลบรารี .NET: คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET อื่น ๆ
- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# และ .NET framework

## นำเข้าเนมสเปซ

ในการเริ่มต้น ให้แน่ใจว่าคุณได้นำเนมสเปซที่จำเป็นเข้ามาในโครงการของคุณแล้ว:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## ขั้นตอนที่ 1: โหลดเอกสารต้นฉบับ

สิ่งแรกที่ต้องทำคือคุณต้องโหลดเอกสารต้นฉบับซึ่งมีข้อความที่คั่นหน้าไว้ซึ่งคุณต้องการคัดลอก

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 ที่นี่,`dataDir` เป็นเส้นทางไปยังไดเรกทอรีเอกสารของคุณและ`Bookmarks.docx` เป็นเอกสารต้นฉบับ

## ขั้นตอนที่ 2: ระบุบุ๊กมาร์ก

ขั้นต่อไป ให้ระบุบุ๊กมาร์กที่คุณต้องการคัดลอกจากเอกสารต้นฉบับ

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 แทนที่`"MyBookmark1"` ด้วยชื่อจริงของบุ๊กมาร์กของคุณ

## ขั้นตอนที่ 3: สร้างเอกสารปลายทาง

ตอนนี้ให้สร้างเอกสารใหม่ที่ข้อความที่คั่นหน้าจะถูกคัดลอก

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## ขั้นตอนที่ 4: นำเข้าเนื้อหาที่คั่นหน้าไว้

 เพื่อให้แน่ใจว่ารูปแบบและการจัดรูปแบบได้รับการรักษาไว้ ให้ใช้`NodeImporter` เพื่อนำเข้าเนื้อหาที่คั่นหน้าไว้จากเอกสารต้นฉบับไปยังเอกสารปลายทาง

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## ขั้นตอนที่ 5: กำหนดวิธีการ AppendBookmarkedText

นี่คือจุดที่เวทมนตร์เกิดขึ้น กำหนดวิธีการจัดการการคัดลอกข้อความที่คั่นหน้าไว้:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## ขั้นตอนที่ 6: บันทึกเอกสารปลายทาง

สุดท้ายให้บันทึกเอกสารปลายทางเพื่อตรวจสอบเนื้อหาที่คัดลอก

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## บทสรุป

เพียงเท่านี้ คุณก็คัดลอกข้อความที่คั่นหน้าจากเอกสาร Word หนึ่งไปยังอีกเอกสารหนึ่งได้สำเร็จโดยใช้ Aspose.Words สำหรับ .NET วิธีนี้มีประสิทธิภาพในการทำให้กระบวนการจัดการเอกสารเป็นแบบอัตโนมัติ ทำให้เวิร์กโฟลว์ของคุณมีประสิทธิภาพและคล่องตัวมากขึ้น

## คำถามที่พบบ่อย

### ฉันสามารถคัดลอกบุ๊กมาร์กหลายอันพร้อมกันได้ไหม
ใช่ คุณสามารถทำซ้ำผ่านบุ๊กมาร์กหลาย ๆ อันและใช้วิธีการเดียวกันในการคัดลอกแต่ละอัน

### ถ้าไม่พบบุ๊กมาร์กจะเกิดอะไรขึ้น?
 การ`Range.Bookmarks` ทรัพย์สินจะกลับมา`null`ดังนั้นคุณต้องแน่ใจว่าคุณจัดการกรณีนี้เพื่อหลีกเลี่ยงข้อยกเว้น

### ฉันสามารถรักษาการจัดรูปแบบของบุ๊กมาร์กต้นฉบับได้หรือไม่
 แน่นอน! ใช้`ImportFormatMode.KeepSourceFormatting` ทำให้แน่ใจว่ารูปแบบดั้งเดิมนั้นได้รับการรักษาไว้

### ขนาดของข้อความที่คั่นหน้ามีจำกัดหรือไม่
ไม่มีข้อจำกัดที่เฉพาะเจาะจง แต่ประสิทธิภาพอาจแตกต่างกันไปขึ้นอยู่กับเอกสารที่มีขนาดใหญ่เป็นอย่างมาก

### ฉันสามารถคัดลอกข้อความระหว่างรูปแบบเอกสาร Word ที่แตกต่างกันได้หรือไม่
ใช่ Aspose.Words รองรับรูปแบบ Word มากมาย และวิธีการนี้สามารถใช้ได้กับรูปแบบเหล่านี้
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
