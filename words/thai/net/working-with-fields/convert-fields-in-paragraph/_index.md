---
title: แปลงฟิลด์ในย่อหน้า
linktitle: แปลงฟิลด์ในย่อหน้า
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการแปลงฟิลด์ IF เป็นข้อความธรรมดาในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนโดยละเอียดนี้
weight: 10
url: /th/net/working-with-fields/convert-fields-in-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แปลงฟิลด์ในย่อหน้า

## การแนะนำ

คุณเคยพบว่าตัวเองติดอยู่ในใยของฟิลด์ในเอกสาร Word ของคุณหรือไม่ โดยเฉพาะอย่างยิ่งเมื่อคุณพยายามแปลงฟิลด์ IF ที่เป็นข้อความธรรมดาให้เป็นข้อความธรรมดา? ไม่ใช่คุณคนเดียวที่เป็นแบบนั้น วันนี้ เราจะมาเจาะลึกว่าคุณจะเชี่ยวชาญเรื่องนี้ได้อย่างไรด้วย Aspose.Words สำหรับ .NET ลองนึกภาพว่าคุณเป็นพ่อมดที่มีไม้กายสิทธิ์ที่สามารถแปลงฟิลด์ได้ด้วยการสะบัดโค้ดเพียงครั้งเดียว ฟังดูน่าสนใจใช่ไหม มาเริ่มต้นการเดินทางอันมหัศจรรย์นี้กันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้นการร่ายคาถาหรือการเข้ารหัส มีบางสิ่งที่คุณต้องมี ลองนึกถึงสิ่งเหล่านี้ว่าเป็นชุดเครื่องมือของพ่อมดของคุณ:

-  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารีแล้ว คุณสามารถรับได้จาก[ที่นี่](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา .NET: ไม่ว่าจะเป็น Visual Studio หรือ IDE อื่นๆ ให้เตรียมสภาพแวดล้อมของคุณให้พร้อม
- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับ C# เพียงเล็กน้อยก็จะเป็นประโยชน์มาก

## นำเข้าเนมสเปซ

ก่อนที่เราจะเจาะลึกโค้ด เรามาตรวจสอบให้แน่ใจก่อนว่าเราได้นำเข้าเนมสเปซที่จำเป็นทั้งหมดแล้ว ซึ่งก็เหมือนกับการรวบรวมหนังสือคาถาทั้งหมดของคุณก่อนจะร่ายคาถา

```csharp
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fields;
```

ตอนนี้เรามาอธิบายขั้นตอนการแปลงฟิลด์ IF ในย่อหน้าเป็นข้อความธรรมดากัน เราจะทำทีละขั้นตอนเพื่อให้ทำตามได้ง่าย

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสารของคุณ

สิ่งแรกที่ต้องทำคือกำหนดว่าเอกสารของคุณอยู่ที่ไหน ลองนึกถึงการตั้งค่าพื้นที่ทำงานของคุณดู

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## ขั้นตอนที่ 2: โหลดเอกสาร

ขั้นตอนต่อไปคือคุณต้องโหลดเอกสารที่คุณต้องการใช้งาน ซึ่งก็เหมือนกับการเปิดหนังสือคาถาไปที่หน้าที่ถูกต้อง

```csharp
// โหลดเอกสาร
Document doc = new Document(dataDir + "Linked fields.docx");
```

## ขั้นตอนที่ 3: ระบุฟิลด์ IF ในย่อหน้าสุดท้าย

ตอนนี้เราจะมาดูฟิลด์ IF ในย่อหน้าสุดท้ายของเอกสารกัน นี่คือจุดที่เวทมนตร์ที่แท้จริงเกิดขึ้น

```csharp
// แปลงฟิลด์ IF ให้เป็นข้อความธรรมดาในย่อหน้าสุดท้ายของเอกสาร
doc.FirstSection.Body.LastParagraph.Range.Fields
     .Where(f => f.Type == FieldType.FieldIf)
     .ToList()
     .ForEach(f => f.Unlink());
```

## ขั้นตอนที่ 4: บันทึกเอกสารที่แก้ไข

สุดท้ายนี้ ให้บันทึกเอกสารที่คุณแก้ไขใหม่ นี่คือที่ที่คุณสามารถชื่นชมผลงานของคุณและดูผลลัพธ์ของเวทมนตร์ของคุณ

```csharp
// บันทึกเอกสารที่แก้ไข
doc.Save(dataDir + "WorkingWithFields.TestFile.docx");
```

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้แปลงฟิลด์ IF เป็นข้อความธรรมดาสำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ซึ่งก็เหมือนกับการเปลี่ยนคาถาที่ซับซ้อนให้กลายเป็นคาถาที่เรียบง่าย ทำให้การจัดการเอกสารของคุณง่ายขึ้นมาก ดังนั้น ครั้งต่อไปที่คุณพบปัญหากับฟิลด์ที่ยุ่งเหยิง คุณจะรู้ว่าต้องทำอย่างไร ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพสำหรับการทำงานกับเอกสาร Word ด้วยโปรแกรม ช่วยให้คุณสามารถสร้าง แก้ไข และแปลงเอกสารได้โดยไม่ต้องติดตั้ง Microsoft Word

### ฉันสามารถใช้วิธีนี้เพื่อแปลงฟิลด์ประเภทอื่นได้หรือไม่
 ใช่ คุณสามารถปรับใช้วิธีนี้เพื่อแปลงฟิลด์ประเภทต่างๆ ได้โดยการเปลี่ยนแปลง`FieldType`.

### เป็นไปได้ไหมที่จะทำให้กระบวนการนี้เป็นแบบอัตโนมัติสำหรับเอกสารหลายฉบับ?
แน่นอน! คุณสามารถวนซ้ำผ่านไดเร็กทอรีของเอกสารและทำตามขั้นตอนเดียวกันกับเอกสารแต่ละฉบับได้

### จะเกิดอะไรขึ้นถ้าเอกสารไม่มีช่อง IF ใดๆ?
วิธีการนี้จะไม่มีการเปลี่ยนแปลงใดๆ เนื่องจากไม่มีฟิลด์ที่ต้องยกเลิกการเชื่อมโยง

### ฉันสามารถย้อนกลับการเปลี่ยนแปลงหลังจากยกเลิกการเชื่อมโยงฟิลด์ได้ไหม
ไม่ เมื่อยกเลิกการเชื่อมโยงฟิลด์และแปลงเป็นข้อความธรรมดาแล้ว คุณไม่สามารถเปลี่ยนกลับเป็นฟิลด์ได้
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
