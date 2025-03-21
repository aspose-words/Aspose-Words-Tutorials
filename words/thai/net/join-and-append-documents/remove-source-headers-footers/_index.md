---
title: ลบส่วนหัวและส่วนท้ายของแหล่งที่มา
linktitle: ลบส่วนหัวและส่วนท้ายของแหล่งที่มา
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการลบส่วนหัวและส่วนท้ายในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ทำให้การจัดการเอกสารของคุณง่ายขึ้นด้วยคำแนะนำทีละขั้นตอนของเรา
weight: 10
url: /th/net/join-and-append-documents/remove-source-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ลบส่วนหัวและส่วนท้ายของแหล่งที่มา

## การแนะนำ

ในคู่มือฉบับสมบูรณ์นี้ เราจะเจาะลึกถึงวิธีการลบส่วนหัวและส่วนท้ายออกจากเอกสาร Word อย่างมีประสิทธิภาพโดยใช้ Aspose.Words สำหรับ .NET ส่วนหัวและส่วนท้ายมักใช้สำหรับการกำหนดหมายเลขหน้า ชื่อเอกสาร หรือเนื้อหาที่ซ้ำกันอื่นๆ ในเอกสาร Word ไม่ว่าคุณจะกำลังรวมเอกสารหรือจัดระเบียบการจัดรูปแบบ การเชี่ยวชาญกระบวนการนี้จะทำให้การจัดการเอกสารของคุณราบรื่นขึ้น มาสำรวจกระบวนการทีละขั้นตอนในการบรรลุผลนี้โดยใช้ Aspose.Words สำหรับ .NET กัน

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มบทช่วยสอนนี้ ให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นดังต่อไปนี้:

1. สภาพแวดล้อมการพัฒนา: มีการติดตั้ง Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET อื่น ๆ
2.  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ดาวน์โหลดและติดตั้ง Aspose.Words สำหรับ .NET แล้ว หากยังไม่ได้ดาวน์โหลด คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/net/).
3. ความรู้พื้นฐาน: ความคุ้นเคยกับการเขียนโปรแกรม C# และพื้นฐานของ .NET framework

## นำเข้าเนมสเปซ

ก่อนที่คุณจะเริ่มเขียนโค้ด โปรดแน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นลงในไฟล์ C# ของคุณ:

```csharp
using Aspose.Words;
```

## ขั้นตอนที่ 1: โหลดเอกสารต้นฉบับ

 ขั้นแรก คุณต้องโหลดเอกสารต้นฉบับที่คุณต้องการลบส่วนหัวและส่วนท้าย แทนที่`"YOUR DOCUMENT DIRECTORY"` โดยมีเส้นทางจริงไปยังไดเร็กทอรีเอกสารของคุณซึ่งเอกสารต้นฉบับตั้งอยู่

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## ขั้นตอนที่ 2: สร้างหรือโหลดเอกสารปลายทาง

 หากคุณยังไม่ได้สร้างเอกสารปลายทางที่คุณต้องการวางเนื้อหาที่แก้ไข คุณสามารถสร้างเอกสารใหม่ได้`Document` วัตถุหรือโหลดอันที่มีอยู่แล้ว

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## ขั้นตอนที่ 3: ล้างส่วนหัวและส่วนท้ายออกจากส่วนต่างๆ

ทำซ้ำผ่านแต่ละส่วนในเอกสารต้นฉบับ (`srcDoc`) และล้างส่วนหัวและส่วนท้ายออก

```csharp
foreach (Section section in srcDoc.Sections)
{
    section.ClearHeadersFooters();
}
```

## ขั้นตอนที่ 4: จัดการการตั้งค่า LinkToPrevious

เพื่อป้องกันไม่ให้ส่วนหัวและส่วนท้ายยังคงดำเนินต่อไปในเอกสารปลายทาง (`dstDoc` ) เพื่อให้แน่ใจว่า`LinkToPrevious` การตั้งค่าสำหรับส่วนหัวและส่วนท้ายถูกตั้งค่าเป็น`false`.

```csharp
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## ขั้นตอนที่ 5: ผนวกเอกสารที่แก้ไขแล้วลงในเอกสารปลายทาง

สุดท้ายให้ผนวกเนื้อหาที่แก้ไขจากเอกสารต้นฉบับ (`srcDoc`) ไปยังเอกสารปลายทาง (`dstDoc`) โดยยังคงรักษาการจัดรูปแบบต้นฉบับไว้

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## ขั้นตอนที่ 6: บันทึกเอกสารผลลัพธ์

บันทึกเอกสารสุดท้ายพร้อมลบส่วนหัวและส่วนท้ายไปยังไดเร็กทอรีที่คุณระบุ

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.RemoveSourceHeadersFooters.docx");
```

## บทสรุป

การลบส่วนหัวและส่วนท้ายออกจากเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เป็นกระบวนการง่ายๆ ที่สามารถเพิ่มประสิทธิภาพงานจัดการเอกสารได้อย่างมาก หากปฏิบัติตามขั้นตอนที่ระบุไว้ข้างต้น คุณจะสามารถทำความสะอาดเอกสารได้อย่างมีประสิทธิภาพเพื่อให้ดูสวยงามและเป็นมืออาชีพ

## คำถามที่พบบ่อย

### ฉันสามารถลบส่วนหัวและส่วนท้ายจากเฉพาะส่วนต่างๆ ได้หรือไม่
ใช่ คุณสามารถทำซ้ำตามส่วนต่างๆ และเลือกล้างส่วนหัวและส่วนท้ายตามต้องการได้

### Aspose.Words สำหรับ .NET รองรับการลบส่วนหัวและส่วนท้ายในเอกสารหลายฉบับหรือไม่
แน่นอน คุณสามารถจัดการส่วนหัวและส่วนท้ายของเอกสารหลายฉบับได้โดยใช้ Aspose.Words สำหรับ .NET

###  จะเกิดอะไรขึ้นหากฉันลืมตั้งค่า`LinkToPrevious` to `false`?
ส่วนหัวและส่วนท้ายจากเอกสารต้นฉบับสามารถต่อเนื่องไปยังเอกสารปลายทางได้

### ฉันสามารถลบส่วนหัวและส่วนท้ายโดยใช้โปรแกรมโดยไม่ส่งผลกระทบต่อการจัดรูปแบบอื่นๆ ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET ช่วยให้คุณลบส่วนหัวและส่วนท้ายได้ในขณะที่ยังคงการจัดรูปแบบส่วนที่เหลือของเอกสารไว้

### ฉันสามารถหาทรัพยากรและการสนับสนุนเพิ่มเติมสำหรับ Aspose.Words สำหรับ .NET ได้จากที่ไหน
 เยี่ยมชม[Aspose.Words สำหรับเอกสาร .NET](https://reference.aspose.com/words/net/) สำหรับข้อมูลอ้างอิงและตัวอย่าง API โดยละเอียด

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
