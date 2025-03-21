---
title: การแทรกวัตถุ Ole ในเอกสาร Word
linktitle: การแทรกวัตถุ Ole ในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการแทรกวัตถุ OLE ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนนี้ ปรับปรุงเอกสารของคุณด้วยเนื้อหาที่ฝังไว้
weight: 10
url: /th/net/working-with-oleobjects-and-activex/insert-ole-object/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การแทรกวัตถุ Ole ในเอกสาร Word

## การแนะนำ

เมื่อทำงานกับเอกสาร Word ใน .NET การผสานรวมข้อมูลประเภทต่างๆ อาจมีความจำเป็น คุณลักษณะอันทรงพลังอย่างหนึ่งคือความสามารถในการแทรกวัตถุ OLE (Object Linking and Embedding) ลงในเอกสาร Word วัตถุ OLE สามารถเป็นเนื้อหาประเภทใดก็ได้ เช่น สเปรดชีต Excel งานนำเสนอ PowerPoint หรือเนื้อหา HTML ในคู่มือนี้ เราจะแนะนำวิธีแทรกวัตถุ OLE ลงในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1. Aspose.Words สำหรับไลบรารี .NET: ดาวน์โหลดจาก[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET อื่น ๆ
3. ความรู้พื้นฐานเกี่ยวกับ C#: ถือว่ามีความคุ้นเคยกับการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ

ในการเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้นำเข้าเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

มาแบ่งกระบวนการออกเป็นขั้นตอนที่สามารถจัดการได้

## ขั้นตอนที่ 1: สร้างเอกสารใหม่

ขั้นแรก คุณจะต้องสร้างเอกสาร Word ใหม่ ซึ่งจะทำหน้าที่เป็นคอนเทนเนอร์สำหรับอ็อบเจ็กต์ OLE ของเรา

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: แทรกวัตถุ OLE

 ต่อไปคุณจะใช้`DocumentBuilder`คลาสที่จะแทรกอ็อบเจ็กต์ OLE ในที่นี้ เราใช้ไฟล์ HTML ที่อยู่ที่ "http://www.aspose.com" เป็นตัวอย่าง

```csharp
builder.InsertOleObject("http://www.aspose.com", "htmlfile", true, true, null);
```

## ขั้นตอนที่ 3: บันทึกเอกสาร

สุดท้าย ให้บันทึกเอกสารของคุณไปยังเส้นทางที่ระบุ ตรวจสอบให้แน่ใจว่าเส้นทางนั้นถูกต้องและสามารถเข้าถึงได้

```csharp
doc.Save("Path_to_your_directory/WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
```

## บทสรุป

การแทรกวัตถุ OLE ลงในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เป็นฟีเจอร์อันทรงพลังที่ช่วยให้สามารถรวมเนื้อหาประเภทต่างๆ เข้าด้วยกันได้ ไม่ว่าจะเป็นไฟล์ HTML สเปรดชีต Excel หรือเนื้อหาอื่นๆ ที่เข้ากันได้กับ OLE ความสามารถนี้จะช่วยเพิ่มประสิทธิภาพการทำงานและการโต้ตอบของเอกสาร Word ของคุณได้อย่างมาก หากปฏิบัติตามขั้นตอนที่ระบุไว้ในคู่มือนี้ คุณจะสามารถผสานวัตถุ OLE ลงในเอกสารได้อย่างราบรื่น ทำให้เอกสารมีความไดนามิกและน่าสนใจยิ่งขึ้น

## คำถามที่พบบ่อย

### ฉันสามารถแทรกวัตถุ OLE ประเภทใดได้บ้างโดยใช้ Aspose.Words สำหรับ .NET?
คุณสามารถแทรกวัตถุ OLE ประเภทต่างๆ ได้ รวมถึงไฟล์ HTML สเปรดชีต Excel งานนำเสนอ PowerPoint และเนื้อหาที่เข้ากันได้กับ OLE อื่นๆ

### ฉันสามารถแสดงวัตถุ OLE เป็นไอคอนแทนเนื้อหาจริงได้หรือไม่
 ใช่ คุณสามารถเลือกแสดงวัตถุ OLE เป็นไอคอนได้โดยการตั้งค่า`asIcon` พารามิเตอร์ถึง`true`.

### สามารถเชื่อมโยงวัตถุ OLE เข้ากับไฟล์ต้นฉบับได้หรือไม่
 ใช่ โดยการตั้งค่า`isLinked` พารามิเตอร์ถึง`true`คุณสามารถเชื่อมโยงวัตถุ OLE เข้ากับไฟล์ต้นฉบับได้

### ฉันจะปรับแต่งไอคอนที่ใช้สำหรับวัตถุ OLE ได้อย่างไร
 คุณสามารถจัดทำไอคอนที่กำหนดเองได้โดยระบุ`Image` วัตถุเป็น`image` พารามิเตอร์ใน`InsertOleObject` วิธี.

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด
 คุณสามารถค้นหาเอกสารรายละเอียดได้ที่[หน้าเอกสาร Aspose.Words สำหรับ .NET](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
