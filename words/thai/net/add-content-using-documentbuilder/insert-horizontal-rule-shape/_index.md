---
title: แทรกรูปร่างเส้นกั้นแนวนอนในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 110
limit:
description: คู่มือขั้นตอนต่อขั้นตอนในการแทรกรูปร่างเส้นกั้นแนวนอนลงในเอกสาร Word ด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกรูปร่างเส้นกั้นแนวนอนในเอกสาร Word ด้วย Aspose.Words
เรียนรู้วิธีใช้ Aspose.Words for .NET เพื่อแทรกรูปร่างเส้นกั้นแนวนอนลงในเอกสาร Word บทแนะนำนี้จะพาคุณผ่านขั้นตอนการสร้างเอกสารใหม่, เพิ่มบรรทัดข้อความ, วางรูปเส้นกั้นแนวนอนด้วย DocumentBuilder, และบันทึกไฟล์ เส้นกั้นแนวนอนทำหน้าที่เป็นตัวแบ่งภาพง่าย ๆ สำหรับเนื้อหาของคุณ

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: ฉันสามารถเปลี่ยนลักษณะ (สี, ความหนา) ของเส้นกั้นแนวนอนที่แทรกด้วย DocumentBuilder.InsertHorizontalRule() ได้หรือไม่?**
A: InsertHorizontalRule สร้างรูปเส้นแนวนอนในตัวพร้อมการจัดรูปแบบเริ่มต้น; เพื่อแก้ไขลักษณะของมันคุณต้องดึงอ็อบเจ็กต์ Shape ที่แทรกไว้ (builder.CurrentParagraph.LastChild) แล้วปรับคุณสมบัติ LineFormat

**Q: จะเกิดอะไรขึ้นหากฉันเรียก InsertHorizontalRule() หลังจากย่อหน้าที่จบด้วยการขึ้นบรรทัดใหม่แล้ว?**
A: เมธอดจะใส่เส้นกั้นเป็นย่อหน้าแยกออก ดังนั้นการขึ้นบรรทัดใหม่ก่อนหน้าจะสร้างย่อหน้าเปล่าก่อนเส้นกั้น; เส้นกั้นยังคงแสดงบนบรรทัดของมันเอง

**Q: สามารถแทรกเส้นกั้นแนวนอนมากกว่าหนึ่งเส้นในเอกสารเดียวกันโดยใช้ DocumentBuilder ได้หรือไม่?**
A: ได้, ทุกครั้งที่เรียก builder.InsertHorizontalRule() จะเพิ่มรูปเส้นกั้นแนวนอนใหม่ที่ตำแหน่งเคอร์เซอร์ปัจจุบัน, ทำให้สามารถมีหลายเส้นกั้นทั่วทั้งเอกสาร

**Q: InsertHorizontalRule() ทำงานเมื่อบันทึกเอกสารเป็นรูปแบบอื่นนอกจาก DOCX เช่น PDF หรือไม่?**
A: เส้นกั้นแนวนอนถูกเก็บเป็นรูปในโมเดลเอกสาร, ดังนั้นเมื่อบันทึกเป็น PDF, XPS หรือรูปแบบที่สนับสนุนอื่น ๆ เส้นกั้นจะถูกแสดงผลอย่างถูกต้องในไฟล์ผลลัพธ์

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}