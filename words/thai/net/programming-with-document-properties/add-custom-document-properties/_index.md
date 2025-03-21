---
title: เพิ่มคุณสมบัติเอกสารที่กำหนดเอง
linktitle: เพิ่มคุณสมบัติเอกสารที่กำหนดเอง
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีเพิ่มคุณสมบัติเอกสารแบบกำหนดเองในไฟล์ Word โดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อปรับปรุงเอกสารของคุณด้วยข้อมูลเมตาเพิ่มเติม
weight: 10
url: /th/net/programming-with-document-properties/add-custom-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มคุณสมบัติเอกสารที่กำหนดเอง

## การแนะนำ

สวัสดี! คุณกำลังเข้าสู่โลกของ Aspose.Words สำหรับ .NET และสงสัยว่าจะเพิ่มคุณสมบัติเอกสารแบบกำหนดเองลงในไฟล์ Word ของคุณได้อย่างไรใช่หรือไม่? คุณมาถูกที่แล้ว! คุณสมบัติแบบกำหนดเองนั้นมีประโยชน์อย่างยิ่งในการจัดเก็บข้อมูลเมตาเพิ่มเติมที่ไม่ได้ครอบคลุมอยู่ในคุณสมบัติในตัว ไม่ว่าจะเป็นการอนุญาตเอกสาร การเพิ่มหมายเลขการแก้ไข หรือแม้แต่การแทรกวันที่เฉพาะ คุณสมบัติแบบกำหนดเองก็ช่วยคุณได้ ในบทช่วยสอนนี้ เราจะแนะนำคุณทีละขั้นตอนในการเพิ่มคุณสมบัติเหล่านี้โดยใช้ Aspose.Words สำหรับ .NET ได้อย่างราบรื่น พร้อมเริ่มต้นหรือยัง มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มเขียนโค้ด เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการแล้ว:

1.  ไลบรารี Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณมีไลบรารี Aspose.Words สำหรับ .NET คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: IDE เช่น Visual Studio
3. ความรู้พื้นฐานเกี่ยวกับ C#: บทช่วยสอนนี้ถือว่าคุณมีความเข้าใจพื้นฐานเกี่ยวกับ C# และ .NET
4.  เอกสารตัวอย่าง: เตรียมเอกสาร Word ตัวอย่างที่ตั้งชื่อว่า`Properties.docx`ซึ่งคุณจะปรับเปลี่ยน

## นำเข้าเนมสเปซ

ก่อนที่เราจะเริ่มเขียนโค้ด เราจะต้องนำเข้าเนมสเปซที่จำเป็นเสียก่อน ซึ่งถือเป็นขั้นตอนสำคัญเพื่อให้แน่ใจว่าโค้ดของคุณสามารถเข้าถึงฟังก์ชันทั้งหมดที่ Aspose.Words จัดเตรียมไว้ให้ได้

```csharp
using System;
using Aspose.Words;
```

## ขั้นตอนที่ 1: การตั้งค่าเส้นทางเอกสาร

 สิ่งแรกที่เราต้องทำคือกำหนดเส้นทางไปยังเอกสารของเรา นี่คือจุดที่เราจะระบุตำแหน่งของเอกสารของเรา`Properties.docx` ไฟล์.

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

 ในสคริปท์นี้ ให้แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงไปยังเอกสารของคุณ ขั้นตอนนี้มีความสำคัญเนื่องจากจะช่วยให้โปรแกรมค้นหาและเปิดไฟล์ Word ของคุณได้

## ขั้นตอนที่ 2: การเข้าถึงคุณสมบัติเอกสารที่กำหนดเอง

ต่อไปเราจะเข้าไปที่คุณสมบัติเอกสารแบบกำหนดเองของเอกสาร Word ที่นี่เป็นที่ที่ข้อมูลเมตาแบบกำหนดเองทั้งหมดของคุณจะถูกเก็บไว้

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

การดำเนินการนี้จะทำให้เราสามารถจัดการกับคอลเลกชันคุณสมบัติแบบกำหนดเองได้ ซึ่งเราจะใช้ในขั้นตอนต่อไปนี้

## ขั้นตอนที่ 3: การตรวจสอบคุณสมบัติที่มีอยู่

ก่อนที่จะเพิ่มคุณสมบัติใหม่ ควรตรวจสอบว่ามีคุณสมบัตินั้นอยู่แล้วหรือไม่ เพื่อหลีกเลี่ยงการซ้ำซ้อนที่ไม่จำเป็น

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

บรรทัดนี้จะตรวจสอบว่าคุณสมบัติ "Authorized" มีอยู่แล้วหรือไม่ หากเป็นเช่นนั้น โปรแกรมจะออกจากเมธอดก่อนกำหนดเพื่อป้องกันการเพิ่มคุณสมบัติซ้ำซ้อน

## ขั้นตอนที่ 4: การเพิ่มคุณสมบัติบูลีน

ตอนนี้เรามาเพิ่มคุณสมบัติที่กำหนดเองแรกของเรากัน ซึ่งเป็นค่าบูลีนเพื่อระบุว่าเอกสารได้รับอนุญาตหรือไม่

```csharp
customDocumentProperties.Add("Authorized", true);
```

 บรรทัดนี้จะเพิ่มคุณสมบัติที่กำหนดเองชื่อ "ได้รับอนุญาต" ด้วยค่า`true`. ง่ายๆ และตรงไปตรงมา!

## ขั้นตอนที่ 5: การเพิ่มคุณสมบัติสตริง

ต่อไปเราจะเพิ่มคุณสมบัติที่กำหนดเองอีกอย่างหนึ่งเพื่อระบุว่าใครเป็นผู้อนุญาตเอกสาร

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

ที่นี่ เรากำลังเพิ่มคุณสมบัติที่เรียกว่า "Authorized By" ด้วยค่า "John Smith" คุณสามารถแทนที่ "John Smith" ด้วยชื่ออื่นที่คุณต้องการได้

## ขั้นตอนที่ 6: การเพิ่มคุณสมบัติวันที่

มาเพิ่มคุณสมบัติในการจัดเก็บวันที่อนุมัติกันเถอะ วิธีนี้จะช่วยให้ติดตามได้ว่าเอกสารได้รับอนุมัติเมื่อใด

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

 สไนปเป็ตนี้จะเพิ่มคุณสมบัติชื่อ "วันที่ได้รับอนุญาต" โดยมีวันที่ปัจจุบันเป็นค่า`DateTime.Today`คุณสมบัติจะดึงวันที่ปัจจุบันโดยอัตโนมัติ

## ขั้นตอนที่ 7: การเพิ่มหมายเลขการแก้ไข

นอกจากนี้ เรายังสามารถเพิ่มคุณสมบัติเพื่อติดตามหมายเลขการแก้ไขเอกสารได้ ซึ่งมีประโยชน์โดยเฉพาะสำหรับการควบคุมเวอร์ชัน

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

ที่นี่ เรากำลังเพิ่มคุณสมบัติที่เรียกว่า "การแก้ไขที่ได้รับอนุญาต" และกำหนดหมายเลขการแก้ไขปัจจุบันของเอกสารให้

## ขั้นตอนที่ 8: การเพิ่มคุณสมบัติตัวเลข

สุดท้ายนี้ เรามาเพิ่มคุณสมบัติตัวเลขเพื่อจัดเก็บจำนวนเงินที่ได้รับอนุญาตกัน ซึ่งอาจเป็นอะไรก็ได้ตั้งแต่ตัวเลขงบประมาณไปจนถึงจำนวนเงินธุรกรรม

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

 บรรทัดนี้จะเพิ่มคุณสมบัติชื่อ "จำนวนเงินที่ได้รับอนุญาต" ด้วยค่า`123.45`. อีกครั้ง คุณสามารถแทนที่ด้วยหมายเลขใด ๆ ที่เหมาะกับความต้องการของคุณได้

## บทสรุป

และแล้วคุณก็จะได้มัน! คุณได้เพิ่มคุณสมบัติเอกสารแบบกำหนดเองลงในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET คุณสมบัติเหล่านี้มีประโยชน์อย่างยิ่งในการจัดเก็บข้อมูลเมตาเพิ่มเติมที่เฉพาะเจาะจงกับความต้องการของคุณ ไม่ว่าคุณจะกำลังติดตามรายละเอียดการอนุญาต หมายเลขการแก้ไข หรือจำนวนเฉพาะ คุณสมบัติแบบกำหนดเองก็ให้โซลูชันที่ยืดหยุ่นได้

โปรดจำไว้ว่ากุญแจสำคัญในการเชี่ยวชาญ Aspose.Words สำหรับ .NET คือการฝึกฝน ดังนั้น ให้ทดลองใช้คุณสมบัติต่างๆ อย่างต่อเนื่อง และดูว่าคุณสมบัติเหล่านั้นจะช่วยปรับปรุงเอกสารของคุณได้อย่างไร ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### คุณสมบัติเอกสารที่กำหนดเองคืออะไร
คุณสมบัติเอกสารแบบกำหนดเองคือเมตาข้อมูลที่คุณสามารถเพิ่มลงในเอกสาร Word เพื่อเก็บข้อมูลเพิ่มเติมที่ไม่ครอบคลุมอยู่ในคุณสมบัติในตัว

### ฉันสามารถเพิ่มคุณสมบัติอื่นนอกจากสตริงและตัวเลขได้หรือไม่
ใช่ คุณสามารถเพิ่มคุณสมบัติประเภทต่างๆ ได้ รวมถึงค่าบูลีน วันที่ และแม้กระทั่งวัตถุแบบกำหนดเอง

### ฉันจะเข้าถึงคุณสมบัติเหล่านี้ในเอกสาร Word ได้อย่างไร?
สามารถเข้าถึงคุณสมบัติที่กำหนดเองได้โดยใช้โปรแกรมโดยใช้ Aspose.Words หรือดูโดยตรงใน Word ผ่านคุณสมบัติเอกสาร

### สามารถแก้ไขหรือลบคุณสมบัติที่กำหนดเองได้หรือไม่
ใช่ คุณสามารถแก้ไขหรือลบคุณสมบัติที่กำหนดเองได้อย่างง่ายดายโดยใช้วิธีการที่คล้ายกันที่ให้ไว้ใน Aspose.Words

### คุณสมบัติที่กำหนดเองสามารถใช้เพื่อกรองเอกสารได้หรือไม่
แน่นอน! คุณสมบัติที่กำหนดเองนั้นยอดเยี่ยมสำหรับการจัดหมวดหมู่และการกรองเอกสารตามข้อมูลเมตาที่เจาะจง

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
