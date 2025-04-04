---
title: ขีดฆ่า
linktitle: ขีดฆ่า
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีใช้การจัดรูปแบบขีดทับกับข้อความโดยใช้ Aspose.Words สำหรับ .NET ด้วยคำแนะนำทีละขั้นตอนของเรา พัฒนาทักษะการประมวลผลเอกสารของคุณ
weight: 10
url: /th/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ขีดฆ่า

## การแนะนำ

ยินดีต้อนรับสู่คู่มือโดยละเอียดเกี่ยวกับวิธีการใช้การจัดรูปแบบขีดทับกับข้อความโดยใช้ Aspose.Words สำหรับ .NET หากคุณกำลังมองหาวิธีเพิ่มพูนทักษะการประมวลผลเอกสารและเพิ่มสัมผัสที่เป็นเอกลักษณ์ให้กับข้อความของคุณ คุณมาถูกที่แล้ว มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.Words สำหรับ .NET: ดาวน์โหลด[ที่นี่](https://releases.aspose.com/words/net/).
- .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework ไว้ในระบบของคุณแล้ว
- สภาพแวดล้อมการพัฒนา: IDE เช่น Visual Studio
- ความรู้พื้นฐานเกี่ยวกับ C#: มีความคุ้นเคยกับการเขียนโปรแกรม C# เป็นสิ่งจำเป็น

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็น ซึ่งเป็นสิ่งสำคัญสำหรับการเข้าถึงไลบรารี Aspose.Words และฟีเจอร์ต่างๆ

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน DocumentBuilder

 การ`DocumentBuilder` class เป็นเครื่องมืออันทรงพลังใน Aspose.Words ที่ช่วยให้คุณสามารถเพิ่มเนื้อหาลงในเอกสารของคุณได้อย่างง่ายดาย

```csharp
// เริ่มต้นใช้งาน DocumentBuilder
DocumentBuilder builder = new DocumentBuilder();
```

## ขั้นตอนที่ 2: ตั้งค่าคุณสมบัติ Strikethrough

ตอนนี้ ลองใช้คุณสมบัติการขีดฆ่ากับข้อความของเรา ซึ่งเกี่ยวข้องกับการตั้งค่า`StrikeThrough` ทรัพย์สินของ`Font` คัดค้าน`true`.

```csharp
// ให้ข้อความถูกขีดฆ่า
builder.Font.StrikeThrough = true;
```

## ขั้นตอนที่ 3: เขียนข้อความโดยขีดฆ่า

 เมื่อตั้งค่าคุณสมบัติการขีดฆ่าแล้ว ตอนนี้เราสามารถเพิ่มข้อความของเราได้แล้ว`Writeln` วิธีการจะเพิ่มข้อความลงในเอกสาร

```csharp
// เขียนข้อความโดยใช้การขีดฆ่า
builder.Writeln("This text will be StrikeThrough");
```

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้เพิ่มรูปแบบการขีดฆ่าลงในข้อความของคุณสำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ไลบรารีอันทรงพลังนี้เปิดโลกแห่งความเป็นไปได้สำหรับการประมวลผลและปรับแต่งเอกสาร ไม่ว่าคุณจะกำลังสร้างรายงาน จดหมาย หรือเอกสารประเภทอื่นใด การเชี่ยวชาญคุณสมบัติเหล่านี้จะช่วยเพิ่มประสิทธิภาพการทำงานและคุณภาพของผลลัพธ์ของคุณอย่างไม่ต้องสงสัย

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words for .NET เป็นไลบรารีการประมวลผลเอกสารอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง จัดการ และแปลงเอกสาร Word ได้โดยการใช้โปรแกรม

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET ในโครงการเชิงพาณิชย์ได้หรือไม่
 ใช่ คุณสามารถใช้ Aspose.Words สำหรับโปรเจ็กต์เชิงพาณิชย์ได้ สำหรับตัวเลือกการซื้อ โปรดไปที่[หน้าซื้อ](https://purchase.aspose.com/buy).

### มี Aspose.Words สำหรับ .NET ให้ทดลองใช้งานฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร
คุณสามารถรับการสนับสนุนจากชุมชน Aspose และผู้เชี่ยวชาญได้ที่[ฟอรั่มสนับสนุน](https://forum.aspose.com/c/words/8).

### ฉันสามารถใช้ตัวเลือกการจัดรูปแบบข้อความอื่นโดยใช้ Aspose.Words สำหรับ .NET ได้หรือไม่
แน่นอน! Aspose.Words สำหรับ .NET รองรับตัวเลือกการจัดรูปแบบข้อความมากมาย รวมถึงตัวหนา ตัวเอียง ขีดเส้นใต้ และอื่นๆ
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
