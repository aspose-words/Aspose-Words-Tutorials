---
title: สร้างบรรทัดลายเซ็นใหม่และตั้งค่ารหัสผู้ให้บริการ
linktitle: สร้างบรรทัดลายเซ็นใหม่และตั้งค่ารหัสผู้ให้บริการ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการสร้างบรรทัดลายเซ็นใหม่และตั้งค่า ID ผู้ให้บริการในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET คำแนะนำทีละขั้นตอน
weight: 10
url: /th/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างบรรทัดลายเซ็นใหม่และตั้งค่ารหัสผู้ให้บริการ

## การแนะนำ

สวัสดีผู้ชื่นชอบเทคโนโลยี! คุณเคยสงสัยไหมว่าจะเพิ่มบรรทัดลายเซ็นในเอกสาร Word ของคุณโดยใช้โปรแกรมได้อย่างไร วันนี้เราจะมาเจาะลึกเรื่องนั้นโดยใช้ Aspose.Words สำหรับ .NET คู่มือนี้จะแนะนำคุณทีละขั้นตอน ทำให้การสร้างบรรทัดลายเซ็นใหม่และกำหนด ID ผู้ให้บริการในเอกสาร Word ของคุณเป็นเรื่องง่าย ไม่ว่าคุณจะกำลังทำให้การประมวลผลเอกสารเป็นแบบอัตโนมัติหรือเพียงแค่ต้องการปรับปรุงเวิร์กโฟลว์ของคุณ บทช่วยสอนนี้จะช่วยคุณได้

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงมือทำ เรามาตรวจสอบให้แน่ใจก่อนว่าเรามีทุกสิ่งที่จำเป็น:

1.  Aspose.Words สำหรับ .NET: หากคุณยังไม่ได้ดาวน์โหลด โปรดดาวน์โหลด[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: Visual Studio หรือสภาพแวดล้อมการพัฒนา C# อื่นๆ
3. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework แล้ว
4. ใบรับรอง PFX: สำหรับการลงนามเอกสาร คุณจะต้องมีใบรับรอง PFX คุณสามารถรับใบรับรองได้จากผู้มีอำนาจออกใบรับรองที่เชื่อถือได้

## นำเข้าเนมสเปซ

ขั้นแรกเลย ขอทำการอิมพอร์ตเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

เอาล่ะ มาเริ่มลงรายละเอียดกันเลย ต่อไปนี้คือรายละเอียดของแต่ละขั้นตอนในการสร้างบรรทัดลายเซ็นใหม่และกำหนด ID ผู้ให้บริการ

## ขั้นตอนที่ 1: สร้างเอกสารใหม่

ในการเริ่มต้น เราต้องสร้างเอกสาร Word ใหม่ ซึ่งจะเป็นพื้นที่สำหรับบรรทัดลายเซ็นของเรา

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 ในสไนปเป็ตนี้ เรากำลังเริ่มต้นสิ่งใหม่`Document` และก`DocumentBuilder` . การ`DocumentBuilder` ช่วยให้เราเพิ่มองค์ประกอบต่างๆ ให้กับเอกสารของเรา

## ขั้นตอนที่ 2: กำหนดตัวเลือกบรรทัดลายเซ็น

ต่อไป เราจะกำหนดตัวเลือกสำหรับบรรทัดลายเซ็นของเรา ซึ่งรวมถึงชื่อผู้ลงนาม ตำแหน่ง อีเมล และรายละเอียดอื่นๆ

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

ตัวเลือกเหล่านี้จะช่วยปรับแต่งบรรทัดลายเซ็นให้ชัดเจนและเป็นมืออาชีพ

## ขั้นตอนที่ 3: แทรกบรรทัดลายเซ็น

เมื่อตั้งค่าตัวเลือกแล้ว เราสามารถแทรกบรรทัดลายเซ็นลงในเอกสารได้

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 ที่นี่`InsertSignatureLine` วิธีการเพิ่มบรรทัดลายเซ็น และเรากำหนด ID ผู้ให้บริการเฉพาะให้กับบรรทัดนั้น

## ขั้นตอนที่ 4: บันทึกเอกสาร

หลังจากแทรกบรรทัดลายเซ็นแล้ว เรามาบันทึกเอกสารกันเถอะ

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

การดำเนินการนี้จะบันทึกเอกสารของคุณโดยมีบรรทัดลายเซ็นที่เพิ่มใหม่

## ขั้นตอนที่ 5: ตั้งค่าตัวเลือกการลงนาม

ตอนนี้ เราต้องตั้งค่าตัวเลือกสำหรับการลงนามในเอกสาร ซึ่งรวมถึง ID บรรทัดลายเซ็น ID ผู้ให้บริการ ความคิดเห็น และเวลาลงนาม

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

ตัวเลือกเหล่านี้ช่วยให้แน่ใจว่าเอกสารได้รับการลงนามด้วยรายละเอียดที่ถูกต้อง

## ขั้นตอนที่ 6: สร้างผู้ถือใบรับรอง

ในการลงนามในเอกสาร เราจะใช้ใบรับรอง PFX มาสร้างผู้ถือใบรับรองสำหรับเอกสารนี้กัน

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 อย่าลืมเปลี่ยน`"morzal.pfx"` ด้วยไฟล์ใบรับรองจริงของคุณและ`"aw"` ด้วยรหัสผ่านใบรับรองของคุณ

## ขั้นตอนที่ 7: ลงนามในเอกสาร

สุดท้ายเราลงนามเอกสารโดยใช้ยูทิลิตี้ลายเซ็นดิจิทัล

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

การดำเนินการนี้จะลงนามในเอกสารและบันทึกเป็นไฟล์ใหม่

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณได้สร้างบรรทัดลายเซ็นใหม่และกำหนด ID ผู้ให้บริการในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ไลบรารีอันทรงพลังนี้ทำให้การจัดการและจัดการงานประมวลผลเอกสารอัตโนมัติเป็นเรื่องง่ายอย่างเหลือเชื่อ ลองใช้ดูและดูว่าจะช่วยเพิ่มประสิทธิภาพเวิร์กโฟลว์ของคุณได้อย่างไร

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งลักษณะของเส้นลายเซ็นได้หรือไม่?
 แน่นอน! คุณสามารถปรับเปลี่ยนตัวเลือกต่างๆ ได้ใน`SignatureLineOptions`เพื่อให้เหมาะกับความต้องการของคุณ

### จะเกิดอะไรขึ้นหากฉันไม่มีใบรับรอง PFX?
คุณจะต้องขอรับใบรับรองจากผู้มีอำนาจออกใบรับรองที่เชื่อถือได้ ซึ่งถือเป็นสิ่งสำคัญสำหรับการลงนามเอกสารแบบดิจิทัล

### ฉันสามารถเพิ่มบรรทัดลายเซ็นหลายบรรทัดลงในเอกสารได้หรือไม่
ใช่ คุณสามารถเพิ่มบรรทัดลายเซ็นได้มากเท่าที่ต้องการโดยทำซ้ำขั้นตอนการแทรกด้วยตัวเลือกที่แตกต่างกัน

### Aspose.Words สำหรับ .NET เข้ากันได้กับ .NET Core หรือไม่
ใช่ Aspose.Words สำหรับ .NET รองรับ .NET Core ทำให้มีความยืดหยุ่นสำหรับสภาพแวดล้อมการพัฒนาที่แตกต่างกัน

### ลายเซ็นดิจิทัลมีความปลอดภัยแค่ไหน?
ลายเซ็นดิจิทัลที่สร้างด้วย Aspose.Words มีความปลอดภัยสูง โดยขอให้คุณใช้ใบรับรองที่ถูกต้องและเชื่อถือได้
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
