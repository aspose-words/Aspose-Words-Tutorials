---
title: แทรกบาร์โค้ด DataMatrix ใน Word Document ด้วย Aspose.Words for .NET
weight: 210
limit:
description: เพิ่มบาร์โค้ด DataMatrix ลงใน Word document อย่างโปรแกรมด้วย Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: เพิ่มบาร์โค้ด DataMatrix ลงใน Word document อย่างโปรแกรมด้วย Aspose.Words
    for .NET.
  headline: แทรกบาร์โค้ด DataMatrix ใน Word Document ด้วย Aspose.Words for .NET
  type: TechArticle
- description: เพิ่มบาร์โค้ด DataMatrix ลงใน Word document อย่างโปรแกรมด้วย Aspose.Words
    for .NET.
  name: แทรกบาร์โค้ด DataMatrix ใน Word Document ด้วย Aspose.Words for .NET
  steps:
  - name: สร้าง Word Document ว่างใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนี้.
    text: สร้าง Word Document ว่างใหม่และ DocumentBuilder เพื่อแก้ไขเอกสารนี้.
  - name: แทรกฟิลด์ DISPLAYBARCODE ที่ตำแหน่งเคอร์เซอร์ปัจจุบัน ซึ่งจะเพิ่มตัวแทนฟิลด์ลงในเอกสาร.
    text: แทรกฟิลด์ DISPLAYBARCODE ที่ตำแหน่งเคอร์เซอร์ปัจจุบัน ซึ่งจะเพิ่มตัวแทนฟิลด์ลงในเอกสาร.
  - name: ตั้งค่า BarcodeType ของฟิลด์เป็น DataMatrix และระบุสตริงข้อมูลที่จะเข้ารหัส.
    text: ตั้งค่า BarcodeType ของฟิลด์เป็น DataMatrix และระบุสตริงข้อมูลที่จะเข้ารหัส.
  - name: สามารถกำหนดสีพื้นหลังและสีพื้นหน้าของบาร์โค้ดได้ตามต้องการ.
    text: สามารถกำหนดสีพื้นหลังและสีพื้นหน้าของบาร์โค้ดได้ตามต้องการ.
  - name: เรียกใช้ UpdateFields บนเอกสารเพื่อเรนเดอร์ภาพบาร์โค้ดภายในฟิลด์.
    text: เรียกใช้ UpdateFields บนเอกสารเพื่อเรนเดอร์ภาพบาร์โค้ดภายในฟิลด์.
  - name: บันทึกเอกสารเป็นไฟล์ .docx.
    text: บันทึกเอกสารเป็นไฟล์ .docx.
  type: HowTo
- questions:
  - answer: ฟิลด์จะถูกแทรก แต่ `document.UpdateFields()` จะทำให้บาร์โค้ดว่างเปล่าและ
      Aspose.Words จะโยน `FieldException` ที่ระบุว่าชนิดบาร์โค้ดไม่ถูกต้อง.
    question: จะเกิดอะไรขึ้นหากฉันกำหนดค่าที่ไม่รองรับให้กับ `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` จะเรนเดอร์ภาพบาร์โค้ด ดังนั้นคุณสามารถแทรกออบเจ็กต์
      `FieldDisplayBarcode` หลายตัวและเรียก `document.UpdateFields()` เพียงครั้งเดียวที่ท้ายเพื่อเรนเดอร์ทั้งหมด.'
    question: ฉันจำเป็นต้องเรียก `document.UpdateFields()` หลังจากแทรกบาร์โค้ดแต่ละอันหรือสามารถเรียกอัปเดตครั้งเดียวหลังจากเพิ่มฟิลด์ทั้งหมดได้หรือไม่?
  - answer: ทั้งสองคุณสมบัติต้องการสตริง RGB แบบฐานสิบหกที่มีคำนำหน้า `0x` (เช่น "0xFF0000"
      สำหรับสีแดง); รูปแบบอื่นจะถูกละเว้นและใช้สีเริ่มต้น.
    question: สตริงสีสำหรับ `BackgroundColor` และ `ForegroundColor` ควรอยู่ในรูปแบบใด?
  - answer: ได้—เพียงตั้งค่า `displayBarcodeField.BarcodeValue` เป็นสตริงใหม่และเรียก
      `document.UpdateFields()` อีกครั้งเพื่อรีเฟรชภาพที่เรนเดอร์.
    question: ฉันสามารถเปลี่ยนข้อมูลบาร์โค้ดหลังจากที่ฟิลด์ถูกแทรกแล้วได้หรือไม่?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: แทรกบาร์โค้ด DataMatrix ด้วย Aspose.Words
og_description: เรียนรู้วิธีเพิ่มบาร์โค้ด DataMatrix ลงในไฟล์ Word เพียงไม่กี่บรรทัดของโค้ด .NET.
og_image_alt: คู่มือแสดงวิธีแทรกและเรนเดอร์บาร์โค้ด DataMatrix ใน Word document ด้วย Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกบาร์โค้ด DataMatrix ใน Word Document ด้วย Aspose.Words
ด้วย Aspose.Words for .NET คุณสามารถเพิ่มบาร์โค้ด DataMatrix ลงใน Word document ได้โดยโปรแกรม บทแนะนำนี้แสดงวิธีสร้างเอกสารใหม่, แทรกฟิลด์ DISPLAYBARCODE, ตั้งค่าชนิดเป็น DataMatrix, และเรนเดอร์ภาพบาร์โค้ดโดยใช้คลาส Document และ DocumentBuilder. ทำตามขั้นตอนเพื่อสร้างบาร์โค้ดที่พิมพ์ได้โดยตรงในไฟล์ .docx ของคุณ.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: จะเกิดอะไรขึ้นหากฉันกำหนดค่าที่ไม่รองรับให้กับ `displayBarcodeField.BarcodeType`?**  
A: ฟิลด์จะถูกแทรก แต่ `document.UpdateFields()` จะทำให้บาร์โค้ดว่างเปล่าและ Aspose.Words จะโยน `FieldException` ที่ระบุว่าชนิดบาร์โค้ดไม่ถูกต้อง.

**Q: ฉันจำเป็นต้องเรียก `document.UpdateFields()` หลังจากแทรกบาร์โค้ดแต่ละอันหรือสามารถเรียกอัปเดตครั้งเดียวหลังจากเพิ่มฟิลด์ทั้งหมดได้หรือไม่?**  
A: `UpdateFields()` จะเรนเดอร์ภาพบาร์โค้ด ดังนั้นคุณสามารถแทรกออบเจ็กต์ `FieldDisplayBarcode` หลายตัวและเรียก `document.UpdateFields()` เพียงครั้งเดียวที่ท้ายเพื่อเรนเดอร์ทั้งหมด.

**Q: สตริงสีสำหรับ `BackgroundColor` และ `ForegroundColor` ควรอยู่ในรูปแบบใด?**  
A: ทั้งสองคุณสมบัติต้องการสตริง RGB แบบฐานสิบหกที่มีคำนำหน้า `0x` (เช่น "0xFF0000" สำหรับสีแดง); รูปแบบอื่นจะถูกละเว้นและใช้สีเริ่มต้น.

**Q: ฉันสามารถเปลี่ยนข้อมูลบาร์โค้ดหลังจากที่ฟิลด์ถูกแทรกแล้วได้หรือไม่?**  
A: ได้—เพียงตั้งค่า `displayBarcodeField.BarcodeValue` เป็นสตริงใหม่และเรียก `document.UpdateFields()` อีกครั้งเพื่อรีเฟรชภาพที่เรนเดอร์.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}