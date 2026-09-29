---
title: แทนที่ข้อมูลบาร์โค้ดในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 110
limit:
description: เรียนรู้วิธีแทรกฟิลด์ DISPLAYBARCODE และแทนที่สตริงข้อมูลของมันด้วย Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, barcode field, replace barcode data, Document.Range.Replace, DISPLAYBARCODE, Word barcode update]
url: /net/working-with-fields/replace-barcode-data/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: เรียนรู้วิธีแทรกฟิลด์ DISPLAYBARCODE และแทนที่สตริงข้อมูลของมันด้วย
    Aspose.Words for .NET.
  headline: แทนที่ข้อมูลบาร์โค้ดในเอกสาร Word ด้วย Aspose.Words for .NET
  type: TechArticle
- description: เรียนรู้วิธีแทรกฟิลด์ DISPLAYBARCODE และแทนที่สตริงข้อมูลของมันด้วย
    Aspose.Words for .NET.
  name: แทนที่ข้อมูลบาร์โค้ดในเอกสาร Word ด้วย Aspose.Words for .NET
  steps:
  - name: สร้างอ็อบเจ็กต์ Document ใหม่และ DocumentBuilder เพื่อสร้างเนื้อหาของมัน.
    text: สร้างอ็อบเจ็กต์ Document ใหม่และ DocumentBuilder เพื่อสร้างเนื้อหาของมัน.
  - name: แทรกฟิลด์ DISPLAYBARCODE และตั้งค่าชนิด, ค่าเริ่มต้น, และอักขระเริ่ม/หยุด,
      จากนั้นเพิ่มการขึ้นบรรทัดใหม่.
    text: แทรกฟิลด์ DISPLAYBARCODE และตั้งค่าชนิด, ค่าเริ่มต้น, และอักขระเริ่ม/หยุด,
      จากนั้นเพิ่มการขึ้นบรรทัดใหม่.
  - name: เรียกใช้ UpdateFields เพื่อเรนเดอร์ฟิลด์บาร์โค้ดที่เพิ่งแทรกใหม่.
    text: เรียกใช้ UpdateFields เพื่อเรนเดอร์ฟิลด์บาร์โค้ดที่เพิ่งแทรกใหม่.
  - name: ใช้เครื่องมือ Find/Replace เพื่อเปลี่ยนสตริงข้อมูลของบาร์โค้ดจาก INIT123
      เป็น NEWVAL.
    text: ใช้เครื่องมือ Find/Replace เพื่อเปลี่ยนสตริงข้อมูลของบาร์โค้ดจาก INIT123
      เป็น NEWVAL.
  - name: อัปเดตฟิลด์อีกครั้งเพื่อให้ DISPLAYBARCODE แสดงสตริงข้อมูลใหม่.
    text: อัปเดตฟิลด์อีกครั้งเพื่อให้ DISPLAYBARCODE แสดงสตริงข้อมูลใหม่.
  - name: บันทึกเอกสารเป็นไฟล์ .docx.
    text: บันทึกเอกสารเป็นไฟล์ .docx.
  type: HowTo
- questions:
  - answer: '`Range.Replace` จะเปลี่ยนเฉพาะข้อความพื้นฐาน; ผลลัพธ์ภาพของฟิลด์ DISPLAYBARCODE
      จะถูกสร้างใหม่เฉพาะเมื่อเรียก `UpdateFields()` ดังนั้นบาร์โค้ดใหม่จึงปรากฏในเอกสารที่บันทึกไว้.'
    question: ทำไมฉันต้องเรียก `myDocument.UpdateFields()` หลังจากทำ `Range.Replace`?
  - answer: ใช่, `Document.Range.Replace` ทำงานบนช่วงเอกสารทั้งหมด ดังนั้นข้อความที่ตรงกันที่อื่นจะถูกแทนที่
      เว้นแต่คุณจะจำกัดการค้นหาโดยใช้ `FindReplaceOptions` (เช่น ตั้งค่า `Range` เฉพาะหรือใช้
      `.MatchWholeWord`).
    question: '`Replace(\"INIT123\", \"NEWVAL\", ...)` จะส่งผลต่อการปรากฏของ \"INIT123\"
      ที่อยู่นอกฟิลด์บาร์โค้ดหรือไม่?'
  - answer: คุณสามารถกำหนดค่าใหม่ให้กับ `displayBarcode.BarcodeType` ได้ตลอดเวลา แต่ต้องเรียก
      `myDocument.UpdateFields()` หลังจากนั้นเพื่อให้การเปลี่ยนแปลงแสดงในบาร์โค้ดที่เรนเดอร์.
    question: ฉันสามารถเปลี่ยนประเภทของบาร์โค้ด (เช่นจาก CODE39 เป็น QR) หลังจากที่ฟิลด์ถูกแทรกแล้วได้หรือไม่?
  - answer: เมื่อ `AddStartStopChar` เป็น true, Aspose.Words จะเพิ่มอักขระเริ่ม/หยุด
      (`*`) ที่จำเป็นรอบค่าบาร์โค้ดโดยอัตโนมัติ ซึ่งเป็นข้อกำหนดของ CODE39; ตั้งค่าเป็น
      false หากสัญลักษณ์ของคุณไม่ต้องการอักขระเหล่านี้.
    question: '`AddStartStopChar = true` มีผลอย่างไรกับบาร์โค้ด CODE39?'
  - answer: ไม่จำเป็นต้องตั้งค่าพิเศษสำหรับการจับคู่ที่ตรงกันอย่างสมบูรณ์แบบ แต่คุณอาจเปิดใช้งาน
      `.MatchCase` หรือ `.MatchWholeWord` ใน `FindReplaceOptions` เพื่อหลีกเลี่ยงการแทนที่บางส่วนโดยบังเอิญ.
    question: ฉันต้องกำหนดค่าตัวเลือกพิเศษใดใน `FindReplaceOptions` เพื่อแทนค่าบาร์โค้ดอย่างปลอดภัยหรือไม่?
  type: FAQPage
images:
- /net/working-with-fields/replace-barcode-data/og-image.png
og_title: อัปเดตฟิลด์บาร์โค้ดใน Word ด้วย Aspose.Words
og_description: สลับสตริงข้อมูลของบาร์โค้ดและรีเฟรชทันทีในไฟล์ Word.
og_image_alt: ภาพหน้าจอแสดงเอกสาร Word ที่มีฟิลด์ DISPLAYBARCODE ก่อนและหลังการแทนที่ข้อมูลโดยใช้ Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทนที่ข้อมูลบาร์โค้ดในเอกสาร Word ด้วย Aspose.Words
บทแนะนำนี้แสดงวิธีแทรกฟิลด์ DISPLAYBARCODE ลงในเอกสาร Word และจากนั้นใช้เมธอด Document.Range.Replace เพื่อเปลี่ยนสตริงข้อมูลของบาร์โค้ด หลังจากการแทนที่ ฟิลด์จะถูกรีเฟรชเพื่อให้บาร์โค้ดที่อัปเดตปรากฏในไฟล์ที่บันทึกไว้ ทำตามขั้นตอนเพื่อดูการอัปเดตบาร์โค้ดทันทีโดยไม่ต้องสร้างฟิลด์ใหม่.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/replace-barcode-data" >}}


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

**Q: ทำไมฉันต้องเรียก `myDocument.UpdateFields()` หลังจากทำ `Range.Replace`?**  
A: `Range.Replace` จะเปลี่ยนเฉพาะข้อความพื้นฐาน; ผลลัพธ์ภาพของฟิลด์ DISPLAYBARCODE จะถูกสร้างใหม่เฉพาะเมื่อเรียก `UpdateFields()` ดังนั้นบาร์โค้ดใหม่จึงปรากฏในเอกสารที่บันทึกไว้.

**Q: `Replace(\"INIT123\", \"NEWVAL\", ...)` จะส่งผลต่อการปรากฏของ \"INIT123\" ที่อยู่นอกฟิลด์บาร์โค้ดหรือไม่?**  
A: ใช่, `Document.Range.Replace` ทำงานบนช่วงเอกสารทั้งหมด ดังนั้นข้อความที่ตรงกันที่อื่นจะถูกแทนที่ เว้นแต่คุณจะจำกัดการค้นหาโดยใช้ `FindReplaceOptions` (เช่น ตั้งค่า `Range` เฉพาะหรือใช้ `.MatchWholeWord`).

**Q: ฉันสามารถเปลี่ยนประเภทของบาร์โค้ด (เช่นจาก CODE39 เป็น QR) หลังจากที่ฟิลด์ถูกแทรกแล้วได้หรือไม่?**  
A: คุณสามารถกำหนดค่าใหม่ให้กับ `displayBarcode.BarcodeType` ได้ตลอดเวลา แต่ต้องเรียก `myDocument.UpdateFields()` หลังจากนั้นเพื่อให้การเปลี่ยนแปลงแสดงในบาร์โค้ดที่เรนเดอร์.

**Q: `AddStartStopChar = true` มีผลอย่างไรกับบาร์โค้ด CODE39?**  
A: เมื่อ `AddStartStopChar` เป็น true, Aspose.Words จะเพิ่มอักขระเริ่ม/หยุด (`*`) ที่จำเป็นรอบค่าบาร์โค้ดโดยอัตโนมัติ ซึ่งเป็นข้อกำหนดของ CODE39; ตั้งค่าเป็น false หากสัญลักษณ์ของคุณไม่ต้องการอักขระเหล่านี้.

**Q: ฉันต้องกำหนดค่าตัวเลือกพิเศษใดใน `FindReplaceOptions` เพื่อแทนค่าบาร์โค้ดอย่างปลอดภัยหรือไม่?**  
A: ไม่จำเป็นต้องตั้งค่าพิเศษสำหรับการจับคู่ที่ตรงกันอย่างสมบูรณ์แบบ แต่คุณอาจเปิดใช้งาน `.MatchCase` หรือ `.MatchWholeWord` ใน `FindReplaceOptions` เพื่อหลีกเลี่ยงการแทนที่บางส่วนโดยบังเอิญ.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}