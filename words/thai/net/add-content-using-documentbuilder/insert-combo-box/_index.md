---
title: เพิ่มฟิลด์ฟอร์มแบบคอมโบบ็อกซ์ในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 310
limit:
description: เรียนรู้วิธีเพิ่มฟิลด์ฟอร์มแบบคอมโบบ็อกซ์ที่มีรายการที่กำหนดไว้ล่วงหน้าในเอกสาร Word ด้วย Aspose.Words for .NET
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มฟิลด์ฟอร์มแบบคอมโบบ็อกซ์ในเอกสาร Word ด้วย Aspose.Words
บทแนะนำนี้แสดงวิธีใช้ DocumentBuilder ของ Aspose.Words for .NET เพื่อสร้างเอกสาร Word ใหม่และแทรกฟิลด์ฟอร์มแบบคอมโบบ็อกซ์ที่มีรายการที่กำหนดไว้ล่วงหน้า โดยการทำตามโค้ดทีละขั้นตอน คุณจะเห็นวิธีกำหนดค่าตัวเลือกของคอมโบบ็อกซ์และจากนั้นบันทึกเอกสารเพื่อใช้ในฟอร์มแบบโต้ตอบ

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: `items` อาเรย์ที่ส่งให้ `InsertComboBox` แทนอะไร?**
A: มันกำหนดรายการสตริงที่ปรากฏเป็นตัวเลือกที่สามารถเลือกได้ในเมนูดรอปดาวน์ของคอมโบบ็อกซ์

**Q: ฉันจะเปลี่ยนรายการที่เลือกเป็นค่าเริ่มต้นเมื่อเปิดเอกสารได้อย่างไร?**
A: ตั้งค่าอาร์กิวเมนต์ที่สาม (`selectedIndex`) ของ `InsertComboBox` ให้เป็นดัชนีเริ่มจากศูนย์ของรายการเริ่มต้นที่ต้องการ (เช่น `2` สำหรับ \"Three\")

**Q: สามารถวางคอมโบบ็อกซ์ในตำแหน่งเฉพาะของเอกสารได้หรือไม่?**
A: ได้—ย้ายเคอร์เซอร์ของ `DocumentBuilder` ไปยังตำแหน่งที่ต้องการโดยใช้เมธอดเช่น `MoveToParagraph`, `InsertParagraph` หรือ `Write` ก่อนเรียก `InsertComboBox`

**Q: รูปแบบไฟล์ที่โค้ดนี้สร้างคืออะไรและสามารถเปิดในเวอร์ชัน Word เก่ากว่าได้หรือไม่?**
A: โค้ดนี้บันทึกไฟล์ `.docx` ซึ่งสามารถเปิดได้โดย Word 2007 ขึ้นไป รวมถึงแอปพลิเคชันใด ๆ ที่รองรับรูปแบบ OpenXML

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}