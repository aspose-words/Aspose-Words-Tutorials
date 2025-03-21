---
title: รับรายละเอียดกลุ่มการแก้ไข
linktitle: รับรายละเอียดกลุ่มการแก้ไข
second_title: API การประมวลผลเอกสาร Aspose.Words
description: รับรายละเอียดกลุ่มการแก้ไขในเอกสาร Word ได้อย่างง่ายดายโดยใช้ Aspose.Words สำหรับ .NET พร้อมคำแนะนำทีละขั้นตอนนี้ เหมาะสำหรับนักพัฒนา .NET
weight: 10
url: /th/net/working-with-revisions/get-revision-group-details/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# รับรายละเอียดกลุ่มการแก้ไข

## การแนะนำ

คุณเคยพบว่าตัวเองจำเป็นต้องลงลึกในรายละเอียดเล็กๆ น้อยๆ ของการแก้ไขในเอกสาร Word หรือไม่ บางทีคุณอาจกำลังทำงานร่วมกันในโครงการ และคุณจำเป็นต้องติดตามการเปลี่ยนแปลงอย่างพิถีพิถัน เตรียมตัวให้พร้อม เพราะเรากำลังจะเจาะลึกบทช่วยสอนที่ยอดเยี่ยมเกี่ยวกับวิธีการรับรายละเอียดกลุ่มการแก้ไขโดยใช้ Aspose.Words สำหรับ .NET เมื่ออ่านคู่มือนี้จบ คุณจะกลายเป็นผู้เชี่ยวชาญในการแยกและแสดงรายละเอียดการแก้ไข ทำให้การจัดการเอกสารของคุณเป็นเรื่องง่าย

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มเส้นทางการเขียนโค้ด เรามาตรวจสอบก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:
-  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งเวอร์ชันล่าสุดแล้ว หากยังไม่ได้ติดตั้ง คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา .NET: ตรวจสอบว่าคุณมีสภาพแวดล้อมการพัฒนา .NET ที่ใช้งานได้ Visual Studio เป็นตัวเลือกที่ยอดเยี่ยม
- เอกสาร Word ที่มีการแก้ไข: สำหรับบทช่วยสอนนี้ เราจะใช้เอกสาร Word ตัวอย่างที่มีการแก้ไข (`Revisions.docx`-

## นำเข้าเนมสเปซ

ขั้นแรก ให้เรานำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ของคุณก่อน ซึ่งถือเป็นสิ่งสำคัญในการเข้าถึงฟังก์ชัน Aspose.Words

```csharp
using Aspose.Words;
using System;
```

เอาล่ะ มาแบ่งขั้นตอนนี้ออกเป็นขั้นตอนต่างๆ กัน แต่ละขั้นตอนจะแนะนำคุณตลอดกระบวนการรับรายละเอียดกลุ่มการแก้ไขโดยใช้ Aspose.Words สำหรับ .NET

## ขั้นตอนที่ 1: โหลดเอกสาร Word

ขั้นตอนแรกคือการโหลดเอกสาร Word ของคุณ ซึ่งเป็นที่ที่การแก้ไขของคุณถูกเก็บไว้

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Revisions.docx");
```

 ในสคริปท์นี้ ให้แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงไปยังเอกสารของคุณ รหัสนี้จะโหลด`Revisions.docx` ไฟล์เข้าใน`doc` วัตถุ.

## ขั้นตอนที่ 2: เข้าถึงคอลเลกชันการแก้ไข

 ตอนนี้มาดูการแก้ไขในเอกสารกัน Aspose.Words จัดเตรียม`Revisions` คอลเลกชั่นที่เราสามารถทำซ้ำได้

```csharp
foreach (Revision revision in doc.Revisions)
{
    // ดำเนินการแก้ไขแต่ละครั้ง
}
```

ลูปนี้จะผ่านการแก้ไขแต่ละครั้งในเอกสาร ซึ่งทำให้เราสามารถดึงรายละเอียดออกมาได้

## ขั้นตอนที่ 3: ดึงรายละเอียดการแก้ไข

ภายในลูป เราสามารถแยกรายละเอียดต่าง ๆ เกี่ยวกับการแก้ไขแต่ละครั้งได้ เช่น ประเภท ผู้เขียน วันที่ และข้อความ

```csharp
foreach (Revision revision in doc.Revisions)
{
    Console.WriteLine("Type: " + revision.RevisionType);
    Console.WriteLine("Author: " + revision.Author);
    Console.WriteLine("Date: " + revision.DateTime);
    Console.WriteLine("Revision text: " + revision.ParentNode.ToString(SaveFormat.Text));
}
```

โค้ดนี้จะพิมพ์ประเภทการแก้ไข ผู้เขียน วันที่ และข้อความไปยังคอนโซล

## ขั้นตอนที่ 4: ตรวจสอบกลุ่มการแก้ไข

บางครั้งการแก้ไขจะถูกจัดกลุ่ม เราจำเป็นต้องตรวจสอบว่าการแก้ไขนั้นอยู่ในกลุ่มหรือไม่ และหากเป็นเช่นนั้น แสดงข้อความของกลุ่ม

```csharp
foreach (Revision revision in doc.Revisions)
{
    string groupText = revision.Group != null
        ? "Revision group text: " + revision.Group.Text
        : "The revision does not belong to any group";

    Console.WriteLine(groupText);
}
```

สไนปเป็ตนี้จะพิมพ์ข้อความกลุ่มหากการแก้ไขเป็นส่วนหนึ่งของกลุ่มหรือระบุว่าไม่ได้อยู่ในกลุ่มใดๆ

## บทสรุป

และแล้วคุณก็ทำได้! ด้วยการทำตามขั้นตอนเหล่านี้ คุณจะได้รับข้อมูลโดยละเอียดเกี่ยวกับการแก้ไขในเอกสาร Word ได้อย่างง่ายดายโดยใช้ Aspose.Words สำหรับ .NET เครื่องมืออันทรงพลังนี้ทำให้การจัดการและติดตามการเปลี่ยนแปลงเป็นเรื่องง่าย และทำให้มั่นใจว่าโครงการร่วมมือของคุณดำเนินไปอย่างราบรื่น

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
เป็นไลบรารี .NET ที่ทรงพลังสำหรับการสร้าง แก้ไข แปลง และพิมพ์เอกสาร Word ด้วยโปรแกรม

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET ร่วมกับภาษา .NET อื่นๆ ได้หรือไม่
แน่นอน! คุณสามารถใช้ได้กับภาษา .NET ใดๆ ก็ได้ รวมถึง C#, VB.NET และ ASP.NET

### ฉันจะได้รับรุ่นทดลองใช้งาน Aspose.Words สำหรับ .NET ฟรีได้อย่างไร
 คุณสามารถรับสิทธิ์ทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.Words สำหรับ .NET หรือไม่?
 ใช่ Aspose.Words สำหรับ .NET ต้องมีใบอนุญาตจึงจะใช้งานได้เต็มรูปแบบ คุณสามารถซื้อได้[ที่นี่](https://purchase.aspose.com/buy) หรือรับใบอนุญาตชั่วคราว[ที่นี่](https://purchase.aspose.com/temporary-license/).

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด
 เอกสารรายละเอียดมีให้[ที่นี่](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
