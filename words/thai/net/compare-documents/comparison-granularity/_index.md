---
"description": "เรียนรู้คุณลักษณะการเปรียบเทียบรายละเอียดในเอกสาร Word ของ Aspose.Words สำหรับ .NET ที่ช่วยให้สามารถเปรียบเทียบเอกสารทีละอักขระ และรายงานการเปลี่ยนแปลงที่เกิดขึ้น"
"linktitle": "การเปรียบเทียบความละเอียดในเอกสาร Word"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "การเปรียบเทียบความละเอียดในเอกสาร Word"
"url": "/th/net/compare-documents/comparison-granularity/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การเปรียบเทียบความละเอียดในเอกสาร Word

ต่อไปนี้เป็นคู่มือทีละขั้นตอนในการอธิบายโค้ดต้นฉบับ C# ด้านล่าง ซึ่งใช้คุณลักษณะ Compare Granularity ในเอกสาร Word ของ Aspose.Words สำหรับ .NET

## ขั้นตอนที่ 1: บทนำ

คุณลักษณะ Compare Granularity ของ Aspose.Words สำหรับ .NET ช่วยให้คุณเปรียบเทียบเอกสารในระดับอักขระ ซึ่งหมายความว่าอักขระแต่ละตัวจะถูกเปรียบเทียบและจะรายงานการเปลี่ยนแปลงตามนั้น

## ขั้นตอนที่ 2: การตั้งค่าสภาพแวดล้อม

ก่อนเริ่มต้น คุณต้องตั้งค่าสภาพแวดล้อมการพัฒนาของคุณให้ทำงานกับ Aspose.Words สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี Aspose.Words และมีโปรเจ็กต์ C# ที่เหมาะสมเพื่อฝังโค้ดลงไป

## ขั้นตอนที่ 3: เพิ่มส่วนประกอบที่จำเป็น

หากต้องการใช้ฟีเจอร์ Compare Granularity ของ Aspose.Words สำหรับ .NET คุณจะต้องเพิ่มแอสเซมบลีที่จำเป็นลงในโปรเจ็กต์ของคุณ ตรวจสอบให้แน่ใจว่าคุณมีการอ้างอิง Aspose.Words ที่ถูกต้องในโปรเจ็กต์ของคุณ

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## ขั้นตอนที่ 4: การสร้างเอกสาร

ในขั้นตอนนี้ เราจะสร้างเอกสารสองฉบับโดยใช้คลาส DocumentBuilder เอกสารเหล่านี้จะถูกใช้ในการเปรียบเทียบ

```csharp
// สร้างเอกสาร A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// สร้างเอกสาร B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## ขั้นตอนที่ 5: การกำหนดค่าตัวเลือกการเปรียบเทียบ

ในขั้นตอนนี้ เราจะกำหนดค่าตัวเลือกการเปรียบเทียบเพื่อระบุระดับรายละเอียดของการเปรียบเทียบ ที่นี่เราจะใช้ระดับรายละเอียดของอักขระ

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## ขั้นตอนที่ 6: การเปรียบเทียบเอกสาร

ต่อไปเราจะเปรียบเทียบเอกสารโดยใช้เมธอด Compare ของคลาส Document การเปลี่ยนแปลงจะถูกบันทึกไว้ในเอกสาร A

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

การ `Compare` วิธีการเปรียบเทียบเอกสาร A กับเอกสาร B และบันทึกการเปลี่ยนแปลงในเอกสาร A คุณสามารถระบุชื่อผู้เขียนและวันที่เปรียบเทียบเพื่อใช้เป็นข้อมูลอ้างอิงได้

## บทสรุป

ในบทความนี้ เราได้สำรวจฟีเจอร์ Compare Granularity ของ Aspose.Words สำหรับ .NET ฟีเจอร์นี้ช่วยให้คุณเปรียบเทียบเอกสารในระดับอักขระและรายงานการเปลี่ยนแปลง คุณสามารถใช้ความรู้เหล่านี้เพื่อเปรียบเทียบเอกสารโดยละเอียดในโครงการของคุณได้

### ตัวอย่างโค้ดต้นฉบับสำหรับการเปรียบเทียบรายละเอียดโดยใช้ Aspose.Words สำหรับ .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## บทสรุป

ในบทช่วยสอนนี้ เราได้สำรวจคุณลักษณะการเปรียบเทียบระดับรายละเอียด (Comparison Granularity) ของ Aspose.Words สำหรับ .NET คุณลักษณะนี้ช่วยให้คุณระบุระดับรายละเอียดเมื่อเปรียบเทียบเอกสารได้ โดยการเลือกระดับรายละเอียดที่แตกต่างกัน คุณสามารถทำการเปรียบเทียบรายละเอียดในระดับอักขระ คำ หรือบล็อก ขึ้นอยู่กับข้อกำหนดเฉพาะของคุณ Aspose.Words สำหรับ .NET มอบความสามารถในการเปรียบเทียบเอกสารที่ยืดหยุ่นและทรงพลัง ทำให้สามารถระบุความแตกต่างในเอกสารที่มีระดับรายละเอียดที่แตกต่างกันได้อย่างง่ายดาย

### คำถามที่พบบ่อย

#### ถาม: จุดประสงค์ของการใช้ Comparison Granularity ใน Aspose.Words สำหรับ .NET คืออะไร

A: ระดับความละเอียดของการเปรียบเทียบใน Aspose.Words สำหรับ .NET ช่วยให้คุณระบุระดับรายละเอียดเมื่อเปรียบเทียบเอกสาร ด้วยคุณลักษณะนี้ คุณสามารถเปรียบเทียบเอกสารในระดับต่างๆ เช่น ระดับอักขระ ระดับคำ หรือแม้แต่ระดับบล็อก ระดับความละเอียดแต่ละระดับจะให้ระดับรายละเอียดที่แตกต่างกันในผลลัพธ์การเปรียบเทียบ

#### ถาม: ฉันจะใช้ Comparison Granularity ใน Aspose.Words สำหรับ .NET ได้อย่างไร

A: หากต้องการใช้ Comparison Granularity ใน Aspose.Words สำหรับ .NET ให้ทำตามขั้นตอนเหล่านี้:
1. ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณด้วยไลบรารี Aspose.Words
2. เพิ่มแอสเซมบลีที่จำเป็นให้กับโครงการของคุณโดยอ้างอิง Aspose.Words
3. สร้างเอกสารที่คุณต้องการเปรียบเทียบโดยใช้ `DocumentBuilder` ระดับ.
4. กำหนดค่าตัวเลือกการเปรียบเทียบโดยการสร้าง `CompareOptions` วัตถุและการตั้งค่า `Granularity` คุณสมบัติให้ถึงระดับที่ต้องการ (เช่น `Granularity.CharLevel` เพื่อการเปรียบเทียบระดับตัวละคร)
5. ใช้ `Compare` วิธีการในเอกสารหนึ่งโดยส่งเอกสารอื่นและ `CompareOptions` วัตถุเป็นพารามิเตอร์ วิธีนี้จะเปรียบเทียบเอกสารตามระดับความละเอียดที่ระบุและบันทึกการเปลี่ยนแปลงในเอกสารแรก

#### ถาม: ระดับความละเอียดของการเปรียบเทียบที่มีอยู่ใน Aspose.Words สำหรับ .NET มีอะไรบ้าง

A: Aspose.Words สำหรับ .NET มีระดับความละเอียดของการเปรียบเทียบสามระดับ:
- `Granularity.CharLevel`:เปรียบเทียบเอกสารในระดับอักขระ
- `Granularity.WordLevel`:เปรียบเทียบเอกสารในระดับคำ
- `Granularity.BlockLevel`:เปรียบเทียบเอกสารในระดับบล็อค

#### ถาม: ฉันจะตีความผลการเปรียบเทียบด้วยรายละเอียดระดับอักขระได้อย่างไร

A: ด้วยความละเอียดระดับอักขระ อักขระแต่ละตัวในเอกสารที่เปรียบเทียบจะได้รับการวิเคราะห์ความแตกต่าง ผลการเปรียบเทียบจะแสดงการเปลี่ยนแปลงในระดับอักขระแต่ละตัว รวมถึงการเพิ่ม การลบ และการแก้ไข


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}