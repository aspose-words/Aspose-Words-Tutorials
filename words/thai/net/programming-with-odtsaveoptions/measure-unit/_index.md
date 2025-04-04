---
title: หน่วยวัด
linktitle: หน่วยวัด
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการกำหนดค่าฟีเจอร์หน่วยการวัดใน Aspose.Words สำหรับ .NET เพื่อรักษาการจัดรูปแบบเอกสารในระหว่างการแปลง ODT
weight: 10
url: /th/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# หน่วยวัด

## การแนะนำ

คุณเคยต้องแปลงเอกสาร Word ของคุณเป็นรูปแบบต่างๆ แต่ต้องการหน่วยวัดเฉพาะสำหรับเค้าโครงของคุณหรือไม่ ไม่ว่าคุณจะใช้หน่วยนิ้ว เซนติเมตร หรือจุด การทำให้มั่นใจว่าเอกสารของคุณยังคงความสมบูรณ์ระหว่างกระบวนการแปลงนั้นถือเป็นสิ่งสำคัญ ในบทช่วยสอนนี้ เราจะแนะนำวิธีการกำหนดค่าฟีเจอร์หน่วยวัดใน Aspose.Words สำหรับ .NET ฟีเจอร์อันทรงพลังนี้ช่วยให้มั่นใจว่าการจัดรูปแบบของเอกสารของคุณได้รับการรักษาไว้ตามที่คุณต้องการเมื่อแปลงเป็นรูปแบบ ODT (Open Document Text)

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มเขียนโค้ด มีบางสิ่งที่คุณจะต้องเริ่มต้น:

1. Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Aspose.Words สำหรับ .NET เวอร์ชันล่าสุดแล้ว หากยังไม่มี คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: IDE เช่น Visual Studio เพื่อเขียนและดำเนินการโค้ด C# ของคุณ
3. ความรู้พื้นฐานเกี่ยวกับ C#: การทำความเข้าใจพื้นฐานของ C# จะช่วยให้คุณทำตามบทช่วยสอนได้
4. เอกสาร Word: เตรียมเอกสาร Word ตัวอย่างไว้เพื่อใช้ในการแปลง

## นำเข้าเนมสเปซ

ก่อนที่เราจะเริ่มเขียนโค้ด เรามาตรวจสอบให้แน่ใจก่อนว่าเรามีเนมสเปซที่จำเป็นนำเข้าแล้ว โดยเพิ่ม using directives เหล่านี้ไว้ที่ด้านบนของไฟล์โค้ดของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสารของคุณ

ขั้นแรก คุณต้องกำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ นี่คือตำแหน่งที่เอกสาร Word ของคุณอยู่และตำแหน่งที่ไฟล์ที่แปลงแล้วจะถูกบันทึก

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 แทนที่`"YOUR DOCUMENTS DIRECTORY"` ด้วยเส้นทางจริงไปยังไดเร็กทอรีของคุณ วิธีนี้จะช่วยให้โค้ดของคุณทราบว่าจะค้นหาเอกสาร Word ของคุณได้ที่ใด

## ขั้นตอนที่ 2: โหลดเอกสาร Word

 ขั้นต่อไป คุณต้องโหลดเอกสาร Word ที่คุณต้องการแปลง ซึ่งทำได้โดยใช้`Document` คลาสจาก Aspose.Words

```csharp
// โหลดเอกสาร Word
Document doc = new Document(dataDir + "Document.docx");
```

ตรวจสอบให้แน่ใจว่าเอกสาร Word ของคุณชื่อ "Document.docx" อยู่ในไดเร็กทอรีที่ระบุ

## ขั้นตอนที่ 3: กำหนดค่าหน่วยการวัด

 ตอนนี้เรามาตั้งค่าหน่วยวัดสำหรับการแปลง ODT กัน นี่คือจุดที่ความมหัศจรรย์เกิดขึ้น เราจะตั้งค่า`OdtSaveOptions` ให้ใช้หน่วยนิ้วเป็นหน่วยวัด

```csharp
// การกำหนดค่าตัวเลือกการสำรองข้อมูลด้วยฟีเจอร์ "หน่วยการวัด"
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 ในตัวอย่างนี้ เราจะตั้งค่าหน่วยวัดเป็นนิ้ว คุณสามารถเลือกหน่วยอื่นได้ เช่น`OdtSaveMeasureUnit.Centimeters` หรือ`OdtSaveMeasureUnit.Points` ขึ้นอยู่กับความต้องการของคุณ

## ขั้นตอนที่ 4: แปลงเอกสารเป็น ODT

 ในที่สุดเราจะแปลงเอกสาร Word เป็นรูปแบบ ODT โดยใช้การกำหนดค่า`OdtSaveOptions`.

```csharp
// แปลงเอกสารเป็น ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

บรรทัดโค้ดนี้จะบันทึกเอกสารที่แปลงแล้วในไดเร็กทอรีที่ระบุโดยใช้หน่วยการวัดใหม่

## บทสรุป

และแล้วคุณก็ทำได้! ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถกำหนดค่าฟีเจอร์หน่วยการวัดใน Aspose.Words สำหรับ .NET ได้อย่างง่ายดาย เพื่อให้แน่ใจว่าเค้าโครงของเอกสารของคุณได้รับการรักษาไว้ระหว่างการแปลง ไม่ว่าคุณจะใช้หน่วยนิ้ว เซนติเมตร หรือจุด บทช่วยสอนนี้จะแสดงให้คุณเห็นถึงวิธีการควบคุมการจัดรูปแบบของเอกสารของคุณได้อย่างง่ายดาย

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพสำหรับการทำงานกับเอกสาร Word ด้วยโปรแกรม ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข แปลง และประมวลผลเอกสาร Word ได้โดยไม่ต้องใช้ Microsoft Word

### ฉันสามารถใช้หน่วยวัดอื่นนอกจากนิ้วได้หรือไม่
 ใช่ Aspose.Words สำหรับ .NET รองรับหน่วยวัดอื่นๆ เช่น เซนติเมตรและจุด คุณสามารถระบุหน่วยที่ต้องการได้โดยใช้`OdtSaveMeasureUnit` การนับจำนวน

### มี Aspose.Words สำหรับ .NET ให้ทดลองใช้งานฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีของ Aspose.Words สำหรับ .NET ได้จาก[ที่นี่](https://releases.aspose.com/).

### ฉันสามารถหาเอกสารสำหรับ Aspose.Words สำหรับ .NET ได้จากที่ไหน
 คุณสามารถเข้าถึงเอกสารประกอบที่ครอบคลุมสำหรับ Aspose.Words สำหรับ .NET ได้ที่[ลิงค์นี้](https://reference.aspose.com/words/net/).

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร
 หากต้องการความช่วยเหลือ คุณสามารถเยี่ยมชมฟอรัม Aspose.Words ได้ที่[ลิงค์นี้](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
