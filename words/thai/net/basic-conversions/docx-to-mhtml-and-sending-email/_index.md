---
"description": "เรียนรู้วิธีแปลง DOCX เป็น MHTML และส่งอีเมลโดยใช้ Aspose.Words สำหรับ .NET ในคู่มือทีละขั้นตอนนี้ เพิ่มประสิทธิภาพการทำงานของคุณด้วยการทำงานอัตโนมัติที่ง่ายดาย"
"linktitle": "แปลง Docx เป็น Mhtml และส่งอีเมล"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "แปลง Docx เป็น Mhtml และส่งอีเมล"
"url": "/th/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แปลง Docx เป็น Mhtml และส่งอีเมล

## การแนะนำ

ในยุคดิจิทัลทุกวันนี้ การแปลงเอกสารจากรูปแบบหนึ่งไปเป็นอีกรูปแบบหนึ่งและส่งทางอีเมลถือเป็นงานทั่วไป บทความนี้จะแนะนำคุณเกี่ยวกับกระบวนการแปลงไฟล์ DOCX เป็นรูปแบบ MHTML จากนั้นส่งเป็นอีเมลโดยใช้ Aspose.Words สำหรับ .NET เราจะอธิบายแต่ละขั้นตอนอย่างละเอียดและปฏิบัติตามได้ง่าย เพื่อให้คุณเข้าใจกระบวนการตั้งแต่ต้นจนจบ มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

1. Aspose.Words สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารี Aspose.Words สำหรับ .NET จาก [หน้าวางจำหน่าย Aspose](https://releases-aspose.com/words/net/).
2. Aspose.Email สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารี Aspose.Email สำหรับ .NET จาก [หน้าวางจำหน่าย Aspose](https://releases-aspose.com/email/net/).
3. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework ไว้ในเครื่องของคุณแล้ว
4. เซิร์ฟเวอร์ SMTP: คุณต้องเข้าถึงเซิร์ฟเวอร์ SMTP เพื่อส่งอีเมล

## นำเข้าเนมสเปซ

หากต้องการใช้ Aspose.Words และ Aspose.Email ในโปรเจ็กต์ของคุณ คุณจะต้องนำเข้าเนมสเปซที่จำเป็น เพิ่มคำสั่ง using ต่อไปนี้ที่ด้านบนของไฟล์ C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

มาแบ่งกระบวนการออกเป็นหลายขั้นตอนเพื่อให้แน่ใจว่าคุณเข้าใจแต่ละส่วนอย่างชัดเจน

## ขั้นตอนที่ 1: โหลดเอกสาร DOCX

ขั้นแรก คุณต้องโหลดเอกสาร DOCX ที่คุณต้องการแปลง ใช้ `Document` คลาสจาก Aspose.Words เพื่อโหลดไฟล์ DOCX ของคุณ

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## ขั้นตอนที่ 2: บันทึกเอกสารเป็น MHTML

ขั้นตอนต่อไป ให้บันทึกเอกสารที่โหลดเป็นไฟล์ MHTML ซึ่งทำได้โดยใช้ `Save` วิธีการของ `Document` ระดับ.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// กรอกลับสตรีมมายังจุดเริ่มต้นเพื่อให้ Aspose.Email อ่านได้
stream.Position = 0;
```

## ขั้นตอนที่ 3: สร้างข้อความอีเมล์

ตอนนี้สร้างข้อความอีเมลจากสตรีม MHTML โดยใช้ Aspose.Email คุณจะใช้ `MailMessage` ชั้นเรียนสำหรับจุดประสงค์นี้

```csharp
// สร้างข้อความอีเมล MIME Aspose.Email จากสตรีม
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## ขั้นตอนที่ 4: ส่งอีเมล

สุดท้ายให้ส่งอีเมลโดยใช้ไคลเอนต์ SMTP กำหนดค่าไคลเอนต์ SMTP ด้วยรายละเอียดเซิร์ฟเวอร์ SMTP ของคุณและใช้ `Send` วิธีการส่งข้อความ

```csharp
// ส่งข้อความโดยใช้ Aspose.Email
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## บทสรุป

ขอแสดงความยินดี! คุณได้แปลงเอกสาร DOCX เป็น MHTML และส่งทางอีเมลโดยใช้ Aspose.Words สำหรับ .NET สำเร็จแล้ว ขั้นตอนนี้เกี่ยวข้องกับการโหลดเอกสาร แปลงเป็น MHTML สร้างข้อความอีเมล และส่งโดยใช้ไคลเอนต์ SMTP ด้วยขั้นตอนเหล่านี้ คุณสามารถทำให้การแปลงและส่งอีเมลเอกสารในแอปพลิเคชันของคุณเป็นแบบอัตโนมัติได้อย่างง่ายดาย

## คำถามที่พบบ่อย

### ฉันสามารถใช้วิธีนี้เพื่อแปลงรูปแบบเอกสารอื่นได้หรือไม่
ใช่ Aspose.Words รองรับรูปแบบต่างๆ และคุณสามารถแปลงเอกสารเช่น DOC, DOCX, RTF และอื่นๆ เป็น MHTML ได้

### ฉันจะเพิ่มไฟล์แนบไปในอีเมล์ได้อย่างไร?
คุณสามารถใช้ `Attachments` ทรัพย์สินของ `MailMessage` ชั้นเรียนเพื่อเพิ่มไฟล์แนบไปในอีเมล์ของคุณ

### Aspose.Words เข้ากันได้กับ .NET Core ได้หรือไม่
ใช่ Aspose.Words เข้ากันได้กับ .NET Core และคุณสามารถใช้ในแอปพลิเคชัน .NET Core ได้เช่นกัน

### ฉันต้องมีใบอนุญาตสำหรับ Aspose.Words และ Aspose.Email หรือไม่?
ใช่ ทั้งสองห้องสมุดต้องมีใบอนุญาต คุณสามารถขอใบอนุญาตชั่วคราวได้จาก [หน้าสั่งซื้อ Aspose](https://purchase.aspose.com/temporary-license/) เพื่อวัตถุประสงค์ในการประเมินผล

### ฉันสามารถหาเอกสารเพิ่มเติมได้ที่ไหน
คุณสามารถค้นหาเอกสารรายละเอียดสำหรับ Aspose.Words ได้ [ที่นี่](https://reference.aspose.com/words/net/) และสำหรับ Aspose.อีเมล [ที่นี่](https://reference-aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}