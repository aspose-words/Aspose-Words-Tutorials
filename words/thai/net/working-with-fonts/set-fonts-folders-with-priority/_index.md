---
title: ตั้งค่าโฟลเดอร์แบบอักษรตามลำดับความสำคัญ
linktitle: ตั้งค่าโฟลเดอร์แบบอักษรตามลำดับความสำคัญ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีตั้งค่าโฟลเดอร์แบบอักษรตามลำดับความสำคัญในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET คำแนะนำของเราจะช่วยให้เอกสารของคุณแสดงผลได้สมบูรณ์แบบทุกครั้ง
weight: 10
url: /th/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าโฟลเดอร์แบบอักษรตามลำดับความสำคัญ

## การแนะนำ

ในโลกของการจัดการเอกสาร การตั้งค่าโฟลเดอร์ฟอนต์แบบกำหนดเองสามารถสร้างความแตกต่างอย่างมากในการทำให้เอกสารของคุณแสดงผลได้อย่างสมบูรณ์แบบ ไม่ว่าจะดูจากที่ใดก็ตาม วันนี้ เราจะเจาะลึกว่าคุณสามารถตั้งค่าโฟลเดอร์ฟอนต์ตามลำดับความสำคัญในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET ได้อย่างไร คู่มือฉบับสมบูรณ์นี้จะแนะนำคุณในแต่ละขั้นตอนเพื่อให้กระบวนการราบรื่นที่สุด

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้น เรามาตรวจสอบให้แน่ใจก่อนว่าเรามีทุกสิ่งที่จำเป็น นี่คือรายการตรวจสอบอย่างรวดเร็ว:

-  Aspose.Words สำหรับ .NET: คุณต้องติดตั้งไลบรารีนี้ก่อน หากคุณยังไม่มี คุณสามารถทำได้[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณมีสภาพแวดล้อมการพัฒนา .NET ที่ใช้งานได้ เช่น Visual Studio
-  ไดเรกทอรีเอกสาร: ตรวจสอบให้แน่ใจว่าคุณมีไดเรกทอรีสำหรับเอกสารของคุณ สำหรับตัวอย่างของเรา เราจะใช้`"YOUR DOCUMENT DIRECTORY"` เป็นตัวแทนสำหรับเส้นทางนี้

## นำเข้าเนมสเปซ

สิ่งแรกที่ต้องทำคือนำเข้าเนมสเปซที่จำเป็น เนมสเปซเหล่านี้มีความจำเป็นต่อการเข้าถึงคลาสและเมธอดที่ Aspose.Words จัดเตรียมไว้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

ต่อไปเรามาดูแต่ละขั้นตอนในการกำหนดโฟลเดอร์แบบอักษรตามลำดับความสำคัญกัน

## ขั้นตอนที่ 1: ตั้งค่าแหล่งที่มาของแบบอักษรของคุณ

ในการเริ่มต้น คุณจะต้องกำหนดแหล่งที่มาของฟอนต์ ซึ่งคุณจะต้องแจ้งให้ Aspose.Words ทราบว่าควรค้นหาฟอนต์ที่ใด คุณสามารถระบุโฟลเดอร์ฟอนต์หลายโฟลเดอร์และกำหนดลำดับความสำคัญของโฟลเดอร์เหล่านั้นได้

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

ในตัวอย่างนี้ เราจะตั้งค่าแหล่งแบบอักษรสองแหล่ง:
- SystemFontSource: นี่คือแหล่งฟอนต์เริ่มต้นที่รวมฟอนต์ทั้งหมดที่ติดตั้งอยู่ในระบบของคุณ
-  FolderFontSource: นี่เป็นโฟลเดอร์แบบอักษรที่กำหนดเองที่ตั้งอยู่ที่`C:\\MyFonts\\` . การ`true` พารามิเตอร์ระบุว่าควรสแกนโฟลเดอร์นี้ซ้ำๆ และ`1` กำหนดลำดับความสำคัญของมัน

## ขั้นตอนที่ 2: โหลดเอกสารของคุณ

ขั้นตอนต่อไปคือโหลดเอกสารที่คุณต้องการใช้งาน ตรวจสอบให้แน่ใจว่าเอกสารนั้นอยู่ในไดเร็กทอรีที่คุณระบุ

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 บรรทัดโค้ดนี้โหลดเอกสารชื่อ`Rendering.docx` จากไดเร็กทอรีเอกสารของคุณ

## ขั้นตอนที่ 3: บันทึกเอกสารของคุณด้วยการตั้งค่าแบบอักษรใหม่

สุดท้าย ให้บันทึกเอกสารของคุณ เมื่อคุณบันทึกเอกสาร Aspose.Words จะใช้การตั้งค่าแบบอักษรที่คุณระบุ

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

 การดำเนินการนี้จะบันทึกเอกสารเป็น PDF ในไดเร็กทอรีเอกสารของคุณโดยใช้ชื่อ`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้ตั้งค่าโฟลเดอร์ฟอนต์ตามลำดับความสำคัญสำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET โดยการระบุโฟลเดอร์ฟอนต์และลำดับความสำคัญที่กำหนดเอง คุณสามารถมั่นใจได้ว่าเอกสารของคุณจะแสดงผลอย่างสม่ำเสมอไม่ว่าจะดูจากที่ใดก็ตาม ซึ่งมีประโยชน์อย่างยิ่งในสภาพแวดล้อมที่ไม่มีการติดตั้งฟอนต์เฉพาะตามค่าเริ่มต้น

## คำถามที่พบบ่อย

### เหตุใดฉันจึงต้องตั้งค่าโฟลเดอร์ฟอนต์แบบกำหนดเอง?
การตั้งค่าโฟลเดอร์ฟอนต์แบบกำหนดเองจะช่วยให้แน่ใจว่าเอกสารของคุณแสดงอย่างถูกต้อง แม้ว่าจะใช้ฟอนต์ที่ไม่ได้ติดตั้งไว้ในระบบที่กำลังดูอยู่ก็ตาม

### ฉันสามารถตั้งค่าโฟลเดอร์ฟอนต์ที่กำหนดเองได้หลายโฟลเดอร์ไหม
ใช่ คุณสามารถระบุโฟลเดอร์ฟอนต์ได้หลายโฟลเดอร์ Aspose.Words ช่วยให้คุณกำหนดลำดับความสำคัญสำหรับแต่ละโฟลเดอร์ได้ เพื่อให้แน่ใจว่าจะพบฟอนต์ที่สำคัญที่สุดก่อน

### จะเกิดอะไรขึ้นถ้าแบบอักษรหายไปจากแหล่งที่มาที่ระบุทั้งหมด?
ถ้าแบบอักษรหายไปจากแหล่งที่ระบุทั้งหมด Aspose.Words จะใช้แบบอักษรสำรองเพื่อให้แน่ใจว่าเอกสารยังคงสามารถอ่านได้

### ฉันสามารถเปลี่ยนลำดับความสำคัญของแบบอักษรระบบได้หรือไม่
แบบอักษรของระบบจะรวมอยู่เสมอตามค่าเริ่มต้น แต่คุณสามารถตั้งค่าลำดับความสำคัญสัมพันธ์กับโฟลเดอร์แบบอักษรที่กำหนดเองของคุณได้

### เป็นไปได้ไหมที่จะใช้เส้นทางเครือข่ายสำหรับโฟลเดอร์แบบอักษรที่กำหนดเอง?
ใช่ คุณสามารถระบุเส้นทางเครือข่ายเป็นโฟลเดอร์แบบอักษรที่กำหนดเองได้ ทำให้คุณสามารถรวมทรัพยากรแบบอักษรไว้ที่ตำแหน่งเครือข่ายได้
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
