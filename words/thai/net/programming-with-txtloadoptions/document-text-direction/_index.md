---
title: ทิศทางข้อความเอกสาร
linktitle: ทิศทางข้อความเอกสาร
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีกำหนดทิศทางข้อความในเอกสารใน Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนนี้ เหมาะอย่างยิ่งสำหรับการจัดการภาษาที่อ่านจากขวาไปซ้าย
weight: 10
url: /th/net/programming-with-txtloadoptions/document-text-direction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ทิศทางข้อความเอกสาร

## การแนะนำ

เมื่อทำงานกับเอกสาร Word โดยเฉพาะเอกสารที่มีหลายภาษาหรือต้องมีการจัดรูปแบบพิเศษ การกำหนดทิศทางของข้อความอาจมีความสำคัญ ตัวอย่างเช่น เมื่อจัดการกับภาษาที่อ่านจากขวาไปซ้าย เช่น ภาษาฮีบรูหรืออาหรับ คุณอาจต้องปรับทิศทางของข้อความให้เหมาะสม ในคู่มือนี้ เราจะแนะนำวิธีกำหนดทิศทางของข้อความในเอกสารโดยใช้ Aspose.Words สำหรับ .NET 

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเจาะลึกโค้ด ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  ไลบรารี Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Aspose.Words สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์อาโพส](https://releases.aspose.com/words/net/).
- Visual Studio: สภาพแวดล้อมการพัฒนาสำหรับการเขียนและดำเนินการโค้ด C#
- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะเป็นประโยชน์เนื่องจากเราจะได้เขียนโค้ดบางส่วน

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นสำหรับการใช้งาน Aspose.Words ในโปรเจ็กต์ของคุณ โดยคุณสามารถทำได้ดังนี้:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

เนมสเปซเหล่านี้ให้สิทธิ์ในการเข้าถึงคลาสและวิธีการที่จำเป็นในการจัดการเอกสาร Word

## ขั้นตอนที่ 1: กำหนดเส้นทางไปยังไดเรกทอรีเอกสารของคุณ

ขั้นแรก ให้กำหนดเส้นทางไปยังตำแหน่งที่เอกสารของคุณตั้งอยู่ ซึ่งเป็นสิ่งสำคัญสำหรับการโหลดและบันทึกไฟล์อย่างถูกต้อง

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงที่คุณเก็บเอกสารไว้

## ขั้นตอนที่ 2: สร้าง TxtLoadOptions พร้อมการตั้งค่าทิศทางเอกสาร

 ต่อไปคุณจะต้องสร้างอินสแตนซ์ของ`TxtLoadOptions` และตั้งค่าของมัน`DocumentDirection` คุณสมบัตินี้แจ้งให้ Aspose.Words ทราบว่าจะจัดการทิศทางของข้อความในเอกสารอย่างไร

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

 ในตัวอย่างนี้เราใช้`DocumentDirection.Auto` เพื่อให้ Aspose.Words กำหนดทิศทางโดยอัตโนมัติตามเนื้อหา

## ขั้นตอนที่ 3: โหลดเอกสาร

 ตอนนี้โหลดเอกสารโดยใช้`Document` คลาสและที่กำหนดไว้ก่อนหน้านี้`loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

 ที่นี่,`"Hebrew text.txt"` คือชื่อไฟล์ข้อความของคุณ ตรวจสอบว่าไฟล์นี้มีอยู่ในไดเร็กทอรีที่คุณระบุ

## ขั้นตอนที่ 4: เข้าถึงและตรวจสอบการจัดรูปแบบสองทิศทางของย่อหน้า

เพื่อยืนยันว่าทิศทางของข้อความได้รับการตั้งค่าอย่างถูกต้อง ให้เข้าถึงย่อหน้าแรกของเอกสารและตรวจสอบการจัดรูปแบบทิศทางสองทาง

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

ขั้นตอนนี้มีประโยชน์ในการดีบักและตรวจยืนยันว่าทิศทางข้อความในเอกสารได้รับการใช้ตามที่คาดหวังหรือไม่

## ขั้นตอนที่ 5: บันทึกเอกสารด้วยการตั้งค่าใหม่

สุดท้าย ให้บันทึกเอกสารเพื่อใช้และคงการเปลี่ยนแปลงไว้

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

 ที่นี่,`"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` คือชื่อของไฟล์เอาต์พุต โปรดเลือกชื่อที่สะท้อนถึงการเปลี่ยนแปลงที่คุณได้ทำ

## บทสรุป

การตั้งค่าทิศทางของข้อความในเอกสาร Word เป็นกระบวนการที่ตรงไปตรงมาด้วย Aspose.Words สำหรับ .NET โดยทำตามขั้นตอนเหล่านี้ คุณสามารถกำหนดค่าวิธีการจัดการข้อความจากขวาไปซ้ายหรือซ้ายไปขวาในเอกสารของคุณได้อย่างง่ายดาย ไม่ว่าคุณจะทำงานกับเอกสารหลายภาษาหรือต้องการจัดรูปแบบทิศทางของข้อความสำหรับภาษาเฉพาะ Aspose.Words ก็มีโซลูชันที่แข็งแกร่งเพื่อตอบสนองความต้องการของคุณ

## คำถามที่พบบ่อย

###  อะไรคือ`DocumentDirection` property used for?

 การ`DocumentDirection` ทรัพย์สินใน`TxtLoadOptions` กำหนดทิศทางข้อความสำหรับเอกสาร สามารถตั้งค่าได้`DocumentDirection.Auto`, `DocumentDirection.LeftToRight` , หรือ`DocumentDirection.RightToLeft`.

### ฉันสามารถกำหนดทิศทางข้อความสำหรับย่อหน้าเฉพาะแทนทั้งเอกสารได้ไหม

 ใช่ คุณสามารถกำหนดทิศทางข้อความสำหรับย่อหน้าเฉพาะได้โดยใช้`ParagraphFormat.Bidi` ทรัพย์สินแต่`TxtLoadOptions.DocumentDirection` คุณสมบัติกำหนดทิศทางเริ่มต้นให้กับเอกสารทั้งหมด

###  รูปแบบไฟล์ใดบ้างที่รองรับการโหลดด้วย`TxtLoadOptions`?

`TxtLoadOptions` ใช้เป็นหลักในการโหลดไฟล์ข้อความ (.txt) สำหรับรูปแบบไฟล์อื่น ให้ใช้คลาสอื่น เช่น`DocLoadOptions` หรือ`DocxLoadOptions`.

### ฉันจะจัดการเอกสารที่มีคำแนะนำแบบข้อความผสมกันได้อย่างไร

 สำหรับเอกสารที่มีข้อความผสมกัน คุณอาจต้องจัดการการจัดรูปแบบตามย่อหน้า ใช้`ParagraphFormat.Bidi` คุณสมบัติในการปรับเปลี่ยนทิศทางของแต่ละย่อหน้าตามความจำเป็น

### ฉันสามารถหาข้อมูลเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ไหน

 สำหรับรายละเอียดเพิ่มเติมโปรดตรวจสอบ[Aspose.Words สำหรับเอกสาร .NET](https://reference.aspose.com/words/net/) คุณยังสามารถสำรวจแหล่งข้อมูลเพิ่มเติมได้ เช่น[ลิงค์ดาวน์โหลด](https://releases.aspose.com/words/net/), [ซื้อ](https://purchase.aspose.com/buy), [ทดลองใช้งานฟรี](https://releases.aspose.com/), [ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) , และ[สนับสนุน](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
