---
title: ไม่สนใจส่วนหัว ส่วนท้าย
linktitle: ไม่สนใจส่วนหัว ส่วนท้าย
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีผสานเอกสาร Word โดยไม่สนใจส่วนหัวและส่วนท้ายโดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนนี้
weight: 10
url: /th/net/join-and-append-documents/ignore-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ไม่สนใจส่วนหัว ส่วนท้าย

## การแนะนำ

การผสานเอกสาร Word เข้าด้วยกันอาจเป็นเรื่องยุ่งยากเล็กน้อย โดยเฉพาะอย่างยิ่งเมื่อคุณต้องการคงส่วนต่างๆ ไว้โดยไม่สนใจส่วนอื่นๆ เช่น ส่วนหัวและส่วนท้าย โชคดีที่ Aspose.Words สำหรับ .NET มีวิธีที่ยอดเยี่ยมในการจัดการเรื่องนี้ ในบทช่วยสอนนี้ ฉันจะอธิบายกระบวนการทีละขั้นตอนให้คุณฟัง เพื่อให้คุณเข้าใจทุกส่วน เราจะทำให้มันเรียบง่าย เป็นกันเอง และน่าสนใจ เช่นเดียวกับการพูดคุยกับเพื่อน พร้อมหรือยัง มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม เรามาตรวจสอบให้แน่ใจก่อนว่าเรามีทุกสิ่งที่เราต้องการ:

-  Aspose.Words สำหรับ .NET: คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/net/).
- Visual Studio: เวอร์ชันล่าสุดใดๆ ก็สามารถใช้ได้
- ความเข้าใจพื้นฐานเกี่ยวกับ C#: ไม่ต้องกังวล ฉันจะแนะนำคุณเกี่ยวกับโค้ดเอง
- เอกสาร Word สองฉบับ: ฉบับหนึ่งต้องผนวกเข้ากับอีกฉบับหนึ่ง

## นำเข้าเนมสเปซ

สิ่งแรกที่ต้องทำคือนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของเรา ซึ่งถือเป็นสิ่งสำคัญมาก เนื่องจากช่วยให้เราใช้คลาสและเมธอด Aspose.Words ได้โดยไม่ต้องอ้างอิงเนมสเปซแบบเต็มอยู่ตลอดเวลา

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

### สร้างโครงการใหม่

เริ่มต้นด้วยการสร้างโปรเจ็กต์ Console App ใหม่ใน Visual Studio

1. เปิด Visual Studio
2. เลือก "สร้างโครงการใหม่"
3. เลือก "แอปคอนโซล (.NET Core)"
4. ตั้งชื่อโครงการของคุณและคลิก "สร้าง"

### ติดตั้ง Aspose.Words สำหรับ .NET

ต่อไปเราต้องเพิ่ม Aspose.Words สำหรับ .NET ลงในโปรเจ็กต์ของเรา คุณสามารถทำได้ผ่านตัวจัดการแพ็กเกจ NuGet:

1. คลิกขวาที่โครงการของคุณใน Solution Explorer
2. เลือก "จัดการแพ็คเกจ NuGet"
3. ค้นหา "Aspose.Words" และติดตั้ง

## ขั้นตอนที่ 2: โหลดเอกสารของคุณ

ตอนนี้เราได้ตั้งค่าโปรเจ็กต์เรียบร้อยแล้ว เรามาโหลดเอกสาร Word ที่ต้องการรวมเข้าด้วยกันกัน สำหรับบทช่วยสอนนี้ เราจะตั้งชื่อว่า "Document source.docx" และ "Northwind traders.docx"

นี่คือวิธีโหลดโดยใช้ Aspose.Words:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDocument = new Document(dataDir + "Document source.docx");
Document dstDocument = new Document(dataDir + "Northwind traders.docx");
```

โค้ดสั้นๆ นี้จะกำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณและโหลดเอกสารลงในหน่วยความจำ

## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการนำเข้า

ก่อนที่จะรวมเอกสาร เราจะต้องตั้งค่าตัวเลือกการนำเข้า ขั้นตอนนี้มีความสำคัญเพราะช่วยให้เราระบุได้ว่าต้องการละเว้นส่วนหัวและส่วนท้าย

นี่คือโค้ดสำหรับกำหนดค่าตัวเลือกการนำเข้า:

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { IgnoreHeaderFooter = true };
```

 โดยการตั้งค่า`IgnoreHeaderFooter` ถึง`true`เรากำลังแจ้งให้ Aspose.Words ละเว้นส่วนหัวและส่วนท้ายในระหว่างกระบวนการผสาน

## ขั้นตอนที่ 4: รวมเอกสาร

เมื่อโหลดเอกสารและกำหนดค่าตัวเลือกการนำเข้าเรียบร้อยแล้ว ก็ถึงเวลาที่จะรวมเอกสาร

วิธีทำมีดังต่อไปนี้:

```csharp
dstDocument.AppendDocument(srcDocument, ImportFormatMode.KeepSourceFormatting, importFormatOptions);
```

บรรทัดโค้ดนี้จะผนวกเอกสารต้นฉบับเข้ากับเอกสารปลายทางโดยคงการจัดรูปแบบต้นฉบับไว้และละเว้นส่วนหัวและส่วนท้าย

## ขั้นตอนที่ 5: บันทึกเอกสารที่ผสาน

สุดท้ายเราจะต้องบันทึกเอกสารที่ผสาน 

นี่คือโค้ดสำหรับบันทึกเอกสารผสานของคุณ:

```csharp
dstDocument.Save(dataDir + "JoinAndAppendDocuments.IgnoreHeaderFooter.docx");
```

การดำเนินการนี้จะบันทึกเอกสารที่ผสานไว้ในไดเร็กทอรีที่ระบุโดยมีชื่อไฟล์ว่า "JoinAndAppendDocuments.IgnoreHeaderFooter.docx"

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้รวมเอกสาร Word สองฉบับเข้าด้วยกันสำเร็จแล้วโดยไม่สนใจส่วนหัวและส่วนท้ายของเอกสารโดยใช้ Aspose.Words สำหรับ .NET วิธีนี้มีประโยชน์สำหรับงานจัดการเอกสารต่างๆ ที่การดูแลรักษาส่วนต่างๆ ของเอกสารเป็นสิ่งสำคัญ

การทำงานกับ Aspose.Words สำหรับ .NET จะช่วยเพิ่มประสิทธิภาพเวิร์กโฟลว์การประมวลผลเอกสารของคุณได้อย่างมาก โปรดจำไว้ว่าหากคุณประสบปัญหาหรือต้องการข้อมูลเพิ่มเติม คุณสามารถตรวจสอบได้เสมอ[เอกสารประกอบ](https://reference.aspose.com/words/net/).

## คำถามที่พบบ่อย

### ฉันสามารถละเว้นส่วนอื่นๆ ของเอกสารนอกจากส่วนหัวและส่วนท้ายได้หรือไม่

ใช่ Aspose.Words มีตัวเลือกต่างๆ เพื่อปรับแต่งกระบวนการนำเข้า รวมถึงการละเว้นส่วนต่างๆ และการจัดรูปแบบ

### เป็นไปได้ไหมที่จะเก็บส่วนหัวและส่วนท้ายไว้แทนที่จะละเลยมัน?

 แน่นอน ตั้งค่าอย่างง่ายๆ`IgnoreHeaderFooter` ถึง`false` ใน`ImportFormatOptions`.

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.Words สำหรับ .NET หรือไม่?

 ใช่ Aspose.Words สำหรับ .NET เป็นผลิตภัณฑ์เชิงพาณิชย์ คุณสามารถรับได้[ทดลองใช้งานฟรี](https://releases.aspose.com/) หรือซื้อใบอนุญาต[ที่นี่](https://purchase.aspose.com/buy).

### ฉันสามารถรวมเอกสารมากกว่าสองฉบับด้วยวิธีนี้ได้หรือไม่?

 ใช่ คุณสามารถผนวกเอกสารหลายฉบับในลูปได้โดยการทำซ้ำ`AppendDocument` วิธีการสำหรับเอกสารเพิ่มเติมแต่ละฉบับ

### ฉันสามารถหาตัวอย่างและเอกสารเพิ่มเติมสำหรับ Aspose.Words สำหรับ .NET ได้จากที่ไหน

 คุณสามารถค้นหาเอกสารและตัวอย่างที่ครอบคลุมได้ที่[เว็บไซต์อาโพส](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
