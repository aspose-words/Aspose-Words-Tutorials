---
title: คัดลอกรูปแบบเอกสาร Word
linktitle: คัดลอกรูปแบบเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีคัดลอกรูปแบบเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อให้แน่ใจว่าการจัดรูปแบบเอกสารมีความสอดคล้องกันโดยไม่ต้องใช้ความพยายามมาก
weight: 10
url: /th/net/programming-with-styles-and-themes/copy-styles/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# คัดลอกรูปแบบเอกสาร Word

## การแนะนำ

หากคุณเคยจำเป็นต้องทำให้เอกสารดูสอดคล้องกับเอกสารอื่น คุณอาจเคยพบกับความท้าทายในการคัดลอกรูปแบบ ลองนึกภาพว่าคุณเป็นนักออกแบบที่ได้รับมอบหมายให้ดูแลให้รายงานใหม่ทุกฉบับตรงกับรูปแบบของเทมเพลตที่มีอยู่ การใช้ Aspose.Words สำหรับ .NET จะช่วยให้คุณทำงานนี้ได้ง่ายขึ้น และทำให้เอกสารของคุณดูคมชัดและสม่ำเสมอ ในบทช่วยสอนนี้ เราจะเจาะลึกถึงวิธีการคัดลอกรูปแบบจากเอกสาร Word หนึ่งไปยังอีกเอกสารหนึ่งได้อย่างง่ายดาย มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1.  ไลบรารี Aspose.Words สำหรับ .NET: คุณจะต้องมีสิ่งนี้เพื่อทำงานกับเอกสาร Word ใน .NET คุณสามารถดาวน์โหลดได้จาก[ดาวน์โหลด Aspose.Words สำหรับ .NET](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา .NET: คุณควรมีการตั้งค่าสภาพแวดล้อมการพัฒนา .NET ที่ใช้งานได้ เช่น Visual Studio
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับ C# จะช่วยให้คุณเข้าใจและนำชิ้นส่วนโค้ดไปใช้ได้อย่างมีประสิทธิภาพ

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณจะต้องรวมเนมสเปซที่จำเป็นไว้ในโปรเจ็กต์ C# ของคุณ ซึ่งจะช่วยให้คุณสามารถเข้าถึงคลาสและเมธอดที่ Aspose.Words จัดเตรียมไว้ได้ ต่อไปนี้คือวิธีที่คุณสามารถนำเข้าเนมสเปซที่จำเป็นได้:

```csharp
using Aspose.Words;
```

ด้วยการรวมเนมสเปซนี้ คุณจะสามารถเข้าถึงฟีเจอร์อันทรงพลังทั้งหมดของไลบรารี Aspose.Words ได้

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสารของคุณ

 ขั้นแรก คุณต้องกำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ นี่คือตำแหน่งที่ Aspose.Words จะค้นหาไฟล์ของคุณ แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงที่คุณเก็บเอกสารไว้

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ขั้นตอนที่ 2: โหลดเอกสารของคุณ

ในขั้นตอนนี้ คุณจะโหลดเอกสารต้นฉบับและเอกสารปลายทาง เอกสารต้นฉบับคือเอกสารที่มีรูปแบบที่คุณต้องการคัดลอก ในขณะที่เอกสารปลายทางคือเอกสารที่จะนำรูปแบบเหล่านี้ไปใช้ 

```csharp
Document doc = new Document();
Document target = new Document(dataDir + "Rendering.docx");
```

 ที่นี่,`Rendering.docx` เป็นเอกสารต้นฉบับของคุณที่มีรูปแบบที่คุณต้องการคัดลอก`doc` วัตถุแสดงถึงเอกสารเป้าหมายที่จะคัดลอกสไตล์

## ขั้นตอนที่ 3: คัดลอกสไตล์จากแหล่งที่มาไปยังเป้าหมาย

 เมื่อโหลดเอกสารทั้งสองแล้ว คุณสามารถคัดลอกสไตล์ได้แล้ว`CopyStylesFromTemplate` วิธีนี้เป็นเครื่องมือของคุณสำหรับงานนี้ โดยจะคัดลอกรูปแบบจาก`doc`เทมเพลตไปที่`target` เอกสาร.

```csharp
target.CopyStylesFromTemplate(doc);
```

## ขั้นตอนที่ 4: บันทึกเอกสารที่อัปเดต

หลังจากคัดลอกสไตล์แล้ว ให้บันทึกเอกสารเป้าหมายที่อัปเดต ขั้นตอนนี้จะช่วยให้แน่ใจว่าการเปลี่ยนแปลงทั้งหมดที่คุณทำจะถูกเก็บไว้ในไฟล์ใหม่

```csharp
doc.Save(dataDir + "WorkingWithStylesAndThemes.CopyStyles.docx");
```

รหัสนี้จะบันทึกเอกสารที่แก้ไขด้วยชื่อใหม่ โดยรักษาไฟล์ต้นฉบับของคุณไว้

## บทสรุป

และแล้วคุณก็ทำได้! การคัดลอกรูปแบบระหว่างเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เป็นกระบวนการที่ตรงไปตรงมาเมื่อคุณคุ้นเคยกับมันแล้ว การทำตามขั้นตอนเหล่านี้จะช่วยให้คุณมั่นใจได้ว่าเอกสารของคุณจะมีรูปลักษณ์และความรู้สึกที่สอดคล้องกัน ทำให้การทำงานของคุณมีประสิทธิภาพและเป็นมืออาชีพมากขึ้น ไม่ว่าคุณจะกำลังอัปเดตรายงานหรือสร้างเทมเพลตใหม่ วิธีนี้จะช่วยประหยัดเวลาและความพยายามของคุณ ทำให้คุณสามารถมุ่งเน้นไปที่เนื้อหาแทนที่จะจัดรูปแบบ

## คำถามที่พบบ่อย

###  จุดประสงค์ของการ`CopyStylesFromTemplate` method?  
 การ`CopyStylesFromTemplate` วิธีการคัดลอกรูปแบบจากเอกสารหนึ่งไปยังอีกเอกสารหนึ่ง ทำให้แน่ใจว่าเอกสารเป้าหมายจะสืบทอดการจัดรูปแบบของเอกสารต้นฉบับ

###  ฉันสามารถใช้`CopyStylesFromTemplate` with documents in different formats?  
 ไม่,`CopyStylesFromTemplate` วิธีนี้ใช้ได้กับเอกสารที่มีรูปแบบเดียวกันเท่านั้น โดยทั่วไปคือ DOCX

### ฉันจะตรวจสอบได้อย่างไรว่าสไตล์ได้รับการคัดลอกสำเร็จแล้ว?  
เปิดเอกสารเป้าหมายและตรวจสอบการตั้งค่ารูปแบบ คุณควรเห็นรูปแบบจากเอกสารต้นฉบับที่นำไปใช้

### จะทำอย่างไรหากเอกสารเป้าหมายมีสไตล์อยู่แล้ว?  
 การ`CopyStylesFromTemplate` วิธีการนี้จะเขียนทับรูปแบบที่มีอยู่แล้วในเอกสารเป้าหมายด้วยรูปแบบจากเอกสารต้นฉบับ

### Aspose.Words สำหรับ .NET ใช้ได้ฟรีหรือไม่?  
 Aspose.Words สำหรับ .NET เป็นผลิตภัณฑ์เชิงพาณิชย์ แต่คุณสามารถทดลองใช้งานฟรีได้จาก[Aspose.Words สำหรับทดลองใช้งาน .NET ฟรี](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
