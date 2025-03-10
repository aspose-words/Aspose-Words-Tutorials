---
title: แทรกเขตข้อมูลผสานโดยใช้ DOM
linktitle: แทรกเขตข้อมูลผสานโดยใช้ DOM
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีแทรกและกำหนดค่าเขตข้อมูลผสานในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยบทช่วยสอนทีละขั้นตอนที่ครอบคลุมนี้
weight: 10
url: /th/net/working-with-fields/insert-merge-field-using-dom/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แทรกเขตข้อมูลผสานโดยใช้ DOM

## การแนะนำ

หากคุณกำลังทำงานกับการประมวลผลเอกสารใน .NET คุณคงเคยพบกับ Aspose.Words ซึ่งเป็นไลบรารีอันทรงพลังที่มีคุณลักษณะมากมายสำหรับการจัดการเอกสาร Word ด้วยโปรแกรม ในบทช่วยสอนนี้ เราจะเน้นที่คุณลักษณะเฉพาะอย่างหนึ่ง: การแทรกฟิลด์ผสานโดยใช้ Document Object Model (DOM) ใน Aspose.Words สำหรับ .NET คู่มือนี้จะแนะนำคุณในทุกขั้นตอน ตั้งแต่การตั้งค่าสภาพแวดล้อมของคุณไปจนถึงการแทรกและอัปเดตฟิลด์ผสานในเอกสาร Word

## ข้อกำหนดเบื้องต้น

ก่อนจะเจาะลึกโค้ด ให้แน่ใจว่าคุณมีทุกสิ่งที่จำเป็นในการปฏิบัติตามบทช่วยสอนนี้

1. ความรู้พื้นฐานเกี่ยวกับ C#: คุณควรจะคุ้นเคยกับการเขียนโปรแกรม C#
2. ติดตั้ง Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio หรือ IDE C# อื่น ๆ ไว้ในเครื่องของคุณแล้ว
3.  Aspose.Words สำหรับ .NET: ดาวน์โหลดและติดตั้ง Aspose.Words เวอร์ชันล่าสุดสำหรับ .NET จาก[การเปิดตัว](https://releases.aspose.com/words/net/).
4.  ใบอนุญาตที่ถูกต้อง: หากคุณไม่มีใบอนุญาต คุณสามารถขอรับได้[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อการประเมินผล

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

ขั้นแรกเรามาตั้งค่าโปรเจ็กต์ใหม่ใน Visual Studio กันก่อน

1. เปิด Visual Studio
2. สร้างโปรเจ็กต์ใหม่: ไปที่ไฟล์ > ใหม่ > โปรเจ็กต์ เลือกแอปคอนโซล C#
3. ตั้งชื่อโครงการของคุณ: ตั้งชื่อโครงการของคุณให้มีความหมายและคลิกสร้าง

## ขั้นตอนที่ 2: ติดตั้ง Aspose.Words

หากต้องการใช้ Aspose.Words คุณต้องเพิ่ม Aspose.Words ลงในโปรเจ็กต์ของคุณ ซึ่งสามารถทำได้ผ่านตัวจัดการแพ็กเกจ NuGet

1. เปิดตัวจัดการแพ็กเกจ NuGet: คลิกขวาที่โครงการของคุณใน Solution Explorer จากนั้นเลือกจัดการแพ็กเกจ NuGet
2. ค้นหา Aspose.Words: ในตัวจัดการแพ็กเกจ NuGet ให้ค้นหา "Aspose.Words"
3. ติดตั้งแพ็คเกจ: คลิกติดตั้งเพื่อเพิ่ม Aspose.Words ลงในโปรเจ็กต์ของคุณ

## ขั้นตอนที่ 3: นำเข้าเนมสเปซ

หากต้องการเริ่มใช้ Aspose.Words คุณต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ โดยคุณสามารถทำได้ดังนี้:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

## ขั้นตอนที่ 4: เริ่มต้นเอกสารของคุณ

ตอนนี้ทุกอย่างตั้งค่าเสร็จเรียบร้อยแล้ว มาสร้างเอกสาร Word ใหม่และเริ่มต้นใช้งาน DocumentBuilder กัน

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// สร้างเอกสารและ DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 5: เลื่อนเคอร์เซอร์ไปที่ย่อหน้าที่ต้องการ

ต่อไปเราต้องย้ายเคอร์เซอร์ไปยังย่อหน้าเฉพาะในเอกสารที่เราต้องการแทรกเขตข้อมูลผสาน

```csharp
Paragraph para = (Paragraph) doc.GetChild(NodeType.Paragraph, 0, true);
builder.MoveTo(para);
```

## ขั้นตอนที่ 6: แทรกฟิลด์ผสาน

 การแทรกฟิลด์ผสานนั้นทำได้ง่าย เราจะใช้`InsertField` วิธีการของ`DocumentBuilder` ระดับ.

```csharp
// แทรกฟิลด์ผสานฟิลด์
FieldMergeField field = (FieldMergeField)builder.InsertField(FieldType.FieldMergeField, false);
```

## ขั้นตอนที่ 7: กำหนดค่าฟิลด์ผสาน

หลังจากแทรกเขตข้อมูลผสานแล้ว คุณสามารถตั้งค่าคุณสมบัติต่าง ๆ เพื่อกำหนดค่าตามความต้องการของคุณได้

```csharp
field.FieldName = "Test1";
field.TextBefore = "Test2";
field.TextAfter = "Test3";
field.IsMapped = true;
field.IsVerticalFormatting = true;
```

## ขั้นตอนที่ 8: อัปเดตและบันทึกเอกสาร

สุดท้าย ให้อัปเดตฟิลด์เพื่อให้แน่ใจว่าการตั้งค่าทั้งหมดถูกนำไปใช้ และบันทึกเอกสาร

```csharp
// อัพเดทข้อมูลสนาม
field.Update();

// บันทึกเอกสาร
doc.Save(dataDir + "InsertionChampMergeChamp.docx");
```

## บทสรุป

หากทำตามขั้นตอนเหล่านี้ คุณจะสามารถแทรกและกำหนดค่าฟิลด์ผสานในเอกสาร Word ได้อย่างง่ายดายโดยใช้ Aspose.Words สำหรับ .NET บทช่วยสอนนี้ครอบคลุมขั้นตอนสำคัญตั้งแต่การตั้งค่าสภาพแวดล้อมไปจนถึงการบันทึกเอกสารขั้นสุดท้าย ด้วย Aspose.Words คุณสามารถทำให้กระบวนการประมวลผลเอกสารที่ซับซ้อนเป็นอัตโนมัติ ทำให้แอปพลิเคชัน .NET ของคุณมีประสิทธิภาพและมีประสิทธิภาพมากขึ้น

## คำถามที่พบบ่อย

###  ฟิลด์ผสานคืออะไร?
เขตข้อมูลผสานคือตัวแทนในเอกสารที่สามารถแทนที่แบบไดนามิกด้วยข้อมูลจากแหล่งข้อมูล เช่น ฐานข้อมูลหรือไฟล์ CSV

###  ฉันสามารถใช้ Aspose.Words ได้ฟรีหรือไม่?
 Aspose.Words เสนอรุ่นทดลองใช้งานฟรีซึ่งคุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/)หากต้องการใช้ในระยะยาว คุณจำเป็นต้องซื้อใบอนุญาต

###  ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Words ได้อย่างไร
 คุณสามารถขอใบอนุญาตชั่วคราวได้จากเว็บไซต์ Aspose[ที่นี่](https://purchase.aspose.com/temporary-license/).

### Aspose.Words รองรับ .NET เวอร์ชันใดบ้าง?
Aspose.Words รองรับ .NET หลายเวอร์ชัน รวมถึง .NET Framework, .NET Core และ .NET Standard

###  ฉันสามารถค้นหาเอกสาร API สำหรับ Aspose.Words ได้ที่ไหน
 เอกสารประกอบ API พร้อมใช้งานแล้ว[ที่นี่](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
