---
title: แทรกวัตถุ Ole เป็นไอคอนโดยใช้สตรีม
linktitle: แทรกวัตถุ Ole เป็นไอคอนโดยใช้สตรีม
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการแทรกวัตถุ OLE เป็นไอคอนโดยใช้สตรีมด้วย Aspose.Words สำหรับ .NET ในบทช่วยสอนทีละขั้นตอนโดยละเอียดนี้
weight: 10
url: /th/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon-using-stream/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกวัตถุ Ole เป็นไอคอนโดยใช้สตรีม

## การแนะนำ

ในบทช่วยสอนนี้ เราจะมาเจาะลึกฟีเจอร์สุดเจ๋งของ Aspose.Words สำหรับ .NET: การแทรกวัตถุ OLE (Object Linking and Embedding) เป็นไอคอนโดยใช้สตรีม ไม่ว่าคุณจะฝังงานนำเสนอ PowerPoint สเปรดชีต Excel หรือไฟล์ประเภทอื่น คู่มือนี้จะแสดงให้คุณเห็นว่าต้องทำอย่างไร พร้อมจะเริ่มต้นหรือยัง มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้นเขียนโค้ด มีบางสิ่งที่คุณต้องมี:

-  Aspose.Words สำหรับ .NET: หากคุณยังไม่ได้ทำ[ดาวน์โหลด](https://releases.aspose.com/words/net/) และติดตั้ง Aspose.Words สำหรับ .NET
- สภาพแวดล้อมการพัฒนา: Visual Studio หรือสภาพแวดล้อมการพัฒนา C# อื่นๆ
- ไฟล์อินพุต: ไฟล์ที่คุณต้องการฝัง (เช่น งานนำเสนอ PowerPoint) และรูปภาพไอคอน

## นำเข้าเนมสเปซ

ในการเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้นำเข้าเนมสเปซที่จำเป็นในโครงการของคุณแล้ว:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

มาแบ่งกระบวนการออกเป็นขั้นตอนๆ เพื่อให้ง่ายต่อการปฏิบัติตาม

## ขั้นตอนที่ 1: สร้างเอกสารใหม่

ขั้นแรกเราจะสร้างเอกสารใหม่และตัวสร้างเอกสารเพื่อใช้งานกับเอกสารนั้น

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 คิดถึง`Document` เป็นผืนผ้าใบเปล่าของคุณและ`DocumentBuilder` เป็นพู่กันของคุณ เรากำลังจัดเตรียมเครื่องมือของเราเพื่อเริ่มสร้างผลงานชิ้นเอกของเรา

## ขั้นตอนที่ 2: เตรียมสตรีม

ขั้นต่อไป เราต้องเตรียมสตรีมหน่วยความจำที่มีไฟล์ที่เราต้องการฝัง ในตัวอย่างนี้ เราจะฝังงานนำเสนอ PowerPoint

```csharp
using (MemoryStream stream = new MemoryStream(File.ReadAllBytes("Path_to_your_directory/Presentation.pptx")))
{
```

ขั้นตอนนี้เหมือนกับการโหลดสีลงบนแปรง เรากำลังเตรียมไฟล์ให้พร้อมสำหรับการฝังสี

## ขั้นตอนที่ 3: แทรกวัตถุ OLE เป็นไอคอน

ตอนนี้เราจะใช้ตัวสร้างเอกสารเพื่อแทรกวัตถุ OLE ลงในเอกสาร เราจะระบุสตรีมไฟล์, ProgID สำหรับประเภทของไฟล์ (ในกรณีนี้คือ "แพ็กเกจ"), เส้นทางไปยังภาพไอคอน และป้ายกำกับสำหรับไฟล์ที่ฝังไว้

```csharp
builder.InsertOleObjectAsIcon(stream, "Package", "Path_to_your_directory/Logo icon.ico", "My embedded file");
}
```

นี่คือจุดที่เวทมนตร์เกิดขึ้น! เรากำลังฝังไฟล์และแสดงเป็นไอคอนภายในเอกสาร

## ขั้นตอนที่ 4: บันทึกเอกสาร

สุดท้ายเราบันทึกเอกสารไปยังเส้นทางที่ระบุ

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIconUsingStream.docx");
```

ขั้นตอนนี้เหมือนกับการใส่ภาพวาดที่เสร็จแล้วลงในกรอบและแขวนไว้บนผนัง ตอนนี้เอกสารของคุณก็พร้อมใช้งานแล้ว!

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณได้ฝังวัตถุ OLE เป็นไอคอนในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ฟีเจอร์อันทรงพลังนี้สามารถช่วยให้คุณสร้างเอกสารแบบไดนามิกและโต้ตอบได้อย่างง่ายดาย ไม่ว่าคุณจะฝังงานนำเสนอ สเปรดชีต หรือไฟล์อื่นๆ Aspose.Words ก็ทำให้เป็นเรื่องง่าย ลองใช้ดู แล้วดูความแตกต่างที่มันสร้างให้กับเอกสารของคุณ!

## คำถามที่พบบ่อย

### ฉันสามารถฝังไฟล์ประเภทต่างๆ ด้วยวิธีนี้ได้หรือไม่?
ใช่ คุณสามารถฝังประเภทไฟล์ใดๆ ที่ได้รับการรองรับโดย OLE รวมถึง Word, Excel, PowerPoint และอื่นๆ อีกมากมาย

### ฉันต้องมีใบอนุญาตพิเศษในการใช้ Aspose.Words สำหรับ .NET หรือไม่
 ใช่ Aspose.Words สำหรับ .NET ต้องมีใบอนุญาต คุณสามารถรับได้[ทดลองใช้งานฟรี](https://releases.aspose.com/) หรือซื้อ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อการทดสอบ

### ฉันสามารถปรับแต่งไอคอนที่ใช้สำหรับวัตถุ OLE ได้หรือไม่
 แน่นอน! คุณสามารถใช้ไฟล์รูปภาพใดๆ สำหรับไอคอนได้โดยระบุเส้นทางใน`InsertOleObjectAsIcon` วิธี.

### จะเกิดอะไรขึ้นถ้าเส้นทางไฟล์หรือไอคอนไม่ถูกต้อง?
วิธีการนี้จะส่งข้อยกเว้น ตรวจสอบให้แน่ใจว่าเส้นทางไปยังไฟล์ของคุณถูกต้องเพื่อหลีกเลี่ยงข้อผิดพลาด

### สามารถเชื่อมโยงวัตถุที่ฝังไว้แทนการฝังลงไปได้หรือไม่?
ใช่ Aspose.Words อนุญาตให้คุณแทรกวัตถุ OLE ที่เชื่อมโยง ซึ่งอ้างอิงไฟล์โดยไม่ต้องฝังเนื้อหา
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
