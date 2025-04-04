---
title: การลงนามในบรรทัดลายเซ็นที่มีอยู่แล้วในเอกสาร Word
linktitle: การลงนามในบรรทัดลายเซ็นที่มีอยู่แล้วในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการลงนามในบรรทัดลายเซ็นที่มีอยู่แล้วในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET พร้อมคำแนะนำทีละขั้นตอนโดยละเอียดของเรา เหมาะสำหรับนักพัฒนา
weight: 10
url: /th/net/programming-with-digital-signatures/signing-existing-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การลงนามในบรรทัดลายเซ็นที่มีอยู่แล้วในเอกสาร Word

## การแนะนำ

สวัสดี! คุณเคยต้องลงนามในเอกสารดิจิทัลแต่พบว่ายุ่งยากหรือไม่ คุณโชคดี เพราะวันนี้เราจะมาแนะนำวิธีลงนามในบรรทัดลายเซ็นที่มีอยู่แล้วในเอกสาร Word ได้อย่างง่ายดายโดยใช้ Aspose.Words สำหรับ .NET บทช่วยสอนนี้จะแนะนำคุณทีละขั้นตอน เพื่อให้คุณเชี่ยวชาญในงานนี้ได้ในเวลาอันรวดเร็ว

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกรายละเอียดที่สำคัญ เรามาตรวจสอบให้แน่ใจก่อนว่าเรามีทุกสิ่งที่จำเป็น:

1.  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Aspose.Words สำหรับ .NET แล้ว หากยังไม่ได้ติดตั้ง คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE อื่น ๆ ที่เข้ากันได้กับ C#
3. เอกสารและใบรับรอง: เอกสาร Word ที่มีบรรทัดลายเซ็นและใบรับรองดิจิทัล (ไฟล์ PFX)
4. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะเป็นประโยชน์

## นำเข้าเนมสเปซ

ก่อนที่คุณจะใช้คลาสและวิธีการจาก Aspose.Words ได้ คุณต้องนำเข้าเนมสเปซที่จำเป็นก่อน นี่คือตัวอย่างการนำเข้าที่จำเป็น:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

## ขั้นตอนที่ 1: โหลดเอกสารของคุณ

ขั้นแรก คุณต้องโหลดเอกสาร Word ที่มีบรรทัดลายเซ็น ขั้นตอนนี้มีความสำคัญมาก เนื่องจากเป็นการวางรากฐานให้กับกระบวนการทั้งหมด

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

## ขั้นตอนที่ 2: เข้าถึงสายลายเซ็น

ตอนนี้เราได้โหลดเอกสารแล้ว ขั้นตอนถัดไปคือค้นหาและเข้าถึงบรรทัดลายเซ็นภายในเอกสาร

```csharp
SignatureLine signatureLine = ((Shape) doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

## ขั้นตอนที่ 3: ตั้งค่าตัวเลือกป้าย

การตั้งค่าตัวเลือกลายเซ็นเป็นสิ่งสำคัญ ซึ่งรวมถึงการระบุ ID ของบรรทัดลายเซ็นและจัดเตรียมรูปภาพที่จะใช้เป็นลายเซ็น

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes("YOUR IMAGE DIRECTORY" + "signature_image.emf")
};
```

## ขั้นตอนที่ 4: สร้างผู้ถือใบรับรอง

หากต้องการลงนามในเอกสารแบบดิจิทัล คุณจะต้องมีใบรับรองดิจิทัล ต่อไปนี้เป็นวิธีสร้างผู้ถือใบรับรองจากไฟล์ PFX ของคุณ

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "your_password");
```

## ขั้นตอนที่ 5: ลงนามในเอกสาร

ตอนนี้เรารวมส่วนประกอบทั้งหมดเข้าด้วยกันเพื่อลงนามในเอกสาร นี่คือจุดที่ความมหัศจรรย์เกิดขึ้น!

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Digitally signed.docx",
    dataDir + "Signature line.docx",
    certHolder,
    signOptions
);
```

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณได้ลงนามในบรรทัดลายเซ็นที่มีอยู่แล้วในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET สำเร็จแล้ว ไม่ยากเกินไปใช่ไหม? ด้วยขั้นตอนเหล่านี้ ตอนนี้คุณสามารถลงนามในเอกสารแบบดิจิทัลได้แล้ว ซึ่งช่วยเพิ่มความน่าเชื่อถือและความเป็นมืออาชีพอีกชั้นหนึ่ง ดังนั้น ครั้งต่อไปที่ใครสักคนส่งเอกสารมาให้คุณลงนาม คุณจะรู้ทันทีว่าต้องทำอย่างไร!

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?

Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังสำหรับการทำงานกับเอกสาร Word ในแอปพลิเคชัน .NET ช่วยให้คุณสามารถสร้าง แก้ไข และแปลงเอกสาร Word ได้ด้วยโปรแกรม

### ฉันจะได้รับรุ่นทดลองใช้ Aspose.Words สำหรับ .NET ฟรีได้ที่ไหน

 คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันสามารถใช้รูปแบบภาพใดก็ได้สำหรับลายเซ็นหรือไม่

Aspose.Words รองรับรูปแบบภาพต่างๆ แต่การใช้เมตาไฟล์ที่ได้รับการปรับปรุง (EMF) จะให้คุณภาพของลายเซ็นที่ดีกว่า

### ฉันจะได้รับใบรับรองดิจิทัลได้อย่างไร?

คุณสามารถซื้อใบรับรองดิจิทัลจากผู้ให้บริการต่างๆ ทางออนไลน์ได้ ตรวจสอบให้แน่ใจว่าใบรับรองอยู่ในรูปแบบ PFX และคุณมีรหัสผ่าน

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด

 คุณสามารถค้นหาเอกสารประกอบที่ครอบคลุมได้[ที่นี่](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
