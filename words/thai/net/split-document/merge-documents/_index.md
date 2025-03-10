---
title: รวมเอกสาร Word
linktitle: รวมเอกสาร
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีผสานเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนที่ครอบคลุมนี้ เหมาะอย่างยิ่งสำหรับการสร้างระบบอัตโนมัติให้กับเวิร์กโฟลว์เอกสารของคุณ
weight: 10
url: /th/net/split-document/merge-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# รวมเอกสาร Word

## การแนะนำ

คุณเคยพบว่าคุณจำเป็นต้องรวมเอกสาร Word หลายฉบับเข้าเป็นไฟล์เดียวหรือไม่ ไม่ว่าคุณจะกำลังรวบรวมรายงาน ประกอบโครงการ หรือเพียงแค่พยายามจัดระเบียบ การรวมเอกสารสามารถประหยัดเวลาและความพยายามของคุณได้มาก ด้วย Aspose.Words สำหรับ .NET กระบวนการนี้จะกลายเป็นเรื่องง่ายดาย ในบทช่วยสอนนี้ เราจะแนะนำวิธีรวมเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET โดยแบ่งขั้นตอนต่างๆ ออกเป็นส่วนๆ เพื่อให้คุณทำตามได้ง่าย เมื่อเสร็จสิ้น คุณจะรวมเอกสารได้อย่างมืออาชีพ!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึก เรามาตรวจสอบกันก่อนว่าคุณได้ทุกสิ่งที่คุณต้องการแล้ว:

1. ความรู้พื้นฐานเกี่ยวกับ C#: คุณควรจะคุ้นเคยกับรูปแบบและแนวคิดของ C#
2.  Aspose.Words สำหรับ .NET: ดาวน์โหลด[ที่นี่](https://releases.aspose.com/words/net/) หากคุณแค่กำลังสำรวจ คุณสามารถเริ่มต้นด้วย[ทดลองใช้งานฟรี](https://releases.aspose.com/).
3. Visual Studio: ควรใช้เวอร์ชันล่าสุดใดก็ได้ แต่ขอแนะนำให้ใช้เวอร์ชันล่าสุด
4. .NET Framework: ตรวจสอบให้แน่ใจว่ามีการติดตั้งไว้ในระบบของคุณแล้ว

เอาล่ะ ตอนนี้เราได้จัดเตรียมข้อกำหนดเบื้องต้นเรียบร้อยแล้ว มาเริ่มส่วนสนุกๆ กันเลย!

## นำเข้าเนมสเปซ

สิ่งแรกที่ต้องทำคือนำเข้าเนมสเปซที่จำเป็นสำหรับการใช้งาน Aspose.Words ซึ่งจะทำให้เราสามารถเข้าถึงคลาสและเมธอดทั้งหมดที่เราต้องการได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.LowCode;
```

เนมสเปซเหล่านี้มีความจำเป็นสำหรับการสร้าง เอกสาร การจัดการ และการบันทึกในรูปแบบที่แตกต่างกัน

## ขั้นตอนที่ 1: การตั้งค่าไดเรกทอรีเอกสาร

ก่อนที่เราจะเริ่มรวมเอกสาร เราจะต้องระบุไดเรกทอรีที่เก็บเอกสารของเราเสียก่อน วิธีนี้จะช่วยให้ Aspose.Words ค้นหาไฟล์ที่ต้องการรวมได้

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 ที่นี่เราตั้งค่าเส้นทางไปยังไดเรกทอรีที่เอกสาร Word ของคุณตั้งอยู่ แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางที่แท้จริง

## ขั้นตอนที่ 2: การผสานแบบง่ายๆ

 มาเริ่มกันด้วยการผสานแบบง่ายๆ เราจะผสานเอกสารสองฉบับเป็นฉบับเดียวโดยใช้`Merger.Merge` วิธี.

```csharp
Merger.Merge(dataDir + "MergedDocument.docx", new[] { dataDir + "Document1.docx", dataDir + "Document2.docx" });
```

 ในขั้นตอนนี้เราจะรวม`Document1.docx` และ`Document2.docx` ลงในไฟล์ใหม่ชื่อ`MergedDocument.docx`.

## ขั้นตอนที่ 3: การรวมกับตัวเลือกการบันทึก

บางครั้ง คุณอาจต้องการกำหนดตัวเลือกเฉพาะสำหรับเอกสารที่ผสาน เช่น การป้องกันด้วยรหัสผ่าน คุณสามารถทำได้ดังนี้:

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions { Password = "Aspose.Words" };
Merger.Merge(dataDir + "MergedWithPassword.docx", new[] { dataDir + "Document1.docx", dataDir + "Document2.docx" }, saveOptions, MergeFormatMode.KeepSourceFormatting);
```

โค้ดชิ้นนี้จะรวมเอกสารด้วยการป้องกันด้วยรหัสผ่าน ทำให้แน่ใจว่าเอกสารสุดท้ายจะปลอดภัย

## ขั้นตอนที่ 4: การผสานและบันทึกเป็น PDF

หากคุณต้องการรวมเอกสารและบันทึกผลลัพธ์เป็น PDF Aspose.Words จะทำให้เป็นเรื่องง่าย:

```csharp
Merger.Merge(dataDir + "MergedDocument.pdf", new[] { dataDir + "Document1.docx", dataDir + "Document2.docx" }, SaveFormat.Pdf, MergeFormatMode.KeepSourceLayout);
```

 ที่นี่เรารวมเข้าด้วยกัน`Document1.docx` และ`Document2.docx` และบันทึกผลลัพธ์เป็นไฟล์ PDF

## ขั้นตอนที่ 5: การสร้างอินสแตนซ์เอกสารจากเอกสารที่ผสาน

 บางครั้งคุณอาจต้องการทำงานกับเอกสารที่ผสานเพิ่มเติมก่อนบันทึก คุณสามารถสร้าง`Document` อินสแตนซ์จากเอกสารที่รวมกัน:

```csharp
Document doc = Merger.Merge(new[] { dataDir + "Document1.docx", dataDir + "Document2.docx" }, MergeFormatMode.MergeFormatting);
doc.Save(dataDir + "MergedDocumentInstance.docx");
```

 ในขั้นตอนนี้เราจะสร้าง`Document` อินสแตนซ์จากเอกสารที่ผสานกัน ช่วยให้สามารถจัดการเพิ่มเติมได้ก่อนบันทึก

## บทสรุป

 และแล้วคุณก็ได้เรียนรู้วิธีผสานเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET บทช่วยสอนนี้ครอบคลุมถึงการตั้งค่าสภาพแวดล้อมของคุณ การดำเนินการผสานแบบง่าย การผสานโดยใช้ตัวเลือกบันทึก การแปลงเอกสารที่ผสานเป็น PDF และการสร้างอินสแตนซ์เอกสารจากเอกสารที่ผสาน Aspose.Words นำเสนอคุณลักษณะต่างๆ มากมาย ดังนั้นอย่าลืมสำรวจดู[เอกสารประกอบ API](https://reference.aspose.com/words/net/) เพื่อปลดล็อคศักยภาพทั้งหมดของมัน

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?

Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง จัดการ และแปลงเอกสาร Word ได้ด้วยโปรแกรม เหมาะอย่างยิ่งสำหรับการทำงานที่เกี่ยวข้องกับเอกสารโดยอัตโนมัติ

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET ได้ฟรีหรือไม่?

 คุณสามารถลองใช้ Aspose.Words สำหรับ .NET ได้โดยใช้[ทดลองใช้งานฟรี](https://releases.aspose.com/)หากต้องการใช้ในระยะยาว คุณจำเป็นต้องซื้อใบอนุญาต

### ฉันจะจัดการกับการจัดรูปแบบที่แตกต่างกันในระหว่างการผสานได้อย่างไร

 Aspose.Words มีโหมดการผสานรูปแบบต่างๆ เช่น`KeepSourceFormatting` และ`MergeFormatting` อ้างอิงถึง[เอกสารประกอบ API](https://reference.aspose.com/words/net/) สำหรับคำแนะนำโดยละเอียด

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร

 คุณสามารถรับการสนับสนุนได้โดยการเยี่ยมชม[ฟอรั่มสนับสนุน Aspose](https://forum.aspose.com/c/words/8).

### ฉันสามารถรวมรูปแบบไฟล์อื่นด้วย Aspose.Words สำหรับ .NET ได้หรือไม่

ใช่ Aspose.Words รองรับการรวมไฟล์รูปแบบต่างๆ รวมถึง DOCX, PDF และ HTML
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
