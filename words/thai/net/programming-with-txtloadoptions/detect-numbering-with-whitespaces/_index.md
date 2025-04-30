---
"description": "ค้นพบวิธีการใช้ Aspose.Words สำหรับ .NET เพื่อตรวจจับการนับหมายเลขที่มีช่องว่างในเอกสารข้อความธรรมดา และตรวจสอบให้แน่ใจว่ารายการของคุณได้รับการจดจำอย่างถูกต้อง"
"linktitle": "ตรวจจับการนับเลขด้วยช่องว่าง"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "ตรวจจับการนับเลขด้วยช่องว่าง"
"url": "/th/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ตรวจจับการนับเลขด้วยช่องว่าง

## การแนะนำ

Aspose.Words สำหรับผู้ที่ชื่นชอบ .NET! วันนี้เราจะมาเจาะลึกฟีเจอร์ที่น่าสนใจที่จะช่วยให้การจัดการรายการในเอกสารแบบข้อความธรรมดาเป็นเรื่องง่าย คุณเคยจัดการกับไฟล์ข้อความที่บางบรรทัดควรเป็นรายการ แต่เมื่อโหลดลงในเอกสาร Word กลับดูไม่ถูกต้องหรือไม่ เรามีเคล็ดลับดีๆ ซ่อนอยู่ในมือ: การตรวจจับการนับเลขด้วยช่องว่าง บทช่วยสอนนี้จะแนะนำวิธีใช้ `DetectNumberingWithWhitespaces` ตัวเลือกใน Aspose.Words สำหรับ .NET เพื่อให้แน่ใจว่ารายการของคุณได้รับการจดจำอย่างถูกต้อง แม้ว่าจะมีช่องว่างระหว่างตัวเลขและข้อความก็ตาม

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- Aspose.Words สำหรับ .NET: คุณสามารถดาวน์โหลดได้จาก [การเปิดตัว Aspose](https://releases.aspose.com/words/net/) หน้าหนังสือ.
- สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE C# อื่นๆ
- มีการติดตั้ง .NET Framework ไว้ในเครื่องของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับ C#: การทำความเข้าใจพื้นฐานจะช่วยให้คุณทำตามตัวอย่างได้

## นำเข้าเนมสเปซ

ก่อนจะเริ่มเขียนโค้ด ให้แน่ใจว่าคุณได้นำเนมสเปซที่จำเป็นเข้ามาในโปรเจ็กต์ของคุณแล้ว นี่คือตัวอย่างสั้นๆ ที่จะช่วยให้คุณเริ่มต้นได้:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

มาแบ่งกระบวนการออกเป็นขั้นตอนง่ายๆ ที่จัดการได้ แต่ละขั้นตอนจะแนะนำคุณเกี่ยวกับโค้ดที่จำเป็นและอธิบายสิ่งที่เกิดขึ้น

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอกสารของคุณ

ขั้นแรก ให้ตั้งค่าเส้นทางไปยังไดเร็กทอรีเอกสารของคุณก่อน นี่คือที่ที่ไฟล์อินพุตและเอาต์พุตของคุณจะถูกเก็บเอาไว้

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ขั้นตอนที่ 2: สร้างเอกสารแบบข้อความธรรมดา

ต่อไปเราจะสร้างเอกสารแบบข้อความธรรมดาเป็นสตริง เอกสารนี้จะมีบางส่วนที่สามารถตีความได้ว่าเป็นรายการ

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## ขั้นตอนที่ 3: กำหนดค่า LoadOptions

เพื่อตรวจจับการนับเลขด้วยช่องว่าง เราจำเป็นต้องตั้งค่า `DetectNumberingWithWhitespaces` ตัวเลือกที่จะ `true` ใน `TxtLoadOptions` วัตถุ.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## ขั้นตอนที่ 4: โหลดเอกสาร

ตอนนี้เรามาโหลดเอกสารโดยใช้ `TxtLoadOptions` เป็นพารามิเตอร์ ซึ่งจะทำให้มั่นใจได้ว่ารายการที่สี่ (พร้อมช่องว่าง) จะถูกตรวจพบอย่างถูกต้อง

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้าย ให้บันทึกเอกสารลงในไดเร็กทอรีที่คุณระบุ ซึ่งจะทำให้ได้เอกสาร Word ที่มีรายการที่ตรวจพบได้อย่างถูกต้อง

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## บทสรุป

และแล้วคุณก็จะได้มันมา! ด้วยโค้ดเพียงไม่กี่บรรทัด คุณก็จะสามารถเรียนรู้ศิลปะในการตรวจจับการนับเลขด้วยช่องว่างในเอกสารแบบข้อความธรรมดาโดยใช้ Aspose.Words สำหรับ .NET ฟีเจอร์นี้มีประโยชน์อย่างยิ่งเมื่อต้องจัดการกับรูปแบบข้อความต่างๆ และเพื่อให้แน่ใจว่ารายการของคุณแสดงอย่างถูกต้องในเอกสาร Word ของคุณ ดังนั้น ครั้งต่อไปที่คุณพบกับรายการที่ซับซ้อนเหล่านี้ คุณจะรู้ทันทีว่าต้องทำอย่างไร

## คำถามที่พบบ่อย

### อะไรคือ `DetectNumberingWithWhitespaces` ใน Aspose.Words สำหรับ .NET?
`DetectNumberingWithWhitespaces` เป็นตัวเลือกใน `TxtLoadOptions` ซึ่งช่วยให้ Aspose.Words สามารถจดจำรายการได้แม้จะมีช่องว่างระหว่างการนับหมายเลขและข้อความในรายการก็ตาม

### ฉันสามารถใช้คุณลักษณะนี้สำหรับตัวแบ่งอื่นๆ เช่น เครื่องหมายหัวข้อย่อยและวงเล็บได้หรือไม่
ใช่ Aspose.Words ตรวจจับรายการที่มีตัวกำหนดขอบเขตทั่วไป เช่น จุดหัวข้อย่อยและวงเล็บโดยอัตโนมัติ `DetectNumberingWithWhitespaces` ช่วยโดยเฉพาะกับรายการที่มีช่องว่าง

### จะเกิดอะไรขึ้นถ้าฉันไม่ใช้ `DetectNumberingWithWhitespaces`-
หากไม่มีตัวเลือกนี้ รายการที่มีช่องว่างระหว่างการนับและข้อความอาจไม่ได้รับการจดจำเป็นรายการ และรายการต่างๆ อาจปรากฏเป็นย่อหน้าธรรมดา

### คุณสมบัตินี้มีอยู่ในผลิตภัณฑ์ Aspose อื่น ๆ หรือไม่
คุณลักษณะเฉพาะนี้ได้รับการออกแบบมาเฉพาะสำหรับ Aspose.Words สำหรับ .NET ออกแบบมาเพื่อจัดการการประมวลผลเอกสาร Word

### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร
คุณสามารถขอใบอนุญาตชั่วคราวได้จาก [ใบอนุญาตชั่วคราว Aspose](https://purchase.aspose.com/temporary-license/) หน้าหนังสือ.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}