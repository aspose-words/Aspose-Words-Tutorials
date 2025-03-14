---
title: ตั้งค่าเวอร์ชัน Ms Word
linktitle: ตั้งค่าเวอร์ชัน Ms Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีตั้งค่าเวอร์ชัน MS Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือโดยละเอียดของเรา เหมาะสำหรับนักพัฒนาที่ต้องการปรับปรุงการจัดการเอกสารให้มีประสิทธิภาพ

weight: 10
url: /th/net/programming-with-loadoptions/set-ms-word-version/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าเวอร์ชัน Ms Word

## การแนะนำ

คุณเคยพบว่าคุณต้องทำงานกับเอกสาร MS Word เวอร์ชันเฉพาะแต่ไม่รู้ว่าต้องตั้งค่าอย่างไรในเชิงโปรแกรมหรือไม่? คุณไม่ได้เป็นคนเดียว! ในบทช่วยสอนนี้ เราจะแนะนำขั้นตอนการตั้งค่าเวอร์ชัน MS Word โดยใช้ Aspose.Words สำหรับ .NET ซึ่งเป็นเครื่องมือที่ยอดเยี่ยมที่ช่วยให้การจัดการเอกสาร Word เป็นเรื่องง่าย เราจะเจาะลึกรายละเอียดโดยแบ่งขั้นตอนแต่ละขั้นตอนเพื่อให้แน่ใจว่าคุณสามารถใช้งานได้ราบรื่น พร้อมเริ่มต้นหรือยัง? มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้นเขียนโค้ด เรามาตรวจสอบก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

-  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณมีเวอร์ชันล่าสุด[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: คุณสามารถใช้ Visual Studio หรือ IDE ที่เข้ากันได้กับ .NET อื่น ๆ ได้
- ความรู้พื้นฐานเกี่ยวกับ C#: แม้ว่าเราจะทำให้มันเรียบง่าย แต่การทำความเข้าใจพื้นฐานเกี่ยวกับ C# เป็นสิ่งจำเป็น
- เอกสารตัวอย่าง: เตรียมเอกสาร Word ไว้ในไดเร็กทอรีเอกสารของคุณเพื่อวัตถุประสงค์ในการทดสอบ

## นำเข้าเนมสเปซ

ก่อนที่คุณจะเริ่มเขียนโค้ด คุณจะต้องนำเข้าเนมสเปซที่จำเป็นก่อน โดยคุณสามารถทำได้ดังนี้:

```csharp
using Aspose.Words;
```

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอกสารของคุณ

สิ่งแรกที่ต้องทำคือระบุตำแหน่งที่ตั้งของเอกสารของคุณ ซึ่งเป็นสิ่งสำคัญมาก เนื่องจากคุณจะต้องโหลดและบันทึกเอกสารจากไดเร็กทอรีนี้ ลองนึกถึงการตั้งค่า GPS ก่อนออกเดินทาง

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## ขั้นตอนที่ 2: กำหนดค่าตัวเลือกการโหลด

ขั้นต่อไป คุณต้องกำหนดค่าตัวเลือกการโหลด นี่คือจุดที่ความมหัศจรรย์เกิดขึ้น! การตั้งค่าเวอร์ชัน MS Word ในตัวเลือกการโหลด คุณกำลังแจ้งให้ Aspose.Words ทราบว่าจะเลียนแบบ Word เวอร์ชันใดเมื่อโหลดเอกสาร

```csharp
// กำหนดค่าตัวเลือกการโหลดด้วยคุณสมบัติ "ตั้งค่าเวอร์ชัน MS Word"
LoadOptions loadOptions = new LoadOptions { MswVersion = MsWordVersion.Word2010 };
```

ลองนึกภาพว่าคุณอยู่ที่ร้านกาแฟและกำลังตัดสินใจว่าจะเลือกเบลนด์แบบไหน ในทำนองเดียวกัน คุณกำลังเลือกเวอร์ชันของ Word ที่คุณต้องการใช้งาน

## ขั้นตอนที่ 3: โหลดเอกสาร

เมื่อคุณตั้งค่าตัวเลือกการโหลดเรียบร้อยแล้ว ก็ถึงเวลาโหลดเอกสารของคุณ ขั้นตอนนี้จะคล้ายกับการเปิดเอกสารใน Word เวอร์ชันเฉพาะ

```csharp
// โหลดเอกสารด้วย MS Word เวอร์ชันที่ระบุ
Document doc = new Document(dataDir + "Document.docx", loadOptions);
```

## ขั้นตอนที่ 4: บันทึกเอกสาร

ในที่สุด เมื่อโหลดเอกสารและแก้ไขตามต้องการแล้ว คุณสามารถบันทึกเอกสารได้ ซึ่งก็เหมือนกับการกดปุ่มบันทึกหลังจากแก้ไขใน Word

```csharp
// บันทึกเอกสาร
doc.Save(dataDir + "WorkingWithLoadOptions.SetMsWordVersion.docx");
```

## บทสรุป

การตั้งค่าเวอร์ชัน MS Word ใน Aspose.Words สำหรับ .NET เป็นเรื่องง่ายเมื่อคุณแบ่งขั้นตอนต่างๆ ออกเป็นขั้นตอนที่จัดการได้ โดยการกำหนดค่าตัวเลือกการโหลด การโหลดเอกสาร และการบันทึก คุณสามารถมั่นใจได้ว่าเอกสารของคุณจะได้รับการจัดการอย่างที่คุณต้องการ คำแนะนำนี้ให้แนวทางที่ชัดเจนในการบรรลุเป้าหมายดังกล่าว ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### ฉันสามารถตั้งค่าเวอร์ชันอื่นนอกเหนือจาก Word 2010 ได้หรือไม่?
 ใช่ คุณสามารถตั้งค่าเวอร์ชันต่างๆ เช่น Word 2007, Word 2013 เป็นต้น โดยการเปลี่ยนแปลง`MsWordVersion` คุณสมบัติ.

### Aspose.Words เข้ากันได้กับ .NET Core ได้หรือไม่
แน่นอน! Aspose.Words รองรับ .NET Framework, .NET Core และ .NET 5+

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.Words หรือไม่?
 คุณสามารถใช้รุ่นทดลองใช้งานฟรีได้ แต่หากต้องการใช้คุณสมบัติเต็มรูปแบบ คุณจะต้องมีใบอนุญาต[รับใบอนุญาตชั่วคราวที่นี่](https://purchase.aspose.com/temporary-license/).

### ฉันสามารถจัดการคุณลักษณะอื่นๆ ของเอกสาร Word โดยใช้ Aspose.Words ได้หรือไม่
ใช่ Aspose.Words เป็นไลบรารีที่ครอบคลุมซึ่งช่วยให้คุณสามารถจัดการกับเอกสาร Word ได้แทบทุกด้าน

### ฉันสามารถหาตัวอย่างและเอกสารเพิ่มเติมได้ที่ไหน
 ตรวจสอบออก[เอกสารประกอบ](https://reference.aspose.com/words/net/) สำหรับตัวอย่างเพิ่มเติมและข้อมูลโดยละเอียด

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
