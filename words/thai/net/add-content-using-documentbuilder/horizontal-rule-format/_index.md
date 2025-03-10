---
title: รูปแบบเส้นแนวนอนในเอกสาร Word
linktitle: รูปแบบเส้นแนวนอนในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการแทรกเส้นแนวนอนที่ปรับแต่งได้ลงในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ปรับปรุงการทำงานอัตโนมัติของเอกสารของคุณ
weight: 10
url: /th/net/add-content-using-documentbuilder/horizontal-rule-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# รูปแบบเส้นแนวนอนในเอกสาร Word

## การแนะนำ

ในการพัฒนา .NET การจัดการและจัดรูปแบบเอกสาร Word ด้วยโปรแกรมอาจเป็นงานที่น่าปวดหัว โชคดีที่ Aspose.Words สำหรับ .NET นำเสนอโซลูชันที่แข็งแกร่ง ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และจัดการเอกสารโดยอัตโนมัติได้อย่างง่ายดาย บทความนี้จะเจาะลึกถึงคุณสมบัติที่สำคัญอย่างหนึ่ง: การแทรกเส้นแนวนอนในเอกสาร Word ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้นใช้ Aspose.Words การเชี่ยวชาญความสามารถนี้จะช่วยปรับปรุงกระบวนการสร้างเอกสารของคุณ

## ข้อกำหนดเบื้องต้น

ก่อนจะดำเนินการใช้กฎแนวนอนโดยใช้ Aspose.Words สำหรับ .NET โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- Visual Studio: ติดตั้ง Visual Studio IDE สำหรับการพัฒนา .NET
- Aspose.Words สำหรับ .NET: ดาวน์โหลดและติดตั้ง Aspose.Words สำหรับ .NET จาก[ที่นี่](https://releases.aspose.com/words/net/).
- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับพื้นฐานของภาษาการเขียนโปรแกรม C#
-  คลาส DocumentBuilder: ความเข้าใจของ`DocumentBuilder` คลาสใน Aspose.Words สำหรับการจัดการเอกสาร

## นำเข้าเนมสเปซ

ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:

```csharp
using Aspose.Words;
using System.Drawing;
```

เนมสเปซเหล่านี้ให้การเข้าถึงคลาส Aspose.Words สำหรับการจัดการเอกสารและคลาสมาตรฐาน .NET สำหรับการจัดการสี

มาแบ่งขั้นตอนการเพิ่มกฎแนวนอนในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ออกเป็นขั้นตอนโดยละเอียดกัน:

## ขั้นตอนที่ 1: เริ่มต้น DocumentBuilder และตั้งค่าไดเรกทอรี

 ขั้นแรกให้เริ่มต้น`DocumentBuilder` วัตถุและกำหนดเส้นทางไดเร็กทอรีที่จะบันทึกเอกสาร

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
DocumentBuilder builder = new DocumentBuilder();
```

## ขั้นตอนที่ 2: แทรกไม้บรรทัดแนวนอน

 ใช้`InsertHorizontalRule()` วิธีการของ`DocumentBuilder` คลาสที่จะเพิ่มกฎแนวนอน

```csharp
Shape shape = builder.InsertHorizontalRule();
```

## ขั้นตอนที่ 3: ปรับแต่งรูปแบบเส้นแนวนอน

 เข้าถึง`HorizontalRuleFormat` คุณสมบัติของรูปร่างที่แทรกเพื่อปรับแต่งลักษณะที่ปรากฏของกฎแนวนอน

```csharp
HorizontalRuleFormat horizontalRuleFormat = shape.HorizontalRuleFormat;
horizontalRuleFormat.Alignment = HorizontalRuleAlignment.Center;
horizontalRuleFormat.WidthPercent = 70;
horizontalRuleFormat.Height = 3;
horizontalRuleFormat.Color = Color.Blue;
horizontalRuleFormat.NoShade = true;
```

- การจัดตำแหน่ง: ระบุการจัดตำแหน่งของกฎแนวนอน (`HorizontalRuleAlignment.Center` ในตัวอย่างนี้)
- WidthPercent: กำหนดความกว้างของกฎแนวนอนเป็นเปอร์เซ็นต์ของความกว้างของหน้า (70% ในตัวอย่างนี้)
- ความสูง: กำหนดความสูงของกฎแนวนอนเป็นจุด (3 จุดในตัวอย่างนี้)
- สี: ตั้งค่าสีของกฎแนวนอน (`Color.Blue` ในตัวอย่างนี้)
- NoShade: ระบุว่ากฎแนวนอนควรมีเงาหรือไม่ (`true` ในตัวอย่างนี้)

## ขั้นตอนที่ 4: บันทึกเอกสาร

 สุดท้ายให้บันทึกเอกสารที่แก้ไขโดยใช้`Save` วิธีการของ`Document` วัตถุ.

```csharp
builder.Document.Save(dataDir + "AddContentUsingDocumentBuilder.HorizontalRuleFormat.docx");
```

## บทสรุป

การเรียนรู้การแทรกเส้นแนวนอนในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ช่วยเพิ่มความสามารถในการจัดการเอกสารอัตโนมัติของคุณ ด้วยการใช้ประโยชน์จากความยืดหยุ่นและพลังของ Aspose.Words นักพัฒนาสามารถปรับกระบวนการสร้างและจัดรูปแบบเอกสารให้มีประสิทธิภาพมากขึ้น

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังสำหรับการทำงานกับเอกสาร Word ด้วยโปรแกรมในแอปพลิเคชัน .NET

### ฉันจะดาวน์โหลด Aspose.Words สำหรับ .NET ได้อย่างไร?
 คุณสามารถดาวน์โหลด Aspose.Words สำหรับ .NET ได้จาก[ที่นี่](https://releases.aspose.com/words/net/).

### ฉันสามารถปรับแต่งลักษณะของกฎแนวนอนใน Aspose.Words ได้หรือไม่
ใช่ คุณสามารถปรับแต่งด้านต่างๆ เช่น การจัดตำแหน่ง ความกว้าง ความสูง สี และการแรเงาของกฎแนวนอนได้โดยใช้ Aspose.Words

### Aspose.Words เหมาะสำหรับการประมวลผลเอกสารระดับองค์กรหรือไม่
ใช่ Aspose.Words ถูกใช้กันอย่างแพร่หลายในสภาพแวดล้อมขององค์กรเนื่องจากความสามารถในการจัดการเอกสารอันแข็งแกร่ง

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words สำหรับ .NET ได้จากที่ไหน
 สำหรับการสนับสนุนและการมีส่วนร่วมของชุมชน โปรดไปที่[ฟอรั่ม Aspose.Words](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
