---
title: ตั้งค่าโฟลเดอร์แบบอักษร True Type
linktitle: ตั้งค่าโฟลเดอร์แบบอักษร True Type
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีตั้งค่าโฟลเดอร์แบบอักษร True Type ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนโดยละเอียดของเราเพื่อให้แน่ใจว่าการจัดการแบบอักษรมีความสอดคล้องกัน
weight: 10
url: /th/net/working-with-fonts/set-true-type-fonts-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าโฟลเดอร์แบบอักษร True Type

## การแนะนำ

เรากำลังดำดิ่งสู่โลกอันน่าตื่นตาตื่นใจของการจัดการแบบอักษรในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET หากคุณเคยประสบปัญหาในการฝังแบบอักษรที่ถูกต้องหรือทำให้แน่ใจว่าเอกสารของคุณดูสมบูรณ์แบบในทุกอุปกรณ์ คุณมาถูกที่แล้ว เราจะแนะนำขั้นตอนการตั้งค่าโฟลเดอร์แบบอักษร True Type เพื่อปรับปรุงการจัดการแบบอักษรในเอกสารของคุณ เพื่อให้แน่ใจว่าเอกสารของคุณมีความสอดคล้องและชัดเจน

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงรายละเอียด มาดูข้อกำหนดเบื้องต้นบางประการเพื่อให้แน่ใจว่าคุณพร้อมสำหรับความสำเร็จกันก่อน:

1.  Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งเวอร์ชันล่าสุดแล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนา .NET ที่ใช้งานได้ เช่น Visual Studio
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะเป็นประโยชน์
4. เอกสารตัวอย่าง: เตรียมเอกสาร Word ที่คุณต้องการใช้งานไว้

## นำเข้าเนมสเปซ

สิ่งแรกที่ต้องทำคือนำเข้าเนมสเปซที่จำเป็น ซึ่งเปรียบเสมือนทีมงานเบื้องหลังที่คอยดูแลให้ทุกอย่างดำเนินไปอย่างราบรื่น

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

## ขั้นตอนที่ 1: โหลดเอกสารของคุณ

 เริ่มต้นด้วยการโหลดเอกสารของคุณ เราจะใช้`Document` คลาสจาก Aspose.Words เพื่อโหลดเอกสาร Word ที่มีอยู่

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## ขั้นตอนที่ 2: เริ่มต้นการตั้งค่า FontSettings

 ต่อไปเราจะสร้างอินสแตนซ์ของ`FontSettings`คลาส คลาสนี้ช่วยให้เราปรับแต่งวิธีการจัดการแบบอักษรในเอกสารของเราได้

```csharp
FontSettings fontSettings = new FontSettings();
```

## ขั้นตอนที่ 3: ตั้งค่าโฟลเดอร์แบบอักษร

ตอนนี้มาถึงส่วนที่น่าตื่นเต้นแล้ว เราจะระบุโฟลเดอร์ที่เก็บแบบอักษร True Type ของเรา ขั้นตอนนี้จะช่วยให้มั่นใจว่า Aspose.Words จะใช้แบบอักษรจากโฟลเดอร์นี้เมื่อทำการเรนเดอร์หรือฝังแบบอักษร

```csharp
// โปรดทราบว่าการตั้งค่านี้จะแทนที่แหล่งแบบอักษรเริ่มต้นที่ถูกค้นหาตามค่าเริ่มต้น
// ขณะนี้จะค้นหาแบบอักษรเฉพาะในโฟลเดอร์เหล่านี้เมื่อทำการเรนเดอร์หรือฝังแบบอักษร
fontSettings.SetFontsFolder(@"C:\MyFonts\", false);
```

## ขั้นตอนที่ 4: นำการตั้งค่าแบบอักษรไปใช้กับเอกสาร

เมื่อกำหนดค่าแบบอักษรเรียบร้อยแล้ว เราจะนำการตั้งค่าเหล่านี้ไปใช้กับเอกสาร ขั้นตอนนี้มีความสำคัญเพื่อให้แน่ใจว่าเอกสารของเราใช้แบบอักษรที่ระบุ

```csharp
// ตั้งค่าแบบอักษร
doc.FontSettings = fontSettings;
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายนี้ เราจะบันทึกเอกสาร คุณสามารถบันทึกเอกสารได้หลายรูปแบบ แต่สำหรับบทช่วยสอนนี้ เราจะบันทึกเป็น PDF

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetTrueTypeFontsFolder.pdf");
```

## บทสรุป

และแล้วคุณก็ทำได้สำเร็จ! คุณได้ตั้งค่าโฟลเดอร์แบบอักษร True Type สำหรับเอกสาร Word ของคุณสำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET วิธีนี้จะช่วยให้เอกสารของคุณดูสอดคล้องและเป็นมืออาชีพในทุกแพลตฟอร์ม การจัดการแบบอักษรเป็นส่วนสำคัญของการสร้างเอกสาร และด้วย Aspose.Words จะทำให้ทุกอย่างเป็นเรื่องง่ายอย่างเหลือเชื่อ

## คำถามที่พบบ่อย

### ฉันสามารถใช้โฟลเดอร์ฟอนต์หลายโฟลเดอร์ได้หรือไม่
 ใช่ คุณสามารถใช้โฟลเดอร์แบบอักษรหลายโฟลเดอร์ได้โดยการรวม`FontSettings.GetFontSources` และ`FontSettings.SetFontSources`.

### จะเกิดอะไรขึ้นถ้าโฟลเดอร์ฟอนต์ที่ระบุไม่มีอยู่?
ถ้าไม่มีโฟลเดอร์ฟอนต์ที่ระบุ Aspose.Words จะไม่สามารถระบุตำแหน่งฟอนต์ได้ และจะใช้ฟอนต์ระบบเริ่มต้นแทน

### ฉันสามารถกลับไปใช้การตั้งค่าฟอนต์เริ่มต้นได้หรือไม่
 ใช่ คุณสามารถกลับไปใช้การตั้งค่าแบบอักษรเริ่มต้นได้โดยการรีเซ็ต`FontSettings` ตัวอย่าง.

### สามารถฝังฟอนต์ลงในเอกสารได้หรือไม่
ใช่ Aspose.Words อนุญาตให้คุณฝังแบบอักษรในเอกสารเพื่อให้แน่ใจว่ามีความสอดคล้องกันในอุปกรณ์ต่างๆ

### ฉันสามารถบันทึกเอกสารของฉันในรูปแบบใดได้บ้าง?
Aspose.Words รองรับรูปแบบต่างๆ เช่น PDF, DOCX, HTML และอื่นๆ อีกมากมาย
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
