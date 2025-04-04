---
title: เขียนกฎ CSS ทั้งหมดในไฟล์เดียว
linktitle: เขียนกฎ CSS ทั้งหมดในไฟล์เดียว
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการแปลงเอกสาร Word เป็น HTML โดยใช้ Aspose.Words สำหรับ .NET พร้อมด้วยกฎ CSS ทั้งหมดในไฟล์เดียวเพื่อให้โค้ดสะอาดขึ้นและดูแลรักษาง่ายกว่า
weight: 10
url: /th/net/programming-with-htmlfixedsaveoptions/write-all-css-rules-in-single-file/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เขียนกฎ CSS ทั้งหมดในไฟล์เดียว

## การแนะนำ

คุณเคยพบว่าตัวเองติดอยู่ในเว็บของกฎ CSS ที่กระจัดกระจายไปทั่วเมื่อแปลงเอกสาร Word เป็น HTML หรือไม่ ไม่ต้องกังวล! วันนี้เราจะมาเจาะลึกฟีเจอร์สุดเจ๋งของ Aspose.Words สำหรับ .NET ที่ให้คุณเขียนกฎ CSS ทั้งหมดในไฟล์เดียว ซึ่งไม่เพียงแต่จะทำให้โค้ดของคุณเป็นระเบียบเรียบร้อยเท่านั้น แต่ยังทำให้ชีวิตของคุณง่ายขึ้นมากอีกด้วย เตรียมตัวให้พร้อม แล้วมาเริ่มต้นการเดินทางสู่ผลลัพธ์ HTML ที่สะอาดและมีประสิทธิภาพยิ่งขึ้นกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงรายละเอียด เรามาเริ่มกันก่อนดีกว่า นี่คือสิ่งที่คุณต้องทำ:

1.  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณมีไลบรารี Aspose.Words สำหรับ .NET หากคุณยังไม่มี คุณสามารถทำได้[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา .NET: คุณจะต้องมีสภาพแวดล้อมการพัฒนา .NET ที่ติดตั้งไว้ในเครื่องของคุณ Visual Studio เป็นตัวเลือกยอดนิยม
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C# จะเป็นประโยชน์
4. เอกสาร Word: เตรียมเอกสาร Word (.docx) ที่คุณต้องการแปลงไว้

## นำเข้าเนมสเปซ

ขั้นแรก ให้ทำการอิมพอร์ตเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณก่อน ซึ่งจะช่วยให้เราเข้าถึงฟังก์ชัน Aspose.Words ได้อย่างง่ายดาย

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

เอาล่ะ มาแบ่งกระบวนการออกเป็นขั้นตอนที่ทำตามได้ง่าย ๆ กัน แต่ละขั้นตอนจะแนะนำคุณตลอดขั้นตอนเพื่อให้แน่ใจว่าทุกอย่างดำเนินไปอย่างราบรื่น

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสารของคุณ

ขั้นแรก เราต้องกำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ นี่คือที่ที่เอกสาร Word ของคุณถูกเก็บและที่ที่ HTML ที่แปลงแล้วจะถูกบันทึก

```csharp
// เส้นทางการเข้าถึงไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## ขั้นตอนที่ 2: โหลดเอกสาร Word

 ต่อไปเราจะโหลดเอกสาร Word ที่คุณต้องการแปลงเป็น HTML ซึ่งทำได้โดยใช้`Document` คลาสจากไลบรารี Aspose.Words

```csharp
// โหลดเอกสาร Word
Document doc = new Document(dataDir + "Document.docx");
```

## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการบันทึก HTML

 ตอนนี้ เราต้องกำหนดค่าตัวเลือกการบันทึก HTML โดยเฉพาะอย่างยิ่ง เราต้องการเปิดใช้งานฟีเจอร์ที่เขียนกฎ CSS ทั้งหมดลงในไฟล์เดียว ซึ่งทำได้โดยตั้งค่า`SaveFontFaceCssSeparately`ทรัพย์สินที่จะ`false`.

```csharp
// กำหนดค่าตัวเลือกการสำรองข้อมูลด้วยฟีเจอร์ "เขียนกฎ CSS ทั้งหมดในไฟล์เดียว"
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## ขั้นตอนที่ 4: แปลงเอกสารเป็น HTML คงที่

สุดท้าย เราจะบันทึกเอกสารเป็นไฟล์ HTML โดยใช้ตัวเลือกการบันทึกที่กำหนดไว้ ขั้นตอนนี้จะช่วยให้แน่ใจว่ากฎ CSS ทั้งหมดถูกเขียนไว้ในไฟล์เดียว

```csharp
// แปลงเอกสารเป็น HTML คงที่
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.WriteAllCssRulesInSingleFile.html", saveOptions);
```

## บทสรุป

และแล้วคุณก็ทำได้! ด้วยโค้ดเพียงไม่กี่บรรทัด คุณก็แปลงเอกสาร Word ของคุณเป็น HTML ที่มีกฎ CSS ทั้งหมดที่จัดอย่างเป็นระเบียบในไฟล์เดียวได้สำเร็จ วิธีนี้ไม่เพียงแต่ทำให้การจัดการ CSS ของคุณง่ายขึ้นเท่านั้น แต่ยังช่วยเพิ่มความสามารถในการบำรุงรักษาเอกสาร HTML ของคุณอีกด้วย ดังนั้น ครั้งต่อไปที่คุณได้รับมอบหมายให้แปลงเอกสาร Word คุณจะรู้ทันทีว่าต้องจัดการทุกอย่างให้เป็นระเบียบอย่างไร!

## คำถามที่พบบ่อย

### เหตุใดฉันจึงควรใช้ไฟล์ CSS เดียวสำหรับผลลัพธ์ HTML
การใช้ไฟล์ CSS เพียงไฟล์เดียวช่วยให้การจัดการและการบำรุงรักษารูปแบบต่างๆ ง่ายขึ้น ทำให้ HTML ของคุณสะอาดขึ้นและมีประสิทธิภาพมากขึ้น

### ฉันสามารถแยกกฎ CSS ของแบบอักษรได้หรือไม่หากจำเป็น?
 ใช่ โดยการตั้งค่า`SaveFontFaceCssSeparately` ถึง`true`คุณสามารถแยกกฎ CSS ของแบบอักษรออกเป็นไฟล์อื่นได้

### Aspose.Words สำหรับ .NET ใช้ได้ฟรีหรือไม่?
 Aspose.Words เสนอการทดลองใช้ฟรีซึ่งคุณสามารถ[ดาวน์โหลดที่นี่](https://releases.aspose.com/) หากต้องการใช้ต่อ โปรดพิจารณาซื้อใบอนุญาต[ที่นี่](https://purchase.aspose.com/buy).

### Aspose.Words สำหรับ .NET สามารถแปลงเป็นรูปแบบอื่นใดได้อีกบ้าง
Aspose.Words สำหรับ .NET รองรับรูปแบบต่างๆ รวมถึง PDF, TXT และรูปแบบรูปภาพเช่น JPEG และ PNG

### ฉันสามารถหาทรัพยากรเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด
 ตรวจสอบออก[เอกสารประกอบ](https://reference.aspose.com/words/net/) สำหรับคำแนะนำที่ครอบคลุมและการอ้างอิง API

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
