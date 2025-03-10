---
title: แทรกเอกสารในจดหมายเวียน
linktitle: แทรกเอกสารในจดหมายเวียน
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีแทรกเอกสารในช่องจดหมายผสานโดยใช้ Aspose.Words สำหรับ .NET ในบทช่วยสอนทีละขั้นตอนที่ครอบคลุมนี้
weight: 10
url: /th/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกเอกสารในจดหมายเวียน

## การแนะนำ

ยินดีต้อนรับสู่โลกแห่งการทำงานเอกสารอัตโนมัติด้วย Aspose.Words สำหรับ .NET! คุณเคยสงสัยไหมว่าจะแทรกเอกสารลงในฟิลด์เฉพาะภายในเอกสารหลักระหว่างการดำเนินการผสานจดหมายได้อย่างไร คุณมาถูกที่แล้ว บทช่วยสอนนี้จะแนะนำคุณทีละขั้นตอนในการแทรกเอกสารลงในฟิลด์ผสานจดหมายโดยใช้ Aspose.Words สำหรับ .NET เหมือนกับการต่อจิ๊กซอว์ที่แต่ละชิ้นจะเข้าที่เข้าทางอย่างสมบูรณ์แบบ มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1.  Aspose.Words สำหรับ .NET: คุณสามารถ[ดาวน์โหลดเวอร์ชันล่าสุดได้ที่นี่](https://releases.aspose.com/words/net/) หากคุณต้องการซื้อใบอนุญาต คุณสามารถทำได้[ที่นี่](https://purchase.aspose.com/buy) . อีกวิธีหนึ่ง คุณสามารถรับ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) หรือลองใช้ดูด้วย[ทดลองใช้งานฟรี](https://releases.aspose.com/).
2. สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE C# อื่นๆ
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะทำให้บทช่วยสอนนี้เป็นเรื่องง่าย

## นำเข้าเนมสเปซ

สิ่งแรกที่ต้องทำคือคุณต้องนำเข้าเนมสเปซที่จำเป็น ซึ่งถือเป็นส่วนประกอบพื้นฐานของโปรเจ็กต์ของคุณ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

มาแบ่งกระบวนการออกเป็นขั้นตอนที่จัดการได้ แต่ละขั้นตอนจะต่อยอดจากขั้นตอนก่อนหน้า ช่วยให้คุณหาแนวทางแก้ไขที่สมบูรณ์ได้

## ขั้นตอนที่ 1: การตั้งค่าไดเร็กทอรีของคุณ

ก่อนที่คุณจะเริ่มแทรกเอกสาร คุณต้องกำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณก่อน นี่คือที่ที่เอกสารของคุณถูกจัดเก็บไว้

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ขั้นตอนที่ 2: การโหลดเอกสารหลัก

ขั้นต่อไป คุณจะโหลดเอกสารหลัก เอกสารนี้ประกอบด้วยฟิลด์ผสานที่จะแทรกเอกสารอื่น ๆ เข้าไป

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## ขั้นตอนที่ 3: ตั้งค่าการเรียกกลับการรวมฟิลด์

ในการจัดการกระบวนการผสาน คุณจะต้องตั้งค่าฟังก์ชันการโทรกลับ ฟังก์ชันนี้จะรับผิดชอบในการแทรกเอกสารในฟิลด์ผสานที่ระบุ

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## ขั้นตอนที่ 4: การดำเนินการจดหมายเวียน

ตอนนี้ถึงเวลาดำเนินการผสานจดหมายแล้ว นี่คือจุดที่ความมหัศจรรย์เกิดขึ้น คุณจะต้องระบุฟิลด์ผสานและเอกสารที่จะแทรกในฟิลด์นี้

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## ขั้นตอนที่ 5: การบันทึกเอกสาร

เมื่อการผสานจดหมายเสร็จสมบูรณ์แล้ว คุณจะบันทึกเอกสารที่แก้ไข เอกสารใหม่นี้จะมีเนื้อหาที่แทรกไว้ตรงตำแหน่งที่คุณต้องการ

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## ขั้นตอนที่ 6: การสร้างตัวจัดการการโทรกลับ

ตัวจัดการการโทรกลับเป็นคลาสที่สร้างการประมวลผลพิเศษสำหรับฟิลด์ผสาน โดยจะโหลดเอกสารที่ระบุไว้ในค่าฟิลด์และแทรกเข้าในฟิลด์ผสานปัจจุบัน

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## ขั้นตอนที่ 7: การแทรกเอกสาร

วิธีการนี้จะแทรกเอกสารที่ระบุลงในย่อหน้าหรือเซลล์ตารางปัจจุบัน

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้แทรกเอกสารลงในฟิลด์เฉพาะระหว่างการดำเนินการผสานจดหมายสำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ฟีเจอร์อันทรงพลังนี้จะช่วยประหยัดเวลาและความพยายามของคุณได้มาก โดยเฉพาะอย่างยิ่งเมื่อต้องจัดการกับเอกสารจำนวนมาก ลองนึกดูว่ามีผู้ช่วยส่วนตัวที่ดูแลงานหนักทั้งหมดแทนคุณ ดังนั้น ลองใช้ดูได้เลย สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### ฉันสามารถแทรกเอกสารหลายฉบับในช่องผสานที่แตกต่างกันได้หรือไม่
ใช่ คุณสามารถทำได้ เพียงระบุฟิลด์ผสานที่เหมาะสมและเส้นทางเอกสารที่สอดคล้องกันใน`MailMerge.Execute` วิธี.

### สามารถจัดรูปแบบเอกสารที่แทรกให้แตกต่างจากเอกสารหลักได้หรือไม่
 แน่นอน! คุณสามารถใช้`ImportFormatMode` พารามิเตอร์ใน`NodeImporter` เพื่อควบคุมการจัดรูปแบบ

### จะเกิดอะไรขึ้นถ้าชื่อฟิลด์ผสานเป็นแบบไดนามิก?
คุณสามารถจัดการชื่อฟิลด์การผสานแบบไดนามิกได้โดยส่งเป็นพารามิเตอร์ไปยังตัวจัดการการโทรกลับ

### ฉันสามารถใช้วิธีนี้กับรูปแบบไฟล์อื่นได้หรือไม่
ใช่ Aspose.Words รองรับรูปแบบไฟล์ต่างๆ รวมถึง DOCX, PDF และอื่นๆ อีกมากมาย

### ฉันจะจัดการข้อผิดพลาดในระหว่างกระบวนการแทรกเอกสารได้อย่างไร
นำการจัดการข้อผิดพลาดไปใช้ในตัวจัดการการโทรกลับเพื่อจัดการข้อยกเว้นใดๆ ที่อาจเกิดขึ้น
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
