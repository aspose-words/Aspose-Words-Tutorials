---
title: การป้องกันการอ่านอย่างเดียวในเอกสาร Word
linktitle: การป้องกันการอ่านอย่างเดียวในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีปกป้องเอกสาร Word ของคุณโดยใช้การป้องกันแบบอ่านอย่างเดียวโดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเรา
weight: 10
url: /th/net/document-protection/read-only-protection/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การป้องกันการอ่านอย่างเดียวในเอกสาร Word

## การแนะนำ

เมื่อต้องจัดการเอกสาร Word บางครั้งคุณจำเป็นต้องทำให้เอกสารเป็นแบบอ่านอย่างเดียวเพื่อปกป้องเนื้อหา ไม่ว่าจะเป็นการแชร์ข้อมูลสำคัญโดยไม่ต้องเสี่ยงต่อการแก้ไขโดยไม่ได้ตั้งใจ หรือเพื่อรับรองความสมบูรณ์ของเอกสารกฎหมาย การป้องกันแบบอ่านอย่างเดียวถือเป็นคุณสมบัติที่มีประโยชน์ ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีนำการป้องกันแบบอ่านอย่างเดียวไปใช้ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เราจะอธิบายแต่ละขั้นตอนอย่างละเอียดและน่าสนใจ เพื่อให้คุณทำตามได้ง่าย

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเจาะลึกโค้ด มีข้อกำหนดเบื้องต้นบางประการที่คุณต้องมี:

1.  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Aspose.Words สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาโดยติดตั้ง .NET Visual Studio เป็นตัวเลือกที่ดี
3. ความเข้าใจพื้นฐานเกี่ยวกับ C#: บทช่วยสอนนี้ถือว่าคุณมีความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ

ก่อนอื่น เรามาตรวจสอบให้แน่ใจก่อนว่าเราได้นำเข้าเนมสเปซที่จำเป็นแล้ว ซึ่งถือเป็นสิ่งสำคัญมาก เนื่องจากช่วยให้เราเข้าถึงคลาสและเมธอดที่จำเป็นจาก Aspose.Words สำหรับ .NET ได้

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: ตั้งค่าเอกสาร

ในขั้นตอนนี้ เราจะสร้างเอกสารใหม่และเครื่องมือสร้างเอกสาร ซึ่งถือเป็นรากฐานสำหรับการดำเนินงานของเรา

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// เขียนข้อความบางอย่างลงในเอกสาร
builder.Write("Open document as read-only");
```

คำอธิบาย:

- เราเริ่มต้นด้วยการกำหนดเส้นทางไดเร็กทอรีที่เอกสารจะถูกบันทึก
-  ใหม่`Document` วัตถุถูกสร้างขึ้นและ`DocumentBuilder` ก็มีส่วนเกี่ยวข้องกับมัน
- เราใช้โปรแกรมสร้างเพื่อเพิ่มบรรทัดข้อความเรียบง่ายลงในเอกสาร

## ขั้นตอนที่ 2: ตั้งรหัสผ่านการป้องกันการเขียน

ขั้นต่อไป เราต้องตั้งรหัสผ่านเพื่อป้องกันการเขียน โดยรหัสผ่านสามารถมีความยาวได้ไม่เกิน 15 ตัวอักษร

```csharp
// กรอกรหัสผ่านที่มีความยาวไม่เกิน 15 ตัวอักษร
doc.WriteProtection.SetPassword("MyPassword");
```

คำอธิบาย:

-  การ`SetPassword` วิธีการถูกเรียกใช้งานบน`WriteProtection` ทรัพย์สินของเอกสาร
- เราให้รหัสผ่าน ("MyPassword" ในกรณีนี้) ซึ่งจะต้องใช้ในการลบการป้องกัน

## ขั้นตอนที่ 3: เปิดใช้งานคำแนะนำแบบอ่านอย่างเดียว

ในขั้นตอนนี้ เราแนะนำให้เปิดเอกสารแบบอ่านอย่างเดียว ซึ่งหมายความว่า เมื่อเปิดเอกสาร ระบบจะแจ้งให้ผู้ใช้เปิดเอกสารแบบอ่านอย่างเดียว

```csharp
// แนะนำให้สร้างเอกสารเป็นแบบอ่านอย่างเดียว
doc.WriteProtection.ReadOnlyRecommended = true;
```

คำอธิบาย:

-  การ`ReadOnlyRecommended` ทรัพย์สินถูกตั้งค่าเป็น`true`.
- ระบบจะแจ้งให้ผู้ใช้เปิดเอกสารในโหมดอ่านอย่างเดียว แม้ว่าพวกเขาจะเลือกที่จะละเว้นคำแนะนำก็ตาม

## ขั้นตอนที่ 4: ใช้การป้องกันแบบอ่านอย่างเดียว

ในที่สุด เราจะใช้การป้องกันแบบอ่านอย่างเดียวกับเอกสาร ขั้นตอนนี้จะบังคับใช้การป้องกัน

```csharp
// ใช้การป้องกันการเขียนเป็นแบบอ่านอย่างเดียว
doc.Protect(ProtectionType.ReadOnly);
```

คำอธิบาย:

-  การ`Protect` วิธีการถูกเรียกใช้งานบนเอกสารด้วย`ProtectionType.ReadOnly` เป็นข้อโต้แย้ง
- วิธีการนี้บังคับใช้การป้องกันแบบอ่านอย่างเดียว โดยป้องกันการแก้ไขเอกสารใด ๆ โดยไม่ต้องใช้รหัสผ่าน

## ขั้นตอนที่ 5: บันทึกเอกสาร

ขั้นตอนสุดท้ายคือการบันทึกเอกสารโดยใช้การตั้งค่าการป้องกันที่ใช้

```csharp
// บันทึกเอกสารที่ได้รับการป้องกัน
doc.Save(dataDir + "DocumentProtection.ReadOnlyProtection.docx");
```

คำอธิบาย:

-  การ`Save` เรียกใช้วิธีการบนเอกสารโดยระบุเส้นทางและชื่อของไฟล์
- เอกสารจะได้รับการบันทึกโดยมีระบบการป้องกันแบบอ่านอย่างเดียว

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณได้สร้างเอกสาร Word ที่ได้รับการป้องกันแบบอ่านอย่างเดียวโดยใช้ Aspose.Words สำหรับ .NET สำเร็จแล้ว คุณลักษณะนี้จะช่วยให้มั่นใจว่าเนื้อหาของเอกสารของคุณจะยังคงอยู่ครบถ้วนและไม่มีการเปลี่ยนแปลงใดๆ ช่วยเพิ่มระดับความปลอดภัยอีกชั้น ไม่ว่าคุณจะแชร์ข้อมูลที่ละเอียดอ่อนหรือเอกสารทางกฎหมาย การป้องกันแบบอ่านอย่างเดียวเป็นเครื่องมือที่ต้องมีในคลังอาวุธการจัดการเอกสารของคุณ

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข แปลง และปกป้องเอกสาร Word ด้วยโปรแกรมโดยใช้ C# หรือภาษา .NET อื่นๆ

### ฉันสามารถลบการป้องกันแบบอ่านอย่างเดียวจากเอกสารได้หรือไม่
 ใช่ คุณสามารถลบการป้องกันแบบอ่านอย่างเดียวได้โดยใช้`Unprotect` วิธีการและการระบุรหัสผ่านที่ถูกต้อง

### รหัสผ่านที่ตั้งไว้ในเอกสารมีการเข้ารหัสหรือเปล่า?
ใช่ Aspose.Words เข้ารหัสรหัสผ่านเพื่อประกันความปลอดภัยของเอกสารที่ได้รับการป้องกัน

### ฉันสามารถใช้การป้องกันประเภทอื่นโดยใช้ Aspose.Words สำหรับ .NET ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET รองรับการป้องกันประเภทต่างๆ รวมถึงการอนุญาตเฉพาะความคิดเห็น การกรอกแบบฟอร์ม หรือการติดตามการเปลี่ยนแปลง

### มี Aspose.Words สำหรับ .NET ให้ทดลองใช้งานฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
