---
title: ตั้งค่าโฟลเดอร์รูปภาพ
linktitle: ตั้งค่าโฟลเดอร์รูปภาพ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: แปลงเอกสาร Word เป็น Markdown พร้อมจัดวางตารางให้เหมาะสมโดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำโดยละเอียดของเราเพื่อผลลัพธ์ที่สมบูรณ์แบบ
weight: 10
url: /th/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าโฟลเดอร์รูปภาพ

## การแนะนำ

คุณเคยต้องการส่งออกเอกสาร Word ของคุณเป็นรูปแบบ Markdown พร้อมมั่นใจว่าตารางและเนื้อหาจะจัดเรียงอย่างสมบูรณ์แบบหรือไม่? Aspose.Words สำหรับ .NET คือโซลูชันที่คุณต้องการสำหรับงานนี้ ในบทความนี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนการตั้งค่า Aspose.Words การเตรียมเอกสาร และการส่งออกเป็น Markdown พร้อมการจัดวางเนื้อหาตารางอย่างเหมาะสม เราจะแบ่งขั้นตอนแต่ละขั้นตอนเพื่อให้ทำตามและเข้าใจได้ง่าย ดังนั้น มาเริ่มต้นและแปลงเอกสาร Word ของคุณให้เป็นไฟล์ Markdown ที่จัดเรียงอย่างสวยงามกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.Words สำหรับ .NET: คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
-  ใบอนุญาตที่ถูกต้อง: รับสิทธิ์ทดลองใช้ฟรี[ที่นี่](https://releases.aspose.com/) หรือใบอนุญาตชั่วคราว[ที่นี่](https://purchase.aspose.com/temporary-license/).
- Visual Studio: หรือ IDE อื่นๆ ที่รองรับการพัฒนา .NET
- ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจเกี่ยวกับภาษาการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ เนมสเปซเหล่านี้จะช่วยให้คุณสามารถเข้าถึงฟังก์ชันการทำงานของ Aspose.Words ได้

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

ขั้นแรก ให้ตั้งค่าโปรเจ็กต์ .NET ใน IDE ของคุณ สร้างแอปพลิเคชันคอนโซลใหม่และเพิ่มการอ้างอิงไปยัง Aspose.Words สำหรับ .NET

### 1.1 สร้างโครงการใหม่

เปิด Visual Studio และสร้างโปรเจ็กต์แอปพลิเคชันคอนโซลใหม่ ตั้งชื่อว่า "MarkdownExporter" หรือชื่ออื่นที่คล้ายกัน

### 1.2 เพิ่มการอ้างอิง Aspose.Words

 หากต้องการเพิ่ม Aspose.Words ลงในโปรเจ็กต์ของคุณ คุณสามารถดาวน์โหลด DLL จาก[เว็บไซต์อาโพส](https://releases.aspose.com/words/net/) และเพิ่มด้วยตนเองหรือใช้ตัวจัดการแพ็กเกจ NuGet:

```bash
Install-Package Aspose.Words
```

## ขั้นตอนที่ 2: เขียนโค้ดเพื่อส่งออกเป็นมาร์กดาวน์

ต่อไปเราจะเขียนโค้ดเพื่ออ่านเอกสาร Word และบันทึกเป็นไฟล์ Markdown พร้อมจัดตำแหน่งตารางให้เหมาะสม

### 2.1 กำหนดเส้นทางไปยังเอกสารของคุณ

กำหนดเส้นทางไปยังเอกสาร Word ของคุณและโฟลเดอร์ที่คุณต้องการบันทึกรูปภาพ

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 โหลดเอกสาร

โหลดเอกสาร Word ของคุณโดยใช้ Aspose.Words

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 กำหนดค่าตัวเลือกการบันทึกมาร์กดาวน์

 กำหนดค่า`MarkdownSaveOptions` เพื่อระบุว่าควรเก็บรูปภาพไว้ที่ไหน

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 บันทึกเอกสารเป็นมาร์กดาวน์

 ใช้`MemoryStream` เพื่อบันทึกเอกสารในรูปแบบ Markdown

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## บทสรุป

การส่งออกเอกสาร Word เป็น Markdown พร้อมการจัดแนวเนื้อหาตารางโดยใช้ Aspose.Words สำหรับ .NET เป็นเรื่องง่ายเมื่อคุณทำตามขั้นตอนเหล่านี้ ด้วยโค้ดเพียงไม่กี่บรรทัด คุณสามารถทำให้กระบวนการแปลงเป็นแบบอัตโนมัติและมั่นใจได้ว่าเนื้อหาของคุณได้รับการจัดรูปแบบอย่างถูกต้อง ตอนนี้คุณสามารถแชร์เอกสารของคุณในรูปแบบ Markdown ได้อย่างง่ายดาย โดยมั่นใจได้ว่าเอกสารจะดูดีและรักษาโครงสร้างไว้ได้

## คำถามที่พบบ่อย

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET ร่วมกับภาษาการเขียนโปรแกรมอื่น ๆ ได้หรือไม่

ใช่ Aspose.Words สำหรับ .NET สามารถใช้ร่วมกับภาษาใดๆ ที่เข้ากันได้กับ .NET เช่น VB.NET, F# และอื่นๆ อีกมากมาย

### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Words ได้อย่างไร

คุณสามารถขอใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.aspose.com/temporary-license/).

### ฉันสามารถแปลงเอกสารประเภทใดเป็น Markdown ได้บ้าง

คุณสามารถแปลงเอกสาร Word ต่างๆ รวมถึง .doc, .docx, .rtf และอื่นๆ อีกมากมาย

### มีข้อจำกัดใด ๆ ในเวอร์ชันทดลองใช้ของ Aspose.Words หรือไม่

เวอร์ชันทดลองใช้มีข้อจำกัดบางประการ เช่น ลายน้ำในไฟล์เอาต์พุต คุณสามารถทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันสามารถหาตัวอย่างและเอกสารประกอบเพิ่มเติมสำหรับ Aspose.Words ได้จากที่ไหน

 คุณสามารถค้นหาเอกสารรายละเอียดและตัวอย่างได้ที่[เว็บไซต์อาโพส](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
