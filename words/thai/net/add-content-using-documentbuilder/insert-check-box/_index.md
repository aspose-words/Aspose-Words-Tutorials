---
title: เพิ่มฟิลด์ฟอร์มแบบกล่องกาเครื่องหมายลงในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 210
limit:
description: เรียนรู้วิธีการเพิ่มฟิลด์ฟอร์มแบบกล่องกาเครื่องหมายในเอกสาร Word ใหม่โดยโปรแกรมด้วย Aspose.Words for .NET และบันทึกไฟล์
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มฟิลด์ฟอร์มแบบกล่องกาเครื่องหมายลงในเอกสาร Word ด้วย Aspose.Words
บทแนะนำนี้แสดงวิธีการสร้างเอกสาร Word ใหม่และใช้ DocumentBuilder ของ Aspose.Words for .NET เพื่อแทรกฟิลด์ฟอร์มแบบกล่องกาเครื่องหมาย โดยการทำตามขั้นตอน คุณจะเห็นโค้ดที่ต้องใช้เพื่อเพิ่มองค์ประกอบเชิงโต้ตอบและจากนั้นบันทึกเอกสารเป็นไฟล์ วิธีนี้เป็นวิธีที่รวดเร็วในการสร้างไฟล์ Word ที่มีฟอร์มอย่างง่ายโดยอัตโนมัติ

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: อาร์กิวเมนต์ที่สี่ (0) ใน InsertCheckBox แสดงถึงอะไร?**
A: มันระบุขนาดภาพของกล่องกาเครื่องหมายเป็นหน่วยพอยต์; ค่า 0 บอกให้ Aspose.Words ใช้ขนาดเริ่มต้น

**Q: ฉันสามารถแทรกกล่องกาเครื่องหมายหลายอันที่มีชื่อเดียวกันได้หรือไม่?**
A: ไม่ – ชื่อฟิลด์ฟอร์มแต่ละอันต้องไม่ซ้ำกัน; การพยายามแทรกกล่องกาเครื่องหมายอีกอันที่ชื่อ "CheckBox" จะทำให้เกิด ArgumentException

**Q: ฉันจะเพิ่มกล่องกาเครื่องหมายในเอกสารที่มีอยู่แทนที่จะเป็นเอกสารใหม่ได้อย่างไร?**
A: โหลดเอกสารก่อน (เช่น `Document doc = new Document("Existing.docx");`) จากนั้นสร้าง DocumentBuilder สำหรับเอกสารนั้นและเรียก `InsertCheckBox` ที่ตำแหน่งเคอร์เซอร์ที่ต้องการ

**Q: ฉันจะอ่านสถานะของกล่องกาเครื่องหมายที่แทรกหลังจากบันทึกเอกสารได้อย่างไร?**
A: ดึงฟิลด์ฟอร์มผ่าน `doc.Range.FormFields["CheckBox"]` และตรวจสอบคุณสมบัติ `Checked` เพื่อดูว่ามันถูกเลือกหรือไม่

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}