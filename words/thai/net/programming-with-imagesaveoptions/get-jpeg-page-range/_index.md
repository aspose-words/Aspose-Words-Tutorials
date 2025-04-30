---
"description": "แปลงหน้าเฉพาะของเอกสาร Word เป็น JPEG ด้วยการตั้งค่าแบบกำหนดเองโดยใช้ Aspose.Words สำหรับ .NET เรียนรู้วิธีการปรับความสว่าง ความคมชัด และความละเอียดทีละขั้นตอน"
"linktitle": "รับช่วงหน้า Jpeg"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "รับช่วงหน้า Jpeg"
"url": "/th/net/programming-with-imagesaveoptions/get-jpeg-page-range/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# รับช่วงหน้า Jpeg

## การแนะนำ

การแปลงเอกสาร Word เป็นรูปภาพนั้นมีประโยชน์อย่างยิ่ง ไม่ว่าคุณจะกำลังสร้างภาพขนาดย่อ ดูตัวอย่างเอกสารออนไลน์ หรือแชร์เนื้อหาในรูปแบบที่เข้าถึงได้ง่ายกว่า ด้วย Aspose.Words สำหรับ .NET คุณสามารถแปลงหน้าเฉพาะของเอกสาร Word เป็นรูปแบบ JPEG ได้อย่างง่ายดาย พร้อมปรับแต่งการตั้งค่าต่างๆ เช่น ความสว่าง ความคมชัด และความละเอียด มาดูกันว่าจะทำได้อย่างไรทีละขั้นตอน!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้น คุณจะต้องมีบางสิ่งบางอย่าง:

- Aspose.Words สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Aspose.Words สำหรับ .NET แล้ว คุณสามารถ [ดาวน์โหลดได้ที่นี่](https://releases-aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนา AC# เช่น Visual Studio
- เอกสารตัวอย่าง: เอกสาร Word สำหรับใช้งาน คุณสามารถใช้ไฟล์ .docx ใดก็ได้สำหรับบทช่วยสอนนี้
- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C#

เมื่อคุณพร้อมแล้ว มาเริ่มกันเลย!

## นำเข้าเนมสเปซ

หากต้องการใช้ Aspose.Words สำหรับ .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็นไว้ที่จุดเริ่มต้นของโค้ด ซึ่งจะช่วยให้คุณสามารถเข้าถึงคลาสและวิธีการทั้งหมดที่จำเป็นสำหรับการจัดการเอกสารได้

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: โหลดเอกสารของคุณ

ขั้นแรก เราต้องโหลดเอกสาร Word ที่เราต้องการแปลง สมมติว่าเอกสารของเรามีชื่อว่า `Rendering.docx` และอยู่ในไดเร็กทอรีที่ระบุโดยตัวแทน `YOUR DOCUMENT DIRECTORY`-

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

โค้ดนี้จะเริ่มต้นเส้นทางไปยังเอกสารของคุณและโหลดเข้าใน Aspose.Words `Document` วัตถุ.

## ขั้นตอนที่ 2: ตั้งค่า ImageSaveOptions

ต่อไปเราจะตั้งค่า `ImageSaveOptions` เพื่อระบุว่าเราต้องการสร้างไฟล์ JPEG อย่างไร ซึ่งรวมถึงการตั้งค่าช่วงหน้า ความสว่างของภาพ ความคมชัด และความละเอียด

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // แปลงเฉพาะหน้าแรกเท่านั้น
options.ImageBrightness = 0.3f;   // ตั้งค่าความสว่าง
options.ImageContrast = 0.7f;     // ตั้งค่าคอนทราสต์
options.HorizontalResolution = 72f; // ตั้งค่าความละเอียด
```

## ขั้นตอนที่ 3: บันทึกเอกสารเป็น JPEG

สุดท้าย เราบันทึกเอกสารเป็นไฟล์ JPEG โดยใช้การตั้งค่าที่เราได้กำหนดไว้

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

รหัสนี้จะบันทึกหน้าแรกของ `Rendering.docx` เป็นภาพ JPEG ที่มีการตั้งค่าความสว่าง ความคมชัด และความละเอียดตามที่ระบุ

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้แปลงหน้าเฉพาะของเอกสาร Word เป็นภาพ JPEG สำเร็จแล้วด้วยการตั้งค่าที่กำหนดเองโดยใช้ Aspose.Words สำหรับ .NET กระบวนการนี้สามารถปรับแต่งให้เหมาะกับความต้องการต่างๆ ไม่ว่าคุณจะกำลังเตรียมภาพสำหรับเว็บไซต์ สร้างตัวอย่างเอกสาร หรืออื่นๆ

## คำถามที่พบบ่อย

### ฉันสามารถแปลงหลายหน้าในครั้งเดียวได้ไหม?
ใช่ คุณสามารถระบุช่วงหน้าได้โดยใช้ `PageSet` ทรัพย์สินใน `ImageSaveOptions`-

### ฉันจะปรับคุณภาพของภาพได้อย่างไร?
คุณสามารถปรับคุณภาพของ JPEG ได้โดยใช้ `JpegQuality` ทรัพย์สินใน `ImageSaveOptions`-

### ฉันสามารถบันทึกในรูปแบบรูปภาพอื่นได้หรือไม่
ใช่ Aspose.Words รองรับรูปแบบภาพต่างๆ เช่น PNG, BMP และ TIFF เปลี่ยน `SaveFormat` ใน `ImageSaveOptions` ตามนั้นครับ

### มีวิธีดูตัวอย่างภาพก่อนบันทึกหรือไม่
คุณจะต้องดำเนินการตามกลไกการแสดงตัวอย่างแยกต่างหาก เนื่องจาก Aspose.Words ไม่มีคุณลักษณะการแสดงตัวอย่างในตัว

### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Words ได้อย่างไร
คุณสามารถร้องขอได้ [ใบอนุญาตชั่วคราวที่นี่](https://purchase-aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}