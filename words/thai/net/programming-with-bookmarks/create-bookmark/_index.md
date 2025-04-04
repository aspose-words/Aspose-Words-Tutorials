---
title: สร้างบุ๊กมาร์กในเอกสาร Word
linktitle: สร้างบุ๊กมาร์กในเอกสาร Word
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีสร้างบุ๊กมาร์กในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนโดยละเอียดนี้ เหมาะอย่างยิ่งสำหรับการนำทางและการจัดระเบียบเอกสาร
weight: 10
url: /th/net/programming-with-bookmarks/create-bookmark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างบุ๊กมาร์กในเอกสาร Word

## การแนะนำ

การสร้างบุ๊กมาร์กในเอกสาร Word ถือเป็นเครื่องมือสำคัญ โดยเฉพาะอย่างยิ่งเมื่อคุณต้องการนำทางผ่านเอกสารขนาดใหญ่ได้อย่างง่ายดาย วันนี้ เราจะแนะนำขั้นตอนการสร้างบุ๊กมาร์กโดยใช้ Aspose.Words สำหรับ .NET บทช่วยสอนนี้จะอธิบายให้คุณทราบทีละขั้นตอน เพื่อให้คุณเข้าใจขั้นตอนต่างๆ ของแต่ละขั้นตอน ดังนั้น มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม คุณต้องมีสิ่งต่อไปนี้:

1.  Aspose.Words สำหรับไลบรารี .NET: ดาวน์โหลดและติดตั้งจาก[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET อื่น ๆ
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจเกี่ยวกับแนวคิดการเขียนโปรแกรม C# ขั้นพื้นฐาน

## นำเข้าเนมสเปซ

ในการทำงานกับ Aspose.Words สำหรับ .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็น:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: ตั้งค่าเอกสารและ DocumentBuilder

การเริ่มต้นเอกสาร

ขั้นแรกเราต้องสร้างเอกสารใหม่และเริ่มต้นใช้งาน`DocumentBuilder`นี่คือจุดเริ่มต้นสำหรับการเพิ่มเนื้อหาและบุ๊กมาร์กลงในเอกสารของคุณ

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 คำอธิบาย :`Document` วัตถุคือผืนผ้าใบของคุณ`DocumentBuilder` เป็นเหมือนปากกาของคุณ ซึ่งช่วยให้คุณเขียนเนื้อหาและสร้างบุ๊กมาร์กในเอกสารได้

## ขั้นตอนที่ 2: สร้างบุ๊กมาร์กหลัก

เริ่มต้นและสิ้นสุดบุ๊กมาร์กหลัก

หากต้องการสร้างบุ๊กมาร์ก คุณต้องระบุจุดเริ่มต้นและจุดสิ้นสุด ที่นี่ เราจะสร้างบุ๊กมาร์กชื่อ "บุ๊กมาร์กของฉัน"

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

 คำอธิบาย :`StartBookmark` วิธีการทำเครื่องหมายจุดเริ่มต้นของบุ๊กมาร์กและ`Writeln` เพิ่มข้อความภายในบุ๊กมาร์ก

## ขั้นตอนที่ 3: สร้างบุ๊กมาร์กแบบซ้อน

เพิ่มบุ๊กมาร์กแบบซ้อนภายในบุ๊กมาร์กหลัก

คุณสามารถซ้อนบุ๊กมาร์กไว้ในบุ๊กมาร์กอื่นได้ ที่นี่ เราเพิ่ม "บุ๊กมาร์กซ้อน" ไว้ใน "บุ๊กมาร์กของฉัน"

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

 คำอธิบาย: การคั่นหน้าแบบซ้อนช่วยให้จัดระเบียบเนื้อหาได้เป็นโครงสร้างและมีลำดับชั้นมากขึ้น`EndBookmark` วิธีการปิดบุ๊กมาร์กปัจจุบัน

## ขั้นตอนที่ 4: เพิ่มข้อความภายนอกบุ๊กมาร์กที่ซ้อนกัน

ดำเนินการเพิ่มเนื้อหาต่อไป

หลังจากที่บุ๊กมาร์กแบบซ้อนกันแล้ว เราจะสามารถเพิ่มเนื้อหาเพิ่มเติมภายในบุ๊กมาร์กหลักได้

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

คำอธิบาย: การดำเนินการนี้จะช่วยให้แน่ใจว่าบุ๊กมาร์กหลักจะครอบคลุมทั้งบุ๊กมาร์กแบบซ้อนและข้อความเพิ่มเติม

## ขั้นตอนที่ 5: กำหนดค่าตัวเลือกการบันทึก PDF

ตั้งค่าตัวเลือกการบันทึก PDF สำหรับบุ๊กมาร์ก

เมื่อบันทึกเอกสารเป็น PDF เราสามารถตั้งค่าตัวเลือกเพื่อรวมบุ๊กมาร์กได้

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

 คำอธิบาย :`PdfSaveOptions` คลาสช่วยให้คุณระบุได้ว่าควรบันทึกเอกสารเป็น PDF อย่างไร`BookmarksOutlineLevels` คุณสมบัติจะกำหนดลำดับชั้นของบุ๊กมาร์กใน PDF

## ขั้นตอนที่ 6: บันทึกเอกสาร

บันทึกเอกสารเป็น PDF

สุดท้ายให้บันทึกเอกสารด้วยตัวเลือกที่ระบุ

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

 คำอธิบาย :`Save` วิธีการนี้จะบันทึกเอกสารในรูปแบบและตำแหน่งที่ระบุ ตอนนี้ PDF จะรวมบุ๊กมาร์กที่เราสร้างขึ้น

## บทสรุป

การสร้างบุ๊กมาร์กในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET นั้นทำได้ง่ายและมีประโยชน์อย่างมากสำหรับการนำทางและการจัดระเบียบเอกสาร ไม่ว่าคุณจะกำลังสร้างรายงาน สร้างอีบุ๊ก หรือจัดการเอกสารขนาดใหญ่ บุ๊กมาร์กจะทำให้ชีวิตง่ายขึ้น ทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ แล้วคุณจะมี PDF ที่บุ๊กมาร์กพร้อมใช้งานในเวลาไม่นาน

## คำถามที่พบบ่อย

### ฉันสามารถสร้างบุ๊กมาร์กหลายรายการในระดับที่แตกต่างกันได้หรือไม่

แน่นอน! คุณสามารถสร้างบุ๊กมาร์กได้มากเท่าที่ต้องการและกำหนดระดับลำดับชั้นเมื่อบันทึกเอกสารเป็น PDF

### ฉันจะอัปเดตข้อความของบุ๊กมาร์กได้อย่างไร?

 คุณสามารถนำทางไปยังบุ๊กมาร์กได้โดยใช้`DocumentBuilder.MoveToBookmark` แล้วอัพเดทข้อความ

### สามารถลบบุ๊กมาร์กได้หรือไม่?

 ใช่ คุณสามารถลบบุ๊กมาร์กได้โดยใช้`Bookmarks.Remove` วิธีการโดยการระบุชื่อบุ๊กมาร์ก

### ฉันสามารถสร้างบุ๊กมาร์กในรูปแบบอื่นนอกเหนือจาก PDF ได้หรือไม่

ใช่ Aspose.Words รองรับบุ๊กมาร์กในรูปแบบต่างๆ รวมถึง DOCX, HTML และ EPUB

### ฉันจะมั่นใจได้อย่างไรว่าบุ๊กมาร์กปรากฏอย่างถูกต้องใน PDF?

 ให้แน่ใจว่าได้กำหนด`BookmarksOutlineLevels` อย่างถูกต้องใน`PdfSaveOptions`วิธีนี้จะช่วยให้แน่ใจว่าบุ๊กมาร์กจะรวมอยู่ในโครงร่างของ PDF
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
