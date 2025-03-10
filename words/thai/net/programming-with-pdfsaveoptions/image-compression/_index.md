---
title: การบีบอัดภาพในเอกสาร PDF
linktitle: การบีบอัดภาพในเอกสาร PDF
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการบีบอัดรูปภาพในเอกสาร PDF โดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคู่มือนี้เพื่อปรับขนาดและคุณภาพไฟล์ให้เหมาะสมที่สุด
weight: 10
url: /th/net/programming-with-pdfsaveoptions/image-compression/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การบีบอัดภาพในเอกสาร PDF

## การแนะนำ

ในยุคดิจิทัลทุกวันนี้ การจัดการขนาดเอกสารถือเป็นสิ่งสำคัญทั้งต่อประสิทธิภาพการทำงานและประสิทธิภาพการจัดเก็บ ไม่ว่าคุณจะจัดการกับรายงานขนาดใหญ่หรือการนำเสนอที่ซับซ้อน การลดขนาดไฟล์โดยไม่กระทบต่อคุณภาพถือเป็นสิ่งสำคัญ การบีบอัดรูปภาพในเอกสาร PDF เป็นเทคนิคสำคัญในการบรรลุเป้าหมายนี้ หากคุณกำลังใช้ Aspose.Words สำหรับ .NET คุณโชคดีแล้ว! บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับขั้นตอนการบีบอัดรูปภาพในเอกสาร PDF โดยใช้ Aspose.Words สำหรับ .NET เราจะสำรวจตัวเลือกการบีบอัดต่างๆ และวิธีใช้ให้มีประสิทธิภาพเพื่อให้แน่ใจว่า PDF ของคุณได้รับการปรับให้เหมาะสมทั้งในด้านคุณภาพและขนาด

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มบทช่วยสอนนี้ ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

1. Aspose.Words สำหรับ .NET: คุณต้องติดตั้ง Aspose.Words สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์อาโพส](https://releases.aspose.com/words/net/).

2. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะช่วยให้คุณเข้าใจตัวอย่างโค้ดที่ให้ไว้ในบทช่วยสอนนี้

3. สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนา .NET เช่น Visual Studio

4. เอกสารตัวอย่าง: เตรียมเอกสาร Word ตัวอย่าง (เช่น "Rendering.docx") ไว้เพื่อทดสอบการบีบอัดรูปภาพ

5. ใบอนุญาต Aspose: หากคุณใช้ Aspose.Words เวอร์ชันที่มีใบอนุญาตสำหรับ .NET โปรดตรวจสอบให้แน่ใจว่าคุณได้กำหนดค่าใบอนุญาตอย่างถูกต้องแล้ว หากคุณต้องการใบอนุญาตชั่วคราว คุณสามารถขอรับได้จาก[หน้าใบอนุญาตชั่วคราวของ Aspose](https://purchase.aspose.com/temporary-license/).

## นำเข้าเนมสเปซ

หากต้องการเริ่มต้นการบีบอัดรูปภาพในเอกสาร PDF โดยใช้ Aspose.Words สำหรับ .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็น โดยดำเนินการได้ดังนี้:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

เนมสเปซเหล่านี้ช่วยให้สามารถเข้าถึงฟังก์ชันการทำงานหลักที่จำเป็นในการจัดการเอกสาร Word และบันทึกเป็น PDF พร้อมตัวเลือกต่างๆ

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสารของคุณ

ก่อนที่คุณจะเริ่มเขียนโค้ด ให้กำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณเสียก่อน ซึ่งจะช่วยให้คุณค้นหาและบันทึกไฟล์ได้อย่างง่ายดาย

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` พร้อมกับเส้นทางที่คุณเก็บเอกสารตัวอย่างของคุณ

## ขั้นตอนที่ 2: โหลดเอกสาร Word

 ขั้นตอนต่อไป โหลดเอกสาร Word ของคุณลงใน`Aspose.Words.Document` วัตถุ ซึ่งจะช่วยให้คุณสามารถทำงานกับเอกสารผ่านโปรแกรมได้

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 ที่นี่,`"Rendering.docx"` คือชื่อเอกสาร Word ตัวอย่างของคุณ ตรวจสอบให้แน่ใจว่าไฟล์นี้อยู่ในไดเร็กทอรีที่ระบุ

## ขั้นตอนที่ 3: กำหนดค่าการบีบอัดภาพพื้นฐาน

 สร้าง`PdfSaveOptions`วัตถุเพื่อกำหนดค่าตัวเลือกการบันทึก PDF รวมถึงการบีบอัดรูปภาพ ตั้งค่า`ImageCompression`ทรัพย์สินที่จะ`PdfImageCompression.Jpeg` เพื่อใช้การบีบอัดภาพ JPEG

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
	// บีบอัดรูปภาพโดยใช้ JPEG
    ImageCompression = PdfImageCompression.Jpeg,
	// ตัวเลือก: เก็บรักษาฟิลด์ฟอร์มใน PDF
    PreserveFormFields = true
};
```

## ขั้นตอนที่ 4: บันทึกเอกสารด้วยการบีบอัดพื้นฐาน

บันทึกเอกสาร Word เป็น PDF พร้อมตัวเลือกการบีบอัดรูปภาพที่กำหนดค่าไว้ การดำเนินการนี้จะใช้การบีบอัด JPEG กับรูปภาพใน PDF

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);
```

 ในตัวอย่างนี้ เอาต์พุต PDF มีชื่อว่า`"WorkingWithPdfSaveOptions.PdfImageCompression.pdf"`. ปรับเปลี่ยนชื่อไฟล์ตามต้องการ

## ขั้นตอนที่ 5: กำหนดค่าการบีบอัดขั้นสูงโดยปฏิบัติตาม PDF/A

 เพื่อการบีบอัดที่ดีขึ้น โดยเฉพาะหากคุณจำเป็นต้องปฏิบัติตามมาตรฐาน PDF/A คุณสามารถกำหนดค่าตัวเลือกเพิ่มเติมได้ ตั้งค่า`Compliance`ทรัพย์สินที่จะ`PdfCompliance.PdfA2u` และปรับแต่ง`JpegQuality` คุณสมบัติ.

```csharp
PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	// ตั้งค่าให้สอดคล้องกับ PDF/A-2u
    Compliance = PdfCompliance.PdfA2u,
	// ใช้การบีบอัด JPEG
    ImageCompression = PdfImageCompression.Jpeg,
	// ปรับคุณภาพ JPEG เพื่อควบคุมระดับการบีบอัด
    JpegQuality = 100 
};
```

## ขั้นตอนที่ 6: บันทึกเอกสารด้วยการบีบอัดขั้นสูง

บันทึกเอกสาร Word เป็น PDF ด้วยการตั้งค่าการบีบอัดขั้นสูง การกำหนดค่านี้ช่วยให้แน่ใจว่า PDF เป็นไปตามมาตรฐาน PDF/A และใช้การบีบอัด JPEG คุณภาพสูง

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
```

 ที่นี่เอาต์พุต PDF ถูกตั้งชื่อว่า`"WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf"`. ปรับเปลี่ยนชื่อไฟล์ตามความต้องการของคุณ

## บทสรุป

การลดขนาดเอกสาร PDF โดยการบีบอัดรูปภาพเป็นขั้นตอนสำคัญในการเพิ่มประสิทธิภาพและการจัดเก็บเอกสาร ด้วย Aspose.Words สำหรับ .NET คุณมีเครื่องมืออันทรงพลังเพื่อควบคุมการบีบอัดรูปภาพอย่างมีประสิทธิภาพ ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถมั่นใจได้ว่าเอกสาร PDF ของคุณมีคุณภาพสูงและกะทัดรัด ไม่ว่าคุณจะต้องการการบีบอัดขั้นพื้นฐานหรือขั้นสูง Aspose.Words ก็มอบความยืดหยุ่นเพื่อตอบสนองความต้องการของคุณ


## คำถามที่พบบ่อย

### การบีบอัดภาพใน PDF คืออะไร
การบีบอัดรูปภาพช่วยลดขนาดไฟล์เอกสาร PDF โดยลดคุณภาพของรูปภาพ ซึ่งช่วยเพิ่มประสิทธิภาพการจัดเก็บและประสิทธิภาพการทำงาน

### Aspose.Words สำหรับ .NET จัดการการบีบอัดรูปภาพอย่างไร
Aspose.Words สำหรับ .NET มอบ...`PdfSaveOptions` คลาสที่ให้คุณตั้งค่าตัวเลือกการบีบอัดภาพต่าง ๆ รวมถึงการบีบอัด JPEG

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET เพื่อให้เป็นไปตามมาตรฐาน PDF/A ได้หรือไม่
ใช่ Aspose.Words รองรับ PDF/A ช่วยให้คุณสามารถบันทึกเอกสารในรูปแบบที่ตรงตามมาตรฐานการเก็บถาวรและการรักษาในระยะยาว

### คุณภาพ JPEG มีผลกระทบต่อขนาดไฟล์ PDF อย่างไร
การตั้งค่าคุณภาพ JPEG ที่สูงขึ้นส่งผลให้คุณภาพของภาพดีขึ้นแต่ขนาดไฟล์ใหญ่ขึ้น ขณะที่การตั้งค่าคุณภาพที่ต่ำกว่าจะลดขนาดไฟล์ลงแต่ก็อาจส่งผลต่อความคมชัดของภาพได้

### ฉันสามารถหาข้อมูลเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ไหน
 คุณสามารถสำรวจเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้ที่[เอกสารประกอบ](https://reference.aspose.com/words/net/), [สนับสนุน](https://forum.aspose.com/c/words/8) , และ[ดาวน์โหลด](https://releases.aspose.com/words/net/) หน้า

### ตัวอย่างซอร์สโค้ดสำหรับการบีบอัดรูปภาพด้วย Aspose.Words สำหรับ .NET

```csharp

// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");

PdfSaveOptions saveOptions = new PdfSaveOptions
{
	ImageCompression = PdfImageCompression.Jpeg, PreserveFormFields = true
};

doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);

PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	Compliance = PdfCompliance.PdfA2u,
	ImageCompression = PdfImageCompression.Jpeg,
	JpegQuality = 100, // ใช้การบีบอัด JPEG ที่คุณภาพ 50% เพื่อลดขนาดไฟล์
};



doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
	
```
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
