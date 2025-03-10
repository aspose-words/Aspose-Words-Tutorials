---
title: แสดงซ่อนบุ๊กมาร์กในเอกสาร Word
linktitle: แสดงซ่อนบุ๊กมาร์กในเอกสาร Word
second_title: Aspose.Words API การประมวลผลเอกสาร
description: เรียนรู้วิธีแสดงหรือซ่อนบุ๊กมาร์กในเอกสาร Word แบบไดนามิกโดยใช้ Aspose.Words สำหรับ .NET พร้อมคำแนะนำทีละขั้นตอนของเรา เหมาะสำหรับนักพัฒนา
weight: 10
url: /th/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แสดงซ่อนบุ๊กมาร์กในเอกสาร Word

## การแนะนำ

เคยพบว่าตัวเองจำเป็นต้องซ่อนหรือแสดงบางส่วนของเอกสาร Word แบบไดนามิกหรือไม่? คุณโชคดี! ด้วย Aspose.Words สำหรับ .NET คุณสามารถจัดการการเปิดเผยเนื้อหาที่คั่นหน้าในเอกสารของคุณได้อย่างง่ายดาย บทช่วยสอนนี้จะแนะนำคุณตลอดขั้นตอนการแสดงและซ่อนบุ๊กมาร์กในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เราจะแจกแจงโค้ดทีละขั้นตอน ดังนั้นไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือมือใหม่ คุณจะพบว่าคู่มือนี้ง่ายต่อการปฏิบัติตาม

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกโค้ด เรามาตรวจสอบให้แน่ใจว่าคุณมีทุกสิ่งที่คุณต้องการ:

1.  Aspose.Words for .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Aspose.Words for .NET แล้ว ถ้าไม่คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: IDE เช่น Visual Studio
3. ความรู้พื้นฐานของ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะเป็นประโยชน์
4. เอกสาร Word: เอกสาร Word ตัวอย่างพร้อมที่คั่นหน้า

## นำเข้าเนมสเปซ

ก่อนที่จะเริ่มต้นด้วยโค้ด คุณต้องนำเข้าเนมสเปซที่จำเป็นก่อน เพิ่มสิ่งต่อไปนี้ที่จุดเริ่มต้นของไฟล์ C# ของคุณ:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## ขั้นตอนที่ 1: โหลดเอกสารของคุณ

ก่อนอื่นคุณต้องโหลดเอกสาร Word ที่มีบุ๊กมาร์ก ต่อไปนี้คือวิธีที่คุณสามารถทำได้:

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### คำอธิบาย

- dataDir: นี่คือเส้นทางไดเร็กทอรีที่มีเอกสาร Word ของคุณอยู่
-  เอกสารเอกสาร: นี่เป็นการเริ่มต้นอินสแตนซ์ใหม่ของ`Document` คลาสด้วยไฟล์ที่คุณระบุ

## ขั้นตอนที่ 2: แสดงหรือซ่อนเนื้อหาที่คั่นหน้า

ต่อไปเราจะกำหนดวิธีการแสดงหรือซ่อนเนื้อหาที่บุ๊กมาร์กไว้ นี่คือวิธีการที่สมบูรณ์:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD bookmark}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### คำอธิบาย

- บุ๊กมาร์ก bm: ดึงบุ๊กมาร์กจากเอกสาร
- ตัวสร้าง DocumentBuilder: ช่วยในการนำทางและแก้ไขเอกสาร
- ช่องฟิลด์: แทรกช่อง IF เพื่อตรวจสอบสภาพของที่คั่นหน้า
- โหนด currentNode: สำรวจผ่านโหนดเพื่อค้นหาจุดเริ่มต้นและจุดสิ้นสุดของฟิลด์

## ขั้นตอนที่ 3: ดำเนินการฟังก์ชันแสดง/ซ่อน

 ตอนนี้คุณต้องโทรไปที่`ShowHideBookmarkedContent` วิธีการส่งเอกสาร ชื่อบุ๊กมาร์ก และแฟล็กการมองเห็น:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### คำอธิบาย

- doc: วัตถุเอกสารของคุณ
- "MyBookmark1": ชื่อของบุ๊กมาร์กที่คุณต้องการแสดง/ซ่อน
- เท็จ: ธงการมองเห็น (จริงสำหรับการแสดง เท็จสำหรับการซ่อน)

## ขั้นตอนที่ 4: บันทึกเอกสารของคุณ

สุดท้าย ให้บันทึกเอกสารที่แก้ไข:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### คำอธิบาย

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": เส้นทางและชื่อของเอกสารใหม่ที่จะบันทึกการเปลี่ยนแปลง

## บทสรุป

และคุณก็ได้แล้ว! คุณได้เรียนรู้วิธีการแสดงและซ่อนบุ๊กมาร์กในเอกสาร Word โดยใช้ Aspose.Words for .NET เรียบร้อยแล้ว เทคนิคนี้มีประโยชน์อย่างเหลือเชื่อสำหรับการสร้างเอกสารแบบไดนามิกที่มีเนื้อหาแบบมีเงื่อนไข

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร
Aspose.Words สำหรับ .NET เป็นไลบรารีการประมวลผลเอกสารที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และแปลงเอกสาร Word โดยทางโปรแกรมได้

### ฉันจะรับ Aspose.Words สำหรับ .NET ได้อย่างไร
 คุณสามารถดาวน์โหลด Aspose.Words สำหรับ .NET ได้จาก[ที่นี่](https://releases.aspose.com/words/net/)- มีการทดลองใช้ฟรีด้วย

### ฉันสามารถใช้วิธีนี้กับบุ๊กมาร์กประเภทอื่นได้หรือไม่
ได้ คุณสามารถปรับใช้วิธีนี้เพื่อจัดการการมองเห็นบุ๊กมาร์กในเอกสาร Word ของคุณได้

### จะเกิดอะไรขึ้นหากเอกสารของฉันไม่มีบุ๊กมาร์กที่ระบุ
หากไม่มีบุ๊กมาร์ก วิธีการนี้จะทำให้เกิดข้อผิดพลาด ตรวจสอบให้แน่ใจว่ามีบุ๊กมาร์กก่อนที่จะพยายามแสดง/ซ่อน

### ฉันจะรับการสนับสนุนได้อย่างไรหากฉันประสบปัญหา
 คุณสามารถรับการสนับสนุนจากชุมชน Aspose[ที่นี่](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
