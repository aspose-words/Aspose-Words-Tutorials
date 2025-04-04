---
title: รับประเภทคำแก้ไข
linktitle: รับประเภทคำแก้ไข
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีรับประเภทคำในการแก้ไขในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET คำแนะนำทีละขั้นตอนนี้จะช่วยให้คุณจัดการการแก้ไขเอกสารได้อย่างมีประสิทธิภาพ
weight: 10
url: /th/net/working-with-revisions/get-revision-types/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# รับประเภทคำแก้ไข

## การแนะนำ

คุณเคยพบว่าตัวเองจมอยู่กับการแก้ไขเอกสารมากมายจนไม่รู้ว่าใครย้ายอะไรและเมื่อใดหรือไม่ คุณไม่ได้เป็นคนเดียว การจัดการการแก้ไขเอกสารอาจเป็นงานที่น่าเบื่อ โดยเฉพาะเมื่อต้องจัดการกับเอกสารจำนวนมาก แต่ไม่ต้องกังวล! ด้วย Aspose.Words สำหรับ .NET คุณสามารถระบุและจัดการการแก้ไขเหล่านี้ได้อย่างง่ายดาย ในคู่มือนี้ เราจะแนะนำคุณทีละขั้นตอนเกี่ยวกับวิธีการรับคำประเภทต่างๆ ในการแก้ไขในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ดังนั้น เตรียมตัวให้พร้อม แล้วมาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงมือทำโค้ด เราจำเป็นต้องมีสิ่งเหล่านี้:

1.  Aspose.Words สำหรับไลบรารี .NET: หากคุณยังไม่ได้ดาวน์โหลด ให้ดาวน์โหลดจาก[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE อื่น ๆ ที่เข้ากันได้กับ .NET
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจเกี่ยวกับภาษาการเขียนโปรแกรม C# จะเป็นประโยชน์
4.  เอกสาร Word ที่มีการแก้ไข: ให้แน่ใจว่าคุณมี`.docx`ไฟล์ที่มีการติดตามการเปลี่ยนแปลงเพื่อทดสอบโค้ด

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ ซึ่งจะช่วยให้คุณสามารถเข้าถึงฟังก์ชันต่างๆ ที่ Aspose.Words จัดเตรียมไว้สำหรับ .NET ได้

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

มาแบ่งตัวอย่างออกเป็นหลายขั้นตอนเพื่อให้เข้าใจและนำไปใช้ได้ดียิ่งขึ้น

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสารของคุณ

ขั้นแรก คุณต้องกำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ นี่คือตำแหน่งที่เอกสาร Word ของคุณพร้อมการแก้ไขจะตั้งอยู่

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` พร้อมเส้นทางจริงไปยังโฟลเดอร์เอกสารของคุณ

## ขั้นตอนที่ 2: โหลดเอกสาร Word ของคุณ

ขั้นตอนต่อไป คุณต้องโหลดเอกสาร Word ลงในโปรเจ็กต์ของคุณ เอกสารนี้ควรมีการแก้ไขที่คุณต้องการวิเคราะห์

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

 ให้แน่ใจว่าไฟล์`Revisions.docx` มีอยู่ในไดเร็กทอรีที่ระบุ

## ขั้นตอนที่ 3: เข้าถึงคอลเลกชันย่อหน้า

เมื่อโหลดเอกสารเสร็จแล้ว คุณต้องเข้าถึงย่อหน้าต่างๆ ในส่วนแรกของเนื้อหาเอกสาร ซึ่งจะช่วยให้คุณตรวจสอบการแก้ไขในแต่ละย่อหน้าได้

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## ขั้นตอนที่ 4: ทำซ้ำในแต่ละย่อหน้าและตรวจสอบการแก้ไข

นี่คือจุดที่เวทมนตร์เกิดขึ้น คุณจะต้องตรวจสอบแต่ละย่อหน้าและตรวจสอบว่าย่อหน้าเหล่านั้นถูกย้าย (ลบหรือแทรก) หรือไม่

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

 ลูปนี้จะผ่านแต่ละย่อหน้าและใช้`IsMoveFromRevision` และ`IsMoveToRevision` คุณสมบัติเพื่อกำหนดว่าย่อหน้าจะถูกย้าย (ลบ) หรือย้าย (แทรก)

## บทสรุป

และแล้วคุณก็จะได้มัน! ด้วยโค้ดเพียงไม่กี่บรรทัด คุณสามารถระบุประเภทการแก้ไขในเอกสาร Word ของคุณได้อย่างง่ายดายโดยใช้ Aspose.Words สำหรับ .NET ไลบรารีอันทรงพลังนี้ทำให้การจัดการการแก้ไขเอกสารเป็นเรื่องง่าย ช่วยให้คุณสามารถมุ่งเน้นไปที่งานที่สำคัญกว่าได้ 

## คำถามที่พบบ่อย

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET เพื่อติดตามการเปลี่ยนแปลงที่ทำโดยผู้ใช้เฉพาะได้หรือไม่

ใช่ Aspose.Words สำหรับ .NET มีฟังก์ชันในการเข้าถึงรายละเอียดการแก้ไข รวมถึงผู้เขียนการเปลี่ยนแปลงด้วย

### มี Aspose.Words สำหรับ .NET ให้ทดลองใช้งานฟรีหรือไม่

 แน่นอน! คุณสามารถทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันจะสมัครใบอนุญาตชั่วคราวสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร

 คุณสามารถขอและสมัครใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.aspose.com/temporary-license/).

### ฉันสามารถหาเอกสารรายละเอียดเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ไหน

 เอกสารรายละเอียดสามารถดูได้ที่[เว็บไซต์อาโพส](https://reference.aspose.com/words/net/).

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET ในโครงการที่ไม่ใช่เชิงพาณิชย์ได้หรือไม่

ใช่ Aspose.Words สำหรับ .NET สามารถใช้ได้ทั้งในโปรเจ็กต์เชิงพาณิชย์และไม่ใช่เชิงพาณิชย์ แต่โปรดตรวจสอบเงื่อนไขการอนุญาตสิทธิ์ให้ดี
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
