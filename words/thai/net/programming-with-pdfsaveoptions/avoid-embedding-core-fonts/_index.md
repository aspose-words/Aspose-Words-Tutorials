---
title: ลดขนาดไฟล์ PDF โดยไม่ต้องฝังฟอนต์หลัก
linktitle: ลดขนาดไฟล์ PDF โดยไม่ต้องฝังฟอนต์หลัก
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีลดขนาดไฟล์ PDF โดยไม่ต้องฝังฟอนต์หลักโดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อเพิ่มประสิทธิภาพไฟล์ PDF ของคุณ
weight: 10
url: /th/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ลดขนาดไฟล์ PDF โดยไม่ต้องฝังฟอนต์หลัก

## การแนะนำ

คุณเคยสงสัยไหมว่าทำไมไฟล์ PDF ของคุณถึงมีขนาดใหญ่ขนาดนี้? ไม่ใช่คุณคนเดียวที่คิดเช่นนั้น การฝังฟอนต์หลักอย่าง Arial และ Times New Roman เป็นสาเหตุหลักที่มักเกิดขึ้น โชคดีที่ Aspose.Words สำหรับ .NET มีวิธีแก้ไขปัญหานี้ได้อย่างชาญฉลาด ในบทช่วยสอนนี้ ฉันจะแสดงวิธีลดขนาดไฟล์ PDF ของคุณโดยหลีกเลี่ยงการฝังฟอนต์หลักเหล่านี้ มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้นการเดินทางที่น่าตื่นเต้นนี้ เรามาตรวจสอบกันก่อนว่าคุณได้เตรียมทุกสิ่งที่คุณต้องการแล้ว นี่คือรายการตรวจสอบด่วน:

-  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Aspose.Words สำหรับ .NET แล้ว หากยังไม่มี คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: คุณจะต้องมีสภาพแวดล้อมการพัฒนาเช่น Visual Studio
- เอกสาร Word: เราจะใช้เอกสาร Word (เช่น "Rendering.docx") สำหรับบทช่วยสอนนี้
- ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับ C# จะช่วยให้คุณทำตามได้

เอาล่ะ ตอนนี้เราก็พร้อมแล้ว มาเริ่มรายละเอียดกันเลย!

## นำเข้าเนมสเปซ

ขั้นแรกเลย เรามาทำการนำเข้าเนมสเปซที่จำเป็นกันก่อน ขั้นตอนนี้จะช่วยให้เราสามารถเข้าถึงฟังก์ชัน Aspose.Words ที่จำเป็นทั้งหมดได้

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: เริ่มต้นไดเรกทอรีเอกสารของคุณ

ก่อนที่เราจะเริ่มจัดการเอกสาร เราจะต้องระบุไดเรกทอรีที่เก็บเอกสารของเราเสียก่อน ซึ่งเป็นสิ่งสำคัญในการเข้าถึงไฟล์

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงที่เอกสาร Word ของคุณตั้งอยู่

## ขั้นตอนที่ 2: โหลดเอกสาร Word

ขั้นต่อไป เราต้องโหลดเอกสาร Word ที่ต้องการแปลงเป็น PDF ในตัวอย่างนี้ เราใช้เอกสารชื่อ "Rendering.docx"

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

บรรทัดโค้ดนี้จะโหลดเอกสารเข้าสู่หน่วยความจำเพื่อเตรียมประมวลผลเพิ่มเติม

## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการบันทึก PDF

ตอนนี้มาถึงส่วนที่มหัศจรรย์แล้ว! เราจะกำหนดค่าตัวเลือกการบันทึก PDF เพื่อหลีกเลี่ยงการฝังฟอนต์หลัก นี่เป็นขั้นตอนสำคัญที่ช่วยลดขนาดไฟล์ PDF

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

 การตั้งค่า`UseCoreFonts` ถึง`true` ช่วยให้แน่ใจว่าฟอนต์หลักเช่น Arial และ Times New Roman จะไม่ถูกฝังอยู่ใน PDF ซึ่งจะช่วยลดขนาดไฟล์ได้อย่างมาก

## ขั้นตอนที่ 4: บันทึกเอกสารเป็น PDF

ในที่สุด เราจะบันทึกเอกสาร Word เป็น PDF โดยใช้ตัวเลือกการบันทึกที่กำหนดค่าไว้ ขั้นตอนนี้จะสร้างไฟล์ PDF โดยไม่ฝังฟอนต์หลัก

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

และแล้วคุณก็จะได้มัน! ไฟล์ PDF ของคุณจะถูกบันทึกไว้ในไดเร็กทอรีที่ระบุโดยไม่ต้องใช้ฟอนต์หลักขนาดใหญ่เหล่านั้น

## บทสรุป

การลดขนาดไฟล์ PDF เป็นเรื่องง่ายด้วย Aspose.Words สำหรับ .NET คุณสามารถลดขนาดไฟล์ได้อย่างมากโดยหลีกเลี่ยงการฝังฟอนต์หลัก ทำให้แชร์และจัดเก็บเอกสารได้ง่ายขึ้น หวังว่าบทช่วยสอนนี้จะเป็นประโยชน์และช่วยให้คุณเข้าใจกระบวนการนี้ได้ดีขึ้น โปรดจำไว้ว่าการปรับแต่งเล็กน้อยสามารถสร้างความแตกต่างครั้งใหญ่ได้!

## คำถามที่พบบ่อย

### เหตุใดฉันจึงควรหลีกเลี่ยงการฝังฟอนต์หลักใน PDF
การหลีกเลี่ยงการฝังฟอนต์หลักจะช่วยลดขนาดไฟล์ ทำให้ง่ายต่อการแบ่งปันและจัดเก็บ

### ฉันยังสามารถดู PDF ได้อย่างถูกต้องโดยไม่ต้องฝังฟอนต์หลักหรือไม่
ใช่แล้ว แบบอักษรหลักเช่น Arial และ Times New Roman มักมีให้ใช้ในระบบส่วนใหญ่

### จะเกิดอะไรขึ้นหากฉันต้องการฝังแบบอักษรที่กำหนดเอง?
 คุณสามารถปรับแต่งได้`PdfSaveOptions`เพื่อฝังแบบอักษรเฉพาะตามต้องการ

### Aspose.Words สำหรับ .NET ใช้ได้ฟรีหรือไม่?
 Aspose.Words สำหรับ .NET ต้องมีใบอนุญาต คุณสามารถทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด
 คุณสามารถค้นหาเอกสารรายละเอียดได้[ที่นี่](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
