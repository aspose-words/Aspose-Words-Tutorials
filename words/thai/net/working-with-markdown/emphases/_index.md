---
title: การเน้นย้ำ
linktitle: การเน้นย้ำ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีสร้างข้อความเน้นข้อความใน Markdown โดยใช้ Aspose.Words สำหรับ .NET คู่มือนี้ครอบคลุมรูปแบบตัวหนา ตัวเอียง และแบบผสมผสาน พร้อมคำแนะนำทีละขั้นตอน
weight: 10
url: /th/net/working-with-markdown/emphases/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การเน้นย้ำ

## การแนะนำ

Markdown เป็นภาษามาร์กอัปน้ำหนักเบาที่คุณสามารถใช้เพื่อเพิ่มองค์ประกอบการจัดรูปแบบให้กับเอกสารข้อความธรรมดา ในคู่มือนี้ เราจะเจาะลึกรายละเอียดเกี่ยวกับการใช้ Aspose.Words สำหรับ .NET เพื่อสร้างไฟล์ Markdown ที่มีข้อความเน้นย้ำ เช่น รูปแบบตัวหนาและตัวเอียง ไม่ว่าคุณจะกำลังร่างเอกสาร โพสต์บล็อก หรือข้อความใดๆ ที่ต้องการความโดดเด่น บทช่วยสอนนี้จะแนะนำคุณตลอดทุกขั้นตอนของกระบวนการ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้นเขียนโค้ด เรามาตรวจสอบให้แน่ใจก่อนว่าเรามีทุกสิ่งที่จำเป็นสำหรับการเริ่มต้น:

1.  ไลบรารี Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Aspose.Words สำหรับ .NET เวอร์ชันล่าสุดแล้ว คุณสามารถ[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนา .NET ที่เหมาะสม เช่น Visual Studio
3. ความรู้พื้นฐานเกี่ยวกับ C#: การเข้าใจพื้นฐานของการเขียนโปรแกรม C# จะเป็นประโยชน์
4. หลักพื้นฐานของ Markdown: ความคุ้นเคยกับรูปแบบ Markdown จะช่วยให้คุณเข้าใจบริบทได้ดีขึ้น

## นำเข้าเนมสเปซ

ในการใช้งาน Aspose.Words สำหรับ .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็น เพิ่มคำสั่ง using ต่อไปนี้ที่ด้านบนของไฟล์โค้ดของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: การตั้งค่าเอกสารและ DocumentBuilder

สิ่งแรกที่ต้องทำคือเราต้องสร้างเอกสาร Word ใหม่และเริ่มต้นใช้งาน`DocumentBuilder` เพื่อเริ่มต้นการเพิ่มเนื้อหา

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 การ`dataDir` ตัวแปรคือตัวแทนสำหรับไดเร็กทอรีที่คุณจะบันทึกไฟล์ Markdown ของคุณ อย่าลืมแทนที่ "YOUR DOCUMENT DIRECTORY" ด้วยเส้นทางจริง

## ขั้นตอนที่ 2: การเขียนข้อความปกติ

ตอนนี้เรามาเพิ่มข้อความธรรมดาลงในเอกสารกัน ซึ่งจะเป็นพื้นฐานสำหรับการแสดงการเน้นข้อความ

```csharp
builder.Writeln("Markdown treats asterisks (*) and underscores (_) as indicators of emphases.");
builder.Write("You can write ");
```

 ที่นี่,`Writeln` เพิ่มบรรทัดใหม่หลังข้อความในขณะที่`Write` ยังคงดำเนินต่อไปในแนวเดียวกัน

## ขั้นตอนที่ 3: การเพิ่มข้อความตัวหนา

 หากต้องการเพิ่มข้อความตัวหนาใน Markdown ให้ใส่ข้อความที่ต้องการด้วยเครื่องหมายดอกจันสองอัน (``) ใน Aspose.Words สำหรับ .NET คุณสามารถทำได้โดยตั้งค่า`Bold` ทรัพย์สินของ`Font` คัดค้าน`true`.

```csharp
builder.Font.Bold = true;
builder.Write("bold");
builder.Font.Bold = false;
builder.Write(" or ");
```

โค้ดสั้นๆ นี้จะตั้งค่าข้อความ "ตัวหนา" ให้เป็นตัวหนา และเปลี่ยนกลับเป็นข้อความปกติสำหรับคำว่า "หรือ"

## ขั้นตอนที่ 4: การเพิ่มข้อความตัวเอียง

ข้อความตัวเอียงใน Markdown จะถูกใส่เครื่องหมายดอกจันเพียงตัวเดียว (`*` ). ในทำนองเดียวกัน ให้ตั้งค่า`Italic` ทรัพย์สินของ`Font` คัดค้าน`true`.

```csharp
builder.Font.Italic = true;
builder.Write("italic");
builder.Font.Italic = false;
builder.Writeln(" text.");
```

การดำเนินการนี้จะทำให้แสดง "ตัวเอียง" ในรูปแบบตัวเอียงตามด้วยข้อความปกติ

## ขั้นตอนที่ 5: การรวมข้อความตัวหนาและตัวเอียง

คุณสามารถรวมรูปแบบตัวหนาและตัวเอียงได้โดยการห่อข้อความด้วยเครื่องหมายดอกจันสามตัว (`*` ). ตั้งค่าทั้งสอง`Bold` และ`Italic` คุณสมบัติให้`true`.

```csharp
builder.Write("You can also write ");
builder.Font.Bold = true;
builder.Font.Italic = true;
builder.Write("BoldItalic");
builder.Font.Bold = false;
builder.Font.Italic = false;
builder.Write(" text.");
```

ตัวอย่างนี้สาธิตวิธีการใช้รูปแบบตัวหนาและตัวเอียงกับ "ตัวหนาตัวเอียง"

## ขั้นตอนที่ 6: บันทึกเอกสารเป็นมาร์กดาวน์

หลังจากเพิ่มข้อความที่เน้นทั้งหมดแล้ว ก็ถึงเวลาบันทึกเอกสารเป็นไฟล์ Markdown

```csharp
builder.Document.Save(dataDir + "WorkingWithMarkdown.Emphases.md");
```

บรรทัดนี้จะบันทึกเอกสารในไดเร็กทอรีที่ระบุโดยมีชื่อไฟล์ว่า "WorkingWithMarkdown.Emphases.md"

## บทสรุป

และแล้วคุณก็ทำได้! ตอนนี้คุณได้เรียนรู้วิธีการสร้างข้อความเน้นข้อความใน Markdown โดยใช้ Aspose.Words สำหรับ .NET แล้ว ไลบรารีอันทรงพลังนี้ทำให้การจัดการเอกสาร Word และส่งออกเป็นรูปแบบต่างๆ รวมถึง Markdown เป็นเรื่องง่ายด้วยโปรแกรม เพียงทำตามขั้นตอนที่ระบุไว้ในคู่มือนี้ คุณก็ปรับปรุงเอกสารของคุณด้วยข้อความตัวหนาและตัวเอียง ทำให้เอกสารน่าสนใจและอ่านง่ายขึ้น

## คำถามที่พบบ่อย

### ฉันสามารถใช้รูปแบบข้อความอื่นใน Markdown กับ Aspose.Words สำหรับ .NET ได้หรือไม่
ใช่ คุณสามารถใช้รูปแบบอื่น ๆ เช่น ส่วนหัว รายการ และบล็อกโค้ดได้ Aspose.Words สำหรับ .NET รองรับตัวเลือกการจัดรูปแบบ Markdown มากมาย

### ฉันจะติดตั้ง Aspose.Words สำหรับ .NET ได้อย่างไร?
 คุณสามารถดาวน์โหลดห้องสมุดได้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/)และปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้

### มี Aspose.Words สำหรับ .NET ให้ทดลองใช้งานฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดได้[ทดลองใช้งานฟรี](https://releases.aspose.com/) เพื่อทดสอบคุณสมบัติของ Aspose.Words สำหรับ .NET

### ฉันจะได้รับการสนับสนุนหากประสบปัญหาหรือไม่?
 แน่นอนครับ! สามารถเข้าไปเยี่ยมชมได้ที่[ฟอรั่มสนับสนุน Aspose.Words](https://forum.aspose.com/c/words/8) เพื่อรับความช่วยเหลือจากชุมชนและทีมงาน Aspose

### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร
 คุณสามารถรับได้[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อประเมินศักยภาพของห้องสมุดให้ครบถ้วน
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
