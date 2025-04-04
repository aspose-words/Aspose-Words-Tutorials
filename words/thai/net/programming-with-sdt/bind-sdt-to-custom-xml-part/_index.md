---
title: ผูก SDT กับส่วน XML ที่กำหนดเอง
linktitle: ผูก SDT กับส่วน XML ที่กำหนดเอง
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการผูกแท็กเอกสารที่มีโครงสร้าง (SDT) กับส่วน XML ที่กำหนดเองในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยบทช่วยสอนทีละขั้นตอนนี้
weight: 10
url: /th/net/programming-with-sdt/bind-sdt-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ผูก SDT กับส่วน XML ที่กำหนดเอง

## การแนะนำ

การสร้างเอกสาร Word แบบไดนามิกที่โต้ตอบกับข้อมูล XML ที่กำหนดเองสามารถเพิ่มความยืดหยุ่นและฟังก์ชันการทำงานของแอปพลิเคชันของคุณได้อย่างมาก Aspose.Words สำหรับ .NET มีคุณสมบัติที่แข็งแกร่งในการผูกแท็กเอกสารที่มีโครงสร้าง (SDT) กับส่วน XML ที่กำหนดเอง ช่วยให้คุณสร้างเอกสารที่แสดงข้อมูลแบบไดนามิกได้ ในบทช่วยสอนนี้ เราจะแนะนำคุณทีละขั้นตอนในการผูก SDT กับส่วน XML ที่กำหนดเอง มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

-  Aspose.Words สำหรับ .NET: คุณสามารถดาวน์โหลดเวอร์ชันล่าสุดได้จาก[Aspose.Words สำหรับการเปิดตัว .NET](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: Visual Studio หรือ .NET IDE อื่น ๆ ที่เข้ากันได้
- ความเข้าใจพื้นฐานเกี่ยวกับ C#: มีความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และ .NET framework

## นำเข้าเนมสเปซ

หากต้องการใช้ Aspose.Words สำหรับ .NET อย่างมีประสิทธิภาพ คุณจำเป็นต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ เพิ่มคำสั่ง using ต่อไปนี้ที่ด้านบนของไฟล์โค้ดของคุณ:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Saving;
```

เรามาแบ่งกระบวนการออกเป็นขั้นตอนที่จัดการได้เพื่อให้ปฏิบัติตามได้ง่ายขึ้น โดยแต่ละขั้นตอนจะครอบคลุมเฉพาะส่วนของงาน

## ขั้นตอนที่ 1: เริ่มต้นเอกสาร

ขั้นแรกคุณต้องสร้างเอกสารใหม่และตั้งค่าสภาพแวดล้อม

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

// เริ่มต้นเอกสารใหม่
Document doc = new Document();
```

ในขั้นตอนนี้ เราจะเริ่มต้นเอกสารใหม่ที่จะเก็บข้อมูล XML ที่กำหนดเองและ SDT ของเรา

## ขั้นตอนที่ 2: เพิ่มส่วน XML ที่กำหนดเอง

จากนั้นเราจะเพิ่มส่วน XML ที่กำหนดเองลงในเอกสาร ส่วนนี้จะมีข้อมูล XML ที่เราต้องการเชื่อมโยงกับ SDT

```csharp
// เพิ่มส่วน XML ที่กำหนดเองลงในเอกสาร
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(Guid.NewGuid().ToString("B"), "<root><text>Hello, World!</text></root>");
```

ที่นี่ เราจะสร้างส่วน XML ที่กำหนดเองใหม่ด้วยตัวระบุเฉพาะและเพิ่มข้อมูลตัวอย่าง XML

## ขั้นตอนที่ 3: สร้างแท็กเอกสารที่มีโครงสร้าง (SDT)

หลังจากเพิ่มส่วน XML ที่กำหนดเองแล้ว เราจะสร้าง SDT เพื่อแสดงข้อมูล XML

```csharp
//สร้างแท็กเอกสารที่มีโครงสร้าง (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Block);
doc.FirstSection.Body.AppendChild(sdt);
```

เราสร้าง SDT ชนิด PlainText และผนวกเข้าในส่วนแรกของเนื้อหาเอกสาร

## ขั้นตอนที่ 4: เชื่อมโยง SDT กับส่วน XML ที่กำหนดเอง

ตอนนี้ เราผูก SDT เข้ากับส่วน XML ที่กำหนดเองโดยใช้นิพจน์ XPath

```csharp
// ผูก SDT กับส่วน XML ที่กำหนดเอง
sdt.XmlMapping.SetMapping(xmlPart, "/root[1]/text[1]", "");
```

 ขั้นตอนนี้จะแมป SDT ไปยัง`<text>` องค์ประกอบภายใน`<root>` โหนดของส่วน XML ที่กำหนดเองของเรา

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายเราบันทึกเอกสารไปยังไดเร็กทอรีที่ระบุ

```csharp
// บันทึกเอกสาร
doc.Save(dataDir + "WorkingWithSdt.BindSDTtoCustomXmlPart.doc");
```

คำสั่งนี้จะบันทึกเอกสารที่มี SDT ที่ถูกผูกไว้ไปยังไดเร็กทอรีที่คุณกำหนด

## บทสรุป

ขอแสดงความยินดี! คุณได้ผูก SDT กับส่วน XML ที่กำหนดเองสำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ฟีเจอร์อันทรงพลังนี้ช่วยให้คุณสร้างเอกสารแบบไดนามิกที่สามารถอัปเดตด้วยข้อมูลใหม่ได้อย่างง่ายดายโดยเพียงแค่ปรับเปลี่ยนเนื้อหา XML ไม่ว่าคุณจะกำลังสร้างรายงาน สร้างเทมเพลต หรือทำให้เวิร์กโฟลว์เอกสารเป็นแบบอัตโนมัติ Aspose.Words สำหรับ .NET ก็มีเครื่องมือที่คุณต้องการเพื่อทำให้งานของคุณง่ายขึ้นและมีประสิทธิภาพมากขึ้น

## คำถามที่พบบ่อย

### แท็กเอกสารที่มีโครงสร้าง (SDT) คืออะไร?
แท็กเอกสารที่มีโครงสร้าง (SDT) เป็นองค์ประกอบการควบคุมเนื้อหาในเอกสาร Word ที่ใช้ผูกข้อมูลแบบไดนามิก ทำให้เอกสารเป็นแบบโต้ตอบได้และขับเคลื่อนด้วยข้อมูล

### ฉันสามารถผูก SDT หลายรายการกับส่วน XML ต่างๆ ในเอกสารเดียวได้หรือไม่
ใช่ คุณสามารถผูก SDT หลายรายการกับส่วน XML ต่างๆ ในเอกสารเดียวกันได้ ช่วยให้มีเทมเพลตที่ขับเคลื่อนด้วยข้อมูลที่ซับซ้อนได้

### ฉันจะอัปเดตข้อมูล XML ในส่วน XML ที่กำหนดเองได้อย่างไร
 คุณสามารถอัปเดตข้อมูล XML ได้โดยเข้าถึง`CustomXmlPart` วัตถุและปรับเปลี่ยนเนื้อหา XML โดยตรง

### สามารถผูก SDT เข้ากับแอตทริบิวต์ XML แทนองค์ประกอบได้หรือไม่
ใช่ คุณสามารถผูก SDT เข้ากับแอตทริบิวต์ XML ได้โดยระบุนิพจน์ XPath ที่เหมาะสมซึ่งกำหนดเป้าหมายไปที่แอตทริบิวต์ที่ต้องการ

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด
 คุณสามารถค้นหาเอกสารประกอบที่ครอบคลุมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้ที่[เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
