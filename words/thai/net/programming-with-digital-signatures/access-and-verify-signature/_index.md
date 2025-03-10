---
title: เข้าถึงและตรวจสอบลายเซ็นในเอกสาร Word
linktitle: เข้าถึงและตรวจสอบลายเซ็นในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เข้าถึงและตรวจสอบลายเซ็นดิจิทัลในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนที่ครอบคลุมนี้ รับรองความถูกต้องของเอกสารได้อย่างง่ายดาย
weight: 10
url: /th/net/programming-with-digital-signatures/access-and-verify-signature/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เข้าถึงและตรวจสอบลายเซ็นในเอกสาร Word

## การแนะนำ

สวัสดีเพื่อนนักเทคโนโลยีทุกท่าน คุณเคยพบสถานการณ์ที่ต้องเข้าถึงและยืนยันลายเซ็นดิจิทัลในเอกสาร Word แต่ไม่รู้ว่าต้องเริ่มต้นอย่างไรหรือไม่? ถือว่าคุณโชคดีแล้ว! วันนี้เราจะพาคุณดำดิ่งสู่โลกอันมหัศจรรย์ของ Aspose.Words สำหรับ .NET ซึ่งเป็นไลบรารีอันทรงพลังที่ทำให้การจัดการเอกสาร Word เป็นเรื่องง่าย เราจะพาคุณผ่านขั้นตอนต่างๆ ทีละขั้นตอน ดังนั้นเมื่ออ่านคู่มือนี้จบ คุณจะกลายเป็นผู้เชี่ยวชาญในการยืนยันลายเซ็นดิจิทัลในเอกสาร Word ได้เลย มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกรายละเอียดที่สำคัญ มีบางสิ่งบางอย่างที่คุณจะต้องมี:

1. Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio ไว้ในเครื่องของคุณแล้ว นี่คือที่ที่คุณจะเขียนและรันโค้ดของคุณ
2.  Aspose.Words สำหรับ .NET: คุณจะต้องติดตั้ง Aspose.Words สำหรับ .NET คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/) อย่าลืมรับสิทธิ์ทดลองใช้ฟรี[ที่นี่](https://releases.aspose.com/) หากคุณยังไม่ได้ทำ!
3. เอกสาร Word ที่ลงนามแบบดิจิทัล: มีเอกสาร Word ที่ลงนามแบบดิจิทัลแล้ว นี่คือไฟล์ที่คุณจะใช้เพื่อตรวจสอบลายเซ็น

## นำเข้าเนมสเปซ

ขั้นแรก เรามาทำการนำเข้าเนมสเปซที่จำเป็นกันก่อน เนมสเปซเหล่านี้จะช่วยให้คุณใช้ฟีเจอร์ Aspose.Words ในโปรเจ็กต์ของคุณได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.DigitalSignatures;
```

เอาล่ะ มาแบ่งขั้นตอนต่างๆ ออกเป็นขั้นตอนที่จัดการได้ แต่ละขั้นตอนจะแนะนำคุณตลอดขั้นตอนเฉพาะของกระบวนการ พร้อมหรือยัง ไปกันเลย!

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

ก่อนที่คุณจะตรวจสอบลายเซ็นดิจิทัลได้ คุณต้องตั้งค่าโปรเจ็กต์ของคุณใน Visual Studio เสียก่อน ดังต่อไปนี้:

### สร้างโครงการใหม่

1. เปิด Visual Studio
2. คลิก สร้างโครงการใหม่
3. เลือกแอปคอนโซล (.NET Core) หรือแอปคอนโซล (.NET Framework) ตามความต้องการของคุณ
4. คลิกถัดไป ตั้งชื่อโครงการของคุณ และคลิกสร้าง

### ติดตั้ง Aspose.Words สำหรับ .NET

1. ใน Solution Explorer ให้คลิกขวาที่ชื่อโครงการของคุณ และเลือกจัดการแพ็คเกจ NuGet
2. ในตัวจัดการแพ็กเกจ NuGet ให้ค้นหา Aspose.Words
3. คลิกติดตั้งเพื่อเพิ่มลงในโครงการของคุณ

## ขั้นตอนที่ 2: โหลดเอกสาร Word ที่ลงนามดิจิทัล

ตอนนี้โครงการของคุณตั้งค่าเสร็จเรียบร้อยแล้ว มาโหลดเอกสาร Word ที่ได้รับการลงนามแบบดิจิทัลกัน

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Digitally signed.docx");
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงไปยังไดเรกทอรีเอกสารของคุณ โค้ดนี้จะเริ่มต้นใหม่`Document` วัตถุและโหลดเอกสาร Word ที่คุณลงนาม

## ขั้นตอนที่ 3: เข้าถึงลายเซ็นดิจิทัล

เมื่อคุณโหลดเอกสารเสร็จเรียบร้อยแล้ว ก็ถึงเวลาเข้าถึงลายเซ็นดิจิทัล

```csharp
foreach (DigitalSignature signature in doc.DigitalSignatures)
{
    Console.WriteLine("* Signature Found *");
    Console.WriteLine("Is valid: " + signature.IsValid);
    Console.WriteLine("Reason for signing: " + signature.Comments); 
    Console.WriteLine("Time of signing: " + signature.SignTime);
    Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
    Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
    Console.WriteLine();
}
```

โค้ดนี้จะวนซ้ำลายเซ็นดิจิทัลแต่ละอันในเอกสารและพิมพ์รายละเอียดต่างๆ เกี่ยวกับลายเซ็นออกมา มาดูกันว่าแต่ละส่วนมีหน้าที่อะไรบ้าง:

1. พบลายเซ็น: ระบุว่าพบลายเซ็นแล้ว
2. ถูกต้อง: ตรวจสอบว่าลายเซ็นถูกต้องหรือไม่
3. เหตุผลในการลงนาม: แสดงเหตุผลในการลงนาม หากมี
4. เวลาที่ลงนาม: แสดงเวลาประทับเมื่อเอกสารได้รับการลงนาม
5. ชื่อเรื่อง: ดึงชื่อเรื่องจากใบรับรอง
6. ชื่อผู้ออกใบรับรอง: ดึงชื่อผู้ออกจากใบรับรอง

## ขั้นตอนที่ 4: รันโค้ดของคุณ

เมื่อทุกอย่างตั้งค่าเสร็จเรียบร้อยแล้ว ก็ถึงเวลาที่จะรันโค้ดของคุณและดูผลลัพธ์


1. กด F5 หรือคลิกปุ่มเริ่มใน Visual Studio เพื่อเรียกใช้โปรแกรมของคุณ
2. หากเอกสารของคุณมีลายเซ็นดิจิทัล คุณจะเห็นรายละเอียดลายเซ็นพิมพ์ในคอนโซล

## ขั้นตอนที่ 5: จัดการกับข้อผิดพลาดที่อาจเกิดขึ้น

การจัดการข้อผิดพลาดที่อาจเกิดขึ้นถือเป็นความคิดที่ดีเสมอ มาเพิ่มวิธีการจัดการข้อผิดพลาดพื้นฐานให้กับโค้ดของเรากัน

```csharp
try
{
    // เส้นทางไปยังไดเร็กทอรีเอกสาร
    string dataDir = "YOUR DOCUMENT DIRECTORY";
    Document doc = new Document(dataDir + "Digitally signed.docx");

    foreach (DigitalSignature signature in doc.DigitalSignatures)
    {
        Console.WriteLine("* Signature Found *");
        Console.WriteLine("Is valid: " + signature.IsValid);
        Console.WriteLine("Reason for signing: " + signature.Comments); 
        Console.WriteLine("Time of signing: " + signature.SignTime);
        Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
        Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
        Console.WriteLine();
    }
}
catch (Exception ex)
{
    Console.WriteLine("An error occurred: " + ex.Message);
}
```

การดำเนินการนี้จะตรวจจับข้อยกเว้นใดๆ ที่อาจเกิดขึ้นและพิมพ์ข้อความแสดงข้อผิดพลาด

## บทสรุป

และแล้วคุณก็ทำได้! คุณเข้าถึงและตรวจสอบลายเซ็นดิจิทัลในเอกสาร Word ได้สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ไม่ใช่เรื่องยากอย่างที่คิดใช่ไหม? ด้วยขั้นตอนเหล่านี้ คุณสามารถจัดการลายเซ็นดิจิทัลในเอกสาร Word ของคุณได้อย่างมั่นใจ รับรองความถูกต้องและความสมบูรณ์ของลายเซ็น สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET เพื่อเพิ่มลายเซ็นดิจิทัลลงในเอกสาร Word ได้หรือไม่

ใช่ คุณสามารถใช้ Aspose.Words สำหรับ .NET เพื่อเพิ่มลายเซ็นดิจิทัลลงในเอกสาร Word ได้ ไลบรารีนี้มีฟีเจอร์ที่ครอบคลุมสำหรับการเพิ่มและการตรวจสอบลายเซ็นดิจิทัล

### ลายเซ็นดิจิทัลประเภทใดที่ Aspose.Words สำหรับ .NET สามารถตรวจสอบได้

Aspose.Words สำหรับ .NET สามารถตรวจสอบลายเซ็นดิจิทัลในไฟล์ DOCX ที่ใช้ใบรับรอง X.509 ได้

### Aspose.Words สำหรับ .NET เข้ากันได้กับ Microsoft Word ทุกเวอร์ชันหรือไม่

Aspose.Words สำหรับ .NET รองรับเอกสาร Microsoft Word ทุกเวอร์ชัน รวมถึง DOC, DOCX, RTF และอื่นๆ

### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร

 คุณสามารถรับใบอนุญาตชั่วคราวสำหรับ Aspose.Words สำหรับ .NET ได้จาก[ที่นี่](https://purchase.aspose.com/temporary-license/)ซึ่งจะทำให้คุณสามารถทดลองใช้ฟีเจอร์ทั้งหมดของไลบรารีได้โดยไม่มีข้อจำกัดใดๆ

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด

 คุณสามารถค้นหาเอกสารรายละเอียดสำหรับ Aspose.Words สำหรับ .NET ได้[ที่นี่](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
