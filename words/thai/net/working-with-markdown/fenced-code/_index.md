---
"description": "เรียนรู้วิธีการเพิ่มโค้ดและสตริงข้อมูลลงในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET พร้อมคำแนะนำทีละขั้นตอน พัฒนาทักษะการจัดรูปแบบเอกสารของคุณ"
"linktitle": "รหัสรั้วกั้น"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "รหัสรั้วกั้น"
"url": "/th/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# รหัสรั้วกั้น

## การแนะนำ

สวัสดีเพื่อนนักเขียนโค้ด! วันนี้เราจะมาเจาะลึกในโลกของ Aspose.Words สำหรับ .NET เพื่อเรียนรู้ศิลปะของการเพิ่มโค้ดที่ล้อมรอบและโค้ดที่ล้อมรอบพร้อมสตริงข้อมูลลงในเอกสาร Word ของคุณ ลองนึกภาพเอกสาร Word ของคุณเป็นผืนผ้าใบ และคุณในฐานะศิลปินกำลังจะวาดภาพด้วยความแม่นยำของนักพัฒนาที่มีประสบการณ์ ด้วย Aspose.Words คุณจะสามารถปรับปรุงเอกสารของคุณโดยใช้โปรแกรมด้วยบล็อกโค้ดที่มีโครงสร้างและจัดรูปแบบ ทำให้เอกสารทางเทคนิคของคุณโดดเด่นด้วยความเป็นมืออาชีพและชัดเจน

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มบทช่วยสอน เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

- ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจทั่วไปเกี่ยวกับ C# จะช่วยให้คุณเข้าใจแนวคิดได้อย่างรวดเร็ว
- Aspose.Words สำหรับ .NET: คุณต้องติดตั้ง Aspose.Words สำหรับ .NET หากคุณยังไม่มี ให้ดาวน์โหลดมาเลย [ที่นี่](https://releases-aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE C# อื่น ๆ ที่คุณคุ้นเคย

## นำเข้าเนมสเปซ

สิ่งแรกที่ต้องทำคือนำเข้าเนมสเปซที่จำเป็น ซึ่งก็เหมือนกับการรวบรวมเครื่องมือทั้งหมดของคุณก่อนเริ่มโครงการ

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

ตอนนี้เรามาดูขั้นตอนต่างๆ กันทีละขั้นตอน

## ขั้นตอนที่ 1: การตั้งค่าโครงการของคุณ

ก่อนที่เราจะสามารถสร้างบล็อกโค้ดที่มีการจัดรูปแบบสวยงามในเอกสาร Word เราจำเป็นต้องตั้งค่าโปรเจ็กต์ใหม่ใน Visual Studio

1. สร้างโครงการใหม่: เปิด Visual Studio และสร้างแอปพลิเคชันคอนโซล C# ใหม่
2. เพิ่มการอ้างอิง Aspose.Words: ติดตั้ง Aspose.Words ผ่านตัวจัดการแพ็กเกจ NuGet คุณสามารถทำได้โดยคลิกขวาที่โปรเจ็กต์ของคุณใน Solution Explorer เลือก "จัดการแพ็กเกจ NuGet" และค้นหา Aspose.Words

## ขั้นตอนที่ 2: เริ่มต้นใช้งาน DocumentBuilder

ตอนนี้โปรเจ็กต์ของคุณตั้งค่าเสร็จเรียบร้อยแล้ว มาเริ่มต้น DocumentBuilder กันซึ่งจะเป็นเครื่องมือหลักในการเพิ่มเนื้อหาลงในเอกสาร Word

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## ขั้นตอนที่ 3: สร้างสไตล์สำหรับโค้ดที่มีรั้วกั้น

หากต้องการเพิ่มโค้ดแบบมีรั้ว เราต้องสร้างสไตล์ก่อน ลองนึกถึงการกำหนดธีมให้กับบล็อกโค้ดของเรา

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## ขั้นตอนที่ 4: เพิ่มโค้ดที่ซ่อนไว้ในเอกสาร

เมื่อสไตล์ของเราพร้อมแล้ว เราก็สามารถเพิ่มบล็อกโค้ดที่มีรั้วล้อมลงในเอกสารได้

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## ขั้นตอนที่ 5: สร้างสไตล์สำหรับโค้ดที่มีรั้วล้อมด้วยสตริงข้อมูล

บางครั้งคุณอาจต้องการระบุภาษาการเขียนโปรแกรมหรือเพิ่มข้อมูลเพิ่มเติมลงในบล็อกโค้ดของคุณ มาสร้างสไตล์สำหรับสิ่งนั้นกัน

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## ขั้นตอนที่ 6: เพิ่มโค้ดที่มีรั้วพร้อมสตริงข้อมูลลงในเอกสาร

ตอนนี้ มาเพิ่มบล็อกโค้ดที่มีรั้วล้อมรอบพร้อมสตริงข้อมูลเพื่อระบุว่าเป็นโค้ด C#

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## บทสรุป

ขอแสดงความยินดี! คุณเพิ่งเพิ่มบล็อกโค้ดที่มีรั้วกั้นและโค้ดที่มีสตริงข้อมูลลงในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET นี่เป็นเพียงส่วนเล็กๆ ของเนื้อหาทั้งหมดเท่านั้น ด้วย Aspose.Words คุณสามารถทำให้การประมวลผลเอกสารของคุณเป็นแบบอัตโนมัติและเพิ่มประสิทธิภาพไปสู่ระดับใหม่ได้ เรียนรู้ต่อไปและสนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และแปลงเอกสาร Word ได้ด้วยโปรแกรม

### ฉันสามารถใช้ Aspose.Words กับภาษาการเขียนโปรแกรมอื่นได้หรือไม่
Aspose.Words รองรับภาษา .NET เป็นหลัก แต่ยังมีเวอร์ชันสำหรับ Java, Python และภาษาอื่นๆ อีกด้วย

### Aspose.Words ใช้ได้ฟรีไหม?
Aspose.Words เป็นผลิตภัณฑ์เชิงพาณิชย์ แต่คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้ [ที่นี่](https://releases.aspose.com/) เพื่อสำรวจคุณสมบัติของมัน

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words ได้อย่างไร?
คุณสามารถรับการสนับสนุนจากชุมชนและนักพัฒนา Aspose ได้ [ที่นี่](https://forum-aspose.com/c/words/8).

### Aspose.Words มีฟีเจอร์อื่น ๆ อะไรอีกบ้าง?
Aspose.Words มีคุณสมบัติมากมาย เช่น การแปลงเอกสาร การสร้างเอกสารตามเทมเพลต การสร้างรายงาน และอื่นๆ อีกมากมาย


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}