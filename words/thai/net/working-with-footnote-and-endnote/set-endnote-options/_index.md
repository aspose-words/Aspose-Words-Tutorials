---
title: ตั้งค่าตัวเลือกท้ายบท
linktitle: ตั้งค่าตัวเลือกท้ายบท
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการตั้งค่าตัวเลือกท้ายบทในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนที่ครอบคลุมนี้
weight: 10
url: /th/net/working-with-footnote-and-endnote/set-endnote-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าตัวเลือกท้ายบท

## การแนะนำ

คุณกำลังมองหาวิธีปรับปรุงเอกสาร Word ของคุณโดยการจัดการเชิงอรรถอย่างมีประสิทธิภาพหรือไม่ ไม่ต้องมองหาที่อื่นอีกแล้ว ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนการตั้งค่าตัวเลือกเชิงอรรถในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เมื่ออ่านคู่มือนี้จบ คุณจะกลายเป็นผู้เชี่ยวชาญในการปรับแต่งเชิงอรรถให้เหมาะกับความต้องการของเอกสารของคุณ

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มบทช่วยสอนนี้ โปรดแน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

-  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Aspose.Words สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: มีการตั้งค่าสภาพแวดล้อมการพัฒนา เช่น Visual Studio
- ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C# จะเป็นประโยชน์

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็น เนมสเปซเหล่านี้ให้สิทธิ์ในการเข้าถึงคลาสและวิธีการที่จำเป็นสำหรับการจัดการเอกสาร Word

```csharp
using Aspose.Words;
using Aspose.Words.Notes;
```

## ขั้นตอนที่ 1: โหลดเอกสาร

 ขั้นแรกให้โหลดเอกสารที่เราต้องการตั้งค่าตัวเลือกท้ายบท เราจะใช้`Document` คลาสจากไลบรารี Aspose.Words เพื่อทำสิ่งนี้ให้สำเร็จ

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## ขั้นตอนที่ 2: เริ่มต้น DocumentBuilder

 ต่อไปเราจะเริ่มต้น`DocumentBuilder`คลาส คลาสนี้เป็นวิธีง่ายๆ ในการเพิ่มเนื้อหาลงในเอกสาร

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 3: เพิ่มข้อความและแทรกเชิงอรรถ

 ตอนนี้เรามาเพิ่มข้อความลงในเอกสารและแทรกเชิงอรรถกัน`InsertFootnote` วิธีการของ`DocumentBuilder` คลาสช่วยให้เราเพิ่มเชิงอรรถลงในเอกสารได้

```csharp
builder.Write("Some text");
builder.InsertFootnote(FootnoteType.Endnote, "Footnote text.");
```

## ขั้นตอนที่ 4: เข้าถึงและตั้งค่าตัวเลือก Endnote

 เพื่อปรับแต่งตัวเลือกเชิงอรรถ เราจำเป็นต้องเข้าถึง`EndnoteOptions` ทรัพย์สินของ`Document` คลาส จากนั้นเราสามารถตั้งค่าตัวเลือกต่างๆ เช่น กฎการรีสตาร์ทและตำแหน่ง

```csharp
EndnoteOptions option = doc.EndnoteOptions;
option.RestartRule = FootnoteNumberingRule.RestartPage;
option.Position = EndnotePosition.EndOfSection;
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

 สุดท้ายนี้ ให้บันทึกเอกสารด้วยตัวเลือกท้ายบทที่อัปเดตแล้ว`Save` วิธีการของ`Document` คลาสช่วยให้เราบันทึกเอกสารไปยังไดเร็กทอรีที่ระบุได้

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetEndnoteOptions.docx");
```

## บทสรุป

การตั้งค่าตัวเลือกเชิงอรรถในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET เป็นเรื่องง่ายด้วยขั้นตอนง่ายๆ เหล่านี้ คุณสามารถปรับแต่งเอกสารให้ตรงตามข้อกำหนดเฉพาะได้โดยการกำหนดกฎการรีสตาร์ทและตำแหน่งของเชิงอรรถ ด้วย Aspose.Words พลังในการจัดการเอกสาร Word อยู่ที่ปลายนิ้วของคุณ

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังสำหรับการจัดการเอกสาร Word ด้วยโปรแกรม ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และแปลงเอกสาร Word ในรูปแบบต่างๆ ได้

### ฉันสามารถใช้ Aspose.Words ได้ฟรีหรือไม่?
 คุณสามารถใช้ Aspose.Words ได้ด้วยการทดลองใช้ฟรี หากต้องการใช้งานแบบขยายเวลา คุณสามารถซื้อใบอนุญาตได้จาก[ที่นี่](https://purchase.aspose.com/buy).

### Endnotes คืออะไร
เชิงอรรถคือการอ้างอิงหรือหมายเหตุที่วางไว้ท้ายบทหรือเอกสาร โดยให้ข้อมูลเพิ่มเติมหรือการอ้างอิง

### ฉันจะปรับแต่งลักษณะที่ปรากฏของเชิงอรรถได้อย่างไร
 คุณสามารถปรับแต่งตัวเลือกเชิงอรรถ เช่น การกำหนดหมายเลข ตำแหน่ง และกฎการรีสตาร์ทโดยใช้`EndnoteOptions` คลาสใน Aspose.Words สำหรับ .NET

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ใด
 เอกสารรายละเอียดสามารถดูได้ที่[Aspose.Words สำหรับเอกสาร .NET](https://reference.aspose.com/words/net/) หน้าหนังสือ.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
